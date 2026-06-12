---
title: "Ubuntu 14.04 won't shut down"
date: 2014-04-18
forum: General Help
---

### Post by orange2k on 2014-04-18
When I choose to shut down the computer, it won't shut down - it just hangs there and I have to do push the power off button on my computer to shut it down...

Yesterday I upgraded from 13.10 to 14.04 - I didn't have this problem with 13.10...

---

### Post by marco-prolog on 2014-04-18
I have the same problem, I'm on an old Fujitsu Siemens Amillo pro and upon upgrading to 14.04 when I try to shut down everything seems to work as it should apart that The computer remains idle without turning off once all the processes are closed.
It was fine on 13.10

---

### Post by Kevin Starkey on 2014-04-18
I had the exact same issue, but I found a fix that worked for me.

sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity

At first I thought it still wasn't shutting down, it normally takes 5 seconds, but for some reason it's taking like 30-60 seconds ...

---

### Post by marco-prolog on 2014-04-18
> **Kevin Starkey said:**
> I had the exact same issue, but I found a fix that worked for me.

sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity

At first I thought it still wasn't shutting down, it normally takes 5 seconds, but for some reason it's taking like 30-60 seconds ...

I tried that, sadly didn't work...

But I managed to find out something else:
I changed the line in /etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
```

and then ran 
```
sudo grub-update
```
you won't see the results right away because even after updating the grub configuration this is reloaded only on a new restart so the first time you shut down it will behave exactly as before.

This fixed the reboot and made the system reach the point where it prints "System halted" (or something similar) as the last line in the shutdown sequence.
This still means that you have to press the power button to completely turn off the pc but the system is definitely halted.
The reason this happens is because acpi is the power management and by turning it off the system can't turn the pc off.

This is not at all a final solution or even a fix, but I think it shows us where the problem lies, sadly I'm not sure how we could procede from here, I'm going to try booting on a live cd/usb and see if I can turn of from there (maybe something went wrong with the upgrade)

[B]UPDATE:
[/B]I tried from live cd and the problem is still the same, sadly I really need my laptop to be in working order (I also noticed that the Suspend behaviour is not working, probably still related to the same bug) so I'm reverting to 13.10 for the time being, hope a fix will come out soon ^^

---

### Post by Danger_Monkey on 2014-04-18
If you go to the command line and type the following, what do you get?

```


shutdown -h now


```

---

### Post by marco-prolog on 2014-04-19
I went back to 13.10 now so I can't do any more testing, but I tried that and the behavior was exactly the same as shutting down through the GUI

---

### Post by mmorris on 2014-04-22
Just installed ubuntu 14.04 server and 
```
sudo shutdown now
```
cased the system to shutdown, but not power down.

While
```
sudo shutdown -h now
```
cased the system to shutdown and power down.


from man shutdown:

"-h Requests that the system be either halted or powered off after it has been brought down, with the choice as to which left to the system."

---

### Post by Steve J on 2014-04-24
I have the same problem w/14.04.  I have an HP Pavilion DV9009us and the last two lines I see after I click on "shut down" are
> *Deactivating swap
mount: / is busy
*Will now halt


After that, I have to manually turn the laptop off.

Any help appreciated.

This worked:

> sudo shutdown -h now

---

### Post by WoodenWalker on 2014-04-25
"sudo halt now" should work

---

### Post by Steve J on 2014-04-25
Now, after I walk away for a few minutes, the screeb goes dark & I can't get it back w/o rebooting

> **Steve J said:**
> This worked:

Also,, when I next used the system menu to "shut down," that also worked.

---

### Post by drphysic on 2014-04-28
I have exactly the same experience that Steve J noted above, on an HP Compaq Presario V6105NR with the Broadcom WiFi card:
      *Deactivating swap
       mount: / is busy
      *Will now halt 
and all variations of halt & shutdown cause the same result. I had the identical experience with Lubuntu, which is why I tried running Xubuntu. This is on a clean install, reformatted HDD. Because the system does not shutdown properly, I also seem unable to install the correct driver for the BCM4311 WiFi card, so I am using a Netgear USB WiFi for now.

Lubuntu 13.10 did not have this problem on this machine. Any suggestions?

The solution for me for the " mount: / is busy", using a Compaq Presario V6105NR laptop, with a Broadcom BCM4311 WiFi card was the successful install of a working driver for the WiFi card, using the commands

sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree

which did not work without purging the bcmwl-kernel-source. System now properly does a shutdown.

DRB

---

### Post by svt_raiden on 2014-05-01
I have had the same problem, and I found the reason and the solution to it. 

Cairo Dock causes this. It has it's own mechanism (button) to shutdown and it seems to override the native Linux Shutdown button action. 

the solution is to remove the Cairo Dock. 

> 
sudo apt-get purge cairo-dock-*
sudo apt-get autoremove
sudo apt-get update
sudo reboot


When your computer reboots. Your Shutdown button should work.

---

### Post by Jaman42 on 2014-05-08
I have the same problem but haven't found a solution to it yet. For me it isn't Cairo Dock at least cause that's not installed. I can see some lines of text on the display when I try to shut down but they disappear to quick to read, is the shutdown procedure logged somewhere so I can find out more about this?

> sudo shutdown -r now

isn't working either

---

### Post by webbertiger on 2014-05-26
I found on my Dell e6400, change the following line in /etc/default/grub solve the issue.
GRUB_CMDLINE_LINUX_DEFAULT=""

It will print some messages when booting/shutting down, but it doesn't bother me.

---

### Post by brian_woods on 2014-05-27
yes, also worked for me thanks for help.

---

### Post by sameermw on 2014-05-28
I got the same problem and this solution worked for me. I installed acpi for display information on acpi devices.
```
sudo -i
gedit /etc/default/grub

