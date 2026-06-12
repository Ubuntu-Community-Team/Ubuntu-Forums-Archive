---
title: "Windows not booting?"
date: 2007-08-13
forum: General Help
---

### Post by mike868y on 2007-08-13
I installed wubi and was loving it. Then one day i was meaning to boot into windows and accidentally choose ubuntu. As ubuntu was booting up i hit the power button on my comp. Now, when i try and boot into windows i get an error message stating that windows failed to start and i am given options (boot into safe mode, safe mode with network connections, safe mode with command line) NO matter which one i choose a few screens pop up and my computer attempts to restart? what do i do?

---

### Post by diatribe on 2007-08-13
what do the screens that pop up say?

---

### Post by carmany on 2007-08-13
Boot into safemode and uninstall ubuntu restart comp and it should work

---

### Post by mike868y on 2007-08-13
This is for my friennd, he is in dc, so i'm not sure on the specifics, but apparently when he tries to boot into safe mode the comp just reboots back to the same screen?

---

### Post by misfitpierce on 2007-08-13
It's a sign for the complete move to linux :) lol

---

### Post by omegamike3 on 2007-08-13
what you'll want to do is boot into the recovery console and run chkdsk, you can also look into BartPE, it's basically a much fancier form of the recovery console with a lot more options/features. basically, windows is just freaking out because you didn't let it do what it wanted to and until you run chkdsk, it's just going to ignore the hdd. (in a matter of speaking, yes it is more technical but who gives a hoot, it's windows, i have to support this crap all day long :P)

---

### Post by mike868y on 2007-08-13
how do i boot into recovery console? what will chdisk do?

---

### Post by omegamike3 on 2007-08-13
> **mike868y said:**
> how do i boot into recovery console? what will chdisk do?

booting of the install disk will get you there, or if there is a recovery disk already made, that's the best choice, otherwise BartPE will get you there as well.
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)
chkdsk does just as the name implies, it checks the disk to make sure there aren't any errors and attempts to either fix them or simply marked them so sectors can be ignored. you'll want to use the /f flag so chkdsk knows to repair the bad sectors
```
chkdsk /f
```

---

### Post by mike868y on 2007-08-13
ok.. so will it erase my dual boot? or will i still have it?

---

### Post by ubromtoo on 2007-08-14
Omegamike3 :

     I've been running a dual-boot Win XP Home SP2 / Dapper

for several months now, and recently used Wubi to install Feisty

as well.  All was well for a couple of weeks , but then there was a

real problem with Feisty (the toolbars/taskbars just vanished) so I

did a hard powerdown of Feisty.

     Now Dapper still boots fine (it is the default), but when I choose

Windows or Feisty , the PC simply restarts.  I can choose Windows

Recovery Console but there's no sign of a command line, so I stop

when I get to the "all files will be lost " screen.

     What to do?  All help will be greatly appreciated  [-o<[-o<[-o<

---

### Post by mike868y on 2007-08-14
ok well apparently my friends comp will not boot into anything.. it goes to the error screen right after the hp splash screen?

---

### Post by ago on 2007-08-14
You have to run the chkdsk command as mentioned using the windows cd.

---

### Post by ubromtoo on 2007-08-14
My PC came with Windows preinstalled, so there isn't any disc.

     Some time ago the computer prompted me to burn a two-disc

set of recovery discs, and I've tried to use those to get to a command

line, but the "all files will be lost " screen has made me stop; how do

I just find the command line, without doing a full HDD wipe?

---

### Post by ago on 2007-08-14
see if that helps: 

[http://support.microsoft.com/kb/315265](http://support.microsoft.com/kb/315265)
[http://technet.microsoft.com/en-us/library/bb457122.aspx](http://technet.microsoft.com/en-us/library/bb457122.aspx)

the easiest way is probably to borrow a windows cd and boot into recovery console

---

### Post by omegamike3 on 2007-08-14
> **ago said:**
> the easiest way is probably to borrow a windows cd and boot into recovery console

or if you can't borrow one, using BartPE will also work quite well, as it can offer you many more options beyond the recovery console through it's plugin system.
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

---

### Post by clive_pearce on 2007-08-15
Instead of using BartPE get ubcd4win [http://www.ubcd4win.com/index.htm](http://www.ubcd4win.com/index.htm)

This is based on BartPE. It  has an option to boot to a recovery console.

---

### Post by mike868y on 2007-08-16
ok my friend is not 100% sure if he has his xp disk. I have a purple "reinstallation CD microsoft windows xp home edition including service pack 2" from dell that came with my comp. Could i boot off that in order ot get into recovery console?

---

### Post by mike868y on 2007-08-16
Ok, i booted of my xp cd, ran chkdsk and now i can boot into xp just fine. However, when i go to boot into ubuntu it stalls on the first splash screen. Any recomendations, or should i just reinstall wuuubi

---

### Post by ago on 2007-08-17
I'd try to reinstall, since when windows filesystem gets corrupted also the ubuntu one can be affected

---

### Post by mike868y on 2007-08-17
thank you, everything is working fine now. I ran chkdsk, wlhich allowed me to boot into xp, uninstalled wubi, then reinstalled

---

### Post by ubromtoo on 2007-08-21
Have re-installed Win XP, and will give Wubi another shot, now

that I have a BartPE disk handy.

     The trouble came about because , while I was in Wubi/Feisty ,

the toolbar & Taskbar just vanished, &  I did not know how

to access the Command Line to do a shutdown.

     So, what key combination can I use to make a terminal show up,

if the same thing happens again?

                     Thanks

---

### Post by ago on 2007-08-22
[http://linux.about.com/od/linux101/l/blnewbie5_1.htm](http://linux.about.com/od/linux101/l/blnewbie5_1.htm)


<Ctrl><Alt><F1> 
<Alt><SysRq> <???>
<Ctrl><Alt><BkSpc>

---

### Post by hh93 on 2007-08-22
Hi Ubromtoo,

Happened to me once after beryl installation, panic......, but, i remembered that wubi is sensitive to hard reboot. I pressed Ctrl-Alt F1 (or F2-F6) to get to terminal, and type sudo reboot. Oh ya, to get back to GUI press Ctrl-Alt F7. Better yet, in addition to link ago suggested, do give the guide in the following link a read, [http://users.bigpond.net.au/hermanzone/p10.htm#to_prevent_filesystem_damage](http://users.bigpond.net.au/hermanzone/p10.htm#to_prevent_filesystem_damage) 

Hope this helps.

Cheers!
hh93

---

### Post by ubromtoo on 2007-08-22
Ago & hh93 :

     Thank you both for your help, and for those links ...they look

very helpful .

      Wish me luck, I'm off to see the Wubi (lol)     :guitar:

---

### Post by Sproid on 2008-04-05
Hi,
How do I boot in windows safemode? My option in grub are ubuntu, ubuntu recovery and vista. If I choose vista it start loading. Where is the menu to choose windows normally or safemode??

---

