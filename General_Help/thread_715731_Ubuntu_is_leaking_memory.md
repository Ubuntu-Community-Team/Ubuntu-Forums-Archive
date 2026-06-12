---
title: "Ubuntu is leaking memory"
date: 2008-03-05
forum: General Help
---

### Post by ubanto on 2008-03-05
I have a problem with 7.10 on an amd64 system. At startup 335MB are in use already (which seems too much anyway), and then after some time of work (with usually claws mail, pidgin, one openoffice document, and sometimes one firefox window), it goes up to 100% (I have 1GB).
I thought it might have something to do with the shared memory of the graphic chip (in my case a Nv 6150), but that doesn't justify the gap between the sum of the used memory from the process list, and the overall percentage shown in the resources.
I'm currently at 551 and rising. and I only have opened firefox (this page only, no other tab), pidgin and claws-mail.
Rised to 571 while typing.
Any idea?

---

### Post by PmDematagoda on 2008-03-05
Please post the output of:-
```
top
```

---

### Post by mali2297 on 2008-03-05
Copy/paste this into the terminal:
```

ps h -eo pmem,comm | sort -nr | head

```
You will then get a list of the ten most memory-consuming processes.

---

### Post by ubanto on 2008-03-05
This is current 'top'

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND 
6973 root      15   0  179m 108m  49m S  1.3 11.2   2:19.05 Xorg


however currently I'm not stuck (I'm again around 50% and have rebooted many times since this morning). I'll try as soon as I'm slowed again and will post the result.

---

### Post by ubanto on 2008-03-05
Now I'm stuck:
From System monitor: 934 MB used (rising)
most demanding process: Firefox 85.00MB (the second being emerald at 9.1MB)

PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND 
 7879 anto      15   0  237m  21m  16m S 11.6  2.3   0:03.83 gnome-system-mo    
 6973 root      15   0  216m  92m  44m S  1.3  9.5   3:42.96 Xorg               
 7150 anto      15   0  897m 634m 631m S  0.7 65.3   1:27.26 compiz.real        
 5086 haldaemo  16   0 23992  728  664 S  0.3  0.1   0:00.59 hald-addon-stor    
 7269 anto      16   0  543m  12m 9740 S  0.3  1.3   0:02.25 pidgin             
 7584 anto      15   0  304m  10m 8420 S  0.3  1.0   0:01.98 gnome-terminal

---

### Post by TurboRush on 2008-03-05
Run the free command...

```
free
```

I don't have access to a Linux system so I can't show you the output right now, but essentially you get 3 lines of output

1. Real memory
2. Buffers/cache
3. Swap

Linux holds frequently used items in memory so that they can be accessed quickly... what this means is it may look like you are chewing almost all of your memory over time...

What you should look at line #2.. that will tell you what is actually being used by programs and what is really available.

If you have a zero on line 3 then you are not swapping and your system is not really memory constrained.

---

### Post by mali2297 on 2008-03-05
> **ubanto said:**
> Now I'm stuck:
From System monitor: 934 MB used (rising)
most demanding process: Firefox 85.00MB (the second being emerald at 9.1MB)

PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND 
 7879 anto      15   0  237m  21m  16m S 11.6  2.3   0:03.83 gnome-system-mo    
 6973 root      15   0  216m  92m  44m S  1.3  9.5   3:42.96 Xorg               
 [color="Red"]7150 anto      15   0  897m 634m 631m S  0.7 65.3   1:27.26 compiz.real[/color]        
 5086 haldaemo  16   0 23992  728  664 S  0.3  0.1   0:00.59 hald-addon-stor    
 7269 anto      16   0  543m  12m 9740 S  0.3  1.3   0:02.25 pidgin             
 7584 anto      15   0  304m  10m 8420 S  0.3  1.0   0:01.98 gnome-terminal

The problem seems to be related to Compiz.

---

### Post by ubanto on 2008-03-05
Free says  

           total       used       free     shared    buffers     cached
Mem:        996016     986840       9176          0      33124     167940
-/+ buffers/cache:     785776     210240
Swap:      2048276      61456    1986820

As you see I'm getting close to the stuck-point again (I just restarted gnome after last post).
top:

PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 8517 anto      15   0  237m  21m  15m R 12.3  2.2   0:16.63 gnome-system-mo    
 7922 root      15   0  189m 120m  59m S  3.0 12.3   1:56.54 Xorg               
 8485 anto      15   0  282m  24m  12m S  0.7  2.5   0:00.81 gnome-terminal     
 8112 anto      15   0  118m  10m 6652 S  0.3  1.1   0:03.48 emerald            
 8249 anto      15   0  596m  95m  24m S  0.3  9.9   2:35.39 firefox-bin        
 8526 anto      15   0 18952 1328  972 R  0.3  0.1   0:00.11 top                
    1 root      18   0  5116  404  328 S  0.0  0.0   0:00.74 init   

Reason why compiz appears that bloated in post above may be that I just had used scale to switch between terminal and firefox. I did a couple of tries and I see it peaks sometimes, but is normally below zero%.

It's now 850MB and growing + 62MB Swap according to system monitor.
I'll have to restart X in a few minutes.

---

### Post by mali2297 on 2008-03-05
Post the output of the command that I gave in post #3.

---

### Post by ubanto on 2008-03-05
> **mali2297 said:**
> Post the output of the command that I gave in post #3.

Here's the result, Mali2297
11.0 compiz.real
 9.4 Xorg
 6.5 firefox-bin
 4.3 deskbar-applet
 3.7 gnome-panel
 3.0 pidgin
 2.7 gnome-terminal
 2.1 nautilus
 2.0 gnome-system-mo
 1.8 claws-mail
However I just restarted x. This time it started with 440MB and 60MB swap already used (worst than usual 330MB + 0swap).

---

### Post by mali2297 on 2008-03-05
> **ubanto said:**
> Here's the result, Mali2297
11.0 compiz.real
 9.4 Xorg
 6.5 firefox-bin
 4.3 deskbar-applet
 3.7 gnome-panel
 3.0 pidgin
 2.7 gnome-terminal
 2.1 nautilus
 2.0 gnome-system-mo
 1.8 claws-mail
However I just restarted x. This time it started with 440MB and 60MB swap already used (worst than usual 330MB + 0swap).

I still think it is Compiz that consumes your memory, 11% at start seems much. Check it again with the same command when the used memory starts climbing.

---

### Post by ubanto on 2008-03-05
This way it looks like compiz grows during normal operations.

34.4 compiz.real
11.3 Xorg
 7.7 firefox-bin
 4.4 deskbar-applet
 3.8 gnome-panel
 3.0 pidgin
 2.7 gnome-terminal
 2.2 gnome-system-mo
 2.1 nautilus
 2.0 claws-mail

---

### Post by tech9 on 2008-03-05
> **mali2297 said:**
> Copy/paste this into the terminal:
```

ps h -eo pmem,comm | sort -nr | head

```You will then get a list of the ten most memory-consuming processes.


nice command :)

---

### Post by ubanto on 2008-03-05
current ps h -eo pmem,comm | sort -nr | head
36.3 compiz.real
11.7 Xorg
 7.9 firefox-bin
 4.4 deskbar-applet
 3.8 gnome-panel
 3.0 pidgin
 2.7 gnome-terminal
 2.2 gnome-system-mo
 2.1 nautilus
 2.0 claws-mail

current top
   PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 8959 anto      15   0  238m  21m  15m S 11.0  2.3   0:35.43 gnome-system-mo    
 8583 root      15   0  185m 114m  55m S  6.3 11.8   1:39.39 Xorg               
 8778 anto      15   0  590m 369m 310m S  0.3 38.0   0:59.58 compiz.real        
 8938 anto      15   0  303m  26m  13m R  0.3  2.8   0:00.75 gnome-terminal     
 9119 anto      15   0 19076 1328  972 R  0.3  0.1   0:00.06 top                
    1 root      18   0  5116  404  328 S  0.0  0.0   0:00.74 init   

current free
                    total       used       free     shared    buffers     cached
Mem:        996016     985432      10584          0      27640     175652
-/+ buffers/cache:     782140     213876
Swap:      2048276      66040    1982236


According to system monitor we're at 780MB used (+64swap) and compiz is rated 60MB (firefox rated 80MB).

I'm starting to be confused by the differences.
However thank you for your continuous input and presence, Mali.

