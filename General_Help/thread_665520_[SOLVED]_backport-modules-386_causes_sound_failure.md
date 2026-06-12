---
title: "[SOLVED] backport-modules-386 causes sound failure/wireless failure"
date: 2008-01-12
forum: General Help
---

### Post by doubleij on 2008-01-12
I am running Ubuntu 7.10 on my Acer 4315. After extensive work, I managed to get wireless  internet to work. However, my sound would not play on external speakers. I found a solution at this link that looked easy and promising.

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

I followed the instructions exactly, but after I rebooted my computer I had no wireless internet and my sound card wasn't detected anymore (Gutsy detected it natively before). 

What's wrong? Do I have to do a fresh install? I already tried to remove the -386 backports, but when I rebooted that did nothing. I'm afraid there were some dependant files that were installed that messed up my wireless/sound card.

I'm happy to live without external speakers, but I can't use this computer without wireless internet or any sound at all. If possible, I need to repair the computer in the next few hours. All ideas welcome.

PS. Sorry if this is posted in the wrong place. I wasn't sure where to put a backports issue that affects sound and wireless.

EDIT: No, I did not make any backups of files before trying the modules. Yes, I know it's really stupid. I am brand new and I'm used to system restore in Windows. I don't even know how to back up system files yet in Ubuntu. I'm afraid I have to do a fresh install now. Is there any way to avoid that? Bandwidth is really slow where I live.

---

### Post by Arthur Archnix on 2008-01-14
If your sound and wireless worked on a fresh Gutsy install I would advise you not to try installing the backports modules, especially given the results of your first attempt.

When you say your external speakers don't work what I think that really means is that plugging anything into your sound-out jack (headphones, speakers) doesn't work. Your soundcard is working fine, it's just not recognizing your sound-out jack. If that's the case the fix is usually to add options specific to your card to file /etc/modprobe.d/alsa-base

For example, on my laptop everything works fine out of the box, but I had to add a line at the end of that file so that when I plugged a headset into my sound-out jack the laptop speakers would be muted. 

From another thread I noted that you have an acer laptop, so - from a fresh install - you should try this:

In a terminal type:
```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.backup
gksudo gedit /etc/modprobe.d/alsa-base
```
That creates a backup copy of your sound configuration and then opens the original file for editing. Scroll down to the bottom and paste the following:
```
# Added by me to enable line-out jack
options snd-hda-intel model=acer
```
Save and close, then reboot. Report back here with what you've found.

Unfortunately, you're probably right about messing some things up with the backports. You can try and fix this by first removing the backports modules you installed. Then removing the repository (uncheck it), then update your system and reboot. That may restore it to the state it was in before. If it fails to work then I'm afraid you're likely looking at a clean install.

EDIT:

> 1. Is there any way that editing the modprobe.d/alsa file as you described would affect my wireless? I don't think so, since that file is specifically connected with the sound card. But I need to check, because after the backports fix I couldn't even reinstall the madwifi driver that I used to fix the wireless (as I recall, it gave me an error about not being able to access modprobe or something). That's when I decided I needed a fresh install.

No. But adding the backports repository might have, especially if you allowed it to update the system. But even if not, when it added the backport modules it could easily have broken your wireless by replacing some libraries or something that both sound and wireless used. 

