---
title: "error while loading shared libraries: libwebkitgtk-1.0.so.0: wrong ELF class"
date: 2018-03-30
forum: General Help
---

### Post by olivr3 on 2018-03-30
[COLOR=#000000][FONT=&quot]Hi all![/FONT][/COLOR]
[COLOR=#000000][FONT=&quot] [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]I am getting the following error when trying to run the client UI.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot] [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]/usr/local/pulse/pulseUi: error while loading shared libraries: libwebkitgtk-1.0.so.0: wrong ELF class: ELFCLASS32[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot] [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]I think there is something to do with the OS Type. [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot] [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Does anyone know how to fix it?[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot] [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]thx in advance.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot] [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]OS:[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Ubuntu 16.04 LTS 64-bit[/FONT][/COLOR]

---

### Post by &amp;wP*!) on 2018-04-08
It might be the reason that your application gets dynamically linked shared libraries, say, for 32-bit, but your application is 64-bit. Fix one of them. A similar problem can be found [here]("https://askubuntu.com/questions/398929/unable-to-load-shared-object-wrong-elf-class-elfclass32").

---