```find the line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 

```and change it to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"

```save the file and close it.
now run
```
update-grub

```

now i think your problem solved.

And also if you are using cairo-dock please Removing Cairo-dock from the startup applications and try to shutdown from top panel.

---

### Post by RookY2K on 2014-06-01
Hello everyone. I found this thread when trying to figure out my issue. So instead of starting a new thread, I'll piggyback onto this one. I've already tried some of the suggested solutions here (acpi = force), but so far nothing has really worked. Basically, what is happening is the shutdown process seems to be working, but my laptop will not power down. It will get to the last step, display that it is powering down, but then just sit there. I have left it running like that for a while to see if maybe something would happen, but nothing. Strangely (or perhaps not strangely, I'm fairly new to Ubuntu), Ubuntu will restart just fine. It's only an issue when I shutdown. 

One additional piece of information that may be useful (or probably vital): I dual boot with Windows 8. Recently, I suffered a stop error when booting into Windows (0xc000000f) where I was informed that the acpi.sys file was missing or corrupt. I used my recovery USB and was able to correct this issue through the recovery's boot repair. My guess is this is what caused my issue. Before this, I was able to shut down fine with Ubuntu 14.04. I'm not really sure what caused my Window's boot issue, but since I "fixed" it, I can't power down properly from Ubuntu. This seems like too much of coincidence to ignore. I did remove "quiet splash" from the GRUB_CMDLINE_LINUX_DEFAULT variable and during shutdown, everything returned [OK]. It just hung at the power down step (the last step).  

Thank you for any help you are able to provide.

---

### Post by Kazuki512 on 2014-06-05
Hallo everyone!

I have the same problem since 2 years on one computer starting with (X)ubuntu 12.04, and now with 14.04 on 2 computers.
(X)ubuntu shuts down the computer, stops the HDDs, but does _**not**_ power off.
Today I played around with the power management settings at the BIOS setup, and maybe I found a solution.

Just for the records, I got 5 machines in my network:
#1: Intel DP965LT mainboard, Core2Duo 2.4GHz CPU, 6GB RAM
#2: Intel DG33BU mainboard, Pentium DualCore 2.0GHz, 6GB RAM
#3: Intel DG45ID mainboard, Pentium DualCore 2.5GHz, 8GB RAM
#4: Intel D865PERL mainboard, Pentium4 2.8GHz, 4GB RAM
#5: ASUS Eee PC 1005PE netbook

Machines #3, #4 and #5 are always power off fine, no problem at all.

But machines #1 and #2 did _**not**_ power off after shut down.

These two machines seem to share a nearly identical BIOS (AMI), and thus have the same bugs.
This problem seem to be ACPI (power management) related. So the relevant options should be in the section "Power" of the BIOS setup.
On both computers, the option "Wake on LAN from S5" was set to "Stay Off".

For this 2 machines, it turned out, setting "Wake on LAN from S5" to "Power On" seemed to solve the problem.
Of course, now this 2 machines can powered up via LAN, but the power off problem seem to be solved.

I rebootet both computers a few times and shut them down, to see, if it really worked.
So far, yes it did. But I'm not 100% sure, yet. In the past there were other solutions like "acpi=force" that seemed to work at first, but after a few days the problem was back. It was just luck it worked for a few shut downs...

So maybe someone can test this as well, and report here if it was a solution or not.
Also, please post infos about mainboard and BIOS, if you know. Maybe this can be of help, e.g. it only affects a certain type of mainboard or something like that.


Kazuki

---

### Post by maciej5 on 2014-06-12
Are u using Cairo-Dock? It seems like it is sometimes the cause, well in my case anyway since its on startup I think. But anyway I like Cairo so I just added LogOut applet and its working properly but off course its still not working from the upper panel. So in my case since its working fine from dock I dont care about the upper panel 8-)

---

### Post by Kazuki512 on 2014-06-12
Hallo!

No, I am not using Cairo-Dock. On all of my computers is now a fresh and clean install of Xubuntu 14.04, therefore Cairo-Dock is not even installed.

May I ask what kinf of computer do you use?
Is it a desktop or a notebook? If a desktop, what mainboard is it using?

Did you check your BIOS setup? Do you have the option "Wake on LAN" (WOL)?
How is it set? Does changing it, make a difference?
Please, could you check this?

On my two affected systems (Intel DG33BU + Intel DP965LT mainboards), I can reproduce the problem, if WOL is disabled they do _**not**_ power off after shutdown. If WOL is enabled, both of them power down fine, always.

One of my friends also has an computer build with an Intel DP965LT mainboard. He had the same problem. Now, with WOL enabled, the system always powers off fine.


Kazuki

---

### Post by Kazuki512 on 2014-06-12
Because I was curious, I installed Cairo-Dock on one of my affected machines, the one with Intel DP965LT mainboard.
By the way, nice application, imitating the dock of OS X.
(^_^)

But Cairo-Dock didn't changed anything.
If WOL is enabled in the BIOS setup, the machine powers off fine, always. No matter if I use shutdown button from Cairo-Dock or the shutdown option from the XFCE menu.
If WOL is disabled, the machine sometimes powers off, but mostly not. No matter how I shutdown the computer.

So I don't think Cairo-Dock has to do anything with that.

Of course, this is a BIOS bug of these two mainboards. Normaly, WOL should not affect powering off a system. But on this 2 boards, it does.
That's the reason, why it would be interesting what mainboards other people with this problem are using.
Maybe other mainboards share the same/an similar BIOS bug.


Kazuki

---

### Post by wolflint on 2014-06-12
So is this thread solved?

---

### Post by Kazuki512 on 2014-06-12
> **mwcerrano said:**
> So is this thread solved?

Hallo!

To mark this thread as "solved" would be the job of the starter of this thread, orange2k.

For me, this solved my problem.
But no one else answered so far, and told us if this solved the problem for her/him as well.

Because you are asking, I guess you have the same problem?
If so, how about you? Could you solve it by enabling "Wake on LAN" in your BIOS setup?
And if yes, please could you tell us about your hardware, e.g. what mainboard are you using?


Kazuki

---

### Post by marco-prolog on 2014-06-13
Hey guys,
I've tried reinstalling 14.10 to test the "Wake on Lan" hypothesis, sadly that doesn't seem to be the problem with my pc :(
I've done some more research and it turns out that it's a fairly known issue with no definite fix, apparently it comes and goes between kernel updates (appearing and disappearing on different hardware).
I've also tried a number of possible fixes (mostly concerning acpi) but with no luck...
I think the best approach is to stay on 13.10 for the moment, report the bug and hope a new kernel upgrade will fix the problem

---

### Post by Kazuki512 on 2014-06-13
> **marco-prolog said:**
> ... the "Wake on Lan" hypothesis, sadly that doesn't seem to be the problem with my pc :( ...

Hallo there!

I see...
Too bad, looks like this is only the solution for my 2 mainboards with their buggy BIOSes...

But even if it was not the solution for you, may I ask, what machine do you use?
Is it a notebook or a desktop? What model is it? If it is a desktop, do you know which mainboard does it use?


Kazuki

---

### Post by marco-prolog on 2014-06-14
I have the problem on my laptop, it's a Fujitsu siemens Amilo pro v3505 (specs here: [http://www.cnet.com/products/fujitsu-amilo-pro-v3505-15-4-core-2-duo-t5200-win-xp-pro-512-mb-ram-80-gb-hdd/specs/](http://www.cnet.com/products/fujitsu-amilo-pro-v3505-15-4-core-2-duo-t5200-win-xp-pro-512-mb-ram-80-gb-hdd/specs/))
From what I can tell the motherboard is an Intel 34002938 48.4P501.011

---

### Post by Kazuki512 on 2014-06-14
> **marco-prolog said:**
> I have the problem on my laptop, it's a Fujitsu siemens Amilo pro v3505 (specs here: [http://www.cnet.com/products/fujitsu-amilo-pro-v3505-15-4-core-2-duo-t5200-win-xp-pro-512-mb-ram-80-gb-hdd/specs/](http://www.cnet.com/products/fujitsu-amilo-pro-v3505-15-4-core-2-duo-t5200-win-xp-pro-512-mb-ram-80-gb-hdd/specs/))
From what I can tell the motherboard is an Intel 34002938 48.4P501.011

Thank you for the detailed infos about your system!
(^_^)/

Kazuki

@**marco-prolog**

A friend of me has a similar Fujitsu Siemens notebook with Core2 Duo CPU.
(Sorry, I don't know the exact model right now, but I can ask him if you like.)

He also encountered this "don't power off" problem. But before with Xubuntu 10.04, and now with Xubuntu 12.04. He didn't tried 14.04, yet.

Sometimes, but not always, the notebook doesn't power off after shut down.
When this is happening, he just wipes over the touchpad! Then the notebook powers off!!

Please, maybe can you try that as well?
To try this, you don't need to re-install 14.04, again. Just prepare an bootable USB stick or a DVD with the 14.04 iso imagae file. Boot this, shut it down, and see if the notebook powers off. If not, wipe over the touchpad with your fingers, and see if it powers off then.

Like my 2 mainboards, I think this is a BIOS bug as well. As far as I know, the touchpad is inernally connected as PS/2 mouse. Maybe a BIOS bug concerning power managment (ACPI) <-> PS/2 connection.
Does the BIOS setup have a option to power up the notebook via PS/2 mouse/keyboard???
If so, does changing this option make a difference??
(?_?)


Kazuki

The notebook of my friend is a Fujitsu Siemens Esprimo Mobile V5505 Modell MS 2216, 1.8GHz Core2 Duo CPU, 1GB RAM.

He said, when the notebook doesn't power off after shut down, he needs to wipe over the touchpad or press the space bar of the keyboard. Then it powers off.


Kazuki

---

### Post by Daylus on 2014-06-26
I have a Dell Latitude D630C and my Ubuntu 14.04 install is pretty much stock. I had turned WOL off in the BIOS when setting the machine up and turning it back on (for NIC only) worked for me. The system now no longer hangs at the "System Halted" message, and powers off automatically.

---

### Post by Kazuki512 on 2014-06-26
Hallo!

Thank you for your reply.
(^_^)

So looks like there are other systems too, sharing such an BIOS bug. Not only my 2 old Intel mainboards.
This information could be useful to other Dell Latitude users as well. It's likely that other Dell Latitude notebooks show the same behaviour.


Kazuki

---

### Post by Deanimator on 2014-06-27
I'm having the same problem (14.04 won't shut down/reboot) on a desktop with an ECS Nforce4-A939 MB. 

I had the same problem on a desktop with a Biostar T-Force 6100-A939, before it stopped recognizing the keyboard last week. I disconnected the drives on the ECS (working 12.04, no shutdown issues), pulled the drives from the Biostar, put them in the ECS and did a fresh install of 14.04. It's doing the no reboot/shutdown thing now. At least I can painlessly go back to 12.04 if necessary.

I'm going to try the wake on LAN trick this weekend.

---

### Post by ~zoey~ on 2014-06-29
I'm running ubuntu gnome 14.04 on an Intel DG33TL board with a 82P35 chipset, an Intel Core 2 Duo processor and a Samsung 120 Gb solid state HD.  I was also having shutdown problems and setting Wake on Lan to Power On solved the problem for me.

zoey

---

### Post by Deanimator on 2014-06-30
I tried the Wake on LAN (actually called "Wake on Ring" in the ECS BIOS).  Still won't reboot, but shuts down properly.

This is getting ridiculous.  What good is a server that can't be rebooted without sitting in front of it?

---

### Post by ~zoey~ on 2014-06-30
Hey there,

(this isn't Zoey; that's my Mom ;) I've got a couple of servers that are on a KVM switch and one of my linux boxes just acts weird as a result.  Do you have the keyboard/mouse directly connected to the server or is it on a KVM?  Not sure that it would make much of a difference, but I've seen some odd behavior that goes away soon as I put a keyboard/mouse directly on it.  

(Also have a USB drive on an HP box that will not boot correctly, even after taking USB completely out of the boot order....stupid server)

Still trying to figure out why Wake on LAN would make a difference, but what the heck.  It worked. 

Thanks!

Dee

---

### Post by Kazuki512 on 2014-07-03
Hallo!

@~zoey~
> ... on an Intel DG33TL board ...
I see, the Intel DG33TL board is very similar to my Intel DG33BU board, so I guess same bugs. Just like my Intel DP965LT board.
(^_-)
Glad I could be of any help!
(^_^)/

@Deanimator
> Still won't reboot, but shuts down properly.
So enabling "Wake on LAN" (WOL) also fixed the poweroff problem for you?
That's nice! (^_^)

About your reboot problem:
There are serval kernel parameters regarding the reboot behaviour.
"reboot=warm"
"reboot=cold"
"reboot=bios"
"reboot=smp"
"reboot=triple"
"reboot=kbd"
"reboot=acpi"
"reboot=efi"
"reboot=pci"
"reboot=force"
Have you already tried them all?


Kazuki

---

### Post by sammycj on 2014-07-06
Hi guys,

I don't know if this will help you, but it certainly worked for me. In my case it was the driver for my NVIDIA card. I used the proprietary one instead of the provided Nouveau. Switching back to Nouveau saved the day.

I found this solution here:
[http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer](http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer)


CJ

---

### Post by Kazuki512 on 2014-07-12
> **sammycj said:**
> Hi guys,

I don't know if this will help you, but it certainly worked for me. In my case it was the driver for my NVIDIA card. I used the proprietary one instead of the provided Nouveau. Switching back to Nouveau saved the day.

I found this solution here:
[http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer](http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer)


CJ

Hallo!

Sorry to say so, but as for me, this doesn't helped at all.
I also have Nvidia graphics cards in my 2 affected machines. I already had the "not power off" problem with the nouveau driver. Switching to the nvidia driver didn't made a difference...
(-_-)
But enabling Wake on LAN was the solution on this 2 mainboards. Now both machines always power off fine, with nouveau driver and with nvidia driver!
\(^o^)/


Kazuki

@Deanimator

Sorry, I know it's a bit off topic here, but I would like to know:
Could you fix your reboot problem with one of the kernel parameters?
(?_?)

Kazuki

---

### Post by iceborg2 on 2014-07-23
Hello.
I have the same 'shutdown' problem. I'm running Lubuntu 14.04 (32 bit) on a Acer 4002WLMi laptop ( with forcepae option in the boot loader).
Noticed that after the initial installation of the system was complete the system didn't reboot and just hanged silent for a few minutes... needed to power off the computer with the power on/off button.
Also noticed later that when selecting the 'reboot' option from the shutdown dialog the system rebooted normally but selecting 'shutdown' the system hanged in the final screen and didn't power off.
Until now I have just been searching for similar problems and have not tried any of the suggestions I have encountered but I am doing now a complete software update to see if the problem have already been addressed and solved.
After completion and testing will post the results here.

---

### Post by tja on 2014-08-09
hi @all,

came here as i had the same problem with a brand new **Acer E3-111** Subnotebook (Intel N2930, Intel Valleyview Chipset, might be they are called E3-11 elsewhere).

symptoms were:
would hang on poweroff/reboot/hibernate etc..., in textmode the last message would be always *Will now ...* and then freeze.

the notebook is sold without windows but default bootmode is EFI for windows 8.1.
after much trouble with EFI on other machines/motherboard i turned this off right in the beginning and installed xubuntu 14.04 in classic BIOS mode which resulted in the above behavior.
_this was a mistake_ as this BIOS seems buggy when not booted via EFI.

solution for this machine:
**reinstalled with EFI**.
poweroff, reboot, hibernate, suspend works now flawlessly.

maybe some other "modern" BIOS implementation is buggy as this one, YMMV.

wbr,tja...

---

### Post by marco-prolog on 2014-08-31
Hi guys!

I've finally found a solution to this really annoying problem: the problem lies with a kernel module that crashes, if you disable this the power management works as it should.
The module is wistron_btns, which crashes and is supposed to manage the WiFi kill switch and "special" buttons on the laptop.
I found the solution here: [http://ubuntuforums.org/showthread.php?t=2220591&page=2](http://ubuntuforums.org/showthread.php?t=2220591&page=2)

[B]To find out if you have the same issue:
Run this in a console:Code:
dmesg | grep -i oops
If you see something the kernel reported a module crash (the "Oops") and when you are reading this it might be the same module. For the experts: read dmesg and find the stack trace below the oops, it starts with "call_bios" which originated from "wistron_btns".

[B]The fix:
We need to make sure the module no longer loads on boot, add it to the blacklist:
Code:
sudo nano /etc/modprobe.d/blacklist.conf
Add a new line at the end that says:
Code:
blacklist wistron_btns
Save and reboot, now your laptop shuts down again.

[B]Alternative fix which needs reapplying every kernel update:
Find out which kernel you use:Code:
uname -r
Mine says 3.13.0-24-generic
Open up a terminal and go to the module folder of your kernel, make sure to use the correct version number in the path:
Code:
cd /lib/modules/3.13.0-24-generic/kernel/drivers/input/misc
Rename the module so it can not be loaded:
Code:
mv wistron_btns.ko wistron_btns.ko.old
Reboot, now your laptop shuts down again.

[/B][/B][/B]Hope this will work for all the other people that had the issue!

---

### Post by dominalien on 2014-09-01
This is an excellent find! After blacklisting wistron_btns, my Amilo Pro V3505 now shuts down/restarts/sleeps correctly. Thanks!

---

### Post by tigersands on 2014-09-02
One fix is to consider running another desktop- like XFCE or perhaps the UbuntuStudio. 

 :KSThe other fix which works great under Ubuntu Unity and lets you keep things as is: Add the main repo for LinuxMint 17- plus gives you some package options from LunixMint17- the compatible LinuxMint version of Ubuntu 14.04:

sudo sh -c 'echo "deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) qiana main" >> /etc/apt/sources.list.d/mint.list'

[COLOR=#333333][FONT=UbuntuRegular]Now run an update to retrieve information about what packages are available:[/FONT][/COLOR]  

sudo apt-get update

Next fix the missing repo key:

[LEFT][COLOR=#222222][FONT=Ubuntu Mono]sudo apt-get install linuxmint-keyring[/FONT][/COLOR]
[/LEFT]

Once down update the system one more time:

[LEFT][COLOR=#222222][FONT=Ubuntu Mono]sudo apt-get update

Then upgrade broadly- just assures you get the upgrade and fixes the Shutdown issue:

sudo apt-get dist-upgrade

You should now see "Shutdown" option in the Ubuntu Unity shutdown  options-looks like a turn off cog in the upper right most corner of the  screen on the bar- to right of time-date then click "Shutdown" at the bottom of the menu, which, you will see, when clicked, gives you a  choice of "Shutdown" or "Reboot".[/FONT][/COLOR]
[/LEFT]

[IMG]http://ubuntuforums.org/images/smilies/smiley-faces-80.gif[/IMG]Tiger

---

### Post by linuxrebel on 2014-09-02
Just to add fuel.  This also occurs within VMware and VirtualBox.  So I doubt this is an ACPI issue.  Within a VM running acpi=off is relatively safe.  Outside of that I wouldn't recommend it.

---

### Post by achimdetjen on 2014-09-19
Dear Tigersands, I have Linuxmint 17, 64bit,  laptop Akoya E1232Tand same problem, doesn't  work. Tried Ubuntu 14.04 live CD/USB, same problem. I also tried other kernels and no succes. Only one works, the Gparted live USB, no problem, reboot smoothly. So think this is the Ubuntu  14.04 bug. Please help!

---

### Post by abcuser on 2014-10-03
I had the following problem in Ubuntu 14.04:
- from GUI it shutdowns and powers-off without a problem.
- but if using "sudo halt" sometimes it halts but newer powers-off and sometimes it freezes at shutdown --> THE PROBLEM

According to the manual: man shutdown
-h switch: Halt or poweroff after shutdown. --> But! computer decides if only halt will be done and so manual power off should be pressed or power off will be done
-P Halt action is to turn off the power. --> So computer does not have any decision on halt vs. power off. It just powers off.

My solution is the following command:
```
sudo shutdown -P now
```

---

### Post by maiden_taiwan on 2014-10-10
If you're having this shutdown problem, here's what worked for me.

Before running the shutdown command, umount all external drives, including USB, SAMBA, NFS, etc.

    ```
