---
title: "Boot problem"
date: 2014-09-23
forum: General Help
---

### Post by alexdiees on 2014-09-23
today i installed ubuntu 14.04 using a bootable usb. everything went fine until i wanted to get back to windows to transef files. 
This is what my grub boot menu looks like:

ubuntu
memory test (...)
memeory test (....)
windows recovery environment (loader) (on /dev/sda1)
windows 7 (loader) (on /dev/sda2)

Now, if i go with the windows 7 loader, windows will boot in safe mode, followed by forcing me to shut down because it can't find a solution.
the windows recovery environment gives me the option to bring my pc back to the way i bought it (thus deleting all my files).
I ran boot-repair, but it changed nothing. 
[http://paste.ubuntu.com/8412130/](http://paste.ubuntu.com/8412130/)

Could someone please tell me i didn't mess up that bad that whole my windows is gone.
i will be very grateful if someone can help me.

---

### Post by oldfred on 2014-09-23
Little hard to boot a Windows partition that does not exist. You have recovery & the normally hidden 100MB boot partition but no larger NTFS partition that report would also show /Windows/System32/winload.exe inside it.

Did you make a full recovery image of your Windows or the NTFS partition? If not you do still have recovery partition and may be able to restore from that. You probably have to totally remove Ubuntu and create the NTFS partition and restore a Windows boot loader to MBR.

Grub really only boots working Windows and Boot-Repair can only make minor repairs to Windows. You generally have to use a Windows repairCD or flash drive for major Windows fixes.

If you had files that you do not have backed up, stop using Ubuntu. Everything you do overwrites more data where NTFS partition was.

---

