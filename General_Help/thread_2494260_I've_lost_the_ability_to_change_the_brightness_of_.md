---
title: "I've lost the ability to change the brightness of my monitor"
date: 2024-01-10
forum: General Help
---

### Post by Paddy Landau on 2024-01-10
Up until a few minutes ago, when I ran the standard updates, I could adjust the brightness of my monitor either from the settings or via the keyboard shortcuts.

Now, the monitor is set to maximum brightness, which is so bright that it hurts my eyes. The keyboard shortcuts do nothing; and Settings > Screen Display no longer displays a brightness bar.

I can change the brightness using [FONT=courier new]xrandr[/FONT], but after a while, the monitor resets back to full brightness all by itself! The time before it resets varies seemingly arbitrarily from a couple of seconds to a few minutes.
```
xrandr --current                         # Tells me that the monitor name is eDP-1.
xrandr --output eDP-1 --brightness 0.5   # Sets brightness to 50%, for a short while only.
```

I have no clue how to diagnose or fix this. I don't know what apps were updated when I ran the updates a few minutes ago, nor how to find out.

[LIST]
[*]Hardware: Dell OptiPlex 5480 All-In-One
[*]Ubuntu 22.04
[*]This problem is happening on both Wayland and X.Org (I usually use X.Org)
[/LIST]
Are you able to help, please?

---

### Post by dragonfly41 on 2024-01-10
Some repeat  stories here ..

[https://duckduckgo.com/?q=ubuntu+22.04+screen+brightness+out+of+control&t=canonical&ia=web](https://duckduckgo.com/?q=ubuntu+22.04+screen+brightness+out+of+control&t=canonical&ia=web)

Perhaps glean a few clues.

---

### Post by tea for one on 2024-01-10
A new kernel arrived today (10 January 2024) - vmlinuz-6.5.0-14-generic.
Perhaps try an earlier kernel and see if equilibrium is restored.

---

### Post by #&amp;thj^% on 2024-01-10
Paddy dose this show anything?
```
journalctl -f | grep 'gnome-shell.*Soft-Brightness'

```

---

### Post by Paddy Landau on 2024-01-11
> **dragonfly41 said:**
> Some repeat  stories here ..
Thanks, but they seem to be to do with Nvidia, which I don't have, and they don't address this continuous resetting of the brightness.
> **1fallen said:**
> Paddy dose this show anything?
```
journalctl -f | grep 'gnome-shell.*Soft-Brightness'
```
Unfortunately, nothing at all. Even when I manually reduce the brightness, and the system automatically makes it 100% again, it still shows nothing.
> **tea for one said:**
> A new kernel arrived today (10 January 2024) - vmlinuz-6.5.0-14-generic.
Perhaps try an earlier kernel and see if equilibrium is restored.
This is the one that worked, thank you. I rebooted, and chose the previous version (6.2.0-39) from Grub. This restored the full brightness control. When I rebooted again into the new kernel, the problem resurfaced.

(As a side-note, my laptop works fine with the new kernel.)

This is, therefore, clearly a bug relating to the new kernel.

How specifically should I report this? On Launchpad, I imagine? Also, what hardware information would I need to include? Perhaps the GPU?
```
sudo lshw -numeric -C display
```

---

### Post by #&amp;thj^% on 2024-01-11
Paddy i would think it would be "ACPI"
ACPI is a power interface management standard which is implemented in operating system kernels. By default Linux kernel uses an inbuilt driver for keyboard keys, which is often non compatible with some keyboards.

---

### Post by ne29914 on 2024-01-11
Old story, but never solved. No one cares about this.
That's why I'm still on 20.04. 22.04 killed the brightness function. Reported to GitLab, dead after the default 90 days.
Oh. well...

---

### Post by Paddy Landau on 2024-01-12
> **1fallen said:**
> Paddy i would think it would be "ACPI"
ACPI is a power interface management standard which is implemented in operating system kernels. By default Linux kernel uses an inbuilt driver for keyboard keys, which is often non compatible with some keyboards.
Thanks, but it's not the keyboard at fault. It's the brightness itself.
> **ne29914 said:**
> 22.04 killed the brightness function.
It worked on my 22.04 until the latest kernel update. So, I wonder if it's something to do with the kernel and hardware rather than Ubuntu?
 > **ne29914 said:**
> Reported to GitLab, dead after the default 90 days.
Would you give me the link, please, so that I can refer to it when I create a bug report? I'll link my report here once done so that you can vote for it.

---

### Post by ne29914 on 2024-01-12
> **Paddy Landau said:**
> 
Would you give me the link, please, so that I can refer to it when I create a bug report? I'll link my report here once done so that you can vote for it.

Mine's so old, I abandoned it.

Just submit your report. If you're lucky, someone will respond with "not able to reproduce the issue" and ask for more info.
Then silence, and you can watch it expire after 90 days.

---

### Post by Paddy Landau on 2024-01-13
> **ne29914 said:**
> Mine's so old, I abandoned it.
It would be interesting to see where you reported it, so if you have the link, please let me know.

Anyway, I've submitted the [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.5/+bug/2049248").

Please vote for it (log in, and select the green writing near the top left).

---

### Post by #&amp;thj^% on 2024-01-13
I can't vote for it, it's not happening on mine.
It dose not seem to gather any interest in fixing it.
But your convinced it's not a keyboard driver so I'll just watch from the sidelines.

If it was me I'd file it on ACPI.
Just trying to help. ;)

