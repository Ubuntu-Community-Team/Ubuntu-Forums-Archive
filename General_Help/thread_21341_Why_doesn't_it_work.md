---
title: "Why doesn't it work?"
date: 2005-03-21
forum: General Help
---

### Post by RyaninZion on 2005-03-21
I am still unable to get the Hoary liveCD to work.  I go through the entire boot process, it successfully detects my hardware (the wireless light even pops on), but then I am presented with a blank screen when the desktop should appear.

I have actually tried downloading and burning the iso several times, fearing I had a corrupted copy at first.

I did not have this problem with Warty.  

Any suggestions?  Is there a boot command I can give to make it work?  I have tried a few already (acpi=off, vga=771)

Thank you

---

### Post by az on 2005-03-21
Do you have a command prompt?  If not, do CTRL-ALT-F1 and see what is there?  can you log in?
If you can, is there anything interesting in dmesg?

You can chesk the xserver logs, too.

---

### Post by RyaninZion on 2005-03-22
I do not get a command prompt, just a black screen.  I tried hitting CTRL-ALT-F1 after the black screen came up, but nothing happened.

---

### Post by RyaninZion on 2005-03-22
Maybe I should mention that I am using the Array 6 disc.  Maybe trying the Array 7 will make a difference?

---

### Post by DarkTrancer on 2005-03-22
Ive also had problems with the live cd,at first because of display,so i used vga 771 noapic nolapic etc
Everything was going good untill i got a red screen telling my i had a error, "Enter Preinstalled Session" was the failing step,i`ve tried but can`t find a way around this.
Hardware:
Acer Travel Mate 225:1.33celery,256mb mem,20gig hd,generic dvdrom,netgear wg511 card.

Any ideas?

---

### Post by bela on 2005-03-22
[QUOTE=DarkTrancer]Ive also had problems with the live cd,at first because of display,so i used vga 771 noapic nolapic etc
Everything was going good untill i got a red screen telling my i had a error, "Enter Preinstalled Session" was the failing step,i`ve tried but can`t find a way around this.
Hardware:
Acer Travel Mate 225:1.33celery,256mb mem,20gig hd,generic dvdrom,netgear wg511 card.

Any ideas?[/QUOTE]



I had in some way  same problem, I downloaded several ubuntu disks but no one could be installed because failer in disk, when I checked it with md5sum, the code doesn't correspond to the content of the CD.
I left it awaay and came back to my standard debian.

I think the developpers have to check the disks before putting them for download,  DEBIAN HAS THE BEST POLICY for the realeses, when you get the official release you are really quiet for a wile!!!!

best regards 
bela

---

### Post by RyaninZion on 2005-03-23
I also just tried it with vga=771 noapic nolapic acpi=off, etc - but was still presented with a totally blank screen following the boot process.

---

### Post by vkashin on 2005-04-17
i have the same problem as well. live cd wont boot.. they just show me a blank screen

---

