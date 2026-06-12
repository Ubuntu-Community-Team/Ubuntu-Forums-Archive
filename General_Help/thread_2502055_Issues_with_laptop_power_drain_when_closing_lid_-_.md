---
title: "Issues with laptop power drain when closing lid - secure boot enabled (Dual Boot)"
date: 2024-10-31
forum: General Help
---

### Post by vw16v on 2024-10-31
Hello, I've been noticing issues recently when I close my lid on my laptop with 50% power or so and then when I go to open the lid the next day after I was using Ubuntu it has drained the entire battery! I'm not sure when this first started happening? I checked and confirmed I do not have hibernation enabled. 

I'm not sure if this is related but I'm seeing this entries in my journal logs:
```

Oct 31 09:44:54 yoga9i kernel: PM: hibernation: Registered nosave memory: [mem 0xfed20000-0xfed7ffff]
Oct 31 09:44:54 yoga9i kernel: PM: hibernation: Registered nosave memory: [mem 0xfed80000-0xffffffff]

Oct 31 09:03:39 yoga9i kernel: Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7
Oct 31 09:03:51 yoga9i kernel: Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7
```

What I did so far is follow [this information]("https://ubuntuhandbook.org/index.php/2020/05/lid-close-behavior-ubuntu-20-04/").
That is I removed the # sign from these two entries. 
sudo vi /etc/systemd/logind.conf
HandleLidSwitch=suspend
HandleLidSwitchExternalPower=suspend

I have my doubts that this will help. I don't know why it's sucking so much power when I close the lid? I see the power light on my laptop blinking indicating it should be resting but I have yet to test further after adding these entries.

I'm not sure if I have to rebuild my swap file or something to enable hibernation? I don't know if the suspend operation above requires hibernation to work? 

I was debating on trying to following [this thread]("https://ubuntuhandbook.org/index.php/2021/08/enable-hibernate-ubuntu-21-10/") to enable hibernation. I just want my laptop to not drain all the power when I shut the lid.

 sudo systemctl hibernate
Call to Hibernate failed: Sleep verb 'hibernate' is not configured or configuration is not supported by kernel

Thanks for any ideas or help!

---

### Post by vw16v on 2024-10-31
A few other notes I just confirmed. Per an article I just read it states Ubuntu typically has hibernation disabled by default. Also, the article I have read said the normal operation in Ubuntu when shutting the lid on laptop is suspend. So, I don't believe this is related to my draining issues. However, it does appear that enabling hibernation on laptop lid close would provide the most power savings. I just confirmed how my suspend operation is setup by running this command.

cat /sys/power/mem_sleep
[s2idle] deep

Another individual mentioned having this issue way back on 18.04. I also just changed my USB settings in BIOS to disable charging USB when lid is closed. I don't think this will matter since I don't have any USB devices plugged in. I make sure and disconnect my HDMI to my TV before shutting the lid. What I'm trying to do next is possible get the "suspend" to this mode. 
*Standby* (**shallow**)

[Reference]("https://askubuntu.com/questions/1398674/battery-drain-during-suspend-mode-when-lid-is-closed-20-in-8-hours"): 
*Suspend to idle* (**s2idle**) uses the most power. "User space" is frozen, and I/O devices are put in low power state.
 *Standby* (**shallow**) involves suspension of some more low level functions, with more power savings.
 *Suspend-to-RAM* (**deep**) offers  more significant savings: essentially only the RAM is kept powered to  keep RAM contents and the state of the devices and CPU stored in RAM.

If anyone has experience with this issue please let me know. I will post back what I discover and I research and test. Thanks for any input.

---

### Post by vw16v on 2024-11-01
Hello, I just did some more research on this. What I'd like to try is changed from *Suspend to idle* (**s2idle**) to *Standby* (**shallow**). I'm hoping if I do this I might have better results with the system suspending properly. I don't know what happened but Ubuntu used to power down to a deep sleep after the lid was shut for a while. Typically when I open the Lid on my laptop (which I have set in the BIOS to set system to sleep upon lid close) it will boot to GRUB again instead of Windows or Ubuntu that I shut the lid on beforehand. When it does this it retains the battery power which is what I want.

Here's what I want to try. Do you think this might cause issues with my Dual boot or anything? This is what Brave AI returns for changing the standby state. I want to make sure I can revert this if I encounter any issues. I would imagine I could access GRUB upon boot to change the original value instead of "mem_sleep_default=shallow". Right now I have GRUB_CMDLINE_LINUX_DEFAULT="quiet splash". Thanks for any ideas!


[LIST=1]
[*]**Check your system&#8217;s current suspend behavior**:
[LIST]
[*]Run the command cat /sys/power/state to see the current suspend options. If you see only freeze and mem, your system is currently using suspend-to-idle (S2I) and suspend-to-RAM (S3) respectively. 
[/LIST]
  
[*]**Configure the kernel to use standby (shallow)**:
[LIST]
[*]Edit the file /etc/default/grub using a text editor (e.g., sudo nano /etc/default/grub) and add the following line at the end: 
[/LIST]
  
[/LIST]
GRUB_CMDLINE_LINUX_DEFAULT=[COLOR=#A5D6FF]"mem_sleep_default=shallow"[/COLOR]


* Save the changes and update GRUB:


[COLOR=#FFA657]sudo[/COLOR] update-grub



[LIST=1]
[*]**Verify the changes**:
[LIST]
[*]Run cat /sys/power/state again to confirm that the output now includes shallow as an option. 
[/LIST]
  
[/LIST]
[COLOR=#DADFE1][FONT=Inter]**Note:** If you&#8217;re using a newer kernel version (e.g., 5.15 or later), you might need to use the mem_sleep file instead:[/FONT][/COLOR][COLOR=#FFA657]sudo[/COLOR] [COLOR=#FFA657]echo[/COLOR] shallow > /sys/power/mem_sleep

---

### Post by vw16v on 2024-11-03
Hello.. If anyone has any ideas why Ubuntu Suspend drains power quickly I would appreciate it. While the lid was closed today the system was still somewhat on because I heard the sound for critical battery again! Then I opened the lid and it was almost dead when I closed it 12hrs ago with 60%. I just mainly want to verify if running this command will cause any issues with my Dual boot? 
sudo update-grub
I want to try to change from Suspend to idle (s2idle) to Standby (shallow) suspend mode. I'm hoping that will allow it to go back to how it used to suspend. Thanks for any ideas.

---

### Post by vw16v on 2024-11-07
FYI, I'm going to hold off trying to change from  idle (s2idle) to Standby (shallow) suspend mode for now. I noticed when I closed the lid yesterday at about 85% I still had about 34% left some 12hrs later after going into suspend via idle (s2idle) mode. If anyone else uses this suspend mode can you let me know how quickly your battery drains in this mode? Thanks

---

