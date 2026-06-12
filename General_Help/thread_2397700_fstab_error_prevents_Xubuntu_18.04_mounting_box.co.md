---
title: "fstab error prevents Xubuntu 18.04 mounting box.com"
date: 2018-08-02
forum: General Help
---

### Post by ChrisRChamberlain on 2018-08-02
Hi all

```
sudo mount -t davfs https://dav.box.com/dav /media/Drive_D/Box.com # -o conf=/etc/davfs2/davfs2.conf
```enables box.com to be mounted manually.
Adding ```
https://www.box.com/dav /media/Drive_D/Box.com  davfs rw,user,noauto 0 0
```to /etc/fstab results in a system error and the icon on the desktop always 'greyed out'.

Clicking on the desktop icon produces message 'Failed to mount "Box.com"'.

The setup followed the instructions found here [https://www.maketecheasier.com/auto-mount-box-net-to-linux-desktop/]("https://www.maketecheasier.com/auto-mount-box-net-to-linux-desktop/")

Any ideas on how to resolve the issue, please?

TIA

---

### Post by slickymaster on 2018-08-02
*Thread moved to **General Help**.*

---

### Post by TheFu on 2018-08-02
Why did you change the URL and expect it to work the same?
[https://dav.box.com/dav](https://dav.box.com/dav) works, but [https://www.box.com/dav](https://www.box.com/dav) doesn't. Is that surprising or just a typo?

I know nothing about box, but played with DAV a few times to see how easy it was to hack.

BTW, DAV is known for poor security.  Please take appropriate steps to mitigate those risks.

---

### Post by ChrisRChamberlain on 2018-08-03
TheFu

Thanks for your reply - did not see that error and have since corrected it in /etc/fstab.

The procCmdline error now reported is```
/sbin/mount.davfs https://box.com/media/Drive_D/Box.com -o rw noexec nosuid dodev user
```

The manual mount works and enables the desktop icon correctly to access the mounted drive.

Your comments regarding security noted!

---

### Post by TheFu on 2018-08-03
So solved?

---

### Post by ChrisRChamberlain on 2018-08-04
Sadly no - the drive is not mounted on reboot or startup, the error message was shown in the previous post.

---

### Post by TheFu on 2018-08-04
> **ChrisRChamberlain said:**
> Sadly no - the drive is not mounted on reboot or startup, the error message was shown in the previous post.

You changed something, but haven't shown exactly what was changed.  Be explicit. Please help us to help you.

---

### Post by ChrisRChamberlain on 2018-08-04
```
https://www.box.com/dav /media/Drive_D/Box.com  davfs rw,user,noauto 0 0
``` in /etc/fstab was changed to ```
https://box.com/dav /media/Drive_D/Box.com  davfs rw,user,noauto 0 0
```The drive is not mounted.

Running ```
sudo mount -t davfs https://dav.box.com/dav /media/Drive_D/Box.com # -o conf=/etc/davfs2/davfs2.conf
```mounts the drive, enabling the desktop icon.

After a while, a system error is reported which is procCmdline error ```
/sbin/mount.davfs https://box.com/media/Drive_D/Box.com -o rw noexec nosuid dodev user
```and the drive remains mounted.

---

### Post by oldfred on 2018-08-04
You have a space after user?

---

### Post by TheFu on 2018-08-04
Looks like the same mistake that I pointed out the first time, again.
You've said that [https://dav.box.com/dav](https://dav.box.com/dav) works.  Why don't use that in the fstab?   I really would like to know.  Please.

I'm curious.  Do you understand the significance of the different parts to a DNS hostname?  You can't just change them and magically expect things to work. The names do not tie to any specific protocol, though that is commonly done. There is no real connection.  dav.box.com could be anything .... spock.box.com ... if the DAV service was running on it and firewall rules allowed external access.

---

### Post by ChrisRChamberlain on 2018-08-05
oldfred

Thanks for your reply - the apparent space is an illusion. If you copy the string within the code tags and paste it elsewhere, you will find there is no space after user.

TheFu

Sincere apologies, you are absolutely correct about repeating the same mistake.```
https://dav.box.com/dav /media/Drive_D/Box.com  davfs rw,user,noauto 0 0
```is now the line content in /etc/fstab.

So following reboot/startup, the desktop icon is greyed out but on clicking it, the drive is mounted correctly without error.

The drive is not accessible without clicking on the desktop icon.

Alternatively, entering```
mount /media/DriveD/Box.com
```at the command prompt, successfully mounts the drive.

So added```
@reboot mount /media/DriveD/Box.com
```to the crontab, and the drive is mounted on reboot but not startup.

Now need to to find a way to mount the drive on startup as well as reboot?

Again many thanks to TheFu for his patience and perseverance.

---

### Post by TheFu on 2018-08-05
I'm confused.  What is the different between reboot and startup?

---

### Post by ChrisRChamberlain on 2018-08-05
If the device, an Econel 200 server + temporary Xubuntu desktop installed, is started as a cold boot, the drive is not mounted, and requires either click on desktop icon or 'mount...' to mount the drive.

If the device is rebooted, the drive is mounted automatically and the desktop icon displays the drive as being mounted.

Have tried```
@reboot /sbin/mount /media/DriveD/Box.com
```as opposed to```
@reboot mount /media/DriveD/Box.com
```in the crontab in case there is a pathing issue on a cold boot, without success.

---

### Post by TheFu on 2018-08-05
We all make mistakes.   There was conflicting guides with [www.box.com](www.box.com) and dav.box.com out there that I saw.

I suspect you have a dependency issue with the startup and the timing of how things are started is just a little different between a reboot and a cold-boot. That is just my guess.

I've never heard of that being "a thing" - should behave the same. 

One of the great things about experience is that it teaches you how NOT to do things to avoid the most issues.  Often, because of a failure. ;)
1st, I've learned NOT to use DAV storage. (or plain FTP).
2nd, I use **autofs** for any storage that isn't connected directly to the system with SAS, SATA, eSATA, or Infiniband connections. Autofs, once configured, mounts and unmounts storage as-needed.
3rd, I don't use GUIs for file management very often. GUIs tend to break long understood methods for file access in attempting to make things easier. GUIs also make any file operations slower, at least fractionally, but sometimes 2-4x longer.  That isn't always true, but it is so often, that I avoid GUIs most of the time.

BTW, box.com has announced they are removing webdav support in a few months. [https://community.box.com/t5/Box-Product-News/Deprecation-WebDAV-Support/ba-p/55684](https://community.box.com/t5/Box-Product-News/Deprecation-WebDAV-Support/ba-p/55684)

Looks to me like sftp is the current best option that isn't going away: [https://uisapp2.iu.edu/confluence-prd/display/SOICKB/Using+Box+under+Linux](https://uisapp2.iu.edu/confluence-prd/display/SOICKB/Using+Box+under+Linux) if that link can be trusted. sftp is built into pretty much all Linux GUI file managers, but the sftp protocol doesn't work the same as local/NFS access.  
Might be time to mirror the box.com stuff locally and use NFS.

---

### Post by ChrisRChamberlain on 2018-08-06
TheFu

Marking the thread as solved although the minor irritation with boot type remains.

Your last post is also very helpful in pointing ways forward - will digest when current European heatwave allows frazzled brain to function properly again.

Again many thanks.

---

