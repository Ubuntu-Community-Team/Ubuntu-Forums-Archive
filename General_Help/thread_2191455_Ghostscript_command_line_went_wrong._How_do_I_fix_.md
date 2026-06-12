---
title: "Ghostscript command line went wrong. How do I fix it? Get errors every time now."
date: 2013-12-02
forum: General Help
---

### Post by RavenLX on 2013-12-02
[FONT=arial]I [COLOR=#333333] was reading the man pages and was going to list the devices available to ghostscript. I misread and did this:[/COLOR]
[COLOR=#000080][FONT=courier new]
gs devicenames ==[/FONT][/COLOR]

[COLOR=#333333]Of course that didn't do anything but an error. Then I realized I was supposed to run gs like a program and then type in devicenames == which gave me the names.[/COLOR]

[COLOR=#333333]However, now gs is fubar. I can't do what I want without it giving the same error (which it didn't used to do that before).[/COLOR]

[COLOR=#333333]Example:[/COLOR][/FONT]

[COLOR=#000080][FONT=courier new]gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=MyPDFFile-New.pdf MyPDFFile.pdf[/FONT][/COLOR]
[FONT=arial]
[COLOR=#333333]Now this is run in the same directory that MyPDFFile.pdf is in so it does exist and I was sure to type it exactly (matching upper and lower case). However, I get this:[/COLOR][/FONT]

[COLOR=#0000cd][FONT=courier new]Error: /undefinedfilename in (MyPDFFile.pdf)
Operand stack:

Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push
Dictionary stack:
   --dict:1169/1684(ro)(G)--   --dict:0/20(G)--   --dict:77/200(L)--
Current allocation mode is local
Last OS error: No such file or directory
GPL Ghostscript 9.06: Unrecoverable error, exit code 1[/FONT][/COLOR]


[FONT=arial][COLOR=#333333]What is going on? It worked before...[/COLOR]

[COLOR=#333333]Can someone tell me how to reset the configuration so it will work again?[/COLOR]

[COLOR=#333333]Thanks.[/COLOR][/FONT]

---

