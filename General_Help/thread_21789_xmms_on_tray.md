---
title: "xmms on tray"
date: 2005-03-23
forum: General Help
---

### Post by core on 2005-03-23
isn't there a way to get xmms player minimized on tray? i installed gxmms panel applet but the idea was not only to hide xmms windows, but also to hide it from taskbar.

i've read something around the forum about some gentoo xmms patches, but i have no idea how to get it working on ubuntu.

thanks.

---

### Post by orion_114 on 2005-04-08
There seem to be some plugins available on the xmms site that minimise it to the tray but these seem to be for KDE only. :(
Sorry I couldn't be of more assistance.

---

### Post by nozey on 2005-08-26
Yes there is a way to put xmms on tray ... 

I used kde for this. Here is what u have to do:

**$ sudo apt-get install xmms-status-plugin**

Now restart the xmms.

With xmms opened, press crtl+p and go to General Plugins tab.
Select Status Docklet and press "Active Plugin". Press "ok".


Now we need to tell KDE to hide XMMS from the taskbar.

Open KDE Control Center
Choose Desktop
Choose Window-Specific Settings
Press "New"
Press "Detect" button under Detect Window Properties
Your cursor should change into a crosshair. Click on XMMS (not on the taskbar!)
You've detected the XMMS properties. Make sure you select "Use Window class (whole application)"
Press "Ok" and change to the Preferences tab
Select "Skip taskbar", select Apply Initially from dropdown list and select the cross on the right side of dropdown list.
Press "Ok" 

You're done! Restart XMMS to apply the changes.

I found this tip here:
[http://gentoo-wiki.com/HOWTO_From_Winamp_to_XMMS](http://gentoo-wiki.com/HOWTO_From_Winamp_to_XMMS)

Hope it helps u.
;D

---

### Post by veraction on 2005-09-04
just wondering if you have any idea how to do that in gnome, cause I don't :(

(hide xmms from taskbar)

---

### Post by sizzam on 2005-10-30
The plugin that nozey posted (xmms-status-plugin) will do the trick.  After you enable it, you can click on the tray icon to make the xmms window disappear (both from the screen and from the window list).


Alternatively, with no plugins, ALT+W will close the XMMS main window.   To get it back, run "xmms -m".

---

### Post by core on 2006-02-24
Thanks for the support, now I can do it.

I dunno if by that time it wasn't possible, but it's preety easy to hide xmms from the taskbar under gnome: just click the icon in the tray: everything goes hidden ;)

---

### Post by redgilda on 2006-08-26
> **core said:**
> I dunno if by that time it wasn't possible, but it's preety easy to hide xmms from the taskbar under gnome: just click the icon in the tray: everything goes hidden ;)
hmm yeah _everything_ goes hidden... what should I do if I want to keep the actual xmms windows but to have the xmms disappear from the taskbar? 

I tried installing this applet, hoping it would maybe do the trick : 
[http://home.gna.org/playground/](http://home.gna.org/playground/)
(trying to follow the rules written there) 

but im getting this:

```
redgilda@redgilda-ubuntu:~/playground-0.3$ ./configure --prefix=/usr --with-gconf-schema-file-dir=/usr/share/gconf/schemas
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
redgilda@redgilda-ubuntu:~/playground-0.3$ make
make: *** No targets specified and no makefile found.  Stop.
```

not sure what's wrong. Im new to linux and I have no idea how to compile things.. but Im pretty sure I do have 'make' as I did use it once before ;-)

But if anyone has any other suggestion how to make xmms disappear from taskbar but stay in tray and on desktop - I'd appreciate it :)

---

### Post by kerry_s on 2006-08-26
I use AllTray, you can dock any app into the system tray and it works with all desktops, i'm using it in fluxbox now. Just add these repos to your /etc/apt/sources.list then do> sudo apt-get update > sudo apt-get install alltray < or > you can use synaptic. here's the repos>

 deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper main dupdate french
 deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french

---

### Post by redgilda on 2006-08-27
hmm AllTray doesnt seem to be working with xmms, but thanks for the suggestion. it's probably only not working for me :p

---

### Post by harsh on 2006-08-29
xmms-status-plugin seems to work perfectly in gnome :) 10x ;)