---

### Post by mali2297 on 2008-03-05
I don't know why it doesn't show in the system monitor, but the outputs of ps and top are consistent: it's Compiz that consumes the memory.

You mentioned something about shared memory of the graphic chip, I don't know what that means but it might be worth looking into.

---

### Post by ubanto on 2008-03-06
> **mali2297 said:**
> I don't know why it doesn't show in the system monitor, but the outputs of ps and top are consistent: it's Compiz that consumes the memory.

You mentioned something about shared memory of the graphic chip, I don't know what that means but it might be worth looking into.

ps and top are not always consistent (compiz.real is not even in the list of 'top', unless I recently used Scale), however by shared memory I just meant that the GPU doesn't have its own VRAM but draws from the system RAM. However the Nvidia 6150 cannot manage more than 128MB, so that would be the limit that it can keep occupied. And then what is really strange is this constant rise in memory usage. Anyway, I tried to disable compiz completely to see what happens.Of course I had lower memory consumption at the start (250MB vs the 330MB with compiz), Now we're at 358MB, It seems that stopping compiz didn't stop the unreasonable growth. My impression is that the system keeps considering 'in use' the memory that has been used for processes and applications that are closed, compiz being one of the most consuming, so what I would expect is I will be stuck again but it will simply take more time with compiz disabled. I will check in one hour (or when it happens again in case it is earlier).
I really miss Scale... As I would miss Exposè on the Mac. Any other way to switch between windows seems slow and clumsy.

---

### Post by mali2297 on 2008-03-06
> **ubanto said:**
> ps and top are not always consistent (compiz.real is not even in the list of 'top', unless I recently used Scale)

top sorts the processes according to cpu usage by default. To change it to memory usage, press **shift+f** and then **n+return**.

---

### Post by Arthur Archnix on 2008-03-06
At this point why not test if it's compiz? Open gconf-editor and change the default window manager to metacity.
```
gconf-editor
```search for "window_manager" and check names, or just go to /desktop/gnome/applications/window_manager

change default from /usr/bin/compiz to /usr/bin/metacity

reboot.

You can also just change it using alt+F2 and metacity --replace, but I'm not sure how completely that will disable compiz. Safer just to reboot and test.

EDIT: Sorry, I didn't see that you'd already disabled compiz.

---

### Post by ubanto on 2008-03-06
Growth is very slow. We're at 473MB now.
results from ps h -eo pmem,comm | sort -nr | head
in cronological order. Please note that I'm working with the same apps. Same number of tabs in firefox.
first sample:
 6.7 firefox-bin
 4.4 deskbar-applet
 4.1 Xorg
 3.5 gnome-panel
 2.5 claws-mail
 2.4 gnome-terminal
 2.2 gnome-system-mo
 2.1 nautilus
 1.6 python
 1.5 mixer_applet2
second:
 9.1 firefox-bin
 6.8 Xorg
 4.4 deskbar-applet
 3.5 gnome-panel
 3.1 pidgin
 2.5 claws-mail
 2.4 gnome-terminal
 2.2 gnome-system-mo
 2.1 nautilus
 1.6 python
third:
10.8 firefox-bin
 6.8 Xorg
 4.4 deskbar-applet
 3.5 gnome-panel
 3.3 pidgin
 2.5 claws-mail
 2.4 gnome-terminal
 2.2 gnome-system-mo
 2.1 nautilus
 1.6 python
current:
13.1 firefox-bin
 7.5 Xorg
 4.4 deskbar-applet
 3.6 pidgin
 3.5 gnome-panel
 2.7 claws-mail
 2.4 gnome-terminal
 2.2 gnome-system-mo
 2.1 nautilus
 1.6 python

It has slowed down a lot without compiz. However it's still there: 474.5 MB while typing this.

---

### Post by Arthur Archnix on 2008-03-06
Sorry to state the obvious, but you are running a fully patched system, right?
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ubanto on 2008-03-06
> **Arthur Archnix said:**
> Sorry to state the obvious, but you are running a fully patched system, right?
```
sudo apt-get update && sudo apt-get upgrade
```

Yes. However I checked, just in case I had missed something...

---

