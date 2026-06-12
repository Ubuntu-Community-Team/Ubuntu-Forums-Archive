---
title: "Ubuntu keeps freezing, and logs are not helpful"
date: 2023-07-05
forum: General Help
---

### Post by ravi_joshi on 2023-07-05
My Ubuntu is freezing (not responding, nothing including mouse/keyboard and desktop shows old time). It happens once/twice a week. The computer is not subjected to heavy load. Instead it is freezing with just a text editor open as well. I have not figured out the actual culprit, though I have read many questions online [1]("https://askubuntu.com/q/38367"), [2]("https://askubuntu.com/q/850470"), [3]("https://askubuntu.com/q/1080743"), [4]("https://askubuntu.com/q/1360767"), [5]("https://askubuntu.com/q/1189965") but no success. The logs contain the following error messages:




Kernel Log
```

$ dmesg -T
[Fri May 19 13:50:42 2023] ACPI Error: Aborting method \_SB.PC00.PEG1.PEGP._DSM due to previous error (AE_ALREADY_EXISTS) (20220331/psparse-529)
[Fri May 19 13:50:42 2023] ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.PEG1.PEGP._DSM.USRG], AE_ALREADY_EXISTS (20220331/dsfield-184)
[Fri May 19 13:50:42 2023] ACPI Error: AE_ALREADY_EXISTS, CreateBufferField failure (20220331/dswload2-477)
[Fri May 19 13:50:42 2023] No Local Variables are initialized for Method [_DSM]
[Fri May 19 13:50:42 2023] Initialized Arguments for Method [_DSM]:  (4 arguments defined for method invocation)
[Fri May 19 13:50:42 2023]   Arg0:   00000000ed5b63f3 <Obj>           Buffer(16) 75 0B A5 D4 C7 65 F7 46
[Fri May 19 13:50:42 2023]   Arg1:   000000009f563d37 <Obj>           Integer 0000000000000102
[Fri May 19 13:50:42 2023]   Arg2:   00000000aa83d0d2 <Obj>           Integer 0000000000000010
[Fri May 19 13:50:42 2023]   Arg3:   00000000e5707ac8 <Obj>           Buffer(4) 00 00 50 4F

```


Sys Log
```

$ grep -i error /var/log//syslog.1
Jun 18 01:48:49 asus google-chrome.desktop[5778]: [5771:5802:0618/014849.027835:ERROR:connection_factory_impl.cc(471)] ConnectionHandler failed with net error: -2
Jun 18 02:26:57 asus systemd[1]: Starting Process error reports when automatic reporting is enabled...
Jun 18 02:26:57 asus whoopsie-upload-all[199055]: ERROR: whoopsie.path is not enabled
Jun 18 02:26:57 asus systemd[1]: Failed to start Process error reports when automatic reporting is enabled.
Jun 18 05:27:03 asus systemd[1]: Starting Process error reports when automatic reporting is enabled...
Jun 18 17:27:56 asus systemd[1]: Failed to start Process error reports when automatic reporting is enabled.
Jun 18 18:51:30 asus gnome-shell[2414]: JS ERROR: Failed to initialize fprintd service: Gio.IOErrorEnum: GDBus.Error:net.reactivated.Fprint.Error.NoSuchDevice: No devices available#012asyncCallback@resource:///org/gnome/gjs/modules/core/overrides/Gio.js:114:23
Jun 18 19:24:04 asus google-chrome.desktop[5778]: [5817:5824:0618/192404.953353:ERROR:ssl_client_socket_impl.cc(978)] handshake failed; returned -1, SSL error code 1, net_error -200
Jun 18 19:24:14 asus google-chrome.desktop[5778]: [5817:5824:0618/192414.020800:ERROR:ssl_client_socket_impl.cc(978)] handshake failed; returned -1, SSL error code 1, net_error -200
Jun 18 19:24:22 asus google-chrome.desktop[5778]: [5771:5797:0618/192422.543421:ERROR:cert_issuer_source_aia.cc(34)] Error parsing cert retrieved from AIA (as DER):
Jun 18 19:24:22 asus google-chrome.desktop[5778]: ERROR: Couldn't read tbsCertificate as SEQUENCE
Jun 18 19:24:22 asus google-chrome.desktop[5778]: ERROR: Failed parsing Certificate
Jun 18 22:18:21 asus systemd[1]: Stopped Process error reports when automatic reporting is enabled (timer based).
Jun 19 09:13:16 asus systemd[1]: Started Process error reports when automatic reporting is enabled (timer based).
Jun 19 09:13:16 asus kernel: [    0.683569] RAS: Correctable Errors collector initialized.
Jun 19 09:13:16 asus systemd[1]: Starting Process error reports when automatic reporting is enabled...
Jun 19 09:13:16 asus whoopsie-upload-all[1192]: ERROR: whoopsie.path is not enabled
Jun 19 09:13:16 asus systemd[1]: Failed to start Process error reports when automatic reporting is enabled.
Jun 19 09:13:16 asus systemd-xdg-autostart-generator[1353]: Not generating service for XDG autostart app-xiccd@autostart.service, error parsing Exec= line: No such file or directory
Jun 19 09:13:16 asus /usr/libexec/gdm-x-session[1380]: #011(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
Jun 19 09:13:16 asus kernel: [    3.916389] ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.PEG1.PEGP._DSM.USRG], AE_ALREADY_EXISTS (20220331/dsfield-184)
Jun 19 09:13:16 asus kernel: [    3.916394] ACPI Error: AE_ALREADY_EXISTS, CreateBufferField failure (20220331/dswload2-477)
Jun 19 09:13:16 asus kernel: [    3.916408] ACPI Error: Aborting method \_SB.PC00.PEG1.PEGP._DSM due to previous error (AE_ALREADY_EXISTS) (20220331/psparse-529)
Jun 19 09:13:16 asus kernel: [    3.916522] ACPI BIOS Error (bug): Failure creating named object [\_SB.PC00.PEG1.PEGP._DSM.USRG], AE_ALREADY_EXISTS (20220331/dsfield-184)
Jun 19 09:13:16 asus kernel: [    3.916524] ACPI Error: AE_ALREADY_EXISTS, CreateBufferField failure (20220331/dswload2-477)

```




