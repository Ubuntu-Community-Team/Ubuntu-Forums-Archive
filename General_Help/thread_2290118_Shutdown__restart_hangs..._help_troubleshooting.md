---
title: "Shutdown / restart hangs... help troubleshooting"
date: 2015-08-09
forum: General Help
---

### Post by juliushibert63 on 2015-08-09
[TABLE="width: 797"]
[TR]
[TD="class: t_f"]I've got a fresh install of Lubuntu [COLOR=#393939][FONT=arial, helvetica, clean, sans-serif]Linux 14.04.3, [/FONT][/COLOR][COLOR=#393939][FONT=arial, helvetica, clean, sans-serif]Linux 3.4.103 on armv7l on a Banana Pi. I've reformatted and reinstalled the SD card 3 times now and the same problem persists.[/FONT][/COLOR][COLOR=#393939][FONT=arial, helvetica, clean, sans-serif]
[/FONT][/COLOR]
[COLOR=#393939][FONT=arial, helvetica, clean, sans-serif]Basically whenever I restart or shutdown (I always do this via SSH, as it's going to be used as a headless server), the system just hangs and never restarts or shutdown. Occasionally I'll get some output to the screen, if connected. but somtimes after connecting a screen I just get a black screen with nothing or a flashing '_' prompt and I can't input any further text.[/FONT][/COLOR][COLOR=#393939][FONT=arial, helvetica, clean, sans-serif]
[/FONT][/COLOR]
[COLOR=#393939][FONT=arial, helvetica, clean, sans-serif]I've tried to search through /var/log/ to see if there's a log for shutdown commands but can't seem to find anything of help. Can someone point me in the right direction for how to troubleshoot this issue. [/FONT][/COLOR][/TD]
[/TR]
[/TABLE]

---

### Post by NathanRodriguez on 2015-08-09
Traditional dmesg log don't give some clue ?

---

### Post by juliushibert63 on 2015-08-10
Looking through dmesg seems to be helpful. I'm seeing the same output that I get to the monitor. It stops outputting arround this point....

```
[    2.436426] mousedev: PS/2 mouse device common for all mice[    2.447040] input: sunxi-ir as /devices/virtual/input/input0
[    2.454233] IR Initial OK
[    2.459189] sunxi-rtc sunxi-rtc: Warning: RTC time is wrong!
[    2.470142] sunxi-rtc sunxi-rtc: rtc core: registered rtc as rtc0
[    2.478759] i2c /dev entries driver
[    2.486048] config i2c gpio with gpio_config api
[    2.491615] axp_mfd 0-0034: AXP (CHIP ID: 0x41) detected
[    2.502769] axp_mfd 0-0034: AXP internal temperature monitoring enabled
[    2.514541] [AXP]axp driver uning configuration failed(342)
[    2.516466] [AXP]power_start = 0
[    2.519527] I2C: i2c-0: AW16XX I2C adapter
[    2.527037] config i2c gpio with gpio_config api
[    2.530380] I2C: i2c-1: AW16XX I2C adapter
[    2.537888] config i2c gpio with gpio_config api
[    2.541170] I2C: i2c-2: AW16XX I2C adapter
[    2.548670] config i2c gpio with gpio_config api
[    2.551961] I2C: i2c-3: AW16XX I2C adapter
[    2.557847] [ace_drv] start!!!
[    2.560183] [ace_drv] init end!!!
[    2.561876] [pa_drv] start!!!
[    2.564081] [pa_drv] init end!!!
[    2.568173] Driver for 1-wire Dallas network protocol.
[    2.577537] invalid gpio pin in fex configuration : -1
[    2.585085] axp20_ldo1: 1300 mV 
[    2.593523] axp20_ldo2: 1800 <--> 3300 mV at 3000 mV 
[    2.603839] axp20_ldo3: 700 <--> 3500 mV at 2800 mV 
[    2.613945] axp20_ldo4: 1250 <--> 3300 mV at 2800 mV 
[    2.624359] axp20_buck2: 700 <--> 2275 mV at 1450 mV 
[    2.634570] axp20_buck3: 700 <--> 3500 mV at 1300 mV 
[    2.644471] axp20_ldoio0: 1800 <--> 3300 mV at 2800 mV 
[    2.659233] input: axp20-supplyer as /devices/platform/sunxi-i2c.0/i2c-0/0-0034/axp20-supplyer.28/input/input1
[    2.687370] axp20_ldo2: Failed to create debugfs directory
[    2.697813] device-mapper: uevent: version 1.0.3
[    2.710269] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    2.722009] cpuidle: using governor ladder
[    2.728990] cpuidle: using governor menu
[    2.735263] [mmc-msg] sw_mci_init
[    2.744330] [mmc-msg] MMC host used card: 0x9, boot card: 0x0, io_card 8
[    2.756343] [mmc-msg] sdc0 set round clock 400000, src 24000000
[    2.770567] [mmc-msg] sdc0 set ios: clk 0Hz bm OD pm OFF vdd 3.3V width 1 timing LEGACY(SDR12) dt B
[    2.787818] [mmc-msg] sdc0 Probe: base:0xf0154000 irq:64 sg_cpu:f0156000(4fc00000) ret 0.
[    2.801003] [mmc-msg] sdc3 set round clock 400000, src 24000000
[    2.815119] [mmc-msg] sdc3 set ios: clk 0Hz bm OD pm OFF vdd 3.3V width 1 timing LEGACY(SDR12) dt B
[    2.832348] [mmc-msg] sdc3 Probe: base:0xf0158000 irq:67 sg_cpu:f015a000(4fc01000) ret 0.
[    2.845113] [mmc_pm]: failed to fetch sdio card configuration!
[    2.847549] sunxi_leds driver init
[    2.855030] Registered led device: green:ph24:led1
[    2.858797] Registered led device: blue:pg02:led2
[    2.863848] ledtrig-cpu: registered to indicate activity on CPUs
[    2.876307] usbcore: registered new interface driver usbhid
[    2.884717] usbhid: USB HID core driver
[    2.891255] ashmem: initialized
[    2.898008] logger: created 256K log 'log_main'
[    2.906350] logger: created 256K log 'log_events'
[    2.914765] logger: created 256K log 'log_radio'
[    2.923179] logger: created 256K log 'log_system'
[    2.933604] IPv4 over IPv4 tunneling driver
[    2.940526] TCP: bic registered
[    2.945996] TCP: cubic registered
[    2.951859] TCP: westwood registered
[    2.958049] TCP: highspeed registered
[    2.963992] TCP: hybla registered
[    2.969488] TCP: htcp registered
[    2.975008] TCP: vegas registered
[    2.980504] TCP: veno registered
[    2.986271] TCP: scalable registered
[    2.991866] TCP: lp registered
[    2.997101] TCP: yeah registered
[    3.002875] TCP: illinois registered
[    3.009671] Initializing XFRM netlink socket
[    3.018050] NET: Registered protocol family 10
[    3.026962] NET: Registered protocol family 17
[    3.034891] NET: Registered protocol family 15
[    3.044010] [mmc_pm]: No sdio card, please check your config !!
[    3.047683] Registering the dns_resolver key type
[    3.054449] VFP support v0.3: implementor 41 architecture 2 part 30 variant 7 rev 4
[    3.070692] Registering SWP/SWPB emulation handler
[    3.080107] axp20_buck2: Failed to create debugfs directory
[    3.091856] [cpu_freq] INF:-------------------V-F Table-------------------
[    3.103857] [cpu_freq] INF:	voltage = 1450mv 	frequency = 1008MHz
[    3.115013] [cpu_freq] INF:	voltage = 1425mv 	frequency =  912MHz
[    3.126160] [cpu_freq] INF:	voltage = 1350mv 	frequency =  864MHz
[    3.137306] [cpu_freq] INF:	voltage = 1250mv 	frequency =  720MHz
[    3.148451] [cpu_freq] INF:	voltage = 1150mv 	frequency =  528MHz
[    3.159596] [cpu_freq] INF:	voltage = 1100mv 	frequency =  312MHz
[    3.170742] [cpu_freq] INF:	voltage = 1050mv 	frequency =  144MHz
[    3.181886] [cpu_freq] INF:	voltage = 1000mv 	frequency =    0MHz
[    3.193810] [cpu_freq] INF:-----------------------------------------------
[    3.210429] [cpu_freq] INF:sunxi_cpufreq_initcall, get cpu frequency from sysconfig, max freq: 912MHz, min freq: 720MHz
[    3.224967] registered taskstats version 1
[    3.233612] I2C: i2c-4: HDMI I2C adapter
[    3.260067] ParseEDID
[    3.277040] EDID version: 1.3
[    3.286295] PCLK=148500000 X 1920 2008 2052 2200 Y 1080 1084 1089 1125 fr 60 PP
[    3.297454] Using above mode as preferred EDID mode
[    3.308172] PCLK=85500000 X 1360 1424 1536 1792 Y 768 771 777 795 fr 60 PP
[    3.327696] Unimplemented SVD code 2
[    3.333915] Unimplemented SVD code 33
[    3.340192] Unimplemented SVD code 34
[    3.346480] Unimplemented SVD code 21
[    3.352766] Unimplemented SVD code 38
[    3.359041] Unimplemented SVD code 21
[    3.368551] disp_clk: Could not find a matching pll-freq for 53900000 pclk
[    3.381260] disp_clk: Could not find a matching pll-freq for 25150000 pclk
[    3.393971] disp_clk: Could not find a matching pll-freq for 74200000 pclk
[    3.406680] disp_clk: Could not find a matching pll-freq for 72650000 pclk
[    3.419390] disp_clk: Could not find a matching pll-freq for 81800000 pclk
[    3.432102] disp_clk: Could not find a matching pll-freq for 26150000 pclk
[    3.442664] Parse_VideoData_Block: VIC 16 support
[    3.451804] Parse_VideoData_Block: VIC 31 (native) support
[    3.460870] Parse_VideoData_Block: VIC 4 support
[    3.469143] Parse_VideoData_Block: VIC 19 support
[    3.477417] Parse_VideoData_Block: VIC 5 support
[    3.485699] Parse_VideoData_Block: VIC 20 support
[    3.493972] Parse_VideoData_Block: VIC 3 support
[    3.502157] Parse_VideoData_Block: VIC 2 support
[    3.510438] Parse_VideoData_Block: VIC 18 support
[    3.518807] Parse_VideoData_Block: VIC 32 support
[    3.527182] Parse_VideoData_Block: VIC 33 support
[    3.535551] Parse_VideoData_Block: VIC 34 support
[    3.543920] Parse_VideoData_Block: VIC 21 support
[    3.552191] Parse_VideoData_Block: VIC 1 support
[    3.560386] Parse_AudioData_Block: max channel=2
[    3.569015] Parse_AudioData_Block: SampleRate code=57
[    3.577731] Parse_AudioData_Block: WordLen code=7
[    3.585924] Find HDMI Vendor Specific DataBlock
[    3.596292] PCLK=74250000 X 1920 2008 2052 2200 Y 540 542 547 562 fr 60 PP
[    3.609003] PCLK=74250000 X 1280 1390 1430 1650 Y 720 725 730 750 fr 60 PP
[    3.622148] PCLK=148500000 X 1920 2008 2052 2200 Y 1080 1084 1089 1125 fr 60 PP
[    3.635297] PCLK=74250000 X 1280 1720 1760 1980 Y 720 725 730 750 fr 50 PP
```


But I can't find any obvious errors in the dmesg log. Any ideas...

Full log:
[http://pastebin.com/UEcBnMvt](http://pastebin.com/UEcBnMvt)

---

### Post by him610 on 2015-08-10
Hello,

FWIW, when the original Raspberry Pi (Rpi) came out, to shut it down it had to be physically depowered (unplugged) in order to shut it off. I am not that familiar with Banana Pi, but if it is a digital/electro clone of the Rpi, I would think the same shutdown scenario applies to it.

---

### Post by juliushibert63 on 2015-08-10
> **hgh9mrp said:**
> Hello,

FWIW, when the original Raspberry Pi (Rpi) came out, to shut it down it had to be physically depowered (unplugged) in order to shut it off. I am not that familiar with Banana Pi, but if it is a digital/electro clone of the Rpi, I would think the same shutdown scenario applies to it.

That's true with the Rpi, however the Banana Pi has a physical off button. 

I have another Banana Pi that I've issued shutdown commands on ```
$sudo shutdown -h now
``` and the Banana Pi completely turn offs after about 30s.

The faulty Banana Pi / Lubuntu install in question never powers off or fully reboots.

---

### Post by juliushibert63 on 2015-08-17
[TABLE="width: 797"]
[TR]
[TD="class: t_f"]I worked it out. I'd stupidly installed the Banana Pi pro img and not the standard Pi image.

Banana Pi Lubunutu image -- correct one
[http://www.lemaker.org/portal.php?mod=list&catid=4](http://www.lemaker.org/portal.php?mod=list&catid=4)

Banana Pro Pi Lubunutu Image -- wrong one
[http://www.lemaker.org/portal.php?mod=list&catid=5](http://www.lemaker.org/portal.php?mod=list&catid=5)[/TD]
[/TR]
[/TABLE]

---

