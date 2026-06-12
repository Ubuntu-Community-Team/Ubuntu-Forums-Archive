---
title: "Help getting TV tuner to work"
date: 2013-01-15
forum: General Help
---

### Post by Azrael84 on 2013-01-15
I have bought a new laptop tuner (I think it's the same as the one in this thread: [http://ubuntuforums.org/showthread.php?t=2028123](http://ubuntuforums.org/showthread.php?t=2028123)). `lsusb` gives

```

     Bus 002 Device 005: ID 048d:9135 Integrated Technology Express, Inc. 
     Zolid Mini DVB-T Stick

````dmesg | grep -i dvb` after plugging in the usb stick gives

```

    [12280.493513] dvb-usb: found a 'ITE 9135 Generic' in cold state, will try 
    to load a firmware
    [12280.523395] dvb-usb: downloading firmware from file 'dvb-usb-
    it9137-01.fw'

```and I've followed the steps in the above thread I mentioned (moving the .fw files to relevant places) but end with the errors below. I thought this would now be resolved in a newer Kernel. Was this ever really resolved? my syslog tail shows
  
  ```

    myuser@mylap:~$ tail /var/log/syslog
    Jan 15 11:38:29 mylap kernel: [12280.493513] dvb-usb: found a 'ITE 9135 
    Generic' in cold state, will try to load a firmware
    Jan 15 11:38:29 mylap kernel: [12280.523395] dvb-usb: downloading firmware 
    from file 'dvb-usb-it9137-01.fw'
    Jan 15 11:38:29 mylap kernel: [12280.524030] it913x: FRM Starting 
    Firmware Download
    Jan 15 11:38:29 mylap kernel: [12281.022573] it913x: FRM Firmware Download
    Failed (ffffffed)
    Jan 15 11:38:29 mylap kernel: [12281.222204] it913x: Chip Version=6f Chip 
    Type=0203
    Jan 15 11:38:30 mylap kernel: [12282.056523] it913x: DEV it913x Error
    Jan 15 11:38:30 mylap kernel: [12282.056584] usbcore: registered new
    interface driver it913x

```The Kernel version I'm using is `uname -a`

```

     Linux mylap 3.2.0-35-generic-pae #55-Ubuntu SMP Wed Dec 5 18:04:39 UTC 
    2012 i686 i686 i386 GNU/Linux 

```I can't seem to get any further than this (I followed the steps earlier in the thread and put the .fw files in the firmware folders , but still get above errors). Kaffeine doesn't seem to pick up any tuner and wont even start a scan.

Can anyone help?

---

### Post by Azrael84 on 2013-01-16
I also found this thread: [http://patchwork.linuxtv.org/patch/10516/](http://patchwork.linuxtv.org/patch/10516/) but not sure if it resolves the problem or not to be honest

---

### Post by Azrael84 on 2013-01-17
It turns out I needed to obtain the V4L device drivers in addition to the above steps in OP. The method is presented here: [https://help.ubuntu.com/community/DVB-T_USB](https://help.ubuntu.com/community/DVB-T_USB) and [http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

After a restart

```

     dmesg | grep -i dvb
    [  236.965344] usbcore: registered new interface driver dvb_usb_it913x
    [  236.968782] usb 2-1.1: dvb_usb_v2: found a 'ITE 9135 Generic' in cold 
    state
    [  237.036706] usb 2-1.1: dvb_usb_v2: downloading firmware from file 
    'dvb-usb-it9135-02.fw'
    [  237.359951] usb 2-1.1: dvb_usb_v2: found a 'ITE 9135 Generic' in warm 
    state
    [  237.360025] usb 2-1.1: dvb_usb_v2: will pass the complete MPEG2 
    transport stream to the software demuxer
    [  237.360215] DVB: registering new adapter (ITE 9135 Generic)
    [  237.735476] usb 2-1.1: DVB: registering adapter 0 frontend 0 (ITE 9135 
    Generic_1)...
    [  237.782775] usb 2-1.1: dvb_usb_v2: schedule remote query interval to 250 
    msecs
    [  237.782779] usb 2-1.1: dvb_usb_v2: 'ITE 9135 Generic' successfully 
    initialized and connected

```
Now running `Kaffeine` and after selecting `Configure Television` my device is listed and I can select the source closest to me and the TV works!

---