Based on the Google search, the AE_ALREADY_EXISTS error is reported in the case of an old graphics driver. However, I am using new drivers in my Ubuntu. Please see below:


NVIDIA utility
```

$ nvidia-smi
Wed Jun 28 21:32:12 2023       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 515.65.01    Driver Version: 515.65.01    CUDA Version: 11.7     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  On   | 00000000:01:00.0  On |                  N/A |
|  0%   44C    P8    28W / 350W |   1098MiB / 24576MiB |     10%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      2128      G   /usr/lib/xorg/Xorg                322MiB |
|    0   N/A  N/A      2262      G   /usr/bin/gnome-shell              105MiB |
|    0   N/A  N/A      3795    C+G   ...014929417265448424,262144      620MiB |
|    0   N/A  N/A      6567      G   ...RendererForSitePerProcess       46MiB |
+-----------------------------------------------------------------------------+

```




GPU name
```

$ nvidia-smi --query-gpu=name --format=csv,noheader
NVIDIA GeForce RTX 3090

```


Surprisingly, the OS is using PREEMPT_DYNAMIC instead of SMP. However, I did not perform any kernel customization. Thus I expect it to be the default in Ubuntu, i.e., SMP. See below, please:




Kernel info
```

$ uname -a
Linux asus 5.19.0-45-generic #46~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Jun 7 15:06:04 UTC 20 x86_64 x86_64 x86_64 GNU/Linux

```




OS info
```

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:    22.04
Codename:    jammy

```


I am looking for suggestions to prevent my Ubuntu from freezing. I am wondering if the PREEMPT_DYNAMIC setting could be the cause of the issue. The question is cross-posted at [askubuntu.com]("https://askubuntu.com/q/1468535"), [NVIDIA forums]("https://forums.developer.nvidia.com/t/is-preempt-dynamic-causing-ubuntu-to-freeze/258156"). My apologies for the inconvenience.


It seems that the code formatting is broken. My apologies for the inconvenience.

---

### Post by TheFu on 2023-07-05
Does it happen if you don't use proprietary nvidia drivers?  Test and see.
May want to upgrade your MB BIOS, if a newer one is available too.
And I'd purge Google Chrome, if you think that's involved.

---

### Post by HermanAB on 2023-07-05
FWIIW, in my experience freezing were due to: Nvidia driver, faulty power supply, blown motherboard capacitors, faulty keyboard.

Divide and conquer - change one thing at a time!

---

