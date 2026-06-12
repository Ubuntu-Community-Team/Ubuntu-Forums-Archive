---
title: "Auto mount NTFS (Windows) partition"
date: 2007-10-27
forum: General Help
---

### Post by jklarsen on 2007-10-27
Hi,

I have installed Ubuntu 7.10 on my laptop doing the multiboot with XP.
My Xp disk normally automounts as SDA1. But not it only mounts sometimes,
which is quite annoying.

I can see that SDA1 is present in FSTAB as -

# /dev/sda1
UUID=7684F56684F5296F /media/sda1     ntfs    defaults,umask=007,gid=46 0       1


I am fairly new to linux/ubuntu so i dont really know what to do and where to look.

So if you have any help/tips that would help.

Best...Jan

---

### Post by taurus on 2007-10-27
What is the error message when you run this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo mount -t ntfs /dev/sda1 /media/sda1
```
I bet you didn't shut down Windows cleanly and the error message tells you to do it.

So, boot up Windows and shut it down properly, no hibernating stuff, and see if Ubuntu can mount it now.

---

### Post by jklarsen on 2007-10-27
Hi and thank you for a quick reply.

Actually i didn't consider that if windows didn't shut down correctly, that that might introduce problems, so that might be it.

I read somewhere that it is not recommended that i write to the NTFS disk from ubuntu,
is this still true? because i still keep all of my data files on the NTFS disk.


Best...Jan

---

### Post by taurus on 2007-10-27
Right now, you can't write to your ntfs partition since you are using ntfs driver.  If you want to write to it, you need to install and use ntfs-3g instead and yes, it is safe to write to ntfs now.

Run the command from my previous post and see what the error message is.

---

### Post by jklarsen on 2007-10-28
I get this error

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0

And when windows is shut down correctly the SDA1 mount correctly, so you were right ;-)

Thank you for your help!

Best...Jan

---

### Post by .Ix on 2007-11-10
i have this same error, except that i got it from some bug with the Windows XP installer. i've been running win XP for the longest time on this computer but i wiped the HD and installed ubuntu. then i tried to run the winXP installer (i thought i'd just do the dual boot afterwards) and it went nuts. something about "ntdll.dll" i think? Ubuntu can't read or mount the ntfs partition anymore, and i can't do a clean shutdown since i can't run windows in the first place. 

help anyone? ;_;

---

