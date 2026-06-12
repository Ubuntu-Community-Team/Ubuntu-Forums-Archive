---
title: "rsync not working"
date: 2012-11-05
forum: General Help
---

### Post by rmcellig on 2012-11-05
I can't understand why my test rsync doesn't work. Any ideas?

rsync -ruvn --delete /media/randy/radio_music/test2/ /Home/Desktop/test1

Nothing happens. I have the code in Scheduled tasks which I use all the time. Even when I frce the code to sync, nothing happens. I have some items in the test2 folder that I would assume show up in the test1 folder.

---

### Post by Herbon on 2012-11-06
> **rmcellig said:**
> I can't understand why my test rsync doesn't work. Any ideas?

rsync -ruvn --delete /media/randy/radio_music/test2/ /Home/Desktop/test1

Nothing happens. I have the code in Scheduled tasks which I use all the time. Even when I frce the code to sync, nothing happens. I have some items in the test2 folder that I would assume show up in the test1 folder.


No errors??

And remove the 2nd "-" in front of "-delete"
>   rsync -ruvn -delete /media/randy/radio_music/test2/  /Home/Desktop/test1

---

### Post by Lars Noodén on 2012-11-06
Try -a instead.  It stands for -rlptgoD (recursive, copy symlinks as symlinks, preserve permissions, preserve modification times, preserve group, preserve owner, preserve device files, preserve special files)

```

rsync -av --delete /media/randy/radio_music/test2/ /Home/Desktop/test1/

```

---

### Post by SeijiSensei on 2012-11-06
First, the "-n" switch that you show in your initial posting tells rsync not to do anything and just list what it would have done to the screen.  As Lars says, you usually just need "-av" if you want to sync and display the list of files being copied.  Without the "v" switch, that list will not be displayed.

And you definitely need two hyphens in front of "delete" ("--delete").  Contemporary command-line programs with lots of options like rsync often use these longer specifications that begin with two hyphens.  There are some programs out there that specify options with a single hyphen, but they are becoming rare.

---

### Post by rmcellig on 2012-11-06
I am going to try out the suggestions and post back. Thanks so much for the help!!

---

### Post by rmcellig on 2012-11-06
Ok, so this is what I have come up with. Still doesn't work.

I did try another rsync that did work so maybe it is something in the path that is not right yet?

rsync -av --delete /mnt/sbd1/musicfromimac/ /mnt/sda9/home/randy/Desktop/recordings

---

### Post by rmcellig on 2012-11-06
I am so embarrassed! I just found my error. I have sbd instead of sdb. The code works fine now but I do have one question regarding the path. Do I have to do a full path to make the code work? I'm still not quite clear on this part.

This is the code that now works:

rsync -av --delete /mnt/sdb1/musicfromimac/aleximurdoch/ /root/Desktop/test  

rsync -av --delete /mnt/sdb1/musicfromimac/ /mnt/sda9/home/randy/Desktop/recordings

---

### Post by Lars Noodén on 2012-11-07
You can use either a relative path or an absolute path, but the path does have to be accurate.

---

### Post by muteXe on 2012-11-07
I'm surprised that using 'Home' and not 'home' in your paths works.

---

