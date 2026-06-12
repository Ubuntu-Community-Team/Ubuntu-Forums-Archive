---
title: "Open office crashes in Feisty Fawn"
date: 2007-04-27
forum: General Help
---

### Post by lamborghiniwang on 2007-04-27
I've just fresh installed Feisty fawn into my Thinkpad T60, everything works fine except OpenOffice. When I run openoffice by click Applications->Office->(any openoffice components), the splash screen appears for a few seconds then crashes. I tried run openoffice by typing "ooffice" in Shell, and I got the following error messages:
> 
*** glibc detected *** /usr/lib/openoffice/program/soffice.bin: free(): invalid pointer: 0x080d0440 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6c3e7cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb6c41e30]
/usr/lib/openoffice/program/libuno_sal.so.3(rtl_freeMemory+0x1d)[0xb72940bd]
/usr/lib/openoffice/program/soffice.bin[0x809192e]
/usr/lib/openoffice/program/soffice.bin(_ZdlPv+0x26)[0x8091966]
/usr/lib/libscim-1.0.so.8[0xa974e156]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xa974ef77]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xa9749f05]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so[0xa97edf7b]
/usr/lib/libgobject-2.0.so.0(g_type_class_ref+0x381)[0xb5c47b41]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0xa2f)[0xb5c2e1cf]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x21f)[0xb5c2e5ef]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb5c2e7a0]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(_Z23gtk_im_context_scim_newv+0x67)[0xa97e2b57]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(im_module_create+0x3c)[0xa97f227c]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_im_module_create+0xb9)[0xb5727d29]
/usr/lib/libgtk-x11-2.0.so.0[0xb572893b]
/usr/lib/libgtk-x11-2.0.so.0[0xb5728b39]
/usr/lib/libgtk-x11-2.0.so.0(gtk_im_context_set_client_window+0x4e)[0xb5725f0e]
/usr/lib/libgtk-x11-2.0.so.0[0xb56cf71f]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb5c359d9]
/usr/lib/libgobject-2.0.so.0[0xb5c26e49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5c2862b]
/usr/lib/libgobject-2.0.so.0[0xb5c3959a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5c3a627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5c3a7e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0xba)[0xb5863bea]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_set_parent+0x1de)[0xb58641ce]
/usr/lib/libgtk-x11-2.0.so.0(gtk_fixed_put+0xd3)[0xb56fcec3]
/usr/lib/libgtk-x11-2.0.so.0[0xb56fcf08]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__OBJECT+0x59)[0xb5c34ee9]
/usr/lib/libgobject-2.0.so.0[0xb5c26e49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5c2862b]
/usr/lib/libgobject-2.0.so.0[0xb5c3959a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5c3a627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5c3a7e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_add+0x12c)[0xb56b31bc]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb59942bd]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5996043]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb59a0abd]
/usr/lib/openoffice/program/libvcl680li.so[0xb7df0ff5]
/usr/lib/openoffice/program/libvcl680li.so[0xb7d7e09b]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11ModalDialogC2EP6WindowRK5ResId+0x67)[0xb7d7eac7]
/usr/lib/openoffice/program/libsvt680li.so(_ZN12WizardDialogC2EP6WindowRK5ResIdhs+0x3e)[0xb784b99e]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt14OWizardMachineC2EP6WindowRK5ResIdmhhs+0x4a)[0xb781d1da]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt13RoadmapWizardC2EP6WindowRK5ResIdmS5_h+0x4f)[0xb781a55f]
/usr/lib/openoffice/program/libspl680li.so[0xa9900926]
/usr/lib/openoffice/program/libspl680li.so[0xa98f7024]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0xd59)[0x806bc39]
/usr/lib/openoffice/program/libvcl680li.so[0xb7bfec3c]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x35)[0xb7bfed45]
/usr/lib/openoffice/program/soffice.bin(main+0x65)[0x805ff85]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb6becebc]
/usr/lib/openoffice/program/soffice.bin(__gxx_personality_v0+0x249)[0x805fe11]
======= Memory map: ========
08048000-0809c000 r-xp 00000000 08:05 1384844    /usr/lib/openoffice/program/soffice.bin
0809c000-0809e000 rw-p 00053000 08:05 1384844    /usr/lib/openoffice/program/soffice.bin
0809e000-08366000 rw-p 0809e000 00:00 0          [heap]
a9500000-a9521000 rw-p a9500000 00:00 0 
a9521000-a9600000 ---p a9521000 00:00 0 
a96e6000-a97ba000 r-xp 00000000 08:05 1245603    /usr/lib/libscim-1.0.so.8.1.0
a97ba000-a97c8000 rw-p 000d4000 08:05 1245603    /usr/lib/libscim-1.0.so.8.1.0
a97d6000-a97f7000 r-xp 00000000 08:05 1321922    /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
a97f7000-a97f8000 rw-p 00021000 08:05 1321922    /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
a97f8000-a9858000 rw-s 00000000 00:08 11862053   /SYSV00000000 (deleted)
a9858000-a9868000 r-xp 00000000 08:05 1384962    /usr/lib/openoffice/program/libfileacc.so
a9868000-a9869000 rw-p 00010000 08:05 1384962    /usr/lib/openoffice/program/libfileacc.so
a9869000-a98c6000 r-xp 00000000 08:05 1384992    /usr/lib/openoffice/program/libpackage2.so
a98c6000-a98c9000 rw-p 0005d000 08:05 1384992    /usr/lib/openoffice/program/libpackage2.so
a98c9000-a98e5000 r-xp 00000000 08:05 1339296    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
a98e5000-a98e6000 rw-p 0001b000 08:05 1339296    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
a98e6000-a9918000 r-xp 00000000 08:05 1384907    /usr/lib/openoffice/program/libspl680li.so
a9918000-a991a000 rw-p 00032000 08:05 1384907    /usr/lib/openoffice/program/libspl680li.so
a991a000-a995a000 rw-p a991a000 00:00 0 
a995a000-a9968000 r-xp 00000000 08:05 1384967    /usr/lib/openoffice/program/libgcc3_uno.so
a9968000-a9969000 rw-p 0000e000 08:05 1384967    /usr/lib/openoffice/program/libgcc3_uno.so
a9969000-a9c4d000 r-xp 00000000 08:05 1384882    /usr/lib/openoffice/program/libfwk680li.so
a9c4d000-a9c5d000 rw-p 002e3000 08:05 1384882    /usr/lib/openoffice/program/libfwk680li.so
a9c5d000-a9c5e000 rw-p a9c5d000 00:00 0 
a9c5e000-a9cf9000 r-xp 00000000 08:05 1384922    /usr/lib/openoffice/program/libxcr680li.so
a9cf9000-a9cfe000 rw-p 0009a000 08:05 1384922    /usr/lib/openoffice/program/libxcr680li.so
a9cfe000-a9e61000 r-xp 00000000 08:05 1384897    /usr/lib/openoffice/program/libsb680li.so
a9e61000-a9e72000 rw-p 00163000 08:05 1384897    /usr/lib/openoffice/program/libsb680li.so
a9e72000-a9e73000 rw-p a9e72000 00:00 0 
a9e73000-a9f0d000 r-xp 00000000 08:05 1384880    /usr/lib/openoffice/program/libfwe680li.so
a9f0d000-a9f11000 rw-p 0009a000 08:05 1384880    /usr/lib/openoffice/program/libfwe680li.so
a9f11000-aa2bb000 r-xp 00000000 08:05 1384902    /usr/lib/openoffice/program/libsfx680li.so
aa2bb000-aa2d4000 rw-p 003a9000 08:05 1384902    /usr/lib/openoffice/program/libsfx680li.so
aa2d4000-aa2d5000 rw-p aa2d4000 00:00 0 
aa2d5000-aa330000 r-xp 00000000 08:05 1385024    /usr/lib/openoffice/program/libucpfile1.so
aa330000-aa333000 rw-p 0005a000 08:05 1385024    /usr/lib/openoffice/program/libucpfile1.so
aa333000-aa36d000 r-xp 00000000 08:05 1384881    /usr/lib/openoffice/program/libfwi680li.so
aa36d000-aa36f000 rw-p 0003a000 08:05 1384881    /usr/lib/openoffice/program/libfwi680li.so
aa36f000-aa392000 r-xp 00000000 08:05 1384883    /usr/lib/openoffice/program/libfwl680li.so
aa392000-aa393000 rw-p 00023000 08:05 1384883    /usr/lib/openoffice/program/libfwl680li.so
aa393000-aa3c9000 r-xp 00000000 08:05 1791746    /lib/libsepol.so.1
aa3c9000-aa3ca000 rw-p 00035000 08:05 1791746    /lib/libsepol.so.1
aa3ca000-aa3d4000 rw-p aa3ca000 00:00 0 
aa3d4000-aa3d7000 r-xp 00000000 08:05 1241269    /usr/lib/libgpg-error.so.0.3.0
aa3d7000-aa3d8000 rw-p 00002000 08:05 1241269    /usr/lib/libgpg-error.so.0.3.0
aa3d8000-aa427000 r-xp 00000000 08:05 1241267    /usr/lib/libgcrypt.so.11.2.2
aa427000-aa429000 rw-p 0004e000 08:05 1241267    /usr/lib/libgcrypt.so.11.2.2
aa429000-aa43d000 r-xp 00000000 08:05 1241274    /usr/lib
** (process:15074): WARNING **: Unknown error forking main binary / abnormal early exit ..


