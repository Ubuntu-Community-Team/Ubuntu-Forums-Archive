---
title: "Ubuntu won't boot (Bad LUN number, low graphics mode, and much more!)"
date: 2016-01-11
forum: General Help
---

### Post by damog88 on 2016-01-11
Hi everyone,

I have been using Ubuntu 12.04 for almost 3 years, and I've only had minor problems (just a couple of booting issues with Windows 7, and one kernel update that went wrong). I know that I should have updated the system to 14.04, but I didn't do it because there are several programs working fine which I need almost daily for my job, and I'm afraid to lose compatibilty (i.e., Matlab, Topcat, and IRAF (astronomical analysis tool), and some others), and thus several working days...

My laptot is an HP-Pavilion-dv6, 64bits.

However, this Sunday, I don't know why, Ubuntu decided to give up on booting. On Sunday 4PM Ubuntu was booting without a single problem, and, with no updates nor installations in the middle, when I tried to start Ubuntu, at 9PM, it did not load the GUI. It threw a quick message:

```
Bad LUN (0:1)
Bad target number (1:0)
Bad target number (2:0)
.
.
Bad target number (7:0)
ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
```

Then, a window showed up saying something about "running in low graphics mode", and then, after accepting all the messages, the system goes to a black screen showing a message: ```
could not write bytes: Broken pipe
```, and it gets stuck there.

If I want to get out, I use Ctrl+ALT+F1 (or F2, F3, ...), to go to a tty1 terminal, where it asks me to login. But then, when I try to, and I input my user, it briefly says "Login incorrect" (without even asking for the password), and asks me back again to login. Of course, since I am not able to do anything at this point, I am forced to reboot manually.

After reading about this stuff through the web (I have been searching for over a day), I found several posts.

Since I was not able to login in the "low graphics mode", I went to "Recovery Mode" after booting, and after checking I had internet, I opened a terminal as root user. To my relief, I found that everything in my /home was where it was supposed to be. I used "startx" from the root user (which I am not able to switch to my user, via "su user" (it gives me "Permission denied" (funny, since I am the fu****g root!))). Lucky me, "startx" took me to a low graphic desktop for the root user. From there, I have tried several things I found while searching the web.

The "Bad LUN" and "broken pipe" stuff seem to be related to graphics drivers. However, I have tried to uninstall the nvidia drivers and then reinstalling them, but it keeps throwing the same errors. I have tried to reinstall the "ubuntu-desktop" package and also installing the "fglrx" package, but, again, it does nothing.

I have tried to boot in "runlevel_3", but it does nothing (actually, I do not understand what it does, but it appeared as a solution for the login issues).

I have tried to do an "apt-get upgrade", from the root user to try to overwrite everything that is broken, but it gives dependencies problems, and it does not install sh**.

I have used the "boot-repair" tool, in the hope of solving the booting issue, but it keeps the same.

EDIT: I have also read that it might be a disk space-related issue, so I checked with "df -h" the used disk space. Root partition was over 85%, so I looked for something to delete (some docs which I previouy backed up just in case), and then the free space was around 60%, but the Graphics problem persisted, and Gnome is not starting.

Nothing. I feel really powerless, since I do not know what else can I do.

I paste the outputs of lspci, fstab, and the errors (EE) I found on /var/log/Xorg.N.log:

lspci:```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6730M/6770M/7690M XT]
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
0d:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
19:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
```

fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=094bf11e-c119-4c87-90f4-d70b0f3f48c0 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda6 during installation
#UUID=ade214e0-09f3-47ed-8be4-2232899ba86d /boot           ext4    defaults        0       2
# /home was on /dev/sda10 during installation
UUID=712f3932-870c-4760-92c0-a1a8cc16cdec /home           ext4    defaults        0       2
# /tmp was on /dev/sda7 during installation
UUID=5de34fe5-ddba-4fe1-89b2-381221b5de30 /tmp            ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=65aa28ba-43a8-40ae-9052-c689c128b907 none            swap    sw              0       0
UUID=ade214e0-09f3-47ed-8be4-2232899ba86d       /boot   ext4    defaults        0       2
```

Xorg.0.log, Xorg.0.log.old: ```
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```

Xorg.1.log: ```
(EE) synaptics: SynPS/2 Synaptics TouchPad: Synaptics driver unable to detect protocol
            (EE) PreInit returned 11 for "SynPS/2 Synaptics TouchPad"
