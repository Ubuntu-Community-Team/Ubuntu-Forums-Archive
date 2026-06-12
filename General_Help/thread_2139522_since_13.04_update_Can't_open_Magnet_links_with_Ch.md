---
title: "since 13.04 update: Can't open Magnet links with Chromium :S"
date: 2013-04-27
forum: General Help
---

### Post by domi1711 on 2013-04-27
Hi!

I have a problem:
since the update to Xubuntu 13.04, i cant open magnet links with chromium anymore...
if i want to open a Magnet link to start Transmission on a torrent site, an error message appears:

"Unable to detect the URI-scheme of 'magnet'..."

how can i fix that? i already tried "xdg-mime default transmission.desktop x-scheme-handler/magnet" but it didnt work :((

edit: Works without problem in Firefox! So its got to be chromium...how can i configure the application for magnet links in chromium?

Please help!

Thanks in Advance!

---

### Post by henrixd on 2013-04-27
I have this problem too.

xdg-open "magnet... works properly and it calls exo-open when XFCE

> 
From: [http://askubuntu.com/questions/62585/how-do-i-set-a-new-xdg-open-setting](http://askubuntu.com/questions/62585/how-do-i-set-a-new-xdg-open-setting)

[COLOR=#333333][FONT=Ubuntu Beta]XFCE uses a program called exo-open, this program doesn't have any way to configure it or add uri handlers. Looking through the source code shows that is uses desktop files to specify only three types of programs. TerminalEmulator, WebBrowser and EmailClient.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]With XFCE4 (and probably also others) it is possible to configure xdg-open to define a custom protocol handler. In some you have to create/edit the following files:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]~/.local/share/applications/protocolhandler.desktop ~/.local/share/applications/mimeapps.list[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]An example adding a handler for the ed2k protocol is provided at stackexchange.com[/FONT][/COLOR][2]("http://unix.stackexchange.com/questions/38650/adding-bindings-for-ed2k-links-with-xdg-open")[COLOR=#333333][FONT=Ubuntu Beta].[/FONT][/COLOR]

EDIT:
my mimeapps.list already contains "x-scheme-handler/magnet=transmission-gtk.desktop", so thats not helping..

---

### Post by henrixd on 2013-04-27
xdg-open wont work properly after all..

looks like xdg-open detects xfce and leaves everything to exo-open, witch does not handle magnets at all.

---

### Post by henrixd on 2013-04-27
I'm not expert, but I think it supposed to use gnome-open

this can be forced with editin /usr/bin/xdg-open and change

if [ x"$DE" = x"" ]; then
DE=generic
fi

to

if [ x"$DE" = x"" ]; then
    DE=generic
fi
DE=gnome

---

### Post by henrixd on 2013-04-27
[https://bugs.launchpad.net/ubuntu/+source/xdg-utils/+bug/1173727](https://bugs.launchpad.net/ubuntu/+source/xdg-utils/+bug/1173727)

---

### Post by Elfy on 2013-04-27
*Thread moved to **General Help**.*

---

