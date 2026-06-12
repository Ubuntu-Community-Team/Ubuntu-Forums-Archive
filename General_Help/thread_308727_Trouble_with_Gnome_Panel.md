---
title: "Trouble with Gnome Panel"
date: 2006-11-28
forum: General Help
---

### Post by corporate on 2006-11-28
Hey, everyone. I've been using Ubuntu for a couple of months now, no problems at all, until now. When I log in the taskbar won't expand completely, and the other panels just freeze. I logout and login again, and it says that it's detected a panel already working and it's going to exit now. Then I'm stuck with only the wallpaper and the desktop icons. Any ideas what's the problem? It's a good thing I also have Fluxbox, though :)

---

### Post by wpshooter on 2006-11-28
Sounds like to me that something has corrupted on your hard drive.  Maybe you need to see if you can start in recovery mode or see if you can run the Ubuntu/Linux utility that is comparable to checkdisk.

---

### Post by corporate on 2006-11-28
I'll try to do that. Thanks.

---

### Post by loko on 2006-11-28
hello,

in this case you should first try the following.:

logout, go to console with 'STRG+ALT+F1' and login.

then type something like 'sudo killall gnome-panel'.

then logout, press 'STRG+ALT+F7' and login to your desktop again.

then it should work.

---

### Post by corporate on 2006-11-28
Tried that already. Didn't work. 

I started in recovery mode and ran the check and there was nothing wrong.

n00b question: Can gnome be reinstalled or something?

---

### Post by corporate on 2006-11-28
Bump?

---

### Post by corporate on 2006-11-28
Well, it seems it's a problemw ith Nautilus. Everytime I access it from Fluxbox it just opens repeatedly and the background changes to the one from gnome, and the taskbar disaapears.

---

### Post by rioghal on 2006-11-28
> **corporate said:**
> Well, it seems it's a problemw ith Nautilus. Everytime I access it from Fluxbox it just opens repeatedly and the background changes to the one from gnome, and the taskbar disaapears.

Nautilus manages the desktop (wallpaper, icons, etc) in gnome. In order to stop it from doing this, you need to launch nautilus in a special way:

```

nautilus --no-desktop --browser

```

That will launch nautilus without having nautilus change (manage) your desktop.

---

### Post by corporate on 2006-11-28
> **rioghal said:**
> Nautilus manages the desktop (wallpaper, icons, etc) in gnome. In order to stop it from doing this, you need to launch nautilus in a special way:

```

nautilus --no-desktop --browser

```

That will launch nautilus without having nautilus change (manage) your desktop.
That's how I launch it from Fluxbox. Have it in a menu set like that, It always launches fine the first time. Click on it again and it messes up.

I tried reinstalling gnome-panel. Didn't work. But since it meeses up with Fluxbox I'm assuming that other desktop environment I install is going to inherit this problem. Or am I wrong?

---

### Post by weird_c00kie on 2006-11-28
> **corporate said:**
> Tried that already. Didn't work. 

I started in recovery mode and ran the check and there was nothing wrong.

n00b question: Can gnome be reinstalled or something?

it certainly can
i had this weird thing not too long ago where gnome-panel would crash as soon as it tried to load
i uninstalled it, reinstalled it and then it worked :)

just use
> sudo apt-get remove gnone-panel
sudo apt-get install gnome-panel
:)

if that still doesn't work, you can always try 
> sudo apt-get purge remove gnome-panel
not sure if that's correct. it might be *apt-get --purge* or something
or you can do a complete removal from synaptic. same thing :)

hope that helps

---

### Post by corporate on 2006-11-29
Yeah, I've tried that already, Reinstalled through the terminal, through Sypnaptyc. Nothing. Btw, when I uninstalled it, along with ubuntu-desktop, it  still appeared in the GDM. 

I installed xcfe and it worked fine; access the directories with no problem. But I don't just want to get rid of gnome. Anyways, thanks for the help, guys :)

---

### Post by dio525i on 2006-12-17
okay so i had this problem..and i think i know what's up.....

i'm pretty sure the problem would be traced back to harddrive failure....
i'm running a pretty old laptop...yesterday i put it through it's rounds...it was running at 100%cpu for about an hour temp went up to 88*C for most of that time (AMD..the wonders of bad arch.) after i restarted last night my system preformed routine fsck after 30restarts ....found 2.5% non-cont. files so what i think happend is that pushing my computer (mostly with using four desktops using for multi taskig with beryl running overheated my computer and caused my already faulty harddrive (it has had errors before corrected by fsck...actually the reason i switched to UBUNTU is because it could isolate the bad sectors) to corrupt some more area....

anyhow....after that restart panel started screwing up

i suspect that something similar is happening here.....

my advice run "fsck -y" in safemode terminal restart and then reinstall the panel it SHOULD write the new install data to another part of the harddrive (instead of the corrupted part where your panel is now).....thi sis my thinking...but i don't really know...it worked for me : P

---

### Post by ghcs on 2007-01-18
Hi all,

I had this same problem. I managed to fix it by launching xterm (Terminal) and running gnome-panel. Hope this helps. =)

---

