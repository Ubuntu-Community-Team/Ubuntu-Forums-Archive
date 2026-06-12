---
title: "[SOLVED] NTFS boot problems"
date: 2007-11-01
forum: General Help
---

### Post by itix on 2007-11-01
HELP!

I'm an Idiot as usual, but this time I did something extraordinary stupid. I've done like everything from setting grubs timout to 0 with XP as main choice, to removing the swap and renaming system boot files. One can say that I am an expert at installing Ubuntu right now.

Now to the problem. I have tampered with my NTFS options (not the fstab) without knowing anything about "how they are supposed to be". I (dumb as a brick as always) added an automount at the end of the mount options.

It was just to see if it would save me the "enormous" trouble of mounting my NTFS partition manually everytime i wanted to listen to my music (my HD is 10 gig windows, 10 gig ubuntu and 60 gig files (NTFS)). Now I can only use pidgin and internet and such stuff on my ubuntu.

---

### Post by Saubazi on 2007-11-01
Sorry, I have some probs figuring where you did what?
On Ubuntu side or on Windows side - I assume Ubuntu, right? You did not do
changes in /etc/fstab ? So you are using automount? Did you try something using
some fancy graphical interface - I think you should have that map somewhere under
/etc/auto.master or something like that.

It is a long time since I did automount anything but usually it is not necessary if
you use stuff within the same machine - that is to say mount NTFS partition from
windows to Ubuntu - I'd try to remove the automount options until you get the mounting
working with traditional command and then enter the stuff in /etc/fstab normally...

---

### Post by itix on 2007-11-01
It was on the Ubuntu side (the only good things with windows are the compatibility with games, iTunes and the fact that they don't let idiots like me handle advanced system preferences).

I don't have automount, and I was trying to achieve it by dong that stupid change in the boot options. Since I've only used Ubuntu since September, I prefer doing things the graphical way (thats kinda why I prefer XP over MS DOS too). I changed it by right clicking the icon in the file browser for my NTFS-partition (the 60 GB) and changed a little here and there without knowing exactly what I was doing.I have of course tried to remove the little extra line, but it won't help :(

I can mount my NTFS partition from XP without a problem though, so it's local at least (*phew*)

---

### Post by Saubazi on 2007-11-01
I have some problems following what you did and where.
Making a wild guess you did something on Places - Computer Dialogue and Changed something
for the NTFS partition with right click and properties?

Amm... what extra line are you talking about?

Can you post output from commands "sudo fdisk -l", "mount" and "cat /etc/fstab"?

---

### Post by itix on 2007-11-02
I am on my XP partition right now because I still have to do my programming, but I can post those later on returning to Ubuntu. What i did was open my file browser, clicked on the computer button, right clicked on  the NTFS partition and clicked on the tab mount options and added automount.

---

### Post by itix on 2007-11-03
Thanx for all the help, but I'll just reinstall it. The virtue of having one partition per OS and a common patition for files is that you loose no data upon OS-reset. The printouts from the terminal is exactly as they should (sda 1 through 5 listing 2 NTFS, 1 ext3, 1 swap inside 1 container partition). I'll just do what I do best, reistall the OS (and probably wreck it again in another week or so).

---

