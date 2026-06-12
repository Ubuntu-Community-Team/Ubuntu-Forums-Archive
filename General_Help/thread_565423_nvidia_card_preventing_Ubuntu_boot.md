---
title: "nvidia card preventing Ubuntu boot"
date: 2007-10-02
forum: General Help
---

### Post by pythonbite77 on 2007-10-02
I had ubuntu installed on my computer and whilst tinkering with the nvidia settings, lost the ability to start the x server. I made a back up of the /etc/X11/xorg.conf file and an attempt to  revert back to the original failed. As a consequence I attempted to re-install Ubuntu from the live  CD. However, I get a 'Kernel panic' error, advising me to boot into the disc with the 'apic=debug' option. However, I still have no luck. I have since installed Fedora Core 7 without any problems but attempting to boot from the Ubuntu live disc results in the same error.

Is there any way of resetting my nvidia settings so I can boot into Ubuntu or are there any other methods I could use to try and get a working ubuntu installation?

Any help would be greatly appreciated.

---

### Post by Masterj15 on 2007-10-02
I would just format the harddrive and try to boot the non-live disc onto to hard drive. I had a similar problem before, I am not sure if this is it but you should try (before formating the hard drive) going into the termial (before actual boot. I'm not sure what its called beacuse I haven't had to do this in a while) and type sudo aptitude. That is the synaptic package manager in a termanl form. Then try to reinstall the nvidia graphic properties again. When I mean terminal I mean the safe mode or what ever mode that brings you into all those words and want to you to login from a non graphical standpoint.

Hope this works

---

