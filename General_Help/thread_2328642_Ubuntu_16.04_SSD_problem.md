---
title: "Ubuntu 16.04 SSD problem"
date: 2016-06-23
forum: General Help
---

### Post by raul27 on 2016-06-23
Hey everyone! 
I have just to buy a SSD and i installed Windows 10 and Ubuntu 16.04 on it. 
If I am using Windows i dont have problem, I mean everything is going well but when i try to use Ubuntu my 
laptop is so so slow, its impossible to do two things at the same time or whatever. Also the temperature rise too much. 
I tried to configure SSD (Trim option) but i continue with the same problem, also i tried to change SATA configuration to IDE but the same. 
I know that the problem is not with my SSD because i can work with Windows without these problems. 

Any opinion to solve this problem?

Edit: I have just to see that when i run my laptop i can see the following message: Temperature above threshold... ok so maybe this is the problem but then, why windows is working well?

---

### Post by oldfred on 2016-06-23
What brand, model system?
And what video chip/card?

Often related to having correct or newest video drivers.

---

### Post by cariboo on 2016-06-23
Moved to General Help, as we are now testing Yakkety.

---

### Post by raul27 on 2016-06-24
> **oldfred said:**
> What brand, model system?
And what video chip/card?

Often related to having correct or newest video drivers.

Hi, thanks so much for your answer. 
It is a ASUS K53SD, and the video card is NVIDIA GEFORCE 610M 

Also i tried other linux distribution (linux mint, debian also) but i continue having the same problem.

---

### Post by Linuxisfast on 2016-06-24
I have the same laptop running quite well under Ubuntu. Install nvidia driver, type additional drivers in Dash and select latest driver shown in the app, reboot and then type nvidia-settings in dash and under nvidia-prime, turn off nvidia card and re-login in. Also make sure to install TLP.

---

### Post by oldfred on 2016-06-24
sAsus needs boot parameters. pci=nomsi 
And with nVidia you may need nomodeset, but depending on model & version of Ubuntu you may be booting with Intel and need an Intel parameter.  Then with nVidia driver can switch.

 Asus x555u w/o pci=nomsi - space issue on drive and runaway log files