---

### Post by jhaquo on 2006-11-10
hi
i installed xmm status plugin but when i clic on it, it doesnt disapear from the applications list on the bottom bar

any idea what im doing wrong?

---

### Post by hamirets on 2006-11-15
I'm getting the same problem...
everything went fine before i upgraded to edgy, now clicking the tray icon won't make it disapear from the taskbar anymore
anyone got a clue?

---

### Post by hamirets on 2006-11-15
forgot to say, i'm using the xmms-status-plugin

---

### Post by rotjix on 2006-11-18
As to AllTray it works only with windows which have window decorations enabled.
So it works with XMMS, you only need to enable window decorations. Disabling decorations will make XMMS tray icon to disapear.

---

### Post by matt_risi on 2006-12-28
Holy crap, so much trouble for something that should have been implemented in the first place. Anyone know how to make the XMMS tab disappear from the window list on minimizing to the tray yet?

---

### Post by dominguez.israel on 2006-12-28
HI.
I have ubuntu 6.10 edgy gnome and I have already installed the  xmms-status-plugin
to hide the xmms from the task bar but it doesnt work....any idea???

THANKS...I WILL BE EXPECTING YOUR ANSWER....

---

### Post by ariel on 2006-12-28
Same problem here: the plugin does not hide the XMMS entry in the taskbar & window list...

---

### Post by core on 2006-12-29
Hi

I stopped using XMMS about a months ago so this won't be so helpful. I've been using library-thingy-based players, like amaroK (KDE) or Exaile! (Gnome). But if you really can't live without the XMMS/Winamp interface system, give beep-media-player a try. It's like a simplified gnome version of XMMS.

All of these players - amaroK, Exaile! and Beep Media Player - have hide-to-tray option built-in.

I know I never needed XMMS anymore. Give me a reason why I should use it again ;)

---

### Post by SimonJones on 2007-02-07
> **rotjix said:**
> As to AllTray it works only with windows which have window decorations enabled.
So it works with XMMS, you only need to enable window decorations. Disabling decorations will make XMMS tray icon to disapear.

That's an awesomely simple answer but it makes such a difference!

Thank you! :guitar:

---

### Post by predaeus on 2007-03-13
Thanks, I am back to XMMS and this is a really nice solution!

---

### Post by predaeus on 2007-03-14
Hm, does anybody know how to configure the balloon messages?

The timeout does not work right and the yellow messages get stacked with each song change and have to be clicked away. The grey overlay when moving the mouse over the tray icon vanishes fine.

Apart from that with the window decoration tip everything works fine.

But this other thing is really anoying.


EDIT:

gxmms is a good alternative that I am using now again. But if anybody knows a solution to the above problem. Please post it.

---

### Post by cari on 2007-03-17
Hi, anyone has an idea how to hide xmms from taskbar (xubuntu-edgy) after the xmms-status-plugin installed?

thanks in advance

---

### Post by Andifferous on 2007-04-10
dominguez.israel
I had the same problem as well, although I went back to 6.06, hoping there is a fix in 7.04 when it comes out in a few days.

---

### Post by p0g0 on 2007-05-22
> **predaeus said:**
> Hm, does anybody know how to configure the balloon messages?

The timeout does not work right and the yellow messages get stacked with each song change and have to be clicked away. The grey overlay when moving the mouse over the tray icon vanishes fine.

Apart from that with the window decoration tip everything works fine.

But this other thing is really anoying.


EDIT:

gxmms is a good alternative that I am using now again. But if anybody knows a solution to the above problem. Please post it.
Hi, I disabled them by right clicking in the system tray icon and selecting preferences/status docklet, in there you go to the system tray protocol tab and in balloon timeout (seconds) you reduce it to 0. Restart your XMMS and the balloon messages should no longer appear :).

Edit: I forgot to mention that I don't have activated the support freedesktop.org system tray.

---