$ sudo umount /mnt/whatever
$ sudo umount /mnt/other/drive
$ etc....
```

Now try shutting down. Please post if this works for you.

I suspect the cause is only the networked drives, but I haven't spent the time to narrow it down.

---

### Post by MikSam on 2014-10-12
Hello.

I had this problem too, the shutdown and restart hanged on the Ubuntu logo until the world ends. Didn't have time to wait that long so I long-pressed the power button.
My system had apparently a problem with my wireless card. Mine is broadcom chip, b43* family, which uses non-free drivers and doesn't get autorecognized by Ubuntu. So, in order to get the wireless working AND the system shutdown (power halt) correctly the system needs the correct drivers. So, what I did was:
(Just to make sure everything is removed if there was old driver installed)
```
sudo apt-get remove b43-fwcutter firmware-b43-installer
```
Purge:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source b43-fwcutter firmware-b43-installer
```
And then install the driver:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Then I rebooted and it actually did reboot!
I had two birds with one stone.
I'm not sure if this is posted already somewhere but search for b43 didn't report anything on this thread. This might work with other devices too which have none or incorrect drivers.

---

### Post by AMP444 on 2014-10-21
Hi all
In my case is not an issue with wireless card or grub settings but drivers from Nvidia(not  tested on ATI), had 331.38 switched to 173.14.39 working like a charm. 
it has something to do with VGA which is related to ACPI of PC.
There is a Additional Drivers tool where you can choose desired driver.
I'm using 
Ubuntu Gnome 14.04 LTS 
Nvidia 8800 GTS AlphaDogEdition
Gigabyte GA-99XA-UD3
CPU: Phenom X4 955 Overclocked to 3.7GHz
10GB DDR3 1333 MHz
Mushkin SSD 128GB
and other HDD 5 more
Never had issues with Nvidia until I've install newest available driver for it 331.xx removing it to an earlier version helped me to solve it.

