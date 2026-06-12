---
title: "Ubuntu doesn't start after installing Wubi"
date: 2008-05-06
forum: General Help
---

### Post by ircmaster on 2008-05-06
So, I got wubi it didn't really work well. I installed Ubuntu through Wubi and I got it to work but after I re-started my computer but I can only use it once. After I restarted again (because I enabled the nVidia drivers) I couldn't access ubuntu anymore. Some Command Prompt came up and I couldn't go into Ubuntu. The little bar that loads shows up for a little and then it goes to the command prompt. I don't know what to do. I'm pretty new at this stuff so please go easy on me.

Edit: I have version 8.04 and I'm using Windows Vista.

---

### Post by ago on 2008-05-06
Probably the driver is not appropriate or well configured and the graphical interface fails.

At the prompt try to run:

sudo dpkg-reconfigure xserver-xorg

and select vesa as a driver

---

### Post by ircmaster on 2008-05-06
Where do I put this command? In the command thing?

---

### Post by ago on 2008-05-06
You should get to a login shell (or press ctrl+alt+f2 to get one).

---

### Post by ircmaster on 2008-05-06
Hm...maybe you're thinking about the wrong thing. What shows up for me is some weird command thing. I forgot the name of it. I think it also shows up when you go into the recovery mode of Ubuntu. I don't know about this stuff. I'll try to get the name of the thing though so I can type it in here and you can try to help me out.

---

### Post by ago on 2008-05-06
If it is busybox that might be because of an improper shutdown. Boot into windows and run chkdsk /r within the disk where you installed wubi. Then shutdown properly.

---

### Post by ircmaster on 2008-05-06
Sorry, I'm not good at this stuff. I opened chkdsk /r and then what do I do? 

Do you have any IM program where you can contact me? It'll be much easier.

---

### Post by ago on 2008-05-06
I am xivulon on IRC channel #wubi on irc.freenode.net

---

### Post by ircmaster on 2008-05-06
I'm in there, waiting for you to respond.

---

### Post by ago on 2008-05-06
there too :) sorry was busy testing some build scripts and didn't notice you there.

---

### Post by ircmaster on 2008-05-06
Can anyone help? I'm still not sure what to do.

---

### Post by Midwest-Linux on 2008-05-07
> **ircmaster said:**
> Can anyone help? I'm still not sure what to do.

 I installed Wubi 8.04, and Ubuntu didn't start, got stuck at initramfs. I deleted Wubi 8.04. 

 I tried Wubu 7.04, it installed it until I got to the Xorg.org display where it said "no screens found"

After that I threw in the towel and gave up. I didn't want to fool with the partition, so I went with Wubi instead. Funny thing was that the LIVE Ubuntu 8.04 DVD ran fine as a Live CD, but the same Ubuntu refused to install with Wubi.

 You can do a direct partition with Ubuntu, just I have this Vista computer that I don't want to hose just yet. The reason for the hesitation for doing a straight partition is that I have heard numerous comments that Vista doesn't like partitions and can get hosed. Which doesn't make much sense as Vista and XP are both NTFS and XP I never had a problem doing a Ubuntu direct partition with XP. 

Can someone clear this up?

 I have done a direct partition with Linux Mint 4.0 and Windows XP with no problem. And Windows 2000 and Ubuntu 7.04 on another machine with no problem either. 

Now the thing is with the initramfs problem, it isn't isolated with Wubi or Ubuntu 8.04. I had initramfs problems with Ubuntu 7.10 for Power PC, but with Ubuntu 7.04 for Power PC with the alternate installer it installed with no issues.

 Another computer I tried Xubuntu 7.10 I had issues with that, but the 7.04 Xubuntu installed flawlessly.

 Try 7.04 Wubi, you might have better luck than I did. Its no big deal for me as I know how to partition using the Ubuntu Grub. But the fact that Wubi seems to offer more in that one can delete the program at will and not have to worry about repartitioning the drive again and again.


Wubi 7.04
[http://kent.dl.sourceforge.net/sourceforge/wubi/Wubi-7.04.04.exe](http://kent.dl.sourceforge.net/sourceforge/wubi/Wubi-7.04.04.exe)

---

### Post by puccaso on 2008-06-27
i upgraded to intrepid. and i have the same chkdsk /r error.. check below for more details.. 

how were you able to fix this problem?

---

### Post by puccaso on 2008-06-27
```
ok so i am upgrading my system to intrepid... cos im using the hpmini note and its the new kernel supposedly supports the wifi card.. 

but now im getting an error telling me its due to inconsistancy on the ntfs drive.. and i should run chkdsk -r... 

ive done that
i still get the error.. 

what do i do?:guitar:

ok, so an edit to the first post

the actuall error message reads


could not mount the partition d/ev/disk/by-uuid/xxx this could also happen if the file system is not clean because of an operating sytem cash, an interrupted boot process, an imporer shutdown, or unplugging of a removable device without first unmounting or ejecting it. to fix this simply reboot into windows, let itt fully start, lgo in, run chkdsk /r, then gravefully shutdown and reboot bck into windows. 
after this you should be able to reboot again and resume the installation...

then it goes into initramfs.

the problem seems to accure with the 2.6.26-2-generic kernel, however i do not get this error with the previous hardy kernel.
 		                   		  		  		 		 			 				__________________
				
```


[http://ubuntuforums.org/showthread.php?t=842670](http://ubuntuforums.org/showthread.php?t=842670)

---

