---
title: "Shutdown issue"
date: 2013-08-17
forum: General Help
---

### Post by Redjama on 2013-08-17
Every time I try and shut the comp down I get the following message and it wont shut down, it just sits at that screen.

```
The system is going down for halt NOW!
speech-dispatcher disabled: edit /etc/default/speech-dispatcher
```

Anyone have any ideas?

---

### Post by Crusty Old Fart on 2013-08-18
Let's see what's in /etc/default/speech-dispatcher.
Please post the output of the following command:
```

cat /etc/default/speech-dispatcher

```

Also, please provide answers to the following two questions:
Is your intention to have the computer power off after it has been brought down, or do you just want it to halt?
How are you initiating the shutdown?

---

### Post by Redjama on 2013-08-18
> **Crusty Old Fart said:**
> Let's see what's in /etc/default/speech-dispatcher.
Please post the output of the following command:
```

cat /etc/default/speech-dispatcher

```

Also, please provide answers to the following two questions:
Is your intention to have the computer power off after it has been brought down, or do you just want it to halt?
How are you initiating the shutdown?

```
brian@brian-Aspire-3680:~$ cat /etc/default/speech-dispatcher# Defaults for the speech-dispatcher initscript, from speech-dispatcher


# Set to yes to start system wide Speech Dispatcher
RUN=yes
brian@brian-Aspire-3680:~$ 



```

I changed it to "yes instead of "no" last night to see if that changed anything. Only thing it changes is that with "yes" it sits at the Ubuntu screen shutting down instead of the screen that gave me the message.  I want the computer to power off.  It also does the same thing on a reboot, just sits at that screen.

---

### Post by Crusty Old Fart on 2013-08-18
Okay Brian,

My system shuts down the way you want yours to shut down.

I have never edited my speech-dispatcher. Here's what I get when I look to see what's in it:
```

cat /etc/default/speech-dispatcher

**[COLOR=green]~~~ output ~~~[/COLOR]**

# Change to yes if you would like speech-dispatcher to run as a system service.
RUN_SPEECHD=no

```

Notice that my variable is named RUN_SPEECHD. Yours is apparently just named RUN. If it has always been that way, then the reason is probably due to us running different versions of Ubuntu. I'm running 10.04 LTS. However, if you changed the variable name from RUN_SPEECHD to just RUN, then you should change it back to RUN_SPEECHD. Either way, you should change it back to having a value of "no" (without the quotes).

I don't expect that editing the speech-dispatcher to put it back to the way it was before you changed it last night will have any effect on the shutdown problem.

Thank you for answering my questions. I don't think I was clear enough with my second question, so I'll ask it in a different way:

When you initiate shutdown, are you typing a command into a terminal window (shell), clicking on a launcher that runs a script you have written, mashing a hotkey on your keyboard, clicking on a shutdown icon that has always been one of your desktop features, or by some other method that I haven't mentioned?

Right now, whatever you're doing to shut down your system is not powering it off after bringing it down. Instead, it is "halting" it. Halting doesn't not "power off" the computer.
Please read the manpage for the shutdown command:
```

man shutdown

```
Let's see if the next command works from the shell.
Your system should go down for power off almost immediately after you supply your password to run the following command as root:
```

sudo shutdown -P now

```

In your next post, please answer the question about how you have been initiating shutdown and let me know if the command in the code box above powered off the machine.

Thanks,

Crusty

---

### Post by Redjama on 2013-08-18
I tried the shutdown code you gave me and it did the same exact thing, just sits at the shutdown screen.  Im running Ubuntu 13.04 fully updated.  Im trying to shutdown using the shutdown button in the top left corner.

---

### Post by Crusty Old Fart on 2013-08-18
> **brian9 said:**
> I tried the shutdown code you gave me and it did the same exact thing, just sits at the shutdown screen.  Im running Ubuntu 13.04 fully updated.  Im trying to shutdown using the shutdown button in the top left corner.

Oh, bummage. 

There is a -k option for the shutdown command that will only send out the warning messages and disable logins, it will not actually bring the system down. The -k option can be helpful for testing.
Please enter the following commands and paste the output you get from them in code boxes in your next post. The commands are case sensitive. Notice the some of the uppercase options.
```

sudo shutdown -Pk now

```
Mashing your [Enter] key after issuing the command will bring back your input prompt.

Let's also see the output you get from this command:
```

sudo shutdown -Hk now

```
Again, mashing your [Enter] key after issuing the command will bring back your input prompt.

Finally, just for the hell of it, let's see what you get for output from this command:
```

sudo shutdown -rk now

```
Again, mash your [Enter] key.

Hopefully, the output you get from these commands will shed some light on what's happening under the hood.

---

### Post by Redjama on 2013-08-18
```
brian@brian-Aspire-3680:~$ sudo shutdown -Pk now[sudo] password for brian: 


Broadcast message from brian@brian-Aspire-3680
	(/dev/pts/0) at 14:32 ...


The system is going down for power off NOW!
brian@brian-Aspire-3680:~$ sudo shutdown -Hk now


Broadcast message from brian@brian-Aspire-3680
	(/dev/pts/0) at 14:32 ...


The system is going down for halt NOW!
brian@brian-Aspire-3680:~$ sudo shutdown -rk now


Broadcast message from brian@brian-Aspire-3680
	(/dev/pts/0) at 14:33 ...


The system is going down for reboot NOW!
brian@brian-Aspire-3680:~$ 



```

---

### Post by Crusty Old Fart on 2013-08-18
Well, all that output looks like it should.

And yet, you write that this:
```

sudo shutdown -P now

```
doesn't power off the computer.

Let's try something a little different to capture some output from a time delayed command that you can cancel.
Issue the following command:
```

sudo shutdown -P +3

```
This command is supposed to power off the computer in three minutes.
So, you have three minutes to cancel it by mashing [Crtl+C]
After you cancel the command, you should be able to copy its output to a code box and post it.
Please do that.

Thanks,

Crusty

---

### Post by Redjama on 2013-08-18
```
brian@brian-Aspire-3680:~$ sudo shutdown -P +3[sudo] password for brian: 


Broadcast message from brian@brian-Aspire-3680
	(/dev/pts/0) at 15:03 ...


The system is going down for power off in 3 minutes!
^Cshutdown: Shutdown cancelled
brian@brian-Aspire-3680:~$
```

---

### Post by Crusty Old Fart on 2013-08-18
Thanks. That output is fine too.

There's a chance we can get around this bug by editing your bootloader.
Please post the output of the following command:
```

cat /etc/default/grub

```

---

### Post by Redjama on 2013-08-18
```
brian@brian-Aspire-3680:~$ cat /etc/default/grub# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
brian@brian-Aspire-3680:~$ 



```

---

### Post by Crusty Old Fart on 2013-08-18
Thanks.

Before we edit the grub file, we are going to make a copy of it and verify that our copy was actually saved.
Please be very careful and issue the commands exactly as I explain them. The grub file is an important one that we don't want to mess up.
Make a copy of your grub file with the following command:
```

sudo cp -p /etc/default/grub /etc/default/grub_copy081813

```

Now for verification, please post the output from the following command:
```

ls -al /etc/default/grub*

```

Also, the shutdown bug may have something to do with your video driver.
Please post the output of the following command:
```

lspci

```

I'm being very deliberate with everything I'm writing now. Please follow my instructions carefully and don't rush anything.
I'd also like to know if you know how to edit files from the shell and if so, what editor you use.

---

### Post by Redjama on 2013-08-18
```
brian@brian-Aspire-3680:~$ ls -al /etc/default/grub*-rw-r--r-- 1 root root 1237 Aug 17 19:28 /etc/default/grub
-rw-r--r-- 1 root root 1237 Aug 17 19:28 /etc/default/grub_copy08181

```

```
brian@brian-Aspire-3680:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```

I run gedit through terminal and it brings up a text editor. Not sure which one, whatever comes with it out of the box

---

### Post by Crusty Old Fart on 2013-08-18
Good job. That was perfect.

I use the vi editor, So, I'm not exactly sure on how to bring up gedit from the shell. But, for the editing we're going to do now, you'll need to become root. Perhaps you can do that with sudo in front of the command you use to bring up your editor.

So...a command to open the grub file with your editor might look something like this:
```

sudo your_editor_command /etc/default/grub

```

