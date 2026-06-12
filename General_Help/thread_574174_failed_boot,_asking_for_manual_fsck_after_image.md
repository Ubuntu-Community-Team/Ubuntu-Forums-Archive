---
title: "failed boot, asking for manual fsck after image"
date: 2007-10-12
forum: General Help
---

### Post by Proletariat on 2007-10-12
So I looked through all the threads I could find and found nothing similar to this, so I was wondering if anyone could help here.  I've been using Norton Ghost to create/restore system images on a Dell D600 laptop with Windows XP and Ubuntu.  It has been working great until I updated the Ubuntu side to Feisty (7.04).  The machine which I created the image from works fine, but any subsequent systems which I image fail on boot, with the following error, after successfully
<begin error message>
Activating Swap [OK]:
* Checking root file system

fsck 1.40-WIP (14-Nov-2006)
/dev/sda3: Resize inode not valid.

/dev/sda3: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
fsck died with exit status 4

* An automatic file system check (fsck) of the root filesystem failed.  A manual fsck must be performed, then the system restarted.  The fsck should be performed int he maintenance mode with the root file system mounted in read-only mode.
*The root filesystem is currently mounted in read-only mode.  A maintenance shell will now be started.  After performing system maintenance, press CONTROL-D to terminate the maintance shell and restart the system.  Give root password for maintenance
(or type Control-D to continue):

</end error message>

We ran the manual fsck with like a thousand relocate <Y> answers and it blew up the system to where we couldn't boot without the Live CD (even to Windows).  I also checked the menu.lst file to verify that there wasn't anything funky in there.  I only made one change, which was to move the windows entry up above the linux entry (and to comment out the old Ubuntu version entry), but other than that, no changes.  Does anyone have any suggestions as to where else to begin to start troubleshooting this issue?  I need this machine to work, but currently, there is no critical data I need to keep on the Linux partition.  Lemme know if I need to post fstab data or df data.

Thanks in advance!

---

