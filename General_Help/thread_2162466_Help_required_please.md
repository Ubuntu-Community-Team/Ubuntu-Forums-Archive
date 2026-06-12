---
title: "Help required please"
date: 2013-07-14
forum: General Help
---

### Post by MibunoOokami on 2013-07-14
I'm trying to break my habit of giving a long detailed speech about my Ubuntu woes and get to the point so please bare with me if this is still too detailed or not detailed enough.

I bought an HP mini 110 a little over a year ago, its CPU (Intel Atom) and RAM (2GB upgrade) is smaller than my workhorse laptop so I wasn't concerned when I saw how slow it was and I just tolerated it.
By slow I mean when you first turn it on its slow to load the unity side/toolbar, slow to launch dash, apps, files etc. Typing in LibreOffice is slow, type several words and it takes a few seconds before any of those words show up, scrolling up and down also slow. The same happens in Thunderbird and Firefox. Firefox being very slow, click on a different tab it takes ages to change, ages to load when you have changed it, scrolling down also slow.

My wife's netbook is about 4 or 5 years old and has the same CPU and RAM, also runs Ubuntu 12.04LTS, and when I had to use it the other day, I was stunned to see it is faster than mine. I tried Libre, TB and FF, her netbook showed none of the same slowness of mine.
Now I have become annoyed with the speed of mine and want to know what I may have done when I first installed Ubuntu in mine that has made it so slow, and what I can do to get it to work faster? I honestly thought and expected it to be just the type of my processor and RAM, now I'm certain it must be user error when I installed Ubuntu, even though I have installed it a couple times in the past with better success than this.

If I've missed any relevant info which could assist in fixing this, please let me know. Thank you.

---

### Post by MrSteve on 2013-07-14
this maybe of no help at all, but ...

i use a intel atom 1.6 home built shuttle system and found that not installing a swap file/partition worked wonders for my small system

so i set up the install for system as
/ (root) 20GB primary
/home rest of HDD logical

no swap partition

this was done on two home built shuttle 1.6 intel atom systems. both are working fine ...

---

### Post by houseworkshy on 2013-07-14
I don't know the answer to this but have some diagnoistic ideas. 
  There are some commands which may be informative in the termainal;  "top" or "htop" ( which you'd have to install but it gives a bit more) would show you if some process was eating up your RAM.    
"baobab" would show your hd use.  The reason that is worth looking at is that even though linux handles disks usage well ( never needs defraging for example ) it does work more efficiently with disks that are less than 80% full. 

"man <whatever the command happens to be>" will give more details on how to use the commands above. 

You could also take a look at any swap file usage. 
The easy way to post detailed system spec's is to install "sysinfo", use it's "save file" function to create a txt file which you can attach here.  There may be some hardware specific something which someone may know about. 

2gig ain't bad but on my 1.8 gig whilst Unity runs, it crawls, if you can't fix the issue you may fare better with Xfce or LXDE as an enviroment, assuming a standard install half of your RAM will be used just ticking over taking you down to only 1gig with which to actually do anything.

---

### Post by MibunoOokami on 2013-07-14
> **MrSteve said:**
> this maybe of no help at all, but ...

i use a intel atom 1.6 home built shuttle system and found that not installing a swap file/partition worked wonders for my small system

so i set up the install for system as
/ (root) 20GB primary
/home rest of HDD logical

no swap partition

this was done on two home built shuttle 1.6 intel atom systems. both are working fine ...

Anything is worth a try. Is it possible to remove the swap partition and merge that with /home without having to reinstall from scratch? If so, could you detail the steps please?

---

### Post by Irihapeti on 2013-07-14
I've run an EeePC 900 (900MHz CPU, 1 GB RAM) for four years now with no swap partition, so it certainly can be done. Making the change would depend very much on your partition layout. If the /home partition and swap are next to one another, you can remove the swap partition and expand the /home partition to fill the unallocated space.

Two points with that, though:
[LIST=1]
[*] It would need to be done from a liveCD (or liveUSB). You can't do it from the running system.
[*] Always BACKUP your user files beforehand. Things can, and do, go badly wrong sometimes.
[/LIST]

However, I'm inclined to think that, _if_ the presence of a swap file is slowing things down (and I'm not entirely sure that it is), then there's a lot of writing to swap going on. Meaning that there's not really enough RAM for what you're trying to do. It could be that Unity is too heavy for your machine and you'd be better off with Gnome-fallback or Xubuntu. Both of these run fine on my EeePC, while Unity is sluggish.

