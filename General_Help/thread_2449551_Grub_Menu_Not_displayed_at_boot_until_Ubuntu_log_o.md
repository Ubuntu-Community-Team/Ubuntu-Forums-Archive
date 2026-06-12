---
title: "Grub Menu Not displayed at boot until Ubuntu log on"
date: 2020-08-29
forum: General Help
---

### Post by jsamiry on 2020-08-29
Hi, I am running 20.04, dual boot with Windows 10.  While running 19.10 the grub screen stopped displaying so I cannot select Windows.  Instead, the screen remains blank until the Ubuntu log in screen displays when I can successfully sign in to Ubuntu.  I was hoping that the upgrade to 20.04 would correct this but no luck.  I wonder whether this is a setting in the grub file but am not experienced enough to investigate it.

If I hit the down arrow key at the start, it sounds as though it boots windows but there is no display.

The blank screen means I cannot boot from a USB.

TIA

jsa

---

### Post by dinkidonk on 2020-08-29
Edit the file "/etc/default/grub" and set these lines to the values given here:

```
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=3
```

"GRUB_DEFAULT" is the boot option selected by default, "saved" means the last selected option is used. "GRUB_SAVEDEFAULT" saves the last selected boot optiong (required for "GRUB_DEFAULT=saved"). "GRUB_TIMEOUT_STYLE=hidden" must be commented out with "#" in order to display the grub menu at all. "GRUB_TIMEOUT" is the number of seconds the grub menu is displayed before the selected boot option is launched.

When you are done editing the default grub settings, you must run the command "sudo update-grub" in a terminal. Make sure to unplug any (USB) drives with bootable systems you do not want in the grub menu.

---

### Post by jsamiry on 2020-08-29
Hi, thank you for your prompt response and have followed your suggestion.  The GRUB TIMEOUT_STYLE was = hidden so that has been commented out.  Unfortunately, after running update_grub, the behaviour of the machine on boot up hasn't changed.  Is there a way to check if the update has taken place?

regards

jsa

---

### Post by dinkidonk on 2020-08-29
Did you make the other modifications, like setting a timeout? If there is no timeout the GRUB menu will not display. On some systems, holding down the SHIFT key during boot will force the GRUB menu to display.

---

### Post by oldfred on 2020-08-29
Grub only boots working Windows.
So if Windows is hibernated or needs chkdsk, grub will not boot it.
And Windows fast start up sets hibernation flag and Windows updates keep turning fast startup back on.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by jsamiry on 2020-08-29
> **dinkidonk said:**
> Did you make the other modifications, like setting a timeout? If there is no timeout the GRUB menu will not display. On some systems, holding down the SHIFT key during boot will force the GRUB menu to display.

Sorry, should have been more precise.  Here's what the grub file looks like now:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'




GRUB_DEFAULT=saved
#GRUB_TIMEOUT_STYLE=hidden
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

---

### Post by tea for one on 2020-08-29
Here is an example to give you a 10 second view of grub

```
sudo nano /etc/default/grub
```

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

```
sudo update-grub
```

Please also note **oldfred's** comments about **working Windows** to allow grub to display all OS choices at boot time.

---

### Post by jsamiry on 2020-08-31
> **tea for one said:**
> Here is an example to give you a 10 second view of grub

```
sudo nano /etc/default/grub
```

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

```
sudo update-grub
```

Please also note **oldfred's** comments about **working Windows** to allow grub to display all OS choices at boot time.

Hi, thanks for the detailed suggestion. Ttried this. Same result, blank screen until the Ubuntu log-in presented.

regards

jsa

---

### Post by tea for one on 2020-08-31
When you run ```
sudo update-grub
```

Can you post the terminal output within code tags **#**?

Advanced reply will show the code tag icon.

---

### Post by jsamiry on 2020-08-31
```
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-42-generic
Found initrd image: /boot/initrd.img-5.4.0-42-generic
Found linux image: /boot/vmlinuz-5.4.0-40-generic
Found initrd image: /boot/initrd.img-5.4.0-40-generic
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings
done

```
Hope I've done the "code tags" bit correctly.

Thanks for the help

jsa

---

### Post by tea for one on 2020-08-31
> **jsamiry said:**
> Hope I've done the "code tags" bit correctly.

Yes, you've done the code tags perfectly - it makes the output easier to read.

The output itself looks fine.

Also in code tags, can you post the output of:-

```
sudo nano /etc/default/grub
```

Lastly, in your original post, you mentioned that you dual boot - is this on one drive or separate drives?

---

### Post by jsamiry on 2020-09-01
Oldfred, thanks for info on whether Windows will boot or not.  My problem is that nothing displays until the Ubuntu log on screen appears.  I will certainly come back to your info once I can get it to display the menu from which I could select windows.  At the moment, it does not display.

regards

jsa

---

### Post by jsamiry on 2020-09-01
Hi Tea for Two,

I didn't spot your very prompt and welcome response, because it went onto two pages!

Ok here's /etc/default/grub/

```
GRUB_DEFAULT=0GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'




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

I am dual booting fron one drive.

Thanksa for the help.

jsa

---

### Post by Dennis N on 2020-09-01
This line:
```
GRUB_DEFAULT=0GRUB_TIMEOUT_STYLE=menu
```
should be two lines:
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
```
Fix that, run sudo update-grub, reboot, and the menu should appear.

---

### Post by jsamiry on 2020-09-01
Sorry, Denis N, but that seems to happen when you paste stuff between codes!

Here's the grub file 

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'




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

---

### Post by dinkidonk on 2020-09-01
If GRUB does not display the menu with that config file, my suggestion is that the active GRUB belongs to a different system or is installed on a wrong drive.