After the grub file opens in your editor, you'll want to add the text shown in **[COLOR=green]bold green[/COLOR]** In the code box below and then save your changes,
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **[COLOR=#008000]acpi=force[/COLOR]**"
GRUB_CMDLINE_LINUX="**[COLOR=#008000]acpi=force[/COLOR]**"


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Check to make sure that you didn't make any mistakes by looking at what the shell gives you for the following command:
```

cat /etc/default/grub

```
When you are sure that you've performed the editing correctly, issue the following command:
```

sudo update-grub

```
Now try to reboot your computer. If it hangs like it always does, manually power it down and boot it back up and try again. It may be that the changes to grub need to go through a power cycle before loading. I just don't remember.

Don't get your hopes up too high. It may be that this only works one time. Some folks have had that problem. For others, this has been a lasting fix.

Please let me know what happens.

One more thing. We can always reverse all the changes we've made if this doesn't work. I'll help you through that if we need to.

---

### Post by Redjama on 2013-08-18
Still does the exact same thing.

---

### Post by Crusty Old Fart on 2013-08-18
Sorry for the delay. My computer took a deep dive.
We should put everything back to how it was before we started all this today.
It won't take very long.
Would you like to do that now?

---

### Post by Redjama on 2013-08-18
Yea thats fine

---

### Post by Crusty Old Fart on 2013-08-18
Here's how to undo everything we did:
```

sudo cp -p /etc/default/grub_copy0818* /etc/default/grub
sudo update-grub

### This next command is optional. It removes the copy that we made of the grub file before we started. ###

sudo rm /etc/default/grub_copy0818*

```
That's all there is to it.

I'll need to do some more poking around on the 'nut to see some more of how other folks may have fixed this problem.
It would help if you would make at least one more post to this thread by placing the output of the following command into a code box:
```

lshw

```

I'll hang in here until you let me know that you didn't have any problems executing the commands in this post.

---

### Post by Crusty Old Fart on 2013-08-18
**[COLOR=blue]EDIT: Disregard this post. I hadn't made an error after all.[/COLOR]**

[COLOR=red][s][COLOR=black]I made an error in the copy command I gave you above. It won't work with the wild card.
And I can't really be sure of what the name really is of the copy of the grub file we made based on what you posted above.

Please run the following command so I can see what the name of the file really is:
```

ls -al /etc/default/grub*

```

Sorry, and thanks.

Crusty[/COLOR][/s][/COLOR]

---

### Post by Redjama on 2013-08-18
```
brian@brian-Aspire-3680:~$ lshwWARNING: you should run this program as super-user.
brian-aspire-3680         
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1500MiB
     *-cpu
          product: Intel(R) Celeron(R) M CPU        440  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          size: 1900MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc arch_perfmon bts aperfmperf pni monitor tm2 xtpr pdcm dtherm
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:d0300000-d037ffff ioport:1800(size=8) memory:c0000000-cfffffff memory:d0400000-d043ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:d0380000-d03fffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:d0440000-d0443fff
        *-pci:0
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:64000000-642fffff ioport:64300000(size=2097152)
           *-network
                description: Ethernet interface
                product: 88E8038 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 14
                serial: 00:1b:24:2b:00:18
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:43 memory:64000000-64003fff ioport:2000(size=256)
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:64500000-647fffff ioport:64800000(size=2097152)
           *-network
                description: Network controller
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=wl latency=0
                resources: irq:17 memory:64500000-64503fff
        *-pci:2
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:64a00000-64bfffff ioport:64c00000(size=2097152)
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:d0644000-d06443ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:5000(size=4096) memory:d0200000-d02fffff ioport:60000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 9
                bus info: pci@0000:0a:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:20 memory:d0204000-d0204fff ioport:5000(size=256) ioport:5400(size=256) memory:60000000-63ffffff memory:68000000-6bffffff
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 9.2
                bus info: pci@0000:0a:09.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7
                resources: irq:20 memory:d0205000-d0205fff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:18b0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18c0(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: ec:1a:59:b0:d9:e8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.254.4 multicast=yes wireless=IEEE 802.11bg
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
brian@brian-Aspire-3680:~$ 



```

Sorry it took so long, got a little hectic here.

---

### Post by Crusty Old Fart on 2013-08-18
> **brian9 said:**
> ...Sorry it took so long, got a little hectic here.
No problem. As they say: Stuff Occurs.

If everything went okay with reverting back to the way things were,
could you please post the output of the following command:
```

ls -al /etc/default/grub*

```

Sorry we weren't able to fix the problem. I see that your graphics card is an integrated (on-board) Intel controller. There may be a hardware conflict with the version of Ubuntu you are running and that gpu.
Maybe we'll get lucky and find someone on the 'nut who has the same setup as you do and was able to fix the problem.

---

### Post by Redjama on 2013-08-18
```
brian@brian-Aspire-3680:~$ ls -al /etc/default/grub*-rw-r--r-- 1 root root 1237 Aug 17 19:28 /etc/default/grub
-rw-r--r-- 1 root root 1237 Aug 17 19:28 /etc/default/grub~
brian@brian-Aspire-3680:~$
```

---

### Post by Crusty Old Fart on 2013-08-18
Good job. You did it. Everything looks fine.
There are two grub files there. They look to be identical other than their file names.
One of them is: grub
The other is: grub~
I'm guessing you did that deliberately to keep a copy of the original grub file, which is fine. I do the same.

Unless you have anything else, this will be my last post today.

Best of luck to you and thanks for your patience,

Crusty

---

### Post by Redjama on 2013-08-18
> **Crusty Old Fart said:**
> Good job. You did it. Everything looks fine.
There are two grub files there. They look to be identical other than their file names.
One of them is: grub
The other is: grub~
I'm guessing you did that deliberately to keep a copy of the original grub file, which is fine. I do the same.

Unless you have anything else, this will be my last post today.

Best of luck to you and thanks for your patience,

Crusty


Thank you for your help, it sucks we couldnt get this figured out.

---

### Post by Crusty Old Fart on 2013-08-19
[FONT=Verdana]From the looks of things, it appears that your       computer is an Acer laptop, model: Aspire-3680. My guess is that       it may be about five or six years old. My experience with Linux       and antediluvian hardware has convinced me that the best chance of       getting things to work properly is to install a distribution of       Linux that is just a little newer than your hardware. In my case,       I'm running 10.04 on a computer that I built ten years ago and the       server version of 8.04 on a computer that I built sixteen years       ago. In order to get the sixteen year old machine to work, I had       to find a newer version of the BIOS for it and re-flash.
      
      I've seen folks on the web having problems with 12.04 powering off       on shutdown similar to the problem you are having. So, you may       have to consider a version of Ubuntu older that 12.04.
      
      I'm assuming that you've been having the problem ever since you       installed 13.04, that your 13.04 is a new installation rather than       an upgrade installation, that you've never run any other version       of Ubuntu on that machine, and that you have installed it as a       second operating system (dual boot) so you can choose to run       Ubuntu or some version of Windows during the boot process.
      
      It's possible that a fresh reinstall of 13.04 may not present you       with the shutdown problem. But, I wouldn't pin too many hopes on       that happening.
      
      If you really want to load an Ubuntu OS on that machine, and you       don't mind using an older version, I'd be happy to help       you get it done.
Ubuntu releases can be found here: [http://releases.ubuntu.com/](http://releases.ubuntu.com/) and here: [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

On the other hand, if the video drivers are responsible for the problem, we may have help from Intel.
(Ref.: [https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2](https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2))

      So, what say you, Brian?[/FONT]

---

### Post by Redjama on 2013-08-20
Didnt even know you had made another reply.  My apologies. I say we start with the video drivers.  Ive been seeing that Unity has been causing shutdown problems on Dell Machines, not my particular machine itself, but the issues they are having are identical to what Im having.  Lets start with the video drivers and see where that goes.

---

### Post by Crusty Old Fart on 2013-08-20
> **brian9 said:**
> Didnt even know you had made another reply.  My apologies. I say we start with the video drivers.  Ive been seeing that Unity has been causing shutdown problems on Dell Machines, not my particular machine itself, but the issues they are having are identical to what Im having.  Lets start with the video drivers and see where that goes.
Okay. In preparation for that, I'd like to know how old your laptop is.
I also need to know if you have access to another computer that you can use to post here while we're working on the laptop.
Lastly, it would be nice to know what kernel modules get loaded, so please post the output from the following command:
```

lsmod

```
I need to poke my nose into the information on the the Intel link a little deeper and refresh my memory as to how to change drivers. I also need to make sure I have a plan in place that will allow us to undo everything we change and put the machine back to the state it was in before we started in the event that things don't go well for us.

---

### Post by Redjama on 2013-08-20
```
brian@brian-Aspire-3680:~$ lsmodModule                  Size  Used by
parport_pc             27504  0 
ppdev                  12817  0 
bnep                   17669  2 
rfcomm                 37420  0 
bluetooth             202109  10 bnep,rfcomm
r8712u                162545  0 
wl                   3027822  1 
snd_hda_codec_realtek    63791  1 
snd_hda_intel          38307  3 
snd_hda_codec         117580  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
coretemp               13131  0 
i915                  545385  3 
snd_seq_midi           13132  0 
joydev                 17097  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
pcmcia                 39544  0 
tifm_7xx1              12905  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
drm_kms_helper         47056  1 i915
yenta_socket           27095  0 
acer_wmi               27592  0 
lpc_ich                16925  0 
tifm_core              15068  1 tifm_7xx1
drm                   235837  4 i915,drm_kms_helper
snd_timer              24411  2 snd_pcm,snd_seq
microcode              18286  0 
psmouse                81065  0 
snd                    56485  15 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
pcmcia_rsrc            18191  1 yenta_socket
sparse_keymap          13658  1 acer_wmi
lib80211               14040  1 wl
soundcore              12600  1 snd
pcmcia_core            21505  3 pcmcia,pcmcia_rsrc,yenta_socket
i2c_algo_bit           13197  1 i915
cfg80211              436177  1 wl
serio_raw              13031  0 
wmi                    18590  1 acer_wmi
video                  18894  2 i915,acer_wmi
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
sky2                   52846  0 
brian@brian-Aspire-3680:~$
```

Looks like the MFG date is 07/04.  Ubuntu is the only OS I have installed.  I normally run PcLinuxOs, I took the dive to Ubuntu to give it a whirl.  I refuse to use Winblows. I do have another comp I can use or I can use my phone, doesnt matter.

---

### Post by Crusty Old Fart on 2013-08-20
Thanks, I'm glad you have another machine. It would be much better than using your phone. However, if the phone can take pictures that you can upload to a post, that might be a godsend. It's a round about way to take a screen shot from a machine when there's no other way to capture what's on the screen, like BIOS menus.

Here are some more questions:
The last time we worked on stuff here, you did everything really well. Was I going to slow for you? Would you prefer that I didn't go into as much detail?
Would it be a disaster if we do something that requires you to reinstall the OS, or is that an option we could consider as a solution if we wanted to try something a little risky?
We may get into something that doesn't give us a good place to stop what we're doing and turn off the computer. So it would be nice to know what our time difference is. I'm in the Pacific (US) time zone. It is 8:48pm here now.

We need to know the kernel release. Please post the output of the following command:
```

uname -r

```

---

### Post by Crusty Old Fart on 2013-08-21
I can hardly believe this. I should have told you this in my first post. I fixed this same problem with my computer several years ago by adding the kernel option reboot=b to my grub file. I've known about this all along. I just didn't remember it. So sorry.

So here's how to do it:

If you still have your copy of the original grub file that you saved as: /etc/default/grub~ then you don't need to make another one. If not, then run the following command:
```

sudo cp -p /etc/default/grub /etc/default/grub~

```

Next, as root, you want to edit /etc/default/grub by adding the kernel option shown as **[COLOR=blue]bold blue text[/COLOR]** in the code box below:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="**[COLOR=blue]reboot=b[/COLOR]** quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Now you need to make it stick by running the following command:
```

sudo update-grub

```

Next, you need to shutdown your machine and physically turn it off.

Then boot it up.

I will be *VERY* surprised if this doesn't fix the problem.

If it doesn't, then we can fart around with updating your graphics driver, but I really don't pin much hope on that helping.

Please let me know what happens.

Thanks. And again, my apologies for not remembering this fix. Jeeez!

Crusty

---

### Post by Redjama on 2013-08-21
I edited what you told me to this morning before I went to work and I still get the same thing.  We are 4 hours apart.  Im in EST

```
brian@brian-Aspire-3680:~$ uname -r
3.8.0-29-generic
brian@brian-Aspire-3680:~$
```

---

### Post by Crusty Old Fart on 2013-08-21
> **brian9 said:**
> I edited what you told me to this morning before I went to work and I still get the same thing.  We are 4 hours apart.  Im in EST...

Damn! That sucks.

Alrighty then, I reckon we can try updating your video driver. Right now, you're using the i915 default Intel driver, which is built into your kernel. Also, from what I've discovered on Intel's web page, there doesn't appear to be any conflicts with your hardware or your kernel release. So we should be good to go.

I believe we are three hours apart. It is 2:22 pm here. It should be 5:22pm at your place.

If things go badly for us, would it be a disaster if you had to reinstall the OS from scratch?

---

### Post by Redjama on 2013-08-21
> **Crusty Old Fart said:**
> Damn! That sucks.

Alrighty then, I reckon we can try updating your video driver. Right now, you're using the i915 default Intel driver, which is built into your kernel. Also, from what I've discovered on Intel's web page, there doesn't appear to be any conflicts with your hardware or your kernel release. So we should be good to go.

I believe we are three hours apart. It is 2:22 pm here. It should be 5:22pm at your place.

If things go badly for us, would it be a disaster if you had to reinstall the OS from scratch?


No it wouldnt be, I just installed the other day.  Havent really set anything up yet.  Just been messing around on here

---

### Post by Crusty Old Fart on 2013-08-21
I'd like you to create a script that updates your installed software, cleans up leftover files that are no longer needed, configures your packages, and updates your initramfs and grub.
This script has saved my bacon so many times in the past that it has become my "magic wand" when my system gets balled up and it has never caused me any problems.
It's like dynamite for a logjam.

For ease of communication, please name it: sys_update.sh
Save it somewhere in your home directory that's easy for you to remember. We may use it again later.
It **must** be run as root.

Here's the code that you can cut and paste into it:
```

#!/bin/bash
set -e

apt-get update
apt-get upgrade -y
apt-get clean
apt-get autoremove
dpkg --configure -a
update-initramfs -k all -u
update-grub

exit 0

```

When you're sure you have everything entered correctly, run it.

If you'd like to post its output, I'd be happy to look at it. I'll leave that up to you.

After you've run it, let me know and we can proceed with getting your video driver updated.

---

### Post by Redjama on 2013-08-21
Im assuming it went through.  I copy and pasted and terminal disappeared immediately after i pasted.  I dont think im doing something right.

---

### Post by Crusty Old Fart on 2013-08-21
Nope. That shouldn't have happened.
Please tell me where you saved the script and what you named it.

---

### Post by Redjama on 2013-08-21
I dont think it saved anywhere.  Think I may need a walk thought...lol.  Im confused!!




I believe I got it this time.  Didnt save it though.  Had a brain fart on how to save it

---

### Post by Crusty Old Fart on 2013-08-21
No problem.

From a terminal window, issue the following command to make sure you're in your home directory:
```

cd ~

```
Now create the file as an empty file using the following command:
```

touch sys_update.sh

```
Then open the file ~/sys_update.sh with your gedit editor
Copy and paste the code from Post #34 into the gedit window
Click on save. Exit the gedit editor.

Make the file executable with the following command:
```

chmod 700 ~/sys_update.sh

```
Become root with the following command:
```

sudo su

```
Run the file with the following command:
```

./sys_update.sh

```
If it runs, correctly, you should see a whole bunch of output come flying out of it and the last few lines before it returns you to your input prompt will be similar to:
```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found memtest86+ image: /memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sdb1
done

```
You'll have different image arguments and won't have the Window XP line,
Now you should end your root session by typing: exit
The terminal window should take you right back to your user input prompt.

How's that? Clear as mud?

---

### Post by Redjama on 2013-08-21
Ok, finally got it

---

### Post by Crusty Old Fart on 2013-08-21
[FONT=Verdana]Good.
  
Now we can being installing the new driver.
  
First we need to add keys to Ubuntu's software package manager ("apt"). Open a terminal, and execute these lines, one at a time:
```

wget --no-check-certificate https://download.01.org/gfx/RPM-GPG-KEY-ilg -O - | sudo apt-key add -
  
wget --no-check-certificate https://download.01.org/gfx/RPM-GPG-KEY-ilg-2 -O - | sudo apt-key add -
  

```
  
Let me know when you're done with that and I'll post the next step.
  
[/FONT]

---

### Post by Redjama on 2013-08-21
Done.

---

### Post by Crusty Old Fart on 2013-08-21
Good.

Here's a link that should install the driver. Click on it and use your intuition on what you need to do next:

[Linux Graphics Installer for Ubuntu* 13.04, 32-bit](https://download.01.org/gfx/ubuntu/13.04/main/pool/13.04/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.2-0intel3_i386.deb)

Sorry to leave you flying solo on this one, but I can't install this on my system, so I can't give you a click by click set of instructions on what to do. Hopefully, Intel will take over and do the heavy lifting for you or they will make the process intuitive enough to be obviously simple.

---

### Post by Crusty Old Fart on 2013-08-21
Do you see the Intel logo or the Intel Linux Graphics Installer in your application dashboard?

---

### Post by Redjama on 2013-08-21
ok thats all done

---

### Post by Crusty Old Fart on 2013-08-21
> **brian9 said:**
> ok thats all done

Do you see the Intel logo or the Intel Linux Graphics Installer in your application dashboard?

---

### Post by Redjama on 2013-08-21
I already installed everyting

---

### Post by Crusty Old Fart on 2013-08-21
Okay.
Please post the output for the following commands (one at a time):
```

ls -al ~/sys*

cat /etc/default/grub

```

---

### Post by Redjama on 2013-08-21
```
brian@brian-Aspire-3680:~$ ls -al ~/sys*
-rwx------ 1 brian brian 154 Aug 21 18:29 /home/brian/sys_update.sh
-rw-rw-r-- 1 brian brian  26 Aug 21 18:25 /home/brian/sys_update.sh~



```

```
brian@brian-Aspire-3680:~$ cat /etc/default/grub# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="reboot=b quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
brian@brian-Aspire-3680:~$ 



```

---

### Post by Crusty Old Fart on 2013-08-21
Thanks. There's a little bit of cleanup we'll do later.
Right now, we need to re-launch the kernel.
The only way I know of to make that happen is to reboot the machine.
So, go ahead and reboot--you'll probably still have to physically turn off the computer after it halts.

---

### Post by Crusty Old Fart on 2013-08-21
Any luck?
Did we just brick the laptop?
Does your monitor look any different?
Will the machine power off when you click on shutdown?
Enquiring geeks want to know ](*,)

---

### Post by Redjama on 2013-08-21
> **Crusty Old Fart said:**
> Any luck?
Did we just brick the laptop?
Does your monitor look any different?
Will the machine power off when you click on shutdown?
Enquiring geeks want to know ](*,)


Nope were good. Still have to manually shut down. The screen was blue this time.

---

### Post by Crusty Old Fart on 2013-08-21
Well, I reckon things could have been a lot worse.
Let's leave grub the way it is with the reboot=b kernel option in it for now.
We should to a little bit of cleanup. The file: ~/sys_update.sh~ isn't any good. Let's remove it:
```

rm ~/sys_update.sh~

```
Now let's look at a few things. Please run the following three commands (one at a time) and post their output:
```

dpkg-query -l '*intel*'

lsmod

cat ~/sys_update.sh

```

---

### Post by Redjama on 2013-08-21
```
brian@brian-Aspire-3680:~$ dpkg-query -l '*intel*'Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  intel-gpu-tool 1.3-0ubuntu2 i386         tools for debugging the Intel gra
ii  intel-linux-gr 1.0.2-0intel i386         Intel graphics drivers update uti
ii  libdrm-intel1: 2.4.45-0ubun i386         Userspace interface to intel-spec
ii  libva-intel-va 1.2.0-0ubunt all          VAAPI driver for Intel G45 & HD G
ii  xserver-xorg-v 2:2.21.9-0ub i386         X.Org X server -- Intel i8xx, i9x



```

```
brian@brian-Aspire-3680:~$ lsmodModule                  Size  Used by
parport_pc             27504  0 
ppdev                  12817  0 
bnep                   17669  2 
rfcomm                 37420  0 
bluetooth             202109  10 bnep,rfcomm
r8712u                162545  0 
snd_hda_codec_realtek    63791  1 
wl                   3027822  1 
snd_hda_intel          38307  3 
snd_hda_codec         117580  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
coretemp               13131  0 
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
i915                  545385  3 
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 39544  0 
joydev                 17097  0 
snd_rawmidi            25114  1 snd_seq_midi
tifm_7xx1              12905  0 
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
yenta_socket           27095  0 
tifm_core              15068  1 tifm_7xx1
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
microcode              18286  0 
pcmcia_rsrc            18191  1 yenta_socket
acer_wmi               27592  0 
snd_timer              24411  2 snd_pcm,snd_seq
drm_kms_helper         47056  1 i915
psmouse                81065  0 
lpc_ich                16925  0 
pcmcia_core            21505  3 pcmcia,pcmcia_rsrc,yenta_socket
sparse_keymap          13658  1 acer_wmi
lib80211               14040  1 wl
drm                   235837  4 i915,drm_kms_helper
snd                    56485  15 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
cfg80211              436177  1 wl
serio_raw              13031  0 
soundcore              12600  1 snd
i2c_algo_bit           13197  1 i915
wmi                    18590  1 acer_wmi
mac_hid                13037  0 
video                  18894  2 i915,acer_wmi
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
sky2                   52846  0 
```

```
brian@brian-Aspire-3680:~$ cat ~/sys_update.sh
#!/bin/bash
set -e


apt-get update
apt-get upgrade -y
apt-get clean
apt-get autoremove
dpkg --configure -a
update-initramfs -k all -u
update-grub


exit 0
brian@brian-Aspire-3680:~$ 



```

---

### Post by Crusty Old Fart on 2013-08-21
The Intel driver upgrade appears to be an upgrade to the default i915 driver that is a kernel module. If that's the case, and it sure looks that way, it's good. We didn't end up with a proprietary driver that ended up giving us conflicts. Also, the driver should update automatically now by the system since we have added the certification keys to the package manager. That's good too. I think we're done with the driver upgrade. Good job, Brian.

Your ~/sys_update.sh file looks perfect. Now would be a really good time to run it again, power off, reboot, and then see if the system will power off by clicking on shutdown.

So, here are the steps:

Open a terminal window and make sure you're in your home directory:
```

cd ~

```
Become root:
```

sudo su

```
Run the sys_update.sh script:
```

./sys_update.sh

```
You should expect it to throw a lot of output and end with the word: **done** all by itself on the last line.
Then shutdown--and physically power off (as always).
Boot up again and see if the machine will finally power off by itself when you click the shutdown icon.
It probably won't.
After you post whether or not it's finally working, I'll know if I need to go looking for another hat somewhere that has a rabbit in it.
If I need to go rabbit hat hunting, I won't be posting anymore tonight.

Good luck. I think we both deserve it.

Crusty

---

### Post by Redjama on 2013-08-21
Well I shouldve known better.  Still the same thing.  Im going to bed....lol. Try again tomorrow.  Thanks for your help.

---

### Post by Crusty Old Fart on 2013-08-21
You're mighty welcome.
Good night.

---

### Post by Crusty Old Fart on 2013-08-22
We've been farting around using a shotgun approach to throw everything we can think of at this problem. And so far, we haven't hit the target. Now it's time to get serious and take aim.

The computer is experiencing a power off failure. When it comes to power control and distribution in computers, the BIOS is responsible for some of it, and so is the operating system. Our biggest problem right now is that we don't know what the "mechanism" of failure is. If we can discover that, we'll be able to target it with a solution. Most BIOS configuration utilities have settings in them which can be used to configure some power related parameters. There are also power related settings that we can specify in the Grub bootloader, especially as kernel boot options. I believe that our solution may involve reconfiguring the BIOS, the bootloader, or both. But, there are so many settings and so many options that the number of combinations and permutations make for a situation that is incredibly difficult to fix through trial and error.

So, now, instead of giving the patient another useless injection, we're going to have a little conversation with him until he tells us what is making him sick.

Please post the output from the following command:
```

dmesg

```
...and we'll see what he has to say to our first question. It will be a lot. Please post all of it.

It would also be helpful if you could post the manufacturer and version of your BIOS. That information is often found on its first screen.

Thanks,

Crusty

---

### Post by Redjama on 2013-08-22
```
[    1.965837] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1[    1.965840] usb usb2: Product: UHCI Host Controller
[    1.965843] usb usb2: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.965846] usb usb2: SerialNumber: 0000:00:1d.0
[    1.965970] hub 2-0:1.0: USB hub found
[    1.965977] hub 2-0:1.0: 2 ports detected
[    1.966079] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.966084] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.966091] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.966133] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.966175] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.966179] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.966182] usb usb3: Product: UHCI Host Controller
[    1.966185] usb usb3: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.966188] usb usb3: SerialNumber: 0000:00:1d.1
[    1.966298] hub 3-0:1.0: USB hub found
[    1.966303] hub 3-0:1.0: 2 ports detected
[    1.966403] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.966408] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.966415] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.966457] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.966499] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.966503] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.966506] usb usb4: Product: UHCI Host Controller
[    1.966509] usb usb4: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.966512] usb usb4: SerialNumber: 0000:00:1d.2
[    1.966620] hub 4-0:1.0: USB hub found
[    1.966626] hub 4-0:1.0: 2 ports detected
[    1.966725] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.966730] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.966739] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.966782] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    1.966825] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.966828] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.966831] usb usb5: Product: UHCI Host Controller
[    1.966835] usb usb5: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.966838] usb usb5: SerialNumber: 0000:00:1d.3
[    1.966949] hub 5-0:1.0: USB hub found
[    1.966954] hub 5-0:1.0: 2 ports detected
[    1.967141] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.983178] i8042: Detected active multiplexing controller, rev 1.1
[    1.990676] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.990685] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.990718] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.990746] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.990777] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.990915] mousedev: PS/2 mouse device common for all mice
[    1.991140] rtc_cmos 00:05: RTC can wake from S4
[    1.991304] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.991340] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.991471] device-mapper: uevent: version 1.0.3
[    1.991549] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.991575] EISA: Probing bus 0 at eisa.0
[    1.991582] Cannot allocate resource for EISA slot 1
[    1.991585] Cannot allocate resource for EISA slot 2
[    1.991588] Cannot allocate resource for EISA slot 3
[    1.991590] Cannot allocate resource for EISA slot 4
[    1.991593] Cannot allocate resource for EISA slot 5
[    1.991609] EISA: Detected 0 cards.
[    1.991622] cpufreq-nforce2: No nForce2 chipset.
[    1.991653] cpuidle: using governor ladder
[    1.991689] cpuidle: using governor menu
[    1.991694] ledtrig-cpu: registered to indicate activity on CPUs
[    1.991696] EFI Variables Facility v0.08 2004-May-17
[    1.991911] ashmem: initialized
[    1.992092] TCP: cubic registered
[    1.992235] NET: Registered protocol family 10
[    1.992491] NET: Registered protocol family 17
[    1.992506] Key type dns_resolver registered
[    1.992699] Using IPI No-Shortcut mode
[    1.992796] Loading module verification certificates
[    1.998677] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 3f91e9adadd74ee2134f443ced3a922f70cb07ef'
[    1.998694] registered taskstats version 1
[    2.001961] Key type trusted registered
[    2.004739] Key type encrypted registered
[    2.007969] rtc_cmos 00:05: setting system clock to 2013-08-22 01:40:18 UTC (1377135618)
[    2.008078] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.008080] EDD information not available.
[    2.027711] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.084707] ata2.00: ATAPI: Slimtype DVD C  DS24CZP, PA11, max UDMA/33
[    2.100343] ata2.00: configured for UDMA/33
[    2.133608] ata1.00: ATA-8: ST9250315AS, 0001BSM1, max UDMA/133
[    2.133612] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.148762] ata1.00: configured for UDMA/133
[    2.148906] scsi 0:0:0:0: Direct-Access     ATA      ST9250315AS      0001 PQ: 0 ANSI: 5
[    2.149143] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.149215] sd 0:0:0:0: [sda] Write Protect is off
[    2.149220] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.149252] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.149518] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.151544] scsi 1:0:0:0: CD-ROM            Slimtype DVD C  DS24CZP   PA11 PQ: 0 ANSI: 5
[    2.155572] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
[    2.155577] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.155704] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.155859] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.204921]  sda: sda1 sda2 < sda5 >
[    2.205277] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.205340] Freeing unused kernel memory: 788k freed
[    2.205704] Write protecting the kernel text: 6260k
[    2.205773] Write protecting the kernel read-only data: 2436k
[    2.205774] NX-protecting the kernel data: 3980k
[    2.223679] udevd[94]: starting version 175
[    2.276093] usb 1-2: new high-speed USB device number 2 using ehci-pci
[    2.365904] sky2: driver version 1.30
[    2.365943] sky2 0000:02:00.0: enabling device (0000 -> 0003)
[    2.365995] sky2 0000:02:00.0: Yukon-2 FE chip revision 1
[    2.366112] sky2 0000:02:00.0: irq 43 for MSI/MSI-X
[    2.366427] sky2 0000:02:00.0 eth0: addr 00:1b:24:2b:00:18
[    2.410578] usb 1-2: New USB device found, idVendor=050d, idProduct=945a
[    2.410584] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.410588] usb 1-2: Product: Belkin USB Wireless Adaptor
[    2.410591] usb 1-2: Manufacturer: Manufacturer Realtek 
[    2.410594] usb 1-2: SerialNumber: 00e04c000001
[    2.520066] usb 1-3: new high-speed USB device number 3 using ehci-pci
[    2.652462] usb 1-3: New USB device found, idVendor=04b4, idProduct=6560
[    2.652467] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.652751] hub 1-3:1.0: USB hub found
[    2.652844] hub 1-3:1.0: 4 ports detected
[    2.734268] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.734274] EXT4-fs (sda1): write access will be enabled during recovery
[    2.924213] usb 1-3.3: new full-speed USB device number 4 using ehci-pci
[    3.019080] usb 1-3.3: New USB device found, idVendor=046d, idProduct=c52f
[    3.019087] usb 1-3.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.019090] usb 1-3.3: Product: USB Receiver
[    3.019093] usb 1-3.3: Manufacturer: Logitech
[    3.065027] usbcore: registered new interface driver usbhid
[    3.065032] usbhid: USB HID core driver
[    3.083054] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.0/input/input5
[    3.083325] hid-generic 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.7-3.3/input0
[    3.086454] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.1/input/input6
[    3.087559] hid-generic 0003:046D:C52F.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.7-3.3/input1
[    3.100220] usb 1-3.4: new low-speed USB device number 5 using ehci-pci
[    3.197831] usb 1-3.4: New USB device found, idVendor=05b8, idProduct=3155
[    3.197836] usb 1-3.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.197839] usb 1-3.4: Product: GE 98134
[    3.197842] usb 1-3.4: Manufacturer: GE 98134
[    3.202307] input: GE 98134 GE 98134 as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4:1.0/input/input7
[    3.202430] hid-generic 0003:05B8:3155.0003: input,hidraw2: USB HID v1.00 Keyboard [GE 98134 GE 98134] on usb-0000:00:1d.7-3.4/input0
[    3.209806] input: GE 98134 GE 98134 as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4:1.1/input/input8
[    3.210165] hid-generic 0003:05B8:3155.0004: input,hiddev0,hidraw3: USB HID v1.00 Mouse [GE 98134 GE 98134] on usb-0000:00:1d.7-3.4/input1
[    3.866013] EXT4-fs (sda1): recovery complete
[    3.875582] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    6.798985] Adding 1561596k swap on /dev/sda5.  Priority:-1 extents:1 across:1561596k 
[    7.662516] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.933521] udevd[337]: starting version 175
[    8.900472] Disabling lock debugging due to kernel taint
[    9.047228] lp: driver loaded but no devices found
[    9.894843] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.191160] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.195762] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9
[   10.545118] intel_rng: FWH not detected
[   10.741459] cfg80211: Calling CRDA to update world regulatory domain
[   10.795219] wmi: Mapper loaded
[   10.914691] [drm] Initialized drm 1.1.0 20060810
[   10.928914] lib80211: common routines for IEEE802.11 drivers
[   10.928919] lib80211_crypt: registered algorithm 'NULL'
[   10.957305] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[   10.957315] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.957321] ACPI Warning: 0x000011b0-0x000011bf SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   10.957326] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.957328] ACPI Warning: 0x00001180-0x000011af SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   10.957333] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.957335] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   10.969490] yenta_cardbus 0000:0a:09.0: CardBus bridge found [1025:0110]
[   10.969519] yenta_cardbus 0000:0a:09.0: Using CSCINT to route CSC interrupts to PCI
[   10.969522] yenta_cardbus 0000:0a:09.0: Routing CardBus interrupts to PCI
[   10.969529] yenta_cardbus 0000:0a:09.0: TI: mfunc 0x01321b22, devctl 0x66
[   11.201712] yenta_cardbus 0000:0a:09.0: ISA IRQ mask 0x0cf8, PCI irq 20
[   11.201719] yenta_cardbus 0000:0a:09.0: Socket status: 30000006
[   11.201725] pci_bus 0000:0a: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   11.201736] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge window: [io  0x5000-0x5fff]
[   11.201740] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff:
[   11.250212] acer_wmi: Acer Laptop ACPI-WMI Extras
[   11.250653] acer_wmi: Function bitmap for Communication Device: 0x27
[   11.250661] acer_wmi: Disabling ACPI video driver
[   11.203233]  excluding 0x5000-0x50ff 0x5400-0x54ff
[   11.255337] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge window: [mem 0xd0200000-0xd02fffff]
[   11.255344] pcmcia_socket pcmcia_socket0: cs: memory probe 0xd0200000-0xd02fffff:
[   11.255347]  excluding 0xd0200000-0xd020ffff
[   11.255359] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge window: [mem 0x60000000-0x63ffffff pref]
[   11.255363] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x63ffffff:
[   11.255375]  excluding 0x60000000-0x63ffffff
[   11.270329] input: Acer BMA150 accelerometer as /devices/virtual/input/input10
[   11.357856] microcode: CPU0 sig=0x6ec, pf=0x20, revision=0x54
[   11.740814] leds_ss4200: no LED devices found
[   12.325514] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   12.329736] [drm] 
[   12.332185] [drm] Memory usable by graphics device = 256M
[   12.332199] i915 0000:00:02.0: setting latency timer to 64
[   12.334446] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   12.334451] [drm] Driver supports precise vblank timestamp query.
[   12.334534] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.344597] [drm] initialized overlay support
[   12.382083] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000/0x0, board id: 3655, fw id: 235996
[   12.497484] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
[   12.657884] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af:
[   12.659050]  excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   12.659912] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff:
[   12.660378]  excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   12.660787] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff:
[   12.661456]  clean.
[   12.661476] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
[   12.662218]  clean.
[   12.662241] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[   12.662246]  excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xdc000-0xdffff 0xe4000-0xfffff
[   12.662279] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff:
[   12.662297]  clean.
[   12.662317] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff:
[   12.662329]  excluding 0x60000000-0x60ffffff
[   12.662351] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[   12.663116]  clean.
[   12.684737] fbcon: inteldrmfb (fb0) is primary device
[   12.798875] Console: switching to colour frame buffer device 160x64
[   12.805650] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   12.805653] i915 0000:00:02.0: registered panic notifier
[   12.806219] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.807540] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input12
[   12.808504] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.209807] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   13.411092] hda_codec: ALC883: SKU not ready 0x411111f0
[   13.422536] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   13.422816] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   13.423052] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   13.680601] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.691350] wl 0000:03:00.0: enabling device (0000 -> 0002)
[   13.693858] malloc in abgphy done
[   13.694078] wl driver 6.20.155.1 (r326264) failed with code 21
[   13.694106] ------------[ cut here ]------------
[   13.694157] Kernel BUG at f99299da [verbose debug info unavailable]
[   13.694210] invalid opcode: 0000 [#1] SMP 
[   13.694259] Modules linked in: wl(POF+) snd_hda_codec_realtek snd_hda_intel snd_hda_codec coretemp snd_hwdep(F) snd_pcm(F) snd_page_alloc(F) snd_seq_midi(F) i915(OF) snd_seq_midi_event(F) tifm_7xx1 snd_rawmidi(F) snd_seq(F) tifm_core joydev(F) snd_seq_device(F) pcmcia snd_timer(F) microcode(F) acer_wmi sparse_keymap drm_kms_helper(OF) psmouse(F) yenta_socket lpc_ich lib80211 drm(OF) snd(F) wmi pcmcia_rsrc serio_raw(F) cfg80211 soundcore(F) pcmcia_core i2c_algo_bit video(F) mac_hid lp(F) parport(F) hid_generic usbhid hid sky2
[   13.694871] Pid: 371, comm: modprobe Tainted: PF          O 3.8.0-29-generic #42-Ubuntu Acer, inc. Aspire 3680     /Prespa1         
[   13.694969] EIP: 0060:[<f99299da>] EFLAGS: 00010246 CPU: 0
[   13.695062] EIP is at wl_cfg80211_detach+0xca/0xd0 [wl]
[   13.695106] EAX: 00000000 EBX: f46f6c90 ECX: f4f6dd00 EDX: f46f6c90
[   13.695158] ESI: f754a000 EDI: f4f6dd00 EBP: f4f03c2c ESP: f4f03c1c
[   13.695210]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   13.695255] CR0: 8005003b CR2: bff5ef70 CR3: 34f14000 CR4: 000007f0
[   13.695308] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
[   13.695360] DR6: ffff0ff0 DR7: 00000400
[   13.695394] Process modprobe (pid: 371, ti=f4f02000 task=f6d28000 task.ti=f4f02000)
[   13.695455] Stack:
[   13.695476]  f4f03c24 f46f6c90 f754a000 f4f6dd00 f4f03c44 f99222f3 f46f6c0c f46f6c00
[   13.695586]  f754a000 f4f6d800 f4f03cf0 f992305b c104bc47 c1a02980 00000400 00000096
[   13.695696]  c19e2078 0201826c 0000032b 00000000 00000002 00000000 0000032c 0000032c
[   13.695805] Call Trace:
[   13.695864]  [<f99222f3>] wl_free_if.isra.9+0x23/0xb0 [wl]
[   13.695945]  [<f992305b>] wl_free+0x7b/0x240 [wl]
[   13.695990]  [<c104bc47>] ? console_unlock+0x337/0x480
[   13.696015]  [<f9842e92>] ? wlc_attach+0xf6c/0xfda [wl]
[   13.696015]  [<c160a746>] ? printk+0x4d/0x4f
[   13.696015]  [<f9afa518>] wl_pci_probe+0x4ff/0xfe7 [wl]
[   13.696015]  [<c103ce08>] ? default_spin_lock_flags+0x8/0x10
[   13.696015]  [<c161406d>] ? _raw_spin_lock_irqsave+0x2d/0x40
[   13.696015]  [<c13ed797>] ? __pm_runtime_resume+0x57/0x70
[   13.696015]  [<c1317729>] pci_device_probe+0x79/0xb0
[   13.696015]  [<c13e332c>] driver_probe_device+0x5c/0x1e0
[   13.696015]  [<c1317683>] ? pci_match_device+0xb3/0xc0
[   13.696015]  [<c13e3541>] __driver_attach+0x91/0xa0
[   13.696015]  [<c13e34b0>] ? driver_probe_device+0x1e0/0x1e0
[   13.696015]  [<c13e1b12>] bus_for_each_dev+0x42/0x80
[   13.696015]  [<c13e2eee>] driver_attach+0x1e/0x20
[   13.696015]  [<c13e34b0>] ? driver_probe_device+0x1e0/0x1e0
[   13.696015]  [<c13e2b7f>] bus_add_driver+0x16f/0x250
[   13.696015]  [<c1317520>] ? pci_device_shutdown+0x50/0x50
[   13.696015]  [<c13e3b2a>] driver_register+0x6a/0x160
[   13.696015]  [<f9afa000>] ? 0xf9af9fff
[   13.696015]  [<c13168f3>] __pci_register_driver+0x33/0x40
[   13.696015]  [<f9afa017>] wl_module_init+0x17/0x19 [wl]
[   13.696015]  [<c1003132>] do_one_initcall+0x112/0x160
[   13.696015]  [<c160b085>] ? set_section_ro_nx+0x54/0x59
[   13.696015]  [<c10acc2e>] load_module+0x123e/0x19e0
[   13.696015]  [<c10ad448>] sys_init_module+0x78/0xb0
[   13.696015]  [<c161b24d>] sysenter_do_call+0x12/0x28
[   13.696015] Code: 45 f0 e8 0a 34 71 c7 90 fb 90 8d 74 26 00 89 d8 e8 3c c8 ff ff 89 d8 e8 15 c9 ff ff 89 d8 e8 ce cc ff ff 83 c4 04 5b 5e 5f 5d c3 <0f> 0b 8d 74 26 00 55 89 e5 57 56 53 83 ec 10 3e 8d 74 26 00 8b
[   13.696015] EIP: [<f99299da>] wl_cfg80211_detach+0xca/0xd0 [wl] SS:ESP 0068:f4f03c1c
[   13.697897] ---[ end trace d1d715f222b68e76 ]---
[   14.630437] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   14.633074] r8712u: Staging version
[   14.633145] r8712u: register rtl8712_netdev_ops to netdev_ops
[   14.633195] r8712u: USB_SPEED_HIGH with 4 endpoints
[   14.633832] r8712u: Boot from EFUSE: Autoload OK
[   15.096946] r8712u: CustomerID = 0x0000
[   15.096989] r8712u: MAC Address from efuse = ec:1a:59:b0:d9:e8
[   15.097041] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   15.098695] usbcore: registered new interface driver r8712u
[   15.314113] cfg80211: World regulatory domain updated:
[   15.317040] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.319949] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.322878] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.325709] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.328534] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.331166] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.740876] type=1400 audit(1377135633.230:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=588 comm="apparmor_parser"
[   16.744303] type=1400 audit(1377135633.234:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=596 comm="apparmor_parser"
[   16.747210] type=1400 audit(1377135633.234:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=649 comm="apparmor_parser"
[   16.750619] type=1400 audit(1377135633.238:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=649 comm="apparmor_parser"
[   16.757207] type=1400 audit(1377135633.246:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=588 comm="apparmor_parser"
[   16.762706] type=1400 audit(1377135633.250:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=596 comm="apparmor_parser"
[   16.768823] type=1400 audit(1377135633.258:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=649 comm="apparmor_parser"
[   16.775918] type=1400 audit(1377135633.266:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=588 comm="apparmor_parser"
[   16.782470] type=1400 audit(1377135633.270:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=596 comm="apparmor_parser"
[   18.299523] init: failsafe main process (662) killed by TERM signal
[   20.758703] Bluetooth: Core ver 2.16
[   20.758817] NET: Registered protocol family 31
[   20.758820] Bluetooth: HCI device and connection manager initialized
[   20.760693] Bluetooth: HCI socket layer initialized
[   20.760700] Bluetooth: L2CAP socket layer initialized
[   20.760720] Bluetooth: SCO socket layer initialized
[   21.146942] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.146948] Bluetooth: BNEP filters: protocol multicast
[   21.146963] Bluetooth: BNEP socket layer initialized
[   21.150662] Bluetooth: RFCOMM TTY layer initialized
[   21.150682] Bluetooth: RFCOMM socket layer initialized
[   21.150685] Bluetooth: RFCOMM ver 1.11
[   21.622448] init: avahi-cups-reload main process (755) terminated with status 1
[   21.823802] ppdev: user-space parallel port driver
[   22.355106] type=1400 audit(1377135638.842:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=805 comm="apparmor_parser"
[   22.355863] type=1400 audit(1377135638.842:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=805 comm="apparmor_parser"
[   26.377408] sky2 0000:02:00.0 eth0: enabling interface
[   26.377551] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.378419] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.558926] type=1400 audit(1377135643.046:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=851 comm="apparmor_parser"
[   26.559413] type=1400 audit(1377135643.046:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=851 comm="apparmor_parser"
[   26.659236] type=1400 audit(1377135643.146:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=852 comm="apparmor_parser"
[   26.659811] type=1400 audit(1377135643.146:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=852 comm="apparmor_parser"
[   26.680480] type=1400 audit(1377135643.170:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=853 comm="apparmor_parser"
[   26.680960] type=1400 audit(1377135643.170:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=853 comm="apparmor_parser"
[   26.685548] type=1400 audit(1377135643.174:19): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=854 comm="apparmor_parser"
[   26.686178] type=1400 audit(1377135643.174:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=854 comm="apparmor_parser"
[   27.092462] r8712u: 1 RCR=0x153f00e
[   27.093206] r8712u: 2 RCR=0x553f00e
[   27.200397] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.201010] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.508372] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.416880] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.724392] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   49.198406] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  196.920471] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  197.228381] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  197.536268] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  218.030654] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  411.912936] systemd-hostnamed[2379]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 2076.315370] hid-generic 0003:046D:C52F.0001: can't reset device, 0000:00:1d.7-3.3/input0, status -71
[ 2076.317562] hid-generic 0003:05B8:3155.0003: can't reset device, 0000:00:1d.7-3.4/input0, status -71
[ 2076.319300] usb 1-3: clear tt 3 (0040) error -71
[ 2076.323869] hid-generic 0003:046D:C52F.0002: can't reset device, 0000:00:1d.7-3.3/input1, status -71
[ 2076.324041] usb 1-3: clear tt 4 (0050) error -71
[ 2076.328092] hid-generic 0003:05B8:3155.0004: can't reset device, 0000:00:1d.7-3.4/input1, status -71
[ 2076.328105] usb 1-3: clear tt 3 (0040) error -71
[ 2076.332596] usb 1-3: USB disconnect, device number 3
[ 2076.332602] usb 1-3.3: USB disconnect, device number 4
[ 2076.334831] hid-generic 0003:046D:C52F.0001: can't reset device, 0000:00:1d.7-3.3/input0, status -71
[ 2076.334845] usb 1-3: clear tt 4 (0050) error -71
[ 2076.334851] usb 1-3: clear tt 3 (0040) error -19
[ 2076.338815] hid-generic 0003:046D:C52F.0002: can't reset device, 0000:00:1d.7-3.3/input1, status -71
[ 2076.338830] hid-generic 0003:05B8:3155.0003: can't reset device, 0000:00:1d.7-3.4/input0, status -71
[ 2076.338837] usb 1-3: clear tt 3 (0040) error -19
[ 2076.338841] usb 1-3: clear tt 4 (0050) error -19
[ 2076.339206] usb 1-3.4: USB disconnect, device number 5
[71690.916053] usb 1-3: new high-speed USB device number 6 using ehci-pci
[71691.048396] usb 1-3: New USB device found, idVendor=04b4, idProduct=6560
[71691.048402] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[71691.050569] hub 1-3:1.0: USB hub found
[71691.050622] hub 1-3:1.0: 4 ports detected
[71691.320142] usb 1-3.3: new full-speed USB device number 7 using ehci-pci
[71691.415139] usb 1-3.3: New USB device found, idVendor=046d, idProduct=c52f
[71691.415144] usb 1-3.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[71691.415147] usb 1-3.3: Product: USB Receiver
[71691.415150] usb 1-3.3: Manufacturer: Logitech
[71691.418129] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.0/input/input16
[71691.418263] hid-generic 0003:046D:C52F.0005: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.7-3.3/input0
[71691.421523] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.1/input/input17
[71691.421725] hid-generic 0003:046D:C52F.0006: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.7-3.3/input1
[71691.496147] usb 1-3.4: new low-speed USB device number 8 using ehci-pci
[71691.594379] usb 1-3.4: New USB device found, idVendor=05b8, idProduct=3155
[71691.594386] usb 1-3.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[71691.594389] usb 1-3.4: Product: GE 98134
[71691.594393] usb 1-3.4: Manufacturer: GE 98134
[71691.599031] input: GE 98134 GE 98134 as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4:1.0/input/input18
[71691.599169] hid-generic 0003:05B8:3155.0007: input,hidraw2: USB HID v1.00 Keyboard [GE 98134 GE 98134] on usb-0000:00:1d.7-3.4/input0
[71691.606440] input: GE 98134 GE 98134 as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4:1.1/input/input19
[71691.606835] hid-generic 0003:05B8:3155.0008: input,hiddev0,hidraw3: USB HID v1.00 Mouse [GE 98134 GE 98134] on usb-0000:00:1d.7-3.4/input1
brian@brian-Aspire-3680:~$
```

---

### Post by Crusty Old Fart on 2013-08-22
Excellent. Thank you.
The boy doesn't feel so great. Here's what he's complaining about:
```

[   10.191160] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.957305] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[   10.957315] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.957321] ACPI Warning: 0x000011b0-0x000011bf SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   10.957326] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.957328] ACPI Warning: 0x00001180-0x000011af SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   10.957333] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.250212] acer_wmi: Acer Laptop ACPI-WMI Extras
[   11.250661] acer_wmi: Disabling ACPI video driver
[   12.806219] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.694078] wl driver 6.20.155.1 (r326264) failed with code 21
[   18.299523] init: failsafe main process (662) killed by TERM signal
[  411.912936] systemd-hostnamed[2379]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!

```

Now we can get to work.

Please post the output of the following command:
```

ls -al /etc/default/grub*

```

---

### Post by Redjama on 2013-08-22
```
brian@brian-Aspire-3680:~$ ls -al /etc/default/grub*
-rw-r--r-- 1 root root 1246 Aug 21 06:53 /etc/default/grub
-rw-r--r-- 1 root root 1237 Aug 17 19:28 /etc/default/grub~



```

So its a video driver problem?

---

### Post by Crusty Old Fart on 2013-08-22
> **brian9 said:**
> ...So its a video driver problem?
It certainly involves the video driver, but it could be caused by your BIOS settings conflicting with how the OS wants to manage power.
The first thing we need to do is re-run the dmesg command with the original bootloader and begin working the problem from there.
Let's rename the original grub file. Copy it to a new grub file, update it. Reboot, and then run dmesg again.
Please perform the following:
Become root:
```

sudo su

```
Change the name of grub~ to grub_original:
```

mv /etc/default/grub~ /etc/default/grub_original

```
Remove our modified grub file:
```

rm /etc/default/grub

```
Copy the grub_original file to grub:
```

cp -p /etc/default/grub_original /etc/default/grub

```
Update grub:
```

update-grub

```
Shut down, physically power off, and then boot up the machine.
When it comes back up, post the entire output of the following command into a code box:
```

dmesg

```
This will give us an idea of how the system likes the bootloader that came with the installation, which is the best state for us to begin our diagnosis.

---

### Post by Redjama on 2013-08-22
```
[    1.769150] libphy: Fixed MDIO Bus: probed[    1.769265] tun: Universal TUN/TAP device driver, 1.6
[    1.769267] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.769326] PPP generic driver version 2.4.2
[    1.769378] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.769381] ehci-pci: EHCI PCI platform driver
[    1.769419] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    1.769425] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.769433] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.769452] ehci-pci 0000:00:1d.7: debug port 1
[    1.773368] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    1.773524] ehci-pci 0000:00:1d.7: irq 23, io mem 0xd0644000
[    1.817268] isapnp: No Plug & Play device found
[    1.817280] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.817340] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.817343] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.817347] usb usb1: Product: EHCI Host Controller
[    1.817350] usb usb1: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    1.817353] usb usb1: SerialNumber: 0000:00:1d.7
[    1.817479] hub 1-0:1.0: USB hub found
[    1.817487] hub 1-0:1.0: 8 ports detected
[    1.817677] ehci-platform: EHCI generic platform driver
[    1.817691] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.817714] uhci_hcd: USB Universal Host Controller Interface driver
[    1.817748] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.817753] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.817763] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.817794] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.817839] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.817842] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.817845] usb usb2: Product: UHCI Host Controller
[    1.817849] usb usb2: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.817851] usb usb2: SerialNumber: 0000:00:1d.0
[    1.817973] hub 2-0:1.0: USB hub found
[    1.817979] hub 2-0:1.0: 2 ports detected
[    1.818080] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.818085] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.818092] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.818135] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.818176] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.818180] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.818183] usb usb3: Product: UHCI Host Controller
[    1.818186] usb usb3: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.818189] usb usb3: SerialNumber: 0000:00:1d.1
[    1.818299] hub 3-0:1.0: USB hub found
[    1.818305] hub 3-0:1.0: 2 ports detected
[    1.818402] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.818407] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.818413] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.818456] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.818497] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.818500] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.818504] usb usb4: Product: UHCI Host Controller
[    1.818507] usb usb4: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.818510] usb usb4: SerialNumber: 0000:00:1d.2
[    1.818620] hub 4-0:1.0: USB hub found
[    1.818625] hub 4-0:1.0: 2 ports detected
[    1.818726] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.818731] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.818739] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.818782] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    1.818824] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.818828] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.818831] usb usb5: Product: UHCI Host Controller
[    1.818834] usb usb5: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.818837] usb usb5: SerialNumber: 0000:00:1d.3
[    1.818947] hub 5-0:1.0: USB hub found
[    1.818953] hub 5-0:1.0: 2 ports detected
[    1.819138] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.835263] i8042: Detected active multiplexing controller, rev 1.1
[    1.841264] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.841273] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.841307] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.841335] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.841366] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.841503] mousedev: PS/2 mouse device common for all mice
[    1.841725] rtc_cmos 00:05: RTC can wake from S4
[    1.841887] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.841922] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.842052] device-mapper: uevent: version 1.0.3
[    1.842129] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.842153] EISA: Probing bus 0 at eisa.0
[    1.842161] Cannot allocate resource for EISA slot 1
[    1.842164] Cannot allocate resource for EISA slot 2
[    1.842167] Cannot allocate resource for EISA slot 3
[    1.842169] Cannot allocate resource for EISA slot 4
[    1.842172] Cannot allocate resource for EISA slot 5
[    1.842188] EISA: Detected 0 cards.
[    1.842200] cpufreq-nforce2: No nForce2 chipset.
[    1.842230] cpuidle: using governor ladder
[    1.842266] cpuidle: using governor menu
[    1.842270] ledtrig-cpu: registered to indicate activity on CPUs
[    1.842273] EFI Variables Facility v0.08 2004-May-17
[    1.842489] ashmem: initialized
[    1.842653] TCP: cubic registered
[    1.842794] NET: Registered protocol family 10
[    1.843051] NET: Registered protocol family 17
[    1.843066] Key type dns_resolver registered
[    1.843245] Using IPI No-Shortcut mode
[    1.843342] Loading module verification certificates
[    1.849216] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 3f91e9adadd74ee2134f443ced3a922f70cb07ef'
[    1.849235] registered taskstats version 1
[    1.852514] Key type trusted registered
[    1.855215] Key type encrypted registered
[    1.858476] rtc_cmos 00:05: setting system clock to 2013-08-22 23:10:07 UTC (1377213007)
[    1.858556] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.858558] EDD information not available.
[    1.878093] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.936708] ata2.00: ATAPI: Slimtype DVD C  DS24CZP, PA11, max UDMA/33
[    1.952343] ata2.00: configured for UDMA/33
[    1.988615] ata1.00: ATA-8: ST9250315AS, 0001BSM1, max UDMA/133
[    1.988620] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.004740] ata1.00: configured for UDMA/133
[    2.004882] scsi 0:0:0:0: Direct-Access     ATA      ST9250315AS      0001 PQ: 0 ANSI: 5
[    2.005119] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.005192] sd 0:0:0:0: [sda] Write Protect is off
[    2.005196] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.005228] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.005495] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.007523] scsi 1:0:0:0: CD-ROM            Slimtype DVD C  DS24CZP   PA11 PQ: 0 ANSI: 5
[    2.011475] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
[    2.011479] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.011600] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.011754] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.049253]  sda: sda1 sda2 < sda5 >
[    2.049605] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.049668] Freeing unused kernel memory: 788k freed
[    2.050033] Write protecting the kernel text: 6260k
[    2.050102] Write protecting the kernel read-only data: 2436k
[    2.050104] NX-protecting the kernel data: 3980k
[    2.067654] udevd[94]: starting version 175
[    2.128085] usb 1-2: new high-speed USB device number 2 using ehci-pci
[    2.206324] sky2: driver version 1.30
[    2.206363] sky2 0000:02:00.0: enabling device (0000 -> 0003)
[    2.206414] sky2 0000:02:00.0: Yukon-2 FE chip revision 1
[    2.206532] sky2 0000:02:00.0: irq 43 for MSI/MSI-X
[    2.206852] sky2 0000:02:00.0 eth0: addr 00:1b:24:2b:00:18
[    2.262452] usb 1-2: New USB device found, idVendor=050d, idProduct=945a
[    2.262459] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.262464] usb 1-2: Product: Belkin USB Wireless Adaptor
[    2.262467] usb 1-2: Manufacturer: Manufacturer Realtek 
[    2.262470] usb 1-2: SerialNumber: 00e04c000001
[    2.372048] usb 1-3: new high-speed USB device number 3 using ehci-pci
[    2.491676] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.491682] EXT4-fs (sda1): write access will be enabled during recovery
[    2.504468] usb 1-3: New USB device found, idVendor=04b4, idProduct=6560
[    2.504473] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.504747] hub 1-3:1.0: USB hub found
[    2.504840] hub 1-3:1.0: 4 ports detected
[    2.776231] usb 1-3.1: new high-speed USB device number 4 using ehci-pci
[    2.884470] usb 1-3.1: New USB device found, idVendor=045e, idProduct=076d
[    2.884477] usb 1-3.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.884480] usb 1-3.1: Product: Microsoft\xffffffc2\xffffffae\xffffffae LifeCam HD-5000
[    2.884484] usb 1-3.1: Manufacturer: Microsoft
[    2.956222] usb 1-3.3: new full-speed USB device number 5 using ehci-pci
[    3.051090] usb 1-3.3: New USB device found, idVendor=046d, idProduct=c52f
[    3.051094] usb 1-3.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.051097] usb 1-3.3: Product: USB Receiver
[    3.051101] usb 1-3.3: Manufacturer: Logitech
[    3.099320] usbcore: registered new interface driver usbhid
[    3.099325] usbhid: USB HID core driver
[    3.118603] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.0/input/input5
[    3.118877] hid-generic 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.7-3.3/input0
[    3.124429] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.1/input/input6
[    3.125593] hid-generic 0003:046D:C52F.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.7-3.3/input1
[    3.136225] usb 1-3.4: new low-speed USB device number 6 using ehci-pci
[    3.233837] usb 1-3.4: New USB device found, idVendor=05b8, idProduct=3155
[    3.233842] usb 1-3.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.233845] usb 1-3.4: Product: GE 98134
[    3.233848] usb 1-3.4: Manufacturer: GE 98134
[    3.238320] input: GE 98134 GE 98134 as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4:1.0/input/input7
[    3.238441] hid-generic 0003:05B8:3155.0003: input,hidraw2: USB HID v1.00 Keyboard [GE 98134 GE 98134] on usb-0000:00:1d.7-3.4/input0
[    3.246103] input: GE 98134 GE 98134 as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4:1.1/input/input8
[    3.246569] hid-generic 0003:05B8:3155.0004: input,hiddev0,hidraw3: USB HID v1.00 Mouse [GE 98134 GE 98134] on usb-0000:00:1d.7-3.4/input1
[    4.271619] EXT4-fs (sda1): recovery complete
[    4.281165] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    7.139384] Adding 1561596k swap on /dev/sda5.  Priority:-1 extents:1 across:1561596k 
[    8.002099] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.240298] udevd[341]: starting version 175
[    9.218007] Disabling lock debugging due to kernel taint
[    9.342780] lp: driver loaded but no devices found
[   10.188496] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.723022] intel_rng: FWH not detected
[   10.723498] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.742105] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9
[   10.863361] cfg80211: Calling CRDA to update world regulatory domain
[   10.903177] yenta_cardbus 0000:0a:09.0: CardBus bridge found [1025:0110]
[   10.903207] yenta_cardbus 0000:0a:09.0: Using CSCINT to route CSC interrupts to PCI
[   10.903210] yenta_cardbus 0000:0a:09.0: Routing CardBus interrupts to PCI
[   10.903217] yenta_cardbus 0000:0a:09.0: TI: mfunc 0x01321b22, devctl 0x66
[   11.068187] [drm] Initialized drm 1.1.0 20060810
[   11.093041] lib80211: common routines for IEEE802.11 drivers
[   11.093049] lib80211_crypt: registered algorithm 'NULL'
[   11.131760] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[   11.131771] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.131776] ACPI Warning: 0x000011b0-0x000011bf SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   11.131781] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.131783] ACPI Warning: 0x00001180-0x000011af SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   11.131788] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.131790] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   11.132831] yenta_cardbus 0000:0a:09.0: ISA IRQ mask 0x0cf8, PCI irq 20
[   11.132837] yenta_cardbus 0000:0a:09.0: Socket status: 30000006
[   11.132842] pci_bus 0000:0a: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   11.132851] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge window: [io  0x5000-0x5fff]
[   11.132856] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff:
[   11.134349]  excluding 0x5000-0x50ff 0x5400-0x54ff
[   11.140250] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge window: [mem 0xd0200000-0xd02fffff]
[   11.140256] pcmcia_socket pcmcia_socket0: cs: memory probe 0xd0200000-0xd02fffff:
[   11.140259]  excluding 0xd0200000-0xd020ffff
[   11.140271] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge window: [mem 0x60000000-0x63ffffff pref]
[   11.140275] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x63ffffff:
[   11.140287]  excluding 0x60000000-0x63ffffff
[   11.334207] microcode: CPU0 sig=0x6ec, pf=0x20, revision=0x54
[   11.616767] wmi: Mapper loaded
[   11.750174] leds_ss4200: no LED devices found
[   12.031947] acer_wmi: Acer Laptop ACPI-WMI Extras
[   12.032436] acer_wmi: Function bitmap for Communication Device: 0x27
[   12.032443] acer_wmi: Disabling ACPI video driver
[   12.035761] input: Acer BMA150 accelerometer as /devices/virtual/input/input10
[   12.222090] [drm] 
[   12.222640] [drm] Memory usable by graphics device = 256M
[   12.222651] i915 0000:00:02.0: setting latency timer to 64
[   12.225237] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   12.227760] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   12.227765] [drm] Driver supports precise vblank timestamp query.
[   12.227846] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.236038] [drm] initialized overlay support
[   12.511834] fbcon: inteldrmfb (fb0) is primary device
[   12.668938] Console: switching to colour frame buffer device 128x48
[   12.673128] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   12.673131] i915 0000:00:02.0: registered panic notifier
[   12.673652] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.674968] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input11
[   12.676833] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   12.785097] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af:
[   12.786259]  excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   12.788037] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff:
[   12.788470]  excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   12.788876] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff:
[   12.789541]  clean.
[   12.789561] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
[   12.790296]  clean.
[   12.790319] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[   12.790325]  excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xdc000-0xdffff 0xe4000-0xfffff
[   12.790358] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff:
[   12.790377]  clean.
[   12.790397] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff:
[   12.790409]  excluding 0x60000000-0x60ffffff
[   12.790430] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[   12.791192]  clean.
[   13.206396] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000/0x0, board id: 3655, fw id: 235996
[   13.319222] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input12
[   13.967466] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   14.084272] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.095569] wl 0000:03:00.0: enabling device (0000 -> 0002)
[   14.098182] malloc in abgphy done
[   14.098401] wl driver 6.20.155.1 (r326264) failed with code 21
[   14.098426] ------------[ cut here ]------------
[   14.098477] Kernel BUG at f99f69da [verbose debug info unavailable]
[   14.098530] invalid opcode: 0000 [#1] SMP 
[   14.098578] Modules linked in: wl(POF+) snd_hda_intel(+) snd_hda_codec snd_hwdep(F) snd_pcm(F) joydev(F) snd_page_alloc(F) coretemp snd_seq_midi(F) i915(OF) snd_seq_midi_event(F) acer_wmi snd_rawmidi(F) snd_seq(F) tifm_7xx1 sparse_keymap snd_seq_device(F) wmi tifm_core pcmcia snd_timer(F) microcode(F) drm_kms_helper(OF) psmouse(F) snd(F) lpc_ich lib80211 drm(OF) soundcore(F) yenta_socket mac_hid serio_raw(F) cfg80211 pcmcia_rsrc i2c_algo_bit video(F) pcmcia_core lp(F) parport(F) hid_generic usbhid hid sky2
[   14.099185] Pid: 373, comm: modprobe Tainted: PF          O 3.8.0-29-generic #42-Ubuntu Acer, inc. Aspire 3680     /Prespa1         
[   14.099281] EIP: 0060:[<f99f69da>] EFLAGS: 00010246 CPU: 0
[   14.099370] EIP is at wl_cfg80211_detach+0xca/0xd0 [wl]
[   14.099414] EAX: 00000000 EBX: f43e2090 ECX: f4b66d00 EDX: f43e2090
[   14.099466] ESI: f754a000 EDI: f4b66d00 EBP: f4b39c2c ESP: f4b39c1c
[   14.099518]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   14.099563] CR0: 8005003b CR2: b731f590 CR3: 34b02000 CR4: 000007f0
[   14.099616] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
[   14.099667] DR6: ffff0ff0 DR7: 00000400
[   14.099701] Process modprobe (pid: 373, ti=f4b38000 task=f6cf4010 task.ti=f4b38000)
[   14.099762] Stack:
[   14.099784]  f4b39c24 f43e2090 f754a000 f4b66d00 f4b39c44 f99ef2f3 f43e200c f43e2000
[   14.099893]  f754a000 f4b66800 f4b39cf0 f99f005b c104bc47 c1a02980 00000400 00000096
[   14.100001]  c19e2078 0201826c 0000032c 00000000 00000002 00000000 0000032d 0000032d
[   14.100053] Call Trace:
[   14.100053]  [<f99ef2f3>] wl_free_if.isra.9+0x23/0xb0 [wl]
[   14.100053]  [<f99f005b>] wl_free+0x7b/0x240 [wl]
[   14.100053]  [<c104bc47>] ? console_unlock+0x337/0x480
[   14.100053]  [<f990fe92>] ? wlc_attach+0xf6c/0xfda [wl]
[   14.100053]  [<c160a746>] ? printk+0x4d/0x4f
[   14.100053]  [<f8aff518>] wl_pci_probe+0x4ff/0xfe7 [wl]
[   14.100053]  [<c103ce08>] ? default_spin_lock_flags+0x8/0x10
[   14.100053]  [<c161406d>] ? _raw_spin_lock_irqsave+0x2d/0x40
[   14.100053]  [<c13ed797>] ? __pm_runtime_resume+0x57/0x70
[   14.100053]  [<c1317729>] pci_device_probe+0x79/0xb0
[   14.100053]  [<c13e332c>] driver_probe_device+0x5c/0x1e0
[   14.100053]  [<c1317683>] ? pci_match_device+0xb3/0xc0
[   14.100053]  [<c13e3541>] __driver_attach+0x91/0xa0
[   14.100053]  [<c13e34b0>] ? driver_probe_device+0x1e0/0x1e0
[   14.100053]  [<c13e1b12>] bus_for_each_dev+0x42/0x80
[   14.100053]  [<c13e2eee>] driver_attach+0x1e/0x20
[   14.100053]  [<c13e34b0>] ? driver_probe_device+0x1e0/0x1e0
[   14.100053]  [<c13e2b7f>] bus_add_driver+0x16f/0x250
[   14.100053]  [<c1317520>] ? pci_device_shutdown+0x50/0x50
[   14.100053]  [<c13e3b2a>] driver_register+0x6a/0x160
[   14.100053]  [<f8aff000>] ? 0xf8afefff
[   14.100053]  [<c13168f3>] __pci_register_driver+0x33/0x40
[   14.100053]  [<f8aff017>] wl_module_init+0x17/0x19 [wl]
[   14.100053]  [<c1003132>] do_one_initcall+0x112/0x160
[   14.100053]  [<c160b085>] ? set_section_ro_nx+0x54/0x59
[   14.100053]  [<c10acc2e>] load_module+0x123e/0x19e0
[   14.100053]  [<c10ad448>] sys_init_module+0x78/0xb0
[   14.100053]  [<c161b24d>] sysenter_do_call+0x12/0x28
[   14.100053] Code: 45 f0 e8 0a 64 64 c7 90 fb 90 8d 74 26 00 89 d8 e8 3c c8 ff ff 89 d8 e8 15 c9 ff ff 89 d8 e8 ce cc ff ff 83 c4 04 5b 5e 5f 5d c3 <0f> 0b 8d 74 26 00 55 89 e5 57 56 53 83 ec 10 3e 8d 74 26 00 8b
[   14.100053] EIP: [<f99f69da>] wl_cfg80211_detach+0xca/0xd0 [wl] SS:ESP 0068:f4b39c1c
[   14.117539] ---[ end trace 5b61a3d8ec21e4f6 ]---
[   14.223717] hda_codec: ALC883: SKU not ready 0x411111f0
[   14.236768] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   14.238889] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   14.241236] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   14.440374] Linux video capture interface: v2.00
[   14.632490] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   14.753657] r8712u: Staging version
[   14.755633] r8712u: register rtl8712_netdev_ops to netdev_ops
[   14.757614] r8712u: USB_SPEED_HIGH with 4 endpoints
[   14.760083] r8712u: Boot from EFUSE: Autoload OK
[   15.193333] r8712u: CustomerID = 0x0000
[   15.195225] r8712u: MAC Address from efuse = ec:1a:59:b0:d9:e8
[   15.197121] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   15.200544] usbcore: registered new interface driver r8712u
[   15.752226] 4:3:1: cannot get freq at ep 0x82
[   15.761029] uvcvideo: Found UVC 1.00 device Microsoft\xffffffc2\xffffffae\xffffffae LifeCam HD-5000 (045e:076d)
[   15.764738] usbcore: registered new interface driver snd-usb-audio
[   15.771528] input: Microsoft\xffffffc2\xffffffae\xffffffae LifeCam HD-5000 as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.1/1-3.1:1.0/input/input16
[   15.777213] usbcore: registered new interface driver uvcvideo
[   15.779184] USB Video Class driver (1.1.1)
[   15.972827] cfg80211: World regulatory domain updated:
[   15.974826] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.976885] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.978926] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.980968] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.982977] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.984979] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.380830] type=1400 audit(1377213023.019:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=593 comm="apparmor_parser"
[   17.385364] type=1400 audit(1377213023.023:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=594 comm="apparmor_parser"
[   17.390106] type=1400 audit(1377213023.027:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=668 comm="apparmor_parser"
[   17.400732] type=1400 audit(1377213023.039:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=593 comm="apparmor_parser"
[   17.406483] type=1400 audit(1377213023.043:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=594 comm="apparmor_parser"
[   17.412228] type=1400 audit(1377213023.051:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=668 comm="apparmor_parser"
[   17.418879] type=1400 audit(1377213023.055:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=593 comm="apparmor_parser"
[   17.424875] type=1400 audit(1377213023.063:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=594 comm="apparmor_parser"
[   17.431086] type=1400 audit(1377213023.071:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=668 comm="apparmor_parser"
[   18.853014] init: failsafe main process (681) killed by TERM signal
[   21.213578] Bluetooth: Core ver 2.16
[   21.213699] NET: Registered protocol family 31
[   21.213702] Bluetooth: HCI device and connection manager initialized
[   21.215374] Bluetooth: HCI socket layer initialized
[   21.215382] Bluetooth: L2CAP socket layer initialized
[   21.215396] Bluetooth: SCO socket layer initialized
[   21.369087] Bluetooth: RFCOMM TTY layer initialized
[   21.369106] Bluetooth: RFCOMM socket layer initialized
[   21.369108] Bluetooth: RFCOMM ver 1.11
[   21.555083] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.555090] Bluetooth: BNEP filters: protocol multicast
[   21.555106] Bluetooth: BNEP socket layer initialized
[   21.749220] init: avahi-cups-reload main process (768) terminated with status 1
[   22.077797] ppdev: user-space parallel port driver
[   22.450240] type=1400 audit(1377213028.087:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=793 comm="apparmor_parser"
[   22.450965] type=1400 audit(1377213028.087:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=793 comm="apparmor_parser"
[   26.455913] sky2 0000:02:00.0 eth0: enabling interface
[   26.456354] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.459858] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.754939] type=1400 audit(1377213032.391:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=870 comm="apparmor_parser"
[   26.755577] type=1400 audit(1377213032.391:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=870 comm="apparmor_parser"
[   26.847543] type=1400 audit(1377213032.483:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=871 comm="apparmor_parser"
[   26.848051] type=1400 audit(1377213032.487:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=871 comm="apparmor_parser"
[   26.919583] type=1400 audit(1377213032.559:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=872 comm="apparmor_parser"
[   26.920080] type=1400 audit(1377213032.559:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=872 comm="apparmor_parser"
[   26.924300] type=1400 audit(1377213032.563:19): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=873 comm="apparmor_parser"
[   26.924932] type=1400 audit(1377213032.563:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=873 comm="apparmor_parser"
[   27.172470] r8712u: 1 RCR=0x153f00e
[   27.173213] r8712u: 2 RCR=0x553f00e
[   27.280398] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.281003] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.588393] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.344256] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.652396] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.892358] 4:3:1: cannot get freq at ep 0x82
[   40.892210] 4:3:1: cannot get freq at ep 0x82
[   42.048351] 4:3:1: cannot get freq at ep 0x82
[   43.048351] 4:3:1: cannot get freq at ep 0x82
[   45.827003] cannot submit urb (err = -18)
[   45.827012] cannot submit urb (err = -18)
[   45.827017] cannot submit urb (err = -18)
[   45.827021] cannot submit urb (err = -18)
[   45.827026] cannot submit urb (err = -18)
[   45.827030] cannot submit urb (err = -18)
[   45.827034] cannot submit urb (err = -18)
[   45.827038] cannot submit urb (err = -18)
[   49.145275] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   56.920389] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   57.228391] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   57.536383] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   78.131974] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

Not sure what happened on the reboot.  Now everything is big and I cant change my resolution.  And the screen keeps flickering


****NVM.......cable had come loose....lol

---

### Post by Crusty Old Fart on 2013-08-22
Link to Acer support: [http://us.acer.com/ac/en/US/content/drivers](http://us.acer.com/ac/en/US/content/drivers)

Links to Grub resources:
[LIST]
[*]Grub2: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[*] Grub2/Troubleshooting: [https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)
[/list]
Links to kernel boot parameters:
[LIST]
[*]Large list from O'Reilly (missing reboot parameter): [http://oreilly.com/linux/excerpts/9780596100797/kernel-boot-command-line-parameter-reference.html](http://oreilly.com/linux/excerpts/9780596100797/kernel-boot-command-line-parameter-reference.html) 
[*]Large list from kernel.org (with reboot parameter): [https://www.kernel.org/doc/Documentation/kernel-parameters.txt](https://www.kernel.org/doc/Documentation/kernel-parameters.txt) 
[/LIST]
Links to trouble shooting resources for power off failure:
[LIST]
[*]HOWTO: Fix Linux hang/freeze during reboots and restarts:[http://linux.koolsolutions.com/2009/08/04/howto-fix-linux-hangfreeze-during-reboots-and-restarts/](http://linux.koolsolutions.com/2009/08/04/howto-fix-linux-hangfreeze-during-reboots-and-restarts/)
[/LIST]

---

### Post by Redjama on 2013-08-22
> **Crusty Old Fart said:**
> Link to Acer support: [http://us.acer.com/ac/en/US/content/drivers](http://us.acer.com/ac/en/US/content/drivers)


I have that link already because I needed drivers when I had windows 7 on it.  Did you give the link to me for a reason?? :confused::)

---

### Post by Crusty Old Fart on 2013-08-22
> **brian9 said:**
> ```
[    1.769150]...****NVM.......cable had come loose....lol
Heh heh heh heh heh...We don't need no stinkin' cable :cool:

I suspect that the OS wants to handle ACPI. But it appears that the BIOS may not be letting it. Here's the tip-off:
[code]
[   12.032443] acer_wmi: Disabling ACPI video driver

```
If we can prevent the BIOS from disabling the ACPI function of the video  driver, there's a good possibility that a LOT of the ACPI warnings will  go away.

I'm looking at your manual right now. 
Please answer the following questions:
Have you ever accessed you BIOS settings during POST?
If so, are you comfortably experienced in changing and saving them?

---

### Post by Crusty Old Fart on 2013-08-22
> **brian9 said:**
> I have that link already because I needed drivers when I had windows 7 on it.  Did you give the link to me for a reason?? :confused::)

Not to bust your high or anything, but I created this post mostly as a resource reference for me. I'm looking for documentation for your BIOS, but haven't found it yet. We may end up on the telephone before too much longer so I can talk you through changing a few BIOS settings.

---

### Post by Redjama on 2013-08-22
Im good with bios changes.  Ive flashed a few in my lifetime...lol. I can usually handle what your gonna throw at me.  Im still learning the coding though for linux.

---

### Post by Crusty Old Fart on 2013-08-22
> **brian9 said:**
> Im good with bios changes.  Ive flashed a few in my lifetime...lol. I can usually handle what your gonna throw at me.  Im still learning the coding though for linux.
Oh man! I'm so glad to read that. No problem with linux coding. I don't mind walking you through it.
I know the moderators don't like this much, but we need to get on the phone. Having you upload cellphone pictures of your BIOS screens and then having me post how things should be set up is just way too much BS for the time it takes.

I have my forum account locked down as tight as I can make it for privacy and security reasons. But I just punched a little hole in it so you can send me private messages by sending a friend request to you.

---

### Post by Redjama on 2013-08-22
Just accepted it

---

### Post by Crusty Old Fart on 2013-08-22
Hopefully you got the private message I sent. If so, please reply back to it. Thanks

---

### Post by Crusty Old Fart on 2013-08-22
Look for my message in your forum account. Depending on how you have things set up there, it may not come into the inbox of the email client on your computer.

---

### Post by Crusty Old Fart on 2013-08-22
It looks like we're going to have to do this the hard way. Just in case you're curious about what we're dealing with,
here's a link to the wiki page for Advanced Configuration and Power Interface (ACPI): [https://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](https://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

I like what Linus Torvalds said about it: "a complete design disaster in every way". He's right.

So now, you'll need to be using a different computer to post here so you can describe to me what options are available to you in each successive BIOS screen and I'll tell you which ones to configure.
This ought to be a blast.

---

### Post by Crusty Old Fart on 2013-08-22
On the other hand, maybe it won't be that bad.
If your BIOS has an option in it where you can specify whether or not you're running a Plug and Play (PNP) OS, the setting should be: YES. With this, we're telling the BIOS to let the OS handle power controls.
Also, if there is an option where you can specify the ACPI state, set it to S1.
If you can't find any settings that relate to the type of OS you're using, or the ACPI state. then we'll have to start a conversation about what your BIOS screens are showing you.
I might have a chance of finding a manual for your BIOS that will explain all the available settings if you could tell me the manufacturer and the version of the BIOS.

---

### Post by Redjama on 2013-08-22
[https://docs.google.com/file/d/0Bwysm8N8NIwPTm9WR2VzTUFwZmc/edit?usp=sharing](https://docs.google.com/file/d/0Bwysm8N8NIwPTm9WR2VzTUFwZmc/edit?usp=sharing)
[https://docs.google.com/file/d/0Bwysm8N8NIwPRWNSUXZkRVlwWG8/edit?usp=sharing](https://docs.google.com/file/d/0Bwysm8N8NIwPRWNSUXZkRVlwWG8/edit?usp=sharing)
[https://docs.google.com/file/d/0Bwysm8N8NIwPQXRYNFM1MnRERFE/edit?usp=sharing](https://docs.google.com/file/d/0Bwysm8N8NIwPQXRYNFM1MnRERFE/edit?usp=sharing)
[https://docs.google.com/file/d/0Bwysm8N8NIwPODE4RHAyR2d3ZEk/edit?usp=sharing](https://docs.google.com/file/d/0Bwysm8N8NIwPODE4RHAyR2d3ZEk/edit?usp=sharing)

Those 4 links are pics of my bios.  Take a look. I dont think theres anything in there that will help

---

### Post by Crusty Old Fart on 2013-08-22
> **brian9 said:**
> [https://docs.google.com/file/d/0Bwysm8N8NIwPTm9WR2VzTUFwZmc/edit?usp=sharing](https://docs.google.com/file/d/0Bwysm8N8NIwPTm9WR2VzTUFwZmc/edit?usp=sharing)
[https://docs.google.com/file/d/0Bwysm8N8NIwPRWNSUXZkRVlwWG8/edit?usp=sharing](https://docs.google.com/file/d/0Bwysm8N8NIwPRWNSUXZkRVlwWG8/edit?usp=sharing)
[https://docs.google.com/file/d/0Bwysm8N8NIwPQXRYNFM1MnRERFE/edit?usp=sharing](https://docs.google.com/file/d/0Bwysm8N8NIwPQXRYNFM1MnRERFE/edit?usp=sharing)
[https://docs.google.com/file/d/0Bwysm8N8NIwPODE4RHAyR2d3ZEk/edit?usp=sharing](https://docs.google.com/file/d/0Bwysm8N8NIwPODE4RHAyR2d3ZEk/edit?usp=sharing)

Those 4 links are pics of my bios.  Take a look. I dont think theres anything in there that will help
I think the pictures would help a great deal.
But, my computer has privacy and security protection installed that prevents connections with Google.
You can upload and attach files to your posts, which is the preferred method on this forum, by using the "Adv Reply" link or the "Reply With Quote" link to begin post creation. At the top of the message frame, the third button from the right of the top row of the menu has a paper clip icon. That's the button used to upload and attach files.
Here's an example of a post with attached pictures: [http://ubuntuforums.org/showthread.php?t=2168413&p=12760844#post12760844](http://ubuntuforums.org/showthread.php?t=2168413&p=12760844#post12760844)
And here's an example of a post with attached code files: [http://ubuntuforums.org/showthread.php?t=1616591&p=10355772#post10355772](http://ubuntuforums.org/showthread.php?t=1616591&p=10355772#post10355772)

---

### Post by Redjama on 2013-08-23
Here ya go

---

### Post by Crusty Old Fart on 2013-08-23
> **brian9 said:**
> Here ya go
Now THAT was perfect. You ROCK!
I'll make another post after playing around with a similar BIOS that I have on one of my laptops and studying your manual some more.
This is going to be easier than I thought it would be.
Thank you.

---

### Post by Crusty Old Fart on 2013-08-23
I don't see anything on the **Security** panel or the **Boot** panel that is relevant to our problem, so we can ignore them.

There aren't any configurable settings on the **Information** panel, but there's a lot of information that may help with online searches in the future.

So, in terms of making any meaningful configuration changes, we're limited to the **Main** panel, and there isn't much there. However, just to make sure we don't miss anything while we're looking at the BIOS, we should take a look at what the configuration options are for **Video Memory** and **Power On Display**. So please post the choices that the BIOS makes available for those two items. Pictures aren't necessary, you can just list the available choices for each item, something like:

Power On Display: [Auto|On|Off]

At this point, for reasons I'll explain later, I'd like to know if the **Exit** panel gives you the ability to reload the factory default settings that the BIOS had in it when it shipped.

---

### Post by Redjama on 2013-08-23
Power On Display "auto" & "both
Video Memory "64mb', "128mb" & MAXDVMT
There is an option to load defaults

---

### Post by Crusty Old Fart on 2013-08-23
Thanks. You were right. I don't see anything in the BIOS that we can tweak to fix the problem.
I made a new grub file that we will be testing. It supplies the kernel with ten different values for the reboot parameter. The kernel will try them one at a time. If it finds one that works, your machine will reboot as it should without you having to physically power off. However, and this is important: if it works, it doesn't mean that we are finished because there will be some "throw away" code in it that should be removed. Ultimately, we'll end up with only one value for the reboot parameter. But, in order to determine which one works, I'll be modifying the code and uploading new versions as we go. Rather than manually testing all ten reboot parameter options one at a time, I'll be zeroing in on the one that works by using an elimination technique that is very similar to that of a binary search. Sometimes the file I ask you to test may NOT work. That's not a problem. It let's us know which half of the remaining parameters we can eliminate. We will need to test four different versions of the grub file before we know which value we should use for the reboot parameter.

Before we begin testing grub files, I'd like you to post the output of the following command;
```

[[ acpi_available ]] && echo "ACPI is available" || echo "ACPI is not available"

```

I think we have a very good chance of nailing this problem today.

---

### Post by Redjama on 2013-08-23
```
brian@brian-Aspire-3680:~$ [[ acpi_available ]] && echo "ACPI is available" || echo
ACPI is available
```

---

### Post by Crusty Old Fart on 2013-08-23
That doesn't look right.
It looks like the last part of the command didn't get copied--could have been my fault. I was editing the post right after I put it up.
Please try again.
The command should be:
```

[[ acpi_available ]] && echo "ACPI is available" || echo "ACPI is not available"

```

---

### Post by Redjama on 2013-08-23
same thing

```
brian@brian-Aspire-3680:~$ [[ acpi_available ]] && echo "ACPI is available" || echo "ACPI is not available"
ACPI is available
brian@brian-Aspire-3680:~$ 
```

---

### Post by Crusty Old Fart on 2013-08-23
Good. Thanks for editing that one. We're in good shape.

Sorry for the delay. I had a helluva time getting the file to attach.
Now we'll start with our grub testing.
The first grub file we're going to test is attached right here --> **[attach]245644[/attach]**
Please download it and save it in your home directory.
Then do the following:
Become root:
```

sudo su

```
Copy the new grub file to /etc/default/grub:
```

cp grub_apfcstwekb.txt /etc/default/grub

```
Update grub:
     ```

update-grub

```
End your root session and return to your user input prompt:
```

exit

```
Please post the output from the following commands, one at a time:
```

cat /proc/cmdline

ls -al /etc/default/grub*

ls -al ~ | grep -iE 'grub|sys'

```

---

### Post by Redjama on 2013-08-23
```
brian@brian-Aspire-3680:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=f9dbbb1a-0cba-45cb-9c9d-3d59144ff21e ro quiet splash



```

```
brian@brian-Aspire-3680:~$ ls -al /etc/default/grub*
-rw-r--r-- 1 root root 2230 Aug 23 20:50 /etc/default/grub
-rw-r--r-- 1 root root 1237 Aug 17 19:28 /etc/default/grub_original



```

```
brian@brian-Aspire-3680:~$ ls -al ~ | grep -iE 'grub|sys'
-rw-rw-r--  1 brian brian  2230 Aug 23 20:50 grub_apfcstwekb.txt
-rwx------  1 brian brian   154 Aug 21 18:29 sys_update.sh



```

---

### Post by Crusty Old Fart on 2013-08-23
[color=red][s][color=black]Oops. There's something wrong with my script.
Working on it now.[/color][/s][/color]

Scratch that. It looks okay.

---

### Post by Crusty Old Fart on 2013-08-23
Nothing wrong with the script. The problem was my expectation of what the output of "cat /proc/cmdline" would look like.

The rest of the output was perfect. You did a nice job.

Now we're ready for the first smoke test.
Shut down the machine and physically power off.
Boot it back up.
Instead of the splash screen, you should get a different Grub bootloader  screen that will persist for ten seconds and then it will boot the  selected kernel, which should be the highlighted top line. You can force  the boot to continue without waiting the full ten seconds by hitting  your [Enter] key.
When the machine finishes booting, you should be able to reboot or shutdown without having to physically power off.
If it works, then we'll be able to zero in on the solution. If it  doesn't work, I'll be asking for the output of some more diagnostic  commands to determine if we should reinstall the OS. I've seen output  suggesting a tainted kernel from previous dmesg commands.
Please let me know how it goes.

---

### Post by Redjama on 2013-08-23
This is what it does.  The second pic is blurry but you can see which lines fail.

---

### Post by Crusty Old Fart on 2013-08-23
Please post the output of the following command:
```

cat /proc/cmdline

```
Questions:
Were you able to boot it up and post from it, or are you posting from another computer?
If you're able to use the laptop, did the grub bootloader menu appear and behave as I described in post #87?

---

### Post by Redjama on 2013-08-23
```
brian@brian-Aspire-3680:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=f9dbbb1a-0cba-45cb-9c9d-3d59144ff21e ro reboot=a,p,f,c,s,t,w,e,k,b
```

I had to manually shut it down as normal.  Yes I saw a ton of script during boot

---

### Post by Crusty Old Fart on 2013-08-23
That output looks fine.
The grub bootloader is working like it should. The changes made to it throw a ton of text during boot.

     The next grub file we'll test is attached right here --> **[attach]245652[/attach]**
     Please download it and save it in your home directory.
     Then do the following:
     Become root:
     ```

     sudo su
     
```
     Copy the new grub file to /etc/default/grub:
     ```

     cp grub_apfc.txt /etc/default/grub
     
```
     Run the sys_update file
     ```

     ./sys_update.sh
     
```
     Shut down the machine and physically power off.
Boot it back up and let me know what happens.

---

### Post by Redjama on 2013-08-23
Done

---

### Post by Crusty Old Fart on 2013-08-23
Please post the output of the following commands (one at a time):
```

cat /proc/cmdline

cat dmesg | grep -iE 'kernel|taint|module|disa|warn|fail'

```

Then try to reboot and let me know if you had to physically power off.

Thanks.

---

### Post by Redjama on 2013-08-23
```
root@brian-Aspire-3680:/home/brian# cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=f9dbbb1a-0cba-45cb-9c9d-3d59144ff21e ro reboot=a,p,f,c,s,t,w,e,k,b
```


```
root@brian-Aspire-3680:/home/brian# cat dmesg | grep -iE 'kernel|taint|module|disa|warn|fail'
cat: dmesg: No such file or directory
```

---

### Post by Crusty Old Fart on 2013-08-23
I hosed the second command. I shouldn't have put the "cat" in front of it.
Please post the output to this one:
```

dmesg | grep -iE 'kernel|taint|module|disa|warn|fail'

```

---

### Post by Redjama on 2013-08-23
```
brian@brian-Aspire-3680:~$ dmesg | grep -iE 'kernel|taint|module|disa|warn|fail'[    0.000000] KERNEL supported cpus:[    0.000000] Disabled fast string operations
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=f9dbbb1a-0cba-45cb-9c9d-3d59144ff21e ro reboot=a,p,f,c
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Memory: 1519832k/1563200k available (6257k kernel code, 42912k reserved, 2974k data, 788k init, 649800k highmem)
[    0.000000] virtual kernel memory layout:
[    0.005330] Disabled fast string operations
[    0.083854] ACPI: Added _OSI(Module Device)
[    0.915276] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.915787] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.917097]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.948202] pnp 00:04: disabling [io  0x002e-0x002f] because it overlaps 0000:02:00.0 BAR 2 [io  0x0000-0x00ff]
[    0.948290] pnp 00:04: disabling [io  0x0061] because it overlaps 0000:02:00.0 BAR 2 [io  0x0000-0x00ff]
[    0.948376] pnp 00:04: disabling [io  0x0063] because it overlaps 0000:02:00.0 BAR 2 [io  0x0000-0x00ff]
[    0.948462] pnp 00:04: disabling [io  0x0065] because it overlaps 0000:02:00.0 BAR 2 [io  0x0000-0x00ff]
[    0.948547] pnp 00:04: disabling [io  0x0067] because it overlaps 0000:02:00.0 BAR 2 [io  0x0000-0x00ff]
[    0.948633] pnp 00:04: disabling [io  0x0068-0x006f] because it overlaps 0000:02:00.0 BAR 2 [io  0x0000-0x00ff]
[    0.948719] pnp 00:04: disabling [io  0x0080] because it overlaps 0000:02:00.0 BAR 2 [io  0x0000-0x00ff]
[    0.948804] pnp 00:04: disabling [io  0x0092] because it overlaps 0000:02:00.0 BAR 2 [io  0x0000-0x00ff]
[    0.948889] pnp 00:04: disabling [io  0x00b2-0x00b3] because it overlaps 0000:02:00.0 BAR 2 [io  0x0000-0x00ff]
[    0.950292] PnPBIOS: Disabled by ACPI PNP
[    1.411154] Initialise module verification
[    1.411274] audit: initializing netlink socket (disabled)
[    1.717827] brd: module loaded
[    1.718846] loop: module loaded
[    2.046311] Loading module verification certificates
[    2.234221] Freeing unused kernel memory: 788k freed
[    2.234631] Write protecting the kernel text: 6260k
[    2.234756] Write protecting the kernel read-only data: 2436k
[    2.234815] NX-protecting the kernel data: 3980k
[    9.776595] Disabling lock debugging due to kernel taint
[   11.470127] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[   11.470143] ACPI Warning: 0x000011b0-0x000011bf SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   11.470150] ACPI Warning: 0x00001180-0x000011af SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   12.223885] acer_wmi: Disabling ACPI video driver
[   14.237588] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.251095] wl driver 6.20.155.1 (r326264) failed with code 21
[   14.251180] Kernel BUG at f99b99da [verbose debug info unavailable]
[   14.251282] Modules linked in: wl(POF+) snd_hda_codec_realtek snd_usb_audio(+) videobuf2_core snd_hda_intel videodev snd_hda_codec snd_usbmidi_lib snd_hwdep(F) snd_pcm(F) snd_page_alloc(F) snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) coretemp i915(OF) snd_seq(F) snd_seq_device(F) joydev(F) snd_timer(F) acer_wmi drm_kms_helper(OF) snd(F) pcmcia sparse_keymap lib80211 drm(OF) soundcore(F) wmi cfg80211 microcode(F) yenta_socket tifm_7xx1 i2c_algo_bit pcmcia_rsrc lpc_ich tifm_core mac_hid video(F) psmouse(F) pcmcia_core serio_raw(F) lp(F) parport(F) hid_generic usbhid hid sky2
[   14.251975] Pid: 371, comm: modprobe Tainted: PF          O 3.8.0-29-generic #42-Ubuntu Acer, inc. Aspire 3680     /Prespa1         
[   14.252017]  [<f9b8a017>] wl_module_init+0x17/0x19 [wl]
[   14.252017]  [<c10acc2e>] load_module+0x123e/0x19e0
[   14.252017]  [<c10ad448>] sys_init_module+0x78/0xb0
[   14.439108] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   18.992074] init: failsafe main process (677) killed by TERM signal
brian@brian-Aspire-3680:~$ dmesg | grep -iE 'kernel|taint|module|disa|warn|fail' 