```

Xorg.1.log.old: ```
(EE) open /dev/fb0: No such file or directory
                (EE) synaptics: SynPS/2 Synaptics TouchPad: Synaptics driver unable to detect protocol
                (EE) PreInit returned 11 for "SynPS/2 Synaptics TouchPad"
```

Please, I need help. I need to have a fully functional laptop as soon as possible, this is driving me crazy :( :( :( :(

---

### Post by Seanan on 2016-01-12
Maybe the graphics part is because the NVIDIA drivers updated when you first booted up and are now not compatible? Would make sense because of the that Xorg log error. Also are you saying that you can't boot into the GUI and can't login to the terminal but can though Recovery mode? What do you mean by "low graphics desktop"? When you say "Of course, since I am not able to do anything at this point, I am forced to reboot manually" do you mean you can't type anything?[COLOR=#000000][/COLOR]

---

### Post by Seanan on 2016-01-12
Also make absolutely sure that you typed the correct user in at the prompt.

---

### Post by damog88 on 2016-01-12
> **Seanan said:**
> Maybe the graphics part is because the NVIDIA drivers updated when you first booted up and are now not compatible? Would make sense because of the that Xorg log error. Also are you saying that you can't boot into the GUI and can't login to the terminal but can though Recovery mode? What do you mean by "low graphics desktop"? When you say "Of course, since I am not able to do anything at this point, I am forced to reboot manually" do you mean you can't type anything?

Hi Seanan,

now that you mention this...something funny happens. Here is the output of lspsci:

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6730M/6770M/7690M XT]
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
0d:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
19:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
```

You can see that the graphics are AMD/ATI, not Nvdia. When I realized this, I used

```
apt-get purge nvidia-*
```

to remove all the Nvidia related drivers. However, this does not go away. Reading more, I found that some people managed to fix this by ```
apt-get install fglrx
```, but this didn't work for me. Others fixed this downloading the ATI drivers from the amd web. I downloaded the corresponding driver, built the package for my distro (the .run file you download does this automatically) and then installed it, but that didn't work either.

I managed to fix the apt-get upgrade broken packages, and did an ```
apt-get upgrade
```, which installed the last kernel (.97, I guess), but the same "Low graphics mode" window keeps poping up after the Ubuntu loading system screen.

When I say "low graphics desktop" I refer to the one that comes after executing ```
startx
``` from the root terminal started in the Recovery Mode (1024x768 resolution). And no, when I try to login, it lets me enter my username, just to reject it right after that. No password asked. Just a extremely brief "Login incorrect" after I input my username (which, believe me, is the correct one ("david" is not that difficult xD)), and then again the login prompt. But I am not able to tell the system to reboot via command line, so I need to press the power button.

---

### Post by damog88 on 2016-01-12
I managed to see that after the login issue, a quick message prompts and dissappears (I had to record a video with my phone and slow-play it... xD). The error says:

```
login: PAM failure, aborting: Critical error
```

I'starting to think of booting with a Live CD and reinstalling the OS. Maybe even with the 14.04 LTS. Do you know if there's a chance to keep my programs running after the upgrade? E.g., installing Matlab was a pain in the a**, and I had to install a lot of libraries and stuff. And I work A LOT with Matlab... Besides, I realized that Matlab is installed in /usr/local/Matlab. Do you know if this will be kept, or it will be removed with a new installation? Sorry for the off-topic, but this is starting to become the easiest solution :( :( :(

---

### Post by damog88 on 2016-01-13
I DIIIIIIIIIIID IIIIIITTTTTTTTT!!! I FIXED THE PROBLEEMMMM!!! :D :D :D :D

After reading the "PAM failure" message, I started to look for that error, and I found a post on askubuntu which put me in the right direction:

[http://askubuntu.com/questions/147184/12-04-x64-server-login-failure](http://askubuntu.com/questions/147184/12-04-x64-server-login-failure)

Although I don't have Ubuntu Server, I decided to have a look to my /etc/pam.d directory. And guess what? IT WAS EMPTY! I don't know what the heck happened and how did it happen, but it was empty. So I did exactly what the author of that post did: I loaded a live CD, looked for the files inside /etc/pam.d/, and copied them into my system. And voilá! Everything went back to normal (except for the "Bad LUN" and "Bad target number" messages, and some funny things that my desktop was doing that disappeared as soon as I removed the fglrx drivers).

But everything is right now, so I can finally breathe! :D

---

