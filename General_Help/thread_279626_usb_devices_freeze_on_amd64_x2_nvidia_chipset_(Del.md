---
title: "usb devices freeze on amd64 x2 nvidia chipset (Dell Dimension E521)"
date: 2006-10-18
forum: General Help
---

### Post by mclazarus on 2006-10-18
Hi,

Anyone else try running Linux (in my case Ubuntu 6.06) on the Dell Dimension E521 with the AMD 64 X2 processor? I am having a problem when using xorg where my USB devices, more often my mouse, but my keyboard has had the problem as well stops working. It is almost like the interrupts start getting masked, but it isn't that. Because when the mouse stops working I am usually able to still use the keyboard.

It happens after a while, and usually in times of heavy use. I guess really instead of heavy I would say normal. But it has never happened that it will be working and then I let it lay idle for a while and then reach for it again and it be frozen.

This started happening under the amd64 version of Ubuntu but I have tried several different versions by now and the problem continues to happen.

As far as troubleshooting it has been a real pain. There is never a message in the kernel log or shown by running dmesg. Actually once or twice I have seen the irq status -71 received, but I am pretty sure that is not the cause, becuase it has only happened about twice out of maybe 40 occurances. And there is no message in the Xorg log either.

I have tried the default amd64-generic kernel the latest amd64-generic, the latest amd64-k8 kernel (I think 2.6.15-27.48) I have tried running the i386 uniprocessor kernel and the latest k7-smp kernel. All of them have the same problem.

In an effort to get to the bottom of it I have re-compiled the kernel according to the directions here: [http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper) and turned on debugfs and collected data, but there doesn't seem to be anything of interest. It seems I get hundreds of thousands of lines of -115 status (Which I believe is the controller just telling the device that yeah, I hear ya and I am going to do something EINPROGRESS) and then nothing. The mouse appears to continue to function at least the circuit which senses movement and turns the LED into bright mode. And under Windows I have had no problems at all.

The only solution that always works is to disconnect the USB cable and then reconnect it, which grabs a new device file /dev/input/event7 and probably does some other magic registers with the USB controller, and a bunch of other stuff and then the mouse starts working again.

The only other consistent problem I have noted is the IOAPIC stuff complains about a bug, and sometimes it won't boot and panics, other times it figures out a way to get by and does so. Because of this I have tried booting with noapic and other than changing the way /proc/interrupts looks there seems to be no change in the problem. Eventually under usage the mouse stops responding entirely. Even looking at cat /dev/input/mice there is nothing getting there.

I have upgraded the BIOS to 1.0.3 that had no effect. And also turned off the Cool and Quiet support in the bios.  I have also tried running with and without the nvidia restricted module in the kernel.  And none of these things seems to have any effect.

Any thoughts, recommendations of how to proceed, or any other suggestions are appreciated.

Thank you,
Kevin

---

### Post by chris.olsen on 2006-10-19
I have the exact same problem, also with a dell E521 computer (amd64).  If you figure this out please post what yo did.

Thanks

---

### Post by metalheart on 2006-10-19
Are you using back or front USB ports for connecting? Try switching to front/back.

---

### Post by mclazarus on 2006-10-19
I have tried both the front and back.  I have even put in a usb mouse in the front and the back, although they appear to be the same bus.  when it froze moved to using the one that was plugged into the back and that worked for a while and finally locked up as well.

---

### Post by chris.olsen on 2006-10-20
bump

---

### Post by mclazarus on 2006-10-20
My ongoing struggle:

The problem continues to happen ](*,) 

