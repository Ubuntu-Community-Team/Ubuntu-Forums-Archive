---
title: "Xubuntu Not Booting, Uninitialized Random Read Error"
date: 2018-01-05
forum: General Help
---

### Post by videogame500 on 2018-01-05
[FONT=verdana]I recently got my Xubuntu install working just how I wanted it, and I was really happy that I could finally use Linux again![/FONT]
[FONT=verdana]However, I noticed that my install often stays at a black screen for long after passing GRUB, but the first two times I booted up, it eventually moved onto the LightDM greeter (Though oddly enough, not before chiming the post sound from the PC speaker again).[/FONT]
[FONT=verdana]This morning, however, I tried to boot, and the black screen never went away. Booting again in verbose mode, and I saw that the last bit of code to be displayed was this:[/FONT]
[FONT=verdana]"[0.770602] random: systemd-udevd: uninitialized urandom read (16 bytes read)[/FONT]
[FONT=verdana]And then nothing happens. My computer is using an NVidia GTX 760 graphics card, and I can confirm that its drivers installed correctly and allowed me to boot at least once.[/FONT]
[FONT=verdana]Here is a screenshot of the verbose boot: [https://i.imgur.com/0w4Jqhk.jpg](https://i.imgur.com/0w4Jqhk.jpg)[/FONT]

---

### Post by videogame500 on 2018-01-08
Any ideas on this? I still can't get the install to boot.

---

### Post by Bashing-om on 2018-01-08
videogame500; Hello;

We have the system screaming and hollering ; mounting the file system "read only"

In this event the 1st thing I would do is check/repair the file system:
```

sudo parted -l # to identify the target root partittion
#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see: man e2fsck
sudo e2fsck -f -y -v /dev/sda1
fsck http://www.thegeekstuff.com/2012/08/fsck-command-examples/

```

we see here
[INDENT][INDENT]what is
[/INDENT][/INDENT]

---

### Post by videogame500 on 2018-02-05
> **Bashing-om said:**
> videogame500; Hello;

We have the system screaming and hollering ; mounting the file system "read only"

In this event the 1st thing I would do is check/repair the file system:
```

sudo parted -l # to identify the target root partittion
#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see: man e2fsck
sudo e2fsck -f -y -v /dev/sda1
fsck http://www.thegeekstuff.com/2012/08/fsck-command-examples/

```

we see here[INDENT][INDENT]what is
[/INDENT]
[/INDENT]

[LEFT][COLOR=#222222][FONT=Verdana]When I use this to check and repair the filesystem, it says that there are no errors and it does not seem to change anything. :([/FONT][/COLOR][/LEFT]

---

### Post by Bashing-om on 2018-02-05
videogame500;

> 
and it does not seem to change anything


Still booting read only ? What errors are reported ?

What do you boot to ? 

[INDENT][INDENT]hardware issues ?[/INDENT][/INDENT]

---

### Post by videogame500 on 2018-02-06
The same errors appear now as did in the screenshot I posted in the first post, unfortunately. :(

---

