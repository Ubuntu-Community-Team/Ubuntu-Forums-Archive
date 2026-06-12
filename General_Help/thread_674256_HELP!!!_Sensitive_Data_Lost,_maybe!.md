---
title: "HELP!!! Sensitive Data Lost, maybe!"
date: 2008-01-21
forum: General Help
---

### Post by nkobel003 on 2008-01-21
:cry:WAAAAAAAH:cry:
My 500 GB hard drive could have everything on it GONE!

As a run through of how serious this is:
150 GBs of Music, half I can never get again
Backup Data for EVERYTHING
Pictures of all things cool
Once in a life time pictures.
120 GBs of Roms
Hard to find Movies
Documents I can never get again
AND LOTS MORE
But the most important was homework, all of my soon due reports, ebooks, etc.

Okay, so here is what happened.  I was resizing my hard drive with GParted to open another partition up, and it finished in error.  It was able to consolidate the data, move it, size it down, but then left the hard drive with strange files.  Here is some pictures to help explain what happened.  I would get the error code message from GParted, but I don't know how.

Here is what my hard drive looks after:
Through the partition manager:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=57145&stc=1&d=1200945289[/IMG]

And through the file manager:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=57144&stc=1&d=1200945289[/IMG]

Please help, I don't know what to do, I shouldn't have trusted this software to do it in the first place.

---

### Post by bodhi.zazen on 2008-01-21
big ouch

check out testdisk

[http://www.cgsecurity.org/wiki/Running_TestDisk](http://www.cgsecurity.org/wiki/Running_TestDisk)

testdisk is in the repos

---

### Post by compiledkernel on 2008-01-21
Hum....that doesnt look nice. 

you might be able to use testdisk, if that fails to work, you could use some fancy ddrescue stuff to get it back. Either way its lots of machine time and lots of praying. 

If neither of those work go to a data recovery company.

---

### Post by trash on 2008-01-21
You can't totaly trust ANY software to do what you did. I've had friends using Partition Magic mess up their drives.

I hope you get it all back! good luck!

---

### Post by LeAstrale on 2008-01-21
This just not look good in any way.. 

i would in your case spend the money and send it in to a known data recovery company to get the most possible back. it will cost you some money, but it will definately save more of your files than you might be able to yourself. the more you try yourself, the harder it might be for the company to restore files.. keep that in mind.

that said, i wish you good luck with it.

---

### Post by compiledkernel on 2008-01-21
[http://www.cherrysystems.com/](http://www.cherrysystems.com/)

Decent guys.

---

### Post by nkobel003 on 2008-01-21
What I think happened is that GParted merged all my files and folders into one and cut them all apart.  If I could somehow use the algorithm that GParted used to reverse the moving/merging, then I *may* be able to fix it.  Is there any way to reverse an action in GParted?

---

### Post by compiledkernel on 2008-01-21
After you commit the changes, I think not much can be done.

---

### Post by bodhi.zazen on 2008-01-21
If testdisk failed, I second compiledkernel's advice to get professional help.

---

### Post by nkobel003 on 2008-01-25
i tried testdisk and nothing happened; however, i tried something associated with testdisk called photorec.  i was (its working right now) able to get almost all of my songs back, as well as a few videos.  the part that sucks is that every file name has changed, including the id3 tags. sorry, but i'd rather re download everything than rename 17000 songs~roughly.

any other solutions? am I using testdisk wrong?

---

### Post by Zack McCool on 2008-01-25
Other than a data recovery company, I have no real solutions for you.

But you'll be more diligent about backing up in the future, won't you?  

Expensive lesson that everyone learns at some point.

---

### Post by nkobel003 on 2008-01-25
this is the 4th time, actually.  i don't have the money for the data recovery.

---

### Post by bodhi.zazen on 2008-01-25
> **nkobel003 said:**
> i tried testdisk and nothing happened; however, i tried something associated with testdisk called photorec.  i was (its working right now) able to get almost all of my songs back, as well as a few videos.  the part that sucks is that every file name has changed, including the id3 tags. sorry, but i'd rather re download everything than rename 17000 songs~roughly.

any other solutions? am I using testdisk wrong?

no, that is what you get with data recovery tools. Sometimes you need to do more then that (manually combine files or edit files) and sometimes the files are incomplete. For irreplaceable or valuable data that is a small price to pay. If you can replace the data (ie download it again) in less time, go for it.

Consider backing up your data to an external format (DVD).You may run into a problem though with innodes, ie lots of small files. You have a limit on the number of files you can put onto a CD / DVD, so make sure the burn is good (K3b is IMO best for this).

---

