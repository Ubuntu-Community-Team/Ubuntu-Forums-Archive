---
title: "Transferring Files from Xenix Op Sys"
date: 2008-01-07
forum: General Help
---

### Post by LGM on 2008-01-07
I have to transfer a large number of files that are stored on a 486 computer running SCO Xenix System V, ver 2.2.4 of 1988 to a computer with Dapper Drake, running GRUB in a triple boot mode.

A vast  majority are ASCII files written using vi, that are  in many directories and sub-dirs and most have file names longer than eight characters, which I want to preserve.   Dapper can't read Xenix-formatted diskettes.  I could copy the vi files to 3.5" DOS-formatted diskettes but it would be a very long, time-consuming process and I'll have to rename the truncated file names once I get them onto the Linux system.

Is there any faster way to transfer the vi files from this old computer running Xenix to my modern computer with Linux?

---

### Post by danwood76 on 2008-01-07
Does your 486 machine have a network card of any kind?

Using a network system would be the best method, but im unsure of SCO Xenix as I have never used it.

If you are able to read a common disk format between the two that allows long file names etc you could get another hard disk, format it in that format, transfer the files and just connect that to your newer system.

I think you will have problems doing the transfer as obviously that old PC is nearly 20 years old.

---

### Post by netztier on 2008-01-07
> **danwood76 said:**
> Does your 486 machine have a network card of any kind?

Using a network system would be the best method, but im unsure of SCO Xenix as I have never used it.

If you are able to read a common disk format between the two that allows long file names etc you could get another hard disk, format it in that format, transfer the files and just connect that to your newer system.

I think you will have problems doing the transfer as obviously that old PC is nearly 20 years old.

I agree that the network way is probably the best. If a NIC is not available as such, I suggest thinking about using a SLIP or PPP IP connection over serial line resp. null modem - so you can talk TCP/IP from one system to another. Like this, you can start using ftp, tftp or any other IP-based file transfer service, depending what you find on the old system.

You might be hindered by bit rate limitations of the old serial line chips that were often used in those days (9600bps max), but if the data is so valuable that it must be preserved, time should not be an issue, even if it literally "takes all night".

Another way might be to use [UUCP]("http://en.wikipedia.org/wiki/UUCP") over the serial line - I think it is still supported (or at least installable) in Linux, and probably is available on your old Unix system as well. As little as I know about it, I think it used to be **THE** data transfer mechanism of choice in the "olden days". By doing some Web research, you should be able to find howto's to set up UUCP with Linux.

regards

Marc

---

### Post by LGM on 2008-01-08
> **danwood76 said:**
> Does your 486 machine have a network card of any kind?

Using a network system would be the best method, but im unsure of SCO Xenix as I have never used it.

If you are able to read a common disk format between the two that allows long file names etc you could get another hard disk, format it in that format, transfer the files and just connect that to your newer system.

I think you will have problems doing the transfer as obviously that old PC is nearly 20 years old.


My 486 doesn't have a network card and at this point I don't want to even open the box to do anything to that might disturb the hardware.  I've realized for quite a while that I'm living on borrowed time with that computer.  However, since 1988, when Xenix was installed and fine-tuned, the system has performed flawlessly, which is more than I can say for any of the Microsoft op systems I've used.

On the 486 I have a Scorpion tape drive, (of a similar vintage), but I doubt that would be compatible with Dapper.  I think the only applicable interface between the two machines would be the serial port.

---

### Post by netztier on 2008-01-08
> **LGM said:**
> On the 486 I have a Scorpion tape drive, (of a similar vintage), but I doubt that would be compatible with Dapper.  I think the only applicable interface between the two machines would be the serial port.

You might want to find out what serial chips the machine is equipped with. The classical PC hardware chip was 8250 UART, later on replaced by the 16550, where the former can't really go beyond 9600bps. 

A serial null modem and UUCP literature might be your companions for the next few days :-)
I am pretty positive that this system has UUCP capabilities already built-in.

best regards

Marc

---

