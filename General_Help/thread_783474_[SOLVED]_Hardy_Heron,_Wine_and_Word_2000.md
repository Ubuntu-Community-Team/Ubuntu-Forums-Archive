---
title: "[SOLVED] Hardy Heron, Wine and Word 2000"
date: 2008-05-05
forum: General Help
---

### Post by satterle on 2008-05-05
Upgraded to Hardy Heron. Just installed all updates. I had previously installed MS Word 2000 under Wine and it worked very well. With the upgrade, all the text in my saved documents is bolded and can't be unbolded.

I have repaired the Word install. No help. The docs are important and I really don't want to go back into XP to have to work with them. Any ideas? (Open Office is not an option)

---

### Post by paul101 on 2008-05-05
copy and paste the text into a new document??

---

### Post by jimv on 2008-05-05
you probably need to install Windows fonts.

Type this in a terminal:

sudo apt-get install msttcorefonts

Then try your doc again.  If it still doesn't look right, try installing fonts for Wine using these instructions:

[http://www.linuxforums.org/forum/wine/111138-fonts-wine.html](http://www.linuxforums.org/forum/wine/111138-fonts-wine.html)

---

### Post by satterle on 2008-05-06
I had already installed the core fonts through the applications add/remove gui. Am trying the winetricks script. Two things have happened.

FIRST, when I ran the script the first response was:

fixme:spoolsv:serv_main (0 (nil))

This happened also when I previously reinstalled Word 2000. Doesn't sound good to me. Is this a problem?

SECOND, the winetricks script is still running (about 5 minutes now) and is stuck on 

Backtrace:
...
10 0xb7e909c7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

This behavior also happened when I reinstalled Word 2000 -- terminal hung at the "end" of the routine. I had to Ctrl-C to return to a prompt. Again, is this normal?

---

### Post by satterle on 2008-05-06
Some testing:

Arial, Century Gothic, Times New Roman, Verdana and Wingdings alway stay bold. 

Bitstream Vera, Book Antiqua, Comic Sans, Courier New, Garamond and Georgia toggle between normal and bold. 

All listed as TT fonts in Word. All displayed in a new document.

---

### Post by beow on 2008-05-06
This is hopefully fixed in wine 0.9.60, see

[http://bugs.winehq.org/show_bug.cgi?id=11347](http://bugs.winehq.org/show_bug.cgi?id=11347)

---

### Post by satterle on 2008-05-06
Beow's link (above) answered the problem.

1. Known bug in wine, fixed with version 0.9.60. My current install is .59. Waiting for ubuntu to catch up.

2. Copied arial.ttf from my xp partition to .wine/drive_c/windows/fonts. Everything works fine. wine or corefonts breaks the font into separate packages -- normal, bold, etc -- while the xp package apparently contains all in one.

---

### Post by a1z on 2008-10-14
PART 1/3:

Installing Office 2K in Hardy is done with Wine v1.1.2.

1) install wine 1.1.2
2) extract office 2000 ISO (or zip or rar file)
3) install using setup.exe

====================
PART 2/3:

My question:

MS Word 2000 uses CPU all the time. My CPU meter on the task applet bar shows full usage of CPU when MS Word 2000 is opened and being used. The performance is smooth, nonetheless. When I minimize the window, the CPU relaxes.

What is going on? Is there a way to control the workload of CPU by MS Word 2000? Will this affect the performance of the word processor?

====================
PART 3/3:

SUMMARY:

I see this heavy usage of CPU under these conditions:

1) Hardy + Wine1.1.2 + Office 2000
2) Hardy + Wine1.1.2 + Office 2003
3) XP + Office 2000 (mentioned above)

But it is okay when I open and edit a document under these conditions:

1) XP + Office 2003
2) Hardy + Wine0.9.59 + Office 2003

Thanks in advance!

-a1z

---