Can someone help me on this?

---

### Post by Hagar Delest on 2007-04-27
Personally, I don't trust Ubuntu packages for OOo, see these threads to install from the RPMs:
- [ HOWTO: Install OpenOffice.org 2.2 on Ubuntu 6.10]("http://ubuntuforums.org/showthread.php?t=398074")
- [http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370](http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370).

---

### Post by lamborghiniwang on 2007-04-30
Problem solved. Here is what I did:
1) install scim-bridge, scim-bridge-agent, scim-bridge-client-gtk using Synaptic
2) set GTK_IM_MODULE=scim-bridge in /usr/bin/ooffice, my ooffice script looks like this:
```

#!/bin/sh
GTK_IM_MODULE=scim-bridge
export OOO_EXTRA_ARG=''
/usr/lib/openoffice/program/ooqstart "$@"

```

---

### Post by xiao lei on 2007-05-05
Excellent!  Thank you very much!  Last time this happened, I was tired so I completely removed Openoffice and reinstalled it.  It happened again and you helped me to prevent further occurrences.
Thanks,
&#30333;&#23567;&#38647;

---

### Post by aldeby on 2007-05-28
lamborghiniwang, 
thank you very much! 
I installed chinese support with SCIM and had the same annoying bug, your tip solved it!
Strange OO devs haven't run across it yet, anyway fortunately there had been you to provide the solution! :)
Cheers