### Post by Arthur Archnix on 2008-03-06
And how did you disable compiz completely? The method I suggested, or just turning off desktop effects? Because, and I may be wrong, but I think the latter method still uses compiz, just no effects.

---

### Post by ubanto on 2008-03-06
> **Arthur Archnix said:**
> And how did you disable compiz completely? The method I suggested, or just turning off desktop effects? Because, and I may be wrong, but I think the latter method still uses compiz, just no effects.

Turning off desktop effects works. Here's my ps -A for proof.

 PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   25 ?        00:00:00 kblockd/0
   26 ?        00:00:00 kacpid
   27 ?        00:00:00 kacpi_notify
  181 ?        00:00:00 kseriod
  209 ?        00:00:00 pdflush
  210 ?        00:00:00 pdflush
  211 ?        00:00:00 kswapd0
  264 ?        00:00:00 aio/0
 2177 ?        00:00:00 ksuspend_usbd
 2178 ?        00:00:00 khubd
 2184 ?        00:00:00 ata/0
 2185 ?        00:00:00 ata_aux
 2203 ?        00:00:00 khpsbpkt
 2460 ?        00:00:00 reiserfs/0
 2520 ?        00:00:00 knodemgrd_0
 2560 ?        00:00:00 scsi_eh_0
 2561 ?        00:00:00 usb-storage
 2563 ?        00:00:00 scsi_eh_1
 2564 ?        00:00:00 usb-storage
 2671 ?        00:00:00 udevd
 3751 ?        00:00:00 kpsmoused
 4234 ?        00:00:00 xfslogd/0
 4235 ?        00:00:00 xfsdatad/0
 4242 ?        00:00:00 xfsbufd
 4243 ?        00:00:00 xfssyncd
 4483 tty4     00:00:00 getty
 4484 tty5     00:00:00 getty
 4487 tty2     00:00:00 getty
 4489 tty3     00:00:00 getty
 4490 tty1     00:00:00 getty
 4491 tty6     00:00:00 getty
 4664 ?        00:00:00 acpid
 4699 ?        00:00:00 kondemand/0
 4769 ?        00:00:00 syslogd
 4823 ?        00:00:00 dd
 4825 ?        00:00:00 klogd
 4846 ?        00:00:00 dbus-daemon
 4862 ?        00:00:00 NetworkManager
 4876 ?        00:00:00 NetworkManagerD
 4889 ?        00:00:00 system-tools-ba
 4890 ?        00:00:00 dbus-daemon
 4909 ?        00:00:00 hald
 4910 ?        00:00:00 hald-runner
 4950 ?        00:00:00 hald-addon-keyb
 4961 ?        00:00:00 hald-addon-keyb
 4962 ?        00:00:00 hald-addon-keyb
 4963 ?        00:00:00 hald-addon-keyb
 4968 ?        00:00:00 hald-addon-cpuf
 4969 ?        00:00:00 hald-addon-acpi
 4987 ?        00:00:00 cupsd
 5071 ?        00:00:00 hald-addon-stor
 5107 ?        00:00:00 hald-addon-stor
 5110 ?        00:00:00 hald-addon-stor
 5148 ?        00:00:00 postgres
 5311 ?        00:00:00 postgres
 5312 ?        00:00:00 postgres
 5515 ?        00:00:00 console-kit-dae
 5616 ?        00:00:00 avahi-daemon
 5617 ?        00:00:00 avahi-daemon
 5631 ?        00:00:00 dhcdbd
 5651 ?        00:00:00 hcid
 5661 ?        00:00:00 bluetoothd-serv
 5669 ?        00:00:00 krfcommd
 5686 ?        00:00:00 bluetoothd-serv
 5700 ?        00:00:00 gdm
 5701 ?        00:00:00 gdm
 5708 tty7     00:09:36 Xorg
 5749 ?        00:00:00 ntpd
 5791 ?        00:00:00 atd
 5806 ?        00:00:00 cron
 5885 ?        00:00:00 dhclient
 5966 ?        00:00:00 gnome-keyring-d
 5969 ?        00:00:00 x-session-manag
 6004 ?        00:00:00 ssh-agent
 6006 ?        00:00:01 gconfd-2
 6010 ?        00:00:00 dbus-daemon
 6012 ?        00:00:01 gnome-settings-
 6020 ?        00:00:08 gnome-panel
 6022 ?        00:00:01 nautilus
 6025 ?        00:00:00 gnome-volume-ma
 6034 ?        00:00:00 bonobo-activati
 6071 ?        00:00:00 gnome-vfs-daemo
 6147 ?        00:00:00 emerald
 6150 ?        00:00:14 gnome-screensav
 6151 ?        00:00:00 vino-session
 6155 ?        00:00:00 bluetooth-apple
 6157 ?        00:00:00 update-notifier
 6174 ?        00:00:00 evolution-alarm
 6176 ?        00:00:00 mapping-daemon
 6179 ?        00:00:00 trackerd
 6190 ?        00:00:00 nm-applet
 6192 ?        00:00:00 python
 6194 ?        00:00:00 gnome-power-man
 6201 ?        00:00:00 trashapplet
 6231 ?        00:00:00 evolution-excha
 6233 ?        00:00:01 deskbar-applet
 6242 ?        00:00:00 evolution-data-
 6266 ?        00:00:00 mixer_applet2
 6270 ?        00:00:00 fast-user-switc
 6288 ?        00:00:23 metacity
 6293 ?        00:02:23 gnome-system-mo
 6298 ?        00:00:04 claws-mail
 6343 ?        00:00:00 firefox
 6355 ?        00:00:00 run-mozilla.sh
 6359 ?        00:05:45 firefox-bin
 6600 ?        00:00:01 notification-da
 6795 ?        00:00:01 gnome-terminal
 6800 ?        00:00:00 gnome-pty-helpe
 6801 pts/0    00:00:00 bash
 6831 pts/0    00:00:00 top
 6833 pts/0    00:00:00 top
 6853 ?        00:00:12 pidgin
 7496 ?        00:00:00 gtk-gnash
 7543 pts/0    00:00:00 ps

