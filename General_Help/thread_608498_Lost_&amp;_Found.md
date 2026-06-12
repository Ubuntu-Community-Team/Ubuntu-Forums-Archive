---
title: "Lost &amp; Found"
date: 2007-11-10
forum: General Help
---

### Post by crazytiredguy on 2007-11-10
Hey, thanks in advance for the advice you're going to give.  I've been toying with the idea of putting Ubuntu on my desktop for a while.  I was running Vista Ultimate, but got tired of it dragging my pretty good system down.  I initially tried to go back to XP but it wouldn't recognize any partition or the hard drive, so I threw Ubuntu on here to just demolish the old partition, try something new and if I didn't like it/couldn't handle it I'd go back to XP Pro.  Now I've got Ubuntu running just fine but my harddrive has huge swaths of data (250 gig hd, almost 200 gig of space used) in a lost + found folder I cannot open or delete.  Is there anything I can do to delete this?

---

### Post by jpkotta on 2007-11-10
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

Did you try```
sudo rm -rf /lost+found/*
```

Be EXTREMELY careful with that command.  In particular, make sure there is no space before the asterisk.

---

### Post by crazytiredguy on 2007-11-10
When I do that it gives me nothing, just a blinking line again.  Am I doing something wrong?  I'm sorry, I'm so new to this its painful.  I was doing it in the terminal, of course.

---

### Post by jpkotta on 2007-11-10
Unix tools speak when told to, or when something goes wrong.  The fact that there was no feedback means it probably succeeded. 

Are the files still there?

---

### Post by crazytiredguy on 2007-11-10
Yes, the folder is still there.  Does it need a restart or anything like that?  This is probably some sort of retarded Vista thing, or something I'm doing thats horribly wrong.  When I installed Ubuntu I repartitioned my hard drive (so I could dual boot, so my wife can use Windows until I get comfortable enough with Ubuntu to help her out) and I don't get why those big chunks of files would still be there even after I took a single partition and deleted it to make multiple partitions.  Thanks for your help, though.  :)

---

### Post by por100pre1 on 2007-11-10
> **crazytiredguy said:**
> Yes, the folder is still there. 

The folder should stay there, the previously posted command should empty the folder, not remove it. The folder is needed by the Linux system, don't try remove it.

---

### Post by crazytiredguy on 2007-11-10
The folder still says it contains 200+ gigs of information.  Is there another command or something I'm doing wrong?  I wish it would allow me to open the folder and view the contents, I'm not sure why it isn't.

---

### Post by por100pre1 on 2007-11-10
Try it this way:

```
sudo su -c 'rm -rf /lost+found/*'
```

**be careful doing this!**

---

### Post by crazytiredguy on 2007-11-10
I did that and it gave me this message.

usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }

Thanks for all the help.

---

### Post by jpkotta on 2007-11-11
Let's try again.

Become root so you can actually see the files.
```
sudo -i
```

Delete the files.
```
rm -rfv /lost+found/*
```

Confirm that the files are actually gone.
```
ls -A /lost+found
du -sh /lost+found
```

Being root for longer than you need to is ill-advised.
```
exit
```

---

### Post by crazytiredguy on 2007-11-12
OK, I followed those instructions.

shawn@shawn-desktop:~$ sudo -i
Password:
root@shawn-desktop:~# rm -rfv /lost+found/*
root@shawn-desktop:~# ls -A /lost+found
root@shawn-desktop:~# du -sh /lost+found
16K     /lost+found


However, when I look in the file system and right click on the lost + found folder it still tells me its ~200 gigs full.  This is making my brain hurt, of no fault to anyone here of course.  Thanks for still attempting to help me.

Jokingly, I want to hold a magnet up to my hard drive and let that solve all my problems :guitar:

---

### Post by jpkotta on 2007-11-12
I would trust du and df above any other tools to get disk usage.  I think the other thing you're using is wrong.  Post the output of df, it will tell you how much free space there is.
```
df -h
```

---

