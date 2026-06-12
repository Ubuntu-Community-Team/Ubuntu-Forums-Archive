---
title: "kate autocomplete for svg 1.1"
date: 2016-11-23
forum: General Help
---

### Post by cabanni on 2016-11-23
I would like to hav an autocomplete as i said. I read [this]("http://https://docs.kde.org/trunk5/de/applications/kate/kate-application-plugin-xmltools.html") as how to ascribe a meta-dtd in kate. But in the folder  [COLOR=#000000][FONT=&amp] /usr/share/katexmltools is no matching dtd file for svg. The matching dtd is [here]("https://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd"). I copyed it into the katexmltools folder but it looks like it would have a xml file. I think that means i have to install [/FONT][/COLOR][COLOR=#000000][FONT=&amp]dtdparse. I tried to compile this programm but i became this warnings:

[/FONT][/COLOR]```
[COLOR=#000000][FONT=&amp]Checking [/FONT][/COLOR][COLOR=#007020][FONT=&amp]**if**[/FONT][/COLOR][COLOR=#000000][FONT=&amp] your kit is complete...[/FONT][/COLOR]
Looks good
Warning: prerequisite Text::DelimMatch 1.05 not found.
Warning: prerequisite XML::DOM 1.43 not found.
Generating a Unix-style Makefile
Writing Makefile [COLOR=#007020]**for**[/COLOR] SGML::DTDParse [COLOR=#000000][FONT=&amp]Writing MYMETA.yml and MYMETA.json[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]

DelimMatch and DOM 1.43 are a perl.moduls, but i have no idear how to use it.[/FONT][/COLOR]

---