---

### Post by aleksilver on 2014-11-28
I have learned if you have two users logged in, it can cause problems.  If you forget to log everyone out, and you select shut-down, it might hang. 

At that point you can just hit Ctrl-Alt-F7 for first user logged in, and shut the first user down down, Ctrl-Alt-F8 for second user, etc...

Once all users are logged out, the system will shut down fine.

---

### Post by christophe-naud on 2015-01-17
I had the same problem last week after some Ubuntu 14.04 updates (HP EliteBook 820 laptop).

I tried the various things proposed around grub or bios which didn't work.

I finally open a terminal this morning : **sudo apt-get install laptop-mode-tools**

Reboot the computer, turn off.

No more problem.

---

### Post by marseille2 on 2015-02-02
After some recent updates to 14.04 (xfce ubuntustudio), I can't shut down either... and I used shutdown -h now (had this problem on 12.04 too). Didn't work. I have to hit the main power switch. Not sure what to do, and the thread doesn't seem to have a specific answer. Any suggestions?

---

### Post by abcuser on 2015-02-02
@marseille2, as I have explained in this thread above there is a difference between "halt" and "power off".


**Halt** means shutdown operating system, but LEAVE power on! In this case you have to manually press power button on your computer to power it off.
This is the command:
```
sudo shutdown -h now
```
or
```
sudo halt
```



