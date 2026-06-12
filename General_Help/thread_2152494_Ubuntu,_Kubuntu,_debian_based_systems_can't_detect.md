---
title: "Ubuntu, Kubuntu, debian based systems can't detect Windows Vista"
date: 2013-06-08
forum: General Help
---

### Post by firekage on 2013-06-08
Hi!

I would like to ask for your help. I have problem with Ubuntu, Kubuntu related to not detecting Windows Vista in grub. I run update-grub or update-grub2 and see that on generated cfg there is Windows Vista, also when i use sudo os-prober the same list is being generated with Windows Vista but as soon as i reboot, see purple grub with available systems to boot, there is no Windows Vista.

I think that it is related to call 30_os-prober in /etc/default/grub or /etc/grub.d/ (im on Windows right now, can't check it). The only way of starting Windows is not from grub but by hitting F8 and selecting hard disk with it.

Could you help me? I tried to find a solution, few have the same problem but running os-prober in my case didn't helped at all.

Thanks.

---

### Post by firekage on 2013-06-08
Here are the outputs of update-grub, update-grub2 and os-prober

```
firekage@deusex:~$ sudo os-prober
[sudo] password for firekage: 
/dev/sda2:Slackware Linux (Slackware 13.37.0):Slackware:linux
/dev/sdc1:Windows Vista (loader):Windows:chain
/dev/sdd1:Slackware Linux (Slackware 14.0):Slackware1:linux
/dev/sdf1:Ubuntu 12.04.2 LTS (12.04):Ubuntu:linux
```

and ```

firekage@deusex:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-24-virtual
Found initrd image: /boot/initrd.img-3.2.0-24-virtual
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Slackware Linux (Slackware 13.37.0) on /dev/sda2
Found Windows Vista (loader) on /dev/sdc1
Found Slackware Linux (Slackware 14.0) on /dev/sdd1
Found Ubuntu 12.04.2 LTS (12.04) on /dev/sdf1
done 
```

and ```

firekage@deusex:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-24-virtual
Found initrd image: /boot/initrd.img-3.2.0-24-virtual
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Slackware Linux (Slackware 13.37.0) on /dev/sda2
Found Windows Vista (loader) on /dev/sdc1
Found Slackware Linux (Slackware 14.0) on /dev/sdd1
Found Ubuntu 12.04.2 LTS (12.04) on /dev/sdf1
done
firekage@deusex:~$ 


```

It is, during reboot on purple grub, it isn't.

---

### Post by firekage on 2013-06-09
Help needed ;)

---

### Post by sudodus on 2013-06-15
Probably another distro is governing grub, I mean, the bootloader points to another system. Then it does not help with update-grub. You need to do from the installed system, that is governing grub.

See these links for more details

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

and links from them. Maybe you want to reinstall grub.

---

### Post by YannBuntu on 2013-06-15
@firekage: please run Boot-Repair's Recommended Repair, and indicate the URL that will appear.

---

### Post by firekage on 2013-06-16
Funny thing is that i update grub from installed system, from Ubuntu installed on 1TB Samsung drive. I have exacly the same problem with Kubuntu.

---

### Post by firekage on 2013-06-16
Ok, here is the link:

[http://paste.ubuntu.com/5770704/](http://paste.ubuntu.com/5770704/)


Well, still the same problem after doing boot repair. Vista is being present during update-grub, no present, at all, during reboot on purple grub system list.

---

### Post by YannBuntu on 2013-06-16
You have several disks. Probably your issue is that your BIOS is not booting on the right disk.
Please look at your BIOS and tell us on which disk it is set up to boot.
Then change the boot order in order to make it boot on Ubuntu's disk. (1TB)

---

### Post by firekage on 2013-06-16
Samsung 1TB drive with Ubuntu is being set in bios. If it would be different choose than i wouldn't have purple grub on start (it would be either slackware lilo or blue kubuntu grub) so the disk it the one that should be.

---

### Post by firekage on 2013-06-16
Forgot to mention that during running boot-repair i have warning that there is low disk space on Vista destination disk and boot repair told me that there could be problem with running it (starting it?) but i don't believe that amount of space is cruicial to grub-loader.

---

### Post by firekage on 2013-06-16
As they say, if something is going to gone wrong, it would'vegone even worst. After running boot-repair i can't boot to Vista ), can't boot to Slackware 14 and Slackware 13.37 (even when i choose them from the bios by hitting F9), and the same thing happens with Kubuntu - boot-repair destroyed all their bootloader, and new installed bootloader to a Ubuntu system can't detect Vista and Slackware 14. On system list there is only Ubuntu and Slackware 13.37.

