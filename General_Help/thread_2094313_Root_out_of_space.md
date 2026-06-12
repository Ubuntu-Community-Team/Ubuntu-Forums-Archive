---
title: "Root out of space"
date: 2012-12-13
forum: General Help
---

### Post by adocholiday on 2012-12-13
My root partition is only 8GB. I was following instructions for partitioning and this was recommended. It's now saying that it is full and I know it is because I have installed some programs to the /opt folder. I can't even install updates anymore.

Can I move these programs to my home directory (67GB) to get back some of the disk space? I really don't want to have to reinstall ubuntu as it took me ages to set it up the first time. 

Really appreciate some help with this. Thanks

---

### Post by Cheesemill on 2012-12-13
You can't really move installed programs, you best option is probably to resize your partitions from a Live CD.

Can you run gparted (you may need to install it first) and post a screen shot.

---

### Post by Kirk Schnable on 2012-12-13
> **Cheesemill said:**
> You can't really move installed programs, you best option is probably to resize your partitions from a Live CD.

Can you run gparted (you may need to install it first) and post a screen shot.

I will second this. ^

While it may be possible to move your applications, it will be easier and better to just resize your partitions. 

You can use Gparted on a Ubuntu Live CD, or you can get the Gparted Live CD ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)). 

Here are some instructions to help you with your partition resizing:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by Rexilion on 2012-12-14
Instead of resizing, why not move the /opt/program to the usershome like this:

```
mv /opt/program /home/opt/program
```

and create a symlink?

```
ln -s /home/opt/program /opt/program
```

That way everything keeps working without having to resize partitions...

What did you install in opt anyway?

---

### Post by Kirk Schnable on 2012-12-14
> **Rexilion said:**
> Instead of resizing, why not move the /opt/program to the usershome like this:

```
mv /opt/program /home/opt/program
```

and create a symlink?

```
ln -s /home/opt/program /opt/program
```

That way everything keeps working without having to resize partitions...

What did you install in opt anyway?

In general this will work okay... But I don't always like to put my faith in symlinks. 

Personally, if I just wanted to permanently move /opt to my /home partition, I would...

1. Move all the files. 
```
mv /opt/ /home/opt/
```

2. Use a bind mount to mount the new location to /opt/
```
mount --bind /home/opt /opt
```

3. Permanently add a line to /etc/fstab so this mount automatically happens at boot. 
```
# Add to /etc/fstab file. 
/home/opt    /opt   none    bind  0  0
```

From then on, anything and everything in /opt will be stored in /home/opt, taking up space on the home partition. The /opt folder will still simultaneously exist. I believe this is cleaner behavior than making symlinks.

---