Just this morning, running the k7-smp kernel just because I thought trying with out 64 bit mode may eliminate some of the variables, (ya know since the windows I got with it doesn't take advantage of those bits anyway)

I booted with noapic nolapic routeirq=pci

It came up fine and all was well, but the mouse locked up after time and I still saw no interesting error messages anywhere.

The other thing I tried was increasing the logging level in the Xserver to see if maybe something strange was going on there, although I do think the problem is deeper (the interaction between the motherboard and the kernel) I thought it was worth a shot.

My current research into the problem is looking for issues with the nforce430 chipset in the kernel specifically.  I have posted to Dell's message boards but haven't had much luck.  

Most of my research has shown that the problem is bios related, but a lot of the things I am googling turn up info that is relatively old.

I probably am going to wait until the 26th (assuming it is still on time), install the Edgy release and renew my troubleshooting, as far as compiling kernels with debugfs on and all that jazz.

It'd be nice to get this to a point when I know where to submit the bug report. At this time my vague notion is that it is a kernel issue, but I can't pinpoint it so I it is hard to find the right people to ask for help.

---

### Post by NRios on 2006-10-21
Same with me. The computer is a new Dell Dimension E521 with an AMD64 X2 and an nForce chipset. I'm using a very nice Logitech wireless set of keyboard and mouse which worked just fine in Dapper with my recently deceased previous computer. Keyboard and mouse share a single USB wireless controller which may also be plugged in the two PS/2 type connectors (the latter not being possible in the new Dell, which has no PS/2, no serial, and no parallel ports)

I tried installing Edgy Beta in the new computer using the live disk, but the keyboard pointer was frozen the very moment X started. I retried a couple times, no change. So I wouldn't set my hopes on Edgy.

With Dapper, it's a little different. It boots up with a functional pointer and, after a while, it freezes. The keyboard keeps working, and may be used to restart X, but GDM reappears with the mouse still frozen (and the keyboard still working). No problems are logged anywhere. If I reboot, the pointer works again, for a while. I'd venture is a kernel problem, not an Xorg proble, because rebooting the PC fixes it, but restarting X does not.

So we're finding this problem in Dapper and Edgy, in SMP an uniprocessor kernels, 32-bit and 64-bit. Not looking very bright!

Anybody reading this has a Dell Dimension E521 that works OK with Ubuntu? What about other Linux distos? I'm going to post a message mentioning the Dell Dimension E521 to see if anybody has it working right.

---

### Post by jorden on 2006-10-21
I have -exactly- the same problem on my brand new Dell Dimension E521 AMD64-X2 4200+ 1Gig and Dell optical mouse and Dell keyboard.
I'm struggling with it for a week, and I'm no newbie.
I try to keep positive but I've seen a lot of trouble in the past with
nForce and Linux but none of them were as hopeless as this one.

I'm almost sure that the problem is nForce4 + kernel >= 2.6.15 related.
Older kernels could be a good try-out because they use a complete
different USB principle, but the problem is that strangely older kernels should support nForce4, but udevd doesn't recognize SATA and kernel panics
for that reason.

I've transplanted C-code from different kernel versions in the past, to
solve obscure hardware problems, but this time it is'nt simple or even
as good as impossible, due to very very different kernel setup between
< 2.6.15 and >= 2.6.15. I've tried and failed this time.

I'm using SuSE linux 10.1 boxed version, and their own 2.6.16.4-smp
kernel works almost perfectly, but WITH the irq-lossage error.
Other mainstream-kernels (newer and older) make things worse, ACPI doesn't 
work at all with them + my Dell.
From 2.6.14 and lower there could be a good chance of working OHCI,
but as said, SATA controller is not detected correctly and kernel
sort of panics (sda-x is found, mount / read-only, udevd should detect
sata and populate /dev/sda-x's but that last step fails and a subsequential rw mount from / and friends fails and kernels ends in
e2fsck root login. Kernel seems to detect nForce4 sata only 'half')

Symptoms are:
Very often mouse stops working, replug and mouse works again.
In syslog (when kernel is compiled with usb-debug option) an
ordinairy disconnect seems to appear at the moment of mouse-lock
but the difference with a real disconnect (pull out plug) is that
after 4 seconds after 'disconnect'  an ohci-hcd irq intr_sf lossage appears.
Sometimes even the keyboard gets lost.
And... it's not only in X. Forget X logging and debugging.
Try to load gpm -m /dev/psaux -t imps2 in a TTY move around for
a while and with 'luck' you'll see the mouse freeze also.

In every kernel I tried I've tried the famous combinations of
acpi=off pci=noacpi noapic nolapic pci=routeirq nosmp, and others.
None of them worked as a solution for this ohci problem.

I hope I can fix this someday, but to be honest, I've re-learned my lesson with nVidia, sadly enough. I used to love nVidia + AMD, but since
nForce2 I thought I was cured, but with nForce4 I'm sure.
nVidia + AMD is water+fire nowadays and linux support is very very bad, compared to 3 years ago.
ATI also is a no-no (no linux chipset support at-all?), so I'm back
at Intel. Intel runs on x86-64 SMP for more than a year perfectly,
fast and smooth, whatever brand of system.

I give myself a week or so to fix this annoying Dell E521 problem,
after that I sell this crappy 64 system, sorry.

Good luck guys :-k

---

### Post by mclazarus on 2006-10-22
Yeah seems to be many people thought they were getting a bargain here.  But it is a kernel/chipset/Bios issue.

There are folks on the Dell boards with the same issues using different distros

[http://forums.us.dell.com/supportforums/board/message?board.id=sw_other&message.id=54369#M54369](http://forums.us.dell.com/supportforums/board/message?board.id=sw_other&message.id=54369#M54369)

You may be right the quickest solution may be to sell the computer and get an Intel.

Which debug option did you turn on to see the disconnect?  That may get things going in the right direction to actually fix it or work around buggy bios in the kernel.

---

### Post by jmaier on 2006-10-23
Hi, 

I tried with OpenSuse 10.1, Ubuntu 6.06 and Ubuntu 6.10 beta without any luck. 

In the end I tried knoppix V5.0.1-2006-06-01 which is derived from debian sid. It has kernel 2.6.17-rc and it works properly. 

So it might be helpful to look at the differences between these distros concerning the USB handling. Unfortuately I am no Linux guru and my knowledge in the kernel area is limited.

--
Jürgen

---

### Post by NRios on 2006-10-23
> In the end I tried knoppix V5.0.1-2006-06-01 which is derived 
> from debian sid. It has kernel 2.6.17-rc and it works properly.

That's interesting ... I have tried Debian Etch and it doesn't work either. If sid is working, maybe a fix is coming. I hope Ubuntu includes in its own version of 2.6.17 whatever is that makes Knoppix tick. Anybody there is listening?

---

### Post by mclazarus on 2006-10-23
Thanks, jmaier.  It working well under Knoppix is worth investigating.

---

### Post by czz7661 on 2006-10-23
This is also a problem with the C521 - It does not work in gentoo as well.  Our kernel version is 2.6.17 and the updated kernel doesn't seem to fix the issue.  I wonder if dell is going to release a new bios for these damn things anytime soon?

---

### Post by NRios on 2006-10-23
I have reported the problem in the Malone bug tracker, because it had not been reported yet. We'll see if someone listens to our pleas.

---

### Post by jorden on 2006-10-23
> **mclazarus said:**
> 
Which debug option did you turn on to see the disconnect?  That may get things going in the right direction to actually fix it or work around buggy bios in the kernel.

Hi mclazarus, the option is:
CONFIG_USB_DEBUG=y
in the kernel-sources config file.
In the syslog file, messages will appear when connecting and
disconnecting an usb device, or when our very-nice mouse-losses
occur.

I also read the thread on the Dell forum you pointed to.
The story about Knoppix 5 interested me.
I'm not going to use knoppix, but I've tried the newest Debian kernel
today (2.6.18 patched till extra-version .2), with no luck.

But jmaier mentioned knoppix 5 uses 2.6.17-rc so I'll give it
a try when I've time this week (perhaps today), and if I can
download the sources from exact this kernel and distro.

It still is a weird problem in these E521's but I already have
found buyers for my own E521 :-#

---

### Post by mclazarus on 2006-10-24
Jorden said:
> But jmaier mentioned knoppix 5 uses 2.6.17-rc so I'll give it
a try when I've time this week (perhaps today), and if I can
download the sources from exact this kernel and distro.

I didn't get a chance to try it today, let us know if you get a chance to look at the 2.6.17-rc.

---

### Post by Hephaistos2 on 2006-10-24
I have Slamd-64 (Slackware for x86-64) on Dell E521
I have tried kernel 2.6.19-rc3 and it seems to work correctly in x11 (two hours without freezing now)
But I had to modify the sources of Nvidia driver (NVIDIA-Linux-x86_64-1.0-8776-pkg2.run) , otherwise it would not compile : the second argument of the  function request_irq in kernel 2.6.19-rc3 has changed
There is another problem : I could not make a working kernel in SMP

---

### Post by jorden on 2006-10-24
Yesterday evening I downloaded Knoppix 5 to see what it does.
It looked stable indeed, but it's 32 bit.
I downloaded a 2.6.17(.3) kernel and tried to use the Knoppix
kernel .config 1-to-1 and it failed (of course) because
of x386 settings while compiling forces it to x86_64.

I can experiment with 32bit but I don't. Even if it works
I don't want to run it 32 bit.

Like Hephaistos2 I'll try 2.6.19-rc3, because untill now
I haven't ;) 

Maybe the ACPI (64 bit) trouble with these systems caused
the failure of SMP.
I kind of solve these things bij passing acpi=noirq to the 
kernel.
All 2.6 64 kernels do lockup in my system, until
I disable acpi-irq-redirects.
The resulting system is 64bit SMP+ACPI but with limited irq's
and 'only' the mouse-freezes.

I'll let you know if 2.6.19-rc3 works for me.

B.t.w. I use an ATI 1300pro vga card, let's see what that
kernel module says when compiling against 2.6.19-rc3.

---

### Post by jorden on 2006-10-24
Back again...
Compiled 2.6.19rc3 x86_64 from source.

Kernel worked great, SMP, ACPI everything (including ACPI irq routing)
but mouse freeze still was there...](*,) 
It even got a little worse, because when I pull out the plug en
re-insert, the hal-daemon does not get triggered and mouse never
returns.

Tuned around with kernel params nothing worked, still usb losses.

I found a disturbing message in the kernel-boot-log, and when I
checked afterwards it appears in the log produced with -all- kernels
I've used.
It looks like pci-e has irq bugs in the bios. Perhaps it conflicts
with usb and when screen changes occur while using usb at some point
they get a 'collision' or something(?) and thereby loosing the usb
interface.
Strange fact is that it works good in WinXP-32 and Knoppix-32.
Is this bios bug only 64bit related??? Very strange.
These are the lines in the boot.msg :

<7>PCI: Setting latency timer of device 0000:00:02.0 to 64
<4>pcie_portdrv_probe->Dev[02fc:10de] has invalid IRQ. Check vendor BIOS
<4>assign_interrupt_mode Found MSI capability
<7>Allocate Port Service[0000:00:02.0:pcie00]
<7>PCI: Setting latency timer of device 0000:00:03.0 to 64
<4>pcie_portdrv_probe->Dev[02fd:10de] has invalid IRQ. Check vendor BIOS
<4>assign_interrupt_mode Found MSI capability
<7>Allocate Port Service[0000:00:03.0:pcie00]
<7>PCI: Setting latency timer of device 0000:00:04.0 to 64
<4>pcie_portdrv_probe->Dev[02fb:10de] has invalid IRQ. Check vendor BIOS
<4>assign_interrupt_mode Found MSI capability
<7>Allocate Port Service[0000:00:04.0:pcie00]

Then I hoped to trick this bug by using pci-irq redirects via PCI-bus-packets (kernel option) and by making sure MSI is activated
in the kernel (pci-e arch needs MSI, and always uses irq-packets
instead of hard-wired irq lines.)
It didn't work again...........................](*,) ](*,) 

Any suggestions guys? :-k 

Grtzz
J.

---

### Post by Hephaistos2 on 2006-10-25
I was wrong. X still freezes using kernel 2.6.19rc3, but it can take hours. Maybe in rc4 it will take days.
When it freezes it is still possible to log in from another machine, but I could not kill X from there. Unplugging and re-plugging the mouse produced the message :
usb 2-3: USB disconnect, address 2
ohci_hcd 0000:00:0b.0: IRQ INTR_SF lossage
ohci_hcd 0000:00:0b.0: leak ed ffff81003fdda0f0 (#81) state 0 (has tds)

---

### Post by chris.olsen on 2006-10-25
so what is the verdict?  Is this something that will be considered of importance for the people working on the kernel to allow a fix to be see sometime soon?

I am still new to the linux world so forgive me if this is a dumb question.  The reason that I ask is that both my mom and dad each got the dell model that is causing problems.  I figured I would clean out all the cr@p for them and install ubuntu, but obviously this is not working out as expected.  I am just wondering if I should just install ...ackk...cough..windows and send them on their way or if this is something that will work itself out in the next while.

BTW I tried ubuntu 5.10 and it would not boot up from the cd to allow me to install.

Thanks for the input

---

### Post by NRios on 2006-10-26
As for failing to boot 5.10, it might have to do with the DVD drive being a SATA unit. It gave me a bit of trouble when trying to install Debian Etch, but I googled that it could be circumvented by running the installer with the following line, instead of just hitting enter at the command line:

    install libata.atapi_enabled=1

Don't know it that'll work with Breezy, or it Breezy won't have the mouse freeze problem (Etch did have it). If 5.10 runs OK, please report it here.

This afternoon I'll try with Fedora Core 6. I'll report my findings here.

---

### Post by Qujo on 2006-10-26
I have tried this on Fedora Core 6, both 32 bit and 64 bit versions.  both occasionally lose the mouse.

To install the 64bit version, I had to turn off acpi.  The 32 bit install ran without any modifications.

---

### Post by sadams6696 on 2006-10-26
OK All, here is a $11 workaround...

Get yourselves a low profile PCI USB board and install it in the PCI slot.
Then get into your BIOS setup and disable all the on-board USB ports.
Plug your keyboard and mouse into the PCI USB board.

This solution is working on our five C521's. No hangs so far and it's
been hours...

---

### Post by Hephaistos2 on 2006-10-27
> **sadams6696 said:**
> OK All, here is a $11 workaround...

Get yourselves a low profile PCI USB board and install it in the PCI slot.
Then get into your BIOS setup and disable all the on-board USB ports.
Plug your keyboard and mouse into the PCI USB board.

This solution is working on our five C521's. No hangs so far and it's
been hours...


I am very afraid of doing that, because if something goes wrong I have no way of returning in the bios setup. Of course if you have 5 you can make experiments...

---

### Post by NRios on 2006-10-27
> **sadams6696 said:**
> OK All, here is a $11 workaround...

Get yourselves a low profile PCI USB board and install it in the PCI slot.
Then get into your BIOS setup and disable all the on-board USB ports.
Plug your keyboard and mouse into the PCI USB board.

This solution is working on our five C521's. No hangs so far and it's
been hours...

I was thinking of that solution, and was almost sure it would work, but its *wrongness* makes me queasy. 

In any case, it might not be necessary to disable the on-board USB ports, which might work OK with printers and flash bars and would still offer frontal access to the multicard reader and USB ports. After all, the keyboard does not stop working when the mouse freezes, or does it? Can anybody tell us if there are similar problems with printers, scanners, webcams and other USB peripherals?

---

### Post by chris.olsen on 2006-10-27
is it just me, but the pci slots (long and short sections) in my computer are facing the "other way" which don't allow me to plug a normal usb card in and have the ports facing out the back.

---

### Post by jorden on 2006-10-28
Hi guys, back again...

I am busy selling the E521, I was tired of it.

The USB pci32 card is an option I already thought of two
weeks ago, but it's stupid and I also wanted to use the
2 pci slots for parallel port card AND an soundcard, which is
also stupid but the onboard sound is also very bad supported
but not buggy and perhaps ALSA will come with a driver in 
the future, while the usb bios(?)-bug-fix is very unsure.

To be short: In my specific situation is placing an usb card not acceptable, and violates the goal I had in mind with this
system.

Although I decided to sell this system I did contact Dell by
mail and phone, and of course they blamed linux, but I did not take that and told them to take this serious because a lot of linux-users world-wide have problems with a system that is
presented as linux-perfect (see Dell.com) but what really is
a lie.
And what if Windows-64 is going to give trouble?

I think this AMD64 system is a bad start for Dell with AMD.
They better prove to take their own products serious.

Profesionally I use a lot of Intel-based Dell systems and they
are very good, but this debut AMD64 system is crap for linux, 
sorry.

I also contacted nVidia (nForce4 bug?) and Novell (perhaps they
can help writing a kernel patch. I'm a SuSE user you know.)

nVidia didn't give home, while Novell -did- react, but until
now nothing has happened, no further reactions from their side.

So my brand-new Dimension is almost sold to a WindXP32 user.

I wish you good luck guys, and placing an usb card is a workaround for others indeed.

Signing off... Jorden.

---

### Post by Pinoy915 on 2006-10-28
This also happens with my Acer Aspire E360. It's an AMD X2 with Nvidia chipset also. I just go to the back and unplug/plug my mouse to get it working. I hate doing that but I don't want to buy the pci board.

---

### Post by daxLeet on 2006-10-28
Yes, this is an issue with me as well.  Dell Dimension E521 :[

---

### Post by vinco on 2006-10-30
Has anyone tried using a USB hub?

I just plugged the mouse into the keyboard hub and now it works fine (Knoppix 5.0.1). I'll test Ubuntu 6.10 later.

---

### Post by NRios on 2006-10-30
This morning I tried to plug the keyboard and mouse into a cheap external USB hub, and the 6.10 live CD started up OK, with a functional mouse and keyboard, whereas it would come up already frozen solid without the hub. Had to leave for work, so I couldn't test it  for more than a minute, but I'll look at it harder this evening.

---

### Post by NRios on 2006-10-31
Dapper worked for me OK with the keyboard and mouse plugged into a hub. I cannot say that it won't freeze after more use, but it really seemed to work OK. Then I upgraded to Edgy and it worked too. I had problems with the nVidia drivers so I reinstalled from CD and that also worked fine, and it went fine while I selected and downloaded with Synaptic all the extra programs I wanted.

However, it's been a PITA, because the hub's initialization by the BIOS has been EXTREMELY unreliable, and 9 times out of ten the keyboard is non-functional at the moment I may hit F12 to choose boot media and also in the grub menu. It may be a problem with my hub, because I've read in the Dell forums that it works OK with the built-in hub of the Ultrasharp screen (which I don't have).

With only occasional access to the boot menu, I can only consent to boot from the first entry in grub, which boots Linux and then it seems to work all right. To boot windows, however, I have to ged rid of the hub first.

---

### Post by pregoeater on 2006-11-02
i just got my e521n yesterday....the one without a  OS installed. i had the same problem where the mouse would just stop and i had to unplug it and plug it back in. so i tried the front and back same issue. then i used the hub on the monitor and no more freezing. i have not tried it on any other usb stuff just the mouse so i hope it doesnt have issues with my usb HD.

---

### Post by mclazarus on 2006-11-02
I have had no problems using a USB storage devices.  I have been using the system with a USB PCI card for the keyboard and mouse for a few days.  Running Edgy now (the 64 bit version).  With no problems.

I plan on trying with a USB hub I have sitting around, and when I have time I can then try to actually troubleshoot the problem or contribute to the bugs others have no doubt reported by this time.

---

### Post by pregoeater on 2006-11-02
right now im using the 32 bit version. i was told to use the 32 bit on my 64 bit system because it would work better i might upgrade. what is the advantage to useing the 64 bit? 



Pre

---

### Post by mclazarus on 2006-11-02
As far as I can tell, when running the 64 bit version you get to use all of the hardware you paid for.  Which I guess means I can address more memory than before and you can process floating point numbers to better precision/more efficiently which can effect things such as video/audio editing as long as the software is compiled to take advantage of the extra available resources.

However, as punishment for this you also get to have a hard time and need to do strange workarounds for some common desktop things, like trying to install the adobe flash plugin, or run some games.  To get those things working you typically have to create a chroot 32 bit environment to run them in.

---

### Post by mclazarus on 2006-11-02
> **mclazarus said:**
> To get those things working you typically have to create a chroot 32 bit environment to run them in.

BTW hunting around on here, or in the How TO forums there are some relatively easy ways to get these chroot environments up and running.  Depends on your patience for such things.

---

### Post by pregoeater on 2006-11-02
right now im happy using the 32bit on my 64 works for now....i will wait for better 64 bit distro before i change. OH and its been 24 hours using my usb hub on my monitor and no mouse lock up.....i called dell and one the the techs told me it was a linux problem. he did seem to know what he was talking about. he told me that it has to do with the way linux handles power when the processor uses more power linux does not always supply enough to the usb and it stops the usb ports it and when it puts power back to the usb most devices do not have a problem with it but for some reason mice do. he said the best way to fix that is use a POWERED usb hub that you plug into the wall for power. that way it has enough power at all times. i have not tried this because mine works but atleast dell knows about it.

---

### Post by NRios on 2006-11-06
> **pregoeater said:**
> i called dell and one the the techs told me it was a linux problem. he did seem to know what he was talking about. he told me that it has to do with the way linux handles power when the processor uses more power linux does not always supply enough to the usb and it stops the usb ports it and when it puts power back to the usb most devices do not have a problem with it but for some reason mice do. he said the best way to fix that is use a POWERED usb hub that you plug into the wall for power. that way it has enough power at all times. i have not tried this because mine works but atleast dell knows about it.

Dell treats us as idiots: a pat in our back, a blame on another party, and we're sent back home. But that ridiculous argument does not stand to the slightest consideration.

The mouse may freeze even with no apps running; it may freeze with nothing but a keyboard and a mouse plugged in the USB -- it can even happen with just ONE receiver for a wireless keyboard/mouse combo plugged in.

If using the combo, when the mouse freezes, THE KEYBOARD KEEPS WORKING; it is just not possible that power fails for the mouse and not for the keyboard when they are controlled by exactly the same USB device. And if there is a second mouse plugged in at the moment of the lockup, it still works (for a while) after the first one locks. Funny that it didn't choke on the lack of power together with the other mouse.

It is evident that Dell's tech have not the foggiest notion of why this fails in Linux and, worse, they have not the remotest interest in finding out. All they want is to kick the ball out of their court, and then only if asked directly.

It may well be that something is wrong in Linux -- but funnily, it only fails on this particular Dell hardware, and Dell has done nothing to either fix the hardware or fix Linux, which is what they really should do (and could easily do, too). It is astonishing that they sell a OS-less machine for customers to install Linux on it, and they havent noticed that it does not run right with A SINGLE LINUX DISTRO.

---

### Post by jorden on 2006-11-06
Maybe good news (succes story)::p 

NRios, first; I agree with you. Dell and the e521 pissed me off.
I told I would sell the e521, and still have it for-sale right now.
But.. I also kept trying and at this moment I use an internal usb-hub from SWEEX with a black front-panel.
External powered hubs didn't work for me but their power management is a little different.
This sweex was cheap and also saves a pci32 slot.
Until now... no freezes! I hope it keeps this way.

In my opinion the Dell-cpu-usb-power-story is not that strange as you
might think. Yes, also on my systems the mouse (and sometimes keyb)
freezed constantly no-matter if there was cpu-usage, but internally
and on very small time-scales things can be a little different.
I know that because of the old nForce2 80ns bug, which causes nForce2
systems to randomly lockup with usage of acpi via io-apic.
A complex story about acpi and how it works on hardware level and
the to-be-honoured protocols of usage (kernel).
On nForce2 the problem was that linux kernels do switch power-things
faster than 80ns, something Windows kernels still don't.
So nForce2 never had problems in Windoze, but in Linux it was unusable
until you enirely disable acpi, apic and lapic support in the kernel.
The story is much longer than this, but what I want to say is that
strange power issues could be possible.

But I agree, it's strange and stupid. The nForce2 workarounds do
not work here, only on Dell E521's this occurs, and Dell doesn't do 
anything to fix their 'linux machines'.

This SWEEX hub uses the internal floppy-power which is very stable
of course, doesn't do complex power-tricks with relays but is always
hard-and-simple-powered to the power supply, and maybe better:
I discovered that in some sophisticated way my mouse and keyb are
kernel enabled via ehci instead of ohci(!)
In the boot.msg log I can see that it discovers an usb2.0 hub device,
with 'low-speed' devices connected to it. The ehci module gets loaded
and I believe that it strangely enough uses this interface (but I must ivestigate better). Formerly it never loaded ehci as far as I can remember (I never connected usb2 devices and only saw ohci loaded all the times).
Looks like the sweex acts as some clever gateway device(?)

A relevant dump here:

<7>ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
<6>usb 1-5: new high speed USB device using ehci_hcd and address 2
<6>usb 1-5: new device found, idVendor=04b4, idProduct=6560
<6>usb 1-5: new device strings: Mfr=0, Product=0, SerialNumber=0
<6>usb 1-5: configuration #1 chosen from 1 choice
<6>hub 1-5:1.0: USB hub found
<6>hub 1-5:1.0: 4 ports detected
<4>nvidia: module not supported by Novell, setting U taint flag.
<4>nvidia: module license 'NVIDIA' taints kernel.
<6>Floppy drive(s): fd0 is 1.44M
<6>usb 1-5.3: new low speed USB device using ehci_hcd and address 3 :-D 
<6>usb 1-5.3: new device found, idVendor=046d, idProduct=c016
<6>usb 1-5.3: new device strings: Mfr=1, Product=2, SerialNumber=0
<6>usb 1-5.3: Product: Optical USB Mouse
<6>usb 1-5.3: Manufacturer: Logitech
<6>usb 1-5.3: configuration #1 chosen from 1 choice
<6>usb 1-5.4: new low speed USB device using ehci_hcd and address 4 :-D 
<6>usb 1-5.4: new device found, idVendor=413c, idProduct=2003
<6>usb 1-5.4: new device strings: Mfr=1, Product=2, SerialNumber=0
<6>usb 1-5.4: Product: Dell USB Keyboard
<6>usb 1-5.4: Manufacturer: Dell
<6>usb 1-5.4: configuration #1 chosen from 1 choice
<6>usbcore: registered new driver hiddev
<6>input: Logitech Optical USB Mouse as /class/input/input1
<6>input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0b.1-5.3
<6>input: Dell Dell USB Keyboard as /class/input/input2
<6>input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:0b.1-5.4
<6>usbcore: registered new driver usbhid


I read about succes stories when connecting mouse/keyb via a Dell
wide-screen flatpanel (with internal usb hub), could it be that
the same thing happens in that case?

(While I'm typing the mouse still works, and that has never happened
before on my system, also using standard SuSE10.1 kernel, no extra options, or in other words I'm back at Start but this time without
mouse freezes so far:) :) )

The sweex hub I use can be seen here:
[http://www.sweex.nl/communicatie.php?sectie=3&item=460&artikel=676](http://www.sweex.nl/communicatie.php?sectie=3&item=460&artikel=676)

I hope you guys can smile again. It's not the -best- solution (kernel
patch or bios fix would be better), but at least it saves your pci32 slots
it's black, cheap, and it seems to work so far (I'll keep you informed).

