---
title: "Kubuntu woun't load properly, splash screen, then command prompt"
date: 2008-01-27
forum: General Help
---

### Post by haavardravnaas on 2008-01-27
I have installed Kubuntu using Wubi. 
I have restarted, and as far as i know finished the install progress. When I then reboot i get a splash screen thet seems to load completely before i suddenly end up at som kind of command prompt, exept that I am unable to write any commands.
Whatever i write I just move one line down when i press enter, there are no error messages at all, is looks similiar to writing in an edit file or something, exept that I don't.
Only thing that works is ctrl+alt+delete, I get a message about something exiting but it  goes to fast to read. Then there is a shutdown splash and the system restarts normally.

I am new to linux, but I know that the command prompt is not as it should be.

System specs:

AMD Athlon 64 X2 4200+, 2,2GHz
2 gig ram
Geforce 8800GT 512mb
XP home installed
Wubi 7,04

Thanks in advance for any help

---

### Post by superunknownnot on 2008-01-27
Hi, please look at this

[HTML]http://ubuntuforums.org/showthread.php?t=676207[/HTML]

Are you experience that same as me?

---

### Post by ago on 2008-01-28
> **haavardravnaas said:**
> I have installed Kubuntu using Wubi. 
I have restarted, and as far as i know finished the install progress. When I then reboot i get a splash screen thet seems to load completely before i suddenly end up at som kind of command prompt, exept that I am unable to write any commands.
Whatever i write I just move one line down when i press enter, there are no error messages at all, is looks similiar to writing in an edit file or something, exept that I don't.


Press ctrl+alt+f2, login run

sudo dpkg-reconfigure xserver-xorg
select vesa driver
leave the other options as they are
run

sudo /etc/init.d/gdm restart

---

### Post by haavardravnaas on 2008-01-30
I got an error when I wrote sudo /etc/init.d/gdm, but I restarted anyway and everything worked just fine!
Thanks very much for your help!

---

