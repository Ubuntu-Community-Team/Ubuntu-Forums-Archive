---
title: "Windows 8.1 Partition not mountable (&quot;unsafe state&quot;), Windows Fast Startup disabled"
date: 2015-05-29
forum: General Help
---

### Post by Rock 'n' Linux on 2015-05-29
When trying to access my Windows 8.1 system partition, I get the following error:

[FONT=courier new]**Unable to access “Windows”**
[/FONT][FONT=courier new]Error mounting /dev/sdb1 at /media/username/Windows: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb1" "/media/username/Windows"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.[/FONT]
[FONT=courier new]Failed to mount '/dev/sdb1': Operation not permitted[/FONT]
[FONT=courier new]The NTFS partition is in an unsafe state. Please resume and shutdown[/FONT]
[FONT=courier new]Windows fully (no hibernation or fast restarting), or mount the volume[/FONT]
[FONT=courier new]read-only with the 'ro' mount option.

[FONT=arial]I did not hibernate Windows 8.1, and I have already disabled "fast startup" in Windows (the hybrid hibernation mode).

Any idea what else could be the problem?
[/FONT]
[/FONT]

---

### Post by oldfred on 2015-05-29
It could also need chkdsk.

But are you sure you fully disabled fast startup and fully shutdown? Windows does not make that easy.
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

---

### Post by Rock 'n' Linux on 2015-05-29
Thanks.  Unfortunately, the problem remains.

I checked that fast startup is disabled, and it is (both in the menu and in the registry as indicated in the links in your post).  (I had actually disabled this straight from the beginning after upgrading to Windows 8 as I was aware of the hyberboot/dual boot issue and the setting is still correct.)  I have also shut down fully using Win-X.  In any case, I always shut down fully as I use a custom shutdown batch file with a link on the desktop (easier than Win-X or the stupid charms bar).

I then tried chkdsk, first an online scan "chkdsk C: /scan /perf".  This actually found and fixed quite a few errors in files in my Civilization V installation.

I then used an offline scan at reboot ("chkdsk C: /offlinescanandfix").  This found and fixed a few more errors (free space that was allocated).

Unfortunately, after logging back into Ubuntu, I get the same message as before and can't mount my Windows partition.

Any ideas?

---

### Post by oldfred on 2015-05-29
If chkdsk is finding errors, you need to rerun until no errors are found.

The Linux NTFS driver will not mount a NTFS partition with either the chkdsk or hibernation flags set to avoid the possibility of damage that chkdsk would then not be able to fix.

---

### Post by Rock 'n' Linux on 2015-05-29
This does not seem to help.  I ran chkdsk an additional five or six times (always upon reboot). The chkdsk log always says that it doesn't find any errors and that no further action is necessary.  The only thing it does everytime is to clean up a few unused indexes in file 0x9.

I have not run chkdsk with the /R option yet.  I'll probably do that overnight.  But I don't see why Windows would set a partition to unclean if chkdsk says that there are no issues.

Is there anyway to find out what causes the error when mounting?  I suspect it somehow still thinks Windows is hibernated.  I just ran the mount command manually:

```
username@laptop-ubuntu:/media/username$ sudo mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb1" "/media/m/Windows"
**Windows is hibernated, refused to mount.**
Failed to mount '/dev/sdb1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

```
Any further ideas?

---

### Post by oldfred on 2015-05-30
I have seen this, not sure if it works. Best to have good backups.

 Force removal of hiberfil from Ubuntu
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)
Force mount, read only:
sudo mkdir /media/windows
sudo mount -t ntfs-3g -o ro /dev/sda3 /media/windows

---

