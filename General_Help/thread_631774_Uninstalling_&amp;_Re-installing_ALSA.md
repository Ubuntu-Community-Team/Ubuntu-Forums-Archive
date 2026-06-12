---
title: "Uninstalling &amp; Re-installing ALSA"
date: 2007-12-04
forum: General Help
---

### Post by Patriot1776 on 2007-12-04
Well, I really screwed myself up. In a bid to fix a microphone problem, I re-downloaded ALSA 1.0.14, and tried to re-install it without first removing the ALSA I currently had. Now I've got no sound at all, no KMix says no mixing devices available. What do I do now?  Running Gutsy.

---

### Post by ZipoTe on 2007-12-04
By installing ALSA you mean alsa-tools and alsa-utils? If yes, runnig alsaconf should be all :-s

---

### Post by Patriot1776 on 2007-12-04
No, misguided I was trying to re-install the WHOLE THING.  Lemme guess.  I've screwed up to where I'm going to have completely re-install Ubuntu aren't I?  I was trying to do it manually by downloading the package myself, using './configure && make && make install'.  At 'make install' it gives me a warning message saying the mixers or something are muted by default, and since restarting, KMix icon has a red 'X' on it meaning it must not see the soundcard, and 'alsaconf' is not working either.

---

### Post by Patriot1776 on 2007-12-04
It should be noted too, that the computer does see my soundcard.  Running 'lspci' gives the following:

```

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
05:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)

```

'alsaconf' doesn't work, and 'alsamixer' returns this:

```

alsamixer: function snd_ctl_open failed for default: No such device

```

---

### Post by Patriot1776 on 2007-12-04
More debug info if it'll help:

```

lsmod | grep snd
snd_pcm_oss            44800  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                81028  1 snd_pcm_oss
snd_seq_dummy           4996  0
snd_seq_oss            35328  0
snd_seq_midi            9728  0
snd_rawmidi            26112  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54256  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24452  2 snd_pcm,snd_seq
snd_seq_device          9740  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56452  9 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11272  1 snd_pcm

```

As well as:

```

cat /proc/asound/cards
--- no soundcards ---

```

Finally:

```

sudo /etc/init.d/alsasound start
[sudo] password for noah:
ALSA driver is already running.

```

Alright, with this info, now what?

---

### Post by Patriot1776 on 2007-12-04
New discovery: Mousing over the KMix icon it says 'Mixer cannot be found.'

Am I not going to get any help simply because I've simply not posted in the 'Absolute Beginner Talk' section and this is more of a beginner's question?

---

### Post by ZipoTe on 2007-12-05
> cat /proc/asound/cards
--- no soundcards ---

You have to compile alsa-tools and alsa-utils. Then use alsaconf to set your card and alsamixer to define the volume settings of the card you selected.

Report the errors of the compilation

Or, if your soundcard is not detected and you know the exact snd-XXXX of it, you can use the command "modconf" to load it.

By the way:
> Am I not going to get any help simply because I've simply not posted in the 'Absolute Beginner Talk' section and this is more of a beginner's question?
 
You're asking for help so be polite
;-)

---

### Post by Patriot1776 on 2007-12-05
I apologize then. :(  I guess I still am more of a newbie than I thought, and was panicking when I was making all these posts.

---

### Post by Patriot1776 on 2007-12-05
How do I find out the snd-XXXX of my card?  Its the 'Audio Device' up there listed in the lspci results and is onboard.

---

### Post by ZipoTe on 2007-12-05
Don't worry, just start by the beggining. All the tools you need are here [http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page") Be patient. I use debian and i have had lots of problems with sound ;) kernel not loading the module, cards not detected... but i solved it all, just being patient.

Start with alsaconf :) it will do a search and let you know the name of the snd-XXXX wich your system uses

**EDIT**

what is the model of your sound card?

---

### Post by Patriot1776 on 2007-12-05
Right here:

Intel Corporation 82801G

Onboard Sound chip/card is what it is.

The whole reason I started all of this is because I can't get my microphone working either.  I'll have to tackle this later today, I'm off to cardiac rehab.

---

### Post by Patriot1776 on 2007-12-05
Think I may have found the problem:

```
sudo modprobe snd-hda-intel ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Where's dmesg at?

---

### Post by Patriot1776 on 2007-12-05
Dmesg:

```

