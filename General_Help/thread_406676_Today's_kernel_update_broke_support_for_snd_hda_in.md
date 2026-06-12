---
title: "Today's kernel update broke support for snd_hda_intel"
date: 2007-04-11
forum: General Help
---

### Post by Pedric on 2007-04-11
hi,

after today's kernel update, my laptop's (Asus A6Va) sound card

> 00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

stopped working. lspci detects it, but it get a lot of "disagrees about version of symbol" & "unknown symbol" during booting.

This is the relevant output of dmesg:

> ~$ dmesg | grep snd
[17179604.876000] snd_timer: disagrees about version of symbol snd_info_register
[17179604.876000] snd_timer: Unknown symbol snd_info_register
[17179604.876000] snd_timer: disagrees about version of symbol snd_info_create_module_entry
[17179604.876000] snd_timer: Unknown symbol snd_info_create_module_entry
[17179604.876000] snd_timer: disagrees about version of symbol snd_info_free_entry
[17179604.876000] snd_timer: Unknown symbol snd_info_free_entry
[17179604.880000] snd_timer: disagrees about version of symbol snd_unregister_device
[17179604.880000] snd_timer: Unknown symbol snd_unregister_device
[17179604.880000] snd_timer: disagrees about version of symbol snd_device_new
[17179604.880000] snd_timer: Unknown symbol snd_device_new
[17179604.880000] snd_timer: Unknown symbol snd_info_unregister
[17179604.880000] snd_timer: Unknown symbol snd_register_device
[17179604.880000] snd_timer: disagrees about version of symbol snd_info_register
[17179604.880000] snd_timer: Unknown symbol snd_info_register
[17179604.880000] snd_timer: disagrees about version of symbol snd_info_create_module_entry
[17179604.880000] snd_timer: Unknown symbol snd_info_create_module_entry
[17179604.880000] snd_timer: disagrees about version of symbol snd_info_free_entry
[17179604.880000] snd_timer: Unknown symbol snd_info_free_entry
[17179604.880000] snd_timer: disagrees about version of symbol snd_unregister_device
[17179604.880000] snd_timer: Unknown symbol snd_unregister_device
[17179604.880000] snd_timer: disagrees about version of symbol snd_device_new
[17179604.880000] snd_timer: Unknown symbol snd_device_new
[17179604.884000] snd_timer: Unknown symbol snd_info_unregister
[17179604.884000] snd_timer: Unknown symbol snd_register_device
[17179606.392000] snd_pcm: Unknown symbol snd_timer_notify
[17179606.392000] snd_pcm: Unknown symbol snd_timer_interrupt
[17179606.396000] snd_pcm: Unknown symbol snd_timer_new
[17179609.260000] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[17179609.260000] snd_hda_codec: Unknown symbol snd_ctl_add
[17179609.260000] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
[17179609.260000] snd_hda_codec: Unknown symbol snd_card_proc_new
[17179609.260000] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[17179609.260000] snd_hda_codec: Unknown symbol snd_ctl_find_id
[17179609.260000] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[17179609.260000] snd_hda_codec: Unknown symbol snd_ctl_new1
[17179609.260000] snd_hda_codec: disagrees about version of symbol snd_component_add
[17179609.260000] snd_hda_codec: Unknown symbol snd_component_add
[17179609.260000] snd_hda_codec: disagrees about version of symbol snd_ctl_elem_read
[17179609.260000] snd_hda_codec: Unknown symbol snd_ctl_elem_read
[17179609.260000] snd_hda_codec: disagrees about version of symbol snd_ctl_elem_write
[17179609.260000] snd_hda_codec: Unknown symbol snd_ctl_elem_write
[17179609.260000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_list
[17179609.260000] snd_hda_codec: disagrees about version of symbol snd_device_new
[17179609.260000] snd_hda_codec: Unknown symbol snd_device_new
[17179609.260000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[17179609.260000] snd_hda_codec: Unknown symbol snd_pcm_format_width
[17179609.260000] snd_hda_intel: Unknown symbol snd_pcm_new
[17179609.260000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[17179609.260000] snd_hda_intel: disagrees about version of symbol snd_card_register
[17179609.260000] snd_hda_intel: Unknown symbol snd_card_register
[17179609.260000] snd_hda_intel: disagrees about version of symbol snd_card_free
[17179609.260000] snd_hda_intel: Unknown symbol snd_card_free
[17179609.260000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[17179609.260000] snd_hda_intel: Unknown symbol snd_hda_bus_new
[17179609.260000] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[17179609.260000] snd_hda_intel: Unknown symbol snd_hda_codec_new
[17179609.260000] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[17179609.260000] snd_hda_intel: disagrees about version of symbol snd_card_new
[17179609.260000] snd_hda_intel: Unknown symbol snd_card_new
[17179609.260000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[17179609.260000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[17179609.260000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[17179609.260000] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[17179609.264000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[17179609.264000] snd_hda_intel: Unknown symbol snd_hda_suspend
[17179609.264000] snd_hda_intel: disagrees about version of symbol snd_device_new
[17179609.264000] snd_hda_intel: Unknown symbol snd_device_new
[17179609.264000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[17179609.264000] snd_hda_intel: Unknown symbol snd_hda_resume
[17179609.264000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[17179609.264000] snd_hda_intel: Unknown symbol snd_hda_build_controls
[17179609.264000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed


Help!

---

### Post by uncensored on 2007-04-11
i had the same problem and fix it by compiling alsa drivers.

i am writing a how-to if you can wait for about 10 mins.

---

### Post by uncensored on 2007-04-11
1. Install necessary build tools

```
sudo apt-get install build-essential linux-headers-generic libncurses5 libncurses5-dev libasound2 libasound2-dev
```

2. Get alsa-driver alsa-lib and alsa-utils by using terminal commands

```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14rc3.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14rc2.tar.bz2
```

3. Unpack the tars

```
tar -xjvf alsa-driver-1.0.14rc3.tar.bz2
tar -xjvf alsa-lib-1.0.14rc3.tar.bz2
tar -xjvf alsa-utils-1.0.14rc2.tar.bz2
```

4. Go into the alsa-driver in your home directory and compile it.

```
cd alsa-driver-1.0.14rc3
./configure --with-oss=yes --with-cards=hda-intel
make
sudo make install
```

5. Go into the alsa-lib in your home directory and compile it.

```
cd ../alsa-lib-1.0.14rc3
./configure
make
sudo make install
```

6. Go into the alsa-utils in your home directory and compile it.

```
cd ../alsa-utils-1.0.14rc2
./configure
make
sudo make install
```

7. Configure alsa

```
sudo alsaconf
```

Select your soundcard (in my case it was the first one) and hit the default option on everything else.

8. Load the new alsa module into the kernel.

```
sudo /etc/init.d/alsasound reload
```

9. At this point you should receive messages about a soundcard being removed, as well as messages about a new soundcard being installed.

Upon reboot, there should be no problems, and audio should continue to work.


this is how i fixed that problem at my hp pavilion dv6187eu. i am writing my references below..

References:
[http://ubuntuforums.org/showthread.php?t=305712](http://ubuntuforums.org/showthread.php?t=305712)
[http://www.w1ldt4ng3nt.net/blog/item/77](http://www.w1ldt4ng3nt.net/blog/item/77)

---

### Post by Pedric on 2007-04-11
I'll give that a try

---

### Post by uncensored on 2007-04-11
waiting for your feedback..

---

### Post by wataboutbob on 2007-04-11
Hi! Have the same problem as the original poster. Soundcard not recognised after the latest update. I tried your suggestion but I've run into a roadblock with the alsa-utils.

I'm not able to compile it and when I type ./configure, right at the end I can see the following;

checking for libasound headers version >= 1.0.12... not present.
configure: error: Sufficiently new version of libasound not found.

After this, entering make install only gives an incorrect command error.

You've asked to download alsa-utils rc2 but also ask to extract and compile with alsa-utils-rc1. Not sure which one I had to use so I'd downloaded both. Makes no difference though.

FYI, the laptop is a Dell XPS M1710 with an Intel HDA card and a subwoofer... :) all of which I had working perfectly until about an hour ago............... *sigh*

---

### Post by uncensored on 2007-04-11
i ve just changed the commands for tar. sorry about that.

can you install libasound with the code below and try to compile alsa-utils rc2 again?

```
sudo apt-get install libasound2 libasound2-dev
```

if it works after this i will add the commands to the first step..

---

### Post by wataboutbob on 2007-04-11
okay... the strangest thing just happened. When the sound broke after the restart, I tried alsamixer multiple times and tried to open the volume control many times. Everytime it said there was no sound device. aplay -l gave me no sound device. I restarted the computer again and again but there was no change.

With your suggestion, I only got to compiling the driver and lib but not the utils - for the reasons mentioned above.

But now when I restarted the computer so that I can install libasound2, the sound was back! Don't know why, don't know how. Even the subwoofer. So you can see why I don't want to install libasound2 in case I break it again ;)

---

### Post by wataboutbob on 2007-04-11
okay, I thought I'll try the libasound2 for the benefit of others, but still no dice. Sorry mate, I get the same error when I try to compile alsa-utils-rc2. I guess alsaconf wont run untll the utils are compiled right? 

But alsamixer works - version 1.0.11... I'm sure I had 1.0.14 installed before.

---

### Post by uncensored on 2007-04-11
[QUOTE=wataboutbob]okay, I thought I'll try the libasound2 for the benefit of others, but still no dice. Sorry mate, I get the same error when I try to compile alsa-utils-rc2. I guess alsaconf wont run untll the utils are compiled right?

But alsamixer works - version 1.0.11... I'm sure I had 1.0.14 installed before.[/QUOTE]

thanks for your feedback. maybe somebody will use your experiences.

edit: maybe you can try to compile it again after a restart?

---

### Post by wataboutbob on 2007-04-11
you want me to install libasound or libasound2... 'cos I've already tried libasound2 and that didn't lead to the alsa-utils getting compiled.

so to install libasound the code is the same right?

sudo aptitude install libasound libasound-dev

EDIT:

okay... tried to install libasound but no such package. As already mentioned, I've already installed libasound2 and tried to compile the alsa-utils-rc2 but I'm getting the same error as before.

---

### Post by uncensored on 2007-04-11
interesting.. i ve compiled it without errors..

---

### Post by uncensored on 2007-04-11
have you tried compiling all of them after installing libasound2?

---

### Post by wataboutbob on 2007-04-11
> **uncensored said:**
> have you tried compiling all of them after installing libasound2?

yep, just tried it again. Still the same error message during configure. Anyways, I think I'll leave it to the original poster to try it and revert back to you. Thanks!

---

### Post by uncensored on 2007-04-11
thanks for your efforts..

---

### Post by CSandman on 2007-04-11
Hey uncensored,
I just followed your instructions and got through most of it without any problems.  However, when I got to the alsaconf part I ran into trouble.  The only soundcard that shows up is an SB450 chipset however after looking at my other linux install on this computer (with working sound) I found that the card that I actually have is a Generic Si3054 chipset.  Is there something I have to do differently in your instructions or something special I need to do so I can set up the alsa driver for the proper soundcard?

---

### Post by uncensored on 2007-04-11
hi CSandman,
try the default option(i think it's the first one) if it works it doesn't matter..
You wrote to your signature "ATI HDA SB450 audio" so it matches with your hardware..

---

### Post by uncensored on 2007-04-11
Hey Pedric,
haven't you tried it yet? please let me know what happened..

---

### Post by treesurf on 2007-04-11
Uncensored,

I used your instructions to reinstall alsa, the only difference being that I still had all those packages from the last time I installed them so I didn't have to download anything.  The installation went fine for me.

More importantly when I restarted my computer I had sound again!  Thank you!

---

### Post by fhco on 2007-04-12
> **uncensored said:**
> 
Awesomeness


Thank you so much. This fixed the problem for me. :)

---

### Post by kookjr on 2007-04-12
Uncensored,

Thanks!! Your instructions worked great for me, on Edgy, System76 laptop. I hope there is no conflict when a fixed apt-get package finally comes out with an updated alsa kernel module.

-mat

---

### Post by shaft350x on 2007-04-12
Uncensored, THANK YOU!

I just ran through it on my wife's laptop (A Darter from System76)

Got the sound back!

Thank you so much!

---

### Post by uncensored on 2007-04-12
thanks guys, you ve honored me.

---

### Post by syxbit on 2007-04-12
great!
i can quit whining now.
sound is fixed!
one question though, if i update linux-restricted-modules, (as i'm running feisty, and it's sure to be updapte) will i need to so this over again?

---

### Post by hamil on 2007-04-12
Thanks m8! This finally solved my sound issues also!

Had to do it in a modified way, since it tried to overwrite some existing files on my system.

---

### Post by uncensored on 2007-04-12
> **syxbit said:**
> great!
i can quit whining now.
sound is fixed!
one question though, if i update linux-restricted-modules, (as i'm running feisty, and it's sure to be updapte) will i need to so this over again?

i think yes, you should do it every time whenever kernel is updated until they integrate the latest alsa driver into the kernel, it will be necessary to do this again.

---

### Post by syxbit on 2007-04-12
until they integrate the latest alsa driver into the kernel????
then how come it used to work on kernel 2.6.20-13?
surely they didn't regress on alsa drivers?

---

### Post by irw on 2007-04-12
I cured the problem on my laptop by following the instructions here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by uncensored on 2007-04-12
> **syxbit said:**
> until they integrate the latest alsa driver into the kernel????
then how come it used to work on kernel 2.6.20-13?
surely they didn't regress on alsa drivers?

the version 1.0.14 of alsa drivers are not stable release yet so maybe they ve changed it back because of some issues.

---

### Post by uncensored on 2007-04-12
> **irw said:**
> I cured the problem on my laptop by following the instructions here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

it's almost the same thing.

---

### Post by quickwitt on 2007-04-12
Uncensored,

Thank you. i spent weeks configuring sound on my Toshiba U205 and almost freaked when it didn't work this morning. This is why I love Ubuntu.

Cheers!

---

### Post by Pedric on 2007-04-12
Finally had the time to fix it, it worked, thanks. I'll add that to my "things to do after a kernel update" list...

---

### Post by esukf on 2007-04-13
This fixed my sound on a ASUS A8JS. Thx

---

### Post by drummingpariah on 2007-04-13
> **esukf said:**
> This fixed my sound on a ASUS A8JS. Thx

What did?  I just recompiled ALSA on my A8jm, I'm fairly sure we have the same sound card.

edit* - I did fix it though... somewhat.  I re-installed, and I'll try patching in another week.  If that doesn't work, I'll give an honest shot at troubleshooting my missing sound.  Right now I have sound perfectly fine until I run updates.

---

### Post by fiatguy85 on 2007-04-13
This worked for me on a gateway mx6453.  AMD64 processor, SB450 sound.

---

### Post by alexlex on 2007-04-14
could this be why my mplayer keeps freezing fire fox after a couple minutes?

---

### Post by gene6482 on 2007-04-14
Hey everyone, 

I had a fresh install of ubuntu yesterday and sound has never worked for me, i did run updates initially before testing sound, so its possibe thats why it didnt work in the first place.  I followed these instructions, and although the commands come back with different results than before, which im sure is a step in the right direction, i still have no sound.  Any ideas?

---

### Post by drummingpariah on 2007-04-14
> **gene6482 said:**
> Hey everyone, 

I had a fresh install of ubuntu yesterday and sound has never worked for me, i did run updates initially before testing sound, so its possibe thats why it didnt work in the first place.  I followed these instructions, and although the commands come back with different results than before, which im sure is a step in the right direction, i still have no sound.  Any ideas?

Depends on what system and sound card you have.  "no sound" is a VERY generic error, and I can already see that there are multiple causes in this single thread and a lot of the posts here are unrelated to each other aside from the "sound" issue.

---

### Post by gene6482 on 2007-04-14
basically, i dont have an error at all.  And everything appears like it should be working.  But it just isnt working.  If youd like the outputs of any commands, let me know.

---

### Post by GadgetsGuy on 2007-04-15
OK .... I need help!!

The compile went smoothly for me, however when I get to alsaconf, it does not give me any options ... it tries searching automatically and does not find any PnP or PCI sound devices

I have intel 82801 (AC97) chipset

I have been 3 days without sound now, and getting frustrated to the point I am going to do something stupid and re-install Windows 2000  :(

---

### Post by jmacdonagh on 2007-04-16
I have the same problem as GadgetsGuy.

```
$ lspci
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
```

```
$ aplay -l
aplay: device_list:204: no soundcards found...

```

After compiling the newest ALSA and running alsaconf, it said it found nothing in neither the PCI nor the ISA bus:

```
$ sudo alsaconf
Building card database..
modinfo: could not find module snd-opl3sa2
modinfo: could not find module snd-cs4236
modinfo: could not find module snd-cs4232
modinfo: could not find module snd-cs4231
modinfo: could not find module snd-es18xx
modinfo: could not find module snd-es1688
modinfo: could not find module snd-sb16
modinfo: could not find module snd-sb8

```

Any ideas? This is a Dell Inspiron 8600. My roommate has the exact same laptop and installed the newest kernel package without a problem. Perhaps we can use his to debug?

Thanks

---

### Post by uncensored on 2007-04-16
i am not sure but i think ac97 is not high definiton audio chip..
if i am wrong let me know..

---

### Post by Slarbartifast on 2007-04-16
Thanks uncensored, your instructions worked great for me, only thing I had to do was after configuring with alsaconf and before reloading, I had to run alsamixer and unmute it.  My sound works again! :)

I'm running Kubuntu 6.10 on an Acer Travelmate 2480.

Thanks again!

---

### Post by GadgetsGuy on 2007-04-16
> **uncensored said:**
> i am not sure but i think ac97 is not high definiton audio chip..
if i am wrong let me know..

prior to the kernel update, i did have sound ......

---

### Post by drummingpariah on 2007-04-16
> **GadgetsGuy said:**
> prior to the kernel update, i did have sound ......

same here.  I re-installed the 7.04 today from the latest build (when sound works), and get:

```

~$ lspci
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```
on my Asus a8jm.  I'll try running the updates this week, but want to make sure we can narrow down the cause of the problem using my update as a guinea pig.  I'd like to know exactly what changes are made.  Anyone else who knows of more data i should be grabbing now, let me know.  If anyone has post-update a8jm information they'd like to post, that would be wonderful too.  Seems like we have a lot of unrelated issues in this thread, so it might be a better idea to start a new thread for each separate sound card that's broken.  just a thought.

---

### Post by sirvig on 2007-04-17
I have been goofing with this problem off and on now since the kernel update.  I had sound prior to the update and was using the 1.0.13 driver.  I lost sound after the update.  I have an HP dv6000 with Ubuntu 6.10 loaded.  

lspci shows:
> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

I followed the directions given in an earlier reply (downloaded alsa driver 1.0.14rc3, utils rc2, and lib rc3) and configured/make/make install all of them.  A reboot did not return the sound.  

I also went back to 1.0.13 driver, utils, lib and did a configure/make/make install.  This also did not help.

I have followed the troubleshooting directions located at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) to no avail.

I know the equipment still works as I can select a previous kernel from the GRUB menu and have sound.

I am fairly new to the Linux world and would really like some help with this issue.  I get the impression that upgrading to Fiesty on the 19th will not help my situation as it is still the same kernel and driver.

Thanks!

---

### Post by FatherDale on 2007-04-17
> **uncensored said:**
> 1. Install necessary build tools

this is how i fixed that problem at my hp pavilion dv6187eu. i am writing my references below..

References:
[http://ubuntuforums.org/showthread.php?t=305712](http://ubuntuforums.org/showthread.php?t=305712)
[http://www.w1ldt4ng3nt.net/blog/item/77](http://www.w1ldt4ng3nt.net/blog/item/77)


You rock. Really. :-) [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

Thanks.

fd

---

### Post by lapichiflati on 2007-04-18
[QUOTE=sirvig;2471115]
I followed the directions given in an earlier reply (downloaded alsa driver 1.0.14rc3, utils rc2, and lib rc3) and configured/make/make install all of them.  A reboot did not return the sound.  

I also went back to 1.0.13 driver, utils, lib and did a configure/make/make install.  This also did not help.

I have followed the troubleshooting directions located at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) to no avail.



Hey sirvig,

I have the HP DV2000 and I think it is basically the same sound hardware.  I had many problems with configuration until I applied to patch to the driver before making and installing.  After the latest kernel update I lost sound functionality and just went back to the directories /urs/src/alsa where I had previously downloaded the driver packages and installed them. Follow this thread for information about the patch.  Also make sure you apt-get install your dependencies.

This is where to find the patch for your sound card
[http://article.gmane.org/gmane.linux.alsa.devel/45692]("http://article.gmane.org/gmane.linux.alsa.devel/45692")

This thread will give you an idea how to apply it:
[http://ubuntuforums.org/showthread.php?t=352677&page=1]("http://ubuntuforums.org/showthread.php?t=352677&page=1")

---

### Post by drummingpariah on 2007-04-19
> **sirvig said:**
> I have been goofing with this problem off and on now since the kernel update.  I had sound prior to the update and was using the 1.0.13 driver.  I lost sound after the update.  I have an HP dv6000 with Ubuntu 6.10 loaded.  

lspci shows:


I followed the directions given in an earlier reply (downloaded alsa driver 1.0.14rc3, utils rc2, and lib rc3) and configured/make/make install all of them.  A reboot did not return the sound.  

I also went back to 1.0.13 driver, utils, lib and did a configure/make/make install.  This also did not help.

I have followed the troubleshooting directions located at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) to no avail.

I know the equipment still works as I can select a previous kernel from the GRUB menu and have sound.

I am fairly new to the Linux world and would really like some help with this issue.  I get the impression that upgrading to Fiesty on the 19th will not help my situation as it is still the same kernel and driver.

Thanks!

Exactly the same here, but I broke my old kernel's sound in the process.  Currently working on getting it back so I have a benchmark to start from.

I actually tried everything you posted, but am still getting the same results.  It looks like sound is being processed but not played, or not being transferred to output correctly.  XMMS, for example is showing as active, and will play through an entire song totally oblivious to the face that I'm getting nothing but visual notification that it's working.  Still working on it, but I don't expect to have sound back any time soon.  I'm sure our devs are focused on much more important problems, not just the missing sound for a few users with a specific sound card.

---

### Post by sirvig on 2007-04-20
Just FYI:

The upgrade to Fiesty restored my sound so ignore my last.

Thanks

---

### Post by seesixty on 2007-04-20
Hi there, I've tried everything on this thread to no avail.
I have a toshiba satellite A100 with the hda-intel sound module,  When I run alsaconf it correctly detects it but it still doesn't appear in alsa mixer. I've tried downloading and compiling the latest alsa, Adding the specific line in /etc/modprobe.d/alsa-base. 

 I noticed a line in dmesg which might be suggesting a problem

ACPI: PCI interrupt for device 0000:00:14.2 disabled
ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 20

Which is my soundcard.  I did get this soundcard working with hurd 5 using 2.6.20-9 kernel but installing the latest feisty breaks the sound with kernel 2.6.20-15.

Any suggestions to try would be muchly appreciated.

---

### Post by rrwo on 2007-04-20
I tried all of that. It doesn't help!

I do get an error when building alsa-utils:
```

speaker-test.c: In function ‘main’:
speaker-test.c:767: error: ‘LC_ALL’ undeclared (first use in this function)
speaker-test.c:767: error: (Each undeclared identifier is reported only once
speaker-test.c:767: error: for each function it appears in.)
make[2]: *** [speaker-test.o] Error 1

```

---

### Post by cwalte on 2007-04-24
Uncensored you are a hero!!!!!

I've been trying for a year to get sound working on my Easynote and thanks to your howto it works! I now have Last Town Chorus  with Modern Love playing through the speakers, fantastic.

One bit of advice for others, when I first reloaded the drivers (sudo /etc/init.d/alsasound reload) nothing happended but second time there was a pop an lo and behold, sound!!!

Thanks again!!:K

---

### Post by mooter on 2007-05-08
This helped!
Thank you very much!

---

### Post by sorgud on 2007-07-18
Uncensored
you rock!
I've been a week trying to fix this sound problem.
Fresh Install of kubuntu 7.04 Feisty in a Asus M2N-MX.
When I enter in my user (KDE desktop) a high pitch sound happens. I open kmixer.
Then clicking in the speakers-front the high pitch sound dissapear and with it the sound.
I follow the instructions using the LinuxDrivers that came in the Asus CD instalation.
And I get the sound to work!! THANKS.
But....
Then, **if** I don't enter in my KDE desktop I have full sound.
When I enter to my desktop, the sound dissapear until I reboot (without entering in KDE desktop).
I guess the problem is some kind of incompatibility with the KDE sound system...
any clue?
talueguito
raul

---

### Post by sorgud on 2007-07-18
SOLVED!
I took a look at the Alsa page dealing with KDE:
[http://alsa.opensrc.org/index.php/Dmix_Kde_-_arts%2C_ESD_and_SDL_quick_and_dirty_HOWTO](http://alsa.opensrc.org/index.php/Dmix_Kde_-_arts%2C_ESD_and_SDL_quick_and_dirty_HOWTO)

Well I enter the Kmenu->Systems Settings->Sound System->Hardware
In "Select the audio device" I selected:
Enlightment Sound Daemon
Exit from my user and when I re-enter the sound was working.
I also tested rebooting the machine and the sound is still there.
Thanks
talueguito
raul

---