**Power off** means shutdown operating system and ALSO power off computer. In this case you don't need to manually press power-off button on your computer to power it off.
So you should be using:
```
sudo shutdown -P now
```
or
```
sudo poweroff
```

---

### Post by marseille2 on 2015-02-02
Ok thank-you very much:D I will test it!

Here's what happened:

```
sudo shutdown -P now
``` did turn off the operating system, but the main power stayed on. The main light switch that normally goes off was still on, a bluetooth dongle was still lit up, and the fan wouldn't stop.


```
sudo poweroff
``` only rebooted my computer back into Trusty.

UPDATE: Temporarily Solved (for my system)

Well things temporarily went from bad to worse, after I continued to figure out why I couldn't get a complete shutdown. So I went to the IRC ubuntu channel, and they told me it sounded like an ACPI thing, so I set  'acpi=force' in /etc/grub/default. Didn't work either (note: I didn't remove cairo dock, since I like it). 

After reading through launchpad bugs, it started to look like there was no end to the drama. And I couldn't upgrade the Upstart package, since it's up to date ... so I tried the next suggestion. I wish I never listened! But no... and I upgraded my low-latency kernel. 

BAD BAD BAD....

My screen went black. But luckily, I still had my old kernels (hidden by grub ... hit the SHIFT key when the computer at bios boot / right after to see them). 

Long story short... **I rolled back to the last working kernel**, and found out I can now do a full shut-down. It also solved another problem that I thought was unrelated ... my mouse was going haywire and being overly sensitive. 

I'm so glad that's over... at least for now:D

My working kernel: 

**Linux 3.13.0-44-lowlatency**

Update 2:

I spoke too soon:( While rolling back to a working kernel solved the mouse problem, I'm back to the permanent reboot. Except unmounting my drives, I've tried the commands, tweaking the boot, etc... to no avail. I still have to hit the main power switch to turn off the computer.

---

### Post by ctech-nick on 2015-02-06
> **marco-prolog said:**
> I tried that, sadly didn't work...

But I managed to find out something else:
I changed the line in /etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
```

and then ran 
```
sudo grub-update
```
you won't see the results right away because even after updating the grub configuration this is reloaded only on a new restart so the first time you shut down it will behave exactly as before.

This fixed the reboot and made the system reach the point where it prints "System halted" (or something similar) as the last line in the shutdown sequence.
This still means that you have to press the power button to completely turn off the pc but the system is definitely halted.
[COLOR=#ff0000]**The reason this happens is because acpi is the power management and by turning it off the system can't turn the pc off.**[/COLOR]

This is not at all a final solution or even a fix, but I think it shows us where the problem lies, sadly I'm not sure how we could procede from here, I'm going to try booting on a live cd/usb and see if I can turn of from there (maybe something went wrong with the upgrade)

[B]UPDATE:
[/B]I tried from live cd and the problem is still the same, sadly I really need my laptop to be in working order (I also noticed that the Suspend behaviour is not working, probably still related to the same bug) so I'm reverting to 13.10 for the time being, hope a fix will come out soon ^^


I took your advice but went to grub boot command line and I did erase ACPI = off since I now have the right driver for Nvidia...

It shut down perfectly on it's own, brithness key are assign and work, but nothing change on screen yet...

On Mackbookpro5.1 Ubuntu 14.04

---

### Post by HSken on 2015-02-07
> **drphysic said:**
> The solution for me for the " mount: / is busy", using a Compaq Presario V6105NR laptop, with a Broadcom BCM4311 WiFi card was the successful install of a working driver for the WiFi card, using the commands

sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree

which did not work without purging the bcmwl-kernel-source. System now properly does a shutdown.

DRB

This solved my problem and finally got the wifi working, thanks:p

---

### Post by glenn12 on 2015-02-10
Cheers this worked for me after trying just about everything else! I am also using a Fujitsu Siemens:biggrin:

---

### Post by Taganini on 2015-02-17
That fixed both of my problems: No Shutdown and BCM4311 Wifi card not working! I have an old Compaq Presario C502US. Thanks

---

### Post by thorogood33 on 2015-03-11
I had this problem and tried most of the solutions above - I have a Compaq Presario with Pentium 4 and Nvidia Fx 5200 video - no wi-fi card. 
PC would reboot ok but only shutdown fully using the off switch. I know it's not critical but I found it niggled.
I thought it was possibly a bios/motherboard/video card issue and spent ages on forums - eventually tried some other distros - Watt OS, Xubuntu, Mint, Debian, LXLE, Bodhi, Crunchbang - all same issue and all Debian based. 
Am now running PClinuxOS LXDE which has solved the problem.
PC closes down fine and PClinuxOS has proved a nice smooth OS on a low powered system - (although the legacy Nvidia 173 is no longer supported it runs fine with the xorg nv driver). 
Puppy Linux (Slax) also shut down ok. I happen to prefer PCLinuxOS over Puppy so will stick with it.
I don't know if it is relevant but Puppy (Slax) and PCLinuxOS are not based on Debian and do not use systemd.
Hope this helps someone with similar issue.

---

### Post by g-me-5 on 2015-03-30
I have tried this and did not fix my problems on 14.10 Acer aspire 5560. Wireless is not working.

---

### Post by skeeter-mcbee-y on 2015-04-09
> ```
sudo grub-update
```

This is not a command. Instead it should be ```
sudo update-grub
```

---