If you have the disk space, you can just install these without having to reinstall the entire system.

---

### Post by MibunoOokami on 2013-07-14
> **houseworkshy said:**
> I don't know the answer to this but have some diagnoistic ideas. 
  There are some commands which may be informative in the termainal;  "top" or "htop" ( which you'd have to install but it gives a bit more) would show you if some process was eating up your RAM.    

This was hard to copy and paste, I hope it's the way it should be

```
top - 08:44:31 up  1:41,  2 users,  load average: 0.92, 0.83, 0.83
Tasks: 170 total,   2 running, 167 sleeping,   0 stopped,   1 zombie
Cpu(s): 13.4%us,  9.5%sy,  0.0%ni, 76.7%id,  0.0%wa,  0.0%hi,  0.4%si,  0.0%st
Mem:   2049904k total,  1390300k used,   659604k free,    56736k buffers
Swap:  2999292k total,    27220k used,  2972072k free,   524436k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1026 root      20   0  189m 119m 112m S   45  6.0  42:34.29 Xorg               
 2178 mno       20   0  655m 231m  34m R   31 11.6  22:52.98 firefox            
 6562 mno       20   0 91632  15m  10m S    4  0.7   0:06.29 gnome-terminal     
 1897 mno       20   0  526m  76m  22m S    3  3.8   2:35.63 skype              
 1847 mno       20   0  154m  12m 9.8m S    2  0.6   1:10.59 metacity           
 1888 mno       20   0 62000  10m 8340 S    2  0.5   2:01.90 gkrellm            
 6418 root      20   0     0    0    0 S    2  0.0   0:02.32 kworker/0:2        
 5158 mno       20   0  273m  64m  29m S    1  3.2   0:21.88 unity-2d-shell     
 8621 mno       20   0  2852 1188  888 R    1  0.1   0:00.34 top                
 4510 root      20   0     0    0    0 S    1  0.0   0:03.02 kworker/2:4        
 5082 mno       20   0  351m 132m  77m S    0  6.6   3:22.24 soffice.bin        
 6112 root      20   0     0    0    0 S    0  0.0   0:02.80 kworker/u:1        
    1 root      20   0  3656 1940 1308 S    0  0.1   0:02.25 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.74 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.48 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.16 watchdog/0    
```     


> **houseworkshy said:**
> "baobab" would show your hd use.  The reason that is worth looking at is that even though linux handles disks usage well ( never needs defraging for example ) it does work more efficiently with disks that are less than 80% full. 

Baobab says my disk usage is 21.8% which seems a bit on the low side.

> **houseworkshy said:**
> 
You could also take a look at any swap file usage. 
The easy way to post detailed system spec's is to install "sysinfo", use it's "save file" function to create a txt file which you can attach here.  There may be some hardware specific something which someone may know about. 

2gig ain't bad but on my 1.8 gig whilst Unity runs, it crawls, if you can't fix the issue you may fare better with Xfce or LXDE as an enviroment, assuming a standard install half of your RAM will be used just ticking over taking you down to only 1gig with which to actually do anything.

Sysinfo has my RAM at 59% free and swap 99% free.

---

### Post by varunendra on 2013-07-14
First things first - Your RAM is okay, but with atom processors, I'd recommend to go with either Xubuntu or Lubuntu (or some other lightweight distro). Default Ubuntu with Unity is a bit heavy for that configuration.

That being said, about your swap question -
> **MibunoOokami said:**
> Anything is worth a try. Is it possible to remove the swap partition and merge that with /home without having to reinstall from scratch? If so, could you detail the steps please?

With 2 GB RAM, I do recommend keeping a swap of 1 or 2 GB size. I doubt if removing it is going to improve performance, or significant improvement even if it did.

You can safely test it by temporary turning it off. First, make sure which of your partitions is being used as swap -
```
cat /proc/swaps
```
It should return something like -
```
Filename				Type		Size	Used	Priority
/dev/zram0                              partition	1975292	183188	100
**[COLOR="#0000CD"]/dev/sda5[/COLOR]**                               partition	4341756	0	-1

```
The zram0 device is virtual swap in RAM (may not exist for you, and will only benefit if it does), and the "/dev/sda5" is the actual swap partition in above output. Yours may be different.

Now turn this physical swap off -
```
sudo swapoff /dev/sda5
```
Confirm that it is gone (temporarily) using the same "cat /proc/swaps" command as above. Now use your netbook as usual and see for yourself if there is any performance improvement. In some cases, it may go even worse without a swap.

To turn the swap 'On' again, just reboot or do -
```
sudo swapon /dev/sda5
```
(of course change "sda5" with whatever partition you have as swap)

---

### Post by Irihapeti on 2013-07-14
Xorg is using a lot of CPU. It could be a graphics issue.

What graphics card/chip does the machine use?

---

### Post by MibunoOokami on 2013-07-14
> **Irihapeti said:**
> Xorg is using a lot of CPU. It could be a graphics issue.

What graphics card/chip does the machine use?

Sysinfo says it's a VGA compatable controller. Sorry, I don't know the specific type.

---

### Post by Irihapeti on 2013-07-14
Run the command

```
sudo lspci | grep -i vga
```
and post the output

---

### Post by MibunoOokami on 2013-07-14
> **varunendra said:**
> First things first - Your RAM is okay, but with atom processors, I'd recommend to go with either Xubuntu or Lubuntu (or some other lightweight distro). Default Ubuntu with Unity is a bit heavy for that configuration.

My knowledge is limited and I don't want this to come across the wrong way, but why would Unity work well on one netbook and not another? Could that be due to them being different brands or other hardware or something? Thanks

---

### Post by MibunoOokami on 2013-07-14
> **Irihapeti said:**
> Run the command

```
sudo lspci | grep -i vga
```
and post the output

```
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09)


```

I've just remembered, I had some help with the graphics just after I got the netbook, if I recall it was about running unity 3d. I'll just go through my old threads, maybe something I did back then is making it use more CPU than necessary.

---

### Post by MibunoOokami on 2013-07-14
> **MibunoOokami said:**
> 
I've just remembered, I had some help with the graphics just after I got the netbook, if I recall it was about running unity 3d. I'll just go through my old threads, maybe something I did back then is making it use more CPU than necessary.

I can't see any threads by me, so I must have only viewed other peoples' threads and followed some instructions... Unless I hijacked one of my other threads.

---

### Post by varunendra on 2013-07-14
> **MibunoOokami said:**
> My knowledge is limited and I don't want this to come across the wrong way, but why would Unity work well on one netbook and not another? Could that be due to them being different brands or other hardware or something? Thanks

Mainly, and perhaps the only thing that can make a direct significant difference is graphics and the driver in use. Assuming the CPU and RAM generation (DDR2/3) are same on both netbooks.

However, there are other 'hidden' or not prominently advertised factors too. Like the BIOS may be programmed to use components in their 'low profile' mode to save power (thus 'trying' to give you more backup time). Cheap boards using components that may not be able to use the CPU/bus speeds as good as the other one.

An example I personally witnessed is one of the Acer's timeline series laptops with i5 (2nd gen) CPU. Despite having a superior overall configuration (and much higher price, it performed slower than my Asus x54C with i3-2330 in almost everything I tested on both (7z compression/decompression, Video transcoding and Far-Cry2 game performance, each performed 3 times on fresh win7 installations.). It does deliver 4-6 hours backup though, while mine delivers only 2:40-3:14 hrs.

Not trying to justify my suggestion, just trying to answer your question to the best of my ability. :)