```

---

### Post by Crusty Old Fart on 2013-08-23
See if the machine will reboot without you having to physically power off.
And let me know what happens.
We're almost done for tonight.

---

### Post by Redjama on 2013-08-23
Nope, same thing

---

### Post by Crusty Old Fart on 2013-08-23
Okay. Here's the deal: Output from all the dmesg commands we've been running ever since we first ran it in post #57 have been giving indications of a tainted kernel and several other warnings that have persisted. It suggests to me that we're very unlikely to have any success with your current installation.

My recommendation is to reinstall from scratch.

I expect that even with a new installation, the machine will still fail to power itself off, but at least we may end up with a healthy kernel that we can feed boot parameters to and have them work.

I could try two more versions of the grub file tonight before you reinstall, if you like, or we could bite the bullet and have you reinstall now and see how we do with it tomorrow.

So, what say you, Brian?

By the way, it's been a pleasure working with you on this little project.

Crusty

---

### Post by Crusty Old Fart on 2013-08-23
One thing I forgot to mention: If you're going to reinstall, it might not be a bad idea to load the factory defaults into your BIOS before installing the OS.

---

### Post by Redjama on 2013-08-24
We can trythe 2 other options you have.  I honestly dont feel like reinstalling.

---

### Post by Crusty Old Fart on 2013-08-24
> **Redjama said:**
> We can try the 2 other options you have.  I honestly dont feel like reinstalling.
Okay, but before we do that, it might be a good idea to load the factory default configuration of your BIOS.
What do you think about doing that?

---

### Post by Redjama on 2013-08-24
Factory defaults are already loaded

---

### Post by Crusty Old Fart on 2013-08-24
> **Redjama said:**
> Factory defaults are already loaded
Is that to say we've been running them all along?

The next grub file we'll test is attached right here --> **[attach]245676[/attach]**
     Please download it and save it in your home directory.
     Then do the following:
     Become root:
     ```

     sudo su
     
