---
title: "HDMI output not recognized"
date: 2013-10-16
forum: General Help
---

### Post by Goncalo_Azevedo on 2013-10-16
Hello i am trying to output over my HDMI output port but i can't do it and i already tried a lots of things...

I have used xrandr to force the HDMI output with a FULL HD resolution (1920 x 1080) into my televison...I already have been able to force into VGA the output resolution i want but in HDMI i wasn't able and i dont realy know why....

First: I dont know why, when i do randr command the output are only two, LVDS1 and VGA1 should have HDMI insted of LVDS?

Second: When i did xrandr to VGA1 it works like a charm when i did to LVDS1 i received the follow error.

root@softcorporatetvpc:/home/softcorporatetvuser# xrandr --addmode LVDS1 "1920x1080_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  27
  Current serial number in output stream:  28

Can someone give me a help with this? if you need some more info just notice me and i will do my best...

Best regards
Gonçalo Azevedo

Other info: 
i am using a HDMI cable without DVI converters from the PC to the Television

Some outputs:

root@softcorporatetvpc:/home/softcorporatetvuser# xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 4096 x 4096
LVDS1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1366x768       60.4 +
   1360x768       59.8*    60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 886mm x 498mm
   1920x1080      60.0*+
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1360x768       60.0  
   1280x800       59.8  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
  1920x1080_60.00 (0xb2)  173.0MHz
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock   67.2KHz
        v: height 1080 start 1083 end 1088 total 11230           clock    6.0Hz
  1920x1080_75.00 (0xbf)  220.6MHz
        h: width  1920 start 2056 end 2264 total 2608 skew    0 clock   84.6KHz
        v: height 1080 start 1081 end 1084 total 1128           clock   75.0Hz
root@softcorporatetvpc:/home/softcorporatetvuser# 
--------------------------------------------------------------------------------------------
root@softcorporatetvpc:/home/softcorporatetvuser# lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller (rev 02)
--------------------------------------------------------------------------------------------
root@softcorporatetvpc:/home/softcorporatetvuser# lshw -c video
  *-display:0             
       description: VGA compatible controller
       product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:fe980000-fe9fffff ioport:cc00(size=8) memory:d0000000-dfffffff memory:fea00000-feafffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fe880000-fe8fffff
root@softcorporatetvpc:/home/softcorporatetvuser#
--------------------------------------------------------------------------------------------

---

### Post by Goncalo_Azevedo on 2013-10-21
Anyone?

---