J.C. Keet

---

### Post by jorden on 2006-11-06
Forgot to tell:
Also -no- problems with the lilo menu (I read some hubs are not
enabled during system-power-up, so no possibility to enter
setup or choose other o.s. in lilo/grub).
:D 
Hope it keeps this way, but until now everything still works.
No mouse-freezes, and still 2 pci32 slots free.

---

### Post by jorden on 2006-11-08
Still working ! ;) 
Not a single problem. Mouse works, keyb works (Dell setup AND Lilo menu),
no key-repeat errors or mouse-freezes.

Using the cheap internal sweex usb-hub and standard SuSE10.1 kernel.
(x86_64, smp, apic and ACPI working, i.o.w. no extra kernel parameters 
needed)

This week I'm going to use a mainstream kernel, and I'll keep
you informed.

Important is that the boot.msg reports that mouse and keyb
are connected as slow-devices via EHCI (see my earlier comments).

---

### Post by cks_toh on 2006-11-10
I am so glad for your information there.. have been suffering much with this E521 for a week or so now for this usb mouse/keyboard freezing up on me.. ](*,)  

and i am a noob to ubuntu too.. as sugguested, i am now using an external usb hub.. and seems like it's working mighty fine now!!!8) 

usually it will be freezing up on me after a few minute into the X windows.. but so far so good.. will test it out more.. 