```
     Copy the new grub file to /etc/default/grub:
     ```

     cp grub_a.txt /etc/default/grub
     
```
     Update grub:
     ```

     update-grub
     
```
     Shut down the machine and physically power off.
     Boot it back up.
     
     See if it will reboot and power off by itself.
     
     When it comes back up,
     please post all the output of the following command:
     ```

     dmesg
     
```
     ... and let me know if you had to physically power off for the last     reboot.

     Thanks

---

### Post by Redjama on 2013-08-24
Yes defaults were already set up.
Had to physically shutdown


```

[    1.655299] loop: module loaded
[    1.655539] ata_piix 0000:00:1f.2: version 2.13
[    1.655560] ata_piix 0000:00:1f.2: MAP [
[    1.655617]  P0 P2 IDE IDE ]
[    1.830117] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.874026] scsi0 : ata_piix
[    1.874202] scsi1 : ata_piix
[    1.874320] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[    1.874385] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[    1.874881] libphy: Fixed MDIO Bus: probed
[    1.875050] tun: Universal TUN/TAP device driver, 1.6
[    1.875110] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.875232] PPP generic driver version 2.4.2
[    1.875343] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.875406] ehci-pci: EHCI PCI platform driver
[    1.875502] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    1.875507] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.875572] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.875669] ehci-pci 0000:00:1d.7: debug port 1
[    1.879648] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    1.879679] ehci-pci 0000:00:1d.7: irq 23, io mem 0xd0644000
[    1.923436] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.923557] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.923621] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.923702] usb usb1: Product: EHCI Host Controller
[    1.923762] usb usb1: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    1.923825] usb usb1: SerialNumber: 0000:00:1d.7
[    1.967537] isapnp: No Plug & Play device found
[    1.967692] hub 1-0:1.0: USB hub found
[    1.967753] hub 1-0:1.0: 8 ports detected
[    1.968019] ehci-platform: EHCI generic platform driver
[    1.968090] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.968174] uhci_hcd: USB Universal Host Controller Interface driver
[    1.968268] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.968273] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.968340] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.968449] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.968553] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.968618] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.968698] usb usb2: Product: UHCI Host Controller
[    1.968757] usb usb2: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.968820] usb usb2: SerialNumber: 0000:00:1d.0
[    1.968999] hub 2-0:1.0: USB hub found
[    1.969060] hub 2-0:1.0: 2 ports detected
[    1.969217] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.969222] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.969286] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.969410] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.969510] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.969574] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.969655] usb usb3: Product: UHCI Host Controller
[    1.969715] usb usb3: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.969778] usb usb3: SerialNumber: 0000:00:1d.1
[    1.969945] hub 3-0:1.0: USB hub found
[    1.970005] hub 3-0:1.0: 2 ports detected
[    1.970158] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.970163] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.970227] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.970347] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.970448] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.970514] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.970594] usb usb4: Product: UHCI Host Controller
[    1.970653] usb usb4: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.970715] usb usb4: SerialNumber: 0000:00:1d.2
[    1.970881] hub 4-0:1.0: USB hub found
[    1.970941] hub 4-0:1.0: 2 ports detected
[    1.971095] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.971100] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.971166] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.971286] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    1.971389] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.971453] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.971533] usb usb5: Product: UHCI Host Controller
[    1.971593] usb usb5: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.971656] usb usb5: SerialNumber: 0000:00:1d.3
[    1.971824] hub 5-0:1.0: USB hub found
[    1.971884] hub 5-0:1.0: 2 ports detected
[    1.972141] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.989573] i8042: Detected active multiplexing controller, rev 1.1
[    1.997182] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.997249] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.997341] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.997426] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.997517] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.997712] mousedev: PS/2 mouse device common for all mice
[    1.997995] rtc_cmos 00:05: RTC can wake from S4
[    1.998210] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.998306] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.998496] device-mapper: uevent: version 1.0.3
[    1.998633] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.998738] EISA: Probing bus 0 at eisa.0
[    1.998803] Cannot allocate resource for EISA slot 1
[    1.998863] Cannot allocate resource for EISA slot 2
[    1.998922] Cannot allocate resource for EISA slot 3
[    1.998982] Cannot allocate resource for EISA slot 4
[    1.999041] Cannot allocate resource for EISA slot 5
[    1.999113] EISA: Detected 0 cards.
[    1.999181] cpufreq-nforce2: No nForce2 chipset.
[    1.999267] cpuidle: using governor ladder
[    1.999358] cpuidle: using governor menu
[    1.999416] ledtrig-cpu: registered to indicate activity on CPUs
[    1.999477] EFI Variables Facility v0.08 2004-May-17
[    1.999752] ashmem: initialized
[    1.999966] TCP: cubic registered
[    2.000188] NET: Registered protocol family 10
[    2.000500] NET: Registered protocol family 17
[    2.000570] Key type dns_resolver registered
[    2.000794] Using IPI No-Shortcut mode
[    2.000943] Loading module verification certificates
[    2.006866] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 3f91e9adadd74ee2134f443ced3a922f70cb07ef'
[    2.006969] registered taskstats version 1
[    2.010244] Key type trusted registered
[    2.013088] Key type encrypted registered
[    2.016404] rtc_cmos 00:05: setting system clock to 2013-08-24 23:54:57 UTC (1377388497)
[    2.016571] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.016632] EDD information not available.
[    2.034317] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.040712] ata2.00: ATAPI: Slimtype DVD C  DS24CZP, PA11, max UDMA/33
[    2.057317] ata2.00: configured for UDMA/33
[    2.089511] ata1.00: ATA-8: ST9250315AS, 0001BSM1, max UDMA/133
[    2.089574] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.104741] ata1.00: configured for UDMA/133
[    2.104940] scsi 0:0:0:0: Direct-Access     ATA      ST9250315AS      0001 PQ: 0 ANSI: 5
[    2.105255] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.105407] sd 0:0:0:0: [sda] Write Protect is off
[    2.105467] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.105509] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.105683] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.107698] scsi 1:0:0:0: CD-ROM            Slimtype DVD C  DS24CZP   PA11 PQ: 0 ANSI: 5
[    2.111653] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
[    2.111717] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.111901] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.112065] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.161233]  sda: sda1 sda2 < sda5 >
[    2.161667] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.161788] Freeing unused kernel memory: 788k freed
[    2.162209] Write protecting the kernel text: 6260k
[    2.162336] Write protecting the kernel read-only data: 2436k
[    2.162396] NX-protecting the kernel data: 3980k
[    2.183635] udevd[94]: starting version 175
[    2.276095] usb 1-2: new high-speed USB device number 2 using ehci-pci
[    2.410548] usb 1-2: New USB device found, idVendor=050d, idProduct=945a
[    2.410619] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.410684] usb 1-2: Product: Belkin USB Wireless Adaptor
[    2.410744] usb 1-2: Manufacturer: Manufacturer Realtek 
[    2.410804] usb 1-2: SerialNumber: 00e04c000001
[    2.416959] sky2: driver version 1.30
[    2.417056] sky2 0000:02:00.0: enabling device (0000 -> 0003)
[    2.417165] sky2 0000:02:00.0: Yukon-2 FE chip revision 1
[    2.417340] sky2 0000:02:00.0: irq 43 for MSI/MSI-X
[    2.417663] sky2 0000:02:00.0 eth0: addr 00:1b:24:2b:00:18
[    2.520063] usb 1-3: new high-speed USB device number 3 using ehci-pci
[    2.652434] usb 1-3: New USB device found, idVendor=04b4, idProduct=6560
[    2.652505] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.652843] hub 1-3:1.0: USB hub found
[    2.653052] hub 1-3:1.0: 4 ports detected
[    2.700568] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.700639] EXT4-fs (sda1): write access will be enabled during recovery
[    2.924198] usb 1-3.1: new high-speed USB device number 4 using ehci-pci
[    3.032429] usb 1-3.1: New USB device found, idVendor=045e, idProduct=076d
[    3.032495] usb 1-3.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.032575] usb 1-3.1: Product: Microsoft\xffffffc2\xffffffae\xffffffae LifeCam HD-5000
[    3.032636] usb 1-3.1: Manufacturer: Microsoft
[    3.104187] usb 1-3.3: new full-speed USB device number 5 using ehci-pci
[    3.199178] usb 1-3.3: New USB device found, idVendor=046d, idProduct=c52f
[    3.199244] usb 1-3.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.199325] usb 1-3.3: Product: USB Receiver
[    3.199383] usb 1-3.3: Manufacturer: Logitech
[    3.245424] usbcore: registered new interface driver usbhid
[    3.245491] usbhid: USB HID core driver
[    3.263953] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.0/input/input5
[    3.264359] hid-generic 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.7-3.3/input0
[    3.268452] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.1/input/input6
[    3.269427] hid-generic 0003:046D:C52F.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.7-3.3/input1
[    3.272173] usb 1-3.4: new low-speed USB device number 6 using ehci-pci
[    3.370057] usb 1-3.4: New USB device found, idVendor=05b8, idProduct=3155
[    3.370129] usb 1-3.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.370210] usb 1-3.4: Product: GE 98134
[    3.370267] usb 1-3.4: Manufacturer: GE 98134
[    3.374784] input: GE 98134 GE 98134 as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4:1.0/input/input7
[    3.374994] hid-generic 0003:05B8:3155.0003: input,hidraw2: USB HID v1.00 Keyboard [GE 98134 GE 98134] on usb-0000:00:1d.7-3.4/input0
[    3.382527] input: GE 98134 GE 98134 as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4:1.1/input/input8
[    3.382962] hid-generic 0003:05B8:3155.0004: input,hiddev0,hidraw3: USB HID v1.00 Mouse [GE 98134 GE 98134] on usb-0000:00:1d.7-3.4/input1
[    3.800284] EXT4-fs (sda1): recovery complete
[    3.809884] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    6.857036] Adding 1561596k swap on /dev/sda5.  Priority:-1 extents:1 across:1561596k 
[    7.784068] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.945052] udevd[344]: starting version 175
[    9.065878] Disabling lock debugging due to kernel taint
[    9.267695] lp: driver loaded but no devices found
[    9.981339] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.309109] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.309260] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9
[   10.634905] wmi: Mapper loaded
[   10.644302] intel_rng: FWH not detected
[   10.834822] cfg80211: Calling CRDA to update world regulatory domain
[   10.903425] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[   10.903438] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.903443] ACPI Warning: 0x000011b0-0x000011bf SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   10.903448] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.903450] ACPI Warning: 0x00001180-0x000011af SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   10.903455] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.903457] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   11.094185] lib80211: common routines for IEEE802.11 drivers
[   11.094193] lib80211_crypt: registered algorithm 'NULL'
[   11.148306] yenta_cardbus 0000:0a:09.0: CardBus bridge found [1025:0110]
[   11.148333] yenta_cardbus 0000:0a:09.0: Using CSCINT to route CSC interrupts to PCI
[   11.148336] yenta_cardbus 0000:0a:09.0: Routing CardBus interrupts to PCI
[   11.148344] yenta_cardbus 0000:0a:09.0: TI: mfunc 0x01321b22, devctl 0x66
[   11.371150] microcode: CPU0 sig=0x6ec, pf=0x20, revision=0x54
[   11.380837] yenta_cardbus 0000:0a:09.0: ISA IRQ mask 0x0cf8, PCI irq 20
[   11.380845] yenta_cardbus 0000:0a:09.0: Socket status: 30000006
[   11.380851] pci_bus 0000:0a: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   11.381811] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge window: [io  0x5000-0x5fff]
[   11.381815] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff:
[   11.383308]  excluding 0x5000-0x50ff 0x5400-0x54ff
[   11.390835] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge window: [mem 0xd0200000-0xd02fffff]
[   11.390839] pcmcia_socket pcmcia_socket0: cs: memory probe 0xd0200000-0xd02fffff:
[   11.390842]  excluding 0xd0200000-0xd020ffff
[   11.390854] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge window: [mem 0x60000000-0x63ffffff pref]
[   11.390858] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x63ffffff:
[   11.390870]  excluding 0x60000000-0x63ffffff
[   11.404083] [drm] Initialized drm 1.1.0 20060810
[   11.421426] leds_ss4200: no LED devices found
[   11.467125] acer_wmi: Acer Laptop ACPI-WMI Extras
[   11.467565] acer_wmi: Function bitmap for Communication Device: 0x27
[   11.467572] acer_wmi: Disabling ACPI video driver
[   11.474929] input: Acer BMA150 accelerometer as /devices/virtual/input/input10
[   12.073428] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   12.291319] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000/0x0, board id: 3655, fw id: 235996
[   12.352759] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
[   12.357866] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af:
[   12.359027]  excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   12.359885] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff:
[   12.360338]  excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   12.360745] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff:
[   12.361408]  clean.
[   12.361428] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
[   12.362167]  clean.
[   12.362191] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[   12.362196]  excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xdc000-0xdffff 0xe4000-0xfffff
[   12.362228] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff:
[   12.362246]  clean.
[   12.362266] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff:
[   12.362278]  excluding 0x60000000-0x60ffffff
[   12.362299] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[   12.363061]  clean.
[   12.434238] [drm] 
[   12.434798] [drm] Memory usable by graphics device = 256M
[   12.434809] i915 0000:00:02.0: setting latency timer to 64
[   12.435974] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   12.435978] [drm] Driver supports precise vblank timestamp query.
[   12.436114] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.444067] [drm] initialized overlay support
[   12.792100] fbcon: inteldrmfb (fb0) is primary device
[   12.923765] Console: switching to colour frame buffer device 160x64
[   12.930449] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   12.930452] i915 0000:00:02.0: registered panic notifier
[   12.930760] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.932093] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input12
[   12.936077] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.008549] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   13.124507] hda_codec: ALC883: SKU not ready 0x411111f0
[   13.148686] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   13.148963] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   13.149211] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   13.339367] Linux video capture interface: v2.00
[   13.416811] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.427436] wl 0000:03:00.0: enabling device (0000 -> 0002)
[   13.430191] malloc in abgphy done
[   13.430412] wl driver 6.20.155.1 (r326264) failed with code 21
[   13.430440] ------------[ cut here ]------------
[   13.430492] Kernel BUG at f99b99da [verbose debug info unavailable]
[   13.430545] invalid opcode: 0000 [#1] SMP 
[   13.430593] Modules linked in: wl(POF+) videodev snd_usbmidi_lib snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep(F) snd_pcm(F) coretemp i915(OF) snd_page_alloc(F) snd_seq_midi(F) joydev(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) tifm_7xx1 snd_seq_device(F) drm_kms_helper(OF) acer_wmi pcmcia tifm_core drm(OF) snd_timer(F) microcode(F) psmouse(F) snd(F) yenta_socket sparse_keymap lib80211 soundcore(F) pcmcia_rsrc i2c_algo_bit lpc_ich serio_raw(F) cfg80211 pcmcia_core wmi mac_hid video(F) lp(F) parport(F) hid_generic usbhid hid sky2
[   13.431249] Pid: 397, comm: modprobe Tainted: PF          O 3.8.0-29-generic #42-Ubuntu Acer, inc. Aspire 3680     /Prespa1         
[   13.431346] EIP: 0060:[<f99b99da>] EFLAGS: 00010246 CPU: 0
[   13.431439] EIP is at wl_cfg80211_detach+0xca/0xd0 [wl]
[   13.431484] EAX: 00000000 EBX: f4711490 ECX: f4fb5d00 EDX: f4711490
[   13.431536] ESI: f754a000 EDI: f4fb5d00 EBP: f4f4fc2c ESP: f4f4fc1c
[   13.431588]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   13.431633] CR0: 8005003b CR2: b735a000 CR3: 34f91000 CR4: 000007f0
[   13.431685] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
[   13.431737] DR6: ffff0ff0 DR7: 00000400
[   13.431771] Process modprobe (pid: 397, ti=f4f4e000 task=f77c4010 task.ti=f4f4e000)
[   13.431832] Stack:
[   13.431853]  f4f4fc24 f4711490 f754a000 f4fb5d00 f4f4fc44 f99b22f3 f471140c f4711400
[   13.431963]  f754a000 f4fb5800 f4f4fcf0 f99b305b c104bc47 c1a02980 00000400 00000096
[   13.432064]  c19e2078 0201826c 00000331 00000000 00000002 00000000 00000332 00000332
[   13.432064] Call Trace:
[   13.432064]  [<f99b22f3>] wl_free_if.isra.9+0x23/0xb0 [wl]
[   13.432064]  [<f99b305b>] wl_free+0x7b/0x240 [wl]
[   13.432064]  [<c104bc47>] ? console_unlock+0x337/0x480
[   13.432064]  [<f98d2e92>] ? wlc_attach+0xf6c/0xfda [wl]
[   13.432064]  [<c160a746>] ? printk+0x4d/0x4f
[   13.432064]  [<f8c50518>] wl_pci_probe+0x4ff/0xfe7 [wl]
[   13.432064]  [<c103ce08>] ? default_spin_lock_flags+0x8/0x10
[   13.432064]  [<c161406d>] ? _raw_spin_lock_irqsave+0x2d/0x40
[   13.432064]  [<c13ed797>] ? __pm_runtime_resume+0x57/0x70
[   13.432064]  [<c1317729>] pci_device_probe+0x79/0xb0
[   13.432064]  [<c13e332c>] driver_probe_device+0x5c/0x1e0
[   13.432064]  [<c1317683>] ? pci_match_device+0xb3/0xc0
[   13.432064]  [<c13e3541>] __driver_attach+0x91/0xa0
[   13.432064]  [<c13e34b0>] ? driver_probe_device+0x1e0/0x1e0
[   13.432064]  [<c13e1b12>] bus_for_each_dev+0x42/0x80
[   13.432064]  [<c13e2eee>] driver_attach+0x1e/0x20
[   13.432064]  [<c13e34b0>] ? driver_probe_device+0x1e0/0x1e0
[   13.432064]  [<c13e2b7f>] bus_add_driver+0x16f/0x250
[   13.432064]  [<c1317520>] ? pci_device_shutdown+0x50/0x50
[   13.432064]  [<c13e3b2a>] driver_register+0x6a/0x160
[   13.432064]  [<f8c50000>] ? 0xf8c4ffff
[   13.432064]  [<c13168f3>] __pci_register_driver+0x33/0x40
[   13.432064]  [<f8c50017>] wl_module_init+0x17/0x19 [wl]
[   13.432064]  [<c1003132>] do_one_initcall+0x112/0x160
[   13.432064]  [<c160b085>] ? set_section_ro_nx+0x54/0x59
[   13.432064]  [<c10acc2e>] load_module+0x123e/0x19e0
[   13.432064]  [<c10ad448>] sys_init_module+0x78/0xb0
[   13.432064]  [<c161b24d>] sysenter_do_call+0x12/0x28
[   13.432064] Code: 45 f0 e8 0a 34 68 c7 90 fb 90 8d 74 26 00 89 d8 e8 3c c8 ff ff 89 d8 e8 15 c9 ff ff 89 d8 e8 ce cc ff ff 83 c4 04 5b 5e 5f 5d c3 <0f> 0b 8d 74 26 00 55 89 e5 57 56 53 83 ec 10 3e 8d 74 26 00 8b
[   13.432064] EIP: [<f99b99da>] wl_cfg80211_detach+0xca/0xd0 [wl] SS:ESP 0068:f4f4fc1c
[   13.474234] ---[ end trace 436ecc21fbb4de0c ]---
[   13.783478] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   13.789053] r8712u: Staging version
[   13.792136] r8712u: register rtl8712_netdev_ops to netdev_ops
[   13.795130] r8712u: USB_SPEED_HIGH with 4 endpoints
[   13.798671] r8712u: Boot from EFUSE: Autoload OK
[   14.222924] r8712u: CustomerID = 0x0000
[   14.225873] r8712u: MAC Address from efuse = ec:1a:59:b0:d9:e8
[   14.228817] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   14.233381] usbcore: registered new interface driver r8712u
[   14.716316] 4:3:1: cannot get freq at ep 0x82
[   14.726096] uvcvideo: Found UVC 1.00 device Microsoft\xffffffc2\xffffffae\xffffffae LifeCam HD-5000 (045e:076d)
[   14.730587] usbcore: registered new interface driver snd-usb-audio
[   14.737701] input: Microsoft\xffffffc2\xffffffae\xffffffae LifeCam HD-5000 as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.1/1-3.1:1.0/input/input16
[   14.745247] usbcore: registered new interface driver uvcvideo
[   14.748137] USB Video Class driver (1.1.1)
[   15.369478] cfg80211: World regulatory domain updated:
[   15.369537] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.369604] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.369671] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.369737] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.369803] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.369870] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.592872] type=1400 audit(1377388512.074:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=598 comm="apparmor_parser"
[   16.593598] type=1400 audit(1377388512.074:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=598 comm="apparmor_parser"
[   16.594064] type=1400 audit(1377388512.074:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=598 comm="apparmor_parser"
[   16.595008] type=1400 audit(1377388512.074:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=603 comm="apparmor_parser"
[   16.595717] type=1400 audit(1377388512.074:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=603 comm="apparmor_parser"
[   16.596360] type=1400 audit(1377388512.078:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=669 comm="apparmor_parser"
[   16.597055] type=1400 audit(1377388512.078:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=669 comm="apparmor_parser"
[   16.597509] type=1400 audit(1377388512.078:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=669 comm="apparmor_parser"
[   16.598310] type=1400 audit(1377388512.078:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=603 comm="apparmor_parser"
[   17.769353] init: failsafe main process (682) killed by TERM signal
[   19.157451] type=1400 audit(1377388514.638:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=757 comm="apparmor_parser"
[   20.009214] Bluetooth: Core ver 2.16
[   20.009326] NET: Registered protocol family 31
[   20.009329] Bluetooth: HCI device and connection manager initialized
[   20.010920] Bluetooth: HCI socket layer initialized
[   20.010929] Bluetooth: L2CAP socket layer initialized
[   20.010942] Bluetooth: SCO socket layer initialized
[   20.161762] Bluetooth: RFCOMM TTY layer initialized
[   20.161785] Bluetooth: RFCOMM socket layer initialized
[   20.161787] Bluetooth: RFCOMM ver 1.11
[   20.305784] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.305791] Bluetooth: BNEP filters: protocol multicast
[   20.305807] Bluetooth: BNEP socket layer initialized
[   20.640559] init: avahi-cups-reload main process (837) terminated with status 1
[   20.942428] ppdev: user-space parallel port driver
[   21.609341] audit_printk_skb: 48 callbacks suppressed
[   21.609347] type=1400 audit(1377388517.090:28): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=859 comm="apparmor_parser"
[   21.611181] type=1400 audit(1377388517.090:29): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=859 comm="apparmor_parser"
[   21.612755] type=1400 audit(1377388517.094:30): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*//pxgsettings" pid=859 comm="apparmor_parser"
[   21.613609] type=1400 audit(1377388517.094:31): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*//sanitized_helper" pid=859 comm="apparmor_parser"
[   21.619284] type=1400 audit(1377388517.098:32): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=864 comm="apparmor_parser"
[   21.620057] type=1400 audit(1377388517.102:33): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=864 comm="apparmor_parser"
[   21.930847] type=1400 audit(1377388517.410:34): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=866 comm="apparmor_parser"
[   27.836092] sky2 0000:02:00.0 eth0: enabling interface
[   27.836236] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.837080] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.552560] r8712u: 1 RCR=0x153f00e
[   28.553304] r8712u: 2 RCR=0x553f00e
[   28.660362] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.660979] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.968336] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.628351] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.936362] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.016303] 4:3:1: cannot get freq at ep 0x82
[   39.016315] 4:3:1: cannot get freq at ep 0x82
[   40.156305] 4:3:1: cannot get freq at ep 0x82
[   41.156316] 4:3:1: cannot get freq at ep 0x82
[   44.828517] cannot submit urb (err = -18)
[   44.828525] cannot submit urb (err = -18)
[   44.828530] cannot submit urb (err = -18)
[   44.828534] cannot submit urb (err = -18)
[   44.828538] cannot submit urb (err = -18)
[   44.828542] cannot submit urb (err = -18)
[   44.828546] cannot submit urb (err = -18)
[   44.828550] cannot submit urb (err = -18)
[   50.472352] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready



```

---

### Post by Crusty Old Fart on 2013-08-24
> **Redjama said:**
> Yes defaults were already set up.
Oh, good.
> **Redjama said:**
> Had to physically shutdown
Bummer.

Here's the next test. The steps are very similar to the last test.
     
     The next grub file we'll test is attached right here --> **[attach]245680[/attach]**
     Please download it and save it in your home directory.
     Then do the following:
     Become root:
     ```

     sudo su
     
```
     Copy the new grub file to /etc/default/grub:
     ```

     cp grub_p.txt /etc/default/grub
     
```
     Update grub:
     ```

     update-grub
     
```
     Shut down the machine and physically power off.
     Boot it back up.
     
     See if it will reboot and power off by itself.
     
     When it comes back up,
     please post all the output of the following command:
     ```

     dmesg
     
```
     ... and let me know if you had to physically power off for the last     reboot.

While you're working on this, I'll be preparing the next test for quick posting.

     Thanks

---

### Post by Redjama on 2013-08-24
Still had to shut down manually

```
[    1.471123] ACPI: Battery Slot [BAT1] (battery absent)[    1.471219] isapnp: Scanning for PnP cards...
[    1.476815] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.478724] brd: module loaded
[    1.523304] loop: module loaded
[    1.523540] ata_piix 0000:00:1f.2: version 2.13
[    1.523559] ata_piix 0000:00:1f.2: MAP [
[    1.523617]  P0 P2 IDE IDE ]
[    1.698069] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.741972] scsi0 : ata_piix
[    1.742149] scsi1 : ata_piix
[    1.742268] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[    1.742333] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[    1.742830] libphy: Fixed MDIO Bus: probed
[    1.743001] tun: Universal TUN/TAP device driver, 1.6
[    1.743061] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.743182] PPP generic driver version 2.4.2
[    1.743291] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.743354] ehci-pci: EHCI PCI platform driver
[    1.743450] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    1.743455] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.743521] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.743620] ehci-pci 0000:00:1d.7: debug port 1
[    1.747577] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    1.747609] ehci-pci 0000:00:1d.7: irq 23, io mem 0xd0644000
[    1.791350] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.791468] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.791533] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.791613] usb usb1: Product: EHCI Host Controller
[    1.791673] usb usb1: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    1.791736] usb usb1: SerialNumber: 0000:00:1d.7
[    1.791919] hub 1-0:1.0: USB hub found
[    1.791980] hub 1-0:1.0: 8 ports detected
[    1.792248] ehci-platform: EHCI generic platform driver
[    1.792320] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.792404] uhci_hcd: USB Universal Host Controller Interface driver
[    1.792496] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.792501] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.792567] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.792677] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.792780] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.792844] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.792925] usb usb2: Product: UHCI Host Controller
[    1.792985] usb usb2: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.793048] usb usb2: SerialNumber: 0000:00:1d.0
[    1.793224] hub 2-0:1.0: USB hub found
[    1.793284] hub 2-0:1.0: 2 ports detected
[    1.793441] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.793446] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.793509] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.793629] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.793729] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.793793] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.793872] usb usb3: Product: UHCI Host Controller
[    1.793931] usb usb3: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.793993] usb usb3: SerialNumber: 0000:00:1d.1
[    1.794157] hub 3-0:1.0: USB hub found
[    1.794217] hub 3-0:1.0: 2 ports detected
[    1.794369] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.794374] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.794437] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.794557] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.794656] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.794720] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.794800] usb usb4: Product: UHCI Host Controller
[    1.794860] usb usb4: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.794923] usb usb4: SerialNumber: 0000:00:1d.2
[    1.838593] isapnp: No Plug & Play device found
[    1.838734] hub 4-0:1.0: USB hub found
[    1.838794] hub 4-0:1.0: 2 ports detected
[    1.838948] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.838953] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.839020] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.839141] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    1.839242] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.839307] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.839387] usb usb5: Product: UHCI Host Controller
[    1.839447] usb usb5: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.839509] usb usb5: SerialNumber: 0000:00:1d.3
[    1.839676] hub 5-0:1.0: USB hub found
[    1.839737] hub 5-0:1.0: 2 ports detected
[    1.839977] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.855857] i8042: Detected active multiplexing controller, rev 1.1
[    1.863311] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.863377] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.863468] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.863553] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.863642] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.863837] mousedev: PS/2 mouse device common for all mice
[    1.864139] rtc_cmos 00:05: RTC can wake from S4
[    1.864354] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.864449] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.864638] device-mapper: uevent: version 1.0.3
[    1.864774] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.864878] EISA: Probing bus 0 at eisa.0
[    1.864941] Cannot allocate resource for EISA slot 1
[    1.865000] Cannot allocate resource for EISA slot 2
[    1.865058] Cannot allocate resource for EISA slot 3
[    1.865117] Cannot allocate resource for EISA slot 4
[    1.865175] Cannot allocate resource for EISA slot 5
[    1.865248] EISA: Detected 0 cards.
[    1.865313] cpufreq-nforce2: No nForce2 chipset.
[    1.865398] cpuidle: using governor ladder
[    1.865489] cpuidle: using governor menu
[    1.865548] ledtrig-cpu: registered to indicate activity on CPUs
[    1.865609] EFI Variables Facility v0.08 2004-May-17
[    1.865879] ashmem: initialized
[    1.866090] TCP: cubic registered
[    1.866287] NET: Registered protocol family 10
[    1.866596] NET: Registered protocol family 17
[    1.866670] Key type dns_resolver registered
[    1.866892] Using IPI No-Shortcut mode
[    1.867042] Loading module verification certificates
[    1.872973] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 3f91e9adadd74ee2134f443ced3a922f70cb07ef'
[    1.873072] registered taskstats version 1
[    1.876376] Key type trusted registered
[    1.879149] Key type encrypted registered
[    1.882428] rtc_cmos 00:05: setting system clock to 2013-08-25 01:42:03 UTC (1377394923)
[    1.882589] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.882651] EDD information not available.
[    1.908716] ata2.00: ATAPI: Slimtype DVD C  DS24CZP, PA11, max UDMA/33
[    1.924338] ata2.00: configured for UDMA/33
[    1.951545] ata1.00: ATA-8: ST9250315AS, 0001BSM1, max UDMA/133
[    1.951607] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.956716] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.964725] ata1.00: configured for UDMA/133
[    1.964919] scsi 0:0:0:0: Direct-Access     ATA      ST9250315AS      0001 PQ: 0 ANSI: 5
[    1.965225] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.965375] sd 0:0:0:0: [sda] Write Protect is off
[    1.965436] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.965468] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.965640] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.967963] scsi 1:0:0:0: CD-ROM            Slimtype DVD C  DS24CZP   PA11 PQ: 0 ANSI: 5
[    1.971931] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
[    1.971995] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.972185] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.972336] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.022549]  sda: sda1 sda2 < sda5 >
[    2.022968] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.023089] Freeing unused kernel memory: 788k freed
[    2.023511] Write protecting the kernel text: 6260k
[    2.023659] Write protecting the kernel read-only data: 2436k
[    2.023720] NX-protecting the kernel data: 3980k
[    2.043423] udevd[94]: starting version 175
[    2.141775] usb 1-2: new high-speed USB device number 2 using ehci-pci
[    2.228336] sky2: driver version 1.30
[    2.228435] sky2 0000:02:00.0: enabling device (0000 -> 0003)
[    2.228546] sky2 0000:02:00.0: Yukon-2 FE chip revision 1
[    2.228722] sky2 0000:02:00.0: irq 43 for MSI/MSI-X
[    2.229038] sky2 0000:02:00.0 eth0: addr 00:1b:24:2b:00:18
[    2.274474] usb 1-2: New USB device found, idVendor=050d, idProduct=945a
[    2.274545] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.274612] usb 1-2: Product: Belkin USB Wireless Adaptor
[    2.274673] usb 1-2: Manufacturer: Manufacturer Realtek 
[    2.274733] usb 1-2: SerialNumber: 00e04c000001
[    2.384087] usb 1-3: new high-speed USB device number 3 using ehci-pci
[    2.516355] usb 1-3: New USB device found, idVendor=04b4, idProduct=6560
[    2.516428] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.516772] hub 1-3:1.0: USB hub found
[    2.516984] hub 1-3:1.0: 4 ports detected
[    2.572889] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.572962] EXT4-fs (sda1): write access will be enabled during recovery
[    2.788273] usb 1-3.1: new high-speed USB device number 4 using ehci-pci
[    2.896490] usb 1-3.1: New USB device found, idVendor=045e, idProduct=076d
[    2.896561] usb 1-3.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.896642] usb 1-3.1: Product: Microsoft\xffffffc2\xffffffae\xffffffae LifeCam HD-5000
[    2.896702] usb 1-3.1: Manufacturer: Microsoft
[    2.968118] usb 1-3.3: new full-speed USB device number 5 using ehci-pci
[    3.063235] usb 1-3.3: New USB device found, idVendor=046d, idProduct=c52f
[    3.063301] usb 1-3.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.063383] usb 1-3.3: Product: USB Receiver
[    3.063441] usb 1-3.3: Manufacturer: Logitech
[    3.111088] usbcore: registered new interface driver usbhid
[    3.111154] usbhid: USB HID core driver
[    3.130319] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.0/input/input5
[    3.130686] hid-generic 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.7-3.3/input0
[    3.135546] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.1/input/input6
[    3.136524] hid-generic 0003:046D:C52F.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.7-3.3/input1
[    3.140099] usb 1-3.4: new low-speed USB device number 6 using ehci-pci
[    3.237986] usb 1-3.4: New USB device found, idVendor=05b8, idProduct=3155
[    3.238053] usb 1-3.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.238134] usb 1-3.4: Product: GE 98134
[    3.238191] usb 1-3.4: Manufacturer: GE 98134
[    3.242714] input: GE 98134 GE 98134 as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4:1.0/input/input7
[    3.242928] hid-generic 0003:05B8:3155.0003: input,hidraw2: USB HID v1.00 Keyboard [GE 98134 GE 98134] on usb-0000:00:1d.7-3.4/input0
[    3.250205] input: GE 98134 GE 98134 as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4:1.1/input/input8
[    3.250667] hid-generic 0003:05B8:3155.0004: input,hiddev0,hidraw3: USB HID v1.00 Mouse [GE 98134 GE 98134] on usb-0000:00:1d.7-3.4/input1
[    4.090817] EXT4-fs (sda1): recovery complete
[    4.100391] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    7.167708] Adding 1561596k swap on /dev/sda5.  Priority:-1 extents:1 across:1561596k 
[    8.019420] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.268739] udevd[341]: starting version 175
[    9.301367] Disabling lock debugging due to kernel taint
[    9.514147] lp: driver loaded but no devices found
[   10.394709] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.618652] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.631361] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9
[   10.749122] wmi: Mapper loaded
[   11.077729] cfg80211: Calling CRDA to update world regulatory domain
[   11.101468] intel_rng: FWH not detected
[   11.250422] [drm] Initialized drm 1.1.0 20060810
[   11.263507] lib80211: common routines for IEEE802.11 drivers
[   11.263513] lib80211_crypt: registered algorithm 'NULL'
[   11.489652] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[   11.489663] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.489668] ACPI Warning: 0x000011b0-0x000011bf SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   11.489673] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.489676] ACPI Warning: 0x00001180-0x000011af SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   11.489680] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.489682] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   11.767240] yenta_cardbus 0000:0a:09.0: CardBus bridge found [1025:0110]
[   11.767269] yenta_cardbus 0000:0a:09.0: Using CSCINT to route CSC interrupts to PCI
[   11.767272] yenta_cardbus 0000:0a:09.0: Routing CardBus interrupts to PCI
[   11.767279] yenta_cardbus 0000:0a:09.0: TI: mfunc 0x01321b22, devctl 0x66
[   12.000833] yenta_cardbus 0000:0a:09.0: ISA IRQ mask 0x0cf8, PCI irq 20
[   12.000841] yenta_cardbus 0000:0a:09.0: Socket status: 30000006
[   12.000848] pci_bus 0000:0a: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   12.000859] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge window: [io  0x5000-0x5fff]
[   12.000863] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff:
[   12.002356]  excluding 0x5000-0x50ff 0x5400-0x54ff
[   12.007648] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge window: [mem 0xd0200000-0xd02fffff]
[   12.007652] pcmcia_socket pcmcia_socket0: cs: memory probe 0xd0200000-0xd02fffff:
[   12.007656]  excluding 0xd0200000-0xd020ffff
[   12.007667] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge window: [mem 0x60000000-0x63ffffff pref]
[   12.007671] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x63ffffff:
[   12.007684]  excluding 0x60000000-0x63ffffff
[   12.023135] microcode: CPU0 sig=0x6ec, pf=0x20, revision=0x54
[   12.085947] leds_ss4200: no LED devices found
[   12.363652] acer_wmi: Acer Laptop ACPI-WMI Extras
[   12.364144] acer_wmi: Function bitmap for Communication Device: 0x27
[   12.364152] acer_wmi: Disabling ACPI video driver
[   12.367202] input: Acer BMA150 accelerometer as /devices/virtual/input/input10
[   12.548638] [drm] 
[   12.551676] [drm] Memory usable by graphics device = 256M
[   12.551685] i915 0000:00:02.0: setting latency timer to 64
[   12.552857] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   12.552861] [drm] Driver supports precise vblank timestamp query.
[   12.552938] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.560035] [drm] initialized overlay support
[   12.808459] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000/0x0, board id: 3655, fw id: 235996
[   12.851667] fbcon: inteldrmfb (fb0) is primary device
[   12.901519] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af:
[   12.903529]  excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   12.903553] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff:
[   12.904199] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
[   12.906694]  excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   12.906738] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff:
[   12.907410]  clean.
[   12.907429] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
[   12.908238]  clean.
[   12.908267] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[   12.908283]  excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xdc000-0xdffff 0xe4000-0xfffff
[   12.908302] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff:
[   12.908319]  clean.
[   12.908337] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff:
[   12.908350]  excluding 0x60000000-0x60ffffff
[   12.908368] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[   12.909129]  clean.
[   12.947778] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   12.963479] Console: switching to colour frame buffer device 160x64
[   12.969973] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   12.969976] i915 0000:00:02.0: registered panic notifier
[   12.970282] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.977963] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input12
[   12.978790] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.707374] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.720236] wl 0000:03:00.0: enabling device (0000 -> 0002)
[   13.722821] malloc in abgphy done
[   13.723041] wl driver 6.20.155.1 (r326264) failed with code 21
[   13.723068] ------------[ cut here ]------------
[   13.723119] Kernel BUG at f98f69da [verbose debug info unavailable]
[   13.723171] invalid opcode: 0000 [#1] SMP 
[   13.723220] Modules linked in: wl(POF+) snd_hda_codec snd_hwdep(F) coretemp snd_pcm(F) snd_page_alloc(F) joydev(F) snd_seq_midi(F) i915(OF) snd_seq_midi_event(F) tifm_7xx1 acer_wmi snd_rawmidi(F) snd_seq(F) pcmcia tifm_core sparse_keymap snd_seq_device(F) microcode(F) yenta_socket snd_timer(F) psmouse(F) pcmcia_rsrc lpc_ich drm_kms_helper(OF) pcmcia_core serio_raw(F) lib80211 drm(OF) snd(F) soundcore(F) cfg80211 i2c_algo_bit wmi mac_hid video(F) lp(F) parport(F) hid_generic usbhid hid sky2
[   13.723803] Pid: 386, comm: modprobe Tainted: PF          O 3.8.0-29-generic #42-Ubuntu Acer, inc. Aspire 3680     /Prespa1         
[   13.723901] EIP: 0060:[<f98f69da>] EFLAGS: 00010246 CPU: 0
[   13.723994] EIP is at wl_cfg80211_detach+0xca/0xd0 [wl]
[   13.724015] EAX: 00000000 EBX: f4e77c90 ECX: f47f1d00 EDX: f4e77c90
[   13.724015] ESI: f754a000 EDI: f47f1d00 EBP: f4f7bc2c ESP: f4f7bc1c
[   13.724015]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   13.724015] CR0: 8005003b CR2: b8356054 CR3: 34f43000 CR4: 000007f0
[   13.724015] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
[   13.724015] DR6: ffff0ff0 DR7: 00000400
[   13.724015] Process modprobe (pid: 386, ti=f4f7a000 task=f6d43340 task.ti=f4f7a000)
[   13.724015] Stack:
[   13.724015]  f4f7bc24 f4e77c90 f754a000 f47f1d00 f4f7bc44 f98ef2f3 f4e77c0c f4e77c00
[   13.724015]  f754a000 f47f1800 f4f7bcf0 f98f005b c104bc47 c1a02980 00000400 00000096
[   13.724015]  c19e2078 0201826c 0000032b 00000000 00000002 00000000 0000032c 0000032c
[   13.724015] Call Trace:
[   13.724015]  [<f98ef2f3>] wl_free_if.isra.9+0x23/0xb0 [wl]
[   13.724015]  [<f98f005b>] wl_free+0x7b/0x240 [wl]
[   13.724015]  [<c104bc47>] ? console_unlock+0x337/0x480
[   13.724015]  [<f980fe92>] ? wlc_attach+0xf6c/0xfda [wl]
[   13.724015]  [<c160a746>] ? printk+0x4d/0x4f
[   13.724015]  [<f9ac7518>] wl_pci_probe+0x4ff/0xfe7 [wl]
[   13.724015]  [<c103ce08>] ? default_spin_lock_flags+0x8/0x10
[   13.724015]  [<c161406d>] ? _raw_spin_lock_irqsave+0x2d/0x40
[   13.724015]  [<c13ed797>] ? __pm_runtime_resume+0x57/0x70
[   13.724015]  [<c1317729>] pci_device_probe+0x79/0xb0
[   13.724015]  [<c13e332c>] driver_probe_device+0x5c/0x1e0
[   13.724015]  [<c1317683>] ? pci_match_device+0xb3/0xc0
[   13.724015]  [<c13e3541>] __driver_attach+0x91/0xa0
[   13.724015]  [<c13e34b0>] ? driver_probe_device+0x1e0/0x1e0
[   13.724015]  [<c13e1b12>] bus_for_each_dev+0x42/0x80
[   13.724015]  [<c13e2eee>] driver_attach+0x1e/0x20
[   13.724015]  [<c13e34b0>] ? driver_probe_device+0x1e0/0x1e0
[   13.724015]  [<c13e2b7f>] bus_add_driver+0x16f/0x250
[   13.724015]  [<c1317520>] ? pci_device_shutdown+0x50/0x50
[   13.724015]  [<c13e3b2a>] driver_register+0x6a/0x160
[   13.724015]  [<f9ac7000>] ? 0xf9ac6fff
[   13.724015]  [<c13168f3>] __pci_register_driver+0x33/0x40
[   13.724015]  [<f9ac7017>] wl_module_init+0x17/0x19 [wl]
[   13.724015]  [<c1003132>] do_one_initcall+0x112/0x160
[   13.724015]  [<c160b085>] ? set_section_ro_nx+0x54/0x59
[   13.724015]  [<c10acc2e>] load_module+0x123e/0x19e0
[   13.724015]  [<c10ad448>] sys_init_module+0x78/0xb0
[   13.724015]  [<c161b24d>] sysenter_do_call+0x12/0x28
[   13.724015] Code: 45 f0 e8 0a 64 74 c7 90 fb 90 8d 74 26 00 89 d8 e8 3c c8 ff ff 89 d8 e8 15 c9 ff ff 89 d8 e8 ce cc ff ff 83 c4 04 5b 5e 5f 5d c3 <0f> 0b 8d 74 26 00 55 89 e5 57 56 53 83 ec 10 3e 8d 74 26 00 8b
[   13.724015] EIP: [<f98f69da>] wl_cfg80211_detach+0xca/0xd0 [wl] SS:ESP 0068:f4f7bc1c
[   13.766388] ---[ end trace 391034c02a02460c ]---
[   13.785768] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   13.977038] hda_codec: ALC883: SKU not ready 0x411111f0
[   13.991333] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   13.994575] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   13.997743] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   14.576410] Linux video capture interface: v2.00
[   14.943247] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   14.949013] r8712u: Staging version
[   14.952092] r8712u: register rtl8712_netdev_ops to netdev_ops
[   14.955078] r8712u: USB_SPEED_HIGH with 4 endpoints
[   14.958736] r8712u: Boot from EFUSE: Autoload OK
[   15.371480] r8712u: CustomerID = 0x0000
[   15.374432] r8712u: MAC Address from efuse = ec:1a:59:b0:d9:e8
[   15.377316] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   15.381934] usbcore: registered new interface driver r8712u
[   15.832251] 4:3:1: cannot get freq at ep 0x82
[   15.841789] uvcvideo: Found UVC 1.00 device Microsoft\xffffffc2\xffffffae\xffffffae LifeCam HD-5000 (045e:076d)
[   15.845997] usbcore: registered new interface driver snd-usb-audio
[   15.851113] input: Microsoft\xffffffc2\xffffffae\xffffffae LifeCam HD-5000 as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.1/1-3.1:1.0/input/input16
[   15.860411] usbcore: registered new interface driver uvcvideo
[   15.863085] USB Video Class driver (1.1.1)
[   16.205305] cfg80211: World regulatory domain updated:
[   16.205367] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.205435] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.205504] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.205661] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.205729] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.205794] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.218511] type=1400 audit(1377394938.834:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=577 comm="apparmor_parser"
[   17.219234] type=1400 audit(1377394938.834:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=577 comm="apparmor_parser"
[   17.219693] type=1400 audit(1377394938.834:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=577 comm="apparmor_parser"
[   17.220401] type=1400 audit(1377394938.834:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=576 comm="apparmor_parser"
[   17.221120] type=1400 audit(1377394938.834:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=576 comm="apparmor_parser"
[   17.221583] type=1400 audit(1377394938.834:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=576 comm="apparmor_parser"
[   17.222515] type=1400 audit(1377394938.834:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=660 comm="apparmor_parser"
[   17.223219] type=1400 audit(1377394938.834:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=660 comm="apparmor_parser"
[   17.223678] type=1400 audit(1377394938.834:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=660 comm="apparmor_parser"
[   18.433980] init: failsafe main process (673) killed by TERM signal
[   19.841292] type=1400 audit(1377394941.454:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=756 comm="apparmor_parser"
[   20.280603] Bluetooth: Core ver 2.16
[   20.280740] NET: Registered protocol family 31
[   20.280743] Bluetooth: HCI device and connection manager initialized
[   20.280756] Bluetooth: HCI socket layer initialized
[   20.280759] Bluetooth: L2CAP socket layer initialized
[   20.280768] Bluetooth: SCO socket layer initialized
[   20.452248] Bluetooth: RFCOMM TTY layer initialized
[   20.452268] Bluetooth: RFCOMM socket layer initialized
[   20.452271] Bluetooth: RFCOMM ver 1.11
[   20.602992] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.602998] Bluetooth: BNEP filters: protocol multicast
[   20.603011] Bluetooth: BNEP socket layer initialized
[   20.765973] init: avahi-cups-reload main process (792) terminated with status 1
[   21.067504] ppdev: user-space parallel port driver
[   22.263768] audit_printk_skb: 48 callbacks suppressed
[   22.263774] type=1400 audit(1377394943.878:28): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=853 comm="apparmor_parser"
[   22.264873] type=1400 audit(1377394943.878:29): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=853 comm="apparmor_parser"
[   22.266066] type=1400 audit(1377394943.878:30): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*//pxgsettings" pid=853 comm="apparmor_parser"
[   22.266905] type=1400 audit(1377394943.878:31): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*//sanitized_helper" pid=853 comm="apparmor_parser"
[   22.272280] type=1400 audit(1377394943.886:32): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=855 comm="apparmor_parser"
[   22.273027] type=1400 audit(1377394943.886:33): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=855 comm="apparmor_parser"
[   22.542065] type=1400 audit(1377394944.154:34): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=857 comm="apparmor_parser"
[   28.060468] sky2 0000:02:00.0 eth0: enabling interface
[   28.060611] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.061469] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.772616] r8712u: 1 RCR=0x153f00e
[   28.773359] r8712u: 2 RCR=0x553f00e
[   28.880277] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.880901] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.188285] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.788407] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.096419] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.204244] 4:3:1: cannot get freq at ep 0x82
[   39.204249] 4:3:1: cannot get freq at ep 0x82
[   40.344235] 4:3:1: cannot get freq at ep 0x82
[   41.344245] 4:3:1: cannot get freq at ep 0x82
[   50.574826] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   75.920403] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   76.228381] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   76.536461] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   97.153413] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

