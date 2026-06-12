---
title: "Grub and/or screen problem kubuntu/xp dual boot"
date: 2013-01-15
forum: General Help
---

### Post by TheChristianHippie on 2013-01-15
About a month ago I partitioned my HDD and installed kubuntu to dual boot with windows xp. Everything works great and I LOVE it! 

Yesterday I partitioned my daughter's computer HDD using parted magic and installed edubuntu 12.04. It installed well, updated well. It needed a reboot for an update and on reboot the emachines splash screen comes up with it's bios choices, then a screen of text until "boot from cd..." option and then the screen goes black. It comes back on dark and difficult to see, a large red box asking "are screen settings correct?" comes on and behind it it looks like a screen with lots of interference, text ultra-tiny, and half the image is off screen. Then it goes black again... and a few seconds later edubuntu loaded happily and functioned again perfectly.

I googled a bunch and searched these forums, found nothing particularly helpful or similar to my problem (prolly cause I'm an ultra-n00b" and can't find anywhere to enter any terminal commands I saw suggested, nor could I understand fixes that resulted in [solved] tags on threads) so I put a kubuntu 12.04 disc in and installed it over edubuntu (formatted the edubuntu partitions and installed kubuntu on them). I hoped that would fix the issue if it was an edubuntu problem and it would also re-install grub, but no dice. She needs to access her XP partition for a school program, but we never see grub in order to choose the xp OS. Before installing edubuntu/kubuntu and after partitioning, I had tested to make sure xp would still load and it had. But now we don't get that choice because we can't see it. Everyday we can't access xp is a day behind in her school work :( I'd hate to abandon edubuntu/kubuntu on her puter since it's really a great OS and would be a great supplement to her studies with it's great educational games/software!

We tried pushing "n" and "enter" while the red box was up, but it ignores us.

I need a seriously detailed "idiot's guide" walk through. :redface: I am brand new to linux.

Here's her setup, let me know if you need more info and how to get it to you. And thanks!

She has a VERY OLD early 90's monitor attached to the onboard video card. 
Windows XP on sda1
Windows recovery on sda2
sda3 is the extended partition
kubuntu /home ext3 partition on sda5
kubuntu / "root" ext4 partition on sda6
sda7 is swap

Her partition setup, kubuntu installation (except the edubuntu desktop environment), and computer model are identical to mine (except I have a Dell flat screen monitor), and mine is working perfectly, I see grub and can choose and load xp or kubuntu easily.

Please help? I will check this thread frequently till 11pm tonight, but I won't be available until tomorrow evening late since I have work. Thank you for your time/patience! ):P

---

### Post by TheChristianHippie on 2013-01-15
Ok. I used super grub disc to boot into the windows partition. It booted fine, she can now do her schoolwork.

But I'd really like to have a normal visible grub menu to choose between OS's and boot each normally, rather than have to click through the complicated super grub disc.

Also, kubuntu for some reason froze during "tux paint" and we couldn't get it to do anything. I hit "ctrl-alt-del" since that's what I always do in windows and it's habit, and a window asking if I'd like to restart popped up. I clicked it and the window closed and it hung. Finally I turned off the puter (by holding down the "on/off" button). I restarted it with the kubuntu liveCD in the drive and it came up asking if I'd like to install, and gave no repair boot option or anything like I'd been seeing in suggestions while googling this problem so I hit "cancel" install and the computer restarted and hung in a black screen. I turned it off and turned it back on and this time the kubuntu disc gave me a "start kubuntu", memory test check disc for errors, or "boot from hard disc" option and I chose "boot from hard disc" and it hung on the black screen again. I turned it back off. At this point I put in the super grub disc and booted into windows.

I'm probably digging my hole deeper :oops: I'll leave it in windows and not turn it off again until I get some help! :)

Hope to hear from someone soon! ):P

---

### Post by TheChristianHippie on 2013-01-21
Still waiting.... checking daily.....

---

### Post by oldfred on 2013-01-21
Grub tries to use the video mode of your system, so it may have issues with video? How much RAM does system have?

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by TheChristianHippie on 2013-01-22
Thankyou for your reply! I will get right on that tonight! I will post info as I get it!

Again, thank you! :)

---

### Post by TheChristianHippie on 2013-01-28
SOLVED!! :guitar:

I installed a different (almost as old) monitor thinking perhaps it was a hardware issue. The new monitor's error screen was easier to read/understand. It said something to the effect of "frequency incorrect" or "out of range" something like that. So I googled it and found a thread that discussed editing the grub file in etc/default/grub (I think) and I couldn't modify it. So I googled around on how to do that and found "grub customizer"!!! That program allowed me to set the screen resolution as "custom" and I reset it from some 6**x4** resolution to 800x600 and now WE SEE GRUB!!!!

Thank you for your help oldfred! It was a simple screen resolution mismatch and grub customizer fixed it :)

Maybe someone else with this problem will stumble on this thread and find the fix easier than they thought it would be too :lolflag: !

---

### Post by oldfred on 2013-01-29
Glad you found a solution.

Many use Grub Customizer and find it works.

But Boot-Repair can also reset grub video to default 640x480 to get you to see screen.

---

### Post by TheChristianHippie on 2013-01-29
That was the original setting, 640x480. Our aged monitors couldn't display that range. 800x600 is apparently a pretty safe resolution to set grub to for older monitors, though maybe some can handle 640x480. Just not our two ;) Thanks again! ):P

---