Thanks !!!
:D :D

p/s: if this is working fine after over this weekend.. well.. i guess, the usb power issue should be true huh?

---

### Post by jorden on 2006-11-11
If the mouse still freezes with an external hub (in my case it did)
try using an internal but at -least- check the kernel log if
your usb-1.1 hid devices (mouse/keyb) use ehci instead of ohci (see
my earlier comments, de hub-chip seems to act as a gateway).
It used to be ohci, and the ohci module gave trouble, perhaps in
combination with some power issues.
In my case (with the internal sweex hub) it's now ehci, and still no
trouble here.
I haven't tested a mainstream kernel yet, but my feelings tell
me that as long as ehci is used (a totally different piece of code
of the kernel then ohci) no trouble will appear.
:p

---

### Post by neslot on 2006-11-12
I've been having similar problems with USB on my HP laptop, thumb drive and external hd not being recognized.  Also when I first booted edgy, (64 bit) it would hang on boot.  I did a boot with nolapic and noapic and boot up was fine, but the usb's didn't work except for the cheapy belkin mouse which worked fine and has all the time.
I went back and booted with just noapic and it recognized and mounted the thumb and ext hd.  So I edited the /boot/grub/menu.lst file to: (after the 'ro') quiet splash noapic.
After booting again, it wouldn't see the mem stick/thumb drive.  I just went back and booted again with noapic as the only thing after 'ro' and the drives work again.  So, I am changing (yet again) the grub/menu.lst.  to:
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro noapic
will post again in the near future if this seems to be a lasting fix.

Tony Olsen

OK, a couple more boots and it's still working.  Must be something in 'quiet' or 'splash' that is interfering with LAPIC (Local Advanced Programmable Interrupt Controller) and not allowing EHCI to load and/or load properly.  I may go back and put splash back in when I get bored, but, it's really not needed and you can see the whole boot process without them.

Tony

---

### Post by NRios on 2006-11-13
I compiled a pristine 2.16.18.2 kernel using the config file used by Ubuntu Edgy 2.6.17 kernel; the only option I changed in the config menu was selectin optimisation for Athlon. There were no nasty surprises during compilation, and everything worked fine the first time.

I unplugged the USB hub and plugged my wireless mouse/keyboard combo directly into a USB port and rebooted. My computer booted the new kernel just fine, and unlike Edgy's 2.6.17, it reached GDM with a fully functional mouse and keyboard, which was already an improvement on the previous situation (reaching GDM with BOTH already locked).

I have not given it very extended use, but have used it for about 45 minutes with no apparent problems, which I don't think I ever could with Dapper's kernel.

What I don't know is what functionality have I given up by not running Ubuntu's kernel. What patches have they added to 2.6.17 that are absent from 2.6.18.2?

NTFS-3g works OK (an advantage of user-mode drivers). The on-board network connection works OK, but I have not yet tested the Ralink PCI wifi card. I have not tested audio yet, either. I do know that my iPod works OK from Rhythmbox, and I can read *and write* to it.

nVidia's proprietary driver does not work, unfortunately, as it is built for Ubuntu's 2.6.17; I'll have to rebuild it later for 2.6.18. However, the open-source nv driver works more or less ok and, though it does not seem to like the 1280x1024 resolution, windows move around fast with no tearing as suffered with the VESA drivers.

If anybody is interested, I've generated .deb packages that may be installed *and uninstalled* effortlessly in any Edgy installation. The entry in Grub is automatically added, and an alternative kernel (or XP) may be chosen at boot time.

---

### Post by NRios on 2006-11-14
The 2.6.18.2 kernel has been running for a whole day in my sistem, and I have actively used it for about three hours, with no mouse or keyboard lockups.

Unfortunately not everything works OK off the bat:

[LIST]
[*]ALSA does not work, and sound is output via the OSS driver, so there is no mixer and only one app can use sound at any one time.
[/LIST]
[LIST]
[*]The nVidia proprietary driver needs to be recompiled (which I have not done yet) and for some reason the open-source nvidia driver does not go further than 1024x768.
[/LIST]
[LIST]
[*]The built-in ethernet works fine, but my Ralink PCI wifi card does not.
[/LIST]
[LIST]
[*]The system activity monitor reports only one processor (just like  with Edgy's 2.6.17, actually), so I think the system is half as fast as it could be.
[/LIST]
The steps to compile the kernel and generate the debs are detailed here:

[howtoforge :: compile a kernel - the ubuntu way]("http://www.howtoforge.com/kernel_compilation_ubuntu?")

[Edited 20061120] The problem with nvidia driver and 1024x768 top resolution was solved by chanching hsync and vsync in xorg.conf, which had for some reason changed to some ridiculously low settings (25-50 KHz, which is not enough for 1280x1024@60Hz). Now the screen looks fine (with no 3D acceleration), and still no mouse locks. Still no ALSA and only one core comes up.

---

### Post by luizg on 2006-11-14
Strange, two days ago I compiled 2.6.19-rc5 and the mouse was still freezing, can you post your .config? I will try 2.6.18.2.

The sound works for me in Debian Etch, I had to install alsa-utils and then run alsaconf.

> **NRios said:**
> The 2.6.18.2 kernel has been running for a whole day in my sistem, and I have actively used it for about three hours, with no mouse or keyboard lockups.

Unfortunately not everything works OK off the bat:

[LIST]
[*]ALSA does not work, and sound is output via the OSS driver, so there is no mixer and only one app can use sound at any one time.
[/LIST]
[LIST]
[*]The nVidia proprietary driver needs to be recompiled (which I have not done yet) and for some reason the open-source nvidia driver does not go further than 1024x768.
[/LIST]
[LIST]
[*]The built-in ethernet works fine, but my Ralink PCI wifi card does not.
[/LIST]
[LIST]
[*]The system activity monitor reports only one processor (just like  with Edgy's 2.6.17, actually), so I think the system is half as fast as it could be.
[/LIST]
The steps to compile the kernel and generate the debs are detailed here:

[howtoforge :: compile a kernel - the ubuntu way]("http://www.howtoforge.com/kernel_compilation_ubuntu?")

---

### Post by NRios on 2006-11-14
I copied Edgy's config file, which is /boot/config-2.6.17-xxx, then in make menuconfig I loaded it and chose optimization for Athlon 64; I left the rest as it was.

Its disheartening to see you've had problems with 2.6.19... I hope they get fixed in the release version. I've seen reported that 2.6.18.1 (which comes with FC6) does not work either, so if I'm not deceiving myself maybe it is that the fix is really recent (let's hope!).

---

### Post by Hephaistos2 on 2006-11-14
I have been unable to build a kernel 2.6.18.* with SMP working. But 2.6.19-rc3 works well and SMP has been tested. 
But I had problem with sound. If I add support for Intel HDA the kernel stops somewhere and seems to have problems with ATA1. So I have no sound
X11 is working well, but I use an extra USB hub

---

### Post by jorden on 2006-11-14
I've compiled a 2.6.18.2 X86_64 kernel (AMD64 optimized) and it runs 
almost perfectly, also with SMP.
The only -must- I had to set was a kernel parameter acpi=noirq
so it doesn't lock up while starting. The disadvantage is that
irq routing doesn't occur (not a big deal) but ACPI still works
in all other ways.
(I can supply a working .config for 2.6.18.2 sources if you want.)

Also the internal sweex usb hub still gateways the usb1.1 mouse/keyb to
ehci ('low speed' devices using ehci interface (in kernel log) ; in my 
opinion that's THE solution to the infamous mouse-freezes.)!
In other words, my sytem is still rock-solid and I use it for days
very intensive (it used to mouse-freeze many times in a few minutes).

I also use the ATI X1300 pro vga card and even it wasn't very easy
to get a good working glx, it now runs perfectly with a correct
configured xorg.conf and compiled fglrx proprietary driver.
(I can supply a working Xorg xorg.conf file if you want)

I'm working on sound. My plan is to disable ALSA in the kernel
en compile ALSA outside of it, as I used to do in the 2.4 days.
But I don't know if it enables a lot (all?) the features of the
onboard sound chip. It didn't with the std. SuSE10.1 2.6.16 kernel
(only PCM out) with built in ALSA.
I hope that a newer ALSA version outside the kernel works better.

All (but it's not that much) other things work, also onboard network.

:)

---

### Post by mellis0 on 2006-11-14
Hi

I've joined the usb devices freeze on amd64 x2 nvidia chipset (Dell Dimension E521) club, plus like you I've got an ATI X1300 Pro PCIe graphics card.

I too struggled to get a working OpenGL Enabled X server via the ATI binary drivers, ie fglrx, but I got there!

I've compiled the 2.6.18.2 kernel and see if that works for me.

I've got an Creative Xfi sound card, so no sound card drivers for Linux until mid 2007 :(

I've got another USB issue under Windows XP Media Center 2005. I connect a Aiwa NetMD Mini Disc player via USB and that Blue Screen of Death's (BSOD) on me. I suspect its NForce USB related so I'll keep an eye on Dell's drivers and NVidias.

Its fustrating, timeconsuming but interesting see a few people with similar problems.

---

### Post by luizg on 2006-11-16
I've tested 2.6.18.2 without success, the mouse still freezes. Which kernel boot options are you using?

> **NRios said:**
> I copied Edgy's config file, which is /boot/config-2.6.17-xxx, then in make menuconfig I loaded it and chose optimization for Athlon 64; I left the rest as it was.

Its disheartening to see you've had problems with 2.6.19... I hope they get fixed in the release version. I've seen reported that 2.6.18.1 (which comes with FC6) does not work either, so if I'm not deceiving myself maybe it is that the fix is really recent (let's hope!).

---

### Post by lwatcdr on 2006-11-16
Well I solved my freezing issue buy buying an USB card :(
Not the solution I wanted but it lets me get to work.
If you can loose slot that seems like the simplest way to get up and working for now.

---

### Post by aki-andre on 2006-11-19
> **neslot said:**
>   So, I am changing (yet again) the grub/menu.lst.  to:
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro noapic
will post again in the near future if this seems to be a lasting fix.

Tony Olsen


Hi!

I have still the same problem! When I'm using the comment noapic and nolapic everything is fine but when I plugged external usb hdd the system is not recognizing it :/ 
When I'm not typing this option (noapic nolapic) there is an error appearing that I have a problem with io-apic :/ I'm not good at computers... I don't know what it is (but I know how to solve it: put a noapic comment...) but I can plug-in my external hdd and the system recognize it :/

So my question is: what is the final solution? I hope You Tony found it, so meybe You (or someone else) will help me?

P.S. Sorry for my english :(

---

### Post by nlabadie on 2006-11-19
I think I've got it. I'd tried passing "noapic" as a boot option without any luck, but when I added "noapic irqpoll" it seems to have fixed it. Three hours now without the mouse or keyboard freezing :).

[EDIT]
Argh, it just locked up. Nevermind.

---

### Post by aki-andre on 2006-11-20
So still no hope? :-)

---

### Post by dublinclontarf on 2006-11-22
Just got the same system, trying Kubuntu 6.10, and it freezes on the Kubuntu loadup, after the Kernal has loaded. This is the AMD64 version.

I've a PCI usb card, and even with system usb disabled same result, the keyboard & mouse are connected to the pci usb.

Currently downloading 32bit kubuntu 6.10 & Knoppix 501.

Once we've got some concrete workarounds we can do up a howto.

Will post later on 32 & knoppix results

---

### Post by TLu888@gmail.com on 2006-11-22
It is NOT a Linux problem!!! I have a NEW Dell E521 / Windows XP and the USB keyboard freezes 6~10 times a day.

It is a chipset/BIOS problem. Let's face it, E521 is a piece of ****, and I really regret that I bought it.

What do you do when you bought a LEMON Car?

---

### Post by dublinclontarf on 2006-11-22
> **TLu888@gmail.com said:**
> It is NOT a Linux problem!!! I have a NEW Dell E521 / Windows XP and the USB keyboard freezes 6~10 times a day.

It is a chipset/BIOS problem. Let's face it, E521 is a piece of ****, and I really regret that I bought it.

What do you do when you bought a LEMON Car?
Even though it's a problem with the chipsets a workaround does need to be found unless DELL does a complete recall. Although I have to say my machine works fine under WinXP, infact it's pretty sweet, fast user switching & duel core works pretty damn nice.

---

### Post by TLu888@gmail.com on 2006-11-23
OK, I run into more problems with Dell E521 USB ports.

Canon A430 Digital Camera will NOT work with E521 USB, while it works perfect with all 3 other PCs I tried.

I have Windows XP, so it is NOT a unix problem.

Guys, face the fact. E521 is a piece of crap, and I really regret I bought it. It is less than 1 month old. ](*,)

---

