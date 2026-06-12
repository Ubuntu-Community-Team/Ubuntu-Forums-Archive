---
title: "help recovering from crash"
date: 2008-01-22
forum: General Help
---

### Post by thespamcatcher on 2008-01-22
I am new to ubuntu ( I used HPUX before I retired over 5 years ago) I have a 4 drive ubuntu gusty system (started from the CD) that was up to date last week, I had a power failure & found out my ups batteries are bad. 

It wouldn't boot & I had to run fsck - looks like something in the boot definitions is missing now - now it goes to command line login and X won't start -
Any suggestions?  it looks like the home dir and other dirs are there at least at the top levels.
is there a ubuntu tool for finding out what files are missing or bad? Or a way to rerun the install but only replace the missing stuff?

OR

would it just be easer to reinstall from the original ubuntu CD and go through the long process of upgrading back to where it was.

The question here is will I be able to tell the install to leave my personal files alone? Most of them are on my Home dir. Hopefully I only need ubuntu system files replaced?

---

### Post by Sef on 2008-01-22
> The question here is will I be able to tell the install to leave my personal files alone? Most of them are on my Home dir. Hopefully I only need ubuntu system files replaced?

If you reinstall, you should be able to leave your home alone.

I would would back up your files before doing anything.  

To check your partitions, from the command line, type this and post the results here:

```
sudo fdisk -l
``` (small L)

---

### Post by thespamcatcher on 2008-01-22
problems, problems - I ran "sudo fdisk -l" and piped the output to a file, but have failed to find a simple way to get the file to the XP machine I am using to post. When I upgraded the ubuntu machine to 7.10 I lost the ability to do file transfers from the XP machine to the ubuntu machine, I had not gotten around to finding out why because I could still get and put files on the XP machine from the ubuntu machine. After the crash I can ping the ubuntu machine from the XP but I see no open ports
and can not find a way to access the XP machine to transfer any files.
(short of burning a CD from the command line - which I don't know how to do in ubuntu - if it even works - I have never tried with 7.10) Oh, yes and when I ping the XP machine from ubuntu it times out, but I can ping the Linksys router ok. 

I did look in the 4 lost and found dirs, only one, under /usr has anthing in it. Don't know how to determine what the files are though.

I did notice that when I rebooted the system it complained about a font file header error problem when shutting down the X window manager - which I did not think was running since it only gave me tty0 to login on.

I am willing to try a few more things looking for a fix in hopes of saving time on an install & upgrade, but it is starting to look like that is what I need to do - although fixing the system would be more rewarding in a learning sense.

Thanks for any help
Dave

---

