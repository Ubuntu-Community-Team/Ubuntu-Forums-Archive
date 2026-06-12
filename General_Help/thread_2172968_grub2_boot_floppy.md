---
title: "grub2 boot floppy?"
date: 2013-09-07
forum: General Help
---

### Post by garyed on 2013-09-07
I'd like to make a bootable floppy that will get me to a grub prompt. 
I use to be able to:
```
sudo grub-mkrescue --overlay=/boot/grub --image-type=floppy grub2.img
sudo dd if=grug2.img of=/dev/fd0

```
and it would work fine but now the command doesn't work. Evidently the newer versions of grub2 changed the commands.
It seems like its designed to make an iso file but not for making a file to fit on a floppy which I know is a little obselete.
I'm using Ubuntu 12.04  but I've got 4 hard drives &  5 different versions of Ubuntu plus Windows & some other distros so its confusing enough to find the right Grub files to begin with.
That's why i just want a boot floppy to get me to a grub prompt so i can manually get to where I want. I have one I made a couple years ago when grub2 first came out & it works but I'm trying to find the commands to reproduce it again. I know i could copy the floppy i already have but I'd really like to know how to make one from scratch.
Any ideas?

---

### Post by oldfred on 2013-09-07
Is the typo in the commands you posted the issue(grug2), or did you just not copy correctly?

I have floppy drive but have not used it more than once or twice, since I built system in 2006. But I have grub2 flash drives with ISO for installs and extra boot stanza to boot hard drives.

I think there were issues on mounting floppy.
 [http://ubuntuforums.org/showthread.php?t=1877488](http://ubuntuforums.org/showthread.php?t=1877488)
[http://ubuntuforums.org/showthread.php?p=11244050#post11244050](http://ubuntuforums.org/showthread.php?p=11244050#post11244050) post #2 coffeecat
Mount floppy from command line - Nautilus often does not work
udisks --mount /dev/fd0
ls /dev/fd*
System->Administration->Users and Groups->Advanced Settings->User Privileges and click on "Use floppy drives"

---

### Post by garyed on 2013-09-07
> **oldfred said:**
> Is the typo in the commands you posted the issue(grug2), or did you just not copy correctly?
................


No, that's just a typo but it has nothing to do with the problem. It's the first command "grub-mkrescue..." where I'm getting the error. I'm not even getting to the "dd..." command now.
Something has changed in the grub-mkrescue command where those switches are no longer valid or at least the way I'm using them any more.

---

### Post by oldfred on 2013-09-07
My notes are slightly different, but I have never run it.

 [https://launchpad.net/ubuntu/oneiric/+package/grub-rescue-pc](https://launchpad.net/ubuntu/oneiric/+package/grub-rescue-pc)
/usr/lib/grub-rescue/grub-rescue-floppy.img
grub-mkrescue --image-type=floppy /tmp/grub-rescue.flp
dd if=/tmp/grub-rescue.flp of=/dev/fd0 bs=1024

   Basically the grub-mkrescue copies Grub2 image into the specified file and you use the dd command to write the same onto a floppy. For a bootable Grub2 CD the instructions are

Image still is here with 12.04:
      
 /usr/lib/grub-rescue/grub-rescue-floppy.img

---

### Post by garyed on 2013-09-07
The only thing that works for me so far is ```
sudo grub-mkrescue -o grub2.iso  
``` I haven't tried to burn a CD with it but it does make the file.
With this code ```
 sudo grub-mkrescue --image-type=floppy /tmp/grub-rescue.flp  
``` I get the error >  output file must be given
 

---

### Post by Anthon on 2013-12-01
I have have been trying to create a boot floppy for a computer with CD but without boot option from CD as well. 
After downloading and compiling grub 2.00 and xorriso 1.3.2 you can use the command:

[FONT=Courier New]grub-mkrescue --compress=xz -o /data1/ISO_IMAGE/Linux/grub-rescue.vfd[/FONT]

but that still results in a 4.4Mb image, unusable for writing on a 1.4Mb floppy. The [FONT=Courier New]--diet[/FONT] and [FONT=Courier New]--image-type[/FONT]
are no longer supported, so doing anything special (apart from compression) for floppy is unclear.

I think I will concentrate how to get a grub2 image to boot from grub1 based floppy.

---

### Post by oldfred on 2013-12-01
Herman has some info on floppy drives with grub legacy & grub2.
I prefer USB or CD drive which he also has info on his site.

grub legacy
[http://members.iinet.net.au/~herman546/p15.html#grub_floppy_howto_make](http://members.iinet.net.au/~herman546/p15.html#grub_floppy_howto_make)
Grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_Floppy_Disc](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_Floppy_Disc)

---

### Post by Anthon on 2013-12-01
Have you tried any of that before you posted? At least the stuff [http://members.iinet.net/~herman546/...B2_Floppy_Disc](http://members.iinet.net/~herman546/...B2_Floppy_Disc) does not work.

The first command with grub2 you will get the message that [FONT=Courier New]--overlay[/FONT] is an unrecognized option (on grub 2.0)

---

### Post by oldfred on 2013-12-01
I have not used floppy disk for years. I much prefer flash drives. I use Herman's commands to create those.

 But is system is that old you may need grub legacy anyway?

This thread said it worked with grub2 but it would have been an older version of grub2. I am suprised a parameter has been removed. Maybe it was just ignored in the older version?
[http://ubuntuforums.org/showthread.php?t=1305475](http://ubuntuforums.org/showthread.php?t=1305475)

---