### Post by dublinclontarf on 2006-11-27
Great news, I have a version of Linux that seems to run perfectly fine!:KS 
[http://www.sabayonlinux.org](http://www.sabayonlinux.org), this is what I've got when I do a uname -a

Linux sabayonx86 2.6.18-gentoo #1 SMP Sun Oct 8 16:11:34 UTC 2006 i686 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ AuthenticAMD GNU/Linux

Boots up perfectly fine (which is better than before), no freezes or any problems. And I'm not using a hub, (I do have a pci usb card installed but the keyboard & mouse are using the onboard usb ports).

This distro is normally a DVD download, but I used the mini version which is just a CD. Available here [ftp://mudrii.ath.cx/sabayon/x86/SabayonLinux-x86-3.1-miniEdition.iso](ftp://mudrii.ath.cx/sabayon/x86/SabayonLinux-x86-3.1-miniEdition.iso)

Soon we should be able to find what the hell the problems is!

---

### Post by dublinclontarf on 2006-11-27
Sorry, it seems the installation fails 1/2 way through copying files to the hard disk. I'm gonna download the x86-64 DVD and give that a shot.

---

### Post by jimeno on 2006-11-29
same problems here, but with a Dimension C521. so, still no fix?

uh, and bad thing: i cant install the live 64 bit version, dunno why :P

i installed the 32 bit...

---

### Post by hauteboy on 2006-12-06
Does ubuntu install properly with no USB issues if you use the 'acpi=noirq' kernel option?  I've tried this on FC and SLES and I'm no longer seeing install or USB problems.

---

### Post by airzer0 on 2006-12-06
ok so after some reading on the dell forums it was sugested that either you put in a pci nic or pci usb, so i put a pci nic card, disabled the onboard nic in the bios. problem solved. my mouse does not freeze any more. 
oh i have dell c521 amd 64 running dapper.

---

### Post by batso on 2006-12-10
I have discovered a workaround for this bug.  Boot the kernel with the following parameters.

usb-handoff i8042.nomux

Make sure you don't have any acpi or apic options enabled.  Cheers!

---

### Post by mcs101 on 2006-12-12
I'm new to ubuntu and running it on a Dimension E521 AMD dual core processor and having the same problem (occasional freezes of mouse/keyboard).
How do I boot the kernel with the usb-handoff i8042.nomux parameter?
And what does that parameter do?

---

### Post by 5hundy on 2006-12-12
I too am unfortunately an owner of an e521. I changed my kernel options in /boot/grub/menu.lst from:

/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash

to:

/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash acpi=off noacpi usb-handoff i8042

and my keyboard went completely crazy. I also tried it without the "acpi=off noacpi" but my mouse still locked up. 

For the record I also tried the following:

1)Turned off the on-board nic and used a pci nic. This didn't help at all although some claim it worked for them.

2)I tried using an externally powered usb hub. This also didn't help although some claim it worked for them.

3)I tried using a pci usb card but for whatever reason i could not get the kernel to recognize the card so I gave up on that route.

If anyone gets something to work please please say specifically what you did and/or what hardware you used.

---

### Post by 5hundy on 2006-12-12
> **airzer0 said:**
> ok so after some reading on the dell forums it was sugested that either you put in a pci nic or pci usb, so i put a pci nic card, disabled the onboard nic in the bios. problem solved. my mouse does not freeze any more. 
oh i have dell c521 amd 64 running dapper.

Are you running dapper32 or 64?

---

### Post by mulsoft on 2006-12-14
Hi,

I have installed a cheap (I think Sweex) pci usb card which works fine with edgy 32 bits.
No lockups. My keyboard is in one of the on-board usb ports otherwise you cannot enter the BIOS. My mouse is on the pci card.

For some reason I cannot install edgy 64 bits, I see the graphics grey logo and then my system hangs.

i have an E521 :mad:

---

### Post by 5hundy on 2006-12-14
Yeah looks like getting a pci card is a good way to go. For the record I got an "**HP 5 port USB 2.0 pci host card**" HP product number P8294AA#ABA. There is also a Compaq branded version of the same card. I put it in, disabled the usb controller and I've been running without a mouse lockup for over a day now. 

Note: I tried another card with the VT6212L chipset (not the one HP uses) and it **didn't get recognized** by the kernel. It seems the Via VT6212L is a pretty popular one so be on the lookout for that if you plan on getting a pci usb card.

Also note that I think the machine is designed to enable the usb controller on startup so you won't "brick" your box if you disable the usb and then for whatever reason you can't get your controller card to work. At least that was my experience when I tried unsuccessfully to get the via chipset card to work.

---

### Post by NRios on 2006-12-26
I have tried kernels later than 2.6.18.3 and they seem to work OK as for the USB hangups. However, I missed the stuff that Ubuntu adds to the pristine kernel.org sources (wireless drivers, ALSA sound stuff and surely more things), so the results I got could definitely be better.

Now there's an easy solution to get an Ubuntu 2.6.20 kernel. I have tried it in a white box computer in my office, but not yet in the Dell, so I don't really know if it will fix the USB problem. The procedure is simple, but be careful not to UPGRADE to feisty; me want to get feisty's *kernel only*

[LIST]
[*]run "sudo gedit /etc/apt/sources.list", and change "edgy" for "feisty" in the line where the main repository is referenced
[*]run "sudo apt-get update" from the console (***WARNING:*** NOT UPGRADE -- you only want to download the new package *LIST*
[*]run "sudo apt-get install linux-386" and accept its dependencies (linux-image-386, linux-restricted-modules-386 and linux-restricted-modules-common)
[*]run "sudo gedit /etc/apt/sources.list" and change "feisty" back to "edgy"
[*]run "sudo apt-get update", to be sure you're safely back with edgy's repositories
[/LIST]

Reboot, and there should be a 2.6.20 entry in grub, that I hope should have no problems with the USB mouse. I'll try it tonight at home.

Of course, if it blows up your computer, sets your house on fire, or causes any unpleasant results, I decline any responsibility.

---

### Post by turingtest on 2007-01-02
Dell released a BIOS upgrade for the Dell E521 today.  After upgrading the BIOS with the new release I was able to run Ubuntu 6.10 for over an hour without any USB mouse lockups.  Hopefully, this fixes the problems we've all been seeing with Dell E521's.

---

### Post by mellis0 on 2007-01-02
Hi

I've just upgraded to BIOS 1.1.4 available on the Dell website, and things are looking promising, as suggested by the previous poster.

Plus the BIOS upgrade addresses a Windows XP Media Centre Blue Screen of Death issue I was having when transferring music files to a Mini Disc player.

Regards
Mark

---

### Post by bodzasfanta on 2007-01-04
Hello!

I had a similar problem but thanks God someone told me a good way to fix it.

"In grub, hit e to edit the boot line. Then move the selection over the kernel line and hit e again. Move the cursor to the end of the line and add the following:
Code:

noapic irqpoll pci=routeirq

Then hit enter to get our of line editing mode and b to boot the modified kernel line.

This will set you up until you power down or reboot. Edit /boot/grub/menu.list to make it permanent." (thanks for Frem)

I hope I could help you

---

### Post by dobbytictocard on 2007-01-05
It seems to be fixed after BIOS upgrade,  "noapic irqpoll pci=routeirq" and without "acpi=off" in the /boot/grub/menu.lst

3 hours without a freeze ! Great !

---

### Post by ceestand on 2007-01-05
I wasn't able to even get through the install without losing mouse, keyboard, or both. Updating the bios seems to have solved the problem. 4+ hours last night with no issues.

p.s. Thanks Ubuntu Forums!

---

### Post by neoflight on 2007-01-18
my E521 is working fine as of now. It automatically mounts my usb flash drives.(back).... doesnt freeze....

i am using 32 bit edgy ubuntu installation.

i tried putting 64B edgy server edition and couldnt boot from the cd. so i tried 32bit desktop and its working fine...sometimes it gives weired screens ...some problem with xorg....but working fine with the resolution i want...

edit: yes i updated the bios to 1.1.4 from dell website....

---

### Post by Zer0Nin3r on 2007-01-23
All is said and good, but what if you're not running a Dell?  I'm experiencing these problems with an Asus M2N32-SLI Deluxe using a Logitech MX3200 wireless keyboard & Mouse.  I only experience the problem when I get up and leave the computer for a period of 5 minutes or more.  As long as I use either the keyboard or mouse I don't lose the connectivity...

I've upgraded the bios, tried disabling the power management through the services menu, I have the legacy support enabled under the bios, tried acpi=off during the boot up (that led to problems with mp3 playback within amoraK), and the last time I tried the irqpol pci=routeirq the system froze at the boot up splash screen (I'm thinking of trying it again though...)

I'll only lose the mouse, everything funtions normally i.e. clock keeps time, music keeps playing, screen saver comes on.

---

### Post by magicfab on 2007-01-24
I have started a wiki page about the n-series Dell Dimension desktops so other people can find this information quickly:
[https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDellnSeries](https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDellnSeries)

---

### Post by Zer0Nin3r on 2007-01-27
Success!!

So, I didn't have to make any crazy changes to any of the xorg.conf files or the like.  I ended up going into the bios and enabling* Plug & Play support* and everything seems to be working fine now.  I also have USB Legacy Support enabled.

---

### Post by e45rpm on 2007-01-28
I was having the same problems with the mouse not functioning after a while of use.  I have an optical mouse, and the light would still be on, but the curser would not respond to any movements or mouse clicks.  I ended up upgrading the BIOS, and that seems to have worked for me.

I also have to say, I saw a lot of people saying how they didn't like their Dell E521's.  I have one, and it has really worked out well for me.  This mouse problem is honestly the only problem that I have had with this machine.  Honestly, isn't it a little silly to start considering selling a computer because of a problem that is easily solved?  Patching the BIOS took all of 5 minutes.

---

### Post by neoflight on 2007-02-14
Problem solved as of now! have to do some thorough testing before I could conclude !

I am using Dell E531 AMD Athlon 64B X2 machine. 
I was having terrible problems with mouse lockup. I am still connected to the built-in usb port (back) . I upgraded to BIOS 1.1.4 version with no good result.
I never had a mouse freeze in windows XP. 