Great God...

---

### Post by sudodus on 2013-06-16
As long as you can boot Ubuntu and run

```
sudo update-grub
```

it should work again after reboot, at least what worked before the attempt to repair.

Please explain again

1. What happens on the screen when you run sudo update-grub

2. Are there menuentries in **[FONT=courier new]/boot/grub/grub.cfg[/FONT]** corresponding to what was found according to the screen? Particularly, is there any menuentry for 'Vista' or for 'Windows recovery'?  

3. Are there corresponding menu items (lines) in the grub menu when you have booted? What happens when you select 'Windows recovery' and try to boot from it?

---

### Post by firekage on 2013-06-16
> **sudodus said:**
> 
Please explain again

1. What happens on the screen when you run sudo update-grub


Here is what happens

> 
firekage@deusex:~$ sudo update-grub
[sudo] password for firekage: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-24-virtual
Found initrd image: /boot/initrd.img-3.2.0-24-virtual
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found Slackware Linux (Slackware 13.37.0) on /dev/sda2
Found Windows Vista (loader) on /dev/sdc1
Found Ubuntu 12.04.2 LTS (12.04) on /dev/sdd1
Found Slackware Linux (Slackware 14.0) on /dev/sdg1
done
firekage@deusex:~$ 





> 
2. Are there menuentries in **[FONT=courier new]/boot/grub/grub.cfg[/FONT]** corresponding to what was found according to the screen? Particularly, is there any menuentry for 'Vista' or for 'Windows recovery'?  


Yes.
> 
3. Are there corresponding menu items (lines) in the grub menu when you have booted? What happens when you select 'Windows recovery' and try to boot from it?
[/quote]
Yes, exept Vista. It is not being shown on grub during boot and list of detected systems to choose.

BTW - after grub-repair i can't even boot Vista from bios. I think that grub deleted bootloader, i tried to fix it in windows way (bootrec /fixmbr /fixboot /rebuildbcd) but it doesen't work.

---

### Post by oldfred on 2013-06-16
One of the options in Boot-Repair is to reinstall grub of your Ubuntu install into ALL mbr. I do not like that choice as I have different boot loaders in every MBR and it looks like you did also.

You want to reinstall lilo into the MBR's of Windows and your Slackware & Windows installs or sda, sdc & sdd.
The lilo boot loader works just like Windows in finding the boot flag and jumping to the PBR. PBR then has more boot code for Windows or Lilo.

       Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader. Rerun for sdc & sdd

---

### Post by firekage on 2013-06-17
> **oldfred said:**
> One of the options in Boot-Repair is to reinstall grub of your Ubuntu install into ALL mbr. I do not like that choice as I have different boot loaders in every MBR and it looks like you did also.

Didn't know that...


> sudo lilo -M /dev/sda mbr

I should place it in Slackware and Vista? So i should, for an example, choos /dev/sd(Vista), right?

> Rerun for sdc & sdd

Could you exmplain it again? Rerun? You mean lilo rerun it nerminal?

---

### Post by oldfred on 2013-06-17
You install from Ubuntu. But all computers boot from MBR and find more boot code.

After you download lilo into Ubuntu.
sudo lilo -M /dev/sda mbr
sudo lilo -M /dev/sdc mbr
sudo lilo -M /dev/sdd mbr

While this is Vista it is how BIOS/MBR computers boot. Grub does not use PBR or partition boot sector but Windows & Lilo do.
       Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by firekage on 2013-06-17
Ok, and what about "rerun" of lilo?

