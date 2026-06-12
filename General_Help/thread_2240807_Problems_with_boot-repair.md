---
title: "Problems with boot-repair"
date: 2014-08-22
forum: General Help
---

### Post by Rosngela_P_Sanch on 2014-08-22
I installed Ubuntu 14 in my lapytop along with Windows 8, when I have finished to install the Ubuntu the Grub appeared, but in the 2nd it dissapeared, I tried to use de boot-repair but in the end this error happened:
[COLOR=#000000][FONT=HelveticaNeue]http://paste.ubuntu.com/8110217/

What Can I do?[/FONT][/COLOR]

---

### Post by oldfred on 2014-08-22
Configuration looks normal to me. 
You have both Ubuntu & Windows installed in UEFI boot mode.

You do have a Windows boot loader installed to the MBR for BIOS boot, but that will not work, so do not turn on BIOS/CSM/Legacy boot and try to boot as it just will not work.

I also do not recommend a separate /boot for most desktops, but it is ok. You will need to periodically remove older kernels so it does not fill up. Best to always keep a couple kernels, current and one older one. Then when it gets to several use synaptic to houseclean older ones.

Do you get grub menu now?
From UEFI menu in UEFI boot mode but with secure boot off can you choose both ubuntu or Windows entry to boot? Or from one time boot key, often f12 but varies by vendor?

What brand & model system?
What video? Intel, AMD or nVidia or Intel & one of the others?

---

