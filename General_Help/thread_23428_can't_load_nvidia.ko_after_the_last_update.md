---
title: "can't load nvidia.ko after the last update"
date: 2005-04-01
forum: General Help
---

### Post by caquino on 2005-04-01
Hi,
  I can't load anymore the nvidia driver, I can make an custom kernel to correct my bug but I just want to know if someone got the same problem.
This is my packages versions:
ii  linux-restricted-modules-2.6.10-5-k7  2.6.10.4-1 Non-free Linux 2.6.10 modules on AMD K7
ii  nvidia-glx     1.0.7167-0ubuntu25  NVIDIA binary XFree86 4.x/X.Org driver



dpkg -S nvidia.ko
linux-restricted-modules-2.6.10-5-k7: /lib/modules/2.6.10-5-k7/kernel/drivers/video/nvidia.ko


I have used debsums too to check if any file has been changed.. but all the files has the "OK" status.
debsums linux-restricted-modules-2.6.10-5-k7 | grep nvidia
lib/modules/2.6.10-5-k7/kernel/drivers/video/nvidia.ko                        OK


When I issue modprobe nvidia I got this error
modprobe nvidia
FATAL: Error inserting nvidia (/lib/modules/2.6.10-5-686/kernel/drivers/video/nvidia.ko): Unknown symbol in module, or unknown parameter (see dmesg)

and in dmesg
nvidia: Unknown symbol agp_bind_memory
nvidia: Unknown symbol agp_enable
nvidia: Unknown symbol agp_backend_acquire
nvidia: Unknown symbol agp_free_memory
nvidia: Unknown symbol agp_allocate_memory
nvidia: Unknown symbol agp_unbind_memory
nvidia: Unknown symbol agp_copy_info
nvidia: Unknown symbol agp_backend_release

AFAIK: the modules call some kernel handlers that's not implemented.. or disabled in kernel config. (that's why  I said that I can build a custom kernel)

I have tweaked the modutils to load nvidia with some parameters.. here we are

options nvidia  NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1 NVreg_ReqAGPRate=8

I have tried with this parameters.. and without.. and always I got the same problem..

I have inserted via-agp, agpgart, nvidia in hotplugs blacklist because I use NvAGP "1" in my xorg.conf.. 

This configuration has working until the last update.
I have attached my xorg's configuration if someone want's to take a closer look.

Thanks!!

---

### Post by Joeb on 2005-04-01
After I did my last upgrade, my nvidia driver quit, too, although I didn't have the error you have.  Running "sudo nvidia-glx-config enable" from the cli and restarting X fix it for me, though.

---

### Post by Firetech on 2005-04-02
[QUOTE=caquino]
nvidia: Unknown symbol agp_bind_memory
nvidia: Unknown symbol agp_enable
nvidia: Unknown symbol agp_backend_acquire
nvidia: Unknown symbol agp_free_memory
nvidia: Unknown symbol agp_allocate_memory
nvidia: Unknown symbol agp_unbind_memory
nvidia: Unknown symbol agp_copy_info
nvidia: Unknown symbol agp_backend_release
[...snip...]
I have inserted via-agp, agpgart, nvidia in hotplugs blacklist because I use NvAGP "1" in my xorg.conf..[/QUOTE]
I did that too. and got the same results. I think it happens because NvAGP doesn't work with all chipsets, and among the non-supported is my VIA chip... (You can find the list of supported chipsets [here](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7167/README.txt)  (search for chipsets, it's a LARGE file))
Although, you should first try to do "modprobe agpgart" and "modprobe via-agp". If it works after that, you should un-blacklist those modules... You shouldn't have to blacklist agpgart, because NvAGP "1" means that it tries to use NvAGP, if possible, else it uses Agpgart.

[QUOTE=caquino]I have tweaked the modutils to load nvidia with some parameters.. here we are

options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1 NVreg_ReqAGPRate=8[/QUOTE]
Hmm, AFAIK (after reading the readme), the AGPRate should be 7, not 8. Strange, but if the readme says so, it should be true...

---

### Post by caquino on 2005-04-02
[QUOTE=Firetech]I did that too. and got the same results. I think it happens because NvAGP doesn't work with all chipsets, and among the non-supported is my VIA chip... (You can find the list of supported chipsets [here](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7167/README.txt)  (search for chipsets, it's a LARGE file))
Although, you should first try to do "modprobe agpgart" and "modprobe via-agp". If it works after that, you should un-blacklist those modules... You shouldn't have to blacklist agpgart, because NvAGP "1" means that it tries to use NvAGP, if possible, else it uses Agpgart.


Hmm, AFAIK (after reading the readme), the AGPRate should be 7, not 8. Strange, but if the readme says so, it should be true...[/QUOTE]

