---
title: "Preparing an SSD for cloning existing dual boot system"
date: 2016-08-17
forum: General Help
---

### Post by makem2 on 2016-08-17
I have Windows 10 and xubuntu dual booted on a small EeePC netbook and want to replace the existing 250gb HD with a 250gb SSD.

I understand I should first prepare the SSD to ensure long life and faster operation.

Can anyone point me to a guide? I used to have a good one at home but now an in China for a few weeks and want to upgrade the netbook whilst I am here.

---

### Post by oldfred on 2016-08-17
I have used these in the past. You do need AHCI mode in UEFI/BIOS for trim to work.
 [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd) 
      
 [http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/) 

With new SSD, life is comparable to HDD.

I change Ubuntu's trim to my own script so I also have a log file.

 Shows both discard (not recommended) & fstrim methods for trim and script with log
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html) 

And I typically do not fully use entire drive. Parts are still unpartitioned/unformatted. Or over-provisioned.

---

### Post by makem2 on 2016-08-17
Thank you for your response. Google is banned in China but I will use the other links ad retain the google one for my return.

---

### Post by oldfred on 2016-08-18
The summary of Google:


[LIST]
[*][**1 **Avoid exaggerated measures]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Avoid-exaggerated-measures")
[LIST]
[*][**1.1 **Alignment is not necessary anymore]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Alignment-is-not-necessary-anymore") 
[/LIST]
  
[*][**2 **BIOS and UEFI: set it to AHCI]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-BIOS-and-UEFI:-set-it-to-AHCI") 
[*][**3 **Check for updated firmware]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Check-for-updated-firmware") 
[*][**4 **Avoid quick wear: reduce write actions]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Avoid-quick-wear:-reduce-write-actions") 
[*][**5 **Optional: reserve some space for overprovisioning]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Optional:-reserve-some-space-for-overprovisioning") 
[*][**6 **During installation: select EXT4]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-During-installation:-select-EXT4") 
[*][**7 **After the installation: noatime]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-After-the-installation:-noatime") 
[*][**8 **Still relevant for Ubuntu 16.04 and Linux Mint 18: select your TRIM method]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Still-relevant-for-Ubuntu-16.04-and-Linux-Mint-18:-select-your-TRIM-method")
[LIST]
[*][**8.1 **Outdated method (no longer recommended): by rc.local]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Outdated-method-no-longer-recommended-:-by-rc.local") 
[*][**8.2 **Preferred method: daily by cron]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Preferred-method:-daily-by-cron")
[LIST]
[*][**8.2.1 **How to undo (back to a weekly cron job)]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-How-to-undo-back-to-a-weekly-cron-job-") 
[/LIST]
  
[*][**8.3 **Not advised: by discard]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Not-advised:-by-discard") 
[/LIST]
  
[*][**9 **How to execute TRIM manually]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-How-to-execute-TRIM-manually") 
[*][**10 **Limit swap wear]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Limit-swap-wear") 
[*][**11 **Almost ready after reboot]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Almost-ready-after-reboot") 
[*][**12 **Limit the write actions of Firefox]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Limit-the-write-actions-of-Firefox") 
[*][**13 **Limit the write actions of Chrome and Chromium]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Limit-the-write-actions-of-Chrome-and-Chromium") 
[*][**14 **Check whether the scheduler is set to deadline]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Check-whether-the-scheduler-is-set-to-deadline") 
[*][**15 **Do NOT enable hibernation]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Do-NOT-enable-hibernation") 
[*][**16 **Also for an SSD: prevent fragmentation, and DO NOT defrag]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Also-for-an-SSD:-prevent-fragmentation-and-DO-NOT-defrag") 
[*][**17 **Dual boot? Don't let Windows kill your SSD]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Dual-boot-Don-t-let-Windows-kill-your-SSD") 
[*][**18 **Enjoy your SSD carefree for years and years]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Enjoy-your-SSD-carefree-for-years-and-years") 
[*][**19 **Want more tips?]("https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Want-more-tips-") 
[/LIST]

Main things I do is use gpt and AHCI, alignment & deadline scheduler are defaults now. I add noatime to fstab to reduce writes, and create my own script for trim in daily (as other link above).
Some add temporary files or temporary files for Browsers to fstab and use RAM not cache on SSD. If lots of RAM that probably is a good idea. If you have lots of RAM, you will not use swap anyway, so swap size/setting does not matter.

---

### Post by gordintoronto on 2016-08-18
Hi Fred,

I set up an SSD as GPT (on a BIOS system) and ran into trouble setting up a Windows 10/Mint 18 dual boot system. Had to revert to msdos in gparted. Now it's amazing.

---

### Post by oldfred on 2016-08-18
Yes, if you are dual booting with Windows on same drive, you can only use gpt if booting in UEFI mode.
Windows only boots from gpt with UEFI.
Windows only boots from MBR with BIOS. 
And vice-versa.

I had first drive converted to gpt back with 10.10, but still had XP then on a MBR drive.

---

### Post by gordintoronto on 2016-08-18
Thanks, oldfred.

---

### Post by makem2 on 2016-08-20
I need a step-by-step guide to preparing the ssd as all the provided links start from google which I cannot access until september :-(

It is hard enough waiting for pages to load while the great firewall of china checks then.

As far as I am aware the EeePC just has an mbt, no mention of UEFI

---

### Post by oldfred on 2016-08-20
If only installing Ubuntu, you can use gpt but must also have a bios_grub partition for grub to install correctly. The use of the newer gpt is just a general recommendation.

Make sure BIOS is set to AHCI. Otherwise trim will not work.

Edit fstab & add noatime and perhaps tmpfs if you have lots of RAM.

 An adapted line may look like this:
UUID=xxxxx   /   ext4 [COLOR=#ff0000]noatime,[/COLOR]errors=remount-ro   0   1 

   # Reduce SSD wear
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0 

I manually ran trim for quite a while:

 fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed 

      
 [http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)
sudo nano /etc/cron.daily/trimSSD
sudo chmod +x /etc/cron.daily/trimSSD 
   #!/bin/sh
# trimSSD
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
# fstrim -v /home >> $LOG

Google suggests moving the default weekly to daily, I just turn off weekly as I also like to have the log:
[COLOR=#0000FF]sudo mv -v /etc/cron.daily/fstrim /etc/cron.weekly/fstrim

[/COLOR]

---

