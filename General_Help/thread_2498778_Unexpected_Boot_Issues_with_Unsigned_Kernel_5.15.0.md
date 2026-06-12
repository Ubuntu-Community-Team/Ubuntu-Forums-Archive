---
title: "Unexpected Boot Issues with Unsigned Kernel 5.15.0-113 on Ubuntu 20.04"
date: 2024-06-27
forum: General Help
---

### Post by guimaster on 2024-06-27
Hello Ubuntu Community,


I recently encountered a boot issue on my Ubuntu 20.04 system after a kernel update. The Software Updater installed kernel version 5.15.0-113, which was marked as "unsigned." This caused my system to fail to boot correctly, only allowing me to boot using a startup USB or by selecting an older kernel version.

After removing the unsigned kernel using Synaptic Package Manager (as terminal commands were unsuccessful), I noticed improved stability. However, I'm concerned about how an unsigned kernel was installed via the official update mechanism.

Has anyone else experienced similar issues with unsigned kernels being installed through the Software Updater? Any insights or recommendations to prevent this from happening in the future would be greatly appreciated.

Thank you!

Best regards,
guimaster

---

### Post by yancek on 2024-06-27
Do you have Secure Boot enabled in the BIOS?  Did you previously have it enabled?  The link below provides information.

[https://itsfoss.community/t/what-is-signed-and-unsigned-kernel/10716/2](https://itsfoss.community/t/what-is-signed-and-unsigned-kernel/10716/2)

---

### Post by guimaster on 2024-06-27
Thanks for the reply.

Secure Boot was disabled. I believe I had to disable it to install Linux and I never re-enabled it.

The unsigned kernel 5.15.0-113 was installed via the Software Updater. My active PPAs at the time included:

[LIST]
[*]launchpad.net/atareao
[*]repo.radeon.com (amd)
[*]launchpad.net/deadsnakes
[*]packages.microsoft.com (ms-teams)
[*]Canonical Partners
[*]Canonical Partners somerville
[*]Canonical Partners somerville-beric-amd
[/LIST]
I have since disabled all but the deadsnakes PPA and the three Canonical Partner repositories.

When I ran the command ```
dpkg --list | grep linux-image
``` the kernel was listed as 'unsigned.'
[B]
Questions:[/B]

[LIST=1]
[*]Could the unsigned kernel be related to any of the active PPAs?
[*]Should I enable Secure Boot to prevent similar issues in the future?
[*]ChatGPT suggested that this issue could be caused by repository sync issues. Is that possible? I'm using 'Server for Canada' according to Software & Updates.
[/LIST]
Thanks for your help!

Best regards,
guimaster

---

### Post by guimaster on 2024-06-28
Thank you for your attempt to help! I think I realized what happened...

I see now that I pasted my list of available kernels into ChatGPT when I first had the issue, and at that time 5.15.0-113 showed up as 'signed.' I then attempted to uninstall it and rebooted. Upon reboot, I had no internet, and the temp sensors weren't working. It was likely at that point that the kernel said 'unsigned.' So, it appears that it didn't uninstall properly, causing the kernel to be damaged and resulting in the kernel showing up as 'unsigned.'

Thank you for your attempt to help!

---

### Post by chris-verdon on 2024-06-29
A friend of mine is having a similar problem. What did you do to resolve yours?

---

### Post by guimaster on 2024-06-29
You didn't provide specifics, so I'm not sure exactly where you are stuck. Here's what I did to resolve my issue. Thankfully, I had ChatGPT available to help me, or it would have taken a lot longer to find solutions.

After installing kernel 5.15.0-113, I couldn't boot to the desktop. The GRUB bootloader screen was not enabled, so I couldn't choose a different kernel. Fortunately, I had a USB drive with MX Linux on it. Tapping F12 on bootup, I selected the MX Linux USB drive. Inside MX Linux, there was an option for bootup repair. It didn't actually repair anything but offered five different boot options. I tried each one until I got one that worked.

Once I successfully booted up, I needed to unhide the GRUB bootloader options screen. Here are the instructions I followed, courtesy of ChatGPT:

Open Terminal:
Press Ctrl + Alt + T to open the terminal.

Edit the GRUB Configuration File:
Open the GRUB configuration file using a text editor with superuser privileges. For example, you can use nano:
> sudo nano /etc/default/grub


Modify the GRUB Configuration:
Look for the line that says GRUB_TIMEOUT_STYLE=hidden. Change it to:
> GRUB_TIMEOUT_STYLE=menu


Set the GRUB_TIMEOUT value to a positive integer (e.g., 10), which will give you 10 seconds to choose an option:
> GRUB_TIMEOUT=10
Save and Exit:

If you are using nano, save the file by pressing Ctrl + O, then press Enter to confirm. Exit by pressing Ctrl + X.

Update GRUB:
After editing the configuration file, update GRUB to apply the changes:
> sudo update-grub


Reboot:
Restart your computer to see the changes take effect:
> sudo reboot


By following these steps, the GRUB menu should appear during boot, allowing you to select an older kernel version.

After rebooting, I selected a kernel version that was just slightly older than the most recent one from the GRUB menu. I was able to boot up to the desktop just fine with the older kernel.

Finally, I used Synaptic Package Manager to search for "113" and purged every instance of it that was installed and related to the kernel.

---

### Post by guimaster on 2024-06-29
I'm not knowledeable enough in Linux to fix things on my own so I'm probably not the best person to ask. But here are some instructions from ChatGPT on how to create and use an Ubuntu usb drive to troubleshoot your issues:


[LIST=1]
[*]**Create a Bootable USB**:
[LIST]
[*]Download the Ubuntu ISO from the [official Ubuntu website]("https://ubuntu.com/download").
[*]Use software like Rufus (for Windows) or Startup Disk Creator (for Ubuntu) to create a bootable USB drive.
[/LIST]

[*]**Boot from USB**:
[LIST]
[*]Insert the USB drive into your computer.
[*]Restart your computer and enter the boot menu (usually by pressing F12, F2, Esc, or Del during startup).
[*]Select the USB drive as the boot device.
[/LIST]

[*]**Try Ubuntu**:
[LIST]
[*]When the Ubuntu installer loads, select "Try Ubuntu" to boot into the live session without making any changes to your system.
[/LIST]

[*]**Install Boot Repair**:
[LIST]
[*]Once you&#8217;re in the live session, connect to the internet.
[*]Open a terminal and add the Boot Repair PPA:
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair
[*]Launch Boot Repair by typing:
boot-repair
[/LIST]

[*]**Use Boot Repair**:
[LIST]
[*]The Boot Repair tool will open and automatically scan your system.
[*]Follow the on-screen instructions to repair your boot issues. Typically, you&#8217;ll want to select the "Recommended repair" option.
[/LIST]

[*]**Reboot**:
[LIST]
[*]Once Boot Repair has finished, restart your computer. Hopefully, your boot issues will be resolved.
[/LIST]
[/LIST]

---

### Post by yancek on 2024-06-29
There is no way a kernel update should change the GRUB_TIMEOUT setting in the /etc/default/grub file so I wouldn't know how that happened.  The default setting there is 10 as you show you did.  If you have only the Ubuntu OS installed, you may not see a Grub menu but it should be set to show so you can make an alternate selection in case of problems.  There are ways to show the menu such as holding down the right shift key on boot.

---

### Post by guimaster on 2024-06-29
The kernel update did not change the GRUB_TIMEOUT setting. For some reason, it has always been set to 0 and hidden. I don't recall setting it that way, as I know that I can use it to easily revert to an older kernel version should I have an issue. It might be a by-product of me installing Lubuntu, purging the Lubuntu desktop, and installing MATE, which I had to do because the default Ubuntu installer would not support an encrypted install over multiple drives. 

I was not aware of the right-shift option; ChatGPT did not mention it.

---

### Post by chris-verdon on 2024-06-29
Ah, see we had GRUB access from the get go so we already switched to the old kernel. Thought there was a fix for the new one. Hope that happens soon. Thanks anyway!

---

### Post by guimaster on 2024-06-29
I found this on the Linux Mint subreddit:

> [COLOR=#131313][FONT=-apple-system]Kernel 5.15.0-113 is still having issues like 112, don't update to this kernel if you use:
AMD Picasso/Raven 2 [Radeon Vega Series / Radeon Mobile Series][/FONT][/COLOR]
[COLOR=#131313][FONT=-apple-system]AMD Raven Ridge [Radeon Vega Series / Radeon Mobile Series]
It can be fixed by rolling back but is still an issue with the newest update.
[/FONT][/COLOR]
The only solution as of now is to uninstall it. I used Synaptic Package Manager to search for '113' and purged all instances of the kernel. To prevent it from being installed again, you can use the terminal:

```

sudo apt-mark hold linux-image-5.15.0-113-generic
sudo apt-mark hold linux-headers-5.15.0-113-generic
```

---

