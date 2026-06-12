---
title: "Copying Files From Windows to Ubuntu"
date: 2008-06-08
forum: General Help
---

### Post by alfred3x on 2008-06-08
I'm setting up a Ubuntu box for my mother.  Started with 7.01, and upgraded to 8.04.  It automatically recognized the network and found her Win98 machine, so I was able to copy all her docs and data over.

I've converted her Outlook emails and contacts to Outlook Express, and from there to Thunderbird, still on the Win98 box.  Now I need to move her profile folder to the Ubuntu box, and for some reason it's giving me the following:

Error while copying "extensions".
There was an error copying the file into /home/yvette/Documents/tbird_win98.
No such file or directory

Any assistance would be welcome.

Thanks,
- AAA

---

### Post by NikoC on 2008-06-08
I 'm going out on a limb here but is there a (hidden) .ds file (or something like it) somewhere in the win98 folder you are trying to copy? It doesn't contain anything useful, so you don't need to include it... perhaps linux has problems with these?

---

### Post by alfred3x on 2008-06-08
Thanks for the prompt response, but no, I tried a couple of individual files, and they did work.  Then a group of files, and they worked too.  Then a folder, and it gakked.  So I'm thinking it doesn't want to create new folders for me.  Though it did previously, when I moved a whole bunch of docs and other files over.  Mind you, that was while we were still on 7.01.  Now we're on 8.04.  If that makes a difference...

BTW, does anyone know how to reference a file(s) on a Samba share from the Ubuntu terminal?

Thx.

---

### Post by alfred3x on 2008-06-08
Whoa!  It turns out SAMBA isn't running after all!  So, how am I getting to Win98?  OK, I guess I should install it.  There will be another Windows box on the network, but it's be XP.

---

### Post by alfred3x on 2008-06-14
So, couldn't get past the creating directories problem when copying the whole set of files with directories.  So I sidestepped it.  I zipped up all the files and dirs, then copied the single file to where I wanted, and handily unzipped it.  It created the directories without any issues.

---

