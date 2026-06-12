---
title: "Move my home directory.. (Solved)"
date: 2006-10-20
forum: General Help
---

### Post by katana6434 on 2006-10-20
Hi

I have recently added a hard drive to my system with the intention of using it to store my personal files, instead of it being on the same drive as the operating system.

I am assuming that I need to change the location of the \home directory and mount it on the new hard drive.  How do I achieve this?

Thanks in advance.

Cheers

---

### Post by glug101 on 2006-10-20
Here is how I would do it:

1. Mount the new hard drive to a new folder that you create.

2. Copy all files from your $HOME directory into the new drive/folder.

3. Unmount the drive and edit your /etc/fstab so that the drive maps to your $HOME directory.

4. Reboot.

You might need to do a chown -R userid on your home folder after this, but the end result will put the new drive on your system at your $HOME directory and not destroy any of your old files.  Once you are satisfied that the new drive is working correctly, you can manually unmout the drive and delete the contents of your old $HOME folder to reclaim the space.

Now, this is just a rough outline.  If you need help with the individual steps just post here and I'll help you as much as I can.

Welcome to the world of system maintenance ;)

---

### Post by aysiu on 2006-10-20
Follow these instructions:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by katana6434 on 2006-10-20
OK, going to need a bit of help here with the commands to use.

I don't need to copy over any files as basically this is a new installation, so I just need to mount the new hard drive as /home.

What do I need to type for this?

---

### Post by katana6434 on 2006-10-20
Cheers aysiu

I will have a look into it.

---

### Post by katana6434 on 2006-10-20
Thanks guys

This worked a treat.  Now if only I understood what I done.

I think I understand everything apart from that one long command.

> find . -depth -print0 | sudo cpio --null --sparse -pvd /new/

I'm assuming that it was this command that copied the data over from the old home drive to the new.

Does anyone mind trying to explain that command to me?

Cheers

---

### Post by aysiu on 2006-10-20
Apparently, it's from [here](http://www.us.debian.org/doc/manuals/reference/ch-tips.en.html#s-archiving): > 8.3.5 cpio

cpio copies files into or out of a cpio or tar archive. The archive can be another file on the disk, a magnetic tape, or a pipe.

     ```
$ find . -depth -print0 | cpio --null --sparse -pvd new-dir
``` I don't know what it does either... only that it works.

---

### Post by glug101 on 2006-10-24
I have a basic description/breakdown of the command to add to aysiu's already excellent help:)  I'm only putting this here because I think that there are important bits in the command that I wish somebody would have shown me when I started out.

Basically, cpio is a more capable version of the cp command.  cpio is usually used to place files into a tar file for backup purposes.  Essentially, the command find is being used to create a list of files to be transferred and the '|'(which is called a 'pipe' and shouldn't be confused with an l or a 1 ;)) is being used to transfer that list to 'cpio' without creating a file.  

A more detailed description can be found here:

[http://www.gnu.org/software/cpio/manual/](http://www.gnu.org/software/cpio/manual/)

Cheers!  Hope this helps sombody:)

---

