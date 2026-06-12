---
title: "Too much ram being used?"
date: 2008-02-26
forum: General Help
---

### Post by ep2011 on 2008-02-26
I Have a question about ram usage and how much should averagely be used... Right now, I use Gutsy with openbox (from repositories). It uses about ~200 mb of ram after startup, and loads by default Pidgin, and SCIM (for typing in chinese). What I don't get is that my laptop, using the same configuration (maybe not SCIM), uses about ~40mb less ram than this computer. Anyone have input on why? Is there anything I should do to slim down ubuntu or openbox?

---

### Post by SpaceTeddy on 2008-02-26
200 mybte is really low for a full operating system not using any swap. i would not really worry about it.
As for the difference, it could be anything from resolution different drivers for the hardware that take more or less ram. There might also be different background programms running...

i would worry if it ever went over a gig... THAT would be a lot... but that is a tought one to crack when you are not aiming for it

---

### Post by ep2011 on 2008-02-26
Well 200 is a lot for a light window manager like openbox... I've seen screenshots of people having 90ish and really low

---

### Post by thedaemon on 2008-02-26
Openbox doesn't use that much on my setup. I have pidgin, gnome desklets, epiphany, and blender running while using around 200mb. :\ What processes are running? Is this a fresh install? SCIM maybe using that extra ram. I haven't gotten over 300mb of ram usage in openbox though.

---

### Post by Crafty Kisses on 2008-02-26
> **ep2011 said:**
> I Have a question about ram usage and how much should averagely be used... Right now, I use Gutsy with openbox (from repositories). It uses about ~200 mb of ram after startup, and loads by default Pidgin, and SCIM (for typing in chinese). What I don't get is that my laptop, using the same configuration (maybe not SCIM), uses about ~40mb less ram than this computer. Anyone have input on why? Is there anything I should do to slim down ubuntu or openbox?

Not sure, post the following output:
```
top
```

---

### Post by ep2011 on 2008-02-26
> **thedaemon said:**
> Openbox doesn't use that much on my setup. I have pidgin, gnome desklets, epiphany, and blender running while using around 200mb. :\ What processes are running? Is this a fresh install? SCIM maybe using that extra ram. I haven't gotten over 300mb of ram usage in openbox though.
Look below for the top command... This is not a fresh install, I installed it when Gusty was released. SCIM doesn't seem to be using too much ram, I don't see how it got this high though running basically nothing. Thanks for your input... Hopefully you can help look at my top command and figure out why.. I'll post my autostart.sh file as well:

```
#!/bin/sh
# Auto-mounting drives 
gnome-volume-manager & 
# GTK themes... this is just one method 
gnome-settings-daemon & 
eval `cat $HOME/.fehbg` &
(sleep 5 && pypanel) &
(sleep 6 && pidgin) &
(sleep 6 && conky) &
```

Do you use gnome-volume-manager or gnome-settings-daemon? I was thinking about removing those, I don't know if they are necessary though. The auto-mounting drives seems very helpful since I use a flashdrive pretty often, and the gtk-themes because I use tons of GTK applications.

> **Codename said:**
> Not sure, post the following output:
```
top
```

