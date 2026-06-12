---
title: "Alsa 1.0.15?"
date: 2007-10-16
forum: General Help
---

### Post by hirolau on 2007-10-16
Just saw on [http://www.alsa-project.org](http://www.alsa-project.org) that ALSA 1.0.15 was released today.

My computer have had problems with the sound but i heard that it would be fixed in 1.0.15


So the question is. Do you think ALSA 1.0.15 will be a part of the finale release? Or how long do i need to wait before it is included in the ubuntu install?

 I know i can just install it but right now i have much to do and is to lazy, planning on doing a complete reinstall sooner or later anyway.

My computer is a HP Pavilion dv6521oe... With some realtek audio.. But that is not very important now. The question is about ALSA

---

### Post by jocko on 2007-10-16
> **hirolau said:**
> So the question is. Do you think ALSA 1.0.15 will be a part of the finale release? Or how long do i need to wait before it is included in the ubuntu install?

If by final release, you mean gutsy, then no. Gutsy will be released in... probably less than 48 hours.
(so the packages that are in the repos now may very well be the final versions)
You'll have to wait until april, when hardy heron comes.

---

### Post by ageless on 2007-10-17
> **jocko said:**
> If by final release, you mean gutsy, then no. Gutsy will be released in... probably less than 48 hours.
(so the packages that are in the repos now may very well be the final versions)
You'll have to wait until april, when hardy heron comes.

Perhaps, someone already did the deb with new alsa?

---

### Post by FredB on 2007-10-17
Too late for gutsy. For around 36 hours, no new packages were uploaded. At least for ubuntu.

So, next release, or a backport ?!

---

### Post by hirolau on 2007-10-17
Well, i just installed the release candidate and then alsa 1.0.15 and everything works fine...

---

### Post by karomann on 2007-10-17
how did you do that? I tried compiling alsa on my Gutsy and all I got was only (output of dmesg |grep snd)::
>  
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[ 1058.932000] snd_hda_intel: Unknown symbol snd_ctl_add
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[ 1058.932000] snd_hda_intel: Unknown symbol snd_pcm_new
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[ 1058.932000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_card_register
[ 1058.932000] snd_hda_intel: Unknown symbol snd_card_register
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_card_free
[ 1058.932000] snd_hda_intel: Unknown symbol snd_card_free
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[ 1058.932000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[ 1058.932000] snd_hda_intel: Unknown symbol snd_card_proc_new
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[ 1058.932000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[ 1058.932000] snd_hda_intel: Unknown symbol snd_ctl_new1
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_component_add
[ 1058.932000] snd_hda_intel: Unknown symbol snd_component_add
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_card_new
[ 1058.932000] snd_hda_intel: Unknown symbol snd_card_new
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[ 1058.932000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[ 1058.932000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[ 1058.932000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[ 1058.932000] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[ 1058.932000] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[ 1058.932000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[ 1058.932000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_device_new
[ 1058.932000] snd_hda_intel: Unknown symbol snd_device_new
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[ 1058.932000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[ 1058.932000] snd_hda_intel: Unknown symbol snd_card_disconnect
[ 1058.932000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[ 1058.932000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[ 1058.936000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[ 1058.936000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[ 1058.936000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[ 1058.936000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step


my card is intel hda, realtek alc883. And I followed the instructions from [http://alsa-project.org/main/index.php/Matrix:Module-hda-intel]("http://alsa-project.org/main/index.php/Matrix:Module-hda-intel")

---

### Post by CDNdevil on 2007-10-18
I have the same problem after install 1.0.15 from source in gusty, followed the same way as when I installed in feisty.

---

### Post by pcmanlin on 2007-10-19
I had the same problem and solved it.

ubuntu default snd-hda-intel.ko location:
/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko

alsa 1.0.15's installation location:
/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko
so copy /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko to /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko .

and put the modules/* in alsa's compile directory into /lib/modules/.../kernel/sound, you can use "find" to get their location.
snd-hda-intel.ko
snd-hwdep.ko
snd.ko
snd-mixer-oss.ko
snd-page-alloc.ko
snd-pcm.ko
snd-pcm-oss.ko
snd-rtctimer.ko
snd-seq-device.ko
snd-seq.ko
snd-seq-midi-event.ko
snd-seq-oss.ko
snd-timer.ko

then, depmod -a

reboot, try again.

---

### Post by f4b3r on 2007-10-19
will alsa 1.0.15 be integrated in new kernel in some weeks (and made available with ubuntu auto update software) ?

thanks  :popcorn:

---

### Post by eddiefullmetal on 2007-10-20
pcmanlin thanks dude it worked.I have hp dv6543 i installed gutsy no sound but it recognize my sound card i compiled the latest alsa drivers and then no sound no sound card but with this trick everything worked

---

### Post by f4b3r on 2007-10-22
thank you very much pcmanlin,

i have pavilion dv6560el ( 6560 dv6560 : <-- for google :P) and it worked !!

I followed this guide [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) (till "Reboot"), and then:

sudo cp -v /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
sudo cp -v /usr/src/alsa/alsa-driver-1.0.15/modules/* /lib/modules/2.6.22-14-generic/kernel/sound/
sudo depmod -a

and it worked :D

thx man :D

whohaaaaa finally...  i can listen to bruce springsteen on linux ;p

---

### Post by syxbit on 2007-10-22
we should write a script that would do all of this
shouldn't be too hard (i don't think)
as with each reinstall, or kernel upgrade, we'll have to redo it

---

### Post by syxbit on 2007-10-22
k, i'm done
i haven't tested it, as i got it working by doing it manually.
feel free to check it out, and give feedback
the script will fetch alsa driver, utils, and libs (1.0.15) from the alsa ftp, and do what the above mentioned website does (including install dependencies, and compile)
i think it should work.
there are 2 scripts, cause there has to be a reboot in the middle.

let me know what you think
run the both scripts as sudo
sudo sh alsa1.sh
reboot
sudo sh alsa2.sh

---

### Post by raintheory on 2007-10-22
> **syxbit said:**
> k, i'm done
i haven't tested it, as i got it working by doing it manually.
feel free to check it out, and give feedback
the script will fetch alsa driver, utils, and libs (1.0.15) from the alsa ftp, and do what the above mentioned website does (including install dependencies, and compile)
i think it should work.
there are 2 scripts, cause there has to be a reboot in the middle.

let me know what you think
run the both scripts as sudo
sudo sh alsa1.sh
reboot
sudo sh alsa2.sh

Would it be difficult to modify these to work with the E-MU 1616?

Here is ALSA's page on the unit: [http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga)

I know one of the main differences would be *"./configure --with-cards=**emu10k1 --with-sequencer=yes** ; make ; make install"* when installing the driver, but I'm not sure if there would be anything else..

Thanks!

---

### Post by syxbit on 2007-10-22
that should be it actually
the only thing specific to the intel-hda is that one line

changing that one line should work.

however, alsa_2.sh is not going to work.
you at least have a base. you could run my first script, and just finish up anything extra manually, or append to my script
let me know how it goes.

---

### Post by Technoviking on 2007-10-22
Great tip.

---

### Post by richol on 2007-10-27
No-sound problem solved on MSI Megabook M673X (ALC883), already after running alsa1.sh and reboot. Thanks.

---

### Post by Laz30 on 2007-11-01
Yikes! After following this guide my usb headset are no longer detected....
This is quite a big problem for me since I don't use external speakers and I'm dependent on Skype for my work :(

When I choose System-> System Pref -> Sound I only see 'HDA Intel' and Realtek. Prior to installing 1.0.15 I was always able to select Logitech USB Headset as well but this is gone.

The funny thing is that lsusb shows the device and I can hear a little 'scratch' in the headset when I plug in/out:

ln@ln-laptop:~$ lsusb 
Bus 005 Device 004: ID 046d:c30e Logitech, Inc. 
Bus 005 Device 005: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 005 Device 003: ID 04cc:1520 Philips Semiconductors 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
**Bus 001 Device 006: ID 046d:0a01 Logitech, Inc.** 
Bus 001 Device 001: ID 0000:0000  


ln@ln-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Please - can anyone help me?

---

### Post by mocha on 2007-11-01
I've posted 2 other threads about this and no one responds.  Do any of you with Intel HDA controllers have problems recording from the "stereo mix"?  In other words, recording sound generated from internal sources such as webpages or streams or audio files, etc?  I compiled Alsa 1.0.15 and tried various "model=" options, and although it gives me different results in the mixer app, nothing I do is able to get the internal analog mix to record.  I've also tried different recording applications.  I don't have problems playing any sound, and I also don't have problems recording from external devices such as mic or line-in.  Does this problem have something to do with the driver for the AD1988 in the 2.6.20 kernel?  Should I try compiling the latest kernel?

---

### Post by komsas on 2007-11-14
> **f4b3r said:**
> thank you very much pcmanlin,

i have pavilion dv6560el ( 6560 dv6560 : <-- for google :P) and it worked !!

I followed this guide [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) (till "Reboot"), and then:

sudo cp -v /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
sudo cp -v /usr/src/alsa/alsa-driver-1.0.15/modules/* /lib/modules/2.6.22-14-generic/kernel/sound/
sudo depmod -a

and it worked :D

thx man :D

whohaaaaa finally...  i can listen to bruce springsteen on linux ;p

It worked to me too, JEEE.. :)

---

### Post by Yoshidude on 2007-11-15
Thank you very much, pcmanlin. I had all but given up on getting sounds, I'd followed so many walkthroughs on how to get sound on my line of laptops (Toshiba Satellite A135) and always nothing. Now it works and it's great. Thank you for the help.

---

### Post by michaelcole on 2007-11-15
Rockstar dude!  This worked like a dream!

HP Pavilion dv9500 laptop
Intel 8280 ICH8 HDA
00:16.0 (rev3)
Ubuntu 7.10

Ran the first script and rebooted.  Sound worked.  I ran the second script well, just because.

Thanks syxbit.  This saved me *hours* of work.  I appreciate your help.  Now I can watch Strongbad Emails again ;-)

---

### Post by gindyo on 2007-12-06
hi everybody I have a dell vostro 1400, I had the no sound problem after trying all workarounds to no avail I found this [http://ubuntuforums.org/showthread.php?t=607258](http://ubuntuforums.org/showthread.php?t=607258) post #3 and now everything works great.

---

### Post by Drigerott on 2007-12-13
> **f4b3r said:**
> thank you very much pcmanlin,

i have pavilion dv6560el ( 6560 dv6560 : <-- for google :P) and it worked !!

I followed this guide [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) (till "Reboot"), and then:

sudo cp -v /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
sudo cp -v /usr/src/alsa/alsa-driver-1.0.15/modules/* /lib/modules/2.6.22-14-generic/kernel/sound/
sudo depmod -a

and it worked :D

thx man :D

whohaaaaa finally...  i can listen to bruce springsteen on linux ;p


WOOOOOOOOOOOOOOOOOOOOORKED :D:D:D:D:DD::D oleeeeeeeeeeeeeeeeee

---

### Post by redonisc on 2007-12-28
> **pcmanlin said:**
> I had the same problem and solved it.

ubuntu default snd-hda-intel.ko location:
/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko

alsa 1.0.15's installation location:
/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko
so copy /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko to /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko .

and put the modules/* in alsa's compile directory into /lib/modules/.../kernel/sound, you can use "find" to get their location.
snd-hda-intel.ko
snd-hwdep.ko
snd.ko
snd-mixer-oss.ko
snd-page-alloc.ko
snd-pcm.ko
snd-pcm-oss.ko
snd-rtctimer.ko
snd-seq-device.ko
snd-seq.ko
snd-seq-midi-event.ko
snd-seq-oss.ko
snd-timer.ko

then, depmod -a

reboot, try again.

Jajajaja it works on a dv2000t, the only thing i'm struggling is with the volume... is to low, any one has  changed this:guitar:

---

### Post by ortsov on 2007-12-29
> **syxbit said:**
> 
let me know what you think
run the both scripts as sudo
sudo sh alsa1.sh
reboot
sudo sh alsa2.sh

You've done a marvelous job - it works great for me (or, more precisely, my Vostro 1500)!

Thank's a lot!

*ortsov*

---

### Post by s13_mills on 2008-01-04
Thank you syxbit for your scripts, they worked like a charm for the sound on my Asus P5K motherboard! You are a gentleman and a scholar!:)

---

### Post by doubleij on 2008-01-24
Hi, I'm having trouble running the scripts. I got them, put them in my home folder and enabled them as executables. But when I type syxbit's command sudo sh alsa1.sh i get "Can't open alsa1.sh."

This is frustrating! I'm sure it's a simple fix. Where did I go wrong?

---

### Post by doubleij on 2008-01-29
Never mind, I figured out how to open the bash scripts. Alsa conflicted with my Atheros wireless card somehow. So I had to install Alsa first and then the madwifi driver to fix the Atheros. If I installed wireless first and then Alsa, Alsa somehow broke the wireless fix and I couldn't fix it without a reinstall.

More info here.
[http://ubuntuforums.org/showthread.php?p=4229511#post4229511](http://ubuntuforums.org/showthread.php?p=4229511#post4229511)

---

### Post by monkeymind90 on 2008-03-15
Thanks man. This solved a lot of problems on my laptop!

---

### Post by AWittyUserName on 2008-04-06
At the moment it looks like those two scripts got rid of my crackles and finally got SLVoice to work for me on some level.  Thanks.

---