> 2. I don't yet know how to back up my system in Ubuntu, and I want to learn to do that before I implement the solution, just in case! I've seen programs like Time Vault and Flyback talked about on the forums. Do you have a recommendation for a backup method? If so, could you point me to a good how-to for the method? I would need to be sure that the backup preserved my wireless fix (which is presumably in modprobe, though I don't have that computer in front of me).

It depends on what the solution you try is. Editing configuration files by hand means you should just backup that file. Say for instance you decide to make a few changes to your xorg.conf file. You'd do:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
I did that before editing my xorg while using feisty, and it turns out my edits broke X and kicked me into a terminal. So all I had to do was type:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
and after a reboot my system is like new.

Last time I checked linux doesn't have anything quite like System Restore or Time Vault, though I'm sure there are workarounds available. The easiest solution I'm aware of requires a bit of forethought, but goes something like this:

When installing setup 4 partitions.
8GB /  (ext3)
1GB Swap
# GB /home  (ext3)
4.7 GB unassigned  (ext2)

Then use a program called P.I.N.G. (Ping is not ghost) to create an image of / and place it on the 4.7 GB partition. If you mess up something real bad you just toss in the PING cd, tell it to restore / from unassigned, and 10 minutes later you have your system back. I suggest making it 4.7 GB so that you can also place the image on a DVD or create a bootable recovery DVD.

There are probably other options, but since I use this one I haven't looked much into what the other ones are. If you find a better one though, please let me know :)

---

### Post by doubleij on 2008-01-15
Thanks for the detailed reply. I ended up having to make a fresh install of Ubuntu. I tried uninstalling backports-modules and then disabling the repository, but I still made no progress.

Everything works fine except the audio out/in jack (I incorrectly specified the soundcard above). I will try editing the alsa file as you suggest in a day or two when I get a chance. I'll post back here to let you know how it goes.

In terms of backup, I will keep looking around. When I know which files I've been editing, I've been careful to back them up first. But with the wireless fix, I'm not sure which file exactly I'm editing, or how inserting a wireless driver affects the file structure. I plan to go exploring into modprobe at some point and try and see which files it looks like are involved.

Since a fresh install takes a very long time (the 200 plus megabyte update package takes hours to download on my connection) I will probably not go with your partition solution at this point. Which is a pity, because it looks thorough and easy.

I'll probably use the QuickStart program for now, by mdpalow. It may not do everything, but I figure its a lot better than nothing, which is what I'm currently doing.

Anyways, I'll post back in a couple days with the results of the alsa deal. The Linux community has been very helpful as I work through the newbie issues on my first Linux computer. I'd heard how helpful everyone was, but it takes seeing to believe, I guess.

---

### Post by doubleij on 2008-01-16
UPDATE: Tonight I backed up the alsa-base file and then added the the two lines you suggested to the end of the file. I saved, closed and rebooted and discovered that nothing had changed. I plugged in headphones to test the out jack and I played the sample sound files and video files in the examples folder in Home. I heard the sounds clearly coming from the laptop's internal speakers, but I couldn't hear anything in my headphones, no matter how high the volume was.

On the positive side, altering the alsa-base file didn't affect any other files or cause any problems to the computer or wireless. So no damage done.

I was hopeful that this would be an easy fix, but maybe not. What should I try next? Thanks for your help!

---

### Post by Arthur Archnix on 2008-01-16
It's just a matter of finding the right option to add to the end of that file. You have an Acer laptop so I thought we'd try that option, but it didn't work apparently. Before we give up on it entirely though, have you gone into alsamixer and unmuted your various channels, maxed out the volumes, and such?
```
alsamixer
#make various changes, then hit 'esc' when done.
sudo alsactl store
```
Restart may be required. 

To figure out what other options it would be worthwhile trying, let's see what kind of soundcard you have.
```
lspci | grep Audio
```

---

### Post by doubleij on 2008-01-17
Ok, I tried playing with the Alsamixer tonight. I got all the volumes up to maximum (digital channel for capture was at 50%). I tried to push m as suggested in tutorials to mute/unmute, but I couldn't see any indication of muting either way on the channels. I tried this several times but I couldn't see a green O for on or a red M for mute--everything looked the same. So that's a bit odd. 


Perhaps its muted in some fashion and I can't figure out how to unmute it. I still hear sounds from the internal speakers. I also removed the autodetect on the sound GUI and set all the sound options to Alsamix. No change.

Here are my results for lspci | grep Audio

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)



Hopefully that will be helpful. If you have any ideas about the muting on Alsamixer, let me know. It's just odd that it won't show up. Are some channels not allowed to mute?

Thanks again...

UPDATE: I accessed alsamixer a different way (by double-clicking the sound icon in upper right) and found handy mute/unmute icons. I confirmed that all channels were unmuted. I don't know why that option wasn't accessible in the terminal!

---

### Post by doubleij on 2008-01-18
UPDATE: Tonight, I tweaked the line-out code in the alsa-base file in a couple different ways, but had no luck. In each case, the internal speakers still worked but I heard nothing on the headphones.

