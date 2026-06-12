---
title: "USB Mouse hangs randomly."
date: 2008-05-04
forum: General Help
---

### Post by phyrre on 2008-05-04
I'm having some trouble with my mouse. It hangs afaik randomly. It could be 10 mins from booting up to hours. I've tried setting noapic, irqpoll apci=force as boot options but it hasn't helped. I can plug in my keyboard in a usb slot after the mouse has hung and the keyboard still works. Replugging the mouse does not work though. The mouse works in windoze.

Any ideas?

Cheers,
Engy

---

### Post by ghost_ryder35 on 2008-05-04
> **phyrre said:**
> I'm having some trouble with my mouse. It hangs afaik randomly. It could be 10 mins from booting up to hours. I've tried setting noapic, irqpoll apci=force as boot options but it hasn't helped. I can plug in my keyboard in a usb slot after the mouse has hung and the keyboard still works. Replugging the mouse does not work though. The mouse works in windoze.
 
Any ideas?
 
Cheers,
Engy
have you tried diffrent usb ports?  is it wireless?  if it is wireless have you replaced the batteries?  resynced the mouse?

---

### Post by forrestcupp on 2008-05-04
Is it a Microsoft mouse by chance.  I'm not trying to make a joke.  I had trouble with my MS mouse being sluggish sometimes, and since I replaced it with a Logitech, I never have problems.

---

### Post by phyrre on 2008-05-05
> **ghost_ryder35 said:**
> have you tried diffrent usb ports?  is it wireless?  if it is wireless have you replaced the batteries?  resynced the mouse?

Yes, I've tried different ports. No, it's not wireless. resynced?


[QUOTE=forrestcupp] Is it a Microsoft mouse by chance. I'm not trying to make a joke. I had trouble with my MS mouse being sluggish sometimes, and since I replaced it with a Logitech, I never have problems.[/QUOTE]

No, it's a G3 from logitech

---

### Post by phyrre on 2008-05-05
Bump. Anyone? My USB -> ps2 thing doesn't seem to work so I really  need to fix this.

---

### Post by KeyserSoze93 on 2008-05-05
Try it with only the mouse plugged in - you may have another device using all your usb bandwidth. I has a camera which wouldn't give me  a smooth video when I had other usb devices plugged in.

---

### Post by Leesh on 2008-05-05
> **forrestcupp said:**
> Is it a Microsoft mouse by chance.  I'm not trying to make a joke.  I had trouble with my MS mouse being sluggish sometimes, and since I replaced it with a Logitech, I never have problems.
I use a **Microsoft Comfort Optical Mouse 1000** with Ubuntu 8.04 and it works really great. I don't think that only Microsoft mice sometimes can't correctly work. I had some mice, that had bugs both in Windows and Linux operating environments.

By the way, does the Logitech G3 require an additional driver in Windows?

---

### Post by phyrre on 2008-05-05
> **KeyserSoze93 said:**
> Try it with only the mouse plugged in - you may have another device using all your usb bandwidth. I has a camera which wouldn't give me  a smooth video when I had other usb devices plugged in.

I only have the usbmouse connected. I have my keyboard connected through a usb -> ps2 "dongle".

[QUOTE=leesh]
I use a Microsoft Comfort Optical Mouse 1000 with Ubuntu 8.04 and it works really great. I don't think that only Microsoft mice sometimes can't correctly work. I had some mice, that had bugs both in Windows and Linux operating environments.

By the way, does the Logitech G3 require an additional driver in Windows? 
[/QUOTE]
Nope. I don't use any drivers in windoze.

---

### Post by Leesh on 2008-05-05
> **phyrre said:**
> I only have the usbmouse connected. I have my keyboard connected through a usb -> ps2 "dongle".


Nope. I don't use any drivers in windoze.
In this case, the problem might be in an application, that tries to do something using the USB port. Maybe there is something with the mouse driver in Ubuntu (an error or just a crash). Anyway, if this is possible, try this mouse on other Ubuntu machines, if nearby.

---

### Post by phyrre on 2008-05-06
> **Leesh said:**
> In this case, the problem might be in an application, that tries to do something using the USB port. Maybe there is something with the mouse driver in Ubuntu (an error or just a crash). Anyway, if this is possible, try this mouse on other Ubuntu machines, if nearby.


Hmm, ok. No, I don't have access to another ubuntu comp.

---

### Post by phyrre on 2008-05-06
Dunno if this is related but now when I start ubuntu it goes straight to cli instead of the login window. I prefer it this way but I did not change anything. Something is up. =(

[quote="lsmod"]
engy@sabbath:~$ lsmod
Module                  Size  Used by
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
vmix                   17464  3 
sbxfi                  35392  7 
osscore               594528  4 vmix,sbxfi
ppdev                  11400  0 
powernow_k8            16608  0 
cpufreq_conservative    10632  0 
cpufreq_userspace       6180  0 
cpufreq_powersave       3200  0 
cpufreq_ondemand       11152  1 
cpufreq_stats           8416  0 
freq_table              6464  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
dock                   12960  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
video                  23444  0 
output                  5632  1 video
container               6656  0 
battery                16776  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ac                      8328  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
loop                   21508  0 
ipv6                  311720  10 
serio_raw               9092  0 
psmouse                46236  0 
pcspkr                  4992  0 
k8temp                  7680  0 
evdev                  14976  4 
nvidia               8858052  34 
button                 10912  0 
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
ehci_hcd               41996  0 
i2c_nforce2             8704  0 
i2c_core               28544  2 nvidia,i2c_nforce2
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sd_mod                 33280  8 
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
usbhid                 35168  0 
hid                    44992  1 usbhid
sata_nv                31624  5 
pata_amd               16772  0 
ata_generic             9988  0 
floppy                 69096  0 
r8169                  36612  0 
pata_acpi               9856  0 
libata                176304  4 sata_nv,pata_amd,ata_generic,pata_acpi
scsi_mod              178488  4 sd_mod,sg,sr_mod,libata
ohci_hcd               27524  0 
forcedeth              55564  0 
usbcore               169904  4 ehci_hcd,usbhid,ohci_hcd
thermal                19744  0 
processor              41448  2 powernow_k8,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  9
[/quote]

---

### Post by Leesh on 2008-05-06
> **phyrre said:**
> Dunno if this is related but now when I start ubuntu it goes straight to cli instead of the login window. I prefer it this way but I did not change anything. Something is up. =(
Here is just a simple question: have you ever installed Ubuntu on this machine? If yes, how the mouse was working in that environment?

---

### Post by phyrre on 2008-05-06
> **Leesh said:**
> Here is just a simple question: have you ever installed Ubuntu on this machine? If yes, how the mouse was working in that environment?

Yeah. I had 7.10 earlier, It ran fine up until I was going to install 8.04 at which point it started to act up like 8.04 does now. The only thing I remember changing was adding 1 gb ram from another computer. I'm currently running without the extra ram but the USB Mouse is still hanging.

---