---

### Post by Irihapeti on 2013-07-14
We need to find out why Xorg is using so much CPU.

For comparison, the EeePC is using
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND  
  915 root      20   0 34420  12m 5392 S  1.3  1.2   2:24.46 Xorg
```
Unfortunately, I'm not an expert on graphics, so we'll need to hear from someone who is.

---

### Post by MibunoOokami on 2013-07-14
> **varunendra said:**
> First things first - Your RAM is okay, but with atom processors, I'd recommend to go with either Xubuntu or Lubuntu (or some other lightweight distro). Default Ubuntu with Unity is a bit heavy for that configuration.

How different are Xubuntu and Lubuntu from Ubuntu? Would you recommend one over the other?

> **varunendra said:**
> That being said, about your swap question -


With 2 GB RAM, I do recommend keeping a swap of 1 or 2 GB size. I doubt if removing it is going to improve performance, or significant improvement even if it did.

I turned it off and saw only the slightest difference. I may have too much space allocated to swap, 3GB.

> **Irihapeti said:**
> We need to find out why Xorg is using so much CPU.

For comparison, the EeePC is using
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND  
  915 root      20   0 34420  12m 5392 S  1.3  1.2   2:24.46 Xorg
```
Unfortunately, I'm not an expert on graphics, so we'll need to hear from someone who is.

