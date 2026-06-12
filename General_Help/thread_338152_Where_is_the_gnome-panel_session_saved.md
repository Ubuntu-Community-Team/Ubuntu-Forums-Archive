---
title: "Where is the gnome-panel session saved?"
date: 2007-01-14
forum: General Help
---

### Post by freaker2k4 on 2007-01-14
Hello,
I was trying to locate any file that might contain the gnome-panel's data, by which i mean all the settings i've done to it, and culdn't locate anything but %gconf.xml which i figured out is not the one.
I googled around and found only refarence to gnome-panel-prorerties, but that's not quit it eather.
If to rephraze the title, what file (and what it's path) does Gnome (or gnome-panel) read to load the panels as previously set By Me ?

I've spinning all over the net for 6 hours now, man i'm dizzy.:shock:

---

### Post by jocko on 2007-01-14
It looks to me like it's all stored in a bunch of %gconf.xml files in ~/.gconf/apps/panel and it's subdirectories.

---

### Post by Ecthelion on 2007-01-14
Maybe a tip...
When you use Synaptic and search for "gnome panel", you'll find gnome-panel 8) 
You can then right-klick on it and say properties.
Then choose "installed files".
You should get these:
> /.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/gnome-panel
/usr/share/doc/gnome-panel/README
/usr/share/doc/gnome-panel/AUTHORS
/usr/share/doc/gnome-panel/README.Debian
/usr/share/doc/gnome-panel/copyright
/usr/share/doc/gnome-panel/changelog.gz
/usr/share/doc/gnome-panel/NEWS.gz
/usr/share/doc/gnome-panel/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/panel-test-applets.1.gz
/usr/share/man/man1/gnome-panel.1.gz
/usr/share/man/man1/gnome-desktop-item-edit.1.gz
/usr/bin
/usr/bin/gnome-panel
/usr/bin/gnome-desktop-item-edit
/usr/bin/panel-test-applets
/usr/lib
/usr/lib/gnome-panel
/usr/lib/gnome-panel/libclock-applet.so
/usr/lib/gnome-panel/libclock-applet.la
/usr/lib/gnome-panel/libclock-applet.a
/usr/lib/gnome-panel/libfish-applet-2.so
/usr/lib/gnome-panel/libfish-applet-2.la
/usr/lib/gnome-panel/libfish-applet-2.a
/usr/lib/gnome-panel/libnotification-area-applet.so
/usr/lib/gnome-panel/libnotification-area-applet.la
/usr/lib/gnome-panel/libnotification-area-applet.a
/usr/lib/gnome-panel/libwnck-applet.so
/usr/lib/gnome-panel/libwnck-applet.la
/usr/lib/gnome-panel/libwnck-applet.a

Maybe it's one of those?
Otherwise it'll be a file in ~/.gnome* dir...
Personally I think you should look in ~/.gnome2/
I think this because I use an applet "quick-lounge" and it's there that I find all the links I configured in it etc...

---

### Post by freaker2k4 on 2007-01-14
[COLOR=Red]_Ecthelion_[/COLOR] : i don't see even one file there that i should edit, all of there files are supposed to run the App.
[COLOR=Red]_jocko_[/COLOR] : It's not /proc, it's /home ... if so, it would have been at least more that 873 bytes.[]("http://ubuntuforums.org/member.php?u=52751")

---

### Post by freaker2k4 on 2007-01-14
> **Ecthelion said:**
> 
Maybe a tip...
When you use Synaptic and search for "gnome panel", you'll find gnome-panel 8) 
You can then right-klick on it and say properties.
Then choose "installed files".

Or just type in the console (after "updatedb") :
locate gnome-panel

and you'll get every path with that sequence.

---

### Post by jocko on 2007-01-14
> **freaker2k4 said:**
> [COLOR=Red][/COLOR]
[COLOR=Red]_jocko_[/COLOR] : It's not /proc, it's /home ... if so, it would have been at least more that 873 bytes.

"/proc"? what? I said nothing about /proc! read my post again! I wrote "~/.gconf/apps/panel" which is the same as /home/username/.gconf/apps/panel.

And the settings **are** stored in **several** %gconf.xml files. For example **each launcher** have **it's own** %gconf.xml in **it's own subdirectory** in ~/.gconf/apps/panel/objects

---

### Post by freaker2k4 on 2007-01-14
I mentioned /proc because if you look in it, you'll see how 0B files with special names located is a tree of directories; and I mentioned /proc because it has nothing to do with the case( no offence, but as your answer.)

I've seen .gconf/apps/panel/* and all those files too, tell it how to run, not Appear. Also notice please that most of these XMLs take 3KB and less{ when each one maximum represents a small grid's detailes} and the rest are empty[if at least they had different names{like in /proc ... lol}].