---

### Post by oldfred on 2013-06-17
Not sure what you mean.

If you install lilo's boot loader into a MBR, it should then find the bootable install of Windows or other systems using existing boot flag and existing code in PBR which was not overwritten. Only MBR was overwritten with grub2's boot loader.
But you still have to go into BIOS and choose to boot that drive directly.

But grub2 should give you the option to boot every system from your grub menu. Some systems may need a littile help or a manual setting in 40_custom to chain boot other systems from grub. Chainbooting to lilo in a PBR is just like chainloading to Windows.

---

### Post by firekage on 2013-06-20
I did what you suggested :

> **oldfred said:**
> You install from Ubuntu. But all computers boot from MBR and find more boot code.

After you download lilo into Ubuntu.
sudo lilo -M /dev/sda mbr
sudo lilo -M /dev/sdc mbr
sudo lilo -M /dev/sdd mbr

While this is Vista it is how BIOS/MBR computers boot. Grub does not use PBR or partition boot sector but Windows & Lilo do.
       Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)


And in case of Vista it works, haven't tried other because i don't have right now enough time but i would ask about one thing - it is necessary to write 

> sudo lilo -M /dev/sdX mbr

instead 

> sudo lilo -M /dev/sdX

there must be mbr after device?

Also, it is possible to install this from another system, like Slackware, to other os, like Vista? I don't know how to do it under Slackware.

---

### Post by oldfred on 2013-06-20
X is device number, and MBR is what is being installed. I do not know Slackware so maybe installing from inside Slackware does not need that, but if not it then is a default setting. Or it may be doing the full install of Lilo which is not just MBR but also PBR and boot configuration file or menu.
But you would not want to install the full Lilo to a Windows install as that would overwrite the Windows code in the NTFS PBR or partition boot sector. Windows has to have its code in the PBR.

Many Repair Linux liveCD have lilo installed already so it often can be installed from any version. It is an old boot loader that has been around for ages. I think recently they started maintaining it again, but it was like old grub legacy and did not work with a lot of newer systems.

---

### Post by firekage on 2013-06-20
Thanks. Vista works, only thing to do is force grub to detect it. Don't know why, but it still doesen't work when i do update-grub.

---

### Post by sudodus on 2013-06-20
What do you mean by "Vista works, only thing to do is force grub to detect it"?

How do you boot it? And why is that not good enough?

---

### Post by grahammechanical on 2013-06-20
You have two versions of Ubuntu 12.04.2. One on sdf and another on sdg. which one do you want to be in control of the Grub boot menu?

If it is 12.04.2 on sdf then boot into it and run

```
sudo update-grub
```
```
sudo grub-install /dev/sdf
```

If it is 12.04.2 on sdg then boot into it and run

```
sudo update-grub
```
```
sudo grub-install /dev/sdg
```

It is the second command that install Grub into the MBR. I sometimes find that although update-grub finds the other OS it does not always get shown in the Grub menu until I run the second command. So, try doing that.

Regards.

---

### Post by firekage on 2013-06-21
I have to boot it by hitting F8 and choosing disk that it is installed on because grub doesen't detect it (even when i use sudo update-grub, it sees it only during update-grub, but after reboot not) and it is not present on purple boot screen from grub (also the same thing is with blue grub from kubuntu).

---

### Post by firekage on 2013-06-21
Ok, will check it. Thank you.

---

### Post by oldfred on 2013-06-21
You have a lot of kernels. The new sub-menu usually eliminates the problem, but the box that the menus appear in only shows so many lines. Often those with a lot of systems need to scroll down to find other installs.
If you have a really tiny arrow on the right side of the grub menu box then you have more entries.

---

### Post by ubunt72 on 2013-06-21
> **firekage said:**
> I have to boot it by hitting F8 and choosing disk that it is installed on because grub doesen't detect it (even when i use sudo update-grub, it sees it only during update-grub, but after reboot not) and it is not present on purple boot screen from grub (also the same thing is with blue grub from kubuntu).
I'm somewhat stupid (lol!) so hopefully the experts here will correct me if I'm wrong but I think the problem has to do with mapping because you are trying to boot Windows Vista which is on a separate HDD than your Ubuntu OS.   If someone who has provided the solution thinks that the 'update-grub' will work when you have to factor in both drives, then I'm very interested because I wonder how that works! ;-)

