# Prompt-Bibliothek

Eine durchsuchbare Prompt-Bibliothek als einzelne statische Seite, mit über 3.000 Prompts aus
[prompts.chat](https://github.com/f/prompts.chat) (früher „Awesome ChatGPT Prompts“).

## Nutzung

`index.html` im Browser öffnen. Ein Server ist nicht nötig, weil die Daten als `data/prompts.js` eingebunden sind.

## Funktionen

- **Volltextsuche** in Titel und Inhalt. Mehrere Wörter müssen alle vorkommen, Treffer im Titel stehen oben.
- **Filter** nach Typ (Text, Strukturiert, Bild), „Für Entwickler“ und Favoriten.
- **Platzhalter ausfüllen:** Variablen wie `${thema}` oder `${sprache:Deutsch}` werden als Eingabefelder angezeigt
  und vor dem Kopieren eingesetzt. Ein Standardwert nach dem Doppelpunkt wird genutzt, wenn das Feld leer bleibt.
- **Kopieren** oder den Prompt direkt **in ChatGPT oder Claude öffnen**.
- **Favoriten** werden im Browser gespeichert (`localStorage`).
- Heller und dunkler Modus, auch auf dem Handy nutzbar.

## Daten aktualisieren

```sh
git clone --depth 1 https://github.com/f/prompts.chat.git /tmp/prompts.chat
python3 scripts/build_data.py /tmp/prompts.chat/prompts.csv
```

Das Skript übernimmt Titel, Prompt-Text, Typ und das Entwickler-Flag. Die Spalte `contributor` wird bewusst
weggelassen, weil sie teilweise E-Mail-Adressen enthält.

## prompts.chat als MCP-Server

`.mcp.json` bindet den offiziellen MCP-Server `https://prompts.chat/api/mcp` ein. Claude Code fragt beim
ersten Start im Repo, ob er aktiviert werden soll. Danach stehen unter anderem diese Tools zur Verfügung:

- `search_prompts`: Prompts nach Stichwort, Kategorie, Tag oder Typ suchen
- `get_prompt`: einen Prompt abrufen und `${platzhalter}` direkt ausfüllen
- `improve_prompt`: einen eigenen Prompt verbessern lassen
- `search_skills` und `get_skill`: Agent Skills finden und laden

In anderen Tools (Claude Desktop, Cursor usw.) funktioniert derselbe Eintrag unter `mcpServers`.

## Lizenz der Inhalte

Die Prompts stammen aus prompts.chat und stehen unter [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/)
(Public Domain).