This setup stops after the last update.. I think nvidia doesn't drop support for my agp bus.. I have tried agpgart.. via-agp.. I have to switch to the nv module in xorg because the nvidia module doesn't load..

---

### Post by Aurelius on 2005-04-02
[QUOTE=caquino]This setup stops after the last update.. I think nvidia doesn't drop support for my agp bus.. I have tried agpgart.. via-agp.. I have to switch to the nv module in xorg because the nvidia module doesn't load..[/QUOTE]

I'm having the exact same problem Caquino is having, and I can't get it fixed, either.

---

### Post by Firetech on 2005-04-02
[QUOTE=caquino]This setup stops after the last update.. I think nvidia doesn't drop support for my agp bus.. I have tried agpgart.. via-agp.. I have to switch to the nv module in xorg because the nvidia module doesn't load..[/QUOTE]
It is kind of strange, because I also got it to work with via-agp and agpgart blacklisted... Rebooting made it kill itself again, sometimes... I don't know what happened, but now I'm running safe and secure with agpgart. (The latest drivers directly from nVidia (1.0-7174) improves  performance without nvagp...)
When my self-compiled nvidia driver refuses to load, I just recompile it, and that almost always help. I think it refuses to load when changes are made to the kernel or it's modules or something like that. You should try "apt-get remove nvidia-glx" and then "apt-get install nvidia-glx" again, if that doesn't help, do the same with the linux-restricted-modules... It might be a good idea to do this when running another kernel, though...

---

### Post by Whiffle on 2005-04-02
Shot in the dark, but try NVagp =3 ,works fine for me.

---

### Post by Firetech on 2005-04-02
[QUOTE=Whiffle]Shot in the dark, but try NVagp =3 ,works fine for me.[/QUOTE]
That would be a VERY good idea too... Why didn't I think of that?

---

### Post by caquino on 2005-04-02
[QUOTE=Firetech]That would be a VERY good idea too... Why didn't I think of that?[/QUOTE]

I can use with agpart/via-agp.. but my problem is I can't load the nvidia module... I'm using the xorg now without the nvidia module.. but I'm just trying to determine why I can't use the nvidia to get more from my hardware..

---

### Post by Joeb on 2005-04-03
I don't know if this is it or not, but after re-reading the original post, I noticed that the kernels referenced are all -k7 while the error message for modprobe listed refers to a -686 kernel.

Are you sure you have the right modules in the right directories for the actual kernel you are running?

Joeb

---

### Post by caquino on 2005-04-03
[QUOTE=Joeb]I don't know if this is it or not, but after re-reading the original post, I noticed that the kernels referenced are all -k7 while the error message for modprobe listed refers to a -686 kernel.

Are you sure you have the right modules in the right directories for the actual kernel you are running?

Joeb[/QUOTE]

I'm sorry about this wrong information.. 
FATAL: Error inserting nvidia (/lib/modules/2.6.10-5-k7/kernel/drivers/video/nvidia.ko): Unknown symbol in module, or unknown parameter (see dmesg)
hehe I have tested with k7 and 686.. and pasted the wrong line here.. sorry.. but I got the same error with k7 modules.

---

### Post by Firetech on 2005-04-03
[QUOTE=caquino]I can use with agpart/via-agp.. but my problem is I can't load the nvidia module... I'm using the xorg now without the nvidia module.. but I'm just trying to determine why I can't use the nvidia to get more from my hardware..[/QUOTE]
What do you mean? Can you load the nvidia module with agpgart instead of NvAGP (NvAGP "2" or "3")?

---

### Post by caquino on 2005-04-03
[QUOTE=Firetech]What do you mean? Can you load the nvidia module with agpgart instead of NvAGP (NvAGP "2" or "3")?[/QUOTE]

I can't load nvidia module.. neither loading agpgart.. via-agp.. or only nvidia..

---

### Post by Firetech on 2005-04-04
[QUOTE=caquino]I can't load nvidia module.. neither loading agpgart.. via-agp.. or only nvidia..[/QUOTE]
Can't you modprobe any of agpgart, via-agp (may be via_agp) or nvidia? If so, what error messages do you get?

---

### Post by n4cht on 2005-04-05
I've had this problem as well.  It would seem the problem lies in nvidia-glx updates coming shortly before xorg updates, and the version numbers don't match up, causing the nvidia module to fail loading.

I've noticed that if you wait a day or two for the xorg update, then re-run nvidia-glx-config enable, commenting out the DRI line that it seems to always want to add, it will load fine.

Quickest fix:  If the damn xorg updates were on time with the nvidia updates, or even putting the xorg updates _first_, this would not be an issue.

---

