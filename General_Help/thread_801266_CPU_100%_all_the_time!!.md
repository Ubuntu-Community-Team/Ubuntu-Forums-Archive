---
title: "CPU 100% all the time!!"
date: 2008-05-20
forum: General Help
---

### Post by Kaneda187 on 2008-05-20
Okay this is a bit strange recently my CPU starts working really hard for no reason(well no reason I can see, keep in mind im a bit new to Ubuntu/Linux in general) 

Anyways back to the problem, I have my laptop on for say about 30 mins or more then the cpu just starts hitting 90% to 100% all the time and its not doing anything! All apps everything closed.... anyone got any ideas??

---

### Post by tamoneya on 2008-05-20
type: ```
top
``` into terminal (applications -> accessories -> terminal) and copy the result back in the forum.  The result will constantly be changing but just one "frame" of it.

---

### Post by Lexus Dominus on 2008-05-20
yes, its probably overheating, your cpu cant work as fast if its too hot, keep your laptops vent un-obstructed if you can

---

### Post by Kaneda187 on 2008-05-20
top - 19:12:23 up  1:35,  2 users,  load average: 2.82, 2.69, 2.86
Tasks: 151 total,   3 running, 148 sleeping,   0 stopped,   0 zombie
Cpu(s): 50.7%us,  0.3%sy,  0.0%ni, 48.7%id,  0.2%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2074244k total,   900992k used,  1173252k free,    44332k buffers
Swap:  2273156k total,        0k used,  2273156k free,   427452k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2760 root      16  -4 35904  33m  384 R   99  1.7  48:04.04 udevd              
 5553 root      20   0  356m  68m  18m S    2  3.4  13:19.62 Xorg               
21592 kaneda    20   0 73564  19m  10m R    1  1.0   0:00.72 gnome-terminal     
 5022 syslog    20   0  1936  688  532 S    1  0.0   0:02.64 syslogd            
 5080 klog      20   0  3716 2564  424 S    1  0.1   0:05.08 klogd              
 5930 kaneda    20   0 33500  19m  10m S    1  1.0   0:26.56 python             
18900 kaneda    20   0 21452  12m 7408 S    1  0.6   0:03.26 metacity           
19151 kaneda    20   0  130m  56m  19m S    0  2.8   0:20.84 firefox            
    1 root      20   0  2844 1688  544 S    0  0.1   0:01.40 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.24 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.28 events/0

---

### Post by Kaneda187 on 2008-05-20
thats it!

any ideas?

---

### Post by cdtech on 2008-05-20
I've seen this issue with trackerd

It will eventually settle down after it indexes everything. You can disable it. System > Preferences > Indexing Preferences, Uncheck the two check boxes in the first tab. You can also go to System > Preferences > Sessions and uncheck the Tracker entry.

I unchecked mine and it stoped hogging my cpu.

---

### Post by tamoneya on 2008-05-20
udevd is causing the problems it seems:> 2760 root 16 -4 35904 33m 384 R 99 1.7 48:04.04 udevd Try this article and see if it helps you out:[http://ubuntuforums.org/archive/index.php/t-76742.html](http://ubuntuforums.org/archive/index.php/t-76742.html)
Its a little old but it may work.

---

### Post by tamoneya on 2008-05-20
this bug report actually seems a little bit newer and more relevant:
[https://bugs.launchpad.net/ubuntu/+source/evms/+bug/115616](https://bugs.launchpad.net/ubuntu/+source/evms/+bug/115616)

You should read the report as it isnt to long but the short answer is ```
sudo apt-get remove evms
```

---

### Post by cdtech on 2008-05-20
udevd allows the serialization of hotplug events. I don't see this being the issue.

You would see this in the "tail /var/log/debug" log wouldn't you?

---

### Post by tamoneya on 2008-05-20
> **cdtech said:**
> udevd allows the serialization of hotplug events. I don't see this being the issue.

You would see this in the "tail /var/log/debug" log wouldn't you?

top says udevd is using 99% of the CPU.  That seems to tell me that udevd is doing something wrong.  Also it isnt udevd that I am removing.  Read the bug report and you will see that evms is what is causing the error and unless you know what evms is you probably arent using it so it should be safe to remove.

---

### Post by Kaneda187 on 2008-05-20
Thanks guys!!:) 

I got a lot to learn!

---

### Post by tamoneya on 2008-05-20
> **Kaneda187 said:**
> Thanks guys!!:) 

I got a lot to learn!

so i take it the problem was fully solved?

---

### Post by Kaneda187 on 2008-05-20
Bad news nope not resolved yet... i got this when i tried....

kaneda@Kanedas-Interface:~$ sudo apt-get remove evms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package evms is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libdc1394-13 libavformat1d libdvdread3 libsidplay1 libid3tag0 libquicktime1
  libmpeg2-4 libfaad0 liba52-0.7.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kaneda@Kanedas-Interface:~$ 


Any ideas?

---

### Post by Kaneda187 on 2008-05-20
nope check the log...

---

### Post by tamoneya on 2008-05-21
you should check both the log that cdtech mentioned as well as posting the result of ```
dmesg | tail
```

---

### Post by Kaneda187 on 2008-05-21
this the log of that command...

kaneda@Kanedas-Interface:~$ dmesg | tail
[ 6107.945152] wlan0: authenticate with AP 00:1b:2f:48:8e:bc
[ 6107.946572] wlan0: RX authentication from 00:1b:2f:48:8e:bc (alg=0 transaction=2 status=0)
[ 6107.946581] wlan0: authenticated
[ 6107.946585] wlan0: associate with AP 00:1b:2f:48:8e:bc
[ 6107.948175] wlan0: RX ReassocResp from 00:1b:2f:48:8e:bc (capab=0x431 status=0 aid=3)
[ 6107.948180] wlan0: associated
[ 6127.665974] wlan0: no IPv6 routers present
[ 7166.575317] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (7)
[ 7166.575903] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (9)
[ 7166.575968] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (13)
kaneda@Kanedas-Interface:~$ 

this is when the system is running normal...
it actually hasnt been acting up at all today it more then likely will start it sooner or later.. so ill post again then!

Thank so much for the help I really appreciate it.....and need it!

---

### Post by tamoneya on 2008-05-21
well in the bug report they were saying you have to restart after removing evms so that might be it except for the fact that you didnt actually remove anything.

---

### Post by scotthoge on 2008-06-02
I'm having the same problem, but definitely don't have evms installed. I'm also seeing TONS of nm_hal_device_added() and nm_hal_device_removed() in /var/log/debug. It will stop, of course, when I kill udevd and restart when I kick udevd --daemon off again, though it doesn't do it until it sees a USB device either added or removed.

This seems to be a fairly recent issue, as I didn't notice it doing this until well after I upgraded to Hardy.

---

### Post by scotthoge on 2008-06-03
Followup: The failure seems to be initiated by my BlackBerry. (Which otherwise syncs fine on my non-Linux systems) I tested with several USB drives and my ipod and the system performed normally.

---

