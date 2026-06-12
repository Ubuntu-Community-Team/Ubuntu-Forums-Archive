---
title: "IPOD and Banshee won't detect anymore :("
date: 2007-04-05
forum: General Help
---

### Post by louisd11 on 2007-04-05
I have an apple IPOD and i use banshee to update all my songs on it. But recently, I have had some problems with my GNOMe and I issued a > rm -rf .gnome .gnome2 .gconf .gconfd .metacity command. It fixxed the error but all my songs got erased in banshee so I just put them bakc, but know when I plug my IPOD in the desktop shows it connected and then two windows show up "Music Player" and another music player I think called "rythembox" or somethin like that. Anyway how do i get my ipod to work with banshee because when I have banshee open and pluyg in the ipod it dosen't do anything.

---

### Post by Smuve on 2007-04-05
Check your System > Preference > Removable Drives and Media settings.

You might some weird auto-run behavior going on when you plug it in.

I would choose auto mount, but maybe leave everything else unchecked.  You don't want it to do anything else when you plug it in.  These settings will apply to usb sticks and external hard drives as well.  Maybe you have "browse when attached" checked on.

---

### Post by louisd11 on 2007-04-05
I did both but none of them worked. I unchecked autorun rythem box and I also unchecked "browse removable media"

---

### Post by Smuve on 2007-04-05
Did you try this?  Browse to a music file, presumably .mp3, right click, choose open with and select Banshee

---

### Post by louisd11 on 2007-04-07
I did that and now it comes up at "Local Queue". And I cant delete that. Anywho "music player" detects it just fine.

EDIT: I think it has to do weith my packages also does anyone had 12.1 .deb?

Also when I type in IPOD in terminal I get command not found error. And when I try to install ipod I get this error
> 
ipod:
 Depends: libdbus-1-2 (>=0.60) but it is not installable
 Depends: libipoddevice0 but it is not going to be installed

---

### Post by Smuve on 2007-04-09
Got to synaptic and do a search for "dbus".  See if you have it installed or if there are any dev or libdbus packages you could install.  Do the same for "ipod".  Then try to install bashee again.

---

