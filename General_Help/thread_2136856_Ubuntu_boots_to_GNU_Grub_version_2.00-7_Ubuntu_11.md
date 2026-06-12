---
title: "Ubuntu boots to GNU Grub version 2.00-7 Ubuntu 11"
date: 2013-04-18
forum: General Help
---

### Post by Moontra on 2013-04-18
[COLOR=#333333][FONT=Ubuntu Beta]I am using dual boot windows7/Ubuntu 12 and it has been working just fine in the past.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]After my last reboot when I select Ubuntu it goes to a black screen that shows:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]
GNU GRUB Version 2.00-7 Ubuntu 11
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename1 grub>
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]If I press tab it reads:
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Possible commands are; blocklist boot cat chainloader cmp color configfile debug displaymem embed find fstest geometry halt help hide impsprobe initrd install ioprobe kernel lock makeactive map md5crypt module modulenounzip pager partnew parttype password pause read reboot root rootnoverify savedefault serial setkey setup terminal terminfo testload testvbe unhide uppermem uuid vbeprobe grub>
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Any idea of where to go from here to restore Ubuntu? I am having trouble finding answers through google or forum search
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Thanks[/FONT][/COLOR]

---

### Post by deadflowr on 2013-04-18
Look over

[Boot Repair]("https://help.ubuntu.com/community/Boot-Repair").

---

### Post by Moontra on 2013-04-19
I just ran Boot Repair from disc and it read that it ran successfully. It said I could connect to the internet to get a detailed report but I wasn't able to connect to my wifi even after fiddling with it for a long while. :/

Now when I start my computer I no longer have the option to select Ubuntu. It goes straight to the windows OS.

There was no files stored there that were crucial to me, I figured I could just reinstall ubuntu. But before I jump into that I wanted to see if there was still a way to restore, so I wont have to go through the pain of reinstalling all my old software / settings.

---

### Post by oldfred on 2013-04-19
If you cannot get on Internet with wireless use a Ethernet cable connection. 

Or copy file to flash drive. It usually is too large to post, but you can still copy to one of the pastebin sites.
I have never done it manually, so do not know details. Much easier to let Boot-Repair automate the process.

---

