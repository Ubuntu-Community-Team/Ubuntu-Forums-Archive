---
title: "Ubuntu shuts down randomly"
date: 2014-06-07
forum: General Help
---

### Post by wayne16 on 2014-06-07
Hello -- New member and first time poster here. I'm having a problem with Ubuntu on my laptop. I'm running 14.04LTS in a dual-boot setup with Win7. Here's my hardware basics:

Toshiba Satellite (low-end model, going on 5 years old)
AMD Athlon II Dual-Core M300
 2.0GB RAM
 AMD M880G w/ ATI Mobility Radeon HD 4200

The systems works fine..BUT, periodically the machine will simply shut off with no warning while running Ubuntu. There's no rhyme or reason why it does this, and it's always random and unexpected. This machine never does that under Windows. Any ideas what it could be or how to find out?

Thanks

---

### Post by Impavidus on 2014-06-08
Can you find anything in the log files around the time it shuts down? Or could it be overheating? The graphics driver in particular may not be as good as on Windows, leaving the graphics card in a higher power mode than on Windows.

---

### Post by wayne16 on 2014-06-09
Thanks for that bit of help. I *think* this capture from the syslog indicates when it quit and when I restarted later. I'm wondering if a SD flash card reader plugged into a USB might have something to do with it. Can you tell? \\ wayne

Jun  7 11:22:29 telecaster ntfs-3g[2597]: Version 2013.1.13AR.1 external FUSE 29
Jun  7 11:22:29 telecaster ntfs-3g[2597]: Mounted /dev/sda2 (Read-Write, label "System", NTFS 3.1)
Jun  7 11:22:29 telecaster ntfs-3g[2597]: Cmdline options: rw,nosuid,nodev,uhelper=udisks2,uid=1001,gid=1001,dmask=0077,fmask=0177
Jun  7 11:22:29 telecaster ntfs-3g[2597]: Mount options: rw,nosuid,nodev,uhelper=udisks2,allow_other,nonempty,relatime,default_permissions,fsname=/dev/sda2,blkdev,blksize=4096
Jun  7 11:22:29 telecaster ntfs-3g[2597]: Global ownership and permissions enforced, configuration type 7
Jun  7 11:22:30 telecaster udisksd[2171]: Mounted /dev/sda2 at /media/squier/System on behalf of uid 1001
Jun  7 11:22:30 telecaster dbus[474]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Jun  7 11:22:30 telecaster dbus[474]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jun  7 11:23:27 telecaster kernel: [  732.184849] StaRateAdaptive87SE(): update init_gain to index 6 for date rate 22
Jun  7 11:23:38 telecaster kernel: [  743.547259] r8180: WW:Error: no descriptor left by previous TX (avail 4) 
Jun  7 22:52:09 telecaster rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="500" x-info="http://www.rsyslog.com"] start

---

### Post by wayne16 on 2014-06-09
I shouldn't have written "Ubuntu shuts down randomly." That's incorrect. Ubuntu doesn't shut down at all. The PC shuts off randomly while running Ubuntu...that's a better description of the problem.

---

### Post by wayne16 on 2014-06-13
I think it's a problem of overheating. I need to figure out why Ubuntu is making it run hotter.

---

### Post by whatthefunk on 2014-06-13
Install the program lm-sensors.  From the command line, run "sudo sensors-detect" to find all the temperature sensors in your machine.  Answer yes to all the questions.  Once youve done this, you can run the command "sensors" to find your temperatures.  

Given that this is a laptop, Im guessing that you are having overheating problems and that the cause may be fan control.

---

### Post by wayne16 on 2014-06-14
Yep... the PCI adapter (whatever it refers to) is way hot.

acpitz-virtual-0
Adapter: Virtual device
temp1:        +85.0°C  (crit = +105.0°C)


k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +90.0°C  (high = +70.0°C)
                       (crit = +100.0°C, hyst = +95.0°C)

---

### Post by whatthefunk on 2014-06-14
Where do you usually use the laptop?  On a table?  On your lap?  When its running, can you hear fans running or feel air moving into or out of the vents?

This seems to be a common issue.  Try going through some of these threads to see if you can find a solution that works:
[https://www.google.co.jp/search?q=toshiba+satellite+ubuntu+fan+control+site:ubuntuforums.org&gws_rd=ssl](https://www.google.co.jp/search?q=toshiba+satellite+ubuntu+fan+control+site:ubuntuforums.org&gws_rd=ssl)

---