I have a funny feeling... There are two proprietary drivers available, drm driver for the intel gma500 and intel cedarview graphics driver, both are already activated and in use. I'm going to deactivate the cedarview one and see what happens, When I first installed Ubuntu on here I figured that if several additional drivers are available they must all meant to be used. Thinking back, my wife's netbook has no proprietary drivers and mylaptop only has one.

Will post back shortly with results.

---

### Post by MibunoOokami on 2013-07-14
> **MibunoOokami said:**
> 
I have a funny feeling... There are two proprietary drivers available, drm driver for the intel gma500 and intel cedarview graphics driver, both are already activated and in use. I'm going to deactivate the cedarview one and see what happens,
Will post back shortly with results.

When I deactivated the cedarview driver, the drm one also turned off. I restarted the machine and voila the speed has improved dramatically. Libre was quite slow to load and the CPU was fluctuating between 5-100% according to gkrellm. My screen dimming keys that I programmed have stopped working, but I think I can reprogram them.

I've learned something new today, it's not just the CPU, RAM and/or number of files/programs you're running that determine speed of a machine but also soft/hardware like graphics cards and drivers. Thank you all who posted here today.

---

### Post by MibunoOokami on 2013-07-14
> **varunendra said:**
> Mainly, and perhaps the only thing that can make a direct significant difference is graphics and the driver in use. Assuming the CPU and RAM generation (DDR2/3) are same on both netbooks.

However, there are other 'hidden' or not prominently advertised factors too. Like the BIOS may be programmed to use components in their 'low profile' mode to save power (thus 'trying' to give you more backup time). Cheap boards using components that may not be able to use the CPU/bus speeds as good as the other one.

Not trying to justify my suggestion, just trying to answer your question to the best of my ability. :)

I appreciate your earlier suggestion, it lead me to ask a question that got me an answer which really started my brain ticking over and ultimately lead to the solution. There are a couple of differences between my wife's netbook and mine. Mine has DDR3 which is the generation gap and can't run unity in 3D must be a hidden factor. That's what reminded me I had played with the graphics in terminal trying to see if I could enable 3D unity and then some proprietary drivers became available which I activated. Irihapeti's mention about the CPU usage combined with the graphics card also helped.

Thank you all once again. I'm going to mark this as solved now.[[COLOR=#C61919]****[/COLOR]]("http://ubuntuforums.org/member.php?u=346442")

---

### Post by varunendra on 2013-07-14
Glad you sorted it out. I see the need for some further explanations though -
> **MibunoOokami said:**
> Mine has DDR3 which is the generation gap and can't run unity in 3D must be a hidden factor.
No that is not a hidden factor, anything that you can determine just by looking at the specs can not be called a hidden factor. Besides, DDR3 is actually supposed to perform better than DDR2, although that difference is unnoticeable in normal operations.

However, the native vs. proprietary driver thing, especially in case of graphics, can be a big difference, and often there are not many choices to level that difference. I recently read somewhere (too lazy to dig up the link again) that the embedded graphics some (or perhaps all 2nd/3rd gen) atom chips use has been a bit problematic for Linux. The Intel HD2000/3000 (embedded graphics in i-series cpus) on the other hand works very nicely with the native i915 driver.

Between Xubuntu and Lubuntu (if you wish to give them a shot), Lubuntu is lighter than Xubuntu, but also has much less features in the Desktop environment. It is meant for systems with too low specs. For your netbook, Xubuntu should be quite fast and responsive, Lubuntu - even faster. That is, if you still feel the need to test them. :)

In general, you should test any version in the Live mode before installing it, just to make sure it works well with your hardware (or can be made to work), and satisfies your needs.

---

