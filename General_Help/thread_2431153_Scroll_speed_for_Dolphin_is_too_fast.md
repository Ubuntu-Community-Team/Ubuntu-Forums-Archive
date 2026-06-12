---
title: "Scroll speed for Dolphin is too fast"
date: 2019-11-12
forum: General Help
---

### Post by R%&amp;92GH&amp; on 2019-11-12
I am trying to use Dolphin as the main file manager in Ubuntu 18.04 LTS with Gnome. However, I have encountered a couple of problems.

One of them, is that the scroll speed is too fast (maybe twice or thrice the normal speed in the rest of the apps). It seems to be related to the icon size (the larger the icon, the fastest it scrolls). I tried adjusting it in KDE's systemsettings app, but I guess the module to configure the mouse is not there.

I am aware that there is a bug related to this [https://bugs.kde.org/show_bug.cgi?id=386379](https://bugs.kde.org/show_bug.cgi?id=386379) but I think that reducing the scroll speed in the KDE settings would also help a little.

So, rephrasing my question: how can I add the Mouse module ( [https://userbase.kde.org/System_Settings/Input_Devices#Mouse](https://userbase.kde.org/System_Settings/Input_Devices#Mouse) ) in KDE settings (package systemsettings) under Gnome?

---

### Post by SeijiSensei on 2019-11-12
Why not just run Kubuntu?  I don't have any scroll speed issues that I can think of.  I can't think of a good reason to run KDE apps on top of GNOME and have to deal with all the differences between Gtk and Qt.

---

### Post by R%&amp;92GH&amp; on 2019-11-12
Because I like the rest of Ubuntu the way it is in Gnome (not saying KDE Plasma 5 is bad at all). 

It all started when I wanted a file browser that could display folder thumbnails with the contents of the folders, similar to what Windows does, and I found that Dolphin does that as well. It makes managing picture libraries much easier. But there's the issue that the default scrolling speed in Dolphin is too high, and I'd like to lower it in the settings (from the default 3 lines per scroll to 1).

The command [FONT=Courier New]kcmshell5 mouse[/FONT] should bring the mouse configuration menu, but that module is not installed. Running [FONT=Courier New]kcmshell5 --list[/FONT] to see all installed modules, I see the following output (sorry it's in my language):

```
user@user-TM1703:~$ kcmshell5 --list
The following modules are available:
cache        - Configura les opcions per a la memòria cau del web
cookies      - Configura com funcionaran les galetes
filetypes    - Configura les associacions de fitxer
kcm_ssl      - Versions i certificats SSL
netpref      - Configuració de les preferències genèriques de la xarxa, com ara els valors per als temps d'espera
proxy        - Configura els servidors intermediaris emprats
screenlocker - Configura el bloqueig de pantalla
smb          - Credencials usades per accedir a les comparticions SMB
useragent    - Configura l'agent d'usuari exposat pel «kioslave» HTTP
webshortcuts - Configura les dreceres web
```

So, is there any way to install the "mouse" module for KDE systemsettings without installing the whole kubuntu-desktop environment?

---

### Post by whochismo on 2019-11-15
Any ideas?

---

### Post by dragonfly41 on 2019-11-15
Since I do a lot of experimenting within Ubuntu 16/04 I do have Dolphin installed .. but I don't use it. I think I installed it to look at coloured folders in Krusader.
My preference for dual-pane file manager is Krusader. i live with the added baggage of kde so I mix the two environments of kde and gnome.  I use Krusader Useractions (in toolbar) to create a toolchain with other apps such as Atom editor.  So I use Krusader as my "front end" to load project files into Atom (as just one example). Other approaches to try would be [Nautilus plus Py extensions]("https://www.giuspen.com/nautilus-pyextensions/").

---