I am now dual booting with Debian Sid using 
```
 2.6.20-1-amd64 #1 SMP Sat Feb 10 01:09:27 CET 2007 x86_64 GNU/Linux
```

Added kernel argument at the boot line...

```
title           Debian GNU/Linux, kernel 2.6.20-1-amd64
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-1-amd64 root=/dev/sda1 ro [COLOR="Red"]**noapic irqpoll pci=routeirq**[/COLOR]
initrd          /boot/initrd.img-2.6.20-1-amd64
savedefault

title           Debian GNU/Linux, kernel 2.6.20-1-amd64 (single-user mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-1-amd64 root=/dev/sda1 ro [COLOR="Red"]**noapic irqpoll pci=routeirq **[/COLOR]single
initrd          /boot/initrd.img-2.6.20-1-amd64

```

haven't checked the sound...since its an office PC i am not too concerned about sound issue...
==============================================
```
lspci 
```
[HTML]rcoe51:/home/euclid# lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7183
03:00.1 Display controller: ATI Technologies Inc Unknown device 71a3
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
[/HTML]
================================================
```
dmesg
```

[PHP]Linux version 2.6.20-1-amd64 (Debian 2.6.20-1~experimental.1~snapshot.8297) (waldi@debian.org) (gcc version 4.1.2 20061115 (prerelease) (Debian 4.1.1-21)) #1 SMP Sat Feb 10 01:09:27 CET 2007
Command line: root=/dev/sda1 ro noapic irqpoll pci=routeirq
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
 BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
 BIOS-e820: 000000003fee0000 - 000000003fee3000 (ACPI NVS)
 BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data)
 BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved)
 BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
 BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Entering add_active_range(0, 256, 261856) 1 entries of 3200 used
end_pfn_map = 1048576
DMI 2.4 present.
ACPI: RSDP (v000 DELL                                  ) @ 0x00000000000f83d0
ACPI: RSDT (v001 DELL    bMk     0x42302e31 AWRD 0x00000000) @ 0x000000003fee3040
ACPI: FADT (v001 DELL    bMk     0x42302e31 AWRD 0x00000000) @ 0x000000003fee3100
ACPI: BOOT (v001 DELL    bMk     0x42302e31 AWRD 0x00000000) @ 0x000000003fee8b40
ACPI: SSDT (v001 PTLTD  POWERNOW 0x00000001  LTP 0x00000001) @ 0x000000003fee8c80
ACPI: HPET (v001 DELL    bMk     0x42302e31 AWRD 0x00000098) @ 0x000000003fee8f40
ACPI: MCFG (v001 DELL    bMk     0x42302e31 AWRD 0x00000000) @ 0x000000003fee8fc0
ACPI: SLIC (v001 DELL    bMk     0x42302e31 AWRD 0x0100000e) @ 0x000000003fee9040
ACPI: MADT (v001 DELL    bMk     0x42302e31 AWRD 0x00000000) @ 0x000000003fee8bc0
ACPI: DSDT (v001 DELL    BMK     0x00001000 MSFT 0x0100000e) @ 0x0000000000000000
Scanning NUMA topology in Northbridge 24
Number of nodes 1
Node 0 MemBase 0000000000000000 Limit 000000003fee0000
Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Entering add_active_range(0, 256, 261856) 1 entries of 3200 used
NUMA: Using 63 for the hash shift.
Using node hash shift of 63
Bootmem setup node 0 0000000000000000-000000003fee0000
Zone PFN ranges:
  DMA             0 ->     4096
  DMA32        4096 ->  1048576
  Normal    1048576 ->  1048576
early_node_map[2] active PFN ranges
    0:        0 ->      159
    0:      256 ->   261856
On node 0 totalpages: 261759
  DMA zone: 56 pages used for memmap
  DMA zone: 985 pages reserved
  DMA zone: 2958 pages, LIFO batch:0
  DMA32 zone: 3524 pages used for memmap
  DMA32 zone: 254236 pages, LIFO batch:31
  Normal zone: 0 pages used for memmap
ACPI: PM-Timer IO Port: 0x1008
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Processor #0 (Bootup-CPU)
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Processor #1
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
ACPI: Skipping IOAPIC probe due to 'noapic' option.
ACPI: HPET id: 0x10b9a201 base: 0xfeff0000
Using ACPI for processor (LAPIC) configuration information
Intel MultiProcessor Specification v1.4
MPTABLE: OEM ID: OEM00000 MPTABLE: Product ID: PROD00000000 MPTABLE: APIC at: 0xFEE00000
I/O APIC #2 at 0xFEC00000.
Setting APIC routing to physical flat
Processors: 2
Nosave address range: 000000000009f000 - 00000000000a0000
Nosave address range: 00000000000a0000 - 00000000000f0000
Nosave address range: 00000000000f0000 - 0000000000100000
Allocating PCI resources starting at 40000000 (gap: 3ff00000:b0100000)
SMP: Allowing 2 CPUs, 0 hotplug CPUs
PERCPU: Allocating 36992 bytes of per cpu data
Built 1 zonelists.  Total pages: 257194
Kernel command line: root=/dev/sda1 ro noapic irqpoll pci=routeirq
Misrouted IRQ fixup and polling support enabled
This may significantly impact system performance
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 32768 bytes)
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
Checking aperture...
CPU 0: aperture @ 9b16000000 size 32 MB
Aperture too small (32 MB)
No AGP bridge found
Memory: 1021892k/1047424k available (1969k kernel code, 25144k reserved, 921k data, 284k init)
Calibrating delay using timer specific routine.. 4845.69 BogoMIPS (lpj=9691394)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Capability LSM initialized
Mount-cache hash table entries: 256
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
CPU 0/0 -> Node 0
CPU: Physical Processor ID: 0
CPU: Processor Core ID: 0
SMP alternatives: switching to UP code
ACPI: Core revision 20060707
ACPI: setting ELCR to 0200 (from 8ca0)
Using local APIC timer interrupts.
result 12526108
Detected 12.526 MHz APIC timer.
SMP alternatives: switching to SMP code
Booting processor 1/2 APIC 0x1
Initializing CPU#1
spurious 8259A interrupt: IRQ7.
Calibrating delay using timer specific routine.. 4846.11 BogoMIPS (lpj=9692221)
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
CPU 1/1 -> Node 0
CPU: Physical Processor ID: 0
CPU: Processor Core ID: 1
AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ stepping 02
CPU 1: Syncing TSC to CPU 0.
CPU 1: synchronized TSC with CPU 0 (last diff 0 cycles, maxerr 583 cycles)
Brought up 2 CPUs
testing NMI watchdog ... OK.
time.c: Using 25.000000 MHz WALL HPET GTOD HPET timer.
time.c: Detected 2405.010 MHz processor.
migration_cost=334
NET: Registered protocol family 16
ACPI: bus type pci registered
PCI: Using MMCONFIG at f0000000
PCI: No mmconfig possible on device 00:18
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (0000:00)
PCI: Probing PCI hardware (bus 00)
Boot video device is 0000:03:00.0
PCI: Transparent bridge - 0000:00:10.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNK4] (IRQs *5 7 9 10 11 14 15)
ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 *11 14 15)
ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNK7] (IRQs 5 *7 9 10 11 14 15)
ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 11 14 *15)
ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
ACPI: PCI Interrupt Link [LPMU] (IRQs 5 *7 9 10 11 14 15)
ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: ACPI device : hid PNP0A08
pnp: ACPI device : hid PNP0C02
pnp: ACPI device : hid PNP0C02
pnp: ACPI device : hid PNP0200
pnp: ACPI device : hid PNP0B00
pnp: ACPI device : hid PNP0800
pnp: ACPI device : hid PNP0C04
pnp: ACPI device : hid PNP0C02
pnp: ACPI device : hid PNP0C01
pnp: PnP ACPI: found 9 devices
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
PCI: Using ACPI for IRQ routing
PCI: Routing PCI interrupts for all devices because "pci=routeirq" specified
ACPI: PCI Interrupt Link [LSMB] enabled at IRQ 10
PCI: setting IRQ 10 as level-triggered
ACPI: PCI Interrupt 0000:00:0a.1[A] -> Link [LSMB] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI Interrupt Link [LUBA] enabled at IRQ 15
PCI: setting IRQ 15 as level-triggered
ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUBA] -> GSI 15 (level, low) -> IRQ 15
ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 5
PCI: setting IRQ 5 as level-triggered
ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUB2] -> GSI 5 (level, low) -> IRQ 5
ACPI: PCI Interrupt Link [LSID] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LSID] -> GSI 11 (level, low) -> IRQ 11
ACPI: PCI Interrupt Link [LFID] enabled at IRQ 10
ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LFID] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 10
ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 11
ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
ACPI: PCI Interrupt Link [LNK4] enabled at IRQ 5
ACPI: PCI Interrupt 0000:04:07.0[A] -> Link [LNK4] -> GSI 5 (level, low) -> IRQ 5
hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
hpet0: 3 32-bit timers, 25000000 Hz
pnp: the driver 'system' has been registered
pnp: match found with the PnP device '00:01' and the driver 'system'
pnp: 00:01: ioport range 0x1000-0x107f could not be reserved
pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
pnp: 00:01: ioport range 0x1400-0x147f has been reserved
pnp: 00:01: ioport range 0x1480-0x14ff could not be reserved
pnp: 00:01: ioport range 0x1800-0x187f has been reserved
pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
pnp: 00:01: ioport range 0x2000-0x207f has been reserved
pnp: 00:01: ioport range 0x2080-0x20ff has been reserved
pnp: match found with the PnP device '00:02' and the driver 'system'
pnp: match found with the PnP device '00:07' and the driver 'system'
pnp: match found with the PnP device '00:08' and the driver 'system'
PCI: Bridge: 0000:00:02.0
  IO window: a000-afff
  MEM window: fda00000-fdafffff
  PREFETCH window: fd900000-fd9fffff
