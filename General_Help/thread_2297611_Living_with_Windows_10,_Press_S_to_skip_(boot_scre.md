---
title: "Living with Windows 10, Press S to skip (boot screen)"
date: 2015-10-05
forum: General Help
---

### Post by Quarkrad on 2015-10-05
Running 14.04.  I dual boot with win 10 (itunes) and find that after being in the win10 environment when I reboot to Ubuntu my three ntfs partitions will not auto mount - I get the **Press S to skip** text during boot.   If I launch nautilus and left click on any one of these three ntfs partitions (one of which is win10 itself) I get the following error/message:

[B]Error mounting system-managed device /dev/sda7: Command-line `mount "/media/store1"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda7': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.[/B]

A solution is to reboot into Win 10 and run chkdsk x: /f /r on all three partitions - (there is never any problems reported).  Next reboot (into Ubuntu) there is no problem and the partitions are auto mounted.  I use Ubuntu 90% of the time and every boot the partitions auto mount - it is only after I boot to Win10 do the partitions not auto mount.  I have run SMART TEST on my HDs, where the ntfs partitions are, within Ubuntu and separately within Windows (using a third party app) and the HDs are reported as good.  Seems something happens when I'm in Win10 that Ubuntu does not like when it boots.  Any help appreciated.

---

### Post by yancek on 2015-10-05
This 'problem' has been discussed here numerous times.  Windows 10 doesn't shut down, it puts the system in hibernation by default when you reboot so that it appears to boot faster so I believe you need to do an actual shutdown from windows before rebooting.  I believe the concept behind this is that accessing a system from another system when the first is hibernated will potentially cause problems for the hibernated system.  Someone else who uses windows might be able to give you more details.

---

### Post by Bucky Ball on 2015-10-05
Yep, the above is no doubt your issue. Boot into Windows and switch off hibernation and fast startup (I think it's called). Then do a complete Windows shutdown. This will close and unmount all partitions. Closing to hibernate will not. Therefore, when you boot Ubuntu, as far as it knows, all partitions are already mounted, in use, and unavailable.

Probably nothing to do with running chkdsk or checking smart status. This would only apply if there was a hardware fault or you needed to fix partitions. Doubt there is anything wrong with your drives (as Windows sounds like it is running just fine).

* See links from oldfred below. :)

---

### Post by oldfred on 2015-10-05
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

---

### Post by Quarkrad on 2015-10-06
That fixed it - many thanks.

---

