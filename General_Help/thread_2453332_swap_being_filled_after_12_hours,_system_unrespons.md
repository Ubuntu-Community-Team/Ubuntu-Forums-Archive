---
title: "swap being filled after 12 hours, system unresponsive"
date: 2020-11-08
forum: General Help
---

### Post by subadanus on 2020-11-08
when i first start my computer, its okay and has little to no issue with multi-tasking

after about 6 hours, it becomes slow, and after 12 hours, it requires a full reboot and is unresponsive

using glances, i can see that the swap becomes 100% full over time, despite me closing all applications

pulse-audio is also very glitchy, skips, or repeats with the slow-downs, and gnome regularly uses more than 60% of the cpu while i'm doing absolutely nothing

all i use is discord, firefox, gimp, and spotify

i have one singular 8gb stick of DDR4, a 1tb hdd, an i5 6500, and a radeon 7770 running ubuntu 20.04 on kernel 5.4.0-52

how can i tell what is using my swap or how can i empty it?  how can i stop pulse-audio from being effected by this?  how can i stop gnome from using over 60% of a seemingly reasonable cpu? 

:confused:

---

### Post by Impavidus on 2020-11-08
That's probably not what's supposed to happen, although Firefox (when opening enough tabs) and Gimp (when editing a large image with many layers) are capable of consuming any amount of memory.

**top** can tell you memory usage per application. Use < and > to choose the column used for sorting its output. Interpreting the output isn't always straightforward. Firefox is spread over multiple processes, some memory is shared by multiple processes.

---

### Post by kc1di on 2020-11-08
What is the output of this terminal command?
```
cat /proc/sys/vm/swappiness
``` if it's 60 or above change it to 20  following the steps in this[ tutorial.]("https://easylinuxtipsproject.blogspot.com/p/speed-ubuntu.html#ID1.1")  This may help some.

---

### Post by subadanus on 2020-11-08
changed swap to 20

i think i narrowed down the source of the problem, it may not be firefox

if  i join a voice channel in discord the ENTIRE SYSTEM slows to a crawl,  scrolling is very difficult, audio is glitchy, and opening new windows  is very slow

cpu and ram usage in this configuration is not 100%, but high by discord and the other applications mentioned above

the terminal outputs some kind of gpu related error, along with  many audio errors

i tried installing the latest radeon drivers for ubuntu 20.04 and no matter what i did it just failed to install and gave me unmet dependencies that i could not install myself or didn't exist

```
[COLOR=#4F5660][FONT=Consolas]Discord 0.0.12 
Starting app.
 Starting updater.
 [Modules] Modules initializing 
[Modules] Distribution: remote 
[Modules] Host updates: enabled 
[Modules] Module updates: enabled 
[Modules] Module install path: /home/baron/.config/discord/0.0.12/modules 
[Modules] Module installed file path: /home/baron/.config/discord/0.0.12/modules/installed.json 
[Modules] Module download path: /home/baron/.config/discord/0.0.12/modules/pending [10771:1108/062943.739292:ERROR:buffer_manager.cc(488)] [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command 
[Modules] No updates to install 
[Modules] Checking for host updates. 
[Modules] Host is up to date. 
[Modules] Checking for module updates at https://discord.com/api/modules/stable/versions.json 
[Modules] No module updates available. [10771:1108/062944.140665:ERROR:buffer_manager.cc(488)] [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command 
[000:000] [10840] (audio_device_generic.cc:66): SetRecordingDevice: Not supported on this platform 
[000:071] [10840] (audio_device_generic.cc:66): SetRecordingDevice: Not supported on this platform 
(electron) 'setBadgeCount function' is deprecated and will be removed. Please use 'badgeCount property' instead. 
[008:039] [10840] (audio_send_stream.cc:285): Failed to set up send codec state. 
[008:233] [10840] (audio_send_stream.cc:285): Failed to set up send codec state. 
[008:233] [10840] (audio_device_generic.cc:31): BuiltInAECIsAvailable: Not supported on this platform 
[008:448] [10840] (audio_send_stream.cc:285): Failed to set up send codec state.
[/FONT][/COLOR]
```[COLOR=#4F5660][FONT=Consolas]
[/FONT][/COLOR]

---

### Post by subadanus on 2020-11-09
this is still happening, top, nor htop, nor glances is revealing what is actually using the swap

even with all programs closed and the system slowed to a crawl with 80% or more of the swap being used, no processes show high memory usage

while the system is slow like this, the HDD is going crazy, im assuming it's writing and accessing things to it for memory as the swap is full

---

### Post by Impavidus on 2020-11-10
Have you tried an older kernel?

---

