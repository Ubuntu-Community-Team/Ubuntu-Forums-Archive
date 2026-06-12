---
title: "Arabic numbers/dates showing in various places"
date: 2015-08-14
forum: General Help
---

### Post by nabobbles9 on 2015-08-14
I've just installed Ubuntu 14.04 LTS.

I live in the Middle East, and so I set my country location (in the ME) and set my language to English (UK).

Although I'm now getting Arabic numbers and dates coming up in various places, although not everywhere, for example, when I run `ls -l`:

> 4 drwxr-xr-x 2 user1 user1 4096 &#1571;&#1594;&#1587; 14 12:59 Desktop
4 drwxr-xr-x 2 user1 user1 4096 &#1571;&#1594;&#1587; 14 12:59 Documents
4 drwxr-xr-x 2 user1 user1 4096 &#1571;&#1594;&#1587; 14 14:39 Downloads

I think the Arabic above is where the short month-name should be? I translated it online and it says "Gus", but I guess that's just because the shortened month names aren&#8217;t proper words.

When I launch Virtualbox, and attempt to assign memory to a VM, the numbers on this screen are also in Arabic.
If I click on the calendar drop-down in the top right corner, the date infomration is all in Arabic.

I've gone into Settings->Language Support and deleted 'Arabic' from the list 'Language for menus and windows'.
I've gone into Settings->Keyboard->Text Entry and the only languages here are English(UK) and English(US).
I've gone into Settings->User Accounts and my user Language is set to 'English'.
In Settings->Time & Date I'm also seeing some Arabic numbers, although no settings to change here.

At this point, if I change my location to London UK, this doesn't remove the Arabic characters.

I did a `locate Arabic` at command line and found:
> 
/usr/share/consolefonts/Arabic-Fixed15.psf.gz
/usr/share/consolefonts/Arabic-Fixed16.psf.gz
/usr/share/consolefonts/Arabic-VGA14.psf.gz
/usr/share/consolefonts/Arabic-VGA16.psf.gz
/usr/share/consolefonts/Arabic-VGA28x16.psf.gz
/usr/share/consolefonts/Arabic-VGA32x16.psf.gz
/usr/share/consolefonts/Arabic-VGA8.psf.gz


Any ideas?

---

