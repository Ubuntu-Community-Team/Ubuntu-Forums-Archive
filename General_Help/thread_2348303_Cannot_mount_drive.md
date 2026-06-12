---
title: "Cannot mount drive"
date: 2017-01-02
forum: General Help
---

### Post by spodeworld on 2017-01-02
Hi.

Brand new LINUX user here.

I created a bootable UBUNTU USB drive with 16.04 so that I could boot into a PC with a damaged boot HDD (Windows 10), but fails to boot,to see what files might be recoverable.

I booted successfully off the UBUNTU USB and when I got to the window that looks a lot like File Explorer I saw, 1TB Ext Bay1 (which contains an external HDD that is working), Computer and Gateway (which is my machine).

I wanted to see if the files on the C drive were still accessible.

It appears that Windows 10 is in hibernation mode and I need to get it out of that mode and shut it down completely.  I don't seem to be able to do that.  

When I click on either Gateway or 1TB Ext Bay1, I get a message "Unable to access &#8220;Gateway

Error mounting /dev/sda3 at /media/ubuntu/Gateway: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999" "/dev/sda3" "/media/ubuntu/Gateway"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda3': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option."

It's the same message when I try this with 1TB Ext Bay1, except that it says 1TB Ext Bay1.

I did try right clicking and selecting Mount, but the same message came up.

 Is there a way I can get out of hibernation mode to shut it down completely?

Thanks

Steve

---

### Post by yancek on 2017-01-02
The message you posted mean you left your windows system hibernated and no Linux operating will mount a hibernated system.  You need to turn off anything related to hibernating or fast boot in the BIOS.  I'm not sure if you need to boot into windows to turn hibernation off.  Since your problem is your inability to boot windows, you might try some windows forum or the microsoft support site.  If you posted some info on what happened to your windows, some members here who are more familiar with it might be able to offer suggestions.

---

### Post by coffeecat on 2017-01-02
If you haven't disabled fast startup in Windows, you need to do so. Unless you disable fast startup, Windows doesn't shut down, but merely hibernates. Here's how:

[https://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](https://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

Once you've done that you need to shut Windows down completely. Don't select reboot to get into Ubuntu.

---

### Post by spodeworld on 2017-01-02
Hi coffeecat.  Unfortunately I can't get into Windows to make changes.  I can get to a command prompt through the Windows 10 install/repair disk, but can't find a way to force a full Windows shutdown.

---

