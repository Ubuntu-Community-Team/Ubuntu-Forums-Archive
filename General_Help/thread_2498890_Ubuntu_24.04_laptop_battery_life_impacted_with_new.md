---
title: "Ubuntu 24.04 laptop battery life impacted with newer kernels"
date: 2024-07-02
forum: General Help
---

### Post by epicpilgrim on 2024-07-02
Hi all

When I built my Dell XPS 9570 with Ubuntu 24.04, the battery life I was getting was fantastic. That was running the 6.8.0-31 kernel that comes OOTB with 24.04. Since then, both the -35 and the -36 kernels have been released. I've tried both these kernel images, and they both result in significant depletion of the battery, much quicker than -31 does. I've gone backwards and forwards between the kernels a number of times (particularly -31 and -35, but even messing around today with -36, the problem still occurs).

Where would I even look to figure out what could possibly be causing greater battery consumption in these newer kernels? I'm booting into -31 for now but I know that will have to come to an end at some point. I can only guess that some important parameter to do with timing or ACPI or something has changed, but honestly the last time I dived into Linux kernels in any depth, they started with a number 2 and were closely followed by a dot and a 4, so I'm way out of my depth nowadays.

Thanks in advance.

---

### Post by currentshaft on 2024-07-02
How are you objectively measuring "significant depletion of the battery"? What testing have you performed to reach the conclusion this has to do with the kernel? Is it possible other changes were made your system during this time?

---

### Post by Doug S on 2024-07-02
I would suggest you try the most recent upstream mainline kernel to determine if the issue has been fixed, but just hasn't propagated downstream yet.
While kernel 6.10-rc6 exists, the Ubuntu mainline compile doesn't (for AMD64), so try Ubuntu mainline [6.10-rc4]("https://kernel.ubuntu.com/mainline/v6.10-rc4/").

If it is fixed upstream, then just wait, using -31 in the meantime. If it not fixed upstream, then you would need to bisect the kernel to isolate the bad commit for reporting upstream. Typically kernel bisection takes between 15 and 20 kernel compiles, and is rather tedious.

EDIT 1: I don't think it is anything to do with kernel configuration changes:
```
doug@s19:~$ diff /boot/config-6.8.0-31-generic /boot/config-6.8.0-35-generic
3c3
< # Linux/x86 6.8.1 Kernel Configuration
---
> # Linux/x86 6.8.4 Kernel Configuration
54c54
< CONFIG_VERSION_SIGNATURE="Ubuntu 6.8.0-31.31-generic 6.8.1"
---
> CONFIG_VERSION_SIGNATURE="Ubuntu 6.8.0-35.35-generic 6.8.4"
475d474
< # CONFIG_AMD_MEM_ENCRYPT_ACTIVE_BY_DEFAULT is not set
983a983
> # CONFIG_MODULE_SIG_SHA1 is not set
2018d2017
< CONFIG_BT_HS=y
```

I also found [this]("https://forum.endeavouros.com/t/updated-system-and-now-battery-life-is-significantly-less/53756").

---

### Post by epicpilgrim on 2024-07-02
@currentshaft, I haven't taken a strictly quantitative approach to measuring this, however I have flicked back and forth between the -1 and the -5 image over the last month (and -6 over the last 24 hours) and found that battery just disappears on the newer images when I'm performing exactly the same types of work. If it were just once or twice, I'd put it down to some heavy CPU utilisation, but it's consistent, every single time I boot -5 and -6. And because I can simply reboot into -1 and have the battery usage back to how it should be, I can rule out other changes to my system being the cause (mostly).

---

### Post by epicpilgrim on 2024-07-02
@doug, Thank you, I will try both the 6.10-rc4 kernel and also the suggestions in the post you linked to and see what I can find.

---

