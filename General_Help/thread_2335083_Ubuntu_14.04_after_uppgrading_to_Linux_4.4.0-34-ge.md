---
title: "Ubuntu 14.04 after uppgrading to Linux 4.4.0-34-generic stoppe booting"
date: 2016-08-25
forum: General Help
---

### Post by ultramax on 2016-08-25
[COLOR=#000000][FONT=&amp]Yesterday my system asked me to install new updates ([/FONT][/COLOR]4.4.0-34-generic[FONT=Ubuntu Beta][COLOR=#000000]) [/COLOR][/FONT]
[SIZE=2][FONT=arial][COLOR=#000000]I agreed. After upgrading it asked to reboot. Done and after this I received following (from kern.log)[/COLOR][/FONT][/SIZE]

> **Aug 24 15:07:12 mfilippov kernel: [   53.882139] BUG: unable to handle kernel NULL pointer dereference at 00000018**
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.882183] IP: [<c100368e>] do_fast_syscall_32+0x8e/0x130[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.882215] *pdpt = 0000000034585001 *pde = 0000000000000000 [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.882245] Oops: 0002 [#1] SMP [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.882264] Modules linked in: symev_custom_dkms_i686(OE) nf_log_ipv4 ipt_REJECT nf_reject_ipv4 iptable_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_nat_ipv4 nf_nat iptable_filter ip_tables nf_log_ipv6 nf_log_common xt_LOG xt_limit ip6t_REJECT nf_reject_ipv6 xt_tcpudp ip6t_ah nf_conntrack_ipv6 nf_defrag_ipv6 xt_conntrack ip6table_filter ip6_tables x_tables bnep rfcomm bluetooth nvidia(POE) snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel snd_seq_midi snd_hda_codec drm coretemp snd_seq_midi_event snd_hda_core snd_rawmidi snd_hwdep kvm_intel snd_seq kvm snd_seq_device snd_pcm snd_timer snd irqbypass soundcore input_leds shpchp serio_raw 8250_fintek lpc_ich asus_atk0110 mac_hid binfmt_misc parport_pc ppdev nf_conntrack_ftp nf_conntrack lp parport jitterentropy_rng drbg ansi_cprng xts gf128mul dm_crypt uvesafb psmouse pata_acpi atl1e floppy fjes[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.882726] CPU: 1 PID: 1848 Comm: logger Tainted: P           OE   4.4.0-34-generic #53~14.04.1-Ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.882774] Hardware name: System manufacturer P5QL-E/P5QL-E, BIOS 1104    09/11/2009[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.882814] task: f453b600 ti: f4690000 task.ti: f4690000[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.882842] EIP: 0060:[<c100368e>] EFLAGS: 00010292 CPU: 1[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.882871] EIP is at do_fast_syscall_32+0x8e/0x130[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.882895] EAX: 00000000 EBX: 00000000 ECX: 80080007 EDX: 80080008[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.882926] ESI: b77adcf9 EDI: f4690000 EBP: f4691fa4 ESP: f4691f80[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.882958]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.882985] CR0: 8005003b CR2: 00000018 CR3: 353b0780 CR4: 000406f0[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.883016] Stack:[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.883027]  09680588 09638bc8 09673208 00000000 b7762000 09680588 09680588 00000000[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.883072]  b7762000 bf85aba4 c175b91c 00000000 00000000 00000000 00000000 00000000[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.883118]  00000000 00000000 0000007b 0000007b 00000000 00000000 0000000b b77c10d0[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.883163] Call Trace:[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.883179]  [<c175b91c>] sysenter_past_esp+0x3d/0x61[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.883204] Code: 54 24 14 8b 53 10 89 54 24 10 8b 53 0c 89 54 24 0c 8b 53 08 89 54 24 08 8b 53 04 89 54 24 04 8b 13 89 14 24 ff 14 85 80 f1 75 c1 <89> 43 18 8b 57 04 f7 c2 91 00 00 10 75 7e fa 66 66 90 66 90 8b[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.883356] EIP: [<c100368e>] do_fast_syscall_32+0x8e/0x130 SS:ESP 0068:f4691f80[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.883397] CR2: 0000000000000018[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.883415] ---[ end trace fe98051702291206 ]---[/FONT][/COLOR]
**Aug 24 15:07:12 mfilippov kernel: [   53.884843] BUG: unable to handle kernel NULL pointer dereference at 00000018**
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.884881] IP: [<c100368e>] do_fast_syscall_32+0x8e/0x130[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.884911] *pdpt = 0000000035129001 *pde = 0000000000000000 [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.884941] Oops: 0002 [#2] SMP [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Aug 24 15:07:12 mfilippov kernel: [   53.884959] Modules linked in: symev_custom_dkms_i686(OE) nf_log_ipv4 ipt_REJECT nf_reject_ipv4 iptable_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_nat_ipv4 nf_nat iptable_filter ip_tables nf_log_ipv6 nf_log_common xt_LOG xt_limit ip6t_REJECT nf_reject_ipv6 xt_tcpudp ip6t_ah nf_conntrack_ipv6 nf_defrag_ipv6 xt_conntrack ip6table_filter ip6_tables x_tables bnep rfcomm bluetooth nvidia(POE) snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel snd_seq_midi snd_hda_codec drm coretemp snd_seq_midi_event snd_hda_core snd_rawmidi snd_hwdep kvm_intel snd_seq kvm snd_seq_device snd_pcm snd_timer snd irqbypass soundcore input_leds shpchp serio_raw 8250_fintek lpc_ich asus_atk0110 mac_hid binfmt_misc parport_pc ppdev nf_conntrack_ftp nf_conntrack lp parport jitterentropy_rng drbg ansi_cprng xts gf128mul dm_crypt uvesafb psmouse pata_acpi atl1e floppy fjes[/FONT][/COLOR]

and again and again the same

[COLOR=#000000][FONT=&amp]I had to go to the GRUB, advanced settings, and then I chose loading of the old version (**marked as bold**). Then system booted OK
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]Now all the time I need to boot I have to choose this one otherwise using the new [/FONT][/COLOR][COLOR=#000000][FONT=&amp]4.4.0-34-generic system is not loading[/FONT][/COLOR][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]> [INDENT]
Ubuntu, &#1089; Linux 4.4.0-34-generic
Ubuntu with Linux 4.4.0-34-generic (recovery mode)
**Ubuntu, &#1089; Linux 3.19.0-30-generic**
Ubuntu with Linuxl 3.19.0-30-generic  (recovery mode)
Ubuntu, &#1089; Linux 3.19.0-28-generic
Ubuntu with Linuxl 3.19.0-28-generic  (recovery mode)[/INDENT]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]Can anyone tell me how can I handle this to make it work with [/FONT][/COLOR][COLOR=#000000]4.4.0-34-generic?

Someone told me to downgrade my videoadapter's driver ([/COLOR][COLOR=#000000][FONT=&quot]NVIDIA Corporation GT218 [GeForce 8400 GS Rev. 3] (rev a2)[/FONT][/COLOR][COLOR=#000000]) from Nvidia binary driver 340.96 to 304.131... but is it really problem in the adapter's driver?[/COLOR]

---

### Post by oldfred on 2016-08-26
This says the 340 version is correct.
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

But how did you install nVidia driver?
If you installed from nVidia with a .run file you have to re-integrate it into every new kernel.
If installed from repository (or ppa) then nVidia driver is automatically configured for new kernels.

 #What is installed
dkms status

---

### Post by ultramax on 2016-08-30
I installed it from Software & Updates -> Additional drivers. Today I also tried to use open driver, also Nvidia 304 legacy driver - no luck on 4.4.0-34-generic. Only **3.19.0-30-generic **works

dkms status
bbswitch, 0.7, 3.19.0-28-generic, i686: installed
bbswitch, 0.7, 3.19.0-30-generic, i686: installed
bbswitch, 0.7, 4.4.0-34-generic, i686: installed
openclient-savap-config, 1.0.14, 3.19.0-30-generic, i686: installed
openclient-savap-config, 1.0.14, 4.4.0-34-generic, i686: installed

---

### Post by oldfred on 2016-08-30
Did you purge nVidia driver, before installing another.
New one does not remove old and you get major conflicts.

       Updated driver search by nVidia model, do not download, just check correct driver version
[URL="http://www.geforce.com/drivers"]http://www.geforce.com/drivers
[/URL]
 #What is installed
dkms status 

 # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices 
    
 sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall

---

### Post by ultramax on 2016-08-31
> **oldfred said:**
> Did you purge nVidia driver, before installing another.
New one does not remove old and you get major conflicts.

       Updated driver search by nVidia model, do not download, just check correct driver version
[URL="http://www.geforce.com/drivers"]http://www.geforce.com/drivers
[/URL]
 #What is installed
dkms status 

 # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices 
    
 sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall

No I did not purge anything. I just went there and selected the driver. And it all worked fine on 3-rd version

[IMG]http://savepic.ru/11162744.png[/IMG]

I tried to switch to opensource driver, but I received totally wrong display resolution and was not able to work correctly there

Today I received 4.4.0-36 version that also did not work. So i purged both 4.4.0-34 & 4.4.0-36 versions to make Ubuntu start normally without playing with GRUB
So what do you recommend? Purge all nvidia drivers, switch to opensource driver and install 4.4.0-36 update?

**PS** I also noticed at one forum that users have problems with cursor after gong back from sleep mode on both 4.4.0-34 and 4.4.0-36 versions. So maybe something wrong with them?

---

### Post by ultramax on 2016-09-07
Today I tried to boot from "live CD" Ubuntu 16.04.1 LTS. Everything booted OK without any problems (working with the default video driver from  X.Org server (open source) 
> [COLOR=#000000][FONT=&amp]
uname -r[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]4.4.0-31-generic[/FONT][/COLOR]

So what is wrong with my 14.04 LTS with the new 4 Kernel?

---

### Post by oldfred on 2016-09-07
You also show the bbswitch which is for optimus systems. That will not work with your 8400GS. 

You also show openclient-savap-config which is not in 16.04's repository.

At least purge bbswitch and maybe the openclient application to avoid conflicts.
       sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms

---

### Post by ultramax on 2016-09-08
> **oldfred said:**
> You also show the bbswitch which is for optimus systems. That will not work with your 8400GS. 

You also show openclient-savap-config which is not in 16.04's repository.

At least purge bbswitch and maybe the openclient application to avoid conflicts.
       sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms

First of all I have 14.04 LTS Ubuntu (not 16.04)
and... if I remove bbswitch and openclient application so will my system continue working? I am not familiar with these modules and I did not install it manually so I need to be 100% sure that it won't break my system.
All I need is to understand why 4-th version of kernel has broken my system and how to avoid it. And also - after O purged 4-th version - it shows that there are no such update for this system. But I want to install it - what do I have to do?

---

### Post by oldfred on 2016-09-08
This is what system says about bbswitch:
> bbswitch is a kernel module which automatically detects the required ACPI
calls for two kinds of Optimus laptops. It has been verified to work with
"real" Optimus and "legacy" Optimus laptops (at least, that is what the
author Lekensteyn calls those).

This package uses DKMS to automatically build the bbswitch kernel module.

It looks like openclient-savap-config is related to Symantec&#8482; AntiVirus. Google search shows only this thread as any issue in last couple of years. Either not a problem or no one uses it.

---

### Post by ultramax on 2016-09-22
Well I have a question. Now i do not have any [COLOR=#000000]4.4.0-xx modules[/COLOR] and everything works ok (after I have purged it)
How can install them again and check if they gonna work if I remove [COLOR=#000000]bbswitch[/COLOR]?
And regarding [COLOR=#000000]openclient-savap-config is related to Symantec&#8482; AntiVirus[/COLOR] - I can't remove it as this my office workstations and I need to use this antivirus there[COLOR=#000000][/COLOR]

---

### Post by oldfred on 2016-09-22
If you run this, you should be current with versions:

sudo apt-get update
sudo apt-get upgrade

---

### Post by ultramax on 2016-10-07
> **oldfred said:**
> If you run this, you should be current with versions:

sudo apt-get update
sudo apt-get upgrade

Just did it. This did not update anything. Seems like if I have purged 4.4.0-34-generic etc modules it cannot find anymore (maybe it thinks that if I removed it I do not need it anymore)

---

### Post by oldfred on 2016-10-07
Then you may need the updates for the Enablement stack.
Specific upgrade commands in this:
 [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr)

---

