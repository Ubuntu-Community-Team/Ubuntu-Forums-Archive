---
title: "installing nemo file manager at 16.04 gnome"
date: 2016-08-01
forum: General Help
---

### Post by drechsel on 2016-08-01
[COLOR=#2A2E2E][FONT=&amp]As I love quite some of nemo's feature, I tried to install it according to these instuctions:
[http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html](http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html)

at my ubuntu 16.04 gnome box. Nemo will not launch from "activities", trying it from the terminal, it will throw:[/FONT][/COLOR]```
[COLOR=#2A2E2E][FONT=&amp]nemo: error while loading shared libraries: libgnome-desktop-3.so.10: cannot open shared object file: No such file or directory[/FONT][/COLOR]

```[COLOR=#2A2E2E][FONT=&amp]Doing:
```
ls -l /usr/lib/x86_64-linux-gnu/[libgnome-desktop-3.so]("http://libgnome-desktop-3.so/")*
```[/FONT][/COLOR]
[COLOR=#2A2E2E][FONT=&amp]gives:
```
/usr/lib/x86_64-linux-gnu/[libgnome-desktop-3.so]("http://libgnome-desktop-3.so/") -> libgnome-desktop-3.so.12.0.0
/usr/lib/x86_64-linux-gnu/libgnome-desktop-3.so.12 -> libgnome-desktop-3.so.12.0.0
/usr/lib/x86_64-linux-gnu/libgnome-desktop-3.so.12.0.0
```[/FONT][/COLOR]
[COLOR=#2A2E2E][FONT=&amp]So I've got so.12 instead of so.10 - is that the error?[/FONT][/COLOR]
[COLOR=#2A2E2E][FONT=&amp]
Any hints would be appreciated.[/FONT][/COLOR]
[COLOR=#2A2E2E][FONT=&amp]
Cheers,
Wolf[/FONT][/COLOR]

---