---

### Post by Brian96 on 2007-06-04
> **lamborghiniwang said:**
> Problem solved. Here is what I did:
1) install scim-bridge, scim-bridge-agent, scim-bridge-client-gtk using Synaptic
2) set GTK_IM_MODULE=scim-bridge in /usr/bin/ooffice, my ooffice script looks like this:
```

#!/bin/sh
GTK_IM_MODULE=scim-bridge
export OOO_EXTRA_ARG=''
/usr/lib/openoffice/program/ooqstart "$@"

```

Question: Is this for running SCIM for Chinese input in an English session? If so, which HOWTO did you use to do the rest of the configuration? I've tried a couple, but never seem to get everything working right.

I am a complete noob, and I really hate configuring stuff in the terminal, mainly because a) I don't know what all the commands mean that I find on these HOWTOs and b) it isn't always clear how to undo a change that has been made in the terminal.

Anyway, Chinese input in English sessions with full support for OpenOffice, Firefox, Thunderbird, etc., is one of the handful of sticking points I have left about switching completely over from Win XP.

Thanks.

---

### Post by stchman on 2007-06-04
> **Hagar de l'Est said:**
> Personally, I don't trust Ubuntu packages for OOo, see these threads to install from the RPMs:
- [ HOWTO: Install OpenOffice.org 2.2 on Ubuntu 6.10]("http://ubuntuforums.org/showthread.php?t=398074")
- [http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370](http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370).

OO2.2 that came with the Feisty install works fine on all my machines.

---

### Post by Hagar Delest on 2007-06-04
> **stchman said:**
> OO2.2 that came with the Feisty install works fine on all my machines.
Have you tried the Impress module (especially switching to slideshow IIRC) ? and the Base wizards ?

---

### Post by stchman on 2007-06-04
> **Hagar de l'Est said:**
> Have you tried the Impress module (especially switching to slideshow IIRC) ? and the Base wizards ?

Yes I tried the Impress slideshow and it tries to recover.  I consider that a minor nuisance.  The file is not damaged so it is not really a huge factor.  I don't use Base so I don't know about what you say.

The fonts on OO2.2 downloaded from OO's website suck major and Ubuntu has fixed the fonts problem in OO2.2.

For everything I use OO for it does the job just fine.

---

### Post by Hagar Delest on 2007-06-04
> **stchman said:**
> Yes I tried the Impress slideshow and it tries to recover.  I consider that a minor nuisance.
It depends on your needs. For someone using mainly Impress, it's a show stopper (some threads about this issue in this very forum).

> **stchman said:**
> I don't use Base so I don't know about what you say.
Wizards freeze at the very end of the process.

> **stchman said:**
> The fonts on OO2.2 downloaded from OO's website suck major
Never had any problem with the fonts (using official OOo version from 2.0.2).

I can't understand why there are still such issues for OOo, it's a so important soft. Why Ubuntu team doesn't focus on a perfect integration ???

---

### Post by aldeby on 2007-06-05
Brian96,
I followed the following guide to add chinese support to english ubuntu:
[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)
enjoy &#20889;&#27721;&#35821;&#65281;

---

### Post by stchman on 2007-06-06
> **Hagar de l'Est said:**
> It depends on your needs. For someone using mainly Impress, it's a show stopper (some threads about this issue in this very forum).


Wizards freeze at the very end of the process.


Never had any problem with the fonts (using official OOo version from 2.0.2).

I can't understand why there are still such issues for OOo, it's a so important soft. Why Ubuntu team doesn't focus on a perfect integration ???

The fonts issue does only seems to present itself when using an LCD.  I had Edgy with the OO2.2 from OO's website and the fonts looked fine.  On my LCD equipped machines they looked like CR@P.  I attribute it to LCDs being far sharper and showing every flaw where CRTs hide flaws better.

Ubuntu will get the problem fixed or it will be fixed in Gutsy.  I am not a heavy OO user so it suits me just fine.

---

