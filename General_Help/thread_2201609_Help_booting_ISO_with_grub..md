---
title: "Help booting ISO with grub."
date: 2014-01-25
forum: General Help
---

### Post by stinkeye on 2014-01-25
I've actually got it working.... through trial and error.

What I need help with is determing the hd[COLOR="#FF0000"]X[/COLOR] value to use in grub.

eg my **/etc/grub.d/40_custom** entry
```
menuentry 'ISO Lubuntu  ' {

set isofile="/distros/lubuntu-13.10-desktop-amd64.iso"

loopback loop (hd[COLOR="#FF0000"]2[/COLOR],6)$isofile

linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject 

initrd (loop)/casper/initrd.lz 

} 
```

I have 3 hard drives 
```
[COLOR="#008000"]glen@Saucy:~$[/COLOR] **sudo blkid**
/dev/sda1: LABEL="XP" UUID="F0D4A588D4A55220" TYPE="ntfs" 
/dev/sda2: LABEL="Storage" UUID="E0D8480AD847DE02" TYPE="ntfs" 
/dev/sda5: LABEL="GAMES" UUID="40D0591AD059178C" TYPE="ntfs" 
/dev/sda6: LABEL="IsoFiles" UUID="6b9a9671-af34-44ed-89b0-fd1859ec2a81" TYPE="ext4"

/dev/sdb1: LABEL="Lubuntu" UUID="c5880bf6-ecea-4f32-b1a7-add902119045" TYPE="ext4" 
/dev/sdb4: UUID="09092549-56a6-44c6-bdad-4bf4ea4a5e54" TYPE="swap" 
/dev/sdb5: LABEL="Trusty" UUID="987f6d0e-34e4-455f-b580-4824ef5ac7d8" TYPE="ext4"
 
/dev/sdc1: LABEL="SaucySys" UUID="34354461-99dc-4fd8-8122-53365f2e6770" TYPE="ext4" 
/dev/sdc2: LABEL="SaucyHome" UUID="002b5ef7-1be7-4d52-a6d2-8ea23e87a782" TYPE="ext4" 
/dev/sdc3: UUID="ac6cb7ba-4f9b-4493-842f-0926a86e3a89" TYPE="swap" 
/dev/sdc5: LABEL="StudioSys" UUID="9bfca5fd-e66c-47af-a691-9974f1556173" TYPE="ext4" 
/dev/sdc6: LABEL="StudioHome" UUID="0b97f7ce-6103-41e5-abff-0fc11f4f94d8" TYPE="ext4" 
/dev/sdc7: LABEL="Data" UUID="bb31761a-6d8a-4693-b7c1-97f95100a126" TYPE="ext4"
 

```

**sda** is 2 windows installs with an ext4 partition(IsoFiles) at the end.I placed my iso files here.
**sdb** has a lubuntu and Trusty install
**sdc** is where grub is installed and has Saucy and Ubuntu-studio.

To use my iso file located in **/dev/sda6**  I have to use (hd[COLOR="#FF0000"]2[/COLOR],6) in **/etc/grub.d/40_custom**
I know (hd[COLOR="#FF0000"]0[/COLOR],1) is the first drive first partition but I thought sda6 would correspond to (hd[COLOR="#FF0000"]0[/COLOR],6)

I don't understand how you work out the hd[COLOR="#FF0000"]X[/COLOR] values for each drive.

---

### Post by jeanjd63 on 2014-01-25
Hello

