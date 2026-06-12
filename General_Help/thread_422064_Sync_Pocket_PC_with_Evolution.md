---
title: "Sync Pocket PC with Evolution?"
date: 2007-04-24
forum: General Help
---

### Post by CybaCowboy on 2007-04-24
Hi,


I'm trying to connect my Pocket PC to my computer and synchronize it with Evolution, however I'm not having any luck...


These are the instructions I used:

> **tUrtleAE86 said:**
> 
**[SIZE=3]Does Linux like your PDA?[/SIZE]**

1) Connect your Pocket PC and type "dmesg" in a shell to see if the ipaq kernel module is loaded. The output might look like the following. Take note of the tty used for the connection.
```
usb 4-2: new full speed USB device using uhci_hcd and address 3
ipaq 4-2:1.0: PocketPC PDA converter detected
usb 4-2: PocketPC PDA converter now attached to ttyUSB0
```
2) Optionally, you can use "cat /proc/bus/usb/devices" to check for a USB device that's using the ipaq kernel module.
```
T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.01 Cls=ff(vend.) Sub=ff Prot=ff MxPS=16 #Cfgs=  1
P:  Vendor=413c ProdID=4002 Rev= 0.00
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=ipaq
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
```

**[SIZE=3]SynCE Setup and Configuration[/SIZE]**

1) Install the required packages for SynCE:
```
sudo apt-get install librra0 librra0-tools librapi2-tools libsynce0 synce-dccm synce-multisync-plugin synce-serial
```
2) synce-serial setup will be invoked by apt, follow this through using the default settings, unless you have reason to do otherwise. 
```
/dev/ttyUSB0
local address: 192.168.131.102
remote address: 192.168.131.201
no dns entry needed
```
3) Perform the following the following command to tell SynCE where to look. This seems redundant, but doesn't hurt.
```
sudo synce-serial-config ttyUSB0
```
4) Start the SynCE connection daemon by typing "dccm" in a shell. Use "dccm -p password" if your Pocket PC is password protected.
5) Initiate a serial connection by typing "sudo synce-serial-start" in a shell. You should be greeted with "synce-serial-start is now waiting for your device to connect".



However when I type this:

> **tUrtleAE86 said:**
> 
6) "synce-pstatus" shows a LOT of information about your Pocket PC, such as current mode of operation, battery charge level, memory usage as well as backup battery status. If you want to see some other synce commands, type "dpkg -L librapi2-tools". You can use these commands to do things such as installing Pocket PC programs, etc.


I am told:
*synce-pstatus: Could not find configuration at path '(Default)'*


Finally, when I type:

> **tUrtleAE86 said:**
> 
7) Create the partnership between the Pocket PC and your computer. There are 2 slots on the device, so the INDEX can be 1 or 2.
```
synce-matchmaker create INDEX
```
You should be greeted with:
```
Partnership creation succeeded. Using partnership index INDEX.
```


I am told:
[i]cowboy@cowboy-pc:~$ synce-matchmaker create index
[synce_info_from_file:51] unable to open file: /home/cowboy/.synce/active_connection
[rapi_context_connect:100] Failed to get connection info
[main:62] Failed to initialize RAPI
[/i]


Can someone help me get my Pocket PC to sync with Evolution?

It's only my contacts that I particularly need to sync, but if i can actually get it working, then it will be enough to convince me to switch to Ubuntu (Linux) full-time...

---

### Post by wersdaluv on 2007-04-26
What happens when you enter sudo synce-serial-start?

---

### Post by CybaCowboy on 2007-04-26
This is my Terminal screen after typing "sudo synce-serial-start":

[i]
cowboy@cowboy-pc:~$ sudo synce-serial-start
Password:

Warning!

synce-serial-start cannot find the dccm process.
Without dccm your PPP connection will soon terminate!


synce-serial-start is now waiting for your device to connect
[/i]

If it's any help, a graphical version of "Multisync" loads up whenever I connect my Pocket PC, but I've played around with the program and nothing seems to happen... It says that it's running, but that's it.

Is this somehow related to my problems?

---

### Post by CybaCowboy on 2007-04-27
Bump!

---

### Post by Stormx on 2007-05-01
You need to run vdccm before you run sudo synce-serial-start

---

### Post by famleon on 2008-01-07
do you know where i can find a really easy script or, step by step but for dummies instructions, because i have been looking and even that i try to look for this, itr says do this or do that, but..where do i have to do this or that??? I am LOST...I am new in this linux thingy and I am trying to learn.. thanks

---