### Post by LGM on 2008-01-08
> **netztier said:**
> You might want to find out what serial chips the machine is equipped with. The classical PC hardware chip was 8250 UART, later on replaced by the 16550, where the former can't really go beyond 9600bps. 

A serial null modem and UUCP literature might be your companions for the next few days :-)
I am pretty positive that this system has UUCP capabilities already built-in.

best regards

Marc



Thanks Marc for your most helpful suggestions.  After your first post I went online re UUCP, as I think that's the way to go.  I have all the SCO Xenix manuals but it's been a very long time since I've had to think about UUCP, null modems, RS232 cables and the like, (for which I'm very grateful).  My interest has always been on the software side and in particular database design.

I've flipped through the section on UUCP in the Xenix manual, and also searched on the net for articles, but the explicit steps I need to do to get UUCP functioning between the two machines are not yet obvious to me.  A lot of the articles are aimed towards modems and email.  

The max data transfer rate from Xenix is certain to be very slow.  Is that going to make any difference to Linux?  Will it just wait patiently for the next bit or fall asleep due to lack of activity or boredom?

I was hoping that some one who has used UUCP this way, (maybe not for sending info from a Xenix machine but for something comparable), would post and could give me a roadmap on what the steps are.  I know from past experience how one dumb error can take days to track down and correct; at this point I begrudge spending a lot of time relearning what I knew (to some degree) twenty years ago.  ;)

If you know of any reference with more or less step-by-step instructions on how to implement UUCP for my purpose I would very much appreciate it.
Thanks,
LGM

---

### Post by dcstar on 2008-01-09
> **LGM said:**
> I have to transfer a large number of files that are stored on a 486 computer running SCO Xenix System V, ver 2.2.4 of 1988 to a computer with Dapper Drake, running GRUB in a triple boot mode.

A vast  majority are ASCII files written using vi, that are  in many directories and sub-dirs and most have file names longer than eight characters, which I want to preserve.   Dapper can't read Xenix-formatted diskettes.  I could copy the vi files to 3.5" DOS-formatted diskettes but it would be a very long, time-consuming process and I'll have to rename the truncated file names once I get them onto the Linux system.

Is there any faster way to transfer the vi files from this old computer running Xenix to my modern computer with Linux?

You can probably compile a kernel with Xenix filesystem access turned on - I'm pretty sure that I've seen this in the options.

The other options would be to create a partition with a filesystem that Xenix and Ubuntu can both use, and then use that as an intermediately.

---

### Post by netztier on 2008-01-09
> **dcstar said:**
> 
The other options would be to create a partition with a filesystem that Xenix and Ubuntu can both use, and then use that as an intermediately.

Which still leaves the problem of how to get a physical medium containing such a file system from one system to the other.

If the OP is lucky, the old server has SCSI disks - finding a simple PCI SCSI controller and adding the disk from the old system to the new one could turn out as the fastest and most comfortable way - but has the disadvantage in that it includes physical intervention on the old machine. This might not be a viable option.

The only other way might be floppies - provided the OP has a floppy drive to use with the Ubuntu system.

Still - complicated as it might be - I think UUCP is the way to go, provided the Xenix system has UUCP support installed.


best regards

Marc

---

### Post by LGM on 2008-01-09
> **netztier said:**
> Which still leaves the problem of how to get a physical medium containing such a file system from one system to the other.

If the OP is lucky, the old server has SCSI disks - finding a simple PCI SCSI controller and adding the disk from the old system to the new one could turn out as the fastest and most comfortable way - but has the disadvantage in that it includes physical intervention on the old machine. This might not be a viable option.

The only other way might be floppies - provided the OP has a floppy drive to use with the Ubuntu system.

Still - complicated as it might be - I think UUCP is the way to go, provided the Xenix system has UUCP support installed.


best regards

Marc


Both computers have 3.5" diskette drives but the Ubuntu system can not read diskettes that are _Xenix-formatted_.  If  I knew how to add this capability to Ubuntu that would be the best fallback method if I can't get UUCP running.   I agree that UUCP is by far the best method.