---

### Post by Crusty Old Fart on 2013-08-24
Okay. I'm beginning to suspect that none of our reboot parameter values  are working may be because of ACPI not being available for them. The  next test forces ACPI on and tests four reboot parameter values. Let's  see what this does. I'm especially interested in the output of dmesg for this run. 
     
     The next grub file we'll test is attached right here --> **[attach]245686[/attach]**
     Please download it and save it in your home directory.
     Then do the following:
     Become root:
     ```

     sudo su
     
```
     Copy the new grub file to /etc/default/grub:
     ```

     cp grub_af_rabcp.txt /etc/default/grub
     
```
     Update grub:
     ```

     update-grub
     
```
     Shut down the machine and physically power off.
     Boot it back up.
     
     See if it will reboot and power off by itself.
     
     When it comes back up,
     please post all the output of the following command:
     ```

     dmesg
     
```
     ... and let me know if you had to physically power off for the last     reboot.

     Thanks

---

### Post by Redjama on 2013-08-24
Still the same

```
[    1.470457] agpgart-intel 0000:00:00.0: Intel 945GM Chipset[    1.470573] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    1.470849] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.471120] ACPI: Battery Slot [BAT1] (battery absent)
[    1.471215] isapnp: Scanning for PnP cards...
[    1.476813] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.478715] brd: module loaded
[    1.523306] loop: module loaded
[    1.523546] ata_piix 0000:00:1f.2: version 2.13
[    1.523567] ata_piix 0000:00:1f.2: MAP [
[    1.523624]  P0 P2 IDE IDE ]
[    1.698137] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.742050] scsi0 : ata_piix
[    1.742228] scsi1 : ata_piix
[    1.742344] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[    1.742409] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[    1.742907] libphy: Fixed MDIO Bus: probed
[    1.743076] tun: Universal TUN/TAP device driver, 1.6
[    1.743135] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.743254] PPP generic driver version 2.4.2
[    1.743363] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.743427] ehci-pci: EHCI PCI platform driver
[    1.743523] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    1.743529] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.743594] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.743691] ehci-pci 0000:00:1d.7: debug port 1
[    1.747653] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    1.747686] ehci-pci 0000:00:1d.7: irq 23, io mem 0xd0644000
[    1.791440] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.791560] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.791625] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.791706] usb usb1: Product: EHCI Host Controller
[    1.791765] usb usb1: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    1.791828] usb usb1: SerialNumber: 0000:00:1d.7
[    1.835536] isapnp: No Plug & Play device found
[    1.835689] hub 1-0:1.0: USB hub found
[    1.835749] hub 1-0:1.0: 8 ports detected
[    1.835996] ehci-platform: EHCI generic platform driver
[    1.836083] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.836167] uhci_hcd: USB Universal Host Controller Interface driver
[    1.836259] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.836264] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.836331] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.836440] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.836540] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.836604] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.836683] usb usb2: Product: UHCI Host Controller
[    1.836743] usb usb2: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.836805] usb usb2: SerialNumber: 0000:00:1d.0
[    1.836981] hub 2-0:1.0: USB hub found
[    1.837042] hub 2-0:1.0: 2 ports detected
[    1.837198] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.837203] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.837267] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.837387] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.837490] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.837554] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.837634] usb usb3: Product: UHCI Host Controller
[    1.837693] usb usb3: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.837756] usb usb3: SerialNumber: 0000:00:1d.1
[    1.837921] hub 3-0:1.0: USB hub found
[    1.837981] hub 3-0:1.0: 2 ports detected
[    1.838136] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.838141] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.838204] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.838325] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.838425] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.838490] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.838570] usb usb4: Product: UHCI Host Controller
[    1.838629] usb usb4: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.838692] usb usb4: SerialNumber: 0000:00:1d.2
[    1.838856] hub 4-0:1.0: USB hub found
[    1.838917] hub 4-0:1.0: 2 ports detected
[    1.839072] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.839078] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.839145] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.839266] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    1.839367] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.839432] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.839512] usb usb5: Product: UHCI Host Controller
[    1.839572] usb usb5: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    1.839635] usb usb5: SerialNumber: 0000:00:1d.3
[    1.839799] hub 5-0:1.0: USB hub found
[    1.839860] hub 5-0:1.0: 2 ports detected
[    1.840115] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.856061] i8042: Detected active multiplexing controller, rev 1.1
[    1.862059] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.862125] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.862218] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.862303] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.862392] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.862587] mousedev: PS/2 mouse device common for all mice
[    1.862870] rtc_cmos 00:05: RTC can wake from S4
[    1.863086] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.863183] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.863373] device-mapper: uevent: version 1.0.3
[    1.863511] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.863616] EISA: Probing bus 0 at eisa.0
[    1.863679] Cannot allocate resource for EISA slot 1
[    1.863739] Cannot allocate resource for EISA slot 2
[    1.863798] Cannot allocate resource for EISA slot 3
[    1.863857] Cannot allocate resource for EISA slot 4
[    1.863916] Cannot allocate resource for EISA slot 5
[    1.863989] EISA: Detected 0 cards.
[    1.864076] cpufreq-nforce2: No nForce2 chipset.
[    1.864162] cpuidle: using governor ladder
[    1.864253] cpuidle: using governor menu
[    1.864312] ledtrig-cpu: registered to indicate activity on CPUs
[    1.864373] EFI Variables Facility v0.08 2004-May-17
[    1.864645] ashmem: initialized
[    1.864856] TCP: cubic registered
[    1.865050] NET: Registered protocol family 10
[    1.865355] NET: Registered protocol family 17
[    1.865425] Key type dns_resolver registered
[    1.865655] Using IPI No-Shortcut mode
[    1.865805] Loading module verification certificates
[    1.871723] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 3f91e9adadd74ee2134f443ced3a922f70cb07ef'
[    1.871823] registered taskstats version 1
[    1.875132] Key type trusted registered
[    1.877978] Key type encrypted registered
[    1.881245] rtc_cmos 00:05: setting system clock to 2013-08-25 02:23:11 UTC (1377397391)
[    1.881417] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.881479] EDD information not available.
[    1.899255] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.912457] ata2.00: ATAPI: Slimtype DVD C  DS24CZP, PA11, max UDMA/33
[    1.928345] ata2.00: configured for UDMA/33
[    1.957544] ata1.00: ATA-8: ST9250315AS, 0001BSM1, max UDMA/133
[    1.957607] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.972747] ata1.00: configured for UDMA/133
[    1.972946] scsi 0:0:0:0: Direct-Access     ATA      ST9250315AS      0001 PQ: 0 ANSI: 5
[    1.973264] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.973414] sd 0:0:0:0: [sda] Write Protect is off
[    1.973475] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.973515] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.973692] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.975707] scsi 1:0:0:0: CD-ROM            Slimtype DVD C  DS24CZP   PA11 PQ: 0 ANSI: 5
[    1.979743] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
[    1.979806] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.979989] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.980155] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.028796]  sda: sda1 sda2 < sda5 >
[    2.029228] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.029350] Freeing unused kernel memory: 788k freed
[    2.029771] Write protecting the kernel text: 6260k
[    2.029896] Write protecting the kernel read-only data: 2436k
[    2.029956] NX-protecting the kernel data: 3980k
[    2.050899] udevd[94]: starting version 175
[    2.144095] usb 1-2: new high-speed USB device number 2 using ehci-pci
[    2.189340] sky2: driver version 1.30
[    2.189437] sky2 0000:02:00.0: enabling device (0000 -> 0003)
[    2.189548] sky2 0000:02:00.0: Yukon-2 FE chip revision 1
[    2.189722] sky2 0000:02:00.0: irq 43 for MSI/MSI-X
[    2.190041] sky2 0000:02:00.0 eth0: addr 00:1b:24:2b:00:18
[    2.278550] usb 1-2: New USB device found, idVendor=050d, idProduct=945a
[    2.278621] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.278686] usb 1-2: Product: Belkin USB Wireless Adaptor
[    2.278746] usb 1-2: Manufacturer: Manufacturer Realtek 
[    2.278806] usb 1-2: SerialNumber: 00e04c000001
[    2.388049] usb 1-3: new high-speed USB device number 3 using ehci-pci
[    2.520457] usb 1-3: New USB device found, idVendor=04b4, idProduct=6560
[    2.520529] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.520856] hub 1-3:1.0: USB hub found
[    2.521074] hub 1-3:1.0: 4 ports detected
[    2.529255] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.529326] EXT4-fs (sda1): write access will be enabled during recovery
[    2.792191] usb 1-3.1: new high-speed USB device number 4 using ehci-pci
[    2.900436] usb 1-3.1: New USB device found, idVendor=045e, idProduct=076d
[    2.900502] usb 1-3.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.900584] usb 1-3.1: Product: Microsoft\xffffffc2\xffffffae\xffffffae LifeCam HD-5000
[    2.900644] usb 1-3.1: Manufacturer: Microsoft
[    2.972192] usb 1-3.3: new full-speed USB device number 5 using ehci-pci
[    3.067185] usb 1-3.3: New USB device found, idVendor=046d, idProduct=c52f
[    3.067250] usb 1-3.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.067332] usb 1-3.3: Product: USB Receiver
[    3.067390] usb 1-3.3: Manufacturer: Logitech
[    3.113733] usbcore: registered new interface driver usbhid
[    3.113799] usbhid: USB HID core driver
[    3.140404] usb 1-3.4: new low-speed USB device number 6 using ehci-pci
[    3.144069] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.0/input/input5
[    3.148269] hid-generic 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.7-3.3/input0
[    3.157171] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.1/input/input6
[    3.158132] hid-generic 0003:046D:C52F.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.7-3.3/input1
[    3.177733] EXT4-fs (sda1): recovery complete
[    3.182232] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.238067] usb 1-3.4: New USB device found, idVendor=05b8, idProduct=3155
[    3.238154] usb 1-3.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.238235] usb 1-3.4: Product: GE 98134
[    3.238293] usb 1-3.4: Manufacturer: GE 98134
[    3.242792] input: GE 98134 GE 98134 as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4:1.0/input/input7
[    3.242990] hid-generic 0003:05B8:3155.0003: input,hidraw2: USB HID v1.00 Keyboard [GE 98134 GE 98134] on usb-0000:00:1d.7-3.4/input0
[    3.250257] input: GE 98134 GE 98134 as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.4/1-3.4:1.1/input/input8
[    3.250503] hid-generic 0003:05B8:3155.0004: input,hiddev0,hidraw3: USB HID v1.00 Mouse [GE 98134 GE 98134] on usb-0000:00:1d.7-3.4/input1
[    6.165003] Adding 1561596k swap on /dev/sda5.  Priority:-1 extents:1 across:1561596k 
[    7.013221] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.262433] udevd[340]: starting version 175
[    8.141100] Disabling lock debugging due to kernel taint
[    8.342882] lp: driver loaded but no devices found
[    9.223474] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.681061] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    9.681183] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9
[    9.818604] cfg80211: Calling CRDA to update world regulatory domain
[    9.897557] lib80211: common routines for IEEE802.11 drivers
[    9.897563] lib80211_crypt: registered algorithm 'NULL'
[    9.968995] wmi: Mapper loaded
[   10.112278] [drm] Initialized drm 1.1.0 20060810
[   10.447619] intel_rng: FWH not detected
[   10.670896] acer_wmi: Acer Laptop ACPI-WMI Extras
[   10.671340] acer_wmi: Function bitmap for Communication Device: 0x27
[   10.671348] acer_wmi: Disabling ACPI video driver
[   10.676439] input: Acer BMA150 accelerometer as /devices/virtual/input/input10
[   10.691373] yenta_cardbus 0000:0a:09.0: CardBus bridge found [1025:0110]
[   10.691402] yenta_cardbus 0000:0a:09.0: Using CSCINT to route CSC interrupts to PCI
[   10.691405] yenta_cardbus 0000:0a:09.0: Routing CardBus interrupts to PCI
[   10.691412] yenta_cardbus 0000:0a:09.0: TI: mfunc 0x01321b22, devctl 0x66
[   10.913431] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[   10.913444] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.913449] ACPI Warning: 0x000011b0-0x000011bf SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   10.913454] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.913456] ACPI Warning: 0x00001180-0x000011af SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   10.913461] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.913463] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   10.920821] yenta_cardbus 0000:0a:09.0: ISA IRQ mask 0x0cf8, PCI irq 20
[   10.920828] yenta_cardbus 0000:0a:09.0: Socket status: 30000006
[   10.920833] pci_bus 0000:0a: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   10.920844] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge window: [io  0x5000-0x5fff]
[   10.920848] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff:
[   10.922343]  excluding 0x5000-0x50ff 0x5400-0x54ff
[   10.930053] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge window: [mem 0xd0200000-0xd02fffff]
[   10.930057] pcmcia_socket pcmcia_socket0: cs: memory probe 0xd0200000-0xd02fffff:
[   10.930060]  excluding 0xd0200000-0xd020ffff
[   10.930072] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge window: [mem 0x60000000-0x63ffffff pref]
[   10.930075] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x63ffffff:
[   10.930088]  excluding 0x60000000-0x63ffffff
[   11.060762] microcode: CPU0 sig=0x6ec, pf=0x20, revision=0x54
[   11.310842] [drm] 
[   11.311400] [drm] Memory usable by graphics device = 256M
[   11.311410] i915 0000:00:02.0: setting latency timer to 64
[   11.312644] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   11.312649] [drm] Driver supports precise vblank timestamp query.
[   11.312734] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   11.320074] [drm] initialized overlay support
[   11.366509] leds_ss4200: no LED devices found
[   11.612903] fbcon: inteldrmfb (fb0) is primary device
[   11.675166] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af:
[   11.677194]  excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   11.677219] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff:
[   11.678046]  excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   11.678066] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff:
[   11.678733]  clean.
[   11.678751] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
[   11.679490]  clean.
[   11.679512] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[   11.679527]  excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xdc000-0xdffff 0xe4000-0xfffff
[   11.679546] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff:
[   11.679562]  clean.
[   11.679580] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff:
[   11.679592]  excluding 0x60000000-0x60ffffff
[   11.679611] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[   11.681228]  clean.
[   11.728382] Console: switching to colour frame buffer device 160x64
[   11.735081] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   11.735084] i915 0000:00:02.0: registered panic notifier
[   11.735454] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   11.736781] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input11
[   11.739698] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   11.804143] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000/0x0, board id: 3655, fw id: 235996
[   11.831252] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   11.901181] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input12
[   12.503088] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.513978] wl 0000:03:00.0: enabling device (0000 -> 0002)
[   12.516485] malloc in abgphy done
[   12.516822] wl driver 6.20.155.1 (r326264) failed with code 21
[   12.516847] ------------[ cut here ]------------
[   12.516899] Kernel BUG at f99f69da [verbose debug info unavailable]
[   12.516951] invalid opcode: 0000 [#1] SMP 
[   12.516999] Modules linked in: wl(POF+) snd_hda_codec coretemp snd_hwdep(F) snd_pcm(F) snd_page_alloc(F) snd_seq_midi(F) tifm_7xx1 snd_seq_midi_event(F) tifm_core i915(OF) snd_rawmidi(F) snd_seq(F) pcmcia joydev(F) snd_seq_device(F) microcode(F) lpc_ich snd_timer(F) psmouse(F) yenta_socket acer_wmi pcmcia_rsrc sparse_keymap serio_raw(F) drm_kms_helper(OF) snd(F) pcmcia_core drm(OF) soundcore(F) wmi lib80211 i2c_algo_bit cfg80211 video(F) mac_hid lp(F) parport(F) hid_generic usbhid hid sky2
[   12.517587] Pid: 374, comm: modprobe Tainted: PF          O 3.8.0-29-generic #42-Ubuntu Acer, inc. Aspire 3680     /Prespa1         
[   12.517685] EIP: 0060:[<f99f69da>] EFLAGS: 00010246 CPU: 0
[   12.517779] EIP is at wl_cfg80211_detach+0xca/0xd0 [wl]
[   12.517824] EAX: 00000000 EBX: f4af9c90 ECX: f6790500 EDX: f4af9c90
[   12.517876] ESI: f754a000 EDI: f6790500 EBP: f6711c2c ESP: f6711c1c
[   12.517927]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   12.517973] CR0: 8005003b CR2: b73ed000 CR3: 36724000 CR4: 000007f0
[   12.518025] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
[   12.518077] DR6: ffff0ff0 DR7: 00000400
[   12.518111] Process modprobe (pid: 374, ti=f6710000 task=f6cd4010 task.ti=f6710000)
[   12.518172] Stack:
[   12.518194]  f6711c24 f4af9c90 f754a000 f6790500 f6711c44 f99ef2f3 f4af9c0c f4af9c00
[   12.518303]  f754a000 f6790000 f6711cf0 f99f005b c104bc47 c1a02980 00000400 00000096
[   12.518411]  c19e2078 0201826c 0000032b 00000000 00000002 00000000 0000032c 0000032c
[   12.518520] Call Trace:
[   12.518580]  [<f99ef2f3>] wl_free_if.isra.9+0x23/0xb0 [wl]
[   12.518661]  [<f99f005b>] wl_free+0x7b/0x240 [wl]
[   12.518706]  [<c104bc47>] ? console_unlock+0x337/0x480
[   12.518778]  [<f990fe92>] ? wlc_attach+0xf6c/0xfda [wl]
[   12.518825]  [<c160a746>] ? printk+0x4d/0x4f
[   12.518883]  [<f8a95518>] wl_pci_probe+0x4ff/0xfe7 [wl]
[   12.518932]  [<c103ce08>] ? default_spin_lock_flags+0x8/0x10
[   12.518985]  [<c161406d>] ? _raw_spin_lock_irqsave+0x2d/0x40
[   12.519039]  [<c13ed797>] ? __pm_runtime_resume+0x57/0x70
[   12.519087]  [<c1317729>] pci_device_probe+0x79/0xb0
[   12.519132]  [<c13e332c>] driver_probe_device+0x5c/0x1e0
[   12.519180]  [<c1317683>] ? pci_match_device+0xb3/0xc0
[   12.519226]  [<c13e3541>] __driver_attach+0x91/0xa0
[   12.519269]  [<c13e34b0>] ? driver_probe_device+0x1e0/0x1e0
[   12.519317]  [<c13e1b12>] bus_for_each_dev+0x42/0x80
[   12.519362]  [<c13e2eee>] driver_attach+0x1e/0x20
[   12.519402]  [<c13e34b0>] ? driver_probe_device+0x1e0/0x1e0
[   12.519450]  [<c13e2b7f>] bus_add_driver+0x16f/0x250
[   12.520057]  [<c1317520>] ? pci_device_shutdown+0x50/0x50
[   12.520057]  [<c13e3b2a>] driver_register+0x6a/0x160
[   12.520057]  [<f8a95000>] ? 0xf8a94fff
[   12.520057]  [<c13168f3>] __pci_register_driver+0x33/0x40
[   12.520057]  [<f8a95017>] wl_module_init+0x17/0x19 [wl]
[   12.520057]  [<c1003132>] do_one_initcall+0x112/0x160
[   12.520057]  [<c160b085>] ? set_section_ro_nx+0x54/0x59
[   12.520057]  [<c10acc2e>] load_module+0x123e/0x19e0
[   12.520057]  [<c10ad448>] sys_init_module+0x78/0xb0
[   12.520057]  [<c161b24d>] sysenter_do_call+0x12/0x28
[   12.520057] Code: 45 f0 e8 0a 64 64 c7 90 fb 90 8d 74 26 00 89 d8 e8 3c c8 ff ff 89 d8 e8 15 c9 ff ff 89 d8 e8 ce cc ff ff 83 c4 04 5b 5e 5f 5d c3 <0f> 0b 8d 74 26 00 55 89 e5 57 56 53 83 ec 10 3e 8d 74 26 00 8b
[   12.520057] EIP: [<f99f69da>] wl_cfg80211_detach+0xca/0xd0 [wl] SS:ESP 0068:f6711c1c
[   12.562259] ---[ end trace c237efa9a38f17a4 ]---
[   12.577892] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   12.750787] hda_codec: ALC883: SKU not ready 0x411111f0
[   12.765252] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   12.768632] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   12.771932] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   13.603144] Linux video capture interface: v2.00
[   13.983904] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   13.989640] r8712u: Staging version
[   13.993064] r8712u: register rtl8712_netdev_ops to netdev_ops
[   13.996178] r8712u: USB_SPEED_HIGH with 4 endpoints
[   14.000814] r8712u: Boot from EFUSE: Autoload OK
[   14.404351] cfg80211: World regulatory domain updated:
[   14.404412] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.404479] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.404546] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.404613] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.404680] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.404746] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.429304] r8712u: CustomerID = 0x0000
[   14.429347] r8712u: MAC Address from efuse = ec:1a:59:b0:d9:e8
[   14.429399] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   14.430958] usbcore: registered new interface driver r8712u
[   14.952323] 4:3:1: cannot get freq at ep 0x82
[   14.960236] uvcvideo: Found UVC 1.00 device Microsoft\xffffffc2\xffffffae\xffffffae LifeCam HD-5000 (045e:076d)
[   14.960375] usbcore: registered new interface driver snd-usb-audio
[   14.965817] input: Microsoft\xffffffc2\xffffffae\xffffffae LifeCam HD-5000 as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.1/1-3.1:1.0/input/input16
[   14.966090] usbcore: registered new interface driver uvcvideo
[   14.966141] USB Video Class driver (1.1.1)
[   15.857782] type=1400 audit(1377397405.474:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=597 comm="apparmor_parser"
[   15.858522] type=1400 audit(1377397405.474:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=597 comm="apparmor_parser"
[   15.858984] type=1400 audit(1377397405.474:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=597 comm="apparmor_parser"
[   15.859922] type=1400 audit(1377397405.474:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=596 comm="apparmor_parser"
[   15.860696] type=1400 audit(1377397405.478:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=596 comm="apparmor_parser"
[   15.861165] type=1400 audit(1377397405.478:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=596 comm="apparmor_parser"
[   15.862076] type=1400 audit(1377397405.478:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=665 comm="apparmor_parser"
[   15.862784] type=1400 audit(1377397405.478:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=665 comm="apparmor_parser"
[   15.863245] type=1400 audit(1377397405.478:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=665 comm="apparmor_parser"
[   16.986940] init: failsafe main process (678) killed by TERM signal
[   18.429418] type=1400 audit(1377397408.046:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=755 comm="apparmor_parser"
[   19.170944] Bluetooth: Core ver 2.16
[   19.171029] NET: Registered protocol family 31
[   19.171031] Bluetooth: HCI device and connection manager initialized
[   19.172866] Bluetooth: HCI socket layer initialized
[   19.172874] Bluetooth: L2CAP socket layer initialized
[   19.172887] Bluetooth: SCO socket layer initialized
[   19.357971] Bluetooth: RFCOMM TTY layer initialized
[   19.357993] Bluetooth: RFCOMM socket layer initialized
[   19.357996] Bluetooth: RFCOMM ver 1.11
[   19.475543] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.475549] Bluetooth: BNEP filters: protocol multicast
[   19.475562] Bluetooth: BNEP socket layer initialized
[   19.528668] init: avahi-cups-reload main process (790) terminated with status 1
[   19.919160] ppdev: user-space parallel port driver
[   20.950276] audit_printk_skb: 48 callbacks suppressed
[   20.950283] type=1400 audit(1377397410.566:28): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=855 comm="apparmor_parser"
[   20.951187] type=1400 audit(1377397410.566:29): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=855 comm="apparmor_parser"
[   20.952688] type=1400 audit(1377397410.570:30): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*//pxgsettings" pid=855 comm="apparmor_parser"
[   20.953532] type=1400 audit(1377397410.570:31): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*//sanitized_helper" pid=855 comm="apparmor_parser"
[   20.960043] type=1400 audit(1377397410.574:32): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=859 comm="apparmor_parser"
[   20.960825] type=1400 audit(1377397410.578:33): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=859 comm="apparmor_parser"
[   21.180999] type=1400 audit(1377397410.798:34): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=862 comm="apparmor_parser"
[   27.110002] sky2 0000:02:00.0 eth0: enabling interface
[   27.110145] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.110988] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.849200] r8712u: 1 RCR=0x153f00e
[   27.850682] r8712u: 2 RCR=0x553f00e
[   27.956356] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.956968] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.286145] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.924361] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.232373] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.156323] 4:3:1: cannot get freq at ep 0x82
[   38.156325] 4:3:1: cannot get freq at ep 0x82
[   39.296438] 4:3:1: cannot get freq at ep 0x82
[   40.296322] 4:3:1: cannot get freq at ep 0x82
[   49.776126] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready



```