If the iso partition is /dev/sda6, in grub the directive is :
[B][COLOR=#000000]loopback loop (hd[/COLOR][COLOR=#ff0000]0[/COLOR][COLOR=#000000],6)$isofile

[/COLOR][/B][COLOR=#000000]Bye[/COLOR]**[COLOR=#000000][/COLOR]**

---

### Post by stinkeye on 2014-01-25
> **jeanjd63 said:**
> Hello

If the iso partition is /dev/sda6, in grub the directive is :
[B][COLOR=#000000]loopback loop (hd[/COLOR][COLOR=#ff0000]0[/COLOR][COLOR=#000000],6)$isofile

[/COLOR][/B][COLOR=#000000]Bye[/COLOR]**[COLOR=#000000][/COLOR]**

No, that's the question.....the iso partition **is** /dev/sda6 but I have to use (hd2,6) in /etc/grub.d/40_custom
Tested and boots with (hd2,6)...does not with (hd0,6)
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry 'ISO Lubuntu  ' {

set isofile="/distros/lubuntu-13.10-desktop-amd64.iso"

loopback loop [COLOR="#FF0000"](hd2,6)[/COLOR]$isofile

linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject 

initrd (loop)/casper/initrd.lz 

}

menuentry 'ISO Elementary OS  ' {

set isofile="/distros/elementaryos-stable-amd64.20130810.iso"

loopback loop [COLOR="#FF0000"](hd2,6)[/COLOR]$isofile

linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject nomodeset 

initrd (loop)/casper/initrd.lz 
```

---

### Post by jeanjd63 on 2014-01-25
The explication seems to be what grub rename devices /dev/sda --> /dev/sdc ect..
What contains file /boot/grub/grub.cfg and what is the boot device ?

---

### Post by sudodus on 2014-01-25
When you are at the grub menu, press c to get to the command prompt and run the command
```
ls
```
or
```
ls -l
```
which should help you identify the device number. It will often be in another order compared to when Ubuntu is running and you have /dev/sda, /dev/sdb ...

---

### Post by stinkeye on 2014-01-25
> **sudodus said:**
> When you are at the grub menu, press c to get to the command prompt and run the command
```
ls
```
or
```
ls -l
```
which should help you identify the device number. It will often be in another order compared to when Ubuntu is running and you have /dev/sda, /dev/sdb ...

That's even more confusing ...
hd0 = sdc  .....boot drive (makes sense)
hd1 = sda  .....location of iso in partition 6
hd2 = sdb  .....other linux installs

so from that I would expect to use (hd[COLOR="#FF0000"]1[/COLOR],6) ???

---

### Post by sudodus on 2014-01-25
Try it :-)

If it works, make it permanent and use it.

---

### Post by jeanjd63 on 2014-01-25
You can try it in dynamic. In the menu grub you choose the line "ISO lubuntu" and press "e" touch and change the number in line :
loopback loop [COLOR=#FF0000](hdX,6)[/COLOR]$isofile

and valid with CTRL+X or F10 keys

---

### Post by stinkeye on 2014-01-25
> **sudodus said:**
> Try it :-)

If it works, make it permanent and use it.
I've already got it working with (hd[COLOR="#FF0000"]2[/COLOR],6) by trial and error.
I was trying to find out how to get the right hd[COLOR="#FF0000"]X[/COLOR] value without guessing.

---

### Post by sudodus on 2014-01-25
I had expected it to be the same (shown by ls and used in the script), assuming that the same drives are there and connected the same way. I agree that it is confusing. To avoid guessing, maybe you can use the ***search*** command, as described in this link

[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html)

---

### Post by stinkeye on 2014-01-25
> **sudodus said:**
> I had expected it to be the same (shown by ls and used in the script), assuming that the same drives are there and connected the same way. I agree that it is confusing. To avoid guessing, maybe you can use the ***search*** command, as described in this link

[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html)
OK thanks...the grub menu ls command seems like it should have worked.
I'll have a read of Herman's tutorial.
No biggie as I've got it working I just like to give myself headaches. ;)

---

### Post by stinkeye on 2014-01-25
Tried from grub...
```
search -l IsoFiles
```
gave me
```
hd1,msdos6
```

...so same as your original **ls -l**

---

### Post by sudodus on 2014-01-25
OK, and what happens if you have ***search*** in your script. Let us hope it will work :-)

---

### Post by stinkeye on 2014-01-25
Just for the hell of it I changed my /etc/grub.d/40_custom entry
to use (hd[COLOR="#FF0000"]1[/COLOR],6)
Ran **sudo update-grub**, rebooted to the iso and it loaded.

Seems somewhere along the line while I was doing trial and error I forgot to update-grub. :oops: User error.

So it appears running **ls -l** or using the **search** command from grub give the correct values.
Thanks for the trouble sudodus and jeanjd63.
....or should that be sorry for the trouble. :P

---

### Post by sudodus on 2014-01-25
I'm glad it works for you, and that we have found out how it works. We all forget some step that we should remember. Next time I'm the one ;-)

You can also run ***search*** automatically (put it via 40_custom into grub.cfg) and let it assign a shell variable, that is used by the script.

---

### Post by oldfred on 2014-01-25
Drive order in grub is set by BIOS and will be different than the Ubuntu drive order of sda, sdb etc if  you do not boot from sda.

I boot from sdd and the boot drive is always hd0 in grub, then I find drives usually are in SATA port order on motherboard. But I skipped a port. So When I plug in a flash drive it is sde, and if I boot from flash drive it always is hd0. But if I boot from sdd, my sda is hd1, but flash drive is hd2 and after booting becomes sdb or BIOS and Ubuntu insert it in the space for the empty port on motherboard. Seems strange, but how my system works.

Or trial and error often required as you found.

---

