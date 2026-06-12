---
title: "bash: make: command not found NEED HELP"
date: 2006-07-26
forum: General Help
---

### Post by Zigon on 2006-07-26
Long story short I completly screwed myself over by deleting the partition which ubuntu was installed on, I'm getting the grub error, I'm trying to make the boot floppy and I'm a complete linux noob. I've been trying this for a while and im stuck on "make" "make install". Can someone pleeease help me and talk me through it as if im 9 years old, that would help a lot thanks!

---

### Post by Paerez on 2006-07-26
OK so when you say you "deleted the partition" do you mean from fdisk? Or from grub somehow?

What is the grub error?

And are the make make install errors coming from making the boot disk?

I commend your bravery and ability by installing ubuntu at age 9. I think I was playing with legos when I was 9.

---

### Post by Zigon on 2006-07-26
And are the make make install errors coming from making the boot disk?
I meen deleted the partition from fdisk, so it's gone and the memory is al free.
The grub error is somethingl like grub 2.2 error, then sits there doing nothing.
I'm 16 but right now I do feel like a 9 year old trying to figure all of this out.

---

### Post by Paerez on 2006-07-26
put the ubuntu cd into the drive to boot it live (or use any other livecd).

Then try following this guide:
[http://www.faqs.org/docs/Linux-mini/Partition.html#RECOVERING](http://www.faqs.org/docs/Linux-mini/Partition.html#RECOVERING)

---

### Post by Zigon on 2006-07-26
Sorry this is very confusing, could you kind of summarize what im looking at here and what it's saying. And I'm using the live cd right now, linux is not installed on my computer anymore.

---

### Post by Paerez on 2006-07-26
well if you want to recover a deleted partition, it is kind of a complicated process.

Try running "gparted" and see if your partition is there. Also there is a program called testdisk that may help.

Also search this forum. A search for "recover deleted partition" yields 53 results! I am sure one of those people is smarter than me.

---

### Post by Zigon on 2006-07-26
Lol oh god I'm hating this.[IMG]http://img233.imageshack.us/img233/3556/ohgodbr2.png[/IMG]

---

### Post by Paerez on 2006-07-26
Just don't do any saving.

Deleting partitions is a very serious issue. The fix involves manually ready the disk, there isn't going to be a happy "undeleter wizard" as far as I know.

---

### Post by mkw87 on 2006-07-26
> **Zigon said:**
> Lol oh god I'm hating this.[IMG]http://img233.imageshack.us/img233/3556/ohgodbr2.png[/IMG]
Run "sudo gparted" to launch gparted (sudo is superuser).

---

### Post by Henrik on 2006-07-26
Is your plan to recover the data on the deleted parition or just reinstall Ubuntu?

If you plan to recover data then I would suggest asking this question here: [http://www.ubuntuforums.org/forumdisplay.php?f=73](http://www.ubuntuforums.org/forumdisplay.php?f=73) or here: [http://www.ubuntuforums.org/forumdisplay.php?f=100](http://www.ubuntuforums.org/forumdisplay.php?f=100)

If you just want to resinstall you can do that easily from the live CD. Type 'sudo gparted' (password 'ubuntu') and remove the partition leaving unalocated space. Then just reinstall from the Live CD, selecting that space for ubuntu. This will fix grub too.

(btw, this forum section is mainly for assistive technology issues).

---

### Post by Zigon on 2006-07-26
Henrik I just did that, worked great except I had to reformat my computer anyway, it wouldn't give me the option to do otherwise. Thanks for all your help guys!

---

