---
title: "Floppy drive question"
date: 2007-01-18
forum: General Help
---

### Post by tc101 on 2007-01-18
I think my floppy drive is mounted because I see it listed in Nautilis file manager.  However, when I put an old floppy in it I get a message

Unable to mount the selected floppy drive.
mount: /dev/ is not a block device

I think this is just because the  floppy was formated by windows  in some format ubuntu can't read.  Does this  make sense?  I had a  similar problem with my  CD drive and CDs  created by  windows.

So if  that does make sense, how  can I  reformat the  floppy  so ubuntu can  write to it?

---

### Post by kingmonkey on 2007-01-18
ubuntu should be able to read vfat disks

---

### Post by tc101 on 2007-01-18
Then what does this message mean?

Unable to mount the selected floppy drive.
mount: /dev/ is not a block device

---

### Post by garybrlow on 2007-01-18
I think this is a bug. After installing Ubuntu Edgy this seems to be the default setting for the floppy drive(s).

Open your fstab as root and locate the floppy drive entry. It should like this:

/dev/     /media/floppy0  auto    rw,user,noauto  0       0

Add fd0 after /dev/ and i should look like this:

/dev/fd0     /media/floppy0  auto    rw,user,noauto  0       0

Save the changes to fstab and do one the following:
1)use drive mounting plugin to mount /dev/fd0
2)open terminal and type "mount /dev/fd0"
3)reload fstab
4)restart ubuntu

After the procedures above, the floppy drive should be able to load properly with read and write access.

Cheers!

---

### Post by tc101 on 2007-01-25
I don't understand what you mean when you say

"Open your fstab as root and locate the floppy drive entry."

How do I do that?

---

### Post by dexter on 2007-01-25
> **tc101 said:**
> I don't understand what you mean when you say

"Open your fstab as root and locate the floppy drive entry."

How do I do that?

sudo gedit /etc/fstab

---

### Post by tc101 on 2007-01-25
I did some reading and found the fstab file at etc/fstab.  I found it using the nautalis file browser, clicked on it and opened it with the gedit text editor.  Can I just make the change there and save it?

---

### Post by tc101 on 2007-01-25
Thanks Dexter, your reply slipped in before my second post.

---

### Post by tc101 on 2007-01-25
OK, I made the change I was told to make

> Open your fstab as root and locate the floppy drive entry. It should like this:

/dev/ /media/floppy0 auto rw,user,noauto 0 0

Add fd0 after /dev/ and i should look like this:

/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0


I then did

mount /dev/fd0

and got this message 

mount: /dev/fd0 is not a valid block device

What did I do wrong?  Here is my whole fstab file:






# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=29179f3c-17e7-4a8d-b394-34fbfd39cece /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=60f6ba7d-ac65-484c-957d-f8b7e03f5c62 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by tc101 on 2007-01-25
I also tried

sudo mount /dev/fd0 /mnt/floppy

and got this message

mount: mount point /mnt/floppy does not exist

---

### Post by milton1 on 2007-01-25
try 

sudo mount /dev/fd0 /mnt/floppy0

---

### Post by tc101 on 2007-01-25
It still doesn't work

tomcarr@tomcarr-desktop:~$ sudo mount /dev/fd0 /mnt/floppy0
mount: mount point /mnt/floppy0 does not exist

---

### Post by tc101 on 2007-01-25
Could there be a problem in this line:

/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

Is there supposed to be a comma between auto and rw, so it should look like this:

/dev/fd0 /media/floppy0 auto,rw,user,noauto 0 0

---

### Post by milton1 on 2007-01-25
cd /mnt

sudo mkdir floppy0

---

### Post by milton1 on 2007-01-25
that will make the mount point. Then try mounting again.

---

### Post by tc101 on 2007-01-25
It still doesn't work.  I created the directory and tried to mount it in two different ways.  Both failed:

tomcarr@tomcarr-desktop:~$ cd /mnt
tomcarr@tomcarr-desktop:/mnt$ sudo mkdir floppy0
tomcarr@tomcarr-desktop:/mnt$ sudo mount /dev/fd0 /mnt/floppy0
mount: /dev/fd0 is not a valid block device
tomcarr@tomcarr-desktop:/mnt$ sudo mount /mnt/floppy0
mount: can't find /mnt/floppy0 in /etc/fstab or /etc/mtab
tomcarr@tomcarr-desktop:/mnt$

---

### Post by tc101 on 2007-01-25
Here is my fstab file 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=29179f3c-17e7-4a8d-b394-34fbfd39cece /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=60f6ba7d-ac65-484c-957d-f8b7e03f5c62 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto rw,user,noauto  0       0

---

### Post by milton1 on 2007-01-25
cd /dev

ls fd*

is fd0 listed?

---

### Post by tc101 on 2007-01-25
Yes, it looks like it.  Here is from the terminal window:

tomcarr@tomcarr-desktop:/mnt$ cd /dev
tomcarr@tomcarr-desktop:/dev$ ls fd*
fd0

fd:
0  1  2  3
tomcarr@tomcarr-desktop:/dev$

---

### Post by milton1 on 2007-01-25
OOPS! your fstab calls for the mount on /media/floppy0

I had you make the directory in the wrong place. try

sudo mount /dev/fd0 /media/floppy0

---

### Post by tc101 on 2007-01-25
Still a problem, see below, but do I need to mkdir  /media/floppy0?

tomcarr@tomcarr-desktop:/dev$ sudo mount /dev/fd0 /media/floppy0
Password:
mount: /dev/fd0 is not a valid block device
tomcarr@tomcarr-desktop:/dev$

---

### Post by tc101 on 2007-01-25
I checked and /media/floppy0 already exists, so that is not the problem.

---

### Post by milton1 on 2007-01-25
try

sudo mount -t vfat /dev/fd0 /media/floppy0

---

### Post by tc101 on 2007-01-25
Nope, but please keep trying because I am stumped.  Here is what I got:

tomcarr@tomcarr-desktop:/dev$ sudo mount -t vfat /dev/fd0 /media/floppy0
mount: /dev/fd0 is not a valid block device

---

### Post by milton1 on 2007-01-25
OK, well let's try the obvious questions:

Is the drive plugged in?
Have you tried another floppy?
Have you tried formatting a floppy?

Out of curiosity, what version of ubuntu are you using?

---

### Post by tc101 on 2007-01-25
Milton, I feel like an idiot.  I did not have a floppy in the drive.  I thought mounting meant I was setting up the drive so it could read all floppies.  I did not realize I was mounting a particular floppy.

Thanks for spending so much time helping me with this.

---

### Post by tc101 on 2007-01-25
So does this mean every time I put in a new floppy I have to unmount the old one and mount the new one?  I don't have to do that when I put in a new CD.

---

### Post by milton1 on 2007-01-25
yes. in fact often times data will not be actually written to the floppy until you issue the umount command. if you pull the floppy without unmounting it you can lose data.

also, technically you should unmount and remount cd's as well. The eject option on cd menus includes the unmount process.

---

### Post by milton1 on 2007-01-25
...and you're welcome. I'm happy to help.  :)

---

### Post by tc101 on 2007-01-25
I am new to ubuntu and linux.  I have used windows ever since it first came out.  Maybe I am missing something, but the need to mount and unmount the floppy seems very primitive compared to the way it works in windows.

---

### Post by jdtanner on 2007-02-08
> **tc101 said:**
> I am new to ubuntu and linux.  I have used windows ever since it first came out.  Maybe I am missing something, but the need to mount and unmount the floppy seems very primitive compared to the way it works in windows.

Hi there! I thought I'd chip in here :-) In fact mounting/unmounting is a very safe way of doing things. In Windows you can remove a disk at any time, even if the computer is currently trying to access it. By mounting/unmounting, you remove this problem; I agree that it does seem more difficult when you have to do it the first few times, but you'll get used to it :-D I think the mount/unmount thing stems from the use of tape drives etc in times gone by ;-)

John

---

