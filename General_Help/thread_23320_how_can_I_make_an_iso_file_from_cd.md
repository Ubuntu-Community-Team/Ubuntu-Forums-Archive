---
title: "how can I make an iso file from cd?"
date: 2005-04-01
forum: General Help
---

### Post by valter on 2005-04-01
can someone pleas tell how can I make an iso file from cd? any command for that or application?

---

### Post by Juergen on 2005-04-01
For data cds:
```
dd if=/dev/cdrom of=bla.iso
```

---

### Post by Buffalo Soldier on 2005-04-01
Post #6 from the [can i copy a cd under Ubuntu? if so, how?](http://ubuntuforums.org/showthread.php?t=12462&) thread. [QUOTE=wayover13]Well, here's a temporary workaround. It involves going to the command line. Hopefully someone will have a suggestion for a program that will work where those I've tried have failed, or a solution to get the programs I do have (Gnome's CD burner, xcdroast or bashburn) working.

To copy a CD, we'll take the extra step of making an iso from the CD, storing it on the hard drive, then burning it with our CD burning prog of choice. Though it involves some convolution, it's still fairly simple.

Insert the CD to be copied into your CD drive. Gnome will automount it, which we'll have to undo. To unmount the CD you've just inserted, open a console and issue ```
 umount /media/cdrom0 -l
``` That will leave your CD in the drive, but with its filesystem unmounted--which is what we want. Then, you create the iso from the CD. In this case, we need to give the device file name for the CD drive, and use the command line program dd (disk dump). dd requires root/superuser privileges (most likely), so we'll sudo to use it, like so: ```
sudo dd if=/dev/hdc of=piratedM$OS.iso
``` This will make an iso of the CD called piratedM$OS.iso in the pwd (present working directory) where you issued the command from. Now, use your favorite burning app--including Gnome's lousy excuse for a burning prog--to burn your iso to a CD. Worked fine for me.

Notes:

1) /media/cdrom0 happens to be the mount point for the CD reader in my machine. Yours may be different: issue the mount command from the CLI to find out the mount point for yours and substitute accordingly.

2) /dev/hdc is the device file for my CD reader. Yours may be different. Again, use mount to find out the device file name for yours and modify my example code accordingly.

3) feel free to substitute sunos, os-2 or the name of the proprietary OS you're pirating in place of piratedM$OS in my example :)

4) you can name the iso file you're creating whatever you want (within Unix file naming conventions), and it doesn't matter what the extension is--or even whether there is one at all. It might be more coherent for you (or your dippy M$ burning software) if you give it an extension like .iso or .img or the like, but it's not necessary.

James[/QUOTE]But I'm a lazy person. So the app that I used is [Graveman](http://graveman.tuxfamily.org/). It's in the universe repository.

---

### Post by bored2k on 2005-04-01
[QUOTE=valter]can someone pleas tell how can I make an iso file from cd? any command for that or application?[/QUOTE]
 [How to create Image (ISO) file from CD/DVD?](http://ubuntuguide.org/#createisofilefromcddvd)

---

### Post by valter on 2005-04-02
Thank all of you very much  :)

---

### Post by danja on 2005-04-05
[QUOTE=Juergen]For data cds:
```
dd if=/dev/cdrom of=bla.iso
```[/QUOTE]

I've managed this now too, but any chance of an insight into burning the iso back to a blank cd now please?

Much appreciated...

Dan

---

### Post by Juergen on 2005-04-05
In short somewhat like (maybe other device):
```
cdrecord dev=/dev/hdc blah.iso
```but cdrecord has much more options that you probably want to use, so before you do something please read `man cdrecord`

Or look at all the gui-frontends to cdrecord like gcombust, xcdroast (K3b or arson if you don't mind installing KDE-libs)...
They should have an option to 'burn a CD-image'

---

### Post by Buffalo Soldier on 2005-04-05
[QUOTE=danja]I've managed this now too, but any chance of an insight into burning the iso back to a blank cd now please?

Much appreciated...

Dan[/QUOTE]Right click on the file and click **Write to disc...**

---