---

### Post by Crusty Old Fart on 2013-08-24
Please try to give me a phone call.
Thanks

---

### Post by Crusty Old Fart on 2013-08-25
Well, I reckon phone calls are still either impossible or impractical.

So, here are my thoughts on the whole situation.

The following warnings and tainted kernel messages have been given in every single run of dmesg that we have made in this entire thread:
```

[    8.141100] Disabling lock debugging due to kernel taint
[   10.671348] acer_wmi: Disabling ACPI video driver
[   10.913431] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[   10.913449] ACPI Warning: 0x000011b0-0x000011bf SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   10.913456] ACPI Warning: 0x00001180-0x000011af SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   12.503088] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.517587] Pid: 374, comm: modprobe Tainted: PF          O 3.8.0-29-generic #42-Ubuntu Acer, inc. Aspire 3680     /Prespa1        
[   13.983904] r8712u: module is from the staging directory, the quality is unknown, you have been warned.

```

We've tried all ten available values for the reboot parameter at least once, many of them several times. They show up when we run:
```

cat /proc/cmdline

```
...but the kernel never seems to do anything with them.

In **[post=12768148]post #109 [IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG][/post]**, for the first time, we specified kernel options: acpi=force and reboot=a,b,c,p
The output from dmesg was essentially identical to the output we got in **[post=12768124]post #107 [IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG][/post]** when we tested with the only kernel option being: reboot=p
That was not very encouraging, to put it mildly.