You posted:

/dev/sdc1* - Windows Vista
/dev/sdf1* - Ubuntu

So, two different drives here and I think you need to do something further than just run the update-grub command????????   Help?!?   I am not sure.  

Something to do with 'drivemap?'

I was wondering if you have to edit the file 
/boot/grub/grub.cfg 
but I'm not sure what to do there.   Maybe someone can comment?   This also interests me because if I ever buy a solid state drive (SSD), I think I'd want Windows and Linux on separate drives.

P.S.  I wonder if sudodus was on the right track in post #12.   But, I don't know enough about grub2 and editing it so I'm just speculating/guessing.

---

### Post by sudodus on 2013-06-22
... or oldfred was on the right track in post #26?

---

### Post by firekage on 2013-06-22
> **oldfred said:**
> You have a lot of kernels. The new sub-menu usually eliminates the problem, but the box that the menus appear in only shows so many lines. Often those with a lot of systems need to scroll down to find other installs.
If you have a really tiny arrow on the right side of the grub menu box then you have more entries.

Well...i didn't mention that because i though that it is out of the question. Here is picture with my grub after run "update-grub" and reboot ot the system that "update-grub" was done, the same thing happens with ubuntu and kubuntu.

Sorry for quality of the picture but...my digital cam broken and it was made by using phone.

As you can see, there are only 4 entries: 

- 2 with ubuntu (one with kernel and one with revocery mode)
-previous linux version
-Slackware 13.37

Grub can't detect Vista, Kubuntu and Slackware 14 (i fixed their bootloader: Vista, as you mentioned earlier, by installing lilo on it, Kubuntu from live-cd installing his grub, and Slackware 14 by installing again lilo on it, i can boot to all of them by hitting F8 - they are on separate disk - but they are not present on the list).


Forget to mention: i have 2 laptops with Ubuntu, Kubuntu, Vista, Slackware and on them, while there is only one hard disk drive with few partitions, all these systems are being found by grub when i run update-grub. Here, on my desktop, with 6 or 7 drivers it is not.

---

### Post by firekage on 2013-06-22
> **grahammechanical said:**
> You have two versions of Ubuntu 12.04.2. One on sdf and another on sdg. which one do you want to be in control of the Grub boot menu?

If it is 12.04.2 on sdf then boot into it and run

```
sudo update-grub
```
```
sudo grub-install /dev/sdf
```

If it is 12.04.2 on sdg then boot into it and run

```
sudo update-grub
```
```
sudo grub-install /dev/sdg
```

It is the second command that install Grub into the MBR. I sometimes find that although update-grub finds the other OS it does not always get shown in the Grub menu until I run the second command. So, try doing that.

Regards.

I tried this - doesen't work in my case. Thanks ;)

---

### Post by oldfred on 2013-06-22
It also is only showing one Slackware and not the other Ubuntu?

 Found Slackware Linux (Slackware 13.37.0) on /dev/sda2
Found Windows Vista (loader) on /dev/sdc1
Found Ubuntu 12.04.2 LTS (12.04) on /dev/sdd1
Found Slackware Linux (Slackware 14.0) on /dev/sdg1

Repost BootInfo report. Did you edit any of the grub scripts. 

It may be easier to totally uninstall grub in the version you are booting from and totally reinstall grub. 

 # HOWTO: Purge and Reinstall Grub 2 from the live-CD/DVD/USB - drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

   # purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by firekage on 2013-06-22
> **oldfred said:**
> It also is only showing one Slackware and not the other Ubuntu?


Yes, that is correct, only one Slackware (13.37, there is no Slackware 14, and one Ubuntu)

 > Found Slackware Linux (Slackware 13.37.0) on /dev/sda2