On the Xenix system, I can format diskettes for DOS and these can be read by Ubuntu.  Only problem is that the file names are truncated to eight characters, which is a real pain.  The meaningful part of the name is often lost, etc.  I can rename each file once it is on the Ubuntu system but I have several thousand files, so this is not a pleasant option.
Thanks,
LGM

---

### Post by dagnabit dang doohickey on 2008-01-09
For the floppy method: archive the files in a tarball to preserve the long file names.

---

### Post by netztier on 2008-01-10
> **LGM said:**
> Both computers have 3.5" diskette drives but the Ubuntu system can not read diskettes that are _Xenix-formatted_. 

I did a bit of research and found that Xenix seemed to use the sysv format for diskettes.

After reading **man filesystems** and checking the contents of **/proc/filesystems**, I am pretty sure you can add sysv support by issuing the **sudo modprove sysv** command.

Put the floppy in the drive and mount with a command like:

```
 mount -t sysv /dev/floppy /media/floppy 
```

which should just about make the floppy icon appear on your desktop.

Good Luck!

Marc

---

### Post by LGM on 2008-01-11
> **netztier said:**
> I did a bit of research and found that Xenix seemed to use the sysv format for diskettes.

After reading **man filesystems** and checking the contents of **/proc/filesystems**, I am pretty sure you can add sysv support by issuing the **sudo modprove sysv** command.

Put the floppy in the drive and mount with a command like:

```
 mount -t sysv /dev/floppy /media/floppy 
```

which should just about make the floppy icon appear on your desktop.

Good Luck!

Marc


It certainly seemed that your mount suggestion should do it -- but it didn't.  The first statement by mount was that the diskette was "write-protected, mounting read-only" which was true and at least indicated that mount found the diskette

However, mount then reported:
"wrong fs type, bad option, bad superblock on /dev/fd0
missing codepage or other error"

dmesg | tail told me
"VFS: unable to find oldfs superblock on device fd0"

While searching the net a week ago I came across a thread (which I've not been able to find again), that I think said that Linux was not supporting the very old Xenix fs.  Xenix went through many major versions, and it may be that the sysv on Ubuntu corresponds to one Xenix used on more modern computers.  My Xenix System V ver 2.2.4 came out in 1988 and ran on an 80286.  I now have it running on a 80486.

While searching the net tonight I found a post by someone who had SCO Xenix 2.3.x , (for 80386) and wanted to get his user files onto his Ubuntu system.  He installed the Xenix HD in the Linux box and used "mount -t sysv  ..."  to mount the HD - he got the same error msg I did.

Thanks for taking the time to research this.  Guess my next step is to find the necessary cable and try to get UUCP going.
LGM

---

### Post by dcstar on 2008-01-12
> **LGM said:**
> 
.........
Thanks for taking the time to research this.  Guess my next step is to find the necessary cable and try to get UUCP going.
LGM

If you have the SCO install disks, you may want to try installing a Xenix VM in something like VMware (on the Ubuntu box) and use that to read your floppy disks.

---

### Post by LGM on 2008-01-14
> **dagnabit dang doohickey said:**
> For the floppy method: archive the files in a tarball to preserve the long file names.

Creating a tarball to preserve the long file names sounded like a great solution but when I tried it on a small sub-directory I found out that my 2.2.4 version of Xenix doesn't have the -z option for tar.  

I have the set of SCO Xenix manuals.  It does have commands pack and unpack which are used to compact a file in place.  The replaced file is renmaed "file.z".  

The more I've search the net the more posts I find of those who have run into roadblocks trying to work with my version of Xenix and Linux.  I think 2.2.4 is comparitively primitive; it was a stripped down version of Unix for business end users and SCO may even have customized it for the Tandy computers.  

I've also found posts relating  to problems using UUCP to connect to Linux.  Aaarrgghh!  Thanks to all for your suggestions.  I'm still hoping for a reference to a post by someone who was successful in transferring Xenix files to Linux.
LGM

---

