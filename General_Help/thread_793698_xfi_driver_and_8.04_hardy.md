---
title: "xfi driver and 8.04 hardy"
date: 2008-05-14
forum: General Help
---

### Post by adramalech on 2008-05-14
okay i have seen and researched many posts about what to do...so i going to need to figure out how to uninstall all alsa, and reinstall oss, since it screwed up the first time, can someone please tell me how the syntax will look?

also, what should i do for oss xfi beta drivers and 8.04?  I had 7.10 but decided to upgrade, albeit too soon but ohh well, i am having issues because i do everything they say to do in this tutorial

[http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2)

[HTML]
adramalech@adramalech:~$ sudo soundon
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
Failed to disable conflicting sound drivers
Reboot and try running soundon again

Also check that you have not compiled sound support statically
into the kernel.
adramalech@adramalech:~$[/HTML]

i really wish to start over again and get this sound working has anybody got it working with xfi platinum and oss???  :confused:

EDIT******************************************EDIT**************************************************************EDIT 

okay i tried this 

[HTML] sudo soundoff
       cd /usr/lib/oss/etc
       gksudo gedit installed_drivers[/HTML]

and got this 

[HTML]hdaudio #Nvidia High Definition Audio (MCP55)
sbxfi #Creative SB X-Fi (EARLY BETA)
ossusb #Generic USB audio device (BETA)
vmix #OSS Transparent Virtual Mixing Architecture[/HTML]

[HTML]root@adramalech:~# ossdetect -v
Detected Creative SB X-Fi (EARLY BETA)
Detected Nvidia High Definition Audio (MCP55)
Detected Generic USB audio device (BETA)
Detected OSS Transparent Virtual Mixing Architecture
root@adramalech:~# 
[/HTML]

[HTML]adramalech@adramalech:~$ ossinfo
Version info:   (0x00000000) 
Platform: Linux/x86_64 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 (adramalech)

Number of audio devices:	0
Number of audio engines:	0
Number of mixer devices:	0


Device objects


Mixer devices

Audio devices
adramalech@adramalech:~$ 

[/HTML]

[HTML]adramalech@adramalech:~$ ossxmix
No mixers are available
adramalech@adramalech:~$ 
[/HTML]

---

### Post by adramalech on 2008-05-22
bump....

hey what is the code to completly remove alsa and oss4 and then reinstall oss4?

here is my lspci -v 

[html] 02:08.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs X-Fi Platinum
	Flags: bus master, medium devsel, latency 32, IRQ 15
	I/O ports at 6000 [size=32]
	Memory at ec000000 (64-bit, non-prefetchable) [size=2M]
	Memory at e8000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
[/html]

---

### Post by adramalech on 2008-05-23
okay i finally got sound from booting in, but still no sound from you tube video's etc... i even did what he said about getting the sound for flash working....is there anything else i need to do like change some settings or something???:confused:

edit: okay when i go to volume controls->edit->preferences it only shows volume nothing else..

---