### Post by TheFu on 2023-07-05
I had a problem with RAM being incompatible at the stated speeds with a Ryzen system after adding 2 more sticks of the same model/vendor.  Ryzen is known to be picky about RAM.  Over the years, with BIOS upgrades, that has improved, but it still demands "matched sets" for all the RAM in the system.  Intel is much more forgiving, IME.

Ended up slowing down the RAM from 3200 Mhz to 2666 Mhz to get a stable system.  Eventually, RAM got cheap and I pulled all the old RAM out, replaced it with 2 newer, larger, sticks for 60% less money.  

Sold 1 pair of the old RAM (matched) and still have another 16GB pair, also matched, to sell.

Also had a failing GPU cause lockups. It was a cheap nvidia. card (this was many, many, years ago). Replaced it with a cheap $35 nvidia GPU, which is starting to fail and will likely lose proprietary driver support soon. It is almost 15 yrs old now, so not really a bad value. Anyway, hardware issues can be the root cause, but sometimes it is software.  

If using an older kernel brings back stability, then I'd think it is a regression in the kernel being used.

---

### Post by ravi_joshi on 2023-07-05
> **TheFu said:**
> 
Does it happen if you don't use proprietary nvidia drivers? Test and see.

I initially installed cuda and Nvidia drivers from the official Nvidia website. It was cuda 11.7. However, the [online community suggested]("https://www.reddit.com/r/Ubuntu/comments/14pbwlp/comment/jqhgq39/?utm_source=share&utm_medium=web2x&context=3") executing *sudo ubuntu-drivers autoinstall*. It removed cuda 11.7 and installed a newer version. However, in both cases, the problem persists. I made it a dual-boot PC and noticed that Windows is not freezing until now. So, my guess is driver issues with Ubuntu! Well, I custom-built this PC to use Ubuntu, and I will delete the Windows partition once Ubuntu becomes stable.


> **TheFu said:**
> 
May want to upgrade your MB BIOS, if a newer one is available too.

BIOS is in the latest version.


> **TheFu said:**
> 
And I'd purge Google Chrome, if you think that's involved.

I am not sure about Google Chrome. Well, I have noticed the freezing even when Google Chrome is not open. Besides, I use Google Chrome now and then. 


> **TheFu said:**
> 
I had a problem with RAM being incompatible at the stated speeds with a Ryzen system after adding 2 more sticks of the same model/vendor. Ryzen is known to be picky about RAM. Over the years, with BIOS upgrades, that has improved, but it still demands "matched sets" for all the RAM in the system. Intel is much more forgiving, IME.

Yes, this is true. RAM compatibility is a big issue. I am using [Corsair DDR5-5600MHz 64GB (2 x 32GB)]("https://www.corsair.com/us/en/p/memory/cmk64gx5m2b5600c40/vengeancea-64gb-2x32gb-ddr5-dram-5600mhz-c40-memory-kit-a-black-cmk64gx5m2b5600c40"). The RAM, motherboard, and Intel processor's compatibility was verified before. RAM is running on 5600MHz with Intel XMP mode enabled.


> **TheFu said:**
> 
Also had a failing GPU cause lockups. It was a cheap nvidia. card (this was many, many, years ago). Replaced it with a cheap $35 nvidia GPU, which is starting to fail and will likely lose proprietary driver support soon. It is almost 15 yrs old now, so not really a bad value. Anyway, hardware issues can be the root cause, but sometimes it is software.

I understand. Well, I built this PC hardly 2-3 months back. This PC is equipped with an Intel Core i9-13900K processor and 64 GB RAM (DDR5). The GPU is MSI GeForce RTX 3090 VENTUS 3X 24GB. Most of the time, I hardly use even a fraction of the resources. For example, text editor, terminal, VS code editor, or something like that!  I could not spend much time on this PC in the beginning, but recently when I got time, it froze frequently. On the other hand, Windows seems OK. 


> **TheFu said:**
> 
If using an older kernel brings back stability, then I'd think it is a regression in the kernel being used.

Hmmm... I see. Because the freezing is intermittent, how do we know which kernel is well-suited?

---

### Post by ravi_joshi on 2023-07-05
> **HermanAB said:**
> 
FWIIW, in my experience freezing were due to: Nvidia driver, faulty power supply, blown motherboard capacitors, faulty keyboard.
Divide and conquer - change one thing at a time!

I suspect Nvidia driver. I made it a dual-boot PC and noticed that Windows is not freezing until now. So, my guess is driver issues with Ubuntu!

---