---

### Post by tea for one on 2020-09-01
Your grub text looks OK to me - exactly as mine and I see the grub screen at every boot. 

It's a bit baffling but we persevere..........

Do you know the keys to press to see the boot screen or UEFI set up screen?

Do they allow you to see anything before Ubuntu starts?

Alternatively, when in Ubuntu, open a terminal and try:-

```
sudo systemctl reboot --firmware-setup
```

This will take you to your UEFI set up screens - you may see your Windows Boot manager

Also, if you have previously inserted a USB device with the Ubuntu ISO, you should see an entry for this.

---

### Post by jsamiry on 2020-09-01
Hiya,  cannot bring up the bios screens and tried your suggested instruction and received just a blank screen.  Tried using the arrow key to move down two positions.  Nothing displayed but something happened as I got a sort of Windows start up ping.  Screen still blank.

Did you see the comment that it may not be executing the config file I am looking.  Is there a way to put in some way of displaying a message so we know that it is executing the file?

jsa

---

### Post by oldfred on 2020-09-01
Can you directly boot Windows from UEFI boot menu?
And then make sure Windows fast start up is off?

If not:
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by tea for one on 2020-09-01
> **jsamiry said:**
> Hiya,  cannot bring up the bios screens and tried your suggested instruction and received just a blank screen.  Tried using the arrow key to move down two positions.  Nothing displayed but something happened as I got a sort of Windows start up ping.  Screen still blank.

Did you see the comment that it may not be executing the config file I am looking.  Is there a way to put in some way of displaying a message so we know that it is executing the file?

jsa

Still baffled, but there must be a solution.

I suspect that you cannot run boot-repair from a live session because you still cannot access your UEFI boot manager, nor boot from a USB device?

If your UEFI/BIOS screens are inaccessible either at **cold boot** or **sudo systemctl reboot --firmware-setup**, then it may be a hardware problem where the display is not activated early enough?

Yet fortunately Ubuntu still boots quite happily.....

Is this a laptop or desktop with separate monitor?

Do you have a DVD drive?

I don't remember a config file you mentioned - can you post it for us?

---

### Post by oldfred on 2020-09-01
UEFI has a fast boot setting that needs to be off.

If fast boot is on, it assumes no system changes and immediately goes to boot. You then do not have time to press any key to get into UEFI or UEFI boot menu.
Often then a cold boot from full power down forces a full normal boot and you have some time to press keys to get into UEFI or UEFI boot menu.

---

### Post by tea for one on 2020-09-01
> **oldfred said:**
> UEFI has a fast boot setting that needs to be off.

If fast boot is on, it assumes no system changes and immediately goes to boot. You then do not have time to press any key to get into UEFI or UEFI boot menu.
Often then a cold boot from full power down forces a full normal boot and you have some time to press keys to get into UEFI or UEFI boot menu.

Yes, I think you've found something positive here.

Grub screen appears before OS boots.

I had a look at my UEFI settings and following the path: **Advanced > Boot > Boot Configuration**, I found the comment concerning **Fast Boot** 

> Video and USB devices will **not** be available until [COLOR="#0000CD"]after[/COLOR] OS boot

I hope that **cold boot** works for[COLOR="#0000CD"] jsamiry[/COLOR] and that boot repair can be used if required.

Fingers crossed.

---

### Post by jsamiry on 2020-09-02
Hi,

Not sure if you are suggesting a "cold boot".  Just to confirm, I have yet to find a way to access the boot menu or to get the system to boot from a USB, so I can't implement the suggestions concerning windows.

Any further thoughts on how to confirm that the correct config file is being executed?  I was wondering if there was a way to display a message when the file is executed, though I have had a search for other config files and have found none.

As it happens, all my data is stored in the cloud so I could start all over again but I would lose the windows which I have used occasionally.  At the moment, I cannot print or scan using my HP 6960 despite assiduously installing the HP Ubuntu drivers.

Thanks for the help, anyway.

jsa

---

### Post by dinkidonk on 2020-09-02
The actual GRUB script generated by "update-grub" is stored as "/boot/grub/grub.cfg". Since this is a shell script, manually adding something like "echo foobar > /dev/shm/grub.launc" into the file could be used to test if it is actually executed. However, this would require "/dev/shm" (shared memory device) to be available during execution of the script, which I doubt since it is a kernel feature. Be careful though, a bad grub.cfg could cause the system not to boot, requiring an alternative boot media in order to fix grub.cfg.

---

### Post by tea for one on 2020-09-02
> **jsamiry said:**
> Hi,

Not sure if you are suggesting a "cold boot".  

Yes, as [COLOR="#0000CD"]oldfred[/COLOR] mentioned in post 21 - Close Ubuntu, power off, leave it for a few minutes, power on and use your known dedicated key to launch the UEFI set up pages.

Also, there may also be another way to reach the UEFI screens.

For example, this is the method for Intel:-

> Fast Boot in BIOS reduces computer boot time. With Fast Boot enabled:

    You can't press F2 to enter BIOS Setup.
    USB mice and keyboards are unavailable until after the operating system loads.

Disable Fast Boot from the power button menu. Access the power button menu with this sequence:

    Make sure the system is off, and not in Hibernate or Sleep mode.
    Press the power button and hold it down for three seconds and release it.  The power button menu should display.
    Tip: If the system boots to the OS after trying this procedure then you didn't hold the button quite long enough. If the system simply reamins off after trying this procedure, then you held the button too long (longer than 4 seconds).
    Press F3 to disable Fast Boot.

Perhaps, you can research to see if there is something similar for your PC?

---

