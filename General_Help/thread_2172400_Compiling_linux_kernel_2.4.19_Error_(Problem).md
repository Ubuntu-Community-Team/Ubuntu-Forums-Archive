---
title: "Compiling linux kernel 2.4.19 Error (Problem)"
date: 2013-09-04
forum: General Help
---

### Post by troy_bergdahl on 2013-09-04
Hello, I'm trying to compile kernel 2.4.19. I performed "wget"  and retrieved it successfully, performed "tar" and unpacked it  successfully, and finally "make menuconfig" and "make dep" both work  fine. But when I go to "make" or "make bzImage" i get an error as  follows:
```
/home/neily/linux-2.4.19/include/asm/processor.h:74:26: error: array type has incomplete element type
In file included from /home/neily/linux-2.4.19/include/linux/fs.h:317:0,
                 from /home/neily/linux-2.4.19/include/linux/capability.h:17,
                 from /home/neily/linux-2.4.19/include/linux/binfmts.h:5,
                 from /home/neily/linux-2.4.19/include/linux/sched.h:9,
                 from /home/neily/linux-2.4.19/include/linux/mm.h:4,
                 from /home/neily/linux-2.4.19/include/linux/slab.h:14,
                 from /home/neily/linux-2.4.19/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/home/neily/linux-2.4.19/include/linux/ncp_fs_i.h:26:2: warning: ‘packed’ attribute ignored for field of type ‘__u8’ [-Wattributes]
/home/neily/linux-2.4.19/include/linux/ncp_fs_i.h:27:2: warning: ‘packed’ attribute ignored for field of type ‘__u8[6]’ [-Wattributes]
In file included from /home/neily/linux-2.4.19/include/linux/ncp_mount.h:12:0,
                 from /home/neily/linux-2.4.19/include/linux/ncp_fs_sb.h:12,
                 from /home/neily/linux-2.4.19/include/linux/fs.h:701,
                 from /home/neily/linux-2.4.19/include/linux/capability.h:17,
                 from /home/neily/linux-2.4.19/include/linux/binfmts.h:5,
                 from /home/neily/linux-2.4.19/include/linux/sched.h:9,
                 from /home/neily/linux-2.4.19/include/linux/mm.h:4,
                 from /home/neily/linux-2.4.19/include/linux/slab.h:14,
                 from /home/neily/linux-2.4.19/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/home/neily/linux-2.4.19/include/linux/ncp.h:24:2: warning: ‘packed’ attribute ignored for field of type ‘__u8’ [-Wattributes]
/home/neily/linux-2.4.19/include/linux/ncp.h:25:2: warning: ‘packed’ attribute ignored for field of type ‘__u8’ [-Wattributes]
/home/neily/linux-2.4.19/include/linux/ncp.h:26:2: warning: ‘packed’ attribute ignored for field of type ‘__u8’ [-Wattributes]
/home/neily/linux-2.4.19/include/linux/ncp.h:27:2: warning: ‘packed’ attribute ignored for field of type ‘__u8’ [-Wattributes]
/home/neily/linux-2.4.19/include/linux/ncp.h:28:2: warning: ‘packed’ attribute ignored for field of type ‘__u8’ [-Wattributes]
/home/neily/linux-2.4.19/include/linux/ncp.h:29:2: warning: ‘packed’ attribute ignored for field of type ‘__u8[]’ [-Wattributes]
/home/neily/linux-2.4.19/include/linux/ncp.h:37:2: warning: ‘packed’ attribute ignored for field of type ‘__u8’ [-Wattributes]
/home/neily/linux-2.4.19/include/linux/ncp.h:38:2: warning: ‘packed’ attribute ignored for field of type ‘__u8’ [-Wattributes]
/home/neily/linux-2.4.19/include/linux/ncp.h:39:2: warning: ‘packed’ attribute ignored for field of type ‘__u8’ [-Wattributes]
/home/neily/linux-2.4.19/include/linux/ncp.h:40:2: warning: ‘packed’ attribute ignored for field of type ‘__u8’ [-Wattributes]
/home/neily/linux-2.4.19/include/linux/ncp.h:41:2: warning: ‘packed’ attribute ignored for field of type ‘__u8’ [-Wattributes]
/home/neily/linux-2.4.19/include/linux/ncp.h:42:2: warning: ‘packed’ attribute ignored for field of type ‘__u8’ [-Wattributes]
/home/neily/linux-2.4.19/include/linux/ncp.h:43:2: warning: ‘packed’ attribute ignored for field of type ‘__u8[]’ [-Wattributes]
/home/neily/linux-2.4.19/include/linux/ncp.h:137:2: warning: ‘packed’ attribute ignored for field of type ‘__u8’ [-Wattributes]
/home/neily/linux-2.4.19/include/linux/ncp.h:138:2: warning: ‘packed’ attribute ignored for field of type ‘__u8[256]’ [-Wattributes]
/home/neily/linux-2.4.19/include/linux/ncp.h:174:2: warning: ‘packed’ attribute ignored for field of type ‘__u8’ [-Wattributes]
In file included from /home/neily/linux-2.4.19/include/asm/smp.h:17:0,
                 from /home/neily/linux-2.4.19/include/linux/smp.h:14,
                 from /home/neily/linux-2.4.19/include/linux/sched.h:23,
                 from /home/neily/linux-2.4.19/include/linux/mm.h:4,
                 from /home/neily/linux-2.4.19/include/linux/slab.h:14,
                 from /home/neily/linux-2.4.19/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/home/neily/linux-2.4.19/include/asm/mpspec.h:86:2: warning: ‘packed’ attribute ignored for field of type ‘unsigned char[6]’ [-Wattributes]
In file included from /home/neily/linux-2.4.19/include/linux/sched.h:23:0,
                 from /home/neily/linux-2.4.19/include/linux/mm.h:4,
                 from /home/neily/linux-2.4.19/include/linux/slab.h:14,
                 from /home/neily/linux-2.4.19/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/home/neily/linux-2.4.19/include/linux/smp.h:29:13: error: conflicting types for ‘smp_send_reschedule’
/home/neily/linux-2.4.19/include/asm/smp.h:65:13: note: previous declaration of ‘smp_send_reschedule’ was here
In file included from /home/neily/linux-2.4.19/include/linux/unistd.h:9:0,
                 from init/main.c:17:
/home/neily/linux-2.4.19/include/asm/unistd.h:365:15: warning: conflicting types for built-in function ‘_exit’ [enabled by default]
init/main.c: In function ‘start_kernel’:
init/main.c:357:2: warning: format not a string literal and no format arguments [-Wformat-security]
make: *** [init/main.o] Error 1.
                        
```

 If you need anymore information, please let me know. Thank you