[  634.200000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[  634.200000] snd_hda_intel: Unknown symbol snd_ctl_add
[  634.200000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[  634.200000] snd_hda_intel: Unknown symbol snd_pcm_new
[  634.200000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[  634.200000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[  634.200000] snd_hda_intel: disagrees about version of symbol snd_card_register
[  634.200000] snd_hda_intel: Unknown symbol snd_card_register
[  634.200000] snd_hda_intel: disagrees about version of symbol snd_card_free
[  634.200000] snd_hda_intel: Unknown symbol snd_card_free
[  634.200000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  634.200000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  634.200000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[  634.200000] snd_hda_intel: Unknown symbol snd_card_proc_new
[  634.200000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[  634.200000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[  634.200000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[  634.200000] snd_hda_intel: Unknown symbol snd_ctl_new1
[  634.200000] snd_hda_intel: disagrees about version of symbol snd_component_add
[  634.200000] snd_hda_intel: Unknown symbol snd_component_add
[  634.200000] snd_hda_intel: disagrees about version of symbol snd_card_new
[  634.200000] snd_hda_intel: Unknown symbol snd_card_new
[  634.204000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  634.204000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[  634.204000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[  634.204000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[  634.204000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[  634.204000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[  634.204000] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[  634.204000] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[  634.204000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[  634.204000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[  634.204000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[  634.204000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[  634.204000] snd_hda_intel: disagrees about version of symbol snd_device_new
[  634.204000] snd_hda_intel: Unknown symbol snd_device_new
[  634.204000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[  634.204000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[  634.204000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[  634.204000] snd_hda_intel: Unknown symbol snd_card_disconnect
[  634.204000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[  634.204000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[  634.204000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[  634.204000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[  634.204000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[  634.204000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step

```

I think the thing is I've just got the wrong version of ALSA.  my last 7.04 kernel, 2.6.20-16-generic, was using ALSA 1.0.14rc1 to get the sound job done.  I've tried installing ALSA 1.0.15 here, and that's the message I'm getting trying to load the snd-hda-intel module into my 2.6.22-14-generic kernel.

Any new suggestions?

EDIT - Or better yet, what version of ALSA did Gutsy Gibbon come with and what things are Ubuntu-specific to ALSA and how do I install them?  The obvious route of synaptic?  I'm thinking then I'll have re-install 1.0.14 of ALSA then.

---

### Post by Patriot1776 on 2007-12-06
SOLVED!!

Decided to, after killing the non-working ALSA drivers, to go into /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/ and deleted snd-hda-intel.ko and then re ran ./configure, 'sudo make', and 'sudo make install' in /usr/src/alsa/alsa-driver-1.0.15

Rebooted, and heard the telltale 'thump' from the speakers I'm supposed to hear when ALSA kicks in meaning it loaded up this time!! YES!!  Sound is now working!!  I'm guess the snd-hda-intel.ko I deleted was from a previous version and wasn't getting replaced, to explain why it wasn't compatible with the kernel.  Now working on what caused all this trouble in the first place: getting my mic to work.  I'm going to look at it now from the module config side of things.

---

### Post by ZipoTe on 2007-12-07
Oh, i see you solved it!! great!! :) I thought it would be harder... nice work!

---

### Post by Hoppiesbox on 2007-12-07
Just wanted to post a big "thank you". Thanks a lot Patriot1776 and ZipoTe. It's so funny, but I've been having the EXACT same problem(including the cause, lol) starting the day you posted this Patriot, but only yesterday did I find this post, which you had already solved.

I'm a beginner myself, so when you didn't mention exactly how you removed the alsa, it took me a bit. I did finally just use
```

sudo apt-get remove alsa-base alsa-utils
sudo rm /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko

```
I may have used the --purge option for removing alsa, can't recall

Then I went to my /usr/src/alsa/alsa-drivers1.0.0.15 (or whatever, I'm at work) and did just like you wrote in your earlier post:
```

sudo ./configure && sudo make && sudo make install
sudo reboot

```

Worked like a charm. Anyway - just wanted to give some more details and say thanks for posting on the forum. And thank you ZipoTe for your support! YAY for the Linux community! I do agree with many that this type of thing is quite annoying compared to windoze, but:
1. I hate billionaires.
2. I love a challenge.
3. Linux computing is fun and satisfying.

Now that I've got sound, watching videos was just that much better. I did it - and I could feel my nerdiness increasing - thats the best part isn't it? ;)

---

### Post by Patriot1776 on 2007-12-07
Yep.  Solving problems like this in Linux, while challenging, does give one a great sense of accomplishment when you do get it to work.  Now, onto the next sound challege: getting my microphone to work, the reason I started all this monkeying around to begin with.  It's still not working.

---

### Post by sheleztt on 2008-01-02
Hey :) I had the very same problem as you guys !
Thanks a Lot. :)
Community is great. )

Good Luck.

---

### Post by sergiom99 on 2008-01-03
Thanks guys, this help me fixed my sound issues (well, sort of)
I still have to get my laptop's front speaker jack to disable main speakers.

Thanks.

---

### Post by Hoppiesbox on 2008-01-03
Ahoy!
Give this link a try:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
It's the best I've found - I think I used method E the first time, then Method H after my last install.

Cheers!

---

### Post by Patriot1776 on 2008-01-03
Does the link have instructions for activating front headphone and mic jacks?  All three of my rear jacks have been taken up by a surround sound speaker system, so right now, I'm convinced I cannot have a working mic in Linux unless I lose the surround speakers.

---

### Post by sergiom99 on 2008-01-03
OK, guess I am a lucky noob!!!
I uninstalled and re-installed as explained in this post. Then rebooted, and got my sound back!
I added the line "options snd-hda-intel model=laptop" to /etc/modprobe.d/alsa-base even though it was empy, rebooted and got sound from my headphones and not on the speakers.
(I am listening as I type)

now the only thing left to finish setting this baby up is to disable the KDE Help Center from popping up everytime I press the synaptics touchpad on/off button.
Looked in the places you guys told me but found nothing. I use KUBUNTU GUTSY 32.

---

### Post by Hoppiesbox on 2008-01-04
> **Patriot1776 said:**
> Does the link have instructions for activating front headphone and mic jacks?  All three of my rear jacks have been taken up by a surround sound speaker system, so right now, I'm convinced I cannot have a working mic in Linux unless I lose the surround speakers.

Yeah patriot, the link I posted is exactly for that - check around method E nearer the bottom of the page, it should describe what it's supposed to fix - but there are other methods on the page which may work best for your exact hardware - I've got a Toshiba P205-S6347, and method E made my front headphone work - I'm using the "internal" mic at the moment and do not own another mic to plug into my front jack - but I'd assume it works. Let me know what luck you have/what method you end up using :)

---

### Post by ICouldBeatSimon on 2008-01-10
> **Patriot1776 said:**
> SOLVED!!

Decided to, after killing the non-working ALSA drivers, to go into /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/ and deleted snd-hda-intel.ko and then re ran ./configure, 'sudo make', and 'sudo make install' in /usr/src/alsa/alsa-driver-1.0.15

Rebooted, and heard the telltale 'thump' from the speakers I'm supposed to hear when ALSA kicks in meaning it loaded up this time!! YES!!  Sound is now working!!  I'm guess the snd-hda-intel.ko I deleted was from a previous version and wasn't getting replaced, to explain why it wasn't compatible with the kernel.  Now working on what caused all this trouble in the first place: getting my mic to work.  I'm going to look at it now from the module config side of things.

Yeah...I tried doing that and I got some weird command prompt.  No GUI interface.  Luckily, i didn't remove the file so I was able to move it back.  I still have no GUI interface after moving it back.

However, I don't think this was the problem.  I also ran this command:

sudo apt-get remove alsa-base alsa-utils

I bet this is what caused it.  Anyone have any ideas how to reverse my HUGE mistake?

Oh, and I'd greatly appreciate some guidance on how to install the sound from the beginning :)

---

### Post by Patriot1776 on 2008-01-10
> **Hoppiesbox said:**
> Yeah patriot, the link I posted is exactly for that - check around method E nearer the bottom of the page, it should describe what it's supposed to fix - but there are other methods on the page which may work best for your exact hardware - I've got a Toshiba P205-S6347, and method E made my front headphone work - I'm using the "internal" mic at the moment and do not own another mic to plug into my front jack - but I'd assume it works. Let me know what luck you have/what method you end up using :)

I'll try it then.  But another problem I've now got since implementing the fix I mentioned is that now my mixers don't work, including the software-based volume control.  I need to reinstall alsa-utils then?  What kernel module is associated with them so I can uninstall and reinstall the ALSA Utilities?

---

### Post by ICouldBeatSimon on 2008-01-11
OK! I'm back up-and-running.  Now.  How about a little clarification of procedure here?

Do I install alsa v1.0.15rc1? If so, which method do you suggest?

Patriot, could you help me out with this one?  You seem like you know what your doing :).

---

### Post by ICouldBeatSimon on 2008-01-11
I followed your steps as far as reinstalling alsa v1.0.15.  When I tried to navidate to /usr/src/alsa/alsa-driver-1.0.15, it didn't work.  I could, however, navigate to the snd-hda-intel.ko file.  I moved that to a safe place, just in case.  I'm now reinstalling alsa with a method I found elsewhere.

[URL="http://donnieknows.com/bin/view/Main/GatewayML3109"]
Donnie's Instructions
[/URL]

What I'm confused about is why you have the alsa-driver-1.0.15 directory.  I'm installing the same files from the same website listed earlier in this post by ZipoTe.

Could someone shed some light on the issue?

---

### Post by ICouldBeatSimon on 2008-01-11
Well!  You all can ignore my previous post! It worked!

I used Donnie's method to initially install, restarted latptop, removed the snd-hda-intel.ko file, then reinstalled!

I'd give an official thanks to Patriot, but I'm not sure how to do that yet...:lolflag:

---

### Post by Patriot1776 on 2008-01-11
I believe the reason why it worked is because the .ko files are 'kernel object' files.  What you're doing when you use the './configure', 'sudo make', and 'sudo make install' I believe is you're just compiling the .ko files that are actually loaded at boottime by the kernel.

---

### Post by Patriot1776 on 2008-01-19
ALRIGHT!!  I now have my front mic and jacks working!!!

After ignoring the problem for several days, by chance I decided to open alsamixer up and was able to select 'Front Mic' on Input So on the 'Capture' tab,and now my front mic works!

After diong some more testing, my front headphone jack now works as well.

---

