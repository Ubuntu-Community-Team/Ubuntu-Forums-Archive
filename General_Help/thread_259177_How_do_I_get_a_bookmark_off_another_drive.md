---
title: "How do I get a bookmark off another drive?"
date: 2006-09-17
forum: General Help
---

### Post by Maheriano on 2006-09-17
I've got Ubuntu installed on my main drive and an old copy of Gentoo on my backup drive. I want to be able to get a bookmark I had in Firefox for checking my stocks at work. It's on my other Gentoo drive, is there any way to get it? I also want to get the email address of someone who emailed me in my Kmail, is that possible?
I try to boot into the other hard drive but I've changed hardware and it won't boot. What can I do?#-o

---

### Post by amohanty on 2006-09-17
what format is the other drive in?

can you post the output of **sudo fdisk -l**

---

### Post by sktx on 2006-09-17
Assuming that you've got the drive mounted, you can go to your old gentoo /home folder and it should be backed up in your firefox folder... If, for example, you had your old gentoo drive mounted as /mnt/gentoo, and your user name was maheriano, the firefox dir should be something like:

**/mnt/gentoo/home/maheriano/.mozilla/firefox/**

In that firefox dir, there should be another dir whose name consists of random-looking letters and numbers, something like **15agaefw.default/** 
so cd into **15agaefw.default/bookmarkbackups**, and copy the newest  **bookmarks-*.html **file to your home dir (~).

In the firefox menubar, go to **_B_ookmarks**, then to **_M_anage Bookmarks...** 

In the window that pops up, go to _**F**_**ile**, then to _**I**_**mport **and import the file that you've just copied to your home dir.  This should import all the bookmarks that you had from your gentoo installation. 

I'm not so sure about kmail though, never used it. I'm more of a sylpheed-claws-gtk2 type of guy.

Anyway, hope this helps.

 sktx

---

### Post by Maheriano on 2006-09-17
That did it for the bookmarks, thanks. But now I get this when I go to the website.

> Microsoft VBScript runtime  error '800a000d'

Type mismatch: '[string: "unknown"]'

/_private/css.inc, line 2 

I haven't been there in a month or so, but I have about 50 stock in this company and they went up about $8 overnight so I'm trying to find out what's happening!



So anyone for Kmail?

---

### Post by Maheriano on 2006-09-17
sweet sweet moola.

Average Cost Per Share = $46.85
Total Cost = $4278
Market value = $5566

Thanks fellas!

---

### Post by sktx on 2006-09-17
Congrats on your 'folio, man.  :)

Glad it worked out.

---

