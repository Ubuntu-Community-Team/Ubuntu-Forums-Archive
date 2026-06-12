---
title: "&quot;Your drives need to be checked&quot; at every startup"
date: 2013-04-03
forum: General Help
---

### Post by chk1827 on 2013-04-03
I am using Ubuntu 12.04(fresh install), installed on an external HDD.

Somewhere along the line(while installing gnome3, kde, cinammon, xubuntu-desktop, lubuntu-desktop, and mate...using them for a couple of days...and then unstalling gnome3,cinammon,lubuntu-desktop)...i dont exactly know when, or if it was before/after installing/removing above items, that i got the message which has been reappearing ever since:"Checking disk drives for errors..This may take several minutes"..it checked the drives , reported no errors and loaded ubuntu. Thereafter at every boot the message appeared and it found no errors and loaded. Finally i got fedup of it and i pressed 'C' to 'cancel the disk checks' and it showed 'errors were found while checking the disk drive for \"..i pressed 'I' to ignore and it loaded ubuntu..I have been doing that at every boot now.

I tried tunefs -l on my root drive,and it showed that the max mount count=-1 so i set it to 30, however i did this from inside ubuntu while the disk was mounted, and it had no effect whatsoever,it still shows the error(even after the disk had been checked after altering max count)

To furthur complicate matters, I accidently brushed against my external HDD; its connection is very sensitive so it got disconnected while logged on in ubuntu and i had to force shut the system.

When i restarted the "Your drives need to be checked for errors" came up and checked the whole disk and said errors were found with your / drive, press F to fix them or M for manual recovery..i pressed F it did something and then restarted.

After that i got the "The system is running in low graphics mode" 'Your screen,graphics card and input device settings could not be detected correctly.You wil have to configure these yourself.'(I have posted a seperate thread for it [http://ubuntuforums.org/showthread.php?t=2131844&p=12586028#post12586028](http://ubuntuforums.org/showthread.php?t=2131844&p=12586028#post12586028))

So could anyone tell me how to correct this problem so that it does'nt unnecessarily check the drive at every boot?

I have separate partitions for /boot (512mb ext2), / (8.5gb ext3), /home (9.5gb) and swap(2gb).

---

### Post by katanacb on 2013-04-03
A few things here.

Is the system checking *every* filesystem when you restart your computer, or just a few of them (if you don't know how to tell, just reply back and I'll walk you through that)?

I'm thinking that the problem may be something to do with when your computer shuts down it's not unmounting things properly, and hence wants to do an fsck at every startup.

---

### Post by chk1827 on 2013-04-03
First it shows 1 which quickly changes to 2 and sometimes 3 (this is displayed on the bootup page where the"Your drives need to be checked" message comes up.."Checking drive 1 of 2 or 1 of 3")...but i think the main problem is with the / drive because whenever i cancel it it shows device for / is not ready...also during fsck in recovery mode it showed boot and home as clean but found errors with the root device.
But yeah if you could tell some sure way of finding out if its checking 1 or more drives that would be most welcome.

---

### Post by katanacb on 2013-04-04
I'm guessing that when the machine shuts down that it's not unmounting / properly.  Do you get any error messages when you shut the machine down or reboot it about a filesystem being busy..?

You could check the system log and see what is being checked when you boot.  something like:

$ grep sda /var/log/syslog* 

might be helpful ... see if anything comes out of that command in reference to 'checking filesystem' or something of the sort.

---

### Post by chk1827 on 2013-04-04
No i dont get any error messages at shutdown...anyways thanks for the help i am thinking of reinstalling.

---

### Post by davidvandoren on 2013-04-05
It might have to do with the user.rules file in /etc/udev/user.rules.

Open the terminal and type or paste and copy
> 
gksudo /etc/udev/user.rules

If that file is empty, enter a # save and close the file.
This was a problem that existed with Ubuntu 10.04. I don't know how this happened but the above was the fix. 
Tell us if it worked.

---

### Post by katanacb on 2013-04-16
Curious if OP is still having this problem?

---

### Post by dcstar on 2013-04-16
> **chk1827 said:**
> I am using Ubuntu 12.04(fresh install), installed on an external HDD.

Somewhere along the line(while installing gnome3, kde, cinammon, xubuntu-desktop, lubuntu-desktop, and mate...using them for a couple of days...and then unstalling gnome3,cinammon,lubuntu-desktop)...i dont exactly know when, or if it was before/after installing/removing above items, that i got the message which has been reappearing ever since
..........

Something has probably broken the shutdown scripts in that myriad of things that you have installed and uninstalled so you never get a clean shutdown any more.

Find a set of good scripts in another system and copy them to yours, or try and manually fix them or do a reinstall:

```
/etc/rc0.d
/etc/rc6.d
```

The important things are the filenames which determine the exact order in which each is executed, if these have been scrambled then the power-off/reboot script can be run before the unmount script and you have this sort of problem.

---

### Post by chk1827 on 2013-04-20
I think this problem is not only linked to installing and uninstalling the packages...i had this problem before also with installation on my external HDD whose connection gets disturbed very easily...

---

### Post by chk1827 on 2013-04-20
> **davidvandoren said:**
> It might have to do with the user.rules file in /etc/udev/user.rules.

Open the terminal and type or paste and copy


If that file is empty, enter a # save and close the file.
This was a problem that existed with Ubuntu 10.04. I don't know how this happened but the above was the fix. 
Tell us if it worked.

On viewing my root filesystem on windows with ext2fsd, i find that there's no file named user.rules in /etc/udev
there's a file udev and a folder rules.d which has 3 files... 70-persistant-cd, 70-persistant-net, and README
all of these files have something written in them.

---

### Post by chk1827 on 2013-04-20
> **dcstar said:**
> Something has probably broken the shutdown scripts in that myriad of things that you have installed and uninstalled so you never get a clean shutdown any more.

Find a set of good scripts in another system and copy them to yours, or try and manually fix them or do a reinstall:

```
/etc/rc0.d
/etc/rc6.d
```

The important things are the filenames which determine the exact order in which each is executed, if these have been scrambled then the power-off/reboot script can be run before the unmount script and you have this sort of problem.

On viewing my root filesystem on windows with ext2fsd, i think the rc0.d and rc6.d are correct..
in rc0.d umountfs and umountroot occurs before halt...and in rc6.d both occur before reboot.

---

### Post by chk1827 on 2013-04-20
Thanks to the people who've been replying to the posts :)

---

