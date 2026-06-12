---
title: "Ubuntu 12.10 Boot problems(Boot Repair log)"
date: 2013-01-06
forum: General Help
---

### Post by cognition88 on 2013-01-06
Hi, first post, very new to Ubuntu(Linux as a whole really) But I have had Ubuntu 12.10(64bit) installed for a little over a week now and am experiencing problems on boot up. When my computer is started up, I am greeted with the grub 2 screen, with the following options: Ubuntu,advanced options for Ubuntu, and the 2 different memory test.  I beleave all my problems started with the installation of acidrip, and devede(both from the repository). I have since removed both of them(again via the repository). Everything seemed to uninstall fine so I did not note what the terminal kicked out. I can usually get into Ubuntu after selecting "Ubuntu" from that grub2 screen a couple of times after restarting.  

 I ran boot-repair per this [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and ended with the following URl [http://paste.ubuntu.com/1503119/](http://paste.ubuntu.com/1503119/). 

Im hoping this isn't hardware related but just in case

Intel core 2 extreme cpu
EVGA 790i ftw motherboard
4gb mushkin ram
EVGA GTX 260 grapthics card (not showing under All Settings then Details)
Intel 120gb SSD
 
(I may have missed something or other, will add if I remember)

---

### Post by oldfred on 2013-01-06
If you are consistently getting to grub menu, I do not think Boot-Repair will help. That is more for fixing grub issues. I might add a boot parameter if needed, but you did not need those before?

I would look in the logs to see if it is reporting anything. I look at dmesg and look for long times between entries, out right errors, or a drive trying to load multiple times & then maybe failing or working. Use Log File View or look in         /var/log/dmesg
    

Did you enable trim on SSD? And AHCI in BIOS?

---

### Post by cognition88 on 2013-01-06
No I did not enable trim on my ssd, or AHCI in my bios... Should I? I'm not quite sure what either of those are, but I will go and google them.

*Update* I did some reading and enabled trim. This made the Ubuntu load smoother after I select Ubuntu from the GRUB screen.   Unfortunately my motherboard only supports AHCI if I open the case and switch from NVIDIA on board controller to a Jmicron controller, and I've read that will slow my system down.  I'll do it is thought to correct this issue, but I would rather not.

---

### Post by oldfred on 2013-01-06
Trim does not work without AHCI. 

I have used this command and I think this poster believes it is a better way than trim. I ran this command as I had not enable trim initially and got these results.
       fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed
[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
sudo hdparm -I /dev/sdX
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

    
       [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
    
       With SSD or Flash drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.
change to noop i/o scheduler

---

### Post by cognition88 on 2013-01-06
Ok, thanks I'll try that when I get home(night shift) 

On a side note, would you call this a sloppy install? since this is only a week and some days old and I really don't have much on this system, could it be easier just to start over brand new and fresh?

---

### Post by cognition88 on 2013-01-08
Ok I have done everything from your last post and still get the "gnu grub 2.00" screen on boot up

---

### Post by oldfred on 2013-01-08
With only one system, you normally should not be getting the grub menu. That then is saying something is wrong.

Did you install the nVidia proprietary drivers from Ubuntu?

If you have not made a lot of changes, reinstall is an option. Either backup or if nothing to save just reinstall.

---

### Post by cognition88 on 2013-01-09
I haven't installed the nVidia drivers.  But I think I'm just going to go with a fresh install and use the link you gave me to completely wipe my SSD. I had windows 7 prior to this but was having a lot of trouble with the activation key(returned for a refund).  After that I'm not confident I did a proper wipe after reading the link from one of your post.  So I'll try that, I greatly appreciate all the help you have provided.  This is my first experience with Linux(unless you count Android) so I kind of expected a learning curve.

---

### Post by cognition88 on 2013-01-09
So I did a clean wipe([https://wiki.archlinux.org/index.php..._Cell_Clearing](https://wiki.archlinux.org/index.php..._Cell_Clearing)) and install and everything seems to be running great, no grub menu and all. I suppose the problem was when I didn't properly wipe my SSD after removing windows and installing Ubuntu.  I also opened my case and changed my SSD's connection to the correct SATA port to enable AHCI and thus trim. Thanks again for the help, I'll go ahead and call this solved

---

