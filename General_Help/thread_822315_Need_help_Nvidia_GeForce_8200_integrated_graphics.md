---
title: "Need help Nvidia GeForce 8200 integrated graphics"
date: 2008-06-08
forum: General Help
---

### Post by nrdlnd on 2008-06-08
Hi,
I've searched the forums but can't find anything about this chipset. The name of the chipset is MCP78S single chipset. It has an integrated rather powerful Nvidia GeForce 8200 video controller. The chipset supports AMD CPU:s. With this chipset it is possible to build a cost effective and energy efficient PC. I have built a small PC with the new Jetway mini-ITX mainboard JNC62K. The first problem was that the hard disk wasn't recognized during install but with help from the forum I put "all_generic_ide" at the end of the boot line and ubuntu "saw" the hard disk.

The second problem that isn't solved yet is that neither the free nor the restricted Nvidia-drivers seem to support the GeForce 8200 video controller. I can't get higher resolution than 800X600 and that is unacceptable. I have a 19" LCD screen with native resolution 1280X1024 and I have a DVI connection. My screen is an Eizo FlexScan L768. When I go to screen resolutions it says that the screen is "unknown".

I have tried to install the restricted drivers but I only get a black screen. "Envy" says none of the drivers has support for this chipset. The "nvidia-glx" and "nvidia-glx-new" doesnt work either.

At this time I don't care about Open-GL acceleration as I hope the restricted drivers in a couple of months will have support for this chipset. But I want 2D-support for 1280X1024 NOW!

 lspci:

