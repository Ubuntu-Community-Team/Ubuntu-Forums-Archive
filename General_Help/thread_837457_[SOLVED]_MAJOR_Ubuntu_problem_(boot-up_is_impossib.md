---
title: "[SOLVED] MAJOR Ubuntu problem (boot-up is impossible)"
date: 2008-06-22
forum: General Help
---

### Post by S3loth on 2008-06-22
Hello. About a week ago Ubuntu started doing something at the Ubuntu start up splash screen. When it got to 25% it would say something like "Routine drivers check press Esc to skip" when it did this it would get stuck in this, so I always skipped it. Now however it says that x-server failed to load so I can't do anything. If I run it in recovery mode it does the drivers check, so it gets stuck. As a side note, about since the time it started the drivers check Ubuntu takes almost 30 minutes to load. Any help would be much appreciated.

---

### Post by S3loth on 2008-06-22
Bump

---

### Post by spiderbatdad on 2008-06-22
Generally better not to BUMP your own thread before 24 hours has passed.

There is a dedicated "unanswered posts" team who are skilled at problem solving. It makes it difficult to find your post when it has been bumped.

As to your question, not sure. Have you tried to reconfigure xserver?
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by S3loth on 2008-06-22
> **spiderbatdad said:**
> Generally better not to BUMP your own thread before 24 hours has passed.

There is a dedicated "unanswered posts" team who are skilled at problem solving. It makes it difficult to find your post when it has been bumped.

As to your question, not sure. Have you tried to reconfigure xserver?
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Okay, I didn't know that (still getting used to Ubuntu Forums lol)

when I type that in I get 
```
/var/lib/dpkg/info/xserver-xorg.postinst: 1785: cannot create /var/lib/x11/x.roster: Read only file system
```

---

### Post by ginjabunny on 2008-06-22
I think you will find it is a drive check, so fsck is checking the filesystem for errors, be patient it can appear to be stuck and it can take a long time if you have a large drive but I suggest you let it run as it may fix your problem. It not, you may have a hardware problem like a bad block, so download the disk utils from the manufacturers site and scan the disk. If none of that fixes it then you may have corrupted something and you may need a re-install.

---

### Post by spiderbatdad on 2008-06-22
please check to make sure you have a file called /etc/X11/xorg.conf. Try to find it by navigating to it with the file browser. If not goto places>>search for files and type in xorg.conf and select filesystem from the drop down menu.

---

### Post by S3loth on 2008-06-22
Its not a matter of how long I wait for the drivers check. It asks me for my password and then says it failed and goes to a login. I do have the xorg.conf in my X11. What do I do with it?

---

### Post by spiderbatdad on 2008-06-22
nothing lol. from recovery try: ```
su your_username
reconfigure-gdm
```

---

### Post by S3loth on 2008-06-22
Ok, when I do that I get "no such file or directory"
also, i found out why it forces me to check the drivers. It sais that /dev/sda2 contains a file system with errors, check forced. I have no idea what that means though

---

### Post by S3loth on 2008-06-23
Now I can bump, right? lol

---

### Post by S3loth on 2008-06-25
bump

---

### Post by confused57 on 2008-06-25
If you're able to boot into Ubuntu, you might want to post the ouput of:
```
dmesg
```
Be sure to enclose the output in [code]dmesg output[ /code], the output will be fairly long.

You might want to use the Ubuntu live cd and run a filesystem check:
http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem

---

### Post by houstonbofh on 2008-06-25
During one of those checks, it should dump you to a command prompt.  At that point you will need to fsck the drive.  The command will be something like 'fsck /dev/sda1' but whatever partition is broke.  If it does not dump you to a command prompt, boot a Live CD and run it from there.  You can not fsck a mounted partition.

---

### Post by cariboo on 2008-06-25
Start up in recovery mode and unmount your root partition:

```
 umount /dev/hdx
```

then run

```
fsck -a /dev/hdx
```

hdx in both cases is the hard drive that Ubuntu is installed on. You will have to wait until it is finished, so go do something else for a couple of hours. You will not get your sytem running again until your hard drive is repaired.

Jim

---