---

### Post by MAFoElffen on 2024-01-13
The setting is under the brightness file under the (simulated) /sys/class/backlight/acpi_X... Which that folder is really a symlink, which points /sys/devices/<Bus>/<slot, etc>/acpi_videoX/ 

Here is something to try. (Is not persistent...) You need to be root, because of the permissions on the settings file...
```

sudo su -
Paths=$(find /sys/devices/*/*/ -name acpi_video* 2>/dev/null) && for Path in ${Paths}; do grep . $Path/brightness; done

```
It will output what the brightness settings current are... Lets say it says "15". "12" would be about 75% of that right?
```

for Path in ${Paths}; do sudo echo "12" > $Path/brightness; done

```
Play with it, and see if it changes anything for you...

---

### Post by dragonfly41 on 2024-01-13
I know very little on this subject to help but what I tend to do when I'm stuck is grab the evidence as written in your bug report and submit a Query to a Chat GPT assistant - Phind.com in my case - to let it do more detective work. Unfortunately the reply is submit a bug report. But this workaround is mentioned.

[COLOR=#1B1642][FONT=&quot]
[LIST]
[*]Use xcalib: Another workaround involves using the xcalib tool, which can adjust the screen brightness if your video card supports the relevant extension. To test if xcalib works on your machine, you can install it and run xcalib -i -a. If this command inverts the colors on your screen, it means xcalib is working. To revert back to your original screen, run the command again. Then, you can configure xcalib to adjust the brightness [5]("https://www.linux.org/threads/solved-brightness-does-not-work-on-xubuntu-22-04.41827/").
[/LIST]
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&quot][/FONT][/COLOR]
[COLOR=#1B1642][FONT=&quot][COLOR=#F8F8F2][FONT=Consolas]   [COLOR=#F1FA8C]sudo[/COLOR] [COLOR=#F1FA8C]apt[/COLOR] [COLOR=#F1FA8C]install[/COLOR] xcalib
   xcalib -i -a[/FONT][/COLOR]

[/FONT][/COLOR]

---

### Post by ne29914 on 2024-01-13
> **Paddy Landau said:**
> 
Please vote for it (log in, and select the green writing near the top left).

No. I don't even remember my GitLab login. And I'm not going back to the top "User-Hating" thing I've ever experienced.
It's probably good for developers, but NOT for users.
You will get zero votes. No user logs in unless it's a masochist.
If you're really lucky, a developer might have the same issue and give you a vote, but don't hold your breath.

---

### Post by Paddy Landau on 2024-01-14
> **1fallen said:**
> But your convinced it's not a keyboard driver so I'll just watch from the sidelines.
I'm unsure how it could be a keyboard driver, because it's not related to any keystrokes? Or is the keyboard driver somehow related to the monitor brightness settings? If I can change the brightness with xrandr, that's nothing to do with the keyboard, right?

> **1fallen said:**
> If it was me I'd file it on ACPI.
Do you mean on Launchpad against ACPI? Or is there some other place where I should report it? Sorry, I'm rather ignorant in these matters.

> **MAFoElffen said:**
> sudo su - …
For me, I get zero results with this:
```
sudo su
find /sys/devices/*/*/ -name 'acpi_video*'
```

> **dragonfly41 said:**
> … xcalib …
Well, xcalib does work on my machine. But, I didn't understand how to amend the brightness. In the end, trying to amend the brightness got me into a spot of trouble — I had to reboot the machine because I couldn't see what I was doing, ha ha! I'll stick with xrandr.

> **ne29914 said:**
> No. I don't even remember my GitLab login. And I'm not going back to the top "User-Hating" thing I've ever experienced.
It's probably good for developers, but NOT for users.
You will get zero votes. No user logs in unless it's a masochist.
If you're really lucky, a developer might have the same issue and give you a vote, but don't hold your breath.
This isn't GitLab; it's Ubuntu's Launchpad. I've issued plenty of bugs on Launchpad, and many of them have been addressed and fixed. There's no "user-hating", which fortunately for me, I don't think that I've ever experienced. Certainly never on Launchpad.

But, I need someone to vote for the [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.5/+bug/2049248"), because when you get zero votes, it's automatically closed after a while. If you could please vote for it — that's all you have to do, there's no "user-hating" — then at least someone will start to look at it. If it's not suitable for Launchpad, someone will tell me where to repost the bug — but that won't happen without a vote! (You log into Launchpad with the same ID that you use to log into Ubuntu Forums; you don't have to create a new account.) Thank you

---

### Post by MAFoElffen on 2024-01-14
I looked back at your first post to see which computer is was, then did a bit of digging...

Kernel module 'dell_uart_backlight' is responsible for controlling the brightness on that. When there is a problem with that, then the brightness control widget can disappear or not work correctly... They started having problems with Mantic, which uses Kernel 6.5 ([https://askubuntu.com/questions/1491087/brightness-control-no-longer-working-after-update-to-ubuntu-23-10-in-computer-de](https://askubuntu.com/questions/1491087/brightness-control-no-longer-working-after-update-to-ubuntu-23-10-in-computer-de)) Jammy 22.04.3 last week just went to kernel 6.5.0-14.

The User found that if he booted with one of the 6.2.0-X kernels, it then worked again. So the problem is related to Linux kernel 6.5.0-14...

Digging deeper, I found this Bug Report which affected module 'dell_uart_backlight' related to 6.5.0: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2032174](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2032174)

You can see that one that Bug Report, the fix was patched for Mantic, in source package 'linux-oem-6.5'. At the time, Jammy wasn't running kernel 6.5... But it did say that fixes where applied to jammy for both 'linux' and linux-oem-6.5'...

I would file your bug at LaunchPad, using the "Report a Bug" link in the upper right of that page, against 'linux' and 'linux-oem-6.5'.

I might also use find, to look to see if the kernel module 'dell-uart-backlight.ko' is in the modules directory in the 6.5.0 kernel tree
```

find /lib/modules -name dell-uart-backlight.ko

```
I can see it built on mine, but cannot confirm that it is working (on machines I have 6.5.0-14 still installed), as I don't have any Dell's here.

Me??? I'm having problem with Linux Kernel 6.5.0-14 also... But on NVidia drivers not building modules for that kernel in Jammy. That kernel is also affecting some users using VirtualBox from the repo's for Jammy.

---

### Post by Paddy Landau on 2024-01-14
> **MAFoElffen said:**
> I looked back at your first post to see which computer is was, then did a bit of digging...
Thank you! You found much more than I did. Thank you for the links.
> **MAFoElffen said:**
> The User found that if he booted with one of the 6.2.0-X kernels, it then worked again. So the problem is related to Linux kernel 6.5.0-14...
This is exactly what I found, which I've mentioned in my bug report (as noted below).
> **MAFoElffen said:**
> I would file your bug at LaunchPad, using the "Report a Bug" link in the upper right of that page, against 'linux' and 'linux-oem-6.5'.
Thanks, I [have done this]("https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.5/+bug/2049248").
> **MAFoElffen said:**
> I might also use find, to look to see if the kernel module 'dell_uart_backlight' is in the modules directory in the 6.5.0 kernel tree
This, unfortunately, gave zero results:
```
find /lib/modules -name dell_uart_backlight*
```
> **MAFoElffen said:**
> Me??? I'm having problem with Linux Kernel 6.5.0-14 also... But on NVidia driver not building modules for that kernel in Jammy. That kernel is also affecting some users usig VirtialBox from the repo's for Jammy.
Do you think that this is related?

---

### Post by MAFoElffen on 2024-01-14
Yours is Intel UHD 6XX graphics right?

---

### Post by Paddy Landau on 2024-01-14
> **MAFoElffen said:**
> Yours is Intel UHD 6XX graphics right?
You seem to have duplicated most of your previous post!

To answer your question, I don't know how to tell, but I tried this:
```
$ sudo lshw -numeric -C display
  *-display                 
       description: VGA compatible controller
       product: CometLake-S GT2 [UHD Graphics 630] [8086:9BC5]
       vendor: Intel Corporation [8086]
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 resolution=1920,1080
       resources: irq:145 memory:c1000000-c1ffffff memory:d0000000-dfffffff ioport:3000(size=64) memory:c0000-dffff
```
Does that answer your question, or do I have to look elsewhere?

EDIT: Oh, wait, the answer is yes!

---

### Post by MAFoElffen on 2024-01-14
LOL. Dang. Didn't notice I had double posted...

Here is what I have with that (and I don't even have Dell):
```

mafoelffen@Mikes-B460M:~$ find /lib/modules -name dell-uart-backlight.ko
/lib/modules/6.5.0-14-generic/kernel/drivers/platform/x86/dell/dell-uart-backlight.ko
/lib/modules/6.2.0-39-generic/kernel/drivers/platform/x86/dell/dell-uart-backlight.ko

```
But that one does have 
```

mafoelffen@Mikes-B460M:~$ lspci -nnnk | grep -A3 -E 'Display|VGA|3D'
00:02.0 VGA compatible controller [0300]: Intel Corporation CometLake-S GT2 [UHD Graphics 630] [8086:9bc5] (rev 05)
    DeviceName: Onboard - Video
    Subsystem: Gigabyte Technology Co., Ltd CometLake-S GT2 [UHD Graphics 630] [1458:d000]
    Kernel driver in use: i915

```

---

### Post by Paddy Landau on 2024-01-15
> **MAFoElffen said:**
> Here is what I have with that (and I don't even have Dell)…
Ah… Your first post had underscores instead of hyphens. Mine's the same as yours!

 And I have:
```
$ lspci -nnnk | grep -A3 -E 'Display|VGA|3D'00:02.0 VGA compatible controller [0300]: Intel Corporation CometLake-S GT2 [UHD Graphics 630] [8086:9bc5] (rev 05)
    DeviceName: Onboard - Video
    Subsystem: Dell CometLake-S GT2 [UHD Graphics 630] [1028:0988]
    Kernel driver in use: i915
```
This looks like the same as yours.

So, as you suggest, this seems to be to do with the Intel GPU rather than with Dell.

I'll update my bug report, and maybe you can vote for it?

---

### Post by MAFoElffen on 2024-01-15
I think the problem may be the combination of Intel GPU, source packages 'linux' & 'linux-oem-6.5', kernel series 6.5.0, and kernel module:
```

/lib/modules/6.5.0-14-generic/kernel/drivers/platform/x86/dell/dell-uart-backlight.ko

```
I have that same combination of hardware, although mine is a Gigabyte board. (Not Dell)
```

mafoelffen@Mikes-B460M:~$ sudo dmidecode -t 1
# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 3.2.0 present.

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Gigabyte Technology Co., Ltd.
    Product Name: B460M DS3H AC-Y1
    Version: Default string
    Serial Number: Default string
    UUID: 03c00218-044d-053f-4d06-d50700080009
    Wake-up Type: Power Switch
    SKU Number: Default string
    Family: B460 MB

```
And in the doc's, yes, it has underscores between the words, but on the machine, in the filesystem, it has hyphons between the word in the module name. I don't know why.

---

### Post by MAFoElffen on 2024-01-15
I inserted that module into my kernel:
```

mafoelffen@Mikes-B460M:~$ sudo modprobe dell-uart-backlight
mafoelffen@Mikes-B460M:~$ lsmod | grep dell
dell_uart_backlight    20480  0

```
Notice the difference in the undescores and/or hyphons there?

I logged out, and back in, to restart the desktop... No backlight brightness control.

So I do not have a backlight control. I can vote on it if you file it at LaunchPad and post the link... My tip is to include the link I posted to the previous Bug report, saying it is similar, but to that one, but though not crashing, it is resulting in no "Brightness Control".

*** But now that I know that setting exists, there is a control for it (which I though only exists before on laptops), and that I have similar hardware... I can play around with this and see what is possible.

---

### Post by MAFoElffen on 2024-01-15
Notice how I said, in my last post, where I thought only laptops and notebooks had controllable brightness controls?

I installed brightnessctl on it to see what was controllable:
```

mafoelffen@Mikes-B460M:~$ brightnessctl --list
Available devices:
Device 'phy0-led' of class 'leds':
    Current brightness: 1 (100%)
    Max brightness: 1

Device 'input5::capslock' of class 'leds':
    Current brightness: 0 (0%)
    Max brightness: 1

Device 'input5::scrolllock' of class 'leds':
    Current brightness: 0 (0%)
    Max brightness: 1

Device 'input5::numlock' of class 'leds':
    Current brightness: 0 (0%)
    Max brightness: 1

```
I don't have a brightness controllable display... Hmmm. Let me try a few other things.

---

### Post by MAFoElffen on 2024-01-15
I found a way...
```

sudo add-apt-repository ppa:apandada1/brightness-controller
sudo apt update
sudo apt install --yes brightness-controller

```
See attached screenshot. The first slider will control the brightness.

---

### Post by dragonfly41 on 2024-01-15
Responding to the earlier difficulty (post #15) in using suggested xcalib (although the main issue discussed now seems to be resolved) I think if you search for discussions with "xcalib NEAR gamma" the usage becomes clearer.

And here is a link I just found to experiment with.

[https://askubuntu.com/questions/9248/is-there-a-software-utility-to-adjust-screen-gamma-brightness-contrast](https://askubuntu.com/questions/9248/is-there-a-software-utility-to-adjust-screen-gamma-brightness-contrast)

might fill in some gaps.

---

### Post by Paddy Landau on 2024-01-15
> **MAFoElffen said:**
> Notice the difference in the undescores and/or hyphons there?
How odd!
> **MAFoElffen said:**
> I can vote on it if you file it at LaunchPad and post the link... My tip is to include the link I posted to the previous Bug report, saying it is similar, but to that one, but though not crashing, it is resulting in no "Brightness Control".
I have created the [bug report here]("https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.5/+bug/2049248"), and mentioned your link and this thread.
> **MAFoElffen said:**
> Notice how I said, in my last post, where I thought only laptops and notebooks had controllable brightness controls?
Mine is a desktop, and I have had the controls until version kernel 6.5. I was able to also control it through the keypad using custom-assigned keys.
> **MAFoElffen said:**
> I installed brightnessctl on it to see what was controllable:
I get this:
```
Device 'input18::numlock' of class 'leds':    Current brightness: 1 (100%)
    Max brightness: 1
```
> **MAFoElffen said:**
> I found a way... brightness-controller
Thank you! That works for me.
> **dragonfly41 said:**
> Responding to the earlier difficulty (post #15) in using suggested xcalib…
Thank you. That seems to talk mainly about Redshift, which I used to use until Ubuntu reverted to GNOME, which has this setting built in. Interestingly, that setting still works on kernel 6.5; it might be software-controlled rather than hardware-controlled.

---

### Post by MAFoElffen on 2024-01-15
I added a comment on the Bug Report to fill in the gaps.

---

### Post by Paddy Landau on 2024-01-15
> **MAFoElffen said:**
> I added a comment on the Bug Report to fill in the gaps.
Excellent, thank you!

---

### Post by #&amp;thj^% on 2024-01-15
Paddy i had a brain fart on ACPI it is for ASUS only on that tool.
```
acpitool -A
Sorry, but no Asus ACPI extensions were found on this system. 

```
But I knew it was one of those four lettered words....LOL (Dell ASUS)

---

### Post by him610 on 2024-01-15
I got into this discussion a little late, but I use this line to adjust the brightness/dimness of my monitor:
```
xrandr --output HDMI-1 --gamma 0.8:0.8:0.8 
```
It works for me.
```
$ bin/run-id.sh
           `-/osyhddddhyso/-`              hugh@h270m 
        .+yddddddddddddddddddy+.           ---------- 
      :yddddddddddddddddddddddddy:         OS: Xubuntu 22.04.3 LTS x86_64 
    -yddddddddddddddddddddhdddddddy-       Kernel: 6.5.0-14-generic 
   odddddddddddyshdddddddh`dddd+ydddo      Uptime: 3 days, 21 hours, 52 mins 
 `yddddddhshdd-   ydddddd+`ddh.:dddddy`    Packages: 2512 (dpkg), 12 (snap) 
 sddddddy   /d.   :dddddd-:dy`-ddddddds    Shell: bash 5.1.16 
:ddddddds    /+   .dddddd`yy`:ddddddddd:   Resolution: 1920x1080 
sdddddddd`    .    .-:/+ssdyodddddddddds   DE: Xfce 
ddddddddy                  `:ohddddddddd   WM: Xfwm4 
dddddddd.                      +dddddddd   WM Theme: Default 
sddddddy                        ydddddds   Theme: Greybird-dark [GTK2], Greybird [GTK3] 
:dddddd+                      .oddddddd:   Icons: elementary-xfce-darker [GTK2/3] 
 sdddddo                   ./ydddddddds    Terminal: xfce4-terminal 
 `yddddd.              `:ohddddddddddy`    Terminal Font: DejaVu Sans Mono 9 
   oddddh/`      `.:+shdddddddddddddo      CPU: Intel Pentium G4560 (4) @ 3.500GHz 
    -ydddddhyssyhdddddddddddddddddy-       GPU: Intel HD Graphics 610 
      :yddddddddddddddddddddddddy:         Memory: 2281MiB / 7636MiB 
        .+yddddddddddddddddddy+.
           `-/osyhddddhyso/-`                                      
                                                                   


Startup finished in 3.228s (kernel) + 16.316s (userspace) = 19.545s 
graphical.target reached after 16.053s in userspace
Mon Jan 15 01:24:42 PM EST 2024
         #####  #######   ###
 #    # #     # #    #   #   #   #    #
 #    #       #     #   # #   #  ##  ##
 ######  #####     #    #  #  #  # ## #
 #    # #         #     #   # #  #    #
 #    # #         #      #   #   #    #
 #    # #######   #       ###    #    #
 
```

---

### Post by Paddy Landau on 2024-01-17
> **1fallen said:**
> I knew it was one of those four lettered words...
Ha ha, OK.
> **him610 said:**
> I use this line to adjust the brightness/dimness of my monitor…
Unfortunately, that doesn't work well for me. Even with gamma 0.1, the brightness is too high while messing up the colours on the monitor.

---

### Post by Paddy Landau on 2024-01-17
**New information:**

I am using [FONT=courier new]xrandr[/FONT] [FONT=courier new]--brightness[/FONT]… in a background script that repeats every third of a second, to keep the brightness where I need it whenever the system resets it to 100%.

I've noticed that the system resets the brightness *exactly* every minute, with five resets over five seconds (the screen flashes each time before my script resets it). The resets aren't equally timed, but they always follow the same consistent pattern.

However, the system sometimes leaves the brightness alone for a longer period before reverting to resetting each minute.

I would love to be able to diagnose what is causing that weird behaviour. If we could do so, it would help the devs to isolate the problem. The problem is that I have no clue whatsoever where to start.

---

### Post by #&amp;thj^% on 2024-01-19
Paddy I have no clue on your make and model Dell, but do you have this option in your bios
""Eco Power"" if so try and disable it, to check if that gives you brightness control back.

And i assume your Bios is up to date.

---

### Post by Paddy Landau on 2024-01-20
> **1fallen said:**
> Paddy I have no clue on your make and model Dell
Dell OptiPlex 5480 All-In-One (it's in my original post)
> **1fallen said:**
> do you have this option in your bios ""Eco Power"
I've just looked around, and I don't see that, or something that might be equivalent.
> **1fallen said:**
> And i assume your Bios is up to date.
You assume correctly :)

So far this seems to be a bug with the driver for the Intel HD U*nn* GPUs.

---

### Post by dragonfly41 on 2024-01-20
In post #33 you refer to "background script". Is this using cron?

Perhaps this is a clue.

[https://unix.stackexchange.com/questions/215148/xrandr-script-runs-correctly-from-command-line-fails-as-cron-job](https://unix.stackexchange.com/questions/215148/xrandr-script-runs-correctly-from-command-line-fails-as-cron-job)

And I believe that EcoPower is an app for laptop battery management.

I am on Dell Inspiron tower.

---

### Post by Paddy Landau on 2024-01-20
> **dragonfly41 said:**
> In post #33 you refer to "background script". Is this using cron?
No, it's a simple Bash script with a loop that includes "sleep .3s" and the xrandr command. I don't always need to run this; it's highly inconsistent.

The xrandr command does work correctly. It's just the kernel 6.5 repeatedly resets the brightness back to 100%. When it does this, it does so every 60 seconds exactly, and repeats in a consistent pattern over the next couple of seconds. But, sometimes it stops doing it anywhere from a few minutes to an hour or so, during which I don't need to run the background script. It's weird.
> **dragonfly41 said:**
> And I believe that EcoPower is an app for laptop battery management.
Ah, I see. Mine is a desktop, not a laptop.

---

### Post by #&amp;thj^% on 2024-01-20
> **Paddy Landau said:**
> 
Ah, I see. Mine is a desktop, not a laptop.
That clears it up for me then.

---

### Post by dragonfly41 on 2024-01-20
Can you perhaps experiment with Actiona, running your script using code box and using Actiona to test the workflow.  Takes a bit of time to get used to, but you can build in your diagnostics and use the built in delays. Consider it as a test bed.

sudo apt install actiona.

You can run the GUI or use command - actexec myactiona.ascr

---

### Post by Paddy Landau on 2024-01-21
> **dragonfly41 said:**
> Can you perhaps experiment with Actiona…
This looks like I'll have to learn how Actiona works. If I try to run my script as you suggest ("bright" is the name of my script):
```
$ actexec --script bright
Input script file has an invalid script schema
```
I don't understand what you are trying to achieve, though. The script essentially contains a loop, summarised here:
```
#!/usr/bin/env bash
while true
do
        xrandr --output eDP-1 --brightness 0.5
        sleep 0.3s
done
```
It works just as well if I simply issue this command:
```
while true; do xrandr --output eDP-1 --brightness 0.5; sleep 0.3s; done &
```

---

### Post by dragonfly41 on 2024-01-21
> [COLOR=#000000]I don't understand what you are trying to achieve, though. [/COLOR][COLOR=#000000]

[/COLOR]Sorry to drop you in the deepend without swimming lessons.
Better to forget about actexec command. Only required when running a batch of Actiona scripts.
All you require for experimenting is the GUI. Hit Alt + F2 dialogue and run .. actiona .. (no capital) to launch GUI. Each code can be run with System > Command widget.
The first line is simply the app .. xrandr
Then parameters follow on next line.
Set name of output .. e.g. output 
This is a variable .. $output ..  which can be printed in Console widget    

But let me find time in next day or so  to write a sample. You can think of each script as a mini workflow.

---

### Post by Paddy Landau on 2024-01-22
> **dragonfly41 said:**
> But let me find time in next day or so  to write a sample. You can think of each script as a mini workflow.
Thank you. But, could I ask, what would be the point of this? The xrandr command works perfectly; it's something else in the background that changes the brightness every 60 seconds.

---

### Post by dragonfly41 on 2024-01-22
Paddy, the suggested Actiona tool is no more than a repository of custom experiments. a testbed.

Often one is &#8220;scraping&#8221; forum discussions for ideas and running various commands to test ideas. I tend to "cherry pick" and place them in Actiona scripts to be run as "micro workflows".
If you are happy still copying and pasting code snippets then don't bother.
But I have created a little Actiona container which holds various experiments and links to their sources.

Some time back there was an app named clicompanion (still around) which held collections of commands.

Returning to your issue:
This thread for example cites the "60 seconds timeout" you cite.
[https://askubuntu.com/questions/1247965/xrandr-settings-in-cli-are-reset-every-60-seconds](https://askubuntu.com/questions/1247965/xrandr-settings-in-cli-are-reset-every-60-seconds)

And the answer: > For anyone who comes through the same trouble : it was really caused by the night light setting.

This next thread suggests a bash script.
[https://askubuntu.com/questions/1150339/increment-brightness-by-value-using-xrandr](https://askubuntu.com/questions/1150339/increment-brightness-by-value-using-xrandr)

This thread is interesting.
[https://askubuntu.com/questions/1003101/how-to-use-xrandr-gamma-for-gnome-night-light-like-usage](https://askubuntu.com/questions/1003101/how-to-use-xrandr-gamma-for-gnome-night-light-like-usage)

And here is a useful Python script
 
[https://askubuntu.com/questions/672640/desktop-monitor-brightness-adjusting?noredirect=1&lq=1 ]("https://askubuntu.com/questions/672640/desktop-monitor-brightness-adjusting?noredirect=1&lq=1")


I embedded these experiments into an Actiona container. Each within a Procedure.


I like the Python script since I can embed that into Albert (another useful tool).

...

If you are interested in how I build these cherrypicked ideas into Actiona scripts I can post a demo, or you can do it yourself. I use Actiona for all classes of experiments and workflows.

Another example is holding TheFu advice on rdiff-backup.

And for accessing and automating all types of services. Auto login.

---

### Post by tea for one on 2024-01-23
Some gnome extensions have been designed to control screen brightness.
A few of them mention [https://www.ddcutil.com/](https://www.ddcutil.com/)

Paddy, not wanting to send you on a wild goose chase but maybe worth a little investigation.
I have no experience of these extensions nor ddcutil, just offering info.

---

### Post by Paddy Landau on 2024-01-24
> **dragonfly41 said:**
> This thread for example cites the "60 seconds timeout" you cite. … night light
That's interesting! It's been behaving today, but as soon as I manually enabled the Night Light, the problem returned!

I shall experiment a little with that, and add the information to the bug report. It might have been that I normally log into the computer before sunrise, so Night Light was on right from the start.

The other scripts are informative, thank you.
> **tea for one said:**
> Some gnome extensions have been designed to control screen brightness.
A few of them mention [https://www.ddcutil.com/](https://www.ddcutil.com/)
Thank you. I'll have a look.

---

### Post by Paddy Landau on 2024-01-24
**Update:**

This does indeed seem to be linked with the Night Light. When I turn Night Light either on or off, the problem immediately recurs. If the Night Light remains on, the problem happens every 60 seconds.

I haven't checked if it *always* happens while the Night Light is turned on, or if there are times when it takes a break, but this is extra information for the devs, so I'll add it to the [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.5/+bug/2049248").

---

### Post by dragonfly41 on 2024-01-24
I'll get back to chasing my own flock of wild geese.  I did not get around to posting embedded experiments in Actiona but you get the point. It is a container for such multiple choice experiments but one of choice. I believe that if Redshift is disabled/uninstalled this eliminates Night Light. But I cannot see Night Light settings in my Settings. I understand that it depends on what session is chosen at desktop user login point (there are multiple choices and I started on "Ubuntu" but have tried others at login stage).

---

### Post by Paddy Landau on 2024-01-24
> **dragonfly41 said:**
> I cannot see Night Light settings in my Settings.
Settings > Screen Display (on the left) > Night Light (at the very top)

It should be present for both Wayland and X.Org.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293334&stc=1[/IMG]

---

### Post by dragonfly41 on 2024-01-24
Sorry, I don't see that just now. I have been running my own experiments to track down cause of (a) wired mouse freezing and (b) no connection to Bluetooth Logitech Mouse/Keyboard (but ok with Bose audio). This wild goose entails trying different sessions and (without rebooting to check) I think my last boot was into Metacity. I'll try  selecting Xorg again.

[P.S] adding more info.  Since posting above I have tried three sessions.

Gnome Flashback (Metacity)
Gnome on Xorg
Ubuntu on Wayland .. current session

All on Ubuntu 20.04.

None  show Night Light.
  
But this might be due to me using an ancient Philips screen. At a guess.   

Oops. Mouse going crazy again.

---

### Post by Paddy Landau on 2024-01-25
> **dragonfly41 said:**
> None  show Night Light.
What's your kernel version?

Good luck with your mouse!

---

### Post by Paddy Landau on 2024-08-27
I have some good news! There is a solution, albeit not a great one. But at least it's something to add to the bug report.

There is a maintainer who maintains the mainline kernel with the bits and pieces that Canonical has, for reasons known only to itself, removed.

It's [called Zabbly]("https://github.com/zabbly/linux"). Unfortunately, it needs Secure Boot to be turned off, but I'm trying to work out how to sign the kernel so that Secure Boot can be turned on again.

You can, if you wish, follow the [ongoing thread]("https://ubuntuforums.org/showthread.php?t=2499896").

---

### Post by Paddy Landau on 2024-08-30
Aargh! The solution from Zabbly no longer works after the latest update :(

---

### Post by HermanAB on 2024-09-01
My sincere condolences - I had the same issue many moons ago.  This is one of those things that force users to distro-hop till they find one that works.

---

### Post by Paddy Landau on 2024-09-01
> **HermanAB said:**
> My sincere condolences - I had the same issue many moons ago.  This is one of those things that force users to distro-hop till they find one that works.
Thanks. It's such a pain, and so unnecessary.

---

