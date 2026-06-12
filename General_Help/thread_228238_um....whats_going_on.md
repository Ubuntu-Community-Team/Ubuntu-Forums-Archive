---
title: "um....whats going on"
date: 2006-08-02
forum: General Help
---

### Post by Arandomcow5 on 2006-08-02
ok...well ive been using linux for a year...so im not a total idiot...but this is whats going on

earlier today the transformer down the street blew up...so i got a huge power surge to my computer (yes i do have a surge protector) (dont know if this maters to the problem, but thought i would mention it)

anyways i turn on my computer...log into godly ubuntu dapper...and whats on my desktop? a folder thats suppose to be in my home folder...but its also in my home folder at the same time...so it was cloned or something

the folder acts like a shortcut in reality...but i never made a shortcut

now the weird thing is is that i cant delete it...infact my computer doesnt even know its there
ive tried "sudo rm /home/user/Desktop/Documents" but that only tells me it doesnt exist
i thought maybe the permissions might be screwed up, but it doesnt even HAVE permissions
here are some screenshots:
[http://img135.imageshack.us/img135/6601/screenshotsy4.png]("http://img135.imageshack.us/img135/6601/screenshotsy4.png")
[http://img123.imageshack.us/img123/8707/screenshot1zq1.png]("http://img123.imageshack.us/img123/8707/screenshot1zq1.png")

all i know is that i cant delete it, move it, chmod it, or anything

any help is appreciated

---

### Post by RAOF on 2006-08-02
I presume that **after** the surge, the computer lost power, right?  That looks like some common-or-garden filesystem corruption, the sort that running a **fsck** should be able to detect and clean up.

The command line will be something like:
```
sudo fsck -f */dev/hda1*
```
Where you need to replace */dev/hda1* with the actual device that you're filesystem's on.

You may need to run the fsck from a live CD, but I think you should be able to get it to run on boot-up instead.

---

### Post by astoltz on 2006-08-02
Yeah, it's kind of a shortcut.  If there is a directory called ~/Documents, gnome will put a link to it on the Desktop.  Delete it out of your home directory NOT out of the Desktop directory.

---

### Post by RAOF on 2006-08-02
> **astoltz said:**
> Yeah, it's kind of a shortcut.  If there is a directory called ~/Documents, gnome will put a link to it on the Desktop.  Delete it out of your home directory NOT out of the Desktop directory.

Cool.  You live and learn :)

---