PCI: Bridge: 0000:00:03.0
  IO window: 8000-8fff
  MEM window: fd800000-fd8fffff
  PREFETCH window: fde00000-fdefffff
PCI: Bridge: 0000:00:04.0
  IO window: b000-bfff
  MEM window: fdd00000-fddfffff
  PREFETCH window: d0000000-dfffffff
PCI: Bridge: 0000:00:10.0
  IO window: 9000-9fff
  MEM window: fdc00000-fdcfffff
  PREFETCH window: fdb00000-fdbfffff
PCI: Setting latency timer of device 0000:00:02.0 to 64
PCI: Setting latency timer of device 0000:00:03.0 to 64
PCI: Setting latency timer of device 0000:00:04.0 to 64
PCI: Setting latency timer of device 0000:00:10.0 to 64
NET: Registered protocol family 2
IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
TCP: Hash tables configured (established 131072 bind 65536)
TCP reno registered
checking if image is initramfs... it is
Freeing initrd memory: 5237k freed
Simple Boot Flag at 0x3a set to 0x80
audit: initializing netlink socket (disabled)
audit(1171459197.848:1): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered (default)
PCI: Setting latency timer of device 0000:00:02.0 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:02.0:pcie00]
Allocate Port Service[0000:00:02.0:pcie03]
PCI: Setting latency timer of device 0000:00:03.0 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:03.0:pcie00]
Allocate Port Service[0000:00:03.0:pcie03]
PCI: Setting latency timer of device 0000:00:04.0 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:04.0:pcie00]
Allocate Port Service[0000:00:04.0:pcie03]
Real Time Clock Driver v1.12ac
Linux agpgart interface v0.101 (c) Dave Jones
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
pnp: the driver 'serial' has been registered
RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
pnp: the driver 'i8042 kbd' has been registered
pnp: the driver 'i8042 aux' has been registered
pnp: the driver 'i8042 kbd' has been unregistered
pnp: the driver 'i8042 aux' has been unregistered
PNP: No PS/2 controller found. Probing ports directly.
serio: i8042 KBD port at 0x60,0x64 irq 1
serio: i8042 AUX port at 0x60,0x64 irq 12
mice: PS/2 mouse device common for all mice
TCP bic registered
NET: Registered protocol family 1
NET: Registered protocol family 17
NET: Registered protocol family 8
NET: Registered protocol family 20
ACPI: (supports S0 S1 S3 S4 S5)
Freeing unused kernel memory: 284k freed
ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUB2] -> GSI 5 (level, low) -> IRQ 5
PCI: Setting latency timer of device 0000:00:0b.1 to 64
ehci_hcd 0000:00:0b.1: EHCI Host Controller
ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
ehci_hcd 0000:00:0b.1: debug port 1
PCI: cache line size of 64 is not supported by device 0000:00:0b.1
ehci_hcd 0000:00:0b.1: irq 5, io mem 0xfe02e000
ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 8 ports detected
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
pnp: the driver 'ide' has been registered
ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
SCSI subsystem initialized
ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUBA] -> GSI 15 (level, low) -> IRQ 15
PCI: Setting latency timer of device 0000:00:0b.0 to 64
ohci_hcd 0000:00:0b.0: OHCI Host Controller
ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
ohci_hcd 0000:00:0b.0: irq 15, io mem 0xfe02f000
libata version 2.00 loaded.
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 8 ports detected
sata_nv 0000:00:0e.0: version 3.2
ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LSID] -> GSI 11 (level, low) -> IRQ 11
PCI: Setting latency timer of device 0000:00:0e.0 to 64
ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xE000 irq 11
ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xE008 irq 11
scsi0 : sata_nv
ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata1.00: ATA-7, max UDMA/133, 312500000 sectors: LBA48 NCQ (depth 0/32)
ata1.00: ata1: dev 0 multi count 16
ata1.00: configured for UDMA/133
scsi1 : sata_nv
usb 2-3: new low speed USB device using ohci_hcd and address 2
usb 2-3: configuration #1 chosen from 1 choice
ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
usb 2-4: new low speed USB device using ohci_hcd and address 3
ata2.00: ATAPI, max UDMA/33
usb 2-4: configuration #1 chosen from 1 choice
usbcore: registered new interface driver hiddev
input: Dell Dell USB Mouse as /class/input/input0
input: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:0b.0-3
input: Dell Dell USB Keyboard as /class/input/input1
input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:0b.0-4
usbcore: registered new interface driver usbhid
drivers/usb/input/hid-core.c: v2.6:USB HID core driver
ata2.00: configured for UDMA/33
scsi 0:0:0:0: Direct-Access     ATA      ST3160812AS      3.AD PQ: 0 ANSI: 5
scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-H653A D300 PQ: 0 ANSI: 5
ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LFID] -> GSI 10 (level, low) -> IRQ 10
PCI: Setting latency timer of device 0000:00:0f.0 to 64
ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xCC00 irq 10
ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xCC08 irq 10
scsi2 : sata_nv
ata3: SATA link down (SStatus 0 SControl 300)
ATA: abnormal status 0x7F on port 0x9E7
scsi3 : sata_nv
ata4: SATA link down (SStatus 0 SControl 300)
ATA: abnormal status 0x7F on port 0x967
b44.c:v1.01 (Jun 16, 2006)
ACPI: PCI Interrupt 0000:04:07.0[A] -> Link [LNK4] -> GSI 5 (level, low) -> IRQ 5
PCI: Setting latency timer of device 0000:04:07.0 to 64
eth0: Broadcom 4400 10/100BaseT Ethernet 00:18:8b:59:66:04
SCSI device sda: 312500000 512-byte hdwr sectors (160000 MB)
sda: Write Protect is off
sda: Mode Sense: 00 3a 00 00
SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
SCSI device sda: 312500000 512-byte hdwr sectors (160000 MB)
sda: Write Protect is off
sda: Mode Sense: 00 3a 00 00
SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sda: sda1 sda2 sda3 sda4
sd 0:0:0:0: Attached scsi disk sda
Attempting manual resume
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: recovery complete.
EXT3-fs: mounted filesystem with ordered data mode.
sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Uniform CD-ROM driver Revision: 3.20
sr 1:0:0:0: Attached scsi CD-ROM sr0
sd 0:0:0:0: Attached scsi generic sg0 type 0
sr 1:0:0:0: Attached scsi generic sg1 type 5
i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
i2c_adapter i2c-1: nForce2 SMBus adapter at 0x1c40
input: PC Speaker as /class/input/input2
ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 10 (level, low) -> IRQ 10
PCI: Setting latency timer of device 0000:00:10.1 to 64
hda_intel: azx_get_response timeout, switching to polling mode...
Adding 1116508k swap on /dev/sda4.  Priority:-1 extents:1 across:1116508k
EXT3 FS on sda1, internal journal
loop: loaded (max 8 devices)
device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
kjournald starting.  Commit interval 5 seconds
EXT3 FS on sda3, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
ADDRCONF(NETDEV_UP): eth0: link is not ready
b44: eth0: Link is up at 100 Mbps, full duplex.
b44: eth0: Flow control is off for TX and off for RX.
ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
pnp: the driver 'parport_pc' has been registered
lp: driver loaded but no devices found
ppdev: user-space parallel port driver
eth0: no IPv6 routers present
mtrr: no more MTRRs available
mtrr: no more MTRRs available
mtrr: no more MTRRs available
mtrr: no more MTRRs available
mtrr: no more MTRRs available
[/PHP]

```
xorg.conf
```

> Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc ATI Default Card"
        Driver          "fglrx"
        BusID           "PCI:3:0:0"
EndSection


---

### Post by xxsludgexx on 2007-02-28
so the general consensus is to apply the bios update from dell?

---

### Post by mclazarus on 2007-02-28
It has been working well for me with Ubuntu 6.10 and the latest kernel updates since I have applied the Dell BIOS update.

---

### Post by sherlock-holmes on 2007-03-01
uograding BIOS didnt solve my problem...

and add this.. on to ur booting kernel line...in boot/grub/menu.lst

>  ro noapic irqpoll pci=routeirq***

i never had a freeze after that....problem solved !

*** there were identical suggestions in many posts in this thread and elsewhere

---

### Post by samji1 on 2007-03-25
I don't have a spare slot for a front-facing SWEEX internal usb-hub as both 5.25 slots have DVD players in them. are there alternatives to this ? Thanks

---

### Post by samji1 on 2007-03-26
I seem to have resolved my random usb related hardware freeze problem today. I have a new Dimension 9200. I was asked by Dell to switch the DVD cable on SATA 2 to SATA 5 and then make the necessary BIOS changes to reflect that. It seems to have worked so far.

---