I don't appriciate maybe answers, because they don't answer the question[ no offence please for such a heavy state, but it's a one file's name question, who knows it please tell me, I've tried it all to find a file in 6 hour i think...].

---

### Post by Ecthelion on 2007-01-14
> I don't appriciate maybe answers, because they don't answer the question[ no offence please for such a heavy state, but it's a one file's name question, who knows it please tell me, I've tried it all to find a file in 6 hour i think...].
Wow, looks like an obsession 8) 

I readed the /usr/share/doc/gnome-panel/README which gave e this idea: since you seem rather in a hurry to find this out, why not subscribe the mailinglist and ask it there?
These people will surely know.

> gnome-panel 2.16.1
==================

This package is free software and is part of the GNOME 2.0 project.

The package contains the GNOME panel which is the area on your desktop from
which you can run applications and applets, and perform other tasks.

The libpanel-applet library is also in this package. This library allows one to
develop small applications which may be embedded in the panel. These are called
applet.

Several applets are also supplied - the Workspace Switcher, the Window List,
the Window Selector, the Notification Area, the Clock and the infamous 'Wanda
the Fish'.

You may download updates to the package from:
   [http://ftp.gnome.org/pub/GNOME/sources/gnome-panel/](http://ftp.gnome.org/pub/GNOME/sources/gnome-panel/)

There is a page about gnome-panel on the GNOME Wiki:
   [http://live.gnome.org/GnomePanel](http://live.gnome.org/GnomePanel)

[email]desktop-devel-list@gnome.org[/email] is the relevant mailing list:
   [http://mail.gnome.org/mailman/listinfo/desktop-devel-list](http://mail.gnome.org/mailman/listinfo/desktop-devel-list)
[B]
To subscribe, send a mail to [email]desktop-devel-list-request@gnome.org[/email] with the
subject "subscribe".[/B]

I'm really sorry this still won't answer your question...
Still we'r really trying to help :KS 

(If you get an answer on the ML, please also post it here. I'm also curious where this gets saved...)

---

### Post by jocko on 2007-01-14
@ freaker2k4: Sorry, you lost me there. I honestly don't understand your last post.

---

### Post by jocko on 2007-01-14
This is how I **know** the settings for gnome-panel are stored in ~/.gconf/apps/panel (If you don't believe me, try it yourself):

First I copied the folder ~/.gconf/apps/panel to my desktop then I deleted ~/.gconf/apps/panel.
After a reboot the panel is back to how it looked after I first installed Ubuntu. There was still no new ~/.gconf/apps/panel directory. One more reboot and a new ~/.gconf/apps/panel directory appeared, still with the default settings on the panel.
I deleted the new ~/.gconf/apps/panel and replaced it with the backup from my desktop. After one more reboot now I have my customized gnome-panel back again. Proof enough for you?

[COLOR=Red] Edit[/COLOR]: Instead of all the reboots, just run ```
killall gconfd-2 && killall gnome-panel
``` from a terminal.

---

### Post by freaker2k4 on 2007-01-14
> **Ecthelion said:**
> Wow, looks like an obsession 8) 

I readed the /usr/share/doc/gnome-panel/README which gave e this idea: since you seem rather in a hurry to find this out, why not subscribe the mailinglist and ask it there?
These people will surely know.



I'm really sorry this still won't answer your question...
Still we'r really trying to help :KS 

(If you get an answer on the ML, please also post it here. I'm also curious where this gets saved...)

Wohow.... You got a slight mistaken impression..=; I ain't demanding an answer , and tnx A lot for the links; you can bet i'll show off here with the reasults.... :p

---

### Post by freaker2k4 on 2007-01-14
> **jocko said:**
> This is how I **know** the settings for gnome-panel are stored in ~/.gconf/apps/panel (If you don't believe me, try it yourself):

First I copied the folder ~/.gconf/apps/panel to my desktop then I deleted ~/.gconf/apps/panel.
After a reboot the panel is back to how it looked after I first installed Ubuntu. There was still no new ~/.gconf/apps/panel directory. One more reboot and a new ~/.gconf/apps/panel directory appeared, still with the default settings on the panel.
I deleted the new ~/.gconf/apps/panel and replaced it with the backup from my desktop. After one more reboot now I have my customized gnome-panel back again. Proof enough for you?

[COLOR=Red] Edit[/COLOR]: Instead of all the reboots, just run ```
killall gconfd-2 && killall gnome-panel
``` from a terminal.

You were actually right, I deeply apologize. Thought it's a bit fightening operation....

[I Zipped this folder {/panel} and mailed it to myself with the saved Packages file and xorg.conf ...:-)]

---

