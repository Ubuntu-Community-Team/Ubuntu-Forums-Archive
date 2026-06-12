---
title: "Grub creates two entries for OpenELEC"
date: 2016-11-14
forum: General Help
---

### Post by sam3093 on 2016-11-14
Hi there,

Sorry if this is a bit of a noob question, I am fairly new to using Ubuntu / Grub and I have a problem which I can't work out.

I have Ubuntu 16.10, Windows 10, Remix OS and OpenELEC multi-booting on my grub. Each entry works fine but for some reason when I select OpenELEC under grub it won't boot, instead it creates another entry underneath it which will then boot fine if I select it. If I were to select the original entry say 5 times it creates 5 new entries underneath. Now this isn't a major problem but it is annoying since I mainly use OpenELEC on the machine and it is set to autoboot after 10 seconds grub doesn't detect my wireless remote. The other entries don't do this and just boot in straight away.

I used grub customizer to set the entry up, my code is as follows:

```
 menuentry "OpenELEC" {
    search --set=root --label OE_SYSTEM --hint hd0,msdos6
    linux /KERNEL boot=LABEL=OE_SYSTEM disk=LABEL=OE_DATA quiet 
}
```

Any help would be much appreciated!  :D

Thanks,

Sam

---

### Post by oldfred on 2016-11-14
Have not seen that booting creates entries.
But with multiple installs you may have issues on which grub is in MBR and therefore in control of booting and then updates from other systems.
Often better to forget about grub customizer & os-prober and just do it yourself. You then have total control.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

I run this just to documment my system & know what is where:

 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 
OR if running from a script, but not as much info:

 Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)

---

### Post by sam3093 on 2016-11-14
Thanks for the reply, I ran the boot-repair info and got this back:

[http://paste2.org/67D9BegO](http://paste2.org/67D9BegO)

---

### Post by oldfred on 2016-11-14
Somehow you have a nested entry, perhaps that is the issue?

```
menuentry "OpenELEC"{

	menuentry "OpenELEC" {
	    search --set=root --label OE_SYSTEM --hint hd0,msdos6
	    linux /KERNEL boot=LABEL=OE_SYSTEM disk=LABEL=OE_DATA quiet
	 }
	 
}


```

Delete first menu & last }

---

### Post by sam3093 on 2016-11-15
That worked! Thank you very much for your help, I now have it working as it should &#128512;

---

### Post by sam3093 on 2016-11-15
Mods please could you mark as solved as I can't seem to do it on my phone.

---

### Post by QIII on 2016-11-15
Please go to "Thread tools" in the toolbar and select "Mark this thread a solved" in the dropdown.

Thanks.

---