```
eric@eric-desktop:~$ top

top - 18:48:12 up  5:00,  2 users,  load average: 0.33, 0.24, 0.29
Tasks: 112 total,   1 running, 111 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3%us,  0.2%sy,  0.0%ni, 98.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1027260k total,   934968k used,    92292k free,    10364k buffers
Swap:  1044184k total,     7464k used,  1036720k free,   663908k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 5756 root      15   0  360m  27m 5028 S    2  2.7   4:48.00 Xorg                                                                                            
 2209 root      10  -5     0    0    0 S    0  0.0   0:17.41 scsi_eh_0                                                                                       
 7332 eric      15   0  2368 1168  876 R    0  0.1   0:00.02 top                                                                                             
    1 root      15   0  2948 1856  532 S    0  0.2   0:01.38 init                                                                                            
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                     
    4 root      34  19     0    0    0 S    0  0.0   0:00.04 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                     
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1                                                                                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                      
    9 root      10  -5     0    0    0 S    0  0.0   0:00.02 events/0                                                                                        
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1                                                                                        
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                         
   31 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                                                                                       
   32 root      11  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                                       
   33 root      12  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                          
   34 root      13  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                    
  130 root      13  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                         
  155 root      15   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                         
  156 root      15   0     0    0    0 S    0  0.0   0:00.23 pdflush                                                                                         
  157 root      10  -5     0    0    0 S    0  0.0   0:00.15 kswapd0                                                                                         
  208 root      13  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                           
  209 root      14  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                           
 2032 root      10  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                   
 2033 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                           
 2109 root      10  -5     0    0    0 S    0  0.0   0:04.36 ata/0                                                                                           
 2110 root      10  -5     0    0    0 S    0  0.0   0:00.06 ata/1                                                                                           
 2111 root      16  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                         
 2131 root      10  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt                                                                                        
 2210 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                                                       
 2238 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                                                       
 2239 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                                                       
 2268 root      10  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0                                                                                     
 2505 root      10  -5     0    0    0 S    0  0.0   0:00.09 kjournald                                                                                       
 2714 root      21  -4  3036 1388  408 S    0  0.1   0:00.43 udevd                                                                                           
 3714 root      15  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused                                                                                       
 3787 root      20  -5     0    0    0 S    0  0.0   0:00.00 ivtv0/0                                                                                         
 3788 root      19  -5     0    0    0 S    0  0.0   0:00.00 ivtv0/1                                                                                         
 3908 root      20  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_4                                                                                       
 3909 root      10  -5     0    0    0 S    0  0.0   0:00.74 usb-storage                                                                                     
 3998 root      10  -5     0    0    0 S    0  0.0   0:00.59 rt61pci                                                                                         
 4455 root      10  -5     0    0    0 S    0  0.0   0:00.32 kjournald                                                                                       
 4693 root      18   0  1692  516  448 S    0  0.1   0:00.00 getty                                                                                           
 4694 root      18   0  1696  516  448 S    0  0.1   0:00.00 getty                                                                                           
 4696 root      18   0  1692  516  448 S    0  0.1   0:00.00 getty                                                                                           
 4698 root      18   0  1692  516  448 S    0  0.1   0:00.00 getty                                                                                           
 4700 root      18   0  1696  516  448 S    0  0.1   0:00.00 getty                                                                                           
 4701 root      18   0  1696  516  448 S    0  0.1   0:00.00 getty                       
```

Thank you :)

---

### Post by skymera on 2008-02-26
yeah 200mb is a lot for that setup.

i can run standard ubuntu with gnome.

at 100mb RAM usage (have a screeenshot somewhere :P)

type ```
 top 
``` to see whats eating RAM up

---

### Post by ep2011 on 2008-02-26
> **skymera said:**
> yeah 200mb is a lot for that setup.

i can run standard ubuntu with gnome.

at 100mb RAM usage (have a screeenshot somewhere :P)

type ```
 top 
``` to see whats eating RAM up

look right above your post...

---

I really don't know why... I disabled SCIM but it only shaved about ~20 megs off, I didn't restart though so maybe it is more? I know this isn't the linux way of thinking, but would a reinstall be the best way to fix it? or can anyone tell from the TOP command why so much ram is being used?

---

### Post by skymera on 2008-02-26
> **ep2011 said:**
> look right above your post...



look at the times.
we posted at the same time.

---

### Post by regomodo on 2008-02-26
200MB is a lot for openbox (if it's being used on its own, not with gnome)

My laptop with openbox, pypanel, pidgin, and rutilt will use about 45MB (my icewm setup uses ~20MB on login).

Have you loaded kde and gnome services when logging in? That'd do it.

---

### Post by ep2011 on 2008-02-26
> **regomodo said:**
> 200MB is a lot for openbox (if it's being used on its own, not with gnome)

My laptop with openbox, pypanel, pidgin, and rutilt will use about 45MB (my icewm setup uses ~20MB on login).

Have you loaded kde and gnome services when logging in? That'd do it.

All I have loaded are "gnome-settings-daemon" and "gnome-volume-manager" which set up GTK themes and automounts... that would do it? I am using straight openbox and no gnome... I'll try loading without those and see if it will make a difference.

edit: without those two things, it still uses exactly 240 megs of ram after booting... I have gnome installed but I choose the openbox option which doesn't use a desktop environment... Just openbox

edit2: those two programs add 9 megs of ram, which still doesn't explain the extremely high amount... All you people with a low amount of ram, do you use the CLI version of ubuntu and then install openbox? or is it the same as installing openbox and just running that?

---

### Post by ep2011 on 2008-02-26
Does anyone have any ideas or thoughts of why this is happening and how to free up some ram? I'm using openbox to save ram, not to be using so much of it...

---

### Post by regomodo on 2008-02-27
you may want to see what running services you have. Install rconf and pick through what you want and don't want. Be careful!

Using a cli system to install openbox, etc shouldn't make a difference. I installed openbox after having kde,xfce,gnome all on the same laptop.

---

### Post by ep2011 on 2008-02-27
> **regomodo said:**
> you may want to see what running services you have. Install rconf and pick through what you want and don't want. Be careful!

Using a cli system to install openbox, etc shouldn't make a difference. I installed openbox after having kde,xfce,gnome all on the same laptop.

Theres no package in the respiratory that is called rconf...  Is it not in the respiratory?

---

