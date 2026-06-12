---
title: "saving 32 bit files, to 64 bit distro"
date: 2020-11-10
forum: General Help
---

### Post by oneleded on 2020-11-10
1st. question; can i have a 32 bit lubuntu distro and a 64 bit lubuntu dristo on the same drive?
2nd. question; is there any problem with transferring 32 bit files to ta a 64 bit distro using copy and paste?

---

### Post by guiverc on 2020-11-10
Yes you can have both *i386* & *amd64* systems on the same drive.
You'll have them on different partitions selecting which you use via `grub` or another boot loader.

Yes you can safely transfer data files from any *i386* system to an *amd64* system without issue, either way too.


FYI:  i386 is what Debian & Ubuntu refer to all x86 32-bit systems, the linux kernel does distinguish between i386, i486, i586 & i686 internally, but Debian & Ubuntu treat all as i386 (you need a i686 capable CPU to boot a modern i386 Ubuntu or Debian).

FYI: amd64 is the x86_64 architecture name, used by all companies. Intel tried to get everyone to move to IA64 which was not x86 compatible, the market instead went with amd64 (created by AMD) which was fully x86 compatible. IA64 is dead, and intel are now amd64 too (*mentioned only in errata notes in the small print though*).

---

### Post by oneleded on 2020-11-11
thanks. your nice looking dog? what kind

---

### Post by oneleded on 2020-11-25
just one more question. can i install the same distro on a different partition on the same drive? after that, i can mark this solved.

---

### Post by guiverc on 2020-11-25
Sorry I hadn't noticed the reply & question.

My dog was a samoyed, alas he died beginning of the year (15 years old).

The box I'm typing this reply into has two installed OSes
-  Ubuntu 18.04 LTS
- Ubuntu *hirsute* (what will become 21.04 on release). 
The box is a 2009 dell, only has a single hdd (160gb). My disk space has 5 partitions, a shared *swap*, plus / & /home for the two releases (it's MBR so I'll have an *extended* partition)

 Most of my boxes are dual boot (*without windows; I have no win7/8/10*), and it's usually different releases (eg. my prior box which is an older dell) contains Lubuntu 20.04 LTS & Lubuntu 18.04 LTS  (*both installs were actually i386 or 32-bit on initial install, but converted to amd64 via re-install but without format*; ie. software was changed & my user directories re-used for over a decade now). I've got a number of boxes, with various options (including some non-Ubuntu)

I just completed a Lubuntu *hirsuite* install on another box (QA-test), it now contains
- Lubuntu [I]hirsute
- [/I]Lubuntu [I]hirsute
Hirsute[/I] is what I'm testing currently, it'll be *focal* probably next, ie. 20.04.2

The OS, release, and architecture can be anything. I haven't tested i386 since August-2020 (*for the 18.04.5 release*) so currently most my installs are *amd64*; but that matters little.

(FYI: My profile says I'm using Lubuntu *development* release, this my primary box has multiple desktops installed, and I'm using Lubuntu/LXQt currently (*as is normally the case*); but it also has Ubuntu/GNOME, Xubuntu/XFCE.. installed too)

---

### Post by oneleded on 2020-11-27
sorry for your loss of family member. 
i remember a dog like that from long ago, one of my cousins had.
over 50 years ago.
thanks for your answer, bout the installs also.

---