### Post by epicpilgrim on 2024-07-02
> **Doug S said:**
> I would suggest you try the most recent upstream mainline kernel to determine if the issue has been fixed, but just hasn't propagated downstream yet.
While kernel 6.10-rc6 exists, the Ubuntu mainline compile doesn't (for AMD64), so try Ubuntu mainline [6.10-rc4]("https://kernel.ubuntu.com/mainline/v6.10-rc4/").

Ok tried this, didn't fix it.

> **Doug S said:**
> I also found [this]("https://forum.endeavouros.com/t/updated-system-and-now-battery-life-is-significantly-less/53756").

This was very interesting. I had exactly the same problem where the NVIDIA PM tuning was marked as "Bad". As soon as I hit the tuning on it, the power utilisation improved dramatically. Turn the tuning back to "bad", power utilisation sucks again.

For reference, I am using the NVIDIA 550.78 drivers from their website, not the ones that came with Ubuntu (found the official ones more stable and with better automatic power management).

So, two questions are left:
1. Why would the original kernel tune this parameter for my NVIDIA card properly, but newer kernels do not?
2. How do I make this tuning persist between reboots? The command powertop runs is "[FONT=courier new]echo 'auto' > '/sys/bus/pci/devices/0000:01:00.0/power/control'[/FONT]"

Thanks

---

### Post by Doug S on 2024-07-03
> **epicpilgrim said:**
> So, two questions are left:
1. Why would the original kernel tune this parameter for my NVIDIA card properly, but newer kernels do not?
2. How do I make this tuning persist between reboots? The command powertop runs is "[FONT=courier new]echo 'auto' > '/sys/bus/pci/devices/0000:01:00.0/power/control'[/FONT]"


1.) I don't know. I still think the kernel would have to be bisected to isolate the cause and find the answer.
2.) I create and use a systemd service to take care of custom startup stuff.

---

### Post by epicpilgrim on 2024-07-05
[FONT=arial]Thanks! I didn't have time to dig into the kernel, so I've just created a systemd service. For anyone that finds this in the future...

1. Create a script to write the appropriate setting. In my case, I wrote the following to /usr/local/bin/fix_nvidia.sh:[/FONT]
[FONT=courier new]
#!/bin/sh

[/FONT][FONT=courier new]echo 'auto' > '/sys/bus/pci/devices/0000:01:00.0/power/control'

[FONT=arial](this file can also do any/all other power tuning you desire)[/FONT]

[FONT=arial]2. Make the file executable:
[/FONT]
$ sudo chmod +x /usr/local/bin/fix_nvidia.sh

[FONT=arial]3. Create a systemd service file to execute the above. I made this /etc/systemd/system/fix_nvidia_battery.service:

[/FONT][/FONT][FONT=monospace][COLOR=#000000][Unit][/COLOR]
Description=Fix the power management on the NVIDIA card
After=multi-user.target

[Service]
ExecStart=/usr/local/bin/fix_nvidia.sh
Type=simple

[Install]
WantedBy=multi-user.target

[/FONT][FONT=courier new][FONT=arial]4. Enable the service:

[FONT=courier new]$ sudo systemctl daemon-reload
$ sudo systemctl enable fix_nvidia_battery.service[/FONT]

You're set! On reboot, it will automatically execute these commands. Not as easy as it was in my day (where is /etc/rc.local these days??) but not too hard once you get the hang of it.[/FONT][/FONT]

---

### Post by Doug S on 2024-07-05
Thanks for coming back and reporting what you did. I had meant to point to or supply an example of setting up a service but forgot.
Perhaps check every few kernel releases to see if the issue is fixed.

> **epicpilgrim said:**
> Not as easy as it was in my day (where is /etc/rc.local these days??) but not too hard once you get the hang of it.agreed.

---

### Post by raif on 2024-07-08
Interesting. I noticed this degradation with the two newer kernels you mention, after getting fantastic power consumption up to 6.8.0-31.

But using an ASUS Zenbook with integrated AMD Radeon graphics, so not an NVIDIA issue for me.

---

