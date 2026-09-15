# Foodplan

Foodplan ist ein privater, nicht-kommerzieller Essensplaner für einen
Familien- und Freundeskreis: Wochenplan, Einkaufsliste, Rezepte und
Vorratsverwaltung.

**Dieses Repository enthält keinen Quelltext.** Es existiert, damit
Seitenbetreiber nachlesen können, was da bei ihnen anklopft — der
User-Agent der Software verweist hierher. Der Quelltext ist nicht
öffentlich.

## Was die Software abruft

Um Wochenangebote neben die Einkaufsliste stellen zu können, ruft Foodplan
zwei öffentlich zugängliche Seiten ab:

| Quelle | Adresse |
| --- | --- |
| ALDI SÜD | `https://www.aldi-sued.de/produkte/wochenangebote/` |
| EDEKA | `https://www.edeka.de/maerkte/<marktnummer>/angebote/` |

Gelesen werden Artikelname, Preis, Grundpreis, Füllmenge und Pfand. Die
Daten werden nicht weiterveröffentlicht und nicht an Dritte gegeben; sie
erscheinen ausschließlich in der Einkaufsliste der angemeldeten Nutzer
dieser einen Installation.

## Wie oft

**Einmal pro Woche**, montags um 08:00 Uhr (Europe/Berlin), zuzüglich
eines manuell auslösbaren Abrufs. Pro Lauf sind das wenige Anfragen: eine
Seite je EDEKA-Markt, bei ALDI SÜD höchstens vier paginierte Seiten. Es
gibt keine Dauerlast und kein paralleles Crawling.

## User-Agent

```
Foodplan/<version> (+https://github.com/oliGellner/foodplan)
```

Die Software gibt sich **nicht** als Browser aus.

## robots.txt

Vor jedem Abruf wird die `robots.txt` der Quelle gelesen und befolgt. Ist
sie nicht erreichbar oder nicht lesbar, findet **kein** Abruf statt — im
Zweifel wird nicht geladen.

Eine Gruppe mit unserem Namen wird ausgewertet und hat Vorrang vor der
`*`-Gruppe. Um Foodplan gezielt auszuschließen, genügt also:

```
User-agent: Foodplan
Disallow: /
```

Der Abruf hört daraufhin von selbst auf — es braucht keine Nachricht an
uns und niemanden, der es bemerkt.

## Kontakt

Wenn etwas stört, ein Abruf Probleme macht oder Sie ihn aus einem anderen
Grund unterbunden haben möchten: bitte ein Issue in diesem Repository
eröffnen. Anfragen werden beantwortet.