Found Windows Vista (loader) on /dev/sdc1
Found Ubuntu 12.04.2 LTS (12.04) on /dev/sdd1
Found Slackware Linux (Slackware 14.0) on /dev/sdg1

Yes, that is correct. Update-grub finds these systems, but grub doesen't see them after reboot on purple screen.

> Repost BootInfo report. Did you edit any of the grub scripts. 

Ok, will do and post it.

No, i havent edited anything yet.

> It may be easier to totally uninstall grub in the version you are booting from and totally reinstall grub. 

Tried this several times. Doesen't work.

> 
 # HOWTO: Purge and Reinstall Grub 2 from the live-CD/DVD/USB - drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

   # purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub

I tried this several times. I will say that i also did the same thing on second Ubuntu (in fact, "second Ubuntu" is Kubuntu but grub doesen't see the diferences, for him it is the same linux system), in fact, on Kubuntu. Result is the same. I purged grub, installed it again, updated it and after reboot, blue grub from Kubuntu ("second Ubuntu") see...again only one Slackware (13.37), and "Previous linux" and nothing more exept itself and itself with recovery mode.

---

### Post by Beautymist on 2013-06-22
@firekage: can I ask a somewhat insolent question?

What do you need windows vista for, anyway? or anything win at all? I have both a linux and a win OS, I am in no way an expert or computer wizard, still I manage to do *everything* I want & need on my linux OS. I still have win somewhere in the limbo of my PC, but never looked back since a linux OS was installed (not by me) on my computer almost 15 yrs ago.

Just askin'.
:oops:

-BM

---

### Post by oldfred on 2013-06-22
If grub menu is not showing second install are you just choosing Kubuntu from login screen and not the grub menu  boot of the other install?

Post this:
 List entries in grub
cat /boot/grub/grub.cfg  | grep menuentry

---

### Post by firekage on 2013-06-22
> **oldfred said:**
> If grub menu is not showing second install are you just choosing Kubuntu from login screen and not the grub menu  boot of the other install?


Sorry, my english right now doesen't allow me to fully understand this question. If i understand correctly, then i say this: i choose Kubuntu by hitting F8, selecting hard drive that Kubuntu is installed on, after few seconds blue grub shows up and i don't see anything other that i posted earlier: missing Vista, Ubuntu and Slackware 14. The same thing goes with Ubuntu: missing Kubuntu, Vista and Slackware 14 when i hit F8 and select hard drive that Ubuntu is installed on, with purple grub.

> 
Post this:
 List entries in grub
cat /boot/grub/grub.cfg  | grep menuentry

Here it is:

```
cat firekage@deusex:~$ cat /boot/grub/gr
grldr.img  grub.cfg   grubenv    
firekage@deusex:~$ cat /boot/grub/grub.cfg | grep menuentry
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 3.2.0-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 3.2.0-24-generic-pae (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 3.2.0-24-virtual' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 3.2.0-24-virtual (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 3.2.0-24-generic (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Slackware_13.37 (on /dev/sda2)" --class gnu-linux --class gnu --class os {
menuentry "Windows Vista (loader) (on /dev/sdc1)" --class windows --class os {
menuentry "Ubuntu, za pomoc&#261; systemu Linux 3.2.0-39-generic-pae (on /dev/sdd1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, za pomoc&#261; systemu Linux 3.2.0-39-generic-pae (tryb ratunkowy) (on /dev/sdd1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, za pomoc&#261; systemu Linux 3.2.0-37-generic-pae (on /dev/sdd1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, za pomoc&#261; systemu Linux 3.2.0-37-generic-pae (tryb ratunkowy) (on /dev/sdd1)" --class gnu-linux --class gnu --class os {
menuentry "Slackware_14 (on /dev/sdg1)" --class gnu-linux --class gnu --class os {
firekage@deusex:~$ 


```

and here is repair-boot summary:

[http://paste.ubuntu.com/5790898/](http://paste.ubuntu.com/5790898/)

---

### Post by firekage on 2013-06-22
> **Beautymist said:**
> @firekage: can I ask a somewhat insolent question?

What do you need windows vista for, anyway? or anything win at all? I have both a linux and a win OS, I am in no way an expert or computer wizard, still I manage to do *everything* I want & need on my linux OS. I still have win somewhere in the limbo of my PC, but never looked back since a linux OS was installed (not by me) on my computer almost 15 yrs ago.

Just askin'.
:oops:

-BM

Sure, of course ;)

Sometimes i would like to play on it. Linux doesen't allow me to playing games that i would like to play. As a matter of fact, this is the only reason why i still have it because linux gives me everything that i would like to have from system exept playing games - wine and play on linux is not always good approach and with it i'm not able to play in everything that i would like to or with games that i really like, nothing more.

In fact, i don't have much time to spend on playing but i want my systems work the way i want...not the way they want. It worked, now it doesen't, don't know why.

---

### Post by oldfred on 2013-06-22
Slackware as copied by grub2's os-prober has a typo. So all your entires after the typo will not show. 
It is unmatched quotes on last resume line. And both Slackware boot stanzas have the missing quote.

```
 menuentry "Slackware_13.37 (on /dev/sda2)" --class gnu-linux --class gnu --class os {

 insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 0a2ebb07-8b93-4938-9bee-7eca19168eee
linux /boot/vmlinuz root=UUID ro  vt.default_utf8=0 vga = normal append = [COLOR=#ff0000]"[/COLOR]resume=UUID=9a4b8b62-9163-4d61-b9af-4d4c75e29fee

 }
```

The lilo  (line 398 in BootInfo) has both quotes, so it is a bug in  os-prober. You really should file that as a bug report.

In the mean time you have several alternatives. I would just copy all of the os-prober output into 40_custom and correct it there and turn os-prober off. You may have to manually update on changes to your other systems later, but then every update of kernel or grub will not overwrite a direct edit to grub.cfg. Or you can edit the file we are not supposed to edit - grub.cfg.

 Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit only titles:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub


Either of these will turn os-prober off.
 gksudo gedit /etc/default/grub:
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

---

### Post by oldfred on 2013-06-22
You do have to create a login to launchpad.

 bug reports info on how to do:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
[http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem)


I did not find a lilo or quotes missing bug for os-prober.
Grub bugs:
[https://bugs.launchpad.net/ubuntu/+source/grub2](https://bugs.launchpad.net/ubuntu/+source/grub2)

---

### Post by firekage on 2013-06-22
> **oldfred said:**
> Slackware as copied by grub2's os-prober has a typo. So all your entires after the typo will not show. 
It is unmatched quotes on last resume line. And both Slackware boot stanzas have the missing quote.


Yes, somebody, if i remember correctly, on LinuxQuestions, wrote the same thing. Funny thing is that clean install of Ubuntu sees them all, and after something, maybe update, it doesen't - my laptop sees Vosta and Slackware 14!


```
 menuentry "Slackware_13.37 (on /dev/sda2)" --class gnu-linux --class gnu --class os {

 insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 0a2ebb07-8b93-4938-9bee-7eca19168eee
linux /boot/vmlinuz root=UUID ro  vt.default_utf8=0 vga = normal append = [COLOR=#ff0000]"[/COLOR]resume=UUID=9a4b8b62-9163-4d61-b9af-4d4c75e29fee

 }
```

> The lilo  (line 398 in BootInfo) has both quotes, so it is a bug in  os-prober. You really should file that as a bug report.

Will try it later. But what is wrong with Vista? Why it doesen't show either?

> 
In the mean time you have several alternatives. **I would just copy all of the os-prober output** 

Could you write more? What is the output of this, or where, and how should i check it? 

> 
into 40_custom and correct it there and turn os-prober off. You may have to manually update on changes to your other systems later, but then every update of kernel or grub will not overwrite a direct edit to grub.cfg. Or you can edit the file we are not supposed to edit - grub.cfg.


I have only to copy something here or make new 40_custom ?
> 
 Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit only titles:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub


Either of these will turn os-prober off.
 gksudo gedit /etc/default/grub:
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

You wrote: correct only titles. What do you mean? What titles?

---

