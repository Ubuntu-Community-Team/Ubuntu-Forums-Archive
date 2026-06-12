---
title: "Problem with grub on old laptop"
date: 2013-04-25
forum: General Help
---

### Post by mappuso on 2013-04-25
Hello everyone,
I've installed lubuntu 12.04 on a old laptop. I need to add "nolapic" boot parameter otherwise system doesn't boot (system remains on, but freezed in black screen). To make this boot parameter permanent I've modified /etc/default/grup file as follow
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic"
and then I've done "update-grub" command

Everything seems to work, but after the restart of the system no grub menu is presented to me and the system remains on with the black screen (like when I try to boot without the "nolapic"). I have to physically turn off the laptop and turn it back on. In this way, in fact grub menu is presented to me, and choosing the first option, the system can boot successfully,  but when I restart the problem recurs.

Please help me :)
thanks

---

### Post by oldfred on 2013-04-25
Are you perhaps rebooting too quickly?

If you only have one system, the grub menu is not normally shown. It only then shows if you have boot errors, so by stopping it, it will then show menu.

It is normal to have a cursor or black line for a bit as it is booting. And if an older system it may be a bit longer before it does boot.

You can try removing quiet splash and sudo update-grub. Then you will see the boot process. Or you can look in the log files to see if they show any errors.

---

### Post by mappuso on 2013-04-26
> **oldfred said:**
> Are you perhaps rebooting too quickly?

If you only have one system, the grub menu is not normally shown. It only then shows if you have boot errors, so by stopping it, it will then show menu.

It is normal to have a cursor or black line for a bit as it is booting. And if an older system it may be a bit longer before it does boot.

You can try removing quiet splash and sudo update-grub. Then you will see the boot process. Or you can look in the log files to see if they show any errors.

It Is not a matter of time, because when the boot process fails after a few seconds also the cursor disappears and the screen goes black as if it is turned off and not powered (aven if laptop continues to be powered). As soon as I can I try to remove "quiet splash" and I will let you know. 
thanks

---

### Post by mappuso on 2013-04-26
I've removed "quiet splash", but on the characters appears something that is not readable. If I add the boot parameter "acpi = off" system start, but the sound card does not work and after the shutdown I'have to turn off manually the laptop to complete. Also in this case, once rebooted I get the menu group and choosing "Ubuntu, with Linux 3.2.0-40-generic" the system administrator starts normally everything works. 

I should understand what are the boot parameters that allow the departure of the system, but how do this? 
Is there any log file that I can send you to you make a more precise analysis? 

Or if I could always boot the system with the parameters that are used when I choose "Ubuntu, with Linux 3.2.0-40-generic" perhaps it would be a good work around.

help :(!

thanks.

---

### Post by oldfred on 2013-04-26
If you have the abnormal or forced shutdown then grub will show a menu as it knows you had issues and may need recovery mode.
Is the boot entry you use the first one? 

If you use the e on the grub menu you will see the boot parameters. But unless you permanently have added some to /etc/default/grub it should just be the splash quiet. Recovery mode removes splash quiet and adds nomodeset. Have not looked lately if anything else in recovery mode entry. 

No need to post entire log file as it is huge. But I do use Log File Viewer and look for entries in dmesg with errors, warnings, repeated tries at loading a driver (sometime it may eventually work or not), or just an entry with a very long time to next entry. There also are many other log files in /var/log.

My system boots in about 12sec from an older SSD. It is about 40 sec from my hard drive installs.

>      [3.732145] usbhid: USB HID core driver
[    5.959888] EXT4-fs (sdd3): mounted filesystem with ordered data mode. Opts: (null)
[    8.161520] Adding 3076412k swap on /dev/sdc11.  Priority:-1 extents:1 across:3076412k 



But I can see it loses about 2 sec time loading file system and swap, but I expect that is normal but those are 1/3 of my entire boot time.

---

### Post by mappuso on 2013-04-26
The reboot entry in the grub menu that I use is the first and it's ok, but  on the next reboot, grub menu is not presented to me and the the system doesn't boot. I've searched the errors in logs, but I didn't find anything, but I'm not expert.

---

### Post by oldfred on 2013-04-26
That you do not get grub menu is normal with only one system installed.

You should be able to hold shift from BIOS until menu appears. If you do that does it boot first time?

Perhaps BIOS does not bring drive up quick enough?

---

### Post by mappuso on 2013-04-26
1. If I don't press shift menu doesn't appears and the system remains in black screen "frozen", but turned on. 
2. To reboot I have to turn off manually the system pressing (for a 4-5 second) the power button on the laptop.
3. After last step menu appears to me. If I select the first entry [COLOR=#000000]"Ubuntu, with Linux 3.2.0-40-generic" the system start correctly.
[/COLOR]4. but on the next reboot I return on step 1.

If on the step 1 press "shift" menu appears to me, but if I chose the first entry (the same choice of step 3), system remains in black screen "frozen" (like step 1).

[COLOR=#000000]I've removed "quiet splash" and a[/COLOR]nother strange thing is that in the step 1 while system is trying to boot unreadable signs appears on the screen, instead in the step 3 while system is booting I can read everything on the screen and after few second (more or less 30), [COLOR=#000000]the system start correctly.[/COLOR]

---

### Post by oldfred on 2013-04-26
I am out of ideas.

But you never should power off unless it is last option. Remember the elephants. But then I do not think you will get grub menu unless you do it yourself. 

       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

On newer systems some have had to use these settings. You could try adding them to 
 gksudo gedit /etc/default/grub

 rootdelay=90 reboot=a,w

---

### Post by mappuso on 2013-04-27
Maybe I've found a work around... I've added "nolapic" and "nomodeset" boot parameters and now system boot (more or less) correctly, infact when system boot (without [COLOR=#000000] "quiet splash" parameter) I'm not able to read anything because on the screen appears unreadable signs, but when the screen seems crazy (after about 30 seconds) graphic login is presented to me [/COLOR]as if nothing had happened :). I was forgetting to say that my laptop is an old Asus M2400N bought in 2004.

---

### Post by oldfred on 2013-04-27
What video is it?

 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root

---

### Post by mappuso on 2013-05-04
> **oldfred said:**
> What video is it?

 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root

**rosa@laptop:~$ sudo lshw -c display**
[sudo] password for rosa: 
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f0000000-f7ffffff memory:ffa80000-ffafffff ioport:dc00(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:e8000000-efffffff memory:ff980000-ff9fffff

**rosa@laptop:~$ sudo lshw | grep -A 11 display**
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff memory:ffa80000-ffafffff ioport:dc00(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:e8000000-efffffff memory:ff980000-ff9fffff

**rosa@laptop:~$ lspci | grep VGA**
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

**rosa@laptop:~$ xwininfo -root**
xwininfo: Window id: 0x131 (the root window) (has no name)
Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1024
  Height: 768
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: ForgetGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1024x768+0+0

**rosa@laptop:~$**

---

### Post by oldfred on 2013-05-04
My laptop with Intel just works.
Some do need this in place of nomodeset:
  Older Intel video card: i915.modeset=1 or i915.modeset=0 
newer:  i915.i915_enable_rc6=1


 How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

---