00:00.0 RAM memory: nVidia Corporation Unknown device 0754 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 075c (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0752 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0751 (rev a1)
00:01.3 Co-processor: nVidia Corporation Unknown device 0753 (rev a2)
00:01.4 RAM memory: nVidia Corporation Unknown device 0568 (rev a1)
00:02.0 USB Controller: nVidia Corporation Unknown device 077b (rev a1)
00:02.1 USB Controller: nVidia Corporation Unknown device 077c (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 077d (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 077e (rev a1)
00:06.0 IDE interface: nVidia Corporation Unknown device 0759 (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 075a (rev a1)
00:09.0 IDE interface: nVidia Corporation Unknown device 0ad0 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 0760 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0569 (rev a1)
00:12.0 PCI bridge: nVidia Corporation Unknown device 075b (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200 (rev a2)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

I hope someone can help!

---

### Post by Pjotr123 on 2008-06-08
Install the restricted driver:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 2 )

and then do this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 as well)

This will probably do the job. :-)

Greeting, Pjotr.

---

### Post by nrdlnd on 2008-06-08
Thank you Pjotr!

I didn't do exactly as you said as I don't dare to activate the restricted driver as I suspect it hasn't yet support for the GeForce 8200. When I tried I only got a black screen and trying Envy says Envy can't identify my graphics chip. Maybe the latest Nvidia driver does support it but Envy doesn't seem to be updated to that one yet. But the second link helped me and I did:

"gksudo displayconfig-gtk" in the terminal

There I used a "1280X1024 LCD-screen" and just used "vesa-Generic VESA-compliant card" as driver. Now I have a non-accelerated 1280X1024 resolution and that will do until the restricted drivers are updated. Actually I don't care at all about the silly "desktop effects" that only slows down the computer. Accelerated graphics can be useful for other purposes though but I don't need it just now.

Of course if someone has managed to get OpenGL-support with the GeForce 8200 I might make a try!

Thank you again!

Per

---

### Post by nrdlnd on 2008-06-08
Update:

I did also try the Nvidia driver but it wasn't compliant.

Per

---

### Post by GlabGlog on 2008-06-15
I was able to successfully install the nVidia beta driver from the nvidia website (driver NVIDIA-Linux-x86_64-173.14.05-pkg2.run) for my GF8200.

It seems a little buggy though. I will probably remove it.

My GF8200 is the onboard vidio chip on a Biostar TF8200 A2+ MOBO.

I am running Ubuntu 8.04

---

### Post by nrdlnd on 2008-06-16
I tried the last Envy upgrade but only got a black screen. This time Envy didn't warn that it didn't recognize the chip. I have the video "working" with the VESA-generic and it will do until Nvidia may upgrade their driver. I think it's a shame from Nvidia not upgrading the Linux driver the same time as the Windoze variant!

---

### Post by olithered on 2008-06-19
I have the same motherboard and the same problem. Both the "official" and the envy 'nvidia' drivers failed to work and afterwards trying to use 'nv' had exactly the same behaviour. I guess it must have been 'vesa' all along.

Is there an open bug corresponding to this issue?

Meanwhile I am currently unable to get above 800x600 (though it worked before I started messing with things) - the xorg log file says something like "width too large for virtual size" :-/

---

### Post by nrdlnd on 2008-06-20
> **olithered said:**
> I have the same motherboard and the same problem. Both the "official" and the envy 'nvidia' drivers failed to work and afterwards trying to use 'nv' had exactly the same behaviour. I guess it must have been 'vesa' all along.

Is there an open bug corresponding to this issue?

Meanwhile I am currently unable to get above 800x600 (though it worked before I started messing with things) - the xorg log file says something like "width too large for virtual size" :-/

Hi,
See the third post in this thread. My screen wasn't recognized. With "gksudo displayconfig-gtk" in a terminal I could put in a generic LCD-screen and then the VESA-driver. Now I have the correct resolution for my screen (1280x1024).

Yes this is a bug but I don't know how to report bugs. I have contacted Alberto Milone. I did also try to get in contact with NVIDIA directly about the problem but I could nowhere on their web site find a way to contact their support! ](*,)

---

### Post by Hoyland84 on 2008-06-20
I know how you feel, as I have encountered the some problems as you. I got the driver running in Ubuntu 8.04, but it performed quite bad and X wouldn't apply it after rebooting after installation.

Now I am running openSuSE 11.0, with my GeForce 8200 fully accelerated. There are other issues with this OS concerning other hardware though, but it's all about pros and cons. Consider for yourself. I am happy to answer any questions.

---

### Post by sanders_muc on 2008-06-25
Hi

I've got similar problems, and got my on-board GeForce 8200 working now. It seems to me that a recent bugfix in the Nvidia driver solved some problems.

Here is what I have done:

**How to get an Nvidia GeForce 8200 to work on Ubuntu 8.04**

The rather new Nvidia GeForce 8200 chip is not yet supported by the open-source 'nv' driver currently shipped with Ubuntu. Here is how to get Nvidia's proprietary driver to work. (For a while, this driver seemed to require Linux kernel 2.6.25, while Ubuntu 8.04 uses kernel 2.6.24. However, now, the driver works fine with the 2.6.24 kernel.)

0. Prequesites

When I installed Ubuntu, it did boot up with screen resolution 800x600, using the generic VGA (or VESA?) driver. This required, however, to use the 'Alternate' installation CD. If you do not get any X to work, you can use this instructions as well, as everything is done in the command line. Just boot the 'recovery' system and get a shell.

1. Install build-essential by typing in a shell ('Terminal' in Menu 'Applications'/'Accessories')

[FONT="Fixedsys"]  sudo apt-get install build-essential[/FONT]

2. Download the newest NVidia driver from their web site. I have used version 173.14.09, which I found in the Download section of [www.nvidia.com](www.nvidia.com). If you do not have a running X yet and hence cannot use a web browser easily, I suggest to look up the URL of the driver with some other computer on the web site and then type at your command line something like
 
  wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/177.13/NVIDIA-Linux-x86_64-177.13-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/177.13/NVIDIA-Linux-x86_64-177.13-pkg2.run)

3. Shut down X. If you are using the Gnome Display Manager (GDM), which is the default on Ubuntu (but not on Kubuntu or Xubuntu), type in a shell:

[FONT="Fixedsys"]  sudo /etc/init.d/gdm stop[/FONT]

4. X shuts down and you are presented with a black-and-white text screen prompting you to "login". If you do not see the "login" prompt, press Alt-F1 or Alt-F2. Enter your username and password to log in.

5. Change to the directory that contains the downloaded Nvidia driver. If you simply downloaded it to your desktop (which is the Firefox default on Ubuntu), type

  cd Desktop

Type 
[FONT="Fixedsys"]  ls[/FONT]
to see whether the file is present and then start it:

[FONT="Fixedsys"]  sh NVIDIA-Linux-x86_64-177.13-pkg2.run[/FONT]

Answer the questions by navigating with cursor keys and Enter key. Do allow the installer to search for a kernel interface or compile one (if it cannot find one). The installation of 'build-essential' in step 1 was required to allow the installer to do so.

6. Typically, any existing X configuration will only confuse the Nvidia tools. Put it out of the way by typing
[FONT="Fixedsys"]  sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old[/FONT]

7. Let the Nvidia tools build a new X configuration file:
[FONT="Fixedsys"]  sudo nvidia-xconfig [/FONT]

8. Restart X and GDM:
[FONT="Fixedsys"]  sudo /etc/init.d/gdm start[/FONT]

9. Log in, then select 'Screen resolution' in the 'Systems' menu to set the correct resolution. Alternatively, you can use Nvidia's screen setting tool by typing in a shell
[FONT="Fixedsys"]  nvidia-settings[/FONT]
The latter might work better and offers more options.


HTH
  Simon

---

### Post by sanders_muc on 2008-06-25
Only to clarify this: The Ubunty Hardy package for the proprietary driver, the package 'nvidia-glx-new' contains currently version 169.12 of the driver. This version does not support the GeForce 8200. If you tried to use this, do

sudo apt-get remove nvidia-glx-new

before attempting to follow the steps in the previous post.

---

### Post by Kirizan on 2008-06-25
I just did what you said in post #10, and everything works fine, untill I restart.  As soon as I restart I get "Ubuntu is running in low-graphics mode", and it tells me that it could not detect my screen and graphics card correctly.  Any ideas how to fix this?

**edit I am using Ubuntu 8.04 (Heron I believe)

---

### Post by sanders_muc on 2008-06-25
Hi Kirizan,

what a disappointment. I just rebooted my own machine and also was back to 800x600, as you describe. You will probably also find some claim about the kernel being "tainted" by the nvidia module and an API version being wrong in your /var/log/messages.  

After some Googling, I found out how to solve this. 

As last step one should add to my recipe:

10. Edit the file linux-restricted-modules-common by typing

sudo gedit /etc/default/linux-restricted-modules-common

There, add the modules nvm nvidia_new, and nvidia_legacy to the list of disabled modules. In my file, this line now reads:

DISABLED_MODULES="nv nvidia_new nvidia_legacy"

I hope that solves the problem.

The solution was found here: 
  [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

HTH
  Simon

---

### Post by Kirizan on 2008-06-25
That worked perfectly, now everything starts up just fine.  Well, off to go play Oblivion on my new linux desktop.  Thaks again Sanders.

---

### Post by johnlvs2run on 2008-06-25
I also have the Biostar motherboard, and TF8200 online graphics.

Sanders_muc, I found this thread from another I started with the same issue, also getting black screens on the gui, Firefox still starting up with black screen and doesn't work at all.  Epiphany works great, except lines and images are fragmented and need to do a page up page down to read them.

Note:  Your message #10 starts with the correct driver #173.14.09, and then has the incorrect numbers later in the message.  Be sure to use #173.14.09 or the sequence won't work property.

[http://ubuntuforums.org/showthread.php?t=837488&page=4](http://ubuntuforums.org/showthread.php?t=837488&page=4)

---

### Post by johnlvs2run on 2008-06-25
> **nrdlnd said:**
> The first problem was that the hard disk wasn't recognized during install but with help from the forum I put "all_generic_ide" at the end of the boot line and ubuntu "saw" the hard disk.

Thank you for your message and this thread.  I have had the same exact issues, with the Biostar motherboard and Nvidia TF8200 online graphics.

Ubuntu 8,04 did not recognize my hard drive either, until I clicked F6 and typed pci=nomsi at the end of the boot line, i.e. "--pci=nomsi".

```
activate AHCI in the bios
change the AHCI DID for Linux -> Enabled
boot from liveCD
press F6 ... the boot code shows up on the screen
add "pci=nomsi" to the end of the boot code
```

[http://ubuntuforums.org/showthread.php?p=5149310&highlight=pci%3Dnomsi#post5149310](http://ubuntuforums.org/showthread.php?p=5149310&highlight=pci%3Dnomsi#post5149310)

[http://www.ubuntu1501.com/2007/01/installing-ubuntu-on-your-dell-1501.html](http://www.ubuntu1501.com/2007/01/installing-ubuntu-on-your-dell-1501.html)

---

### Post by ratatosk76 on 2008-07-07
I just put together a computer using Biostar T-series with the nvidia 8200 as integrated graphics.  

I'm trying to install Sabayon on the system.  I can put in the LiveCD and it boots the live environment.  Then, I'm staring at a command prompt.  I sign in as sabayonuser and then I'm looking at a bash shell.  I can get to a desktop and everything, but it's all text based.

Sabayon knows the chipset is nvidia but can't tell me what series or anything.

I looked on the Gentoo wiki and the 8200 isn't listed as being supported.

My plan was to buy an SLI capable graphics with a chipset that is supported by gentoo and then wait for nvidia to publish a usable driver for the 8200.  Then I could use my system and hopefully start using both GPUs in a few months.

You guys seem to have found a driver that works, but my question is:  How do I install drivers using a bash shell?

Thanks

---

### Post by sanders_muc on 2008-07-07
Hi raratosk76,

it is not at all difficult to install the driver from the command line. (It would be stupid to require graphics to work to install a graphics driver.)

My explanation in post #10 is meant for command line, so you should be able to follow it. Unfortunately, I am not familiar with Sabayon, but maybe, I can give you a few hints.

- First, you need to download the driver. As you cannot use a web browser (actually, you can: Lynx work in text mode), use 'wget', a command to download files from the web:

wget [http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/NVIDIA-Linux-x86-173.14.09-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/NVIDIA-Linux-x86-173.14.09-pkg1.run)

for the 32bit version and

wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/177.13/NVIDIA-Linux-x86_64-177.13-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/177.13/NVIDIA-Linux-x86_64-177.13-pkg2.run)

for the 64bit version. (These URLs are just copied and pasted from NVidia's selection tool and should be correct as of now.)

- Type 

sudo sh NVIDIA-Linux-x86_64-177.13-pkg2.run

to start the installer. You will see that it comes with a text-based interface that can be used with the cursor keys; no need for a working mouse.

- It may help to write a fresh X configuration afterwards by typing

sudo nvidia-xconfig --force-generate

- After you restart the display manager (by rebooting unless you know how to do otherwise with Sabayon), you may have a working X. If so, launch the command

nvidia-settings

in order to set your screen resolution.

HTH
  Simon

---

### Post by ratatosk76 on 2008-07-08
Hmm, the wget command works great, but I think I'm running into a catch-22.

I haven't even installed the OS yet.  So, it's booting in the live environment, and from there I think it's supposed to give me a gui to install on a hard drive.  Problem is, it can't launch a gui, so it's giving me a command line.

I can download the driver and fix the x.org file and everything, but I have to reboot.

Since the OS can't boot from a hard drive, I don't think it has anywhere to save the new files.  So when the system reboots, I'm right back where I started.

When I boot using the text based install option, I get the same command prompt...it doesn't seem to be any different.

I'm selecting to install the operating system, but it always seems to boot from the LiveCD and then go to a command prompt.  It doesn't seem to load to the hard drive.

All this might be a little too specific to sabayon, but any help would be much appreciated.

---

### Post by sanders_muc on 2008-07-09
Yes, I'm afraid, it's to specific to Sabayon.

For Ubuntu, the answer would be simple: There are two versions of the install CD of Ubuntu: the standard one, which also has a live system, and the "alternate" one, which has a text-based installer. The latter is precisely what you need: it allows you to install the operating system onto the hard disk first and take care of the graphics driver afterwards.

So, as this here is an Ubuntu forum, my advice should obviously be: Why don't you put aside Sabayon and try Ubuntu?

---

### Post by musta78 on 2008-07-10
OK.

I've done everything said.  The first time I got a error message saying that nvidia-installer must be run as root.  

Searched for hours til I finaly got the file copyed to the root folder.

But I still get the same error message.

So it basicly goes wrong when I'm in the root folder and type in the cmd sh NVIDIA-Linux-x86-173.14.19-pkg1.run

---

### Post by sanders_muc on 2008-07-10
'Run as root' does not mean that you should go to the 'root' folder but use the 'root' (i.e., superuser) account, the Linux equivalent to what MS Windows users know as Adminstrator account.

In Ubuntu, you can run any command as root by just prefixing it with 'sudo' (short for 'DO as SuperUser') and confirming this with entering yout password. (This reuqires that your account has the privilege to use 'sudo' which is usually set for the first user created.)

Hence, type in the directory where the file is:

sudo sh NVIDIA-Linux-x86-173.14.19-pkg1.run

---

### Post by herda05 on 2008-07-27
All,

I just bought a Biostar GF8200 M2+ motherboard and can't seem to get the Nvidia drivers working. I tried the steps listed earlier, but the screen keeps flashing black every couple of seconds. It's completely unuseable :(. Does anyone have steps to back out to the generic vesa driver?

thanks,
Dan H.

---

### Post by johnlvs2run on 2008-07-27
The latest driver is > NVIDA-Linux-x86-177.13-pkg1.run
I continued to have problems with the video until getting this latest one.

source page
[http://www.nvidia.com/object/linux_display_ia32_177.13.html](http://www.nvidia.com/object/linux_display_ia32_177.13.html)
click here to download
[http://us.download.nvidia.com/XFree86/Linux-x86/177.13/NVIDIA-Linux-x86-177.13-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/177.13/NVIDIA-Linux-x86-177.13-pkg1.run)

Also, the >> nivida-settings >> command did not work from the command line.  
If anyone has suggestions for changing this from the command line, let me know.
I had to start the gui and the annoying 800x600 resolution had returned.

Then from the desktop > applications > system tools > nvidia X server sttings 
> X server display configuration > "tab" to resolution > "space bar" to open 
> "arrow" to 1280x800 or whatever you want > apply > save to X > quit.

---

### Post by sanders_muc on 2008-07-28
johnlvs2run: This is interesting. A colleague had a very similar problem. His desktop, with ATI on-board graphics chip, worked find, until he upodated to Hardy, and then, the screen went black for a moment every couple of seconds, as you describe it. He bought a cheap NVidia graphics card, put it in and deactivated the onboard graphics. That solved the problem. 

Given that you experience it with Nvidia, it was probably not ATI's fault.

Sorry that I can't offer a solution.

  Simon

---

### Post by sanders_muc on 2008-07-28
johnlvs2run: This is interesting. A colleague had a very similar problem. His desktop, with ATI on-board graphics chip, worked find, until he upodated to Hardy, and then, the screen went black for a moment every couple of seconds, as you describe it. He bought a cheap NVidia graphics card, put it in and deactivated the onboard graphics. That solved the problem. 

Given that you experience it with Nvidia, it was probably not ATI's fault.

Sorry that I can't offer a solution.

  Simon

---

### Post by sanders_muc on 2008-07-28
Sorry for the double post, which was, of course, meant to reply to post #23 by herda05.

What I wanted to remark to #24 by johnlvs2run: Have you tried out the solution that I described in post #13? That solved the same problem for me.

HTH
  Simon

---

### Post by johnlvs2run on 2008-07-28
To clarify, there are still some issues with the video.

I'm using Epiphany browser, as Firefox still comes up all black.

The Nvidia video is not all that sharp as expected, and various screens periodically freeze momentarily.

---

### Post by herda05 on 2008-08-01
Still getting a flashing screen with the newest driver from Nvidia, NVIDIA-Linux-x86_64-173.14.12-pkg2.run.

If someone know how I can get back to the vesa driver and can post it or a link, that would be helpful.

I'm going to try and update the kernel to see if that helps.

---

### Post by johnlvs2run on 2008-08-02
> **herda05 said:**
> Still getting a flashing screen with the newest driver from Nvidia, NVIDIA-Linux-x86_64-173.14.12-pkg2.run.

Check msg #24 - latest driver is 
[http://www.nvidia.com/object/linux_display_ia32_177.13.html](http://www.nvidia.com/object/linux_display_ia32_177.13.html)

---

### Post by huangweiqiu on 2008-08-02
General steps for installing Nvidia diplay driver in Linux:~

[http://www.linuxine.com/2008/07/general-steps-for-installing-nvidia-diplay-driver-in-linux.html]("http://www.linuxine.com/2008/07/general-steps-for-installing-nvidia-diplay-driver-in-linux.html")

for your reference

---

### Post by herda05 on 2008-08-02
Tried installing with the beta driver and I still have the same problem. It's got to be something with the Biostar M2+ GF8200 MB as well. The gpu is integrated into the board, so whatever's happening has to reside with their implementation in some way. Ive seen that others have gotten the 8200 to run.

I'm not sure where to go from here, as there' nothing obvious in dmesg:
```
[ 1172.149520] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.13  Tue Jun 10 16:42:55 PDT 2008
[ 1227.444837] NVRM: Xid (0002:00): 26, Ch 00000003 M 00001b08 D 00000004 intr 00400000
[ 1227.762235] NVRM: Xid (0002:00): 26, Ch 00000003 M 00001b00 D 00000000 intr 00400000
[ 1444.835958] NVRM: Xid (0002:00): 26, Ch 00000003 M 00001b08 D 00000002 intr 00400000
[ 1444.923589] NVRM: Xid (0002:00): 26, Ch 00000003 M 00001b04 D 40b9f110 intr 00400000
[ 1638.701775] NVRM: Xid (0002:00): 26, Ch 00000001 M 00000860 D 00efebe7 intr 00400000
[ 1638.805139] NVRM: Xid (0002:00): 13, 0001 00000000 00000000 00000ff4 05a00000 00000000
[ 1638.805775] NVRM: Xid (0002:00): 13, 0001 00000000 00000000 00000ff4 05a00000 00000000
[ 1638.806362] NVRM: Xid (0002:00): 9, Channel 00000001 Instance 00000000 Intr 00000030
[ 1638.806950] NVRM: Xid (0002:00): 12, Ch 00000001 Cl 00000000 Off 00000ff4 Data 05a00000
[ 1638.821562] NVRM: Xid (0002:00): 9, Channel 00000001 Instance 00000000 Intr 00000030

```

or the xorg log:
```
(II) NVIDIA(0): Setting mode "CRT-0:1440x900_60@1440x900+0+0"
(II) NVIDIA(0): Setting mode "CRT-0:1280x960@1280x960+0+0"
(II) NVIDIA(0): Setting mode "CRT-0:1440x900@1440x900+0+0"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "CRT-0:1440x900@1440x900+0+0"
(II) Mouse0: ps2EnableDataReporting: succeeded
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "CRT-0:1440x900@1440x900+0+0"
(II) Mouse0: ps2EnableDataReporting: succeeded
(II) NVIDIA(0): Initialized GPU GART.
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00008084, 0x0000b498)
tossed event which came in late
mieqEnequeue: out-of-order valuator event; dropping.
tossed event which came in late
mieqEnequeue: out-of-order valuator event; dropping.
tossed event which came in late

```

If anybody has any suggestions on next steps, I'd appreciate it.

---

### Post by herda05 on 2008-08-02
By the way, just to document how I backed out:

1) Change to the directory with the NVIDIA*.run file
2) sudo sh NVIDIA*.run --uninstall
3) reboot
4) When X comes up, it cycles a few times as it tries to load and fails. Then a pop-up comes up with a message regarding low-graphics mode. I hit continue.
5) On login you have 800x600. You need to run gksudo displayconfig-gtk in a terminal. This allows you to set your monitor settings. I chose 1024x768 so I can at least use the screen.

---

### Post by johnlvs2run on 2008-08-02
> **herda05 said:**
> On login you have 800x600. You need to run gksudo displayconfig-gtk in a terminal. This allows you to set your monitor settings. I chose 1024x768 so I can at least use the screen.

Thanks but that only comes up blank and doesn't work for me.
When I set xorg to 1280x800 as in msg#24, every reboot reverts back to 800x600.

---

### Post by herda05 on 2008-08-03
After you set the resolution, a pop-up should appear indicating that you will need to logout for it to take affect. If that doesn't occur, then I don't think it actually makes the changes. By logging out, I believe it recycles X...

---

### Post by johnlvs2run on 2008-08-03
Thanks to Jualin for the part in bold, the resolution is finally staying put.

download latest driver from Nvidia
[http://www.nvidia.com/object/linux_display_ia32_177.13.html](http://www.nvidia.com/object/linux_display_ia32_177.13.html)

sudo apt-get install build-essential libxft-dev
alt-cntr-F1
sudo /etc/init.d/gdm/ stop
cd /home/loginname/Desktop/downloads/
sudo sh NVIDIA-Linux-x86-177.13-pkg1.run
yes, ok, yes, ok
cd ... (optional)
cntr-alt-del ... (or sudo /etc/init.d/gdm restart)

> applications > accessories > terminal
**sudo nvidia-settings**
This didn't work from the command prompt previously.

back to the desktop 
> applications > system tools > nvidia X server settings
> X server display configuration 
> "tab" to resolution
> "space bar" to open
> "arrow" to 1280x800 or whatever you want 
> apply > save to X > quit.

---

### Post by imneal on 2008-08-21
Hello, 

I also just bought the Biostar TF8200.  I'm trying to install the video drivers.  I did all that was said above, except I installed the lasted 64 bit drivers posted at: 

[http://www.nvidia.com/object/linux_display_amd64_173.14.12.html](http://www.nvidia.com/object/linux_display_amd64_173.14.12.html)

The drivers install, and I go into low-res mode.  When I try to get to the nvidia settings however, I get a pop up stating that:

"*You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. *"

I go to root, run nvidia-xconfig, it says that it's updated, I restart X server, and I'm still in low res mode.  When I try to go back to nvidia x server settings, the message is still there, and there are only limited options:  I can't "tab" to resolution or anything because there are no tabs.   

Any ideas? 

Thanks,

---

### Post by sanders_muc on 2008-08-21
imneal: I found that it helps to use
  sudo nvidia-xconfig --force-generate
to completely start from scratch with config file.

Also make sure that X and GDM are down (sudo /etc.init.d/gdm stop) while running this command. Maybe have a look, too, whether some other process modifies the config file afterwards.

HTH
  Simon

---

### Post by imneal on 2008-08-21
Thank you sanders!  

What I did though, was use envy to install the latest 64bit driver from NVIDIA (177.14.12), and it worked great.  

 

However, my sound has completely dropped.  I assume because it's using the GeForce 8200 chipset.  The sound wasn't great before because it kept sort of "skipping" when the startup played, or when I tried to play something on youtube. Now the sound still skips with the Nvidia sound card.  I've tried changing over to the realtek card, but same thing...  The cables are all good, and my speakers are good... 

I know this isn't the right forum, but can someone direct me in the right direction?

---

### Post by iwantmymythtv on 2008-09-03
I have the ecs gf8200 flavor and installed ubuntu 8.04 on it.  My display has been automaticaly set to a decent res, but if I change it in display preferences, the highest it allows is 1600x1024 which is much lower then what the default is set to automatically.  I also had crackling sound.

Where I was experiencing problems with the video was when I tried to play tv, it was clearly not using the gpu, and attempting to install the proprietary drivers caused the screen to get cryptic on reboot and the only resolution appeared to be fresh installs of ubuntu (Yes, I did this multiple times.)

I did find the following post which got my on board video running 100% (At least I think so far)  For anyone experiencing difficulties with onboard graphics drivers try following this:

[http://coyotesg.blogspot.com/2008/06/cracking-ubuntu-804-to-work-with-nvidia.html](http://coyotesg.blogspot.com/2008/06/cracking-ubuntu-804-to-work-with-nvidia.html)

Unfortunately for the sound... it completely dropped, now nothing.  I can see the "card" with lspci -v, but it is not recognized.  I've attempted to update the kernel to get fresh drivers; tried compiling them with alsa-source; and using drivers from alsa-project... but no-joy!

I do not know which drivers would be correct and have tried multiple builds with different drivers but no luck with any.  The end of the above post references "High Definition sound (Azalia)" and says to use  "the Intel HD (Azalia) module in Advanced Linux Sound Architecture, even if it isn't Intel", but I am not familiar with how to accomplish this.  

I hope the above post helps out, and hopefully someone can point me in the right direction for sound. I don't want to read the CC anymore to watch tv!

---

### Post by scotartt on 2008-10-11
> **sanders_muc said:**
> 

1. Install build-essential by typing in a shell ('Terminal' in Menu 'Applications'/'Accessories')

[FONT="Fixedsys"]  sudo apt-get install build-essential[/FONT]

2. Download the newest NVidia driver from their web site. I have used version 173.14.09, which I found in the Download section of [www.nvidia.com](www.nvidia.com). If you do not have a running X yet and hence cannot use a web browser easily, I suggest to look up the URL of the driver with some other computer on the web site and then type at your command line something like
 
  wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/177.13/NVIDIA-Linux-x86_64-177.13-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/177.13/NVIDIA-Linux-x86_64-177.13-pkg2.run)

3. Shut down X. If you are using the Gnome Display Manager (GDM), which is the default on Ubuntu (but not on Kubuntu or Xubuntu), type in a shell:

[FONT="Fixedsys"]  sudo /etc/init.d/gdm stop[/FONT]

4. X shuts down and you are presented with a black-and-white text screen prompting you to "login". If you do not see the "login" prompt, press Alt-F1 or Alt-F2. Enter your username and password to log in.

5. Change to the directory that contains the downloaded Nvidia driver. If you simply downloaded it to your desktop (which is the Firefox default on Ubuntu), type

  cd Desktop

Type 
[FONT="Fixedsys"]  ls[/FONT]
to see whether the file is present and then start it:

[FONT="Fixedsys"]  sh NVIDIA-Linux-x86_64-177.13-pkg2.run[/FONT]

Answer the questions by navigating with cursor keys and Enter key. Do allow the installer to search for a kernel interface or compile one (if it cannot find one). The installation of 'build-essential' in step 1 was required to allow the installer to do so.



When I try this, it insists to either download a pre-compiled kernel, or compile one, and then it breaks because it doesn't know where the kernel source is located. At that point it will not proceed any further.

The NVidia package is NVIDIA-Linux-x86-177.80-pkg1.run ... my kernel is 2.6.24-19-server

---

### Post by herda05 on 2008-11-01
Even with following the steps listed before and using 177.80 I still get flickering. It's not as bad with 177.80, but it still flickers everytime I type.

I'm beginning to think my problem is with the refresh rates settings. I'm going to test using another monitor and see if that solves the problem.

---

### Post by herda05 on 2008-11-03
All,

I just wanted to update everyone, in case someone else purchases this mobo, the Biostar GF8200 M2+.

After trying out the new drivers from Nvidia, 177.80, and upgrading from 8.04 to 8.10, and also playing with the Modeline of my moitor, it appeared there was no solution.

However, during one of the reboots I noticed the following message flash by:

```
Your BIOS doesn't leave a aperture memory hole
Please enable the IOMMU option in the BIOS setup
This costs you 64 MB of RAM 
```

So after I logged in I ran dmesg and greped IOMMU.

Then I turned to the web and saw that there were a lot of sites referencing this problem, but nothing with a good solution other than to enable[ IOMMU in the BIOS]("http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html"), or pass a [kernel parameter during boot]("http://kerneltrap.org/mailarchive/linux-kernel/2007/10/2/327967") in menu.lst

This mobo runs the AMI Bios v8, and after looking on the web I couldn't find any reference to IOMMU settings. Finally I just put this on the end of the kernel line:
```
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3b412076-85b4-4f4a-bb51-34ca49b7cd6a ro quiet splash iommu=memaper=3
```

I then reinstalled the nvidia 177.80 package, and voila, everything worked! AS this was the only problem I had with this machine, I have to say that with the onboard graphics working this is a great Ubuntu machine.

Thanks to everyone for the help.

---

### Post by johnlvs2run on 2008-11-18
I feel all your pain.
I went through endless fixes with ubuntu, none of which either lasted or worked at all.
Then I ran mint for a couple of months, which is similar to ubuntu but has more options and less problems.

A couple of months ago I got a sabayon dvd from ebay and finally installed it yesterday.
The install was flawless, the screen resolution is PERFECT, no hassles, VIOLA!!!!!!

All this time I thought the issue was biostar and nvidia, but the issue was ubuntu.
My recommendation is to get a sabayon dvd, and use sabayon for your os.

---

### Post by tuxolero on 2009-09-05
I have a similar problem in Kubuntu 9.04:

[http://ubuntuforums.org/showthread.php?t=1258494](http://ubuntuforums.org/showthread.php?t=1258494)

I have tried to fix it by following the steps from sanders_muc, but this disabled X completely.
When I start kdm, the computer switches to graphics mode, then returns to my text console. In /var/log/Xorg.0.log, it says "no screen found".
But in my /etc/X11/xorg.conf, there _is_ a screen section.
OK, it's not very detailed, but even when I copy the screen section from my backup xorg.conf to the nvidia-created one, it still complains about "no screen".

The driver I downloaded is NVIDIA-Linux-x86_64-185.18.36-pkg2.run and I think this should be new enough.

This is my xorg.conf (I think this is the original version, after trying to fix it by some editing):
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"    
EndSection                                   

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

How can I fix the xorg.conf or alternatively how can I restore my system to the previous setting and driver ?

---

### Post by Crandes on 2009-09-16
I have had the very same and VERY frustrating problem for a long time with Biostar GF8200 M2+ motherboard and all Nvidia drivers. Today I went to their website and upgraded the latest motherboard BIOS dated back in July and now all the flickering is gone! :P

---