I tried:
=ACER
=toshiba [#because of an obscure reference I find to this working for another Acer Aspire]

I then set the system back to:
=acer

Other discussions of my soundcard have mentioned compiling a new alsa-base driver or patch and installing by hand. I'm hopeful we can find a line that works at the bottom of the alsa-base file so I don't have to do that! :( I'm sure I'd learn a lot, but it would sure be a stretch.

I also found this link to a bug report connected to my soundcard. The various fixes seem to be very dependent on the kernel version. Everyone stresses a "fresh install." I'm not sure how fresh they mean--I've had to put in some minor fixes to get wireless working. Still, the install is less than a week old. I ran a few commands I saw in the bug thread to get audio readout information. I'm not sure how to interpret them, but perhaps you will find them useful.

modinfo snd-hda-intel
filename:       /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
description:    Intel HDA driver
license:        GPL
srcversion:     CE1E01126593A3DE5624AE8
alias:          pci:v000010DEd0000055Dsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000055Csv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Bsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Asv*sd*bc*sc*i*
alias:          pci:v000010DEd000003F0sv*sd*bc*sc*i*
alias:          pci:v000010DEd000003E4sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000371sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000026Csv*sd*bc*sc*i*
alias:          pci:v000010B9d00005461sv*sd*bc*sc*i*
alias:          pci:v00001039d00007502sv*sd*bc*sc*i*
alias:          pci:v00001106d00003288sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA00sv*sd*bc*sc*i*
alias:          pci:v00001002d0000960Csv*sd*bc*sc*i*
alias:          pci:v00001002d00007919sv*sd*bc*sc*i*
alias:          pci:v00001002d0000793Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00004383sv*sd*bc*sc*i*
alias:          pci:v00001002d0000437Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000811Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000284Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000269Asv*sd*bc*sc*i*
alias:          pci:v00008086d000027D8sv*sd*bc*sc*i*
alias:          pci:v00008086d00002668sv*sd*bc*sc*i*
depends:        snd-pcm,snd-page-alloc,snd
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           index:Index value for Intel HD audio interface. (int)
parm:           id:ID string for Intel HD audio interface. (charp)
parm:           model:Use the given board model. (charp)
parm:           position_fix:Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size). (int)
parm:           probe_mask:Bitmask to probe codecs (default = -1). (int)
parm:           single_cmd:Use single command to communicate with codecs (for debugging only). (bool)
parm:           enable_msi:Enable Message Signaled Interrupt (MSI) (int)
parm:           enable:bool



------------------------------------------------------------

charity@charity-laptop:~$ aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

-------------------------------------------------------------

charity@charity-laptop:~$ lsmod | grep snd
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

-------------------------------------------------------------------------------------

charity@charity-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

------------------------------------------------------------------------------------------------------------------------------

Thanks again for your help! Perhaps this information will save us some time.

---

### Post by doubleij on 2008-01-29
I finally solved this issue. For reference, I am running 7.10 with an Acer 4315, a realtek 268 chipset, intel dual core processor, and Atheros 5007EG sound card.

Out of the box, only wireless and audio ports didn't work. I got wireless working initially thanks to the proper madwifi driver. [http://ubuntuforums.org/showthread.php?t=662877&page=2](http://ubuntuforums.org/showthread.php?t=662877&page=2)

But when I tried to fix the sound, either by installing the backports module that included Alsa 1.0.15 or by installing Alsa 1.0.15 directly, the fix broke my wireless fix.

I solved this by doing a fresh install and installing Alsa 1.0.15 first using a couple of bash scripts provided over here. [http://ubuntuforums.org/showthread.php?t=577699&page=3](http://ubuntuforums.org/showthread.php?t=577699&page=3)

The external sound and mic worked fine after reboot with Alsa 1.0.15. A.fter testing the fix, I installed the madwifi driver for my Atheros card. It worked first try and I have no problems with either sound or wireless now. The problem was apparently sequencing. If sound is installed first, wireless is happy to come after. But not the other way around.

---

### Post by Arthur Archnix on 2008-01-29
Good to hear you got it solved doublej. You should mark the thread as solved so that others can more easily find the solution you discovered.

---

### Post by doubleij on 2008-01-29
Done. I should note that I had to insert the =acer line into the alsa-base file after I installed the 1.0.15 driver to enable the audio ports. But once I had the correct driver, "=acer" worked right away after reboot.

---

### Post by trannypunk on 2008-02-21
Just a heads up.

I enabled backports as instructed in [http://ubuntuforums.org/archive/index.php/t-664579.html](http://ubuntuforums.org/archive/index.php/t-664579.html) on my Acer 4315 and I did not lose my wireless. I just rebooted and everything worked. 

Thanks for this fix.

---

### Post by doubleij on 2008-02-21
That's strange trannypunk. I'm glad it worked for you!

---

