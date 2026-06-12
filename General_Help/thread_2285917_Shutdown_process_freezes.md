---
title: "Shutdown process freezes"
date: 2015-07-09
forum: General Help
---

### Post by brogioloedoardo on 2015-07-09
I'm using Lubuntu 15.04 on a Lenovo Essential B50-30, a low-end machine. When I shut it down, after a few seconds (during which you can see the Lubuntu logo and dots "....") the screen just gets stuck (the colored dots beneath the logo not moving anymore), and I have to long press the power button to have it turned off. Am I damaging my pc? (Not really sure if the process is completed or the processor's still working).
Are you aware of any possible solution?

---

### Post by dino99 on 2015-07-09
indeed its a dirty way to shutdown, but when its the only choice you can do it safely

when this happen (may wait for an event that never comes) hit 'ESC' key to see the verbose comments, and know where it hangs. This can be made permanent by removing 'quiet splash' from /etc/default/grub, followed by 'sudo update-grub'

---

### Post by v3.xx on 2015-07-09
You could remove "quiet splash" to see whats going on.

[http://ubuntuforums.org/showthread.php?t=2084208&p=12359797#post12359797](http://ubuntuforums.org/showthread.php?t=2084208&p=12359797#post12359797)

---

### Post by limbenjamin on 2015-07-09
[FONT=Open Sans]Short term solution if it happens,

Holding down Alt and SysRq then slowly type REISUO.

No, I am not joking.

[/FONT]
[LIST]
[*]R: Switch the keyboard from raw mode to XLATE mode
[*]E: Send the SIGTERM signal to all processes except init
[*]I: Send the SIGKILL signal to all processes except init
[*]S: Sync all mounted filesystems
[*]U: Remount all mounted filesystems in read-only mode
[*]O: Immediately shutdown the system, without unmounting partitions or syncing
[/LIST]

---

### Post by tier on 2015-09-13
Have same problem with Lenovo b50-30 and Xubuntu 14.04.3 :( 'acpi pcc probe failed' on boot screen, but on poweroff screen I do not see the problem. Just power does not turn off (like windows 95).

---

### Post by zabalajulen on 2015-09-21
Hi everyone!!
Have the same problem with my new Lenovo B50-30 (E2840, 4GB Ram and Atom Processor graphics Z36xx family) and Ubuntu 15 amd64 (also tried with 14.03 x86 and Fedora, now I'm gonna try with other distros), it freezes when shutting down or rebooting. I've tried editing grub file and removing quiet splash, acpi=force, apm=power_off but nothing seems to work. But the most strange is that I bought a G50-30 some months ago and same os worked really well. 

Would appreciate any help.

 Thanks in advance

---

### Post by ragb1 on 2015-10-03
Hi:

Same problem here. I've got a lenovo b50-30 and I can't shutdown the computer. The shutdown proccess began, but if  freezes at the end of the process. I tried different versions and different distros, and in all cases is the same.

I hope for your answers.

Best regards.

---

### Post by ragb1 on 2015-10-04
Hi again:

Finally I solved it!!! The problem was a bug in the BIOS/UEFI firmware (my laptop was using v. 2.08). You have to update the firmware (Windows mandatory for this step) up to the final release (v. 2.11 at this point). After that, I can finally make a clean shutdown.

Hope it helps.

Best Regards.
Raul.

---

### Post by ale3andro on 2015-10-21
Thank you so much for the fix! It saved my life.
Just after applying the BIOS update (from within Windows 10), the grub menu disappeared and I had to install grub-efi package again (live cd, chroot etc).

---

### Post by strk on 2015-10-27
> **ale3andro said:**
> Thank you so much for the fix! It saved my life.
Just after applying the BIOS update (from within Windows 10), the grub menu disappeared and I had to install grub-efi package again (live cd, chroot etc).

Could you please provide the DSDT obtained from the updated BIOS ?
sudo cat /sys/firmware/acpi/tables/DSDT > DSDT.aml

UPDATE: while lubuntu-15.04 suffer by this problem for me, trisquel 7.0 does not, even without upgrading the BIOS

FYI: Trisquel 7.0, shipping kernel 3.13.0-39-lowlatenc, does NOT suffer from the shutdown freeze, while Debian 8.0, shipping kernel  						3.16.0-4-686-pae, does

Ubuntu 14.04.03-amd64, shipping kernel 3.19.0-25-generic, also freezes

---

### Post by strk on 2015-10-28
I filed a bug upstream: [https://bugzilla.kernel.org/show_bug.cgi?id=106801](https://bugzilla.kernel.org/show_bug.cgi?id=106801)

---

### Post by ale3andro on 2015-10-30
Hello again,
DSDT.aml as requested can be found [https://www.dropbox.com/s/fiumj74af4094cz/DSDT.aml?dl=0](https://www.dropbox.com/s/fiumj74af4094cz/DSDT.aml?dl=0)
Hope it helps

---

### Post by claudiologiudice on 2015-11-12
Hello,
have you solved with dsdt.aml?
I've just bought this freedos pc and I would like to install ubuntu.

---

### Post by ale3andro on 2015-11-12
Yes after the BIOS upgrade grub2 works fine for dual booting Ubuntu and Windows 10.
The only problem is that you have to install Windows 10 first, so that you make the BIOS upgrade from within Windows.

---

### Post by claudiologiudice on 2015-11-12
Someone in other forum said that upgrading your bios doesn't allow to install win7 in dual boot, can you confirm?
Could you also please explain me how to make the bios upgrade from windows?
Thanx in advance.

---

### Post by ale3andro on 2015-11-12
I don't know about Windows 7, I haven't tried it.
But you can definitely install Windows 10, download the update from the official page (where you can get the drivers too) and apply the BIOS update. 
After that you can normally install Ubuntu (EFI mode) and dual boot

---

### Post by claudiologiudice on 2015-11-12
Thanx for your kind explanation.
But i don't understand how to install bios update. Could you please attach the file you used? Or a link?
There is a file on lenovo support website?

---

### Post by ale3andro on 2015-11-13
I have the Lenovo B50-30 and the BIOS (ver. 9CCN33WW(V2.11)) is available at
[http://support.lenovo.com/us/en/products/laptops-and-netbooks/lenovo-b-series-laptops/lenovo-b50-30-notebook](http://support.lenovo.com/us/en/products/laptops-and-netbooks/lenovo-b-series-laptops/lenovo-b50-30-notebook)
You must select BIOS from the Component drop-down menu.
You download the Flash bios update file and just execute it from Windows. There is nothing more to it.

---

### Post by claudiologiudice on 2015-11-13
Thank you.
Did you have problems with your wifi card?

---

### Post by ale3andro on 2015-11-16
No problem with the wifi. Works out of the box.

---

### Post by Zeljko_Kostic on 2015-12-08
I installed couple of distros before I found this solution, about to update bios. I have a question for those of you who did it already: Do you see any speed improvements after updating it? My boot time is slower on all the distros I've tried (Ubuntu, Fedora, Mint, Kubuntu) than on win 10 I have installed, and I'm not used to windows being faster (lol). I know it's a still thread, but I'd appreciate an answer. Thanks in advance

---

### Post by ale3andro on 2015-12-08
Well I can't answer this question because I don't use the Windows 10 Installation so much. But doesn't this depend on the startup applications too?

---

### Post by Zeljko_Kostic on 2015-12-08
I'm talking about fresh installs. Maybe it's the incompatibility with the old bios that's slowing them, but, none the less it's something puzzling to me. I will report boot times in a couple of days, when I get it running and set it up properly and to my liking.

---

### Post by powerman2 on 2015-12-29
> **brogioloedoardo said:**
> I'm using Lubuntu 15.04 on a Lenovo Essential B50-30, a low-end machine. When I shut it down, after a few seconds (during which you can see the Lubuntu logo and dots "....") the screen just gets stuck (the colored dots beneath the logo not moving anymore), and I have to long press the power button to have it turned off. Am I damaging my pc? (Not really sure if the process is completed or the processor's still working).
Are you aware of any possible solution?

As this appears as one of the first Google results relating to this problem, I'm gonna beat the poor dead horse.

The problem may or may not be related to a new driver in kernel versions 3.19 and up. Reverting to linux-image-3.16 solved it for me. The machine now shuts down and reboots normally.

Reconfiguring and recompiling the kernel also should solve it, if this is indeed the source of the problem. Haven't tested that yet. My machine is Lenovo cheap business B50-10 with Insyde UEFI. It does come with some sort of UEFI mailbox device type of thing, at least in Windows Downloads they list a driver for that.
 [URL="http://askubuntu.com/questions/584248/boot-error-acpi-pcc-probe-failed"]Source


[/URL]

---

### Post by powerman2 on 2015-12-29
> **ale3andro said:**
> Yes after the BIOS upgrade grub2 works fine for dual booting Ubuntu and Windows 10.
The only problem is that you have to install Windows 10 first, so that you make the BIOS upgrade from within Windows.

Does [this process]("https://forums.lenovo.com/t5/Welcome-FAQs-Knowledge-Base/How-to-flash-InsydeH2O-EFI-under-DOS-enviroment/ta-p/278406") not work for you? Haven't yet tested this as I used Windows 8.1 to update my UEFI on Lenovo B50-10. Similar method for HP 250 G3 worked. Be very attentive and methodical. As per Lenovo's platform.ini, backing up might not work [this way]("https://forums.lenovo.com/t5/Welcome-FAQs-Knowledge-Base/How-to-backup-your-InsydeH2O-EFI-before-flashing-a-new-one/ta-p/261119") but there is an option to enable backflash inside UEFI.

---

### Post by cyrillefunes on 2016-01-04
Hello,

I have the same trouble with a b50-30. Do you know if i could flash the bios using FreeDos, and how ?

Thanks a lot

---

### Post by StingerMD on 2016-02-16
Greetings,

I've registered just to post the solution that worked for me, hopefully it would be helpful to someone.

(first the solution, story below :)

Lenovo B50-30 with Ubuntu 14.04, same symptoms: not shutting down, not rebooting.

Go to bios, last tab:
"OS Optimized Defaults" set it to "Win8 64bit" or "Enabled" (based on your Bios version)
Hit "Load default settings" (not totally sure it's required).

Save and exit

After this the power works as expected. (although it's unexpected since it's not win8 we're using :D

It has something to do with UEFI/legacy compatibility and it solved the issue for me.


And now, the story
I've been struggling with this issue for a good couple of hours today, and none of the solutions posted here or on other forums/blogs helped (including bios update as someone mentioned).

I was so stubborn to fix it because it's the second laptop of this make/model in our office and the first one (which I've set up a couple of weeks before) works totally fine, and I knew it's not a global and unsolvable bug.

The laptop was brand new with FreeDOS and I can't remember whether it came with this setting set this way from factory or I have changed it thinking "I'm not installing Win8" :)
We have one more in the box and I'll check if I get curious enough :)

I also have an assumption about why BIOS update was helpful to someone - it resets settings to their defaults, and if they changed it before it has thrown it back to win8. 


Please, let me know if it helped you, it will make me feel better about the time wasted into hunting this issue :)

---

### Post by flint3 on 2016-02-25
Hey StingerMD, thank you so much this is it! It took me 3 days and your solution was the only one that worked for me.

---

### Post by jolfig on 2016-11-07
> **brogioloedoardo said:**
> I'm using Lubuntu 15.04 on a Lenovo Essential B50-30, a low-end machine. When I shut it down, after a few seconds (during which you can see the Lubuntu logo and dots "....") the screen just gets stuck (the colored dots beneath the logo not moving anymore), and I have to long press the power button to have it turned off. Am I damaging my pc? (Not really sure if the process is completed or the processor's still working).
Are you aware of any possible solution?

Its a common problen with GRUB2 configuration file
Edith this with:
```
sudo nano /etc/default/grub
```
change the line: GRUB_CMDLINE_LINUX_DEFAULT with
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force apm=power_off"
```
and update GRUB with
> sudo update-grub

---

