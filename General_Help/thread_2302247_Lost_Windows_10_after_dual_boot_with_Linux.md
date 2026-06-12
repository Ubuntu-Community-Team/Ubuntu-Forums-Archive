---
title: "Lost Windows 10 after dual boot with Linux"
date: 2015-11-09
forum: General Help
---

### Post by richard117 on 2015-11-09
I dual booted my windows 10 with xubuntu on my Toshiba Satellite.  No problems initially. I could boot to either. Then I tried to clean up the boot menu with EasyBCD.  I obviously did not do it correctly and lost my windows 10 boot option.  I then tried linux boot repair.  I don't know what I did, but now I cannot access Windows 10 at all. Even the windows 10 repair disk cannot find windows 10. It does not even come up as an option. I have no problem booting to linux.  Can anyone help me recover my Windows 10?

---

### Post by Swagman on 2015-11-09
We have a Toshiba Satellite (Win 7)

If you press F2 at startup it should initiate a restore function.  
I'd try F12/F8 Whatever it is (can't remember) first to select boot options as a factory restore (F2) will, as stated, return you back to exactly how your lappy was when you bought it.

---

### Post by yancek on 2015-11-09
Were you using EasyBCD to boot both Xubuntu and windows 10?  Do you remember what you did to "clean up" the boot menu?
Boot repair has an option to Create BootInfo Summary so run it again and select that option and post a link to the output file here and someone might be able to help.

---

### Post by Cavsfan on 2015-11-09
Post the output of **sudo blkid** also.

---

### Post by richard117 on 2015-11-23
Thanks for the responses. I have not been able to get to this since posting it. 
Here is a link to the BootInfo Summary  [http://paste.ubuntu.com/13472310/](http://paste.ubuntu.com/13472310/)
Thanks for any help.

---

### Post by oldfred on 2015-11-23
Script is not showing major issues with Windows.
Did you leave Windows hibernated or its fast start up setting on?
Have you run chkdsk in Windows on sda2 or its c: "drive"

Have you tried temporarily restoring a Windows boot loader to MBR to see if Windows boots. Boot-Repair can do that. And if it does not directly boot use f8 to get into its repair console?
Then once it works restore grub to MBR with Boot-Repair.

       Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by Cavsfan on 2015-11-23
> **richard117 said:**
> Thanks for the responses. I have not been able to get to this since posting it. 
Here is a link to the BootInfo Summary  [http://paste.ubuntu.com/13472310/](http://paste.ubuntu.com/13472310/)
Thanks for any help.

OK, I'm pretty sure this will work.

Enter this in terminal: **gksudo gedit /etc/grub.d/06_custom** (if you don't have gedit use whatever text editor you have in place of gedit)
That will create a blank file and then copy this into it:

```
#!/bin/sh
echo 1>&2 "Adding Ubuntu Trusty Tahr 14.04 and Windows 10"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu Trusty Tahr 14.04" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro quiet splash
        initrd /initrd.img
}
menuentry "Ubuntu Trusty Tahr 14.04 (Recovery Mode)" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Windows 10" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6C72B4C872B49872
    chainloader +1
}
```

Save it then make it executable - **sudo chmod +x /etc/grub.d/06_custom** Then enter **sudo update-grub** and reboot.

Your first 3 options should be 
[LIST=1]
[*]Trusty Tahr 14.04 
[*]Trusty Tahr 14.04 (Recovery) 
[*]Windows 10 
[/LIST]

If you want to make the menu display longer edit /etc/default/grub - **gksudo gedit /etc/default/grub** and change the number besides GRUB_TIMEOUT= to something higher than 10 seconds.

Then save the file and once again do **sudo update-grub** and reboot.

You should be able to get to Windows 10 this way.

---

### Post by Cavsfan on 2015-11-23
Sorry oldfred, you posted while I was thinking :p.

But what I posted should allow the OP to get into Windows 10 again. It's worked for me for either Windows 7 or 10 for a long time now.

I upgraded 7 to 10 and the grub boot line didn't change while it still boots into Windows 10 just like it did 7.

---

### Post by oldfred on 2015-11-23
@Cavsfan
Your boot stanza should work, if Windows has no other issues.
It just is grub will only boot working Windows, and from grub even trying to get f8 for repair console is very difficult. Timing is too quick, but a few have said it worked. May depend on hard drive speed.
Not sure why Windows boots from MBR->PBR when hibernated, but grub booting directly to PBR does not work??

---

### Post by richard117 on 2015-11-24
Cavsfan, I tried your fix. I got your menu plus a Windows 7 option, but neither boots to windows. I can still get into xubuntu. This is the boot repair output:
[http://paste.ubuntu.com/13489682/]("http://paste.ubuntu.com/13489643/")

---

### Post by oldfred on 2015-11-24
Try changing the set root to 02 as your bootable Windows is sda2. But you have your UUID and that should have overwritten the incorrect partition, and still booted.

menuentry "Windows 10" {
    insmod ntfs
    set root='(hd0,[COLOR=#ff0000]2[/COLOR][COLOR=#ff0000][/COLOR])'
    search --no-floppy --fs-uuid --set 6C72B4C872B49872
    chainloader +1
}


If not try the direct boot from MBR and f8.

---

### Post by Cavsfan on 2015-11-24
> **oldfred said:**
> Try changing the set root to 02 as your bootable Windows is sda2. But you have your UUID and that should have overwritten the incorrect partition, and still booted.

menuentry "Windows 10" {
    insmod ntfs
    set root='(hd0,[COLOR=#ff0000]2[/COLOR])'
    search --no-floppy --fs-uuid --set 6C72B4C872B49872
    chainloader +1
}


If not try the direct boot from MBR and f8.

Yes, this *should* work. Sorry I forget to change the drive to point to partition 2 from 1 as oldfred has pointed out.

That windows 7 entry is coming from /etc/grub.d/30_os-prober and it can't differentiate between Windows 7 and Windows 10 I don't think.

Didn't realize you were using Xubuntu. If you can get into Windows 10 with the above change. Don't forget to do sudo update-grub after you make the change.
But, if it works you can edit /etc/grub.d/06_custom to say Xubuntu. It will display anything you put between the quotes.

---

