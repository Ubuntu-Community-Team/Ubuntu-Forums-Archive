---
title: "Problem with sound modules after kernel compile"
date: 2008-04-01
forum: General Help
---

### Post by P3P on 2008-04-01
Hi,

**My hardware:**

Motherboard [ASUS P5K-E Wifi/AP](http://es.asus.com/products.aspx?l1=3&l2=11&l3=534&l4=0&model=1655&modelmenu=2), Chipsets Intel P35 and ICH9R

CPU Intel Core 2 Duo E6750

Sound (integrated) [Intel HD Audio](http://www.intel.com/design/chipsets/hdaudio.htm) 8 channels with chip [ADI AD1988B](http://www.analog.com/en/prod/0,2877,AD1988B,00.html).

**My software:**

Kubuntu 8.04 amd64 beta (but I think that this issue is not related to the beta status)

Kernel 2.6.24-12-generic (official Ubuntu kernel) and Kernel custom 2.6.24-git (compiled March-31 from ubuntu kernel git repository)



**The problem:**

I have installed Kubuntu 8.04 amd64 and the sound works well. However I should patch the kernel to add support for RAID5 target, because I have a RAID5 array in my integrated raid controller.

I have followed the [Kernel Compile](https://help.ubuntu.com/community/Kernel/Compile) guide from Ubuntu *community* documentation. I have downloaded git kernel sources, patched sources, configured alsa as a module (OSS not configured even as a module), and compiled kernel and linux-resticted-modules.
You can view the kernel config file attached to this post.

But when booting from custom kernel there is none sound device.

I have followed [Comprehensive Sound Problem Solutions Guide](http://ubuntuforums.org/showpost.php?p=1191847&postcount=1) too, and got the same error messages.

During boot I get error messages when loading sound modules. The output of dmesg is:
> [ 2814.152108] snd: disagrees about version of symbol kill_fasync
[ 2814.152113] snd: Unknown symbol kill_fasync
[ 2814.152369] snd: disagrees about version of symbol fasync_helper
[ 2814.152371] snd: Unknown symbol fasync_helper
[ 2814.153031] snd_hwdep: Unknown symbol snd_info_register
[ 2814.153063] snd_hwdep: Unknown symbol snd_info_create_module_entry
[ 2814.153093] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl_compat
[ 2814.153123] snd_hwdep: Unknown symbol snd_info_free_entry
[ 2814.153158] snd_hwdep: Unknown symbol snd_unregister_oss_device
[ 2814.153192] snd_hwdep: Unknown symbol snd_verbose_printk
[ 2814.153222] snd_hwdep: Unknown symbol snd_register_oss_device
[ 2814.153253] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[ 2814.153283] snd_hwdep: Unknown symbol snd_card_file_add
[ 2814.153319] snd_hwdep: Unknown symbol snd_iprintf
[ 2814.153348] snd_hwdep: Unknown symbol snd_major
[ 2814.153389] snd_hwdep: Unknown symbol snd_unregister_device
[ 2814.153421] snd_hwdep: Unknown symbol snd_device_new
[ 2814.153460] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[ 2814.153498] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[ 2814.153530] snd_hwdep: Unknown symbol snd_lookup_minor_data
[ 2814.153560] snd_hwdep: Unknown symbol snd_ctl_register_ioctl_compat
[ 2814.153592] snd_hwdep: Unknown symbol snd_card_file_remove
[ 2814.153621] snd_hwdep: Unknown symbol snd_register_device_for_dev
[ 2814.154023] snd_timer: Unknown symbol snd_info_register
[ 2814.154054] snd_timer: Unknown symbol snd_info_create_module_entry
[ 2814.154061] snd_timer: disagrees about version of symbol kill_fasync
[ 2814.154062] snd_timer: Unknown symbol kill_fasync
[ 2814.154092] snd_timer: Unknown symbol snd_info_free_entry
[ 2814.154149] snd_timer: Unknown symbol snd_verbose_printk
[ 2814.154187] snd_timer: Unknown symbol snd_iprintf
[ 2814.154231] snd_timer: Unknown symbol snd_ecards_limit
[ 2814.154237] snd_timer: disagrees about version of symbol fasync_helper
[ 2814.154239] snd_timer: Unknown symbol fasync_helper
[ 2814.154269] snd_timer: Unknown symbol snd_oss_info_register
[ 2814.154299] snd_timer: Unknown symbol snd_unregister_device
[ 2814.154334] snd_timer: Unknown symbol snd_device_new
[ 2814.154402] snd_timer: Unknown symbol snd_register_device_for_dev
[ 2814.175360] snd: disagrees about version of symbol kill_fasync
[ 2814.175363] snd: Unknown symbol kill_fasync
[ 2814.175606] snd: disagrees about version of symbol fasync_helper
[ 2814.175607] snd: Unknown symbol fasync_helper
[ 2814.176817] snd_timer: Unknown symbol snd_info_register
[ 2814.176849] snd_timer: Unknown symbol snd_info_create_module_entry
[ 2814.176855] snd_timer: disagrees about version of symbol kill_fasync
[ 2814.176857] snd_timer: Unknown symbol kill_fasync
[ 2814.176887] snd_timer: Unknown symbol snd_info_free_entry
[ 2814.176944] snd_timer: Unknown symbol snd_verbose_printk
[ 2814.176982] snd_timer: Unknown symbol snd_iprintf
[ 2814.177026] snd_timer: Unknown symbol snd_ecards_limit
[ 2814.177032] snd_timer: disagrees about version of symbol fasync_helper
[ 2814.177033] snd_timer: Unknown symbol fasync_helper
[ 2814.177063] snd_timer: Unknown symbol snd_oss_info_register
[ 2814.177093] snd_timer: Unknown symbol snd_unregister_device
[ 2814.177129] snd_timer: Unknown symbol snd_device_new
[ 2814.177196] snd_timer: Unknown symbol snd_register_device_for_dev
[ 2814.180176] snd_pcm: Unknown symbol snd_info_register
[ 2814.180208] snd_pcm: Unknown symbol snd_info_create_module_entry
[ 2814.180238] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl_compat
[ 2814.180294] snd_pcm: Unknown symbol snd_timer_notify
[ 2814.180300] snd_pcm: disagrees about version of symbol kill_fasync
[ 2814.180302] snd_pcm: Unknown symbol kill_fasync
[ 2814.180307] snd_pcm: disagrees about version of symbol fget
[ 2814.180309] snd_pcm: Unknown symbol fget
[ 2814.180338] snd_pcm: Unknown symbol snd_timer_interrupt
[ 2814.180368] snd_pcm: Unknown symbol snd_info_free_entry
[ 2814.180398] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[ 2814.180436] snd_pcm: Unknown symbol snd_info_get_str
[ 2814.180516] snd_pcm: Unknown symbol snd_verbose_printk
[ 2814.180586] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[ 2814.180616] snd_pcm: Unknown symbol snd_card_file_add
[ 2814.180653] snd_pcm: Unknown symbol snd_iprintf
[ 2814.180662] snd_pcm: disagrees about version of symbol fput
[ 2814.180663] snd_pcm: Unknown symbol fput
[ 2814.180703] snd_pcm: Unknown symbol snd_major
[ 2814.180719] snd_pcm: disagrees about version of symbol fasync_helper
[ 2814.180720] snd_pcm: Unknown symbol fasync_helper
[ 2814.180777] snd_pcm: Unknown symbol snd_unregister_device
[ 2814.180812] snd_pcm: Unknown symbol snd_timer_new
[ 2814.180842] snd_pcm: Unknown symbol snd_device_new
[ 2814.180903] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[ 2814.180952] snd_pcm: Unknown symbol snd_lookup_minor_data
[ 2814.180981] snd_pcm: Unknown symbol snd_ctl_register_ioctl_compat
[ 2814.181022] snd_pcm: Unknown symbol snd_info_create_card_entry
[ 2814.181052] snd_pcm: Unknown symbol snd_power_wait
[ 2814.181086] snd_pcm: Unknown symbol snd_device_free
[ 2814.181142] snd_pcm: Unknown symbol snd_card_file_remove
[ 2814.181171] snd_pcm: Unknown symbol snd_register_device_for_dev
[ 2814.181248] snd_pcm: Unknown symbol snd_device_register
[ 2814.181279] snd_pcm: Unknown symbol snd_info_get_line
[ 2814.187930] snd_hda_intel: Unknown symbol snd_ctl_add
[ 2814.187973] snd_hda_intel: Unknown symbol snd_pcm_new
[ 2814.188012] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[ 2814.188045] snd_hda_intel: Unknown symbol snd_card_register
[ 2814.188074] snd_hda_intel: Unknown symbol snd_card_free
[ 2814.188104] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[ 2814.188134] snd_hda_intel: Unknown symbol snd_card_proc_new
[ 2814.188229] snd_hda_intel: Unknown symbol snd_ctl_find_id
[ 2814.188269] snd_hda_intel: Unknown symbol snd_verbose_printk
[ 2814.188326] snd_hda_intel: Unknown symbol snd_ctl_new1
[ 2814.188391] snd_hda_intel: Unknown symbol snd_component_add
[ 2814.188428] snd_hda_intel: Unknown symbol snd_card_new
[ 2814.188458] snd_hda_intel: Unknown symbol snd_iprintf
[ 2814.188491] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[ 2814.188520] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info
[ 2814.188561] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[ 2814.188593] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[ 2814.188623] snd_hda_intel: Unknown symbol snd_hwdep_new
[ 2814.188658] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[ 2814.188695] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[ 2814.188734] snd_hda_intel: Unknown symbol snd_device_new
[ 2814.188780] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[ 2814.188822] snd_hda_intel: Unknown symbol snd_card_disconnect
[ 2814.188851] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[ 2814.188927] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[ 2814.188998] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[ 2814.189028] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[ 2814.189078] snd_hda_intel: Unknown symbol snd_pcm_format_width



When I try to load snd-hda-intel module via modprobe the output is:
> sudo modprobe snd-hda-intel
FATAL: Error inserting snd (/lib/modules/2.6.24-13-generic/ubuntu/sound/alsa-driver/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.24-13-generic/ubuntu/sound/alsa-driver/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-13-generic/ubuntu/sound/alsa-driver/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.24-13-generic/ubuntu/sound/alsa-driver/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-13-generic/ubuntu/sound/alsa-driver/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.24-13-generic/ubuntu/sound/alsa-driver/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.24-13-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)


I suppose that there is any problem with kernel modules, but I am newbie on kernel compile and I cannot understand that error messsages, so any help will be appreciated.

I hope that this forum is a correct place to post about kernel compile.

Regards.

---

### Post by carrett on 2008-04-01
It does say "see dmesg," perhaps there's something useful there?

---

### Post by P3P on 2008-04-02
> **carrett said:**
> It does say "see dmesg," perhaps there's something useful there?
Thanks for the response, but if you reread my post you can see that I wrote the error messages that appear on dmesg, but I cannot understand what *Unknown symbol* error means.

---

### Post by carrett on 2008-04-02
Right you are sir, my bad.

Anyway, there seems to be a bug filed in Launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200553](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200553)

It's still beta, don't know what else to tell you. I'd follow that bug report and look for a fix there.

Sorry I don't have something more definitive.

---

### Post by P3P on 2008-04-02
> **carrett said:**
> 
Anyway, there seems to be a bug filed in Launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200553](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200553)

Thanks for the launchpad link.
It would be a bug in the kernel, but I don't think so because the launchpad bug appears to be in the kernel config (sound support not selected even as a module) but in my kernel config sound support is well selected as a module.

However, the error messages are exactly the same, so that bug could be a clue.

> **carrett said:**
> It's still beta, don't know what else to tell you. I'd follow that bug report and look for a fix there.
Ubuntu is beta, but I think that my error is not Ubuntu related but kernel recompile related.
I will keep on trying.
Regards.

---

### Post by Whiffle on 2008-04-02
Could you post the output of 

uname -r 


I think it might be something version related.

---

### Post by P3P on 2008-04-02
> **Whiffle said:**
> Could you post the output of 
uname -r 
I think it might be something version related.

**2.6.24-13-generic**

The ABI version identifier was auto generated by compilation scripts.
I followed the [Kernel Compile Guide](https://help.ubuntu.com/community/Kernel/Compile).
The command that I used was:
> DEB_BUILD_OPTIONS=parallel=2 AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-generic

Thanks.

---

### Post by P3P on 2008-04-11
> **Whiffle said:**
> Could you post the output of 
uname -r 
I think it might be something version related.
Kernel is 2.6.24-13-generic.
Please explain what version related problem might be.

---

### Post by Whiffle on 2008-04-11
I was thinking you might have a module compiled for a different version than you've booted, but it seems this is not the case.  I'll try to have a look at your kernel config when i get home tonight.

---