[http://ubuntuforums.org/showthread.php?t=2327103&page=3](http://ubuntuforums.org/showthread.php?t=2327103&page=3)
[http://ubuntuforums.org/showthread.php?t=2327570](http://ubuntuforums.org/showthread.php?t=2327570)
Installing 15.04 on Asus N550JX, boot parameters required
[URL="http://ubuntuforums.org/showthread.php?t=2293394"]http://ubuntuforums.org/showthread.php?t=2293394
[/URL]
 Asus M32CD desktop - Skylake several boot parameters  pci=nomsi  i915.preliminary_hw_support=1
[http://ubuntuforums.org/showthread.php?t=2312977](http://ubuntuforums.org/showthread.php?t=2312977) 

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
      
 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size 
    [URL="http://ubuntuforums.org/showthread.php?t=2293394"]
[/URL]

---

### Post by banceu_sergiu_ione on 2016-06-24
You might want to disable * Fast Startup * option from windows 10 too. Check if make any difference ( for me it did )

As others said make sure you run the proprietary drivers, select Canonical Partners PPA on other software , select all options shown on ubuntu software. To do this go in System Settings /Software & Updates and select what need to be selected and install proprietary drivers. It might be needed a reload of the of Software & Updates to be able to see the proprietary drivers.
Reboot

Open a terminal and run:

to install ubuntu-restricted-extras run the command

> sudo apt install ubuntu-restricted-extras

for common tools run

> sudo apt install linux-tools-common

to update run the command

> sudo apt update && upgrade

i use to reboot after if upgrades had been done and when i log in back i do a clean

to clean run the commands 

> sudo apt autoclean
> sudo apt autoremove

if had been installed lots of things i run trim after

> sudo fstrim --all or > sudo fstrim -v / reboot and have fun 

As if you think your SSD not run properly you can run same benchmark with [phoronix]("https://wiki.ubuntu.com/PhoronixTestSuite"), i used pts/fio ([my results]("https://openbenchmarking.org/result/1606246-HA-HYPERXSAV65") iif you want to compare) but before you do any test make sure your system is setup.

Open a terminal:
Check if the OS know you have a SSD, run the command :

> for f in /sys/block/sd?/queue/rotational; do printf "$f is "; cat $f; done

the output must be : /sys/block/sd*/queue/rotational is 0 . where sd* is your mount path

Check the scheduler is set on deadline or noop, run the command:

> for f in /sys/block/sd?/queue/scheduler; do printf "$f is "; cat $f; done

recommended on deadline /faster for bencmark on noop 
if it is on cfq the switch with > echo deadline > /sys/block/$YOURDRIVE/queue/scheduler
or echo noop if you're for faster

Check if relatime is set ( wich should already be as it is a default )

> cat /proc/mounts

Same ppl say its better noatime since reduce even more drasticaly the writes on SDD.. but it does not matter really for me. If you want you can switch to noatime.. just see online how to.

Once more important to is to reduce the swampiness, if you have alot of ram you can put it to 1 ( i dont say 0 since it might help to still have access at it ) Mine is set to 30.

You set it by open the /etc/sysctl.conf and add at the end of the file vm.swappiness = 30

I used gksudo , if you want you have to install it or just go for nano if like

> gksudo gedit /etc/sysctl.conf

You might want to check the cpu too

moduls to loud:
Open a terminal and simply run > sudo modprobe msr and > sudo modprobe cpuid
Now from terminal install cpupower and turbostat. 
> sudo apt install cpupower > sudo apt install turbostat
Run update & upgrade/ reboot if needed.
Log in back terminal and run cpupower

> sudo cpupower frequency-info check if boost is activeted and the frequencies set to run
use > sudo turbostat to get a real time frenquency and used of cpu while running sama application ' openssl speed ' in a 2nd terminal if like to see.
Now you can run same benchmarck and see if your SSD run as it must to do. Go for phoronix pts/fio and see.

---

### Post by raul27 on 2016-06-24
> **banceu_sergiu_ione said:**
> You might want to disable * Fast Startup * option from windows 10 too. Check if make any difference ( for me it did )

As others said make sure you run the proprietary drivers, select Canonical Partners PPA on other software , select all options shown on ubuntu software. To do this go in System Settings /Software & Updates and select what need to be selected and install proprietary drivers. It might be needed a reload of the of Software & Updates to be able to see the proprietary drivers.
Reboot

Open a terminal and run:

to install ubuntu-restricted-extras run the command



for common tools run



to update run the command



i use to reboot after if upgrades had been done and when i log in back i do a clean

to clean run the commands 




if had been installed lots of things i run trim after

 or  reboot and have fun 

As if you think your SSD not run properly you can run same benchmark with [phoronix]("https://wiki.ubuntu.com/PhoronixTestSuite"), i used pts/fio ([my results]("https://openbenchmarking.org/result/1606246-HA-HYPERXSAV65") iif you want to compare) but before you do any test make sure your system is setup.

Open a terminal:
Check if the OS know you have a SSD, run the command :



the output must be : /sys/block/sd*/queue/rotational is 0 . where sd* is your mount path

Check the scheduler is set on deadline or noop, run the command:



recommended on deadline /faster for bencmark on noop 
if it is on cfq the switch with 
or echo noop if you're for faster

Check if relatime is set ( wich should already be as it is a default )



Same ppl say its better noatime since reduce even more drasticaly the writes on SDD.. but it does not matter really for me. If you want you can switch to noatime.. just see online how to.

Once more important to is to reduce the swampiness, if you have alot of ram you can put it to 1 ( i dont say 0 since it might help to still have access at it ) Mine is set to 30.

You set it by open the /etc/sysctl.conf and add at the end of the file vm.swappiness = 30

I used gksudo , if you want you have to install it or just go for nano if like



You might want to check the cpu too

moduls to loud:
Open a terminal and simply run  and 
Now from terminal install cpupower and turbostat. 
 
Run update & upgrade/ reboot if needed.
Log in back terminal and run cpupower

 check if boost is activeted and the frequencies set to run
use  to get a real time frenquency and used of cpu while running sama application ' openssl speed ' in a 2nd terminal if like to see.
Now you can run same benchmarck and see if your SSD run as it must to do. Go for phoronix pts/fio and see.

First of all I need to say thanks to all of you, you are the best. 

OK  so I started upgrading my drivers, how? Using ppa and after that installed the last version from settings.

But now, when I reboot my computer it's impossible to log in. I mean the computer says: wrong password but the password is fine because I try to log in using Ctrl Alt F1 and I can use my computer without graphical interface. 

And it's really hard to do anything because ubuntu is going really really bad when my computer temperature is increasing. 

Maybe should I try to install another version or what could I do ?

---

### Post by banceu_sergiu_ione on 2016-06-25
You can try 14.04 version if you want.

All of what i said previously, about updates and system check have nothing to do with the possibility of a password change or add new one. Wont even ask if you had type the password correct or should I?

Not really sure what happened but if you say that you can use Ctrl Alt F1 terminal try run as root > sudo su and see if a new pass fix it > passwd and change the password to a new one ( do not forget it ).. get an easy one to see if work. you can get a better one after since you can run the command as many times you like.

try update Mesa too if you use it

check if you use it 

> glxinfo | grep "OpenGL version"

output :  OpenGL version string: 3.0 Mesa 12.1.0-devel - padoka PPA (git-6b0ac95) -----my output

add Padoka PPA

edit: can't get off of that face. you must type it all and replace the face with : p

> sudo add-apt-repository ppa:paulo-miguel-dias/mesa   that face is : p

then run update and upgrade 

> sudo apt update && upgrade

reboot.

For thermal you may want to check if your fan is clean or its integrity. Or get a pad-cooler.

---

### Post by QLee on 2016-06-26
> **banceu_sergiu_ione said:**
> 

edit: can't get off of that face. you must type it all and replace the face with : p

   that face is : p

If you use ```
 tags for code it will be shown as you want it to be.  [Edit] And be copy and pasteable.

[Code]sudo add-apt-repository ppa:paulo-miguel-dias/mesa 
```

---

### Post by raul27 on 2016-06-27
> **QLee said:**
> If you use ```
 tags for code it will be shown as you want it to be.  [Edit] And be copy and pasteable.

[Code]sudo add-apt-repository ppa:paulo-miguel-dias/mesa 
```


Hey again!  
So sorry for my delay, right now my laptop is running Ubuntu fluently. :D:D
Finally i follow all your instructions and now is going well, as you said, the problem was the graphical drives. 

So the problem is solved and now i only can say thanks, thanks, and thanks so much all of you for your time. 
I am very grateful to all of you.

---

### Post by banceu_sergiu_ione on 2016-06-27
I am gland its all good now. Enjoy it and mark as solved :)

---