I have updated the **[post=12765878]Resource Reference Post [IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG][/post]** in this thread to provide links to the information I've been studying.
You might want to take a look at them for some ideas I may not have considered. You'll see that the list of kernel parameters is extensive.

The power off problem we are having has thrown us the bird with everything we've thrown at it so far.

At this point, I don't think I can fix the problem with the current installation. I'm not exactly sure how serious kernel taints are. But I don't know how to fix them. So, it really doesn't matter. Regardless, the suggestion of a "tainted" kernel seems to indicate a problem.

When I run the following command on either of my Ubuntu machines:
```

dmesg | grep -i taint

```
Neither one of them produces any output whatsoever.
Both kernels accept boot parameters and respond to them appropriately.

In conclusion: I'm stumped.

If my installation was experiencing this kind of problem, I'd start over with a fresh install. And I wouldn't bother doing anything with it until running the following command produced absolutely no output:
```

dmesg | grep -i taint

```

If you want to keep your current installation and reload your original grub file,
then do the following:
Become root:
```

sudo su

```
Copy the original grub file to /etc/default/grub:
```

cp -p /etc/default/grub_original /etc/default/grub

```
Update grub:
```

update-grub

```
End your root session and return to your user prompt:
```

exit

```

If you want some guidance removing any of the files we created, just let me know and I'll be happy to help.

If you decide to start over with a fresh install and you run into problems, I'll be happy to help with that as well.

I'll stay subscribed to this thread, so it'll be easy for me to respond in a timely manner.

Best of luck to you,

Crusty

---

