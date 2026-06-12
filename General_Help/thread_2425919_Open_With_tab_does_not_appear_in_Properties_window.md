---
title: "Open With tab does not appear in Properties window"
date: 2019-09-01
forum: General Help
---

### Post by allelopath on 2019-09-01
I'm following instructions here:
[https://www.howtogeek.com/117709/how-to-change-your-default-applications-on-ubuntu-4-ways/](https://www.howtogeek.com/117709/how-to-change-your-default-applications-on-ubuntu-4-ways/)
in order to associate a file with an application (.tg with Tux Guitar in this case)
but the Open With tab does not appear, only Basic and Permissions.

If I right click on other file types, like .deb, .txt, .mp3, I do see an Open With tab.

What am I doing wrong?

------------------
Nautilus

Ubuntu 18.04.3 LTS

---

### Post by mc4man on 2019-09-01
Maybe mention what release/version of Ubuntu and what file-manager.
Looking here on 18.04 with either nemo or nautilus there is no issue with a .tg file, a right click > properties shows the open with tab.
(though no need to, .tg is automatically associated with tux guitar here, visible in the main context menu or a d. click works..

What happens with a r. click > properties on any other file type?

---

### Post by allelopath on 2019-09-01
Yeah, sorry, a little skimpy on info, huh? Added to original post.

---

### Post by mc4man on 2019-09-02
Well it would appear that if tux isn't installed or maybe installed from some other means than a .deb .tg may not  be recognized and one would see the behavior you describe.
See screen 1 as example.
When installed via the .deb then the file type is registered, a proper .desktop is created and all is well, screen 2

I suspect you installed tux from ubuntu-software and it installed the snap which is deficient in this way..., i.e a poor .desktop file & may not register the mime type
So if context or d. clicking matters then get rid of the snap and install the .deb

```
 sudo snap remove tuxguitar-vs
```
```
sudo apt install tuxguitar
```

You could file an issue if desired at the snapcraft forum or contact the snap creator...
info on snap and so-called contact info.
```
snap info tuxguitar-vs
```

If bound and determined to use the snap then create a fixed .desktop file in ~/.local/share/applications   in a text editor.  Name it tuxguitar-vs.desktop
Ex. below, added the blue to what the snap uses as a .desktop file ( 3 lines edited or added
```
[Desktop Entry]
Name=TuxGuitar[COLOR="#000080"]-vs[/COLOR]
Comment=TuxGuitar
Exec=tuxguitar-vs [COLOR="#000080"]%U[/COLOR]
Terminal=false
Type=Application
Icon=${SNAP}/meta/gui/icon.png
[COLOR="#000080"]MimeType=audio/x-tuxguitar;audio/x-gtp;audio/x-ptb[/COLOR];

```

Then it'll show up in the context menu, screen 3  Probably the icon could also be fixed, didn't bother..

---

