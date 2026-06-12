---
title: "Agpgart problems"
date: 2004-11-26
forum: General Help
---

### Post by Palermo on 2004-11-26
Hi! I want to try out nvagp as I was suggested that it would run better. The problem is that i cant unload agpgart module. I have put "NVAGP" "1" on XF86Config-4. Dmesg shows that nvagp could not be loaded because agpgart module is loaded. How can i edit that it doesn't load at boot time.

---

### Post by p!=f on 2004-11-26
[QUOTE=Palermo]Hi! I want to try out nvagp as I was suggested that it would run better. The problem is that i cant unload agpgart module. I have put "NVAGP" "1" on XF86Config-4. Dmesg shows that nvagp could not be loaded because agpgart module is loaded. How can i edit that it doesn't load at boot time.[/QUOTE]
It's a long time since I last used a kernel with agpgart compiled in. :)

Please post the output of lsmod command here and put it within [ code ] and [ / code ] (without spaces when you compose a reply) so it's more readable.
I can tell you then what/how to remove the appropriate modules so that internal nVidia AGP support will be used instead.
```

 * 17:56:08 * pef @ agonicus *
[~] > lsmod
Module                  Size  Used by
button                  5136  0
ac                      3588  0
battery                 7940  0
md5                     3840  1
ipv6                  229120  14
ipt_TOS                 2176  12
ipt_MASQUERADE          2944  1
ipt_REJECT              5632  4
ipt_pkttype             1536  4
ipt_LOG                 6272  11
ipt_state               1664  17
ipt_multiport           1792  2
ipt_conntrack           2176  3
iptable_mangle          2304  1
ip_nat_irc              3824  0
ip_nat_tftp             3184  0
ip_nat_ftp              4336  0
iptable_nat            21576  5 ipt_MASQUERADE,ip_nat_irc,ip_nat_tftp,ip_nat_ftp
ip_conntrack_irc       70704  1 ip_nat_irc
ip_conntrack_tftp       3248  0
ip_conntrack_ftp       71600  1 ip_nat_ftp
ip_conntrack           39668  10 ipt_MASQUERADE,ipt_state,ipt_conntrack,ip_nat_irc,ip_nat_tftp,ip_nat_ftp,iptable_nat,ip_conntrack_irc,ip_conntrack_tftp,ip_conntrack_ftp
iptable_filter          2432  1
ip_tables              15360  11 ipt_TOS,ipt_MASQUERADE,ipt_REJECT,ipt_pkttype,ipt_LOG,ipt_state,ipt_multiport,ipt_conntrack,iptable_mangle,iptable_nat,iptable_filter
af_packet              16392  4
usbmouse                4480  0
snd_via82xx            22020  5
snd_ac97_codec         68688  1 snd_via82xx
snd_pcm_oss            48168  1
snd_mixer_oss          17536  5 snd_pcm_oss
snd_pcm                81544  2 snd_via82xx,snd_pcm_oss
snd_timer              20228  1 snd_pcm
snd_page_alloc          7816  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6016  1 snd_via82xx
snd_rawmidi            19492  1 snd_mpu401_uart
snd_seq_device          6664  1 snd_rawmidi
usbhid                 29760  0
snd                    45028  9 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               7264  6 snd
uhci_hcd               28944  0
usbcore               101604  5 usbmouse,usbhid,uhci_hcd
8139too                21248  0
mii                     4224  1 8139too
crc32                   4096  1 8139too
3c59x                  36008  0
evdev                   7680  0
w83627hf               28584  0
eeprom                  6816  0
i2c_isa                 1920  0
i2c_viapro              6284  0
i2c_sensor              3328  2 w83627hf,eeprom
i2c_core               19216  5 w83627hf,eeprom,i2c_isa,i2c_viapro,i2c_sensor
nvidia               4812596  22
parport_pc             36672  1
lp                      8744  0
parport                33992  2 parport_pc,lp
ide_cd                 38304  0
cdrom                  37788  1 ide_cd
rtc                     9784  0
unix                   21812  1123
fan                     3076  0
thermal                10888  0
processor              11548  1 thermal

```

---

### Post by p!=f on 2004-11-26
Shut GUI down first
```

sudo /etc/init.d/gdm stop

```
Force remove the modules
Note that if you didn't stop xserver, expect hard freeze.
```

sudo rmmod -f nvidia nvidia_agp agpgart

```
And finally, start GUI again
```

sudo /etc/init.d/gdm start

```

---

### Post by Palermo on 2004-11-26
Thank you. But it would be nice to reject agpgart and nvidia_agp modules at boot automatically.

---

### Post by zenwhen on 2004-11-26
I used "NVAGP" "2" to get around this.

---

### Post by p!=f on 2004-11-26
[QUOTE=zenwhen]I used "NVAGP" "2" to get around this.[/QUOTE]
Yes, but it means "use agpgart if possible".

---

### Post by p!=f on 2004-11-26
[QUOTE=Palermo]Thank you. But it would be nice to reject agpgart and nvidia_agp modules at boot automatically.[/QUOTE]
Does it work? Can you experience any differences in performance?

I'm not sure how to do it. Blacklisting those modules in udev didn't work for me. If you use **discover** there's a blacklist file which you may add those modules in.
If you get some performance gain, try to compile a custom kernel without agpgart module.

---

### Post by Palermo on 2004-11-27
[QUOTE=p!=f]Does it work? Can you experience any differences in performance?

I'm not sure how to do it. Blacklisting those modules in udev didn't work for me. If you use **discover** there's a blacklist file which you may add those modules in.
If you get some performance gain, try to compile a custom kernel without agpgart module.[/QUOTE]

Yes that did work and I did notice slight perfomance gain. Blacklisting doesn't seem to work for me. Im going to try to compile new kernel without agpgart.

---

### Post by Bannet on 2004-12-06
I hade the same prob. this is what I did.

sudo gedit /etc/X11/XF86Config-4

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option		"RenderAccel"		"true"
        Option		"sisAGP"			"1"

 Changed last line from  

 Option		"NVAGP"			       "1"

to

 Option		"sisAGP"			"1"

---

### Post by jdong on 2004-12-06
NvAGP shouldn't be overriding any other AGPGART....


If you want to load modules on startup, put its name in /etc/modules...


I have to warn you that it probably wouldn't solve your problems!

---

### Post by Bannet on 2004-12-06
My agp is sis. And know I get 

agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode


Were before I had

NVRM: not using NVAGP, AGPGART is loaded!!
NVRM: not using NVAGP, AGPGART is loaded!!

Maybe I should of posted it here

[http://ubuntuforums.org/showthread.php?t=6620&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=6620&page=1&pp=10)

---

### Post by rutty on 2005-01-06
[QUOTE=Bannet]I hade the same prob. this is what I did.

sudo gedit /etc/X11/XF86Config-4

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option		"RenderAccel"		"true"
        Option		"sisAGP"			"1"

 Changed last line from  

 Option		"NVAGP"			       "1"

to

 Option		"sisAGP"			"1"[/QUOTE]


This worked for me - thanks :)

I have exactly the same card as you.

---