### Post by tea for one on 2023-07-06
Wayland or X11 session?
There are many internet articles about the performance of Nvidia and Wayland.

---

### Post by ravi_joshi on 2023-07-06
> **tea for one said:**
> 
Wayland or X11 session?
There are many internet articles about the performance of Nvidia and Wayland.


It is a default installation of Ubuntu, and I have not changed the display manager. Therefore, I guess it is an X11 session.

---

### Post by tea for one on 2023-07-06
> **ravi_joshi said:**
> Therefore, I guess it is an X11 session.
Regrettably, department of guesswork failed you this time.;)
Ubuntu 22.04 defaults to Wayland.
You can check via a terminal command:-
```
echo $XDG_SESSION_TYPE
```

---

### Post by TheFu on 2023-07-06
> **ravi_joshi said:**
> I suspect Nvidia driver. I made it a dual-boot PC and noticed that Windows is not freezing until now. So, my guess is driver issues with Ubuntu!

You may want to let nvidia know how unhappy you are with their drivers.  In the meantime, try the F/LOSS driver. Is that stable?
Did you try some other kernels?  Until you try them, you'll never know if this is kernel related or not?

You are running very new hardware. That's often a problem for Linux, since vendors don't test their hardware with Linux and the kernel guys won't have it until it becomes available.  Welcome to Linux, where the newest hardware you'd want needs to be at least 1 yr old.

---

### Post by ravi_joshi on 2023-07-06
> **tea for one said:**
> Regrettably, department of guesswork failed you this time.;)
Ubuntu 22.04 defaults to Wayland.
You can check via a terminal command:-
```
echo $XDG_SESSION_TYPE
```


God is with me and my luck ;)
```

$ echo $XDG_SESSION_TYPE
x11

```

---

### Post by ravi_joshi on 2023-07-06
> **TheFu said:**
> 
You may want to let nvidia know how unhappy you are with their drivers. In the meantime, try the F/LOSS driver. Is that stable?

Thank you very much for providing constant support. Presently, it is NVIDIA proprietary driver. What are the Free and open-source drivers for the same? The X.Org? I wish to use my 4K display and cuda for my AI-related tasks.

[IMG]https://i.ibb.co/VThwdtM/FLOSS-driver.png[/IMG]
[IMG]https://ibb.co/dD3mSrk[/IMG]
[IMG]https://ibb.co/dD3mSrk[/IMG]

> **TheFu said:**
> 
Did you try some other kernels? Until you try them, you'll never know if this is kernel related or not?

I have checked with kernels 5.19.0-*. Do you happen to know an old yet stable kernel?


> **TheFu said:**
> 
You are running very new hardware. That's often a problem for Linux, since vendors don't test their hardware with Linux and the kernel guys won't have it until it becomes available. Welcome to Linux, where the newest hardware you'd want needs to be at least 1 yr old.

Yeah. I think so. I considered building this PC with the latest hardware and dreamed of using Ubuntu! Lol :lolflag:
Please keep guiding me in this journey of debugging! Thank you again.

---

### Post by TheFu on 2023-07-06
I'm not going to be any more help.  

I don't have the problems you have and I don't have the same hardware nor to I run really new OSes directly on hardware. My systems running on physical hardware are on the 5.15.x kernels or older.  Even my newest desktop is running the 5.15.x kernel line.

Whether a kernel is stable is specific to your hardware, drivers, etc.  Only you can figure this out.  My systems are very stable.
```
$ uptime
 10:08:00 up 21 days, 23:30,
```

---

### Post by ravi_joshi on 2023-07-06
Thanks a lot, @TheFu I will try your suggestions, one by one. Thanks again.

---

### Post by tea for one on 2023-07-07
Your processor Intel Core i9-13900K was released in October 2022 therefore it may be worth trying a newer kernel.
New hardware invariably needs a recent kernel.

I suggest that you try Ubuntu 23.04 in a live session for a few hours (without the Nvidia GPU).
If any degree of success, then include the Nvidia GPU and test again.

---

### Post by ravi_joshi on 2023-07-07
> **tea for one said:**
> Your processor Intel Core i9-13900K was released in October 2022 therefore it may be worth trying a newer kernel.
New hardware invariably needs a recent kernel.

I suggest that you try Ubuntu 23.04 in a live session for a few hours (without the Nvidia GPU).
If any degree of success, then include the Nvidia GPU and test again.

Let me try that ! I will update you with the results.

Thank you so much.

---