---

### Post by tgalati4 on 2013-09-04
What is your build environment?  If you are trying to compile this on a 3.5 kernel system, then you might have problems.  Find an old 2.6 kernel distro and use that for your build environment.

I'm going to guess that _u8 might be UTF8 compatibility for international characters--multi-language support.  

What is the application for this old kernel?

---

### Post by troy_bergdahl on 2013-09-04
well, I'm kind of inexperienced when it comes to linux/ubuntu, so I don't know what a build environment is. and I'm trying to download a patch for my wireless adapter so I can test my wireless home networks password strength. How would you suggest I go about getting a 2.6 kernel?

---

### Post by tgalati4 on 2013-09-05
A build environment is when you have all of the tools on a machine that builds a working kernel and other source code for your target machine.  If you have all of the tools to create errors, then you don't quite have a build environment.

Some reading:  [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Ubuntu Hardy would be closer to what you need.  

If you are trying to get your wireless card into passive sniffing mode, then why don't you share with us the card model?

Compiling an old kernel is not trivial--taking 2 to 3 hours.  Typically you would only need to recompile the wireless module, not the entire kernel, then copy the module to the appropriate directory and load it with *modprobe*.

You may only need to turn on a switch.  What is the module that you are currently using?  On this machine I'm using a Broadcom 43xx series module (b43)

tgalati4@Dell600m-mint14 / $ modinfo b43
filename:       /lib/modules/3.5.0-39-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     5C5408969167493023BD033
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,mac80211,bcma,cfg80211
intree:         Y
vermagic:       3.5.0-39-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

---