---

### Post by Arthur Archnix on 2008-03-06
You should wrap those pastes in code so they're easier to scroll through. Glad you've got a workaround, now it's time to head over to compiz or ubuntu-desktop effects and begin figuring out if this is a bug.

---

### Post by mali2297 on 2008-03-06
> **ubanto said:**
> .. by shared memory I just meant that the GPU doesn't have its own VRAM but draws from the system RAM. 

Sorry for my ignorance, but is this some tweak or a default setting?

Have you had the problem with memory leakage ever since you first install ubuntu or did it appear later?

---

### Post by ubanto on 2008-03-06
> **mali2297 said:**
> Sorry for my ignorance, but is this some tweak or a default setting?

Have you had the problem with memory leakage ever since you first install ubuntu or did it appear later?

It is not a tweakable amount of memory, at least not that I know, and not with the Linux drivers, maybe with windows drivers, but I never used windows on this machine. have had ubuntu all of the time 6.06, 7.04, and finally 7.10, always 64bit edition. The problem seemed to appear since about one month, but I have to say that it could have been here earlier, only I didn't use this computer as my main work desktop at the time and might not have noticed. I'm thinking of the changes I've made recently:
1. I've installed the samsung sx4500 drivers (which is not a good thing since they act as sudo, but I need them to use my printer/scanner)
2. I installed emerald. It was late and I was bored,

Any idea?

---

### Post by mali2297 on 2008-03-06
> **ubanto said:**
> Turning off desktop effects works. Here's my ps -A for proof.

 PID TTY          TIME CMD
.
. 
 6147 ?        00:00:00 emerald
.
.

Kill this process as well.

---

### Post by ubanto on 2008-03-06
> **mali2297 said:**
> Kill this process as well.

yes, I saw it was still in the list, however it is sleeping and drawing 0 resources. However I want to try to disinstall emerald and restart compiz.

---

### Post by PmDematagoda on 2008-03-06
About the Turbo Cache technology, it is default, it does not depend on the drivers but depends on your RAM. For example, on my 6200 it needs at least 512Mb of RAM in order to register itself as to having 256Mb of memory, if I have a less amount of RAM then it would only register 128Mb.

---

### Post by ubanto on 2008-03-09
Sorry everybody I didn't update, but I had a lot of work, and I did it on the other computer, so I don't currently have more results to post.
As soon as I can experiment a little and post some result, I will do.

---

