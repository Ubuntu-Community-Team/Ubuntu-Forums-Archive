---
title: "Alsa Woes (Help Needed)"
date: 2007-01-03
forum: General Help
---

### Post by Cefka on 2007-01-03
I use a Gateway mx6453, dual booting between Kubuntu Linux (6.06 LTS with kernel v. 2.6.15-26-amd64-generic) and Microsoft Windows XP Media Center Edition.  There've been a few posts in recent months that users of some Gateway computers with Sigmatel 9000 series codecs have sound problems with Linux because Alsa hasn't been able to play nicely with it (ex. ["Sadly, it's back to Windows for this laptop"]("http://ubuntuforums.org/showthread.php?t=280987")).  

Someone on the newsgroup gmane.linux.alsa.devel has been working on a patch so Gateway computers with these codecs can have sound in Linux.  Just a couple days ago, a patch emerged claiming it adds support for the codecs in Alsa (ex. [http://thread.gmane.org/gmane.linux.alsa.devel/43460/focus=43460]("http://thread.gmane.org/gmane.linux.alsa.devel/43460/focus=43460"))  Following instructions that the maker left for a past test version of this patch ([http://thread.gmane.org/gmane.linux.alsa.devel/42922/focus=42922]("http://thread.gmane.org/gmane.linux.alsa.devel/42922/focus=42922")), I managed to patch it to a download of alsa-driver-1.0.14rc1, compile it, and install it.  I did the following:

```
tar -jxvf alsa-driver-1.0.14rc1.tar.bz2
cd alsa-driver-1.0.14rc1/alsa-kernel
patch -p1 <gateway.patch
cd ..
./configure --with-cards=hda-intel --with-debug=detect
sudo make
sudo make install
sudo dmesg -c >/dev/null
sudo modprobe -r snd-hda-intel
sudo modprobe snd-hda-intel
```

Everything worked perfectly well until I got to the final step: reinserting snd-hda-intel.  I got this.

> WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.15-26-amd64-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.15-26-amd64-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)


And dmesg.out yielded me this.
> [  331.478791] snd_hda_codec: Unknown symbol snd_verbose_printd
[  331.478949] snd_hda_codec: Unknown symbol snd_hidden_kzalloc
[  331.479081] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[  331.479189] snd_hda_codec: Unknown symbol snd_ctl_add
[  331.479321] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
[  331.479437] snd_hda_codec: Unknown symbol snd_card_proc_new
[  331.479578] snd_hda_codec: Unknown symbol snd_hidden_kcalloc
[  331.479711] snd_hda_codec: Unknown symbol snd_hidden_kfree
[  331.479840] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[  331.479954] snd_hda_codec: Unknown symbol snd_ctl_find_id
[  331.480082] snd_hda_codec: Unknown symbol snd_verbose_printk
[  331.480216] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[  331.480330] snd_hda_codec: Unknown symbol snd_ctl_new1
[  331.480457] snd_hda_codec: disagrees about version of symbol snd_component_add
[  331.480573] snd_hda_codec: Unknown symbol snd_component_add
[  331.480706] snd_hda_codec: disagrees about version of symbol snd_iprintf
[  331.480819] snd_hda_codec: Unknown symbol snd_iprintf
[  331.480938] snd_hda_codec: disagrees about version of symbol snd_ctl_elem_read
[  331.481054] snd_hda_codec: Unknown symbol snd_ctl_elem_read
[  331.481203] snd_hda_codec: disagrees about version of symbol snd_ctl_elem_write
[  331.481320] snd_hda_codec: Unknown symbol snd_ctl_elem_write
[  331.481496] snd_hda_codec: Unknown symbol snd_hidden_kstrdup
[  331.481628] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_list
[  331.481762] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_list
[  331.481900] snd_hda_codec: disagrees about version of symbol snd_device_new
[  331.482012] snd_hda_codec: Unknown symbol snd_device_new
[  331.482204] snd_hda_codec: Unknown symbol snd_pci_quirk_lookup
[  331.482341] snd_hda_codec: Unknown symbol snd_hidden_kmalloc
[  331.482469] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step
[  331.482603] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[  331.482741] snd_hda_codec: disagrees about version of symbol snd_pcm_format_width
[  331.482861] snd_hda_codec: Unknown symbol snd_pcm_format_width
[  331.483758] snd_hda_intel: Unknown symbol snd_verbose_printd
[  331.483905] snd_hda_intel: Unknown symbol snd_hidden_kzalloc
[  331.484057] snd_hda_intel: Unknown symbol snd_free_irq
[  331.484198] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[  331.484313] snd_hda_intel: Unknown symbol snd_pcm_new
[  331.484442] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[  331.484572] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[  331.484720] snd_hda_intel: disagrees about version of symbol snd_card_register
[  331.484844] snd_hda_intel: Unknown symbol snd_card_register
[  331.484978] snd_hda_intel: disagrees about version of symbol snd_card_free
[  331.485095] snd_hda_intel: Unknown symbol snd_card_free
[  331.485222] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  331.485373] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  331.485556] snd_hda_intel: Unknown symbol snd_hda_bus_new
[  331.485723] snd_hda_intel: Unknown symbol snd_hidden_kcalloc
[  331.485873] snd_hda_intel: Unknown symbol snd_hidden_kfree
[  331.486027] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[  331.486179] snd_hda_intel: Unknown symbol snd_verbose_printk
[  331.486318] snd_hda_intel: Unknown symbol snd_hda_codec_new
[  331.486527] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[  331.486675] snd_hda_intel: disagrees about version of symbol snd_card_new
[  331.486791] snd_hda_intel: Unknown symbol snd_card_new
[  331.486917] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  331.487051] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[  331.487210] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[  331.487333] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[  331.487468] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[  331.487600] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[  331.487744] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[  331.487893] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[  331.488014] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[  331.488166] snd_hda_intel: Unknown symbol snd_hda_suspend
[  331.488297] snd_hda_intel: disagrees about version of symbol snd_device_new
[  331.488422] snd_hda_intel: Unknown symbol snd_device_new
[  331.488563] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[  331.488690] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[  331.488828] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[  331.488953] snd_hda_intel: Unknown symbol snd_card_disconnect
[  331.489093] snd_hda_intel: Unknown symbol snd_hda_resume
[  331.489221] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[  331.489362] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[  331.489528] snd_hda_intel: Unknown symbol snd_hda_build_controls
[  331.489708] snd_hda_intel: Unknown symbol snd_hidden_kmalloc
[  331.489848] snd_hda_intel: Unknown symbol snd_request_irq
[  331.490015] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[  331.490145] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed


I also get this when I try launching alsamixer:
> alsamixer: function snd_ctl_open failed for default: No such device


The developer said more work has to be done before this is placed in the final release of Alsa, but I have a feeling something is screwing up because of what I've done.  I've tried googling the problem, but couldn't find things that were of too much help.  Could anyone tell me where I might have gone wrong in the process of patching, compiling, and installing the module and how I could go about fixing it?

-Cefka

---

### Post by Cefka on 2007-01-03
Nevermind.  A reboot fixed the problem.  After rebooting I tired doing sudo modprobe snd-hda-intel again and it worked.  It recognizes the sound card, but sadly the patch seems ineffective.

Sorry Gateway/Sigmatel users who have no sound.  This patch still seems to be a dud.  I continue to get the "invalid dep_range" that's been plaguing previous patches. :(

---

### Post by mekas2024 on 2007-01-14
Hello dude, i have a problem here... im not so newbe but.. i dont understand the instructions... i dont know what to do in this part:

patch -p1 <gateway-mp6954.patch.6

Please could u help me... this is really driving me crazy without sound !

I hope u could hepl me

Regards

Atte MeKaS

---

### Post by PolarByte on 2007-02-16
Hi mekas2024 ,

Try applying the patch when you are in the alsa-kernel directory under alsa-driver-1.0.14rc1.
Eg. something along the lines of:

```
tar xvjf alsa-driver-1.0.14rc1.tar.bz2 
cp gateway-mp6954.patch.6 alsa-driver-1.0.14rc1/alsa-kernel/
cd alsa-driver-1.0.14rc1/alsa-kernel/
patch -p1 --verbose < gateway-mp6954.patch.6
```

The '--verbose' just shows you what's happening, if you're curious about it.
In general, when you want to apply patches you can do ...
```
head <patch_file>
```
... and the first line usually gives a hint in which directory to be for applying the patch. In our case the first line says
```
diff -r 1ede4dc9b6ea pci/hda/patch_sigmatel.c
```
which is under  alsa-driver-1.0.14rc1/alsa-kernel/ . So you go there for applying the patch and then all pieces should fall in place.

Regards,
PolarByte

---

### Post by Truefire on 2008-03-15
7.10-8.04 support it on that laptop by default.

---

