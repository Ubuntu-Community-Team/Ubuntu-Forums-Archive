---
title: "HOWTO: Using Bluetooth to acces Mobile Phone and use BT-Headset to use Skype"
date: 2005-10-14
forum: General Help
---

### Post by joker667 on 2005-10-14
I just dont know where to post it, so please feel free to move it. Comments appreaciated :)


Mission: Use Bluetooth to access the Files on my Mobile Phone, and to use my Bluetooth Headset with Skype - in 3 Chapters


PART 1: Copy Files from and to Mobile Phone (K700i) - simple ;)

1. Install bluez-utils
2. Install kdebluetooth (gnome bluetooth is not as far developed as kde I think), libopenobex, qobex
3. Install konqueror
4. Check /etc/bluetooth/hcid.conf: 
	security should be user
	pairing should be multi
	pin_helper should be /usr/bluez-pin
5. restart bluez-utils /etc/init.d/bluez-utils restart
6. start kbluetoothd (it sometimes needs to be startet twice on my machine until the icon shows up in the System Notifications Tray)
7. Enable Bluetooth on your Device (Mobile Phone etc.)
8. If you click on the kbluetoothd Icon, konqueror will show up with "bluetooth:/" location, listing all BT Devices found
9. Click on your Device (sometimes only the MAC-Adress shows up), konqui will list all supported Services, and start using the Service (for my Mobile, K700i its obex File Transfer, then I can browse my Mobile like a Disk Drive, copying what I want). Previous to that, my phone wants to pair with my PC, aksing for a PIN. Just guess one (1234), after that a popup on the PC should occour, asking for the same PIN.
10. You could also send Files from the Phone to your PC, then a popup will show up, asking you, if you wish to receive the file.



PART 2: Using a Bluetooth Headset - tricky, but also easy when knowing how ;)

1. Load Kernel Module for btsco: "sudo modprobe btsco", checking "dmesg" if it runs. To load it permanently add it to /etc/modules, just write "btsco" at the end of the File
2. Install the following missing (at least on my system) packages needed by the btsco Userspace driver. Easy, because you have apt-get or synaptic: 
	gcc
	gcc-4.0
	altgcc 
	libc6-dev
	linux-kernel-headers
	libasound2-dev
	libao-dev
	libbluetooth1-dev
3. Download latest btsco from [http://sourceforge.net/projects/bluetooth-alsa/](http://sourceforge.net/projects/bluetooth-alsa/), unzip to Desktop perhaps
4. Time for the shell! ;)
	cd btsco-0.4
	./configure
	make
	sudo make install
5. Now pair your Headset with your PC (as above with the Mobile):
	- Headset needs to be in pairing-mode (often this is accomplished with holding the on buttons for a looong time)
	- start kbluetoothd, click on it, in the opened konqueror window click on the headset (sometimes the MAC-Adress shows up)
	- a popup should request the PIN for the Headset from you (mostly "0000" or "1234")
6. Start the btsco Userspace Program: "btsco -v 00:00:00:00:00" replace the zeros with the MAC Adress of your Headset (right click on kbluetoothd icon, connection details)
7. Verify its working:
	- "aplay -B 1000000 -D plughw:Headset sound.wav" (replace sound.wav with a Wave-File of your choice. An MP3 also works, but you will only hear strange noise :)
	- Use XMMS: Options -> Preferences -> Audio I/O -> Output Plugin. Select ALSA -> configure, and select your Headset as Audiodevice. Restart XMMS and you should hear the music with the Headset.
	- You can use the VolumeManager from gnome to adjust the volume, right click on the speaker in the tray -> Settings -> File -> Change Device

Everyday Use: If you load the Kernelmodule automatically, you just need to execute "btsco -v your_headsets_mac_adress" - really easy for everyday use. You can optional start kbluetoothd to check Signalstreght etc.



PART 3: Using Skype

1. In Breezy, there is currently no easy way to install Skype (broken dependencies,you can just grab an older Version from here: [http://www.mneylon.com/blog/archives/2005/09/25/skype-on-breezy/](http://www.mneylon.com/blog/archives/2005/09/25/skype-on-breezy/) , [http://www.mneylon.com/blog/go.php?http://www.mneylon.com/skype_1.2.0.11_i386.deb](http://www.mneylon.com/blog/go.php?http://www.mneylon.com/skype_1.2.0.11_i386.deb). Install it via "sudo dpkg -i skype_1.2.0.11_i386.deb
Alternative: [http://www.ubuntuforums.org/showthread.php?t=75107](http://www.ubuntuforums.org/showthread.php?t=75107), or 

2. Launch Skype, go to options Headset and select "/dev/dsp1" as device

3. Try to call "echo123" to check it, when you just hear garbage, turn your headset off and on again, and start "btsco -v 00:00:00:00:00" again. This happens on my Machine every second time I try to use my Headset - also under WindowsXP!

---

### Post by Profus on 2005-10-18
Thanks a lot for this howto... just what I needed.

Now I finally got my Jabra BT250 Headset to work under Linux (Kubuntu Breezy). I still can't use it with skype though, it kind of works but the sound is somewhat distorted and from time to time it fades away completely. On Windows XP and with my mobile phone it works perfectly. Any ideas what I could do?

Cheers,
Fabian

**Edit:**

I've found the problem now: The full duplex checkbox in the audio settings panel was disabled by default. After enabling it, the problems I experienced yesterday were gone.

A new issue has arisen though: 
After making a number of calls using skype initiating a new call will fail (skype says: audio device problem, btsco says device busy), quitting and restarting skype seems to solve the problem but it's not a very comfortable solution. Btw I'm using the following skript to start up skype and enable the headset simultaneously:
[FONT="Courier New"]
#!/bin/bash
btsco -v [headset's MAC-Address] &
skype
[/FONT]

---

### Post by hp99 on 2005-11-12
hi, thanks for the HOWTO.

kdebluetooth 0.99+1-2beta1-2ubuntu3
bluezutils 2.20-0ubuntu3

First I tried using the gnome-bluetooth manager without success due to sdp server problems.

:confused: With kdebluetooth I ran into a stupid misconfiguration-error. The link_key file wasn't set correctly.  
I've got this error message in the terminal, while kdebluetooth notified the Authentication Error:
> QFile::open: No file name specified


Solution: :p 
Kbluetoothd was looking for a file called link_key in /etc/bluetooth. But in out distrubution the file is called /etc/bluetooth/pin. So I renamed it. Also it should work to make a link:

#> sudo ln /etc/bluetooth/pin /etc/bluetooth/link_key -s

Just wanted to tell..

---

### Post by hp99 on 2005-11-12
hi, thanks for the HOWTO.

kdebluetooth 0.99+1-2beta1-2ubuntu3
bluezutils 2.20-0ubuntu3

First I tried using the gnome-bluetooth manager without success due to sdp server problems.

:confused: With kdebluetooth I ran into a stupid misconfiguration-error. The link_key file wasn't set correctly.  
I've got this error message in the terminal, while kdebluetooth notified the Authentication Error:
> QFile::open: No file name specified


Solution: :p 
Kbluetoothd was looking for a file called link_key in /etc/bluetooth. But in out distrubution the file is called /etc/bluetooth/pin. So I renamed it. Also it should work to make a link:

#> sudo ln /etc/bluetooth/pin /etc/bluetooth/link_key -s

Just wanted to tell..

---

### Post by reto on 2005-11-15
Thanks for the how-to, got my plantronics M2500 Headset to work with my Dell inspiron 9300. It works with Linphone an Kphone (next  thing would be to manage to compile and install twinkle, a sip-client which allows to have phone ringing on a different device than the conversation).

However: I cannot supsend or hibernate my laptop any longer :( . I find the following in syslog:
Nov 15 17:41:56 localhost kernel: [4296263.056000] Restarting tasks...<6> Strange, snd-bt-scod not stopped

Did anybody manage to use a bluetotth headset and be able to supspend as well?

---

### Post by jdmpike on 2005-11-19
Hello all,

After many frustrations and stubborness, you have finally won. I have given up trying to use gnome-bluetooth, and I have started trying to use kbluetoothd.

When I enter pairing mode, kbluetoothd can see my headset and after calling bluez-pin to get the pin, it lets me open the device to see the headset profiles that exist there. This is good because I know it can sort of see the device.

However, when I try to run btsco -v <mac_addr>, the shell shows the following error.

```
jordan@jdmlaptop:~$ btsco -v <mac_addr>
btsco v0.4
Device is 1:0
Error: Failed to connect to SDP server: Permission denied
Assuming channel 2

Voice setting: 0x0060
Can't connect RFCOMM channel: Too many levels of symbolic links

```

I was actually able to use my headset to make a call with skype when using hcitool scan and btsco to connect. After the call though, I experienced the same error as above where skype would tell me "Problem with Sound device"

Thanks for the help all...

---

### Post by Lmax on 2005-12-06
Installation of the headset works fine for me up to point 6. I don't get any errors. Except when i verify the installation i don't hear anything.
The headset seems to pair alright, kbluetoothd says it's connected and gives all kind of connection details.
btsco -v <mac-address> is also working fine. No errors there.
Only sometimes a strange error about a driver (see bottom of post)

But when i try to play the sound i don't hear anything. And the aplay command seems to stall(nothing happens and i have to abort. Though when i play it over my regular soundcard this works fine.

dmesg doesn't give any clues. Are there more logs i can check. Or any other clues?
I read on bluetooth-alsa site that when the dongle is on a hub it might give problems. But my bluetooth is built-in. Can't change it. And then the hub itself would probably already give problems then.

It's Ubuntu breezy on a acer trevelmate 8103. The bluetooth chipset is  a broadcom BCM 2035. The headset i try to connect is a logitech HS01

Thanks for any help/response.

```

btsco -v output:

btsco v0.4
Device is 1:0
Voice setting: 0x0060
RFCOMM channel 1 connected
/usr/lib/openoffice2/share/gallery/sounds/explos.wav
speaker volume: 12 mic volume: 1
recieved AT+CKPD=200
recieved AT+CKPD=200
speaker volume: 12 mic volume: 1
driver is in use
connected SCO channel
Done setting sco fd
recieved AT+VGS=12

```

---

### Post by swathi_mathur80 on 2005-12-08
Hello,
I am posting on this forum for the first time. Actually i am trying to transfer audio files from my pc to my headset. My pc is running Red hat Linux OS and using Bluez stack. Can anyone tell me where to find the below modules

1) libbluetooth-dev (aka libbluetooth-devel or bluetooth-devel or bluez-libs) and the 
2) libasound2-dev 

What does the below step mean and i don't know where to execute it, 
--------------------------------------------------------
Check btsco out from cvs: 
cvs -d:pserver:anonymous@cvs.sf.net:/cvsroot/bluetooth-alsa login
cvs -d:pserver:anonymous@cvs.sf.net:/cvsroot/bluetooth-alsa co btsco
--------------------------------------------------------

Thanks in Advance,
Swathi

---

### Post by Lmax on 2005-12-10
I now have the problem i cant connect to my headset anymore. It connected a couple of days ago, but that doesn't work anymore.
Bluetooth is working. I can connect with my nokia phone, and i use a bluetooth mouse so that's not the problem
If i do hidd connect it doesnt seem to work.

hidd --connect 00:0D:44:0B:96:86
Can't get device information: Success

kbluetoothd output's these errors
kbluetoothd: Checking state00:0D:44:0B:96:86 1
kbluetoothd: HciSocket::open()
kbluetoothd: Checking state00:07:61:12:C1:87 1
kbluetoothd: connections: 2
kbluetoothd: slotConnectionStateChanged
kbluetoothd: HciSocket::open()
kbluetoothd: HciSocket::open()
kbluetoothd: Checking state00:0D:44:0B:96:86 1
kbluetoothd: HciSocket::open()
kbluetoothd: Checking state00:07:61:12:C1:87 1
kbluetoothd: connections: 2
kbluetoothd: HCI-event: e
kbluetoothd: HCI-event: 13
kbluetoothd: HCI-event: 13
kbluetoothd: HCI-event: 13
kbluetoothd: HCI-event: 13
kbluetoothd: HCI-event: 13
kbluetoothd: HCI-event: f
kbluetoothd: HCI-event: 5


The mac address ending with 86 is my headset. The one with 87 is my mouse.

Any help or suggestions would be greatly appreciated.

Thanks

---

### Post by skaber on 2005-12-12
I've got my mouse mx900 working perfectly with my bluetooth device integrated but I seriously can't get my iogear headset to work. I m using breezy and fallowed this tutorial step by step (as well as other tuts elsewhere).

It seems my laptop can't pair the headset with the pin 1234. I've also noticed the error "QFile::open: No file name specified" when I click on the Headset in Konqueror. I tried renaming the file /etc/bluetooth/pin to link_key but still had no success....

i ve passed many hours trying alot of changes but nothing was sucessfull yet.
does any one have an idea how i could sucessfully pair the headset with my laptop ?


-----------------------


After looking up some other forums and trying some stuff. I found out from my syslog file that the problem was really pairing. I decided to delete the folder /var/lib/bluetooth/00:10:C6:5B:12:D3 wich refers to my bluetooth integrated device's MAC. This folder usually stores pin numbers for each bluetooth device.

I changed the pin_helper to /usr/bin/bluepin in hcid.conf

I started my headset in pairing mode and this time, i was prompted for a PIN number when using btsco -v <headset>.

the key to my sucess: Deleting the folder /var/lib/bluetooth/<MAC bluetooth>

hope this can help !

---

### Post by J D Wijbenga on 2005-12-21
Exelent how-to, thank you!

I do have one question I hope someone can help me with. When I try to pair my Nikia phone with my Ubuntu laptop I have to enter a code. I have tried 1234 and others but without luck. I constandly recieve the error "Paring failed". 

What am I doing wrong? Am more importantly, how can I fix it?

Thanks,
JD

---

### Post by dannemil on 2005-12-23
> **joker667]I just dont know where to post it, so please feel free to move it. Comments appreaciated :)


Mission: Use Bluetooth to access the Files on my Mobile Phone, and to use my Bluetooth Headset with Skype - in 3 Chapters


<stuff deleted>

PART 2: Using a Bluetooth Headset - tricky, but also easy when knowing how  said:**
> http://sourceforge.net/projects/bluetooth-alsa/[/url], unzip to Desktop perhaps
4. Time for the shell! ;)
	cd btsco-0.4
	./configure
	make
	sudo make install
5. Now pair your Headset with your PC (as above with the Mobile):
	- Headset needs to be in pairing-mode (often this is accomplished with holding the on buttons for a looong time)
	- start kbluetoothd, click on it, in the opened konqueror window click on the headset (sometimes the MAC-Adress shows up)
	- a popup should request the PIN for the Headset from you (mostly "0000" or "1234")
6. Start the btsco Userspace Program: "btsco -v 00:00:00:00:00" replace the zeros with the MAC Adress of your Headset (right click on kbluetoothd icon, connection details)
7. Verify its working:
	- "aplay -B 1000000 -D plughw:Headset sound.wav" (replace sound.wav with a Wave-File of your choice. An MP3 also works, but you will only hear strange noise :)
	- Use XMMS: Options -> Preferences -> Audio I/O -> Output Plugin. Select ALSA -> configure, and select your Headset as Audiodevice. Restart XMMS and you should hear the music with the Headset.
	- You can use the VolumeManager from gnome to adjust the volume, right click on the speaker in the tray -> Settings -> File -> Change Device

Everyday Use: If you load the Kernelmodule automatically, you just need to execute "btsco -v your_headsets_mac_adress" - really easy for everyday use. You can optional start kbluetoothd to check Signalstreght etc.



PART 3: Using Skype

1. In Breezy, there is currently no easy way to install Skype (broken dependencies,you can just grab an older Version from here: [http://www.mneylon.com/blog/archives/2005/09/25/skype-on-breezy/](http://www.mneylon.com/blog/archives/2005/09/25/skype-on-breezy/) , [http://www.mneylon.com/blog/go.php?http://www.mneylon.com/skype_1.2.0.11_i386.deb](http://www.mneylon.com/blog/go.php?http://www.mneylon.com/skype_1.2.0.11_i386.deb). Install it via "sudo dpkg -i skype_1.2.0.11_i386.deb
Alternative: [http://www.ubuntuforums.org/showthread.php?t=75107](http://www.ubuntuforums.org/showthread.php?t=75107), or 

2. Launch Skype, go to options Headset and select "/dev/dsp1" as device

3. Try to call "echo123" to check it, when you just hear garbage, turn your headset off and on again, and start "btsco -v 00:00:00:00:00" again. This happens on my Machine every second time I try to use my Headset - also under WindowsXP!

[COLOR="Red"]**OUTSTANDING! This worked to let me use my Jabra BT200 with skype. Thanks for the help. -- Jim**[/COLOR]

---

### Post by KSDZ on 2005-12-27
[QUOTE=jdmpike]Hello all,

After many frustrations and stubborness, you have finally won. I have given up trying to use gnome-bluetooth, and I have started trying to use kbluetoothd.

When I enter pairing mode, kbluetoothd can see my headset and after calling bluez-pin to get the pin, it lets me open the device to see the headset profiles that exist there. This is good because I know it can sort of see the device.

However, when I try to run btsco -v <mac_addr>, the shell shows the following error.

```
jordan@jdmlaptop:~$ btsco -v <mac_addr>
btsco v0.4
Device is 1:0
Error: Failed to connect to SDP server: Permission denied
Assuming channel 2

Voice setting: 0x0060
Can't connect RFCOMM channel: Too many levels of symbolic links

```

I was actually able to use my headset to make a call with skype when using hcitool scan and btsco to connect. After the call though, I experienced the same error as above where skype would tell me "Problem with Sound device"

Thanks for the help all...[/QUOTE]


I'm experiencing this same problem.

Also, when it doesn't give this error (it does sometimes, I don't know why) and I run aplay, I hear the headset beep to let me know a connection was made, then I don't hear any sound, and after that, when the wav has stopped playing I hear the disconnect beep.

Oh and sometimes ```
"hcitool cc *address*"
``` gives:
```
Can't create connection: Input/output error
```

I'm running Ubuntu 5.10 Linux 2.6.12-10-686 (latest update),
btsco version is 0.4
My headset is a Sony-Ericsson HBH-PV700
```
sdptool search --bdaddr <bluetooth-address> 0x1108
```
gives:
```

Class 0x1108
Searching for 0x1108 on <bluetooth-address> ...
Service Name: SonyEricsson Headset Service
Service RecHandle: 0x10002
Service Class ID List:
  "Headset" (0x1108)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
Profile Descriptor List:
  "Headset" (0x1108)
    Version: 0x0100

```
Heres some info on my bluetooth chip:
```

$ sudo hciconfig hci0 features
hci0:   Type: USB
        BD Address: 00:......:26 ACL MTU: 377:10 SCO MTU: 16:0
        Features: 0xff 0xff 0x0d 0x38 0x08 0x08 0x00 0x00
                <3-slot packets> <5-slot packets> <encryption> <slot offset>
                <timing accuracy> <role switch> <hold mode> <sniff mode>
                <park state> <RSSI> <channel quality> <SCO link> <HV2 packets>
                <HV3 packets> <u-law log> <A-law log> <CVSD> <power control>
                <transparent SCO> <enhanced iscan> <interlaced iscan>
                <interlaced pscan> <AFH cap. slave> <AFH cap. master>
$ sudo hciconfig hci0 revision
hci0:   Type: USB
        BD Address: 00:0B:6B:5E:01:26 ACL MTU: 377:10 SCO MTU: 16:0
        Firmware 105.105 / 74
$ sudo hciconfig hci0 version
hci0:   Type: USB
        BD Address: 00:0B:6B:5E:01:26 ACL MTU: 377:10 SCO MTU: 16:0
        HCI Ver: 1.2 (0x2) HCI Rev: 0x69 LMP Ver: 1.2 (0x2) LMP Subver: 0x694a
        Manufacturer: Broadcom Corporation (15)

```
anyone who knows how to solve this?
thanks in advance

---

### Post by KSDZ on 2006-01-02
Fixed my issiue by buying a new dongle,

As you can see my built-in bluetooth is Broadcom and has SCO MTU16:0
My new one is CSR as recommended and has a SCO MTU 64:8
and it works like a charm!

---

### Post by Zaknarus on 2006-01-02
I proceed like above. I can send data to my Handy. But when I try to pair it with my headset. the follwing message appear(screenshot). Each time I try to connect to my notebook by pressing the connect button on the headset the connection appear for a second an then is deactivatet. Does anybody know a solution?

Best regards
Alexander

---

### Post by _jB on 2006-01-09
Thx alot, that was **soooooo** easy :)

---

### Post by myddrin on 2006-01-10
Yes, as I discovered as well, getting the right dongle is required.  My original dongle a Zonet ZUB6111C looked like it connected, but I could not play or record sound from it.  My new one that I got from PCTekOnline (for about $8 LESS than the zonet one), worked on the first try.

I'm not trying to figure out if there is a way to start the btsco user program when my headset is discovered.  So far no luck, is there an eventing mechanism in bluez or kbluetoothd that will let me do that?  I've tried the kbluetoothd discovery scripts, but they don't seem to be working for what I want to do.

---

### Post by toorima on 2006-01-17
For those who get a problem with pairing there phone I found this [http://www.ubuntuforums.org/showthread.php?t=113903](http://www.ubuntuforums.org/showthread.php?t=113903)

---

### Post by damien82 on 2006-01-17
ok, paring phone and headset is no problem...but, this is what i get:

btsco -v 00:07:A4:a8:94:A6
btsco v0.41
Device is 3:0
Error: Failed to connect to SDP server: Host is down
Assuming channel 2

Voice setting: 0x0060
Can't connect RFCOMM channel: Host is down


Anyone got a clue what to do?

---

### Post by lyly on 2006-01-26
Does anyone know if it is possible to have 2 bluetooth headset connected on one usb dongle to use with skype?

---

### Post by lyly on 2006-02-04
I have tried this tutorial to use my JabraFS28 (seems to correspond to the EU/US model BT205).

I was able to pair it with my usb dongle after having the command ```
 $ xhost +
``` in the terminal.

But when I install btsco driver (make install + edit the /etc/modules file), all my sound is messed up! when lauching rythmbox and play a file, it the application freeze and need to be "force quit" and then no more gnome apps works properly without reboot (logout and relogin leads to a braun screen with noting on it except the cursor. The others virtual consoles are ok...).
I "make uninstall" and correct back the /etc/modules file, and fortunately the sound works again...

Is there a problem using btsco with my hardware? I am under breezy with the official backports... Under are the result of lsusb with the dongle, lspci and lsmod (when everything is repaired)

Please help :cry: ! I really like to have this headset working under breezy... 

```

$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
**Bus 003 Device 003: ID 1131:1001 Integrated System Solution Corp.**
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

```

$ lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
**0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)**
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
0000:03:01.0 CardBus bridge: Texas Instruments: Unknown device 8036
0000:03:01.5 Communication controller: Texas Instruments: Unknown device 8038
0000:03:03.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

```

```
$ lsmod
Module                  Size  Used by
hci_usb                14088  2
ipt_limit               2208  8
iptable_mangle          2720  0
ipt_LOG                 6976  8
ipt_MASQUERADE          3296  0
iptable_nat            22900  1 ipt_MASQUERADE
ipt_TOS                 2336  0
ipt_REJECT              5376  1
ip_conntrack_irc       71696  0
ip_conntrack_ftp       72688  0
ipt_state               1792  6
ip_conntrack           43064  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          2816  1
ip_tables              19456  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
binfmt_misc            11496  1
rfcomm                 38460  0
l2cap                  24740  5 rfcomm
bluetooth              48356  7 hci_usb,rfcomm,l2cap
speedstep_centrino      7636  1
cpufreq_powersave       1696  0
cpufreq_stats           5252  0
cpufreq_userspace       4316  1
cpufreq_ondemand        6044  0
cpufreq_conservative     6948  0
freq_table              4388  2 speedstep_centrino,cpufreq_stats
pcmcia                 26568  2
i915                   19488  1
drm                    64884  2 i915
tc1100_wmi              6692  0
video                  15748  0
battery                 9348  0
container               4384  0
i2c_acpi_ec             5472  0
i2c_core               21200  1 i2c_acpi_ec
button                  6480  0
pcc_acpi               11104  0
sony_acpi               5324  0
ac                      4708  0
dev_acpi               11108  0
hotkey                  9284  0
ipv6                  251232  10
af_packet              21768  2
ppp_generic            28628  0
slhc                    6944  1 ppp_generic
sg                     38080  0
sr_mod                 17028  1
cdrom                  39616  1 sr_mod
pcspkr                  3396  0
rtc                    12344  0
ipw2200               103880  0
firmware_class          9952  1 ipw2200
ieee80211              29380  1 ipw2200
ieee80211_crypt         5604  2 ipw2200,ieee80211
yenta_socket           25292  1
rsrc_nonstatic         13376  1 yenta_socket
pcmcia_core            49348  3 pcmcia,yenta_socket,rsrc_nonstatic
tpm_nsc                 6656  0
tpm                     9888  1 tpm_nsc
snd_intel8x0           33248  3
snd_ac97_codec         83932  1 snd_intel8x0
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24164  2 snd_pcm
snd                    54884  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9600  1 snd
snd_page_alloc         10600  2 snd_intel8x0,snd_pcm
pci_hotplug            27508  0
intel_agp              23164  1
agpgart                34792  3 drm,intel_agp
nls_iso8859_1           4000  1
nls_cp437               5664  1
vfat                   13440  1
fat                    52668  1 vfat
dm_mod                 57692  1
joydev                  9984  0
tsdev                   7776  0
evdev                   9664  1
psmouse                30116  0
mousedev               11616  1
parport_pc             35236  1
lp                     12292  0
parport                35912  2 parport_pc,lp
md                     45584  0
reiserfs              262320  1
thermal                13000  0
processor              22812  2 speedstep_centrino,thermal
fan                     4484  0
usbhid                 35264  0
tg3                    96772  0
ehci_hcd               34248  0
uhci_hcd               31184  0
usbcore               118044  5 hci_usb,usbhid,ehci_hcd,uhci_hcd
sd_mod                 19120  4
ide_generic             1376  0
ide_core              138772  1 ide_generic
ata_piix               10052  8
ahci                   11716  0
libata                 53764  2 ata_piix,ahci
scsi_mod              135688  5 sg,sr_mod,sd_mod,ahci,libata
unix                   26896  1115
vesafb                  7992  0
capability              4712  0
commoncap               6816  1 capability
vga16fb                12584  1
vgastate                9664  1 vga16fb
softcursor              2272  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3872  2 vesafb,vga16fb
cfbcopyarea             4608  2 vesafb,vga16fb
fbcon                  38496  72
tileblit                2368  1 fbcon
font                    8224  1 fbcon
bitblit                 5632  1 fbcon

```

---

### Post by Garyu on 2006-02-05
This guide seems like a good thing to make a wiki about, if there isn't one already. All of the things installed nice enough, but I have a couple of problems.

1) The default sound device after install is now BT Headset. Not good. It should be my speakers, with the option to change to Headset. Took me a while to figure out why the sound suddenly stopped working, and now I've changed it in the mixer preferences, but I haven't restarted the system so I don't know if it will stick. Should be in the HOWTO anyway.

2) I have a Jabra BT-110 headset. When I try to connect (and yes, it is in pairing mode) I get the reply from kbluetoothd "pairing not allowed"

In the terminal, where I started kbluetoothd it says:

```
Launched ok, pid = 9912
kio_bluetooth: *** Starting kio_bluetooth
kio_bluetooth: KioBluetooth::KioBluetooth()
kio_bluetooth: kio_bluetooth: get() was called! This is nonsense.
kio_bluetooth: kio_bluetooth::listdir() (/)
kio_bluetooth: sdp::doListBrowse()
kio_bluetooth: HciSocket::open()
kio_bluetooth: Using hci0 as default bluetooth device.
kio_bluetooth: HciSocket::open()
kio_bluetooth: Send HCI inquiry command..
kio_bluetooth: HciSocket::readStatus()
kio_bluetooth: Inquiry: hci packet received: eventCode=15 packetLength=4
kio_bluetooth: EVT_CMD_STATUS status=0 numPkts=1 cmdOpcode=1025
kio_bluetooth: HciSocket::readStatus(ogf=1,ocf=1,timeout=1000) = 0
kio_bluetooth: Inquiry started successfully
kbluetoothd: HCI-event: f
kbluetoothd: NeighbourMonitor: start of inquiry detected
kio_bluetooth: Inquiry: hci packet received: eventCode=1 packetLength=1
kbluetoothd: HCI-event: 1
kio_bluetooth: EVT_INQUIRY_COMPLETE status=\x00
kio_bluetooth: Inquiry ended successfully
kbluetoothd: NeighbourMonitor: end of inquiry detected
kbluetoothd: HciSocket::open()
kbluetoothd: NeighbourMonitor::processQueue
kio_bluetooth: kio_bluetooth: get() was called! This is nonsense.
kio_bluetooth: kio_bluetooth::listdir() (/)
kio_bluetooth: sdp::doListBrowse()
kio_bluetooth: HciSocket::open()
kio_bluetooth: HciSocket::open()
kio_bluetooth: Send HCI inquiry command..
kio_bluetooth: HciSocket::readStatus()
kio_bluetooth: Inquiry: hci packet received: eventCode=15 packetLength=4
kbluetoothd: HCI-event: f
kio_bluetooth: EVT_CMD_STATUS status=0 numPkts=1 cmdOpcode=1025
kio_bluetooth: HciSocket::readStatus(ogf=1,ocf=1,timeout=1000) = 0
kio_bluetooth: Inquiry started successfully
kbluetoothd: NeighbourMonitor: start of inquiry detected
kio_bluetooth: Inquiry: hci packet received: eventCode=2 packetLength=15
kbluetoothd: HCI-event: 2
kio_bluetooth: INQUIRY_RESULT: 00:07:A4:1E:0C:38
kbluetoothd: DeviceNameCache::slotInquiryResult
kio_sdp: *** Starting kio_sdp
kio_sdp: SdpProtocol::SdpProtocol()
kio_sdp: Looking for ServiceHandlers
kio_sdp: Allowed attributes:UntranslatedGenericName,X-KDE-FactoryName,X-SDPSERVICEHANDLER-mimeType,X-SDPSERVICEHANDLER-requiredUIDs,Type,Name,Comment,GenericName,Icon,Exec,Terminal,TerminalOptions,Path,ServiceTypes,AllowAsDefault,InitialPreference,Library,DesktopEntryPath,DesktopEntryName,Keywords,Categories
kio_sdp: ServiceUIDs:0x0003 & 0x1108 mimetype:bluetooth/headset-profile
kio_sdp: sdp: adding uuid 0x0003
kio_sdp: ->0x00000003:00001000:80000080:5f9b34fb
kio_sdp: sdp: adding uuid 0x1108
kio_sdp: ->0x00001108:00001000:80000080:5f9b34fb
kio_sdp: Allowed attributes:UntranslatedGenericName,X-KDE-FactoryName,X-SDPSERVICEHANDLER-mimeType,X-SDPSERVICEHANDLER-requiredUIDs,Type,Name,Comment,GenericName,Icon,Exec,Terminal,TerminalOptions,Path,ServiceTypes,AllowAsDefault,InitialPreference,Library,DesktopEntryPath,DesktopEntryName,Keywords,Categories
kio_sdp: ServiceUIDs:0x0003 & 0x111f mimetype:bluetooth/handsfree-profile
kio_sdp: sdp: adding uuid 0x0003
kio_sdp: ->0x00000003:00001000:80000080:5f9b34fb
kio_sdp: sdp: adding uuid 0x111f
kio_sdp: ->0x0000111f:00001000:80000080:5f9b34fb
kio_sdp: Allowed attributes:UntranslatedGenericName,X-KDE-FactoryName,X-SDPSERVICEHANDLER-mimeType,X-SDPSERVICEHANDLER-requiredUIDs,Type,Name,Comment,GenericName,Icon,Exec,Terminal,TerminalOptions,Path,ServiceTypes,AllowAsDefault,InitialPreference,Library,DesktopEntryPath,DesktopEntryName,Keywords,Categories
kio_sdp: ServiceUIDs:0x0003 & 0x1105 mimetype:bluetooth/obex-object-push-profilekio_sdp: sdp: adding uuid 0x0003
kio_sdp: ->0x00000003:00001000:80000080:5f9b34fb
kio_sdp: sdp: adding uuid 0x1105
kio_sdp: ->0x00001105:00001000:80000080:5f9b34fb
kio_sdp: Allowed attributes:UntranslatedGenericName,X-KDE-FactoryName,X-SDPSERVICEHANDLER-mimeType,X-SDPSERVICEHANDLER-requiredUIDs,Type,Name,Comment,GenericName,Icon,Exec,Terminal,TerminalOptions,Path,ServiceTypes,AllowAsDefault,InitialPreference,Library,DesktopEntryPath,DesktopEntryName,Keywords,Categories
kio_sdp: ServiceUIDs:0x0003 & 0x1104 mimetype:bluetooth/synchronization-profile
kio_sdp: sdp: adding uuid 0x0003
kio_sdp: ->0x00000003:00001000:80000080:5f9b34fb
kio_sdp: sdp: adding uuid 0x1104
kio_sdp: ->0x00001104:00001000:80000080:5f9b34fb
kio_sdp: Allowed attributes:UntranslatedGenericName,X-KDE-FactoryName,X-SDPSERVICEHANDLER-mimeType,X-SDPSERVICEHANDLER-requiredUIDs,Type,Name,Comment,GenericName,Icon,Exec,Terminal,TerminalOptions,Path,ServiceTypes,AllowAsDefault,InitialPreference,Library,DesktopEntryPath,DesktopEntryName,Keywords,Categories
kio_sdp: ServiceUIDs:0x0003 & 0x1111 mimetype:bluetooth/fax-profile
kio_sdp: sdp: adding uuid 0x0003
kio_sdp: ->0x00000003:00001000:80000080:5f9b34fb
kio_sdp: sdp: adding uuid 0x1111
kio_sdp: ->0x00001111:00001000:80000080:5f9b34fb
kio_sdp: Allowed attributes:UntranslatedGenericName,X-KDE-FactoryName,X-SDPSERVICEHANDLER-mimeType,X-SDPSERVICEHANDLER-requiredUIDs,Type,Name,Comment,GenericName,Icon,Exec,Terminal,TerminalOptions,Path,ServiceTypes,AllowAsDefault,InitialPreference,Library,DesktopEntryPath,DesktopEntryName,Keywords,Categories
kio_sdp: ServiceUIDs:0x0003 & 0x1101 mimetype:bluetooth/serial-port-profile
kio_sdp: sdp: adding uuid 0x0003
kio_sdp: ->0x00000003:00001000:80000080:5f9b34fb
kio_sdp: sdp: adding uuid 0x1101
kio_sdp: ->0x00001101:00001000:80000080:5f9b34fb
kio_sdp: Allowed attributes:UntranslatedGenericName,X-KDE-FactoryName,X-SDPSERVICEHANDLER-mimeType,X-SDPSERVICEHANDLER-requiredUIDs,Type,Name,Comment,GenericName,Icon,Exec,Terminal,TerminalOptions,Path,ServiceTypes,AllowAsDefault,InitialPreference,Library,DesktopEntryPath,DesktopEntryName,Keywords,Categories
kio_sdp: ServiceUIDs:0x0003 & 0x1103 mimetype:bluetooth/dun-profile
kio_sdp: sdp: adding uuid 0x0003
kio_sdp: ->0x00000003:00001000:80000080:5f9b34fb
kio_sdp: sdp: adding uuid 0x1103
kio_sdp: ->0x00001103:00001000:80000080:5f9b34fb
kio_sdp: Allowed attributes:UntranslatedGenericName,X-KDE-FactoryName,X-SDPSERVICEHANDLER-mimeType,X-SDPSERVICEHANDLER-requiredUIDs,Type,Name,Comment,GenericName,Icon,Exec,Terminal,TerminalOptions,Path,ServiceTypes,AllowAsDefault,InitialPreference,Library,DesktopEntryPath,DesktopEntryName,Keywords,Categories
kio_sdp: ServiceUIDs:0x0003 & 0x1106 mimetype:bluetooth/obex-ftp-profile
kio_sdp: sdp: adding uuid 0x0003
kio_sdp: ->0x00000003:00001000:80000080:5f9b34fb
kio_sdp: sdp: adding uuid 0x1106
kio_sdp: ->0x00001106:00001000:80000080:5f9b34fb
kio_sdp: done.
kio_sdp: kio_sdp::setHost(jabra bt110)
kio_sdp: kio_bluetooth: get() was called! This is nonsense.
kio_sdp: kio_sdp::listdir(jabra bt110) (/)
kio_sdp: sdp::findDeviceByName(jabra bt110)
kbluetoothd: resolveCachedDeviceName: jabra bt110=00:07:A4:1E:0C:38
kio_sdp: --[0x1002]6
kio_bluetooth: Inquiry: hci packet received: eventCode=1 packetLength=1
kio_bluetooth: EVT_INQUIRY_COMPLETE status=\x00
kio_bluetooth: Inquiry ended successfully
kio_bluetooth: Slave was killed. Skipping name update.
kio_bluetooth: *** kio_bluetooth Done
kio_bluetooth: KioBluetooth::~KioBluetooth()
kbluetoothd: HCI-event: 1
kbluetoothd: NeighbourMonitor: end of inquiry detected
kbluetoothd: NeighbourMonitor: new device 00:07:A4:1E:0C:38
kbluetoothd: HciSocket::open()
kbluetoothd: NeighbourMonitor: neighbours changed
kbluetoothd: TrayIcon::slotMruMenuUpdate
kbluetoothd: mruMenuUpdate neighbours=1
kbluetoothd: NeighbourMonitor::processQueue
kbluetoothd: HCI-event: f
kbluetoothd: slotConnectionStateChanged
kbluetoothd: HciSocket::open()
kbluetoothd: HciSocket::open()
kbluetoothd: Checking state00:07:A4:1E:0C:38 2
kbluetoothd: connections: 1
kbluetoothd: slotConnectionStateChanged
kbluetoothd: HciSocket::open()
kbluetoothd: HciSocket::open()
kbluetoothd: Checking state00:07:A4:1E:0C:38 2
kbluetoothd: connections: 1
kbluetoothd: HCI-event: e
kbluetoothd: HCI-event: 3
kbluetoothd: HCI event 'connection complete' status:3 ltype:1
kbluetoothd: TrayIcon::slotConnectionComplete()
kio_sdp: WARNING: sdp_connect(00:07:A4:1E:0C:38) failed
kio_sdp: Number of services: 0
kbluetoothd: slotConnectionStateChanged
kbluetoothd: HciSocket::open()
kbluetoothd: HciSocket::open()
kbluetoothd: Checking state00:07:A4:1E:0C:38 2
kbluetoothd: connections: 1
kbluetoothd: slotConnectionStateChanged
kbluetoothd: HciSocket::open()
kbluetoothd: HciSocket::open()
kbluetoothd: Checking state00:07:A4:1E:0C:38 2
kbluetoothd: connections: 1
kbluetoothd: HCI-event: f
kbluetoothd: slotConnectionStateChanged
kbluetoothd: HciSocket::open()
kbluetoothd: HciSocket::open()
kbluetoothd: Checking state00:07:A4:1E:0C:38 2
kbluetoothd: connections: 1
kbluetoothd: slotConnectionStateChanged
kbluetoothd: HciSocket::open()
kbluetoothd: HciSocket::open()
kbluetoothd: Checking state00:07:A4:1E:0C:38 2
kbluetoothd: connections: 1
QFile::open: No file name specified
kbluetoothd: HCI-event: e
kbluetoothd: HCI-event: 3
kbluetoothd: HCI event 'connection complete' status:3 ltype:1
kbluetoothd: TrayIcon::slotConnectionComplete()
kio_sdp: WARNING: sdp_connect(00:07:A4:1E:0C:38) failed
kbluetoothd: slotConnectionStateChanged
kbluetoothd: HciSocket::open()
kbluetoothd: connections: 0
kbluetoothd: slotConnectionStateChanged
kbluetoothd: HciSocket::open()
kbluetoothd: connections: 0
kbluetoothd: TrayIcon::slotMruMenuUpdate
kbluetoothd: mruMenuUpdate neighbours=1
QFile::open: No file name specified

```

---

### Post by reto on 2006-02-05
great! suspend now works with btsco 0.41, just have to rmmod and modprobe in /etc/acpi/sleep.sh resume.sh

---

### Post by MarioFrick on 2006-02-11
[QUOTE=joker667]9. Click on your Device (sometimes only the MAC-Adress shows up), konqui will list all supported Services, and start using the Service (for my Mobile, K700i its obex File Transfer, then I can browse my Mobile like a Disk Drive, copying what I want). Previous to that, my phone wants to pair with my PC, aksing for a PIN. Just guess one (1234), **after that a popup on the PC should occour, asking for the same PIN**.[/QUOTE]
Here is my problem, the PC doesn't pop up asking for the PIN, and the phone asks me again for the PIN until it goes in timeout...

Any ideas?

---

### Post by Garyu on 2006-02-11
[http://www.ubuntuforums.org/showthread.php?t=94713&page=1&pp=20](http://www.ubuntuforums.org/showthread.php?t=94713&page=1&pp=20)

I found this thread about using gnome bluetooth tools. They work flawlessly, even if they are slower than the KDE things.

Using my Jabra BT110 headset still does not work though. :(

---

### Post by angkor on 2006-02-18
[QUOTE=Garyu]Using my Jabra BT110 headset still does not work though. :([/QUOTE]

Try changing the settings in /etc/bluetooth/hcid.conf

Changing the security to 'auto' worked for me. Also check to see where bluez-pin is located on your system and hcid.conf is pointing to the right file.

Also don't forget to restart the bluez-utils after making changes.

sudo /etc/init.d/bluez-utils restart

---

### Post by Garyu on 2006-02-18
[QUOTE=angkor]Changing the security to 'auto' worked for me. Also check to see where bluez-pin is located on your system and hcid.conf is pointing to the right file.[/QUOTE]

Angkor, you're the man. Actually, I've been poking around a lot tonight, following some strange howto's for making bluetooth headset work from terminal command line, and maybe that contributed, but until I set security to "auto" (as it was from the beginning I might add) I got a LMP response timeout error message. BUT now it works! Halleluja, or whatever. :cool:

---

### Post by angkor on 2006-02-18
Cool, congrats! 

I just got it to work myself today (dongle troubles)...No more twisting wires 'round my neck when I'm on skype :) \\:D/

---

### Post by damien82 on 2006-03-04
this is driving me nuts...no problem with pairing my headset, no issues with that what so ever...BUT! i can't hear a thing from the headset except a beep or two whenever i try to press play in xmms...

If anyone have a soloution to this, please post here..or send me a pm..just help me

---

### Post by bbking78 on 2006-03-08
Hi!

I haven't had that much luck with this topic...I've come this far:
I built the btsco package successfully:

```
aquamaniac:/usr/src/btsco-0.41 # ls
.             alsa-plugins    btsco2         config.sub    .libs
..            AUTHORS         btsco2.c       configure     libtool
a2dp.h        autom4te.cache  btsco2.o       configure.in  ltmain.sh
a2play        avdtp           btsco.c        contrib       Makefile
a2play.c      avrcp.h         btsco.o        COPYING       Makefile.am
a2play.o      avrecv          ChangeLog      COPYING.LIB   Makefile.in
a2recv        avrecv.c        config.guess   depcomp       missing
a2recv.c      avrecv.o        config.h       .deps         NEWS
a2recv.o      bootstrap       config.h.in    INSTALL       README
acinclude.m4  bt              config.log     install-sh    sbc
aclocal.m4    btsco           config.status  kernel        stamp-h1

```
when I execute make install and try to load the module with
"sudo modprobe btsco" as suggested here I get

FATAL: Module btsco not found.

so where does this module come from? where can I find it?
at least I discovered that when I do

/usr/local/bin/btsco -v 00:0B:2E:20:EC:BE

at least I get

Error: control open (hw:1): No such device
Error: Can't find device. Bail

should the headset be in pairing mode when I issue the above command?

would be really nice to be able to use the headset with skype! Please, give a hint, where to search further...

cheers,
bbking

---

### Post by GeneralZod on 2006-03-17
Bump for thanks - works great with my m2500 under Dapper, although the kernel module is now called snd-bt-sco.  And btsco is now in the Dapper repositories, so I didn't have to compile from source! \\:D/

Edit:

Bleh - using this stopped hibernate from working (at all!), so in the end I did have to compile from source, as a fix was added to CVS a few days ago - good timing on my behalf!  Upon resume, though, the only way I found to get sound working again was to pull out my bluetooth dongle and put it back in again, which is not exactly ideal - still, apart from that, it's all been quite smooth!

---

### Post by anders.ostling on 2006-03-28
Hi
I have a Sony Ericsson HBH-600 headset, and the setup seems to work. I have managed to pair it successfully, I run btsco which tells me that the volume is changed (using alsa mixer with headset as device). I can also see this

anos@zoolog:~$ cat /proc/asound/cards
0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                     Intel 82801DB-ICH4 with STAC9750,51 at 0xf4fff800, irq 7
1 [Headset        ]: Bluetooth SCO - BT Headset
                     BT Headset 1

anos@zoolog:~$ btsco -v 00:0F:DE:AE:8D:71
btsco v0.4c
Device is 1:0
Voice setting: 0x0060
RFCOMM channel 1 connected
recieved AT*ECBP=?
recieved AT+CLIP=1
recieved AT+CSCS="UTF-8"
recieved AT+CLAN?
speaker volume: 14 mic volume: 1
i/o needed: connecting sco...
connected SCO channel
Done setting sco fd
recieved AT+VGS=15
Sending up speaker change 15
speaker volume: 15 mic volume: 1
...
speaker volume: 11 mic volume: 7
speaker volume: 11 mic volume: 8
speaker volume: 12 mic volume: 8
speaker volume: 11 mic volume: 8
speaker volume: 10 mic volume: 8
speaker volume: 9 mic volume: 8
speaker volume: 10 mic volume: 8
speaker volume: 10 mic volume: 

The issue is that when I send a file with this command 

aplay -B 1000000 -D plughw:Headset /usr/share/sounds/info.wav

I recieve a short beep in the headset. Then I have to press ctrlc to leave the aplay command. After ctrlc, I get a new beep before returning to the command prompt. The same sound for all wav files. Then I tried to use XMMS to play an mp3 through the headset. I configured the output plugin to use Headset. When I click on Play, again a short beep and nothing else.

Any hints on what my problem can be? I would like to use the headset for skype, but without sound to the headset, there is not much idea to play with the microphone yet.

Anders

---

### Post by phetre on 2006-03-31
Thanks, Joker667!  But how can this well-written, effective guide be your *only* post in five months of membership?  Do you have an alter ego?  What a mysterious figure you cut.

I used this in Breezy to get OBEX with my Motorola e815, and everything was fine.  When I run kbluetoothd in Dapper it finds my bluetooth adaptor, but when I click the panel icon to run Konqueror, I get the following message:

**Malformed URL bluetooth:/**

I can't find anything on the web about this.  Am I the only one whose Konqueror has this problem?

---

### Post by phetre on 2006-04-03
Aha, I missed this Debian bug report: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=359153]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=359153").  Seems it might not be a problem if you have your device set up already.

---

### Post by core24 on 2006-04-25
I logged a defect, #41237 at [https://launchpad.net/distros/ubuntu/+source/kdebluetooth/+bug/41237](https://launchpad.net/distros/ubuntu/+source/kdebluetooth/+bug/41237)

Can't wait to get an updated pkg...

---

### Post by Chris_G on 2006-05-04
Not sure if the right place for this - apoligies for the novice approach - however your thread seems to tie in with what I'm looking for.

I use a Sony Ericsson P910i and was wondering if it is possible to link it to my computer as a bluetooth headset - so that when I'm using Skype on my computer I can just talk through my mobile...?

When I try link my computer and phone using the headset link - the computer tells me that the phone doesn't have that functionality - however it will link as an audio gateway and work in reverse - i.e. calls through my phone come out of my computer sound system...

So the questions is...can I do this or do I need to get a seperate bluetooth headset?

Thanks 
Chris

---

### Post by Hellfire73 on 2006-06-11
Hi guys....

i'am a newbie on the Kubuntu distribution..so i will be very grateful to everyone will help me to solve this boring problem.

i'am trying since a week to use my Headset Motorola HS815 and his bluetooth dongle without any positive results.

it's a very frustrating thing to see that threre isn't any standard procedure but it's all randomic.  The same BTSCO bluetooth procedure works for someone but it doesn't works for others ! WHHYYYYYYY????

i read other forums , i read your forums but i've the same trouble trying to paring this ****** device :

i write on colsole :

btsco -v 00:0B:2E:67:49:89

the result is :

btsco v0.42
Device is 0:0
Error: Failed to connect to SDP server: Permission denied
Assuming channel 2

Voice setting: 0x0060
Can't connect RFCOMM channel: Permission denied

i don't see any request of PIN !!!

i tried all that i read on this forum about hcid.conf files...
i tried to make a link to the pin file using the name 'link_key'

i started , stopped, restarted ,( i don't remember how many times)  the bluez-utils daemon....

the problem is always the same The Pairing!!!

Someone can help me, PLEAASSEEEEEeEEeeeEEeEEEeEEeEEEe?

---

### Post by niteblind on 2006-06-24
okay i have changed the security settings and now it seems that problems has gone away. Although every time i turn off the headset i have to rescan manully before it gets picked back up the next time

Also the headset does not think it has paired as it stays in discovery mode. Wierd thing is it is listed now in the bluetooth: directory so this should mean that it works.

So following the link you probided i enter in the console i go to step 2 and get this

niteblind@Wolverine:~$ sudo modprobe btsco
FATAL: Module btsco not found.
niteblind@Wolverine:~$               

I tried searching for btsco on the repositories all i found was bluez-btsco so i installed this and i still get the same error.

Any ideas where i can find the btsco module and how i install it?

niteblind

---

### Post by reto on 2006-06-24
In dapper the module ssems to be called snd_bt_sco, try:
> sudo modprobe snd_bt_sco

---

### Post by -Chi.0 on 2006-06-28
I keep getting this after running [COLOR="Magenta"]btsco -v <mac address>[/COLOR] ](*,) 

```
Error: hwdep next device (hw:0): Operation not permitted
Error: hwdep next device (hw:1): Operation not permitted
Error: control open (hw:2): No such device
Error: Can't find device. Bail
```

Can any one point me in the right direction please?

[COLOR="Orange"]Note: (I'm running Dapper Drake 6.06 & using a Belkin usb 2.0 adapter)[/COLOR]

---

### Post by rbrugman on 2006-07-08
I'm having the same problem of my device not being found.  It actually appears on the list of bluetooth devices in Konquerer, but it's icon says DVD and when I click on it, it asks what to open it with.

I'm using Dapper 6.06 (Kubuntu) with a D-Link DBT-120 adapter and a Motorola H300 headset for my Sony phone.  The phone works fine, but the headset won't pair.

---

### Post by adam s on 2006-07-11
Hi this is a very useful thread.
I am OK up to the point below....

> **joker667 said:**
> 
PART 2: Using a Bluetooth Headset - tricky, but also easy when knowing how ;)

1. Load Kernel Module for btsco: "sudo modprobe btsco", checking "dmesg" if it runs. To load it permanently add it to /etc/modules, just write "btsco" at the end of the File
2. Install the following missing (at least on my system) packages needed by the btsco Userspace driver. Easy, because you have apt-get or synaptic: 
	gcc
	gcc-4.0
	altgcc 
	libc6-dev
	linux-kernel-headers
	libasound2-dev
	libao-dev
	libbluetooth1-dev
3. Download latest btsco from [http://sourceforge.net/projects/bluetooth-alsa/](http://sourceforge.net/projects/bluetooth-alsa/), unzip to Desktop perhaps
4. Time for the shell! ;)
	cd btsco-0.4
	./configure
	make
	sudo make install




First of all, When I run 'sudo modprobe btsco',  I get the error 

FATAL: Module btsco not found.


I tried ignoring this to try configuring the latest btsco (point 2) and came up with the configure error :

checking bluetooth/bluetooth.h usability... no
checking bluetooth/bluetooth.h presence... no
checking for bluetooth/bluetooth.h... no
configure: error: Bluetooth header files not found

What do I need to do to continue with getting my bluetooth headset working?

Thanks in advance,

Adam.

---

### Post by lifeempowered.com on 2006-07-17
Thank you all for your contributions!  This is SWEET.  Got my Plantronics 320 working now with my Kensington USB Bluetooth device! :) very cool

---

### Post by larlin on 2006-07-24
First thanks for this howto...

I have followed this howto: [https://help.ubuntu.com/community/BluetoothSkype](https://help.ubuntu.com/community/BluetoothSkype)
That is based on the howto in this thread but sems updated for Dapper Drake..

I'm trying to get my Jabra BT620s headset to work with ubunthu I got a jabra A320s USB bluetooth dongle...

In that howto I get to "Pair the headset with PC (as above with the Mobile)" part kBluetoothD finds both the dongle and the headset and it is in the bluetooth place in konquer... But when I klick on the headset in konquer it dosen't ask for pin instead it asks open 'sdp://jabra bt260s/'? I got to choose between Save As.. Open with.. and Cancel so I try open with.

This makes it open the avaiable bluetooth services in a new konqueror window then I try klicking the Stereo headset service same open question again but a slightly diffrent url I take open with again and get:

Could not stat
sdp://[00:13:17:70:2b:28]/params?name=jabra%20bt620s.
Unknown device

There is obvius something wrong I have changed in the /etc/bluetooth/hcid.conf to this:
        security user;
        pairing multi;
        pin_helper /usr/bin/bluez-pin;

I'm new to ubunthu and have some experience with linux before but very little so please keep it simple =)

Any ideas what to do?

Thanks for reading this far =)

larlin

---

### Post by ShiftyPowers on 2006-07-24
this works fairly well with my BT250 using the last Howto mentioned.  However, it's fairly static and not that great of an audio quality.  Anyone know how to improve it?

---

### Post by larlin on 2006-07-25
I have continued trying and haven't gotten any where...

I have changed the dongle as [this]("http://ubuntuforums.org/showpost.php?p=304573&postcount=4") howto says that "As output you must get a rowentry like “SCO mapping: HCI”. Without it you can stop, you need some different dongle." I changed dongle to one where I get "SCO mapping: HCI"...

In the same howto he conects using the terminal so I tested that too and got this as printout:

```

$ btsco -v 00:13:17:70:2B:2B
btsco v0.4c
Device is 1:0
Error: Failed to connect to SDP server: Host is down
Assuming channel 2

Voice setting: 0x0060
Can't connect RFCOMM channel: Host is down
```

The dongle change didn't do much as far as I can see, I have tested alot of combinations in the hcid.conf, plz any suggestions would be much appriated!

larlin

---

### Post by janx on 2006-07-25
1) This seems to be correct:
> **reto said:**
> In dapper the module ssems to be called snd_bt_sco, try:
(and not: btsco)

2) Unfortunately, after fixing this it seems I can't see the device anymore...
gnome-bluetooth-manager gives:
gobject.GError: Can't get device id of hci0
and:
```
# hcitool scan
Device is not available: No such device

```
???

---

### Post by gingermark on 2006-07-28
Thanks so much for part 1.

I'm a Kubuntu user, and I figured out how to do it a while ago (cobbling together bits of info from all over the place). After a reinstall, I couldn't remember how to do it again!

Thankyou again.

---

### Post by whakojacko on 2006-07-29
this thread is VERY helpful. I got the obex connection to my phone (finally) working. However, my phone uses various different subdirectories and whenever I select them konqueror prompts me what program I would like to open the file with. 
In addition, whenever I go into the url window and manually type in the name of a folder, say /audio/, it gives a dropdown list of all the files in the folder
What is with this behavior?
[img]http://img84.imageshack.us/img84/6223/ss1bb7.jpg[/img]
[img]http://img101.imageshack.us/img101/3638/ss2ir1.jpg[/img]

---

### Post by sirlancelot on 2006-08-11
Got this to work with my Motorola H500 as well as my T-Mobile MDA. Took a while, turns out the **dapper** command is:```
sudo modprobe snd-bt-scod
```Took some other tweaking to get it to work but I don't remember what I did.

Quick Note: When I tried to pair two devices with my pc, it crashed the daemon, be warned.

---

### Post by ickyb0d on 2006-08-17
> **whakojacko said:**
> this thread is VERY helpful. I got the obex connection to my phone (finally) working. However, my phone uses various different subdirectories and whenever I select them konqueror prompts me what program I would like to open the file with. 
In addition, whenever I go into the url window and manually type in the name of a folder, say /audio/, it gives a dropdown list of all the files in the folder
What is with this behavior?


man... i'm right there with ya.  When i click on a folder as whacko has shown in his helpful pics above... it prompts me for a program.  if i specify konquerer it prompts me again... or if i specify obex file transfer it can't find the device.

here's the crazy thing.  i CAN transfer files to my phone (Motorola v815... hacked for OBEX).  If i drag a file onto one of the folders, konqueror magically opens up the folder, and i can view all of the files in the folder.  And if i release the file, it drops it right in!  awesome!  the bad thing is... since i can't open these folders without dragging a file over them.  i can't get any files off (pictures... ect.).  

Other than that i went through the normal tweaks everyone has gone through.

however, i followed [this]("https://help.ubuntu.com/community/BluetoothDialup") wiki link posted to actually pair with the device properly.  i was unable to pair directly through kbluetoothd.


so all in all... works great! but i just wish i could just use konqueror/kbluetoothd to actually browse the device, instead of having to do this drag-open folder-drop mojo i described above.  any thoughts?

---

### Post by WoodLark on 2006-10-04
I have tried all of the tricks in this thread and others to install my Bluetooth headset (Jabra BT250) and Dongle (Creative Labs). The results have been inconsistent in multiple attempts over several days. Sometimes the headset is detected, sometimes it is not; sometimes pairing works, but most often it does not. Even when pairing apparently worked, no sound comes from the headset. Sometimes, there are error messages, sometimes the commands appear to just hang, and other times they appear to work (but apparently do not).

I am not a novice computer user. I am a retired programmer and certified HP-UX system administrator, and I usually can get things to work, but this time, I have to admit I am licked!

Just to verify that my dongle and headset are not defective, I installed them on another computer under Windows XP. Everything went completely smoothly, including using the headset with Skype. I love Linux and hate to see this, because it is situations like this that are going to keep the public at large using Windows rather than Linux.](*,)

---

### Post by Bizmac on 2006-10-14
Follow the wiki there:[https://help.ubuntu.com/community/BluetoothSkype](https://help.ubuntu.com/community/BluetoothSkype)
works Kubuntu/Ubuntu special section for Dapper (important you download a btso package and you don't compile it as mention at the beginning of this thread)

For those having trouble with pairing just follow this before running btso -v

Run the following to find your mac-adress:
hcitool scan

Run the following, replacing your-phone-mac-address with the proper data:
sudo hcitool cc your-phone-mac-address

Run the following, replacing your-phone-mac-address with the proper data:
sudo hcitool auth your-phone-mac-address

Not an expert but takes time to find the good info: This works for me with my Jabra headset...Viva Kubuntu!

---

### Post by d@vide on 2006-10-30
We are triing to use a bluetooth headset with skype ... all we have the same problem on btsco (with or without parameter):

Error: btsco open (1-0): No such device or address 



Anyone can help us and understand the error or how to see what is the problem?

see the whole forum at

[http://www.slax.org/forum/viewtopic.php?t=14414](http://www.slax.org/forum/viewtopic.php?t=14414)

---

### Post by trojanlinux on 2006-10-31
does this

[https://help.ubuntu.com/community/BluetoothSkype](https://help.ubuntu.com/community/BluetoothSkype)

also apply to 6.10???

---

### Post by Peepsalot on 2006-11-10
I'm trying to get file transfers working(the first part of the howto) in Edgy, and having some difficulty.  Can someone please help me with these issues?

1) My /etc/init.d/hcid.conf did not have a line with pin_helper on it, so I went ahead an added it.  Did I add it properly(see hcid.conf below), and should I have commented the line with the default passkey on it?

2) My bluez-pin was in /usr/bin , not /usr (was this a typo in the howto?)

3) /etc/init.d/bluez-utils does not exist on my system.  However, there is an /etc/init.d/bluetooth .  Are these the same thing?

So far, I have kbluetoothd running, but it doesn't seem to recognize my phone.  I enabled bt on the phone, and tried to connect from phone to computer.  The phone asks for a pin, then tries to connect, but no dialog ever appears on the computer, so it fails in a few seconds.  Also, I' 

Also, when kbluetoothd is started, I get this warning message:
> To use the kbtobexsrv service, some other devices might require a modified class number for your bluetooth adapter in /etc/bluetooth/hcid.conf. 
Currently the class is set to 0x0. We suggest you change this to something like 0x100000 instead and restart BlueZ's hcid. The service will be activated anyway.
But in my hcid.conf it looks like it is set to 0x3e0100

hcid.conf:
```

#
# HCI daemon configuration file.
#

# HCId options
options {
        # Automatically initialize new devices
        autoinit yes;

        # Security Manager mode
        #   none - Security manager disabled
        #   auto - Use local PIN for incoming connections
        #   user - Always ask user for a PIN
        #
        security user;

        # Pairing mode
        #   none  - Pairing disabled
        #   multi - Allow pairing with already paired devices
        #   once  - Pair once and deny successive attempts
        pairing multi;

        # Default PIN code for incoming connections
        # passkey "1234";

        pin_helper "/usr/bin/bluez-pin";
}

# Default settings for HCI devices
device {
        # Local device name
        #   %d - device id
        #   %h - host name
        name "%h-%d";

        # Local device class
        class 0x3e0100;

        # Default packet type
        #pkt_type DH1,DM1,HV1;

        # Inquiry and Page scan
        iscan enable; pscan enable;
        discovto 0;

        # Default link mode
        #   none   - no specific policy 
        #   accept - always accept incoming connections
        #   master - become master on incoming connections,
        #            deny role switch on outgoing connections
        lm accept;

        # Default link policy
        #   none    - no specific policy
        #   rswitch - allow role switch
        #   hold    - allow hold mode
        #   sniff   - allow sniff mode
        #   park    - allow park mode
        lp rswitch,hold,sniff,park;
}

```

---

### Post by Peepsalot on 2006-11-10
Ok somehow I got to see my phone listed as a bluetooth device in konqueror.     So I try to connect in konqueror and my phone asks for the code, i enter it, and one and it asks again, about 4 or 5 times, then gives up.  I never get a chance to enter the pin on my computer.

Something is wrong about my passkey agent setup.  I read in another thread to look in /var/log/syslog and I find this:```

Nov 10 01:03:20 peeps-desktop hcid[6386]: pin_code_request (sba=00:02:72:CD:BA:70, dba=00:12:56:7D:E8:7A)
Nov 10 01:03:20 peeps-desktop hcid[6386]: call_passkey_agent(): no agent registered

```
But I don't know what I'm supposed to do about it.

---

### Post by Paul_M on 2006-11-19
On following the guide to get my bluetooth headset (O2 Karuna) working with my USB bluetooth dongle plugged into my laptop to use it with skype, everything seems to work well, however, after the audio is closed at the end of the call (tested with echo123), it won't work again until after a restart of btsco and unplugging the dongle and then plugging it back in again, dongle is based on an SiW chip.

Any ideas as to why that may be happening? it also occured when I tested the headset with XMMS to comfirm audio was working

---

### Post by rockprincess on 2006-12-27
> **Bizmac said:**
> Follow the wiki there:[https://help.ubuntu.com/community/BluetoothSkype](https://help.ubuntu.com/community/BluetoothSkype)
works Kubuntu/Ubuntu special section for Dapper (important you download a btso package and you don't compile it as mention at the beginning of this thread)

For those having trouble with pairing just follow this before running btso -v

Run the following to find your mac-adress:
hcitool scan

Run the following, replacing your-phone-mac-address with the proper data:
sudo hcitool cc your-phone-mac-address

Run the following, replacing your-phone-mac-address with the proper data:
sudo hcitool auth your-phone-mac-address

Not an expert but takes time to find the good info: This works for me with my Jabra headset...Viva Kubuntu!

followed your advice and after this i got that:

```
sudo hcitool auth 00:16:XX:XX:XX:XX
HCI authentication request failed: Input/output error

```

when will Pairing get fixed on Kubuntu Edgy Eft?! :-k

---

### Post by nrune on 2007-01-01
Okay I give up, Help please.  Everthing up to
```
- a popup should request the PIN for the Headset from you (mostly "0000" or "1234")
```

works, I never see a pop up and 
```
nrune@nrune:~$ btsco -v -r 00:08:1B:XX:XX:XX
btsco v0.42
Device is 1:0
Error: Failed to connect to SDP server: Permission denied
Assuming channel 2

Voice setting: 0x0060
QFile::open: No file name specified
Can't connect RFCOMM channel: Permission denied

```

Any way can't get this paring problem solved?  I never see the "popup" to pair the device. 

Running Edgy

---

### Post by rockprincess on 2007-01-02
feisty fawn is "only" 4 months away, anyway! ;)

---

### Post by dief-eh? on 2007-01-05
> **nrune said:**
> Okay I give up, Help please.  Everthing up to
```
- a popup should request the PIN for the Headset from you (mostly "0000" or "1234")
```

works, I never see a pop up and 
```
nrune@nrune:~$ btsco -v -r 00:08:1B:XX:XX:XX
btsco v0.42
Device is 1:0
Error: Failed to connect to SDP server: Permission denied
Assuming channel 2

Voice setting: 0x0060
QFile::open: No file name specified
Can't connect RFCOMM channel: Permission denied

```

Any way can't get this paring problem solved?  I never see the "popup" to pair the device. 

Running Edgy

I'm also getting to this point, and not getting any popup. Have you managed to get this working?

---

### Post by rockprincess on 2007-01-06
pairing in edgy eft seems disabled or at least inactive....that's why you're not getting any popups asking for pins.....

hopefully this will be fixed in feisty fawn!

---

### Post by Zomp on 2007-01-06
I give up. I have been trying to work off my *Logitech Wireless Headphones for PC* for three days, but it hasn't worked yet. ](*,) 
I acted upon instructions on this and on the other pages, but I probably hashered st.
- When I pair the headphones with the dongle, the only thing I can do is switch and pause songs, but they are still playing from pc speakers. There is no sound in the headphones. (It is same from the beginning.)
- **lsusb** finds the right usb with dongle.
- **hcitool scan** finds nothing. KBluetoothD shows *No working Bluetooth adapter found*.
I couldn't do some of the following steps, because I didn't have the MAC Adress, so there should be more problems.
Can anybody help me, please?

---

### Post by Peepsalot on 2007-01-06
Has anyone gotten a linksys CIT200 Skype phone to work in linux?

---

### Post by dief-eh? on 2007-01-06
> **rockprincess said:**
> pairing in edgy eft seems disabled or at least inactive....that's why you're not getting any popups asking for pins.....

hopefully this will be fixed in feisty fawn!

Thanks for your reply. I thought that lifeempowered.com's message, back in July, about getting his Plantronics headset/Kensington dongle to work meant I could too! 

But I certainly hadn't seen any documented references to the Edgy/Fawn divide you mention a couple of times in this thread into account. lifempowered's message doesn't specify his version, but back in July would have been either Dapper or early Edgy's, n'est-ce pas?  Where can I find the info you're referring to?

A recent thread in bluez-users suggested installing bluez-passkey-gnome and jacking around with the hcid.conf file, which I've done, and I prefer to believe I'm getting closer (see most-recent error messages, below) to a working headset :c), but gaping holes in my understanding of just what the hell I'm doing remain. 

This morning, for instance, I noticed the dongle light was on, i.e. steady, rather than flashing 2x every other second, which is its normal state. It's plugged in to one of the two USB ports on my MS Natural keyboard, and shows up in lsusb listings. But it's never before displayed a steady light, as far as I've seen. And it's back to flashing again. Curious.

I hope this thread can help us collectively.

recent errror messages:

>> btsco 00:03:89:53:EC:7F 2
Can't connect RFCOMM channel: Device or resource busy
>>  btsco 00:03:89:53:EC:7F 2
Can't connect RFCOMM channel: Host is down
>>  btsco 00:03:89:53:EC:7F 2
Can't connect RFCOMM channel: Connection refused	## what's it going to be? 
## how can I connect to RFCOMM channel?
>> btsco -v  00:03:89:53:EC:7F
btsco v0.42
Device is 1:0
Voice setting: 0x0060
Can't connect RFCOMM channel: Connection refused

>> sdptool search --bdaddr 00:03:89:53:EC:7F 0x1108
Class 0x1108
Searching for 0x1108 on 00:03:89:53:EC:7F ...
Service Name: HS-Audio
Service RecHandle: 0x10000
Service Class ID List:
  "Headset" (0x1108)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Headset" (0x1108)
    Version: 0x0100
>> hciconfig -a
hci0:   Type: USB
        BD Address: 00:0C:76:47:81:CC ACL MTU: 192:8 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN
        RX bytes:18266171 acl:684937 sco:0 events:600808 errors:0
        TX bytes:10804242 acl:600618 sco:0 commands:99 errors:0
        Features: 0xff 0xff 0x0f 0x00 0x00 0x00 0x00 0x00
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
        Link policy: RSWITCH HOLD SNIFF PARK
        Link mode: SLAVE ACCEPT
        Name: 'workhorse2-0'
        Class: 0x3e0100
        Service Classes: Networking, Rendering, Capturing
        Device Class: Computer, Uncategorized
        HCI Ver: 1.1 (0x1) HCI Rev: 0x20d LMP Ver: 1.1 (0x1) LMP Subver: 0x20d
        Manufacturer: Cambridge Silicon Radio (10)

---

### Post by Zomp on 2007-01-07
Now, I am sure, that I didn't overlooked st. I tried to get work my headphones many times again, but I haven't succeeded yet. Everything seems to be OK except the **hcitool scan** to get the MAC adress
```
zomp@zomp-desktop:~$ hcitool scan
Device is not available: No such device
```
Can anybody help me, please?

---

### Post by dief-eh? on 2007-01-07
> **Zomp said:**
> Now, I am sure, that I didn't overlooked st. I tried to get work my headphones many times again, but I haven't succeeded yet. Everything seems to be OK except the **hcitool scan** to get the MAC adress
```
zomp@zomp-desktop:~$ hcitool scan
Device is not available: No such device
```
Can anybody help me, please?

Hello
I am not an expert, nor do I play one on TV!
Try 'sudo hcitool scan', while putting your device in pairing mode. Here's what happens for mine:
>> sudo hcitool scan
Password:
Scanning ...                          ## *without* pairing mode
>> sudo hcitool scan
Scanning ...                          ## *with* pairing
        00:03:89:53:EC:7F       320 Plantronics

HTH.

---

### Post by Zomp on 2007-01-08
Many thanks, it still doesn't work, I give up.

---

### Post by brazzmonkey on 2007-01-15
basically this works with acer bluetooth phones (the ones bundled with several acer laptops - note that their pincode is 4444). i have a question though : is this normal behaviour to need to manually run "btsco -v ....." every time i want to use the phone ? this is kind of boring because the bluetooth connection is terminated when skype call ends. i'd be glad to find workaround to this issue :
- the good one would be automatic bluetooth connection on request (say, when starting a call or accepting a call) ;
- the not-so-good one would be a permanent bluetooth connection.

di you guys know of a way to reach any of these ?

thx

---

### Post by rockprincess on 2007-01-24
ohhh i think i've fixed it last night...at least i got my phone and my headset working..

[SIZE="4"]**this is for all Kubuntu Users who are experiencing problems with pairing their bluetooth device:**[/SIZE]

[LIST]
[*]switch on your bluetooth device (mobile phone, headset, etc..)
[*]go into the konsole and type: passkey-agent --default /usr/bin/bluez-pin
[*]and then enter your PIN
[/LIST]

that's about it really...but it must go easier....this is a dirty solution because i can't be bothered starting this pairing assistant everytime i wanna connect to my headset or mobile phone.
does anyone know how to automatize this process?

i've tried following these solutions :
[http://docs.kde.org/development/en/extragear-pim/kdebluetooth/concepts.html](http://docs.kde.org/development/en/extragear-pim/kdebluetooth/concepts.html)
[http://docs.kde.org/development/en/extragear-pim/kdebluetooth/installation.setup.html](http://docs.kde.org/development/en/extragear-pim/kdebluetooth/installation.setup.html)

but in my opinion these aren't much of help! kdebluetooth (or kdebluetoothd) needs a massive revamp, hopefully for the next kde version, or for kde4, because they suck!

and for normal users (like me) it's too complicated to get into that stuff, no I'm not being lazy nor I'm making it too easy for myself.
but the simple fact is that I'd have given up already if I hadn't bought my bluetooth devices.

this should go a lot easier!

you can mark this topic as solved!:KS

---

### Post by Zomp on 2007-01-25
I have also solved my problem, the problem was that I didn't expect that the bluetooth dongle behaves like a sound card and the computer needs to know nothing about the bluetooth integrated in it. For those, who will have the same problem, on [http://alsa.opensrc.org/Hotplugging_USB_audio_devices_%28Howto%29]("http://alsa.opensrc.org/Hotplugging_USB_audio_devices_%28Howto%29") is really good solution.

---

### Post by moose32 on 2007-01-27
I don't know if this is helpful to anyone but I got my Plantronics 590E to work with Ubuntu Edgy and kbluetoothd. The bluetooth dongle I'm using is a Bluetooth 2.0 EDR (seems to be no name as it only says Bluetooth on the package)

Some instructions on how I did

Editing /etc/bluetooth/hcid.conf and adding auto instead of user in security) Restarting bluetooth: sudo /etc/init.d/bluetooth restart

sudo apt-get install kdebluetooth

Pairing the headset: pin_helper didn't do much in bluez as it's no longer supported it seems? You have to use bt-applet instead that is a part of the bluez-passkey-gnome package (sudo apt-get install bluez-passkey-gnome). It's loaded in Sessions (System->Preferences->Sessions) but with the parameter --sm-disable. So disable that one and just add a new one that says "bt-applet" (without the ""). This should enable you to get a popup dialog with kbluetoothd that asks you for a pin number. (Default for headsets usually is 0000)

Modules: I installed btsco-0.5 (bluetooth alsa) and loaded the modules snd_bt_sco and sco (sudo modprobe snd-bt-sco && modprobe sco).

When you have all this in place and bt-applet running correctly in the background you can just pair the device. kbluetoothd might not detect it at first but running btsco -v mac_adress_for_your_headset will fix that (adress can be found with hcitool scan). It should automatically detect your headset from now on.

This will enable the old drivers so if you have a A2DP headset you got to do some more (look at [http://bluetooth-alsa.sourceforge.net/build.html](http://bluetooth-alsa.sourceforge.net/build.html)) I haven't gotten to the A2DP part yet myself.

---

### Post by montag on 2007-02-03
Hi all,
I'm trying to use a Nokia HS-36W headset with skype.
I'm using Kubuntu.
I followed the howto, and it seems all ok, but when I run
aplay -B 1000000 -D plughw:Headset "myfavouritesong"
the headset only say "beep beep" and then nothing...
I tried also with xmms (changing output from default to BT headset), but I got the same result.

Any idea?

Thank you!

---

### Post by mmxbass on 2007-02-17
> **montag said:**
> Hi all,
I'm trying to use a Nokia HS-36W headset with skype.
I'm using Kubuntu.
I followed the howto, and it seems all ok, but when I run
aplay -B 1000000 -D plughw:Headset "myfavouritesong"
the headset only say "beep beep" and then nothing...
I tried also with xmms (changing output from default to BT headset), but I got the same result.

Any idea?

Thank you!I have having this exact same problem with my Motorola H500. Everything seems to be going great up to the point where I hit play. The headset beeps once and then nothing. Interestingly the little slider bar in XMMS stops (as does the song timer) at exactally 2 seconds (my buffer is also 2 seconds). No information yet as to what I can do about it though.

---

### Post by arsenix on 2007-03-15
Just for reference (since google brought me to this thread looking for this issue).

If you get this message when trying hcitool:
"Device is not available: No such device"

it means that hcitool can't find your bluetooth adapter.  for me I had to hotplug it by pressing the fn+F2 on my notebook to cycle the wireless.  So if you are getting that message you need to make sure your bluetooth driver is installed and working.

James

---

### Post by automatthias on 2007-03-17
> **-Chi.0 said:**
> I keep getting this after running [COLOR="Magenta"]btsco -v <mac address>[/COLOR] ](*,) 

```
Error: hwdep next device (hw:0): Operation not permitted
Error: hwdep next device (hw:1): Operation not permitted
Error: control open (hw:2): No such device
Error: Can't find device. Bail
```

Can any one point me in the right direction please?

sudo modprobe snd_bt_sco

---

### Post by hq4ever on 2007-03-26
> **rockprincess said:**
> followed your advice and after this i got that:

```
sudo hcitool auth 00:16:XX:XX:XX:XX
HCI authentication request failed: Input/output error

```

when will Pairing get fixed on Kubuntu Edgy Eft?! :-k

Is this claim still relevant (Ubuntu etch 6.10).
I'm getting exactly the same error trying to peer with Nokia 6820

```

root@lucky:~# hcitool scan
Scanning ...
        00:18:42:CD:D5:26       Nokia 6280
root@lucky:~# hcitool cc 00:18:42:CD:D5:26
root@lucky:~# hcitool con
Connections:
        < ACL 00:18:42:CD:D5:26 handle 42 state 1 lm SLAVE
root@lucky:~# hcitool auth 00:18:42:CD:D5:26
HCI authentication request failed: Input/output error
root@lucky:~# hcitool con
Connections:
        < ACL 00:18:42:CD:D5:26 handle 42 state 1 lm SLAVE

```

The phone is right next to me, and I'm running root so I don't think it's a permission / reception problem. I've also tried to restart /etc/init.d/bluetooth.

What am I doing wrong?

---

### Post by sudo_t43p on 2007-04-02
> **moose32 said:**
> I don't know if this is helpful to anyone but I got my Plantronics 590E to work with Ubuntu Edgy and kbluetoothd. The bluetooth dongle I'm using is a Bluetooth 2.0 EDR (seems to be no name as it only says Bluetooth on the package)

Some instructions on how I did

Editing /etc/bluetooth/hcid.conf and adding auto instead of user in security) Restarting bluetooth: sudo /etc/init.d/bluetooth restart

sudo apt-get install kdebluetooth

Pairing the headset: pin_helper didn't do much in bluez as it's no longer supported it seems? You have to use bt-applet instead that is a part of the bluez-passkey-gnome package (sudo apt-get install bluez-passkey-gnome). It's loaded in Sessions (System->Preferences->Sessions) but with the parameter --sm-disable. So disable that one and just add a new one that says "bt-applet" (without the ""). This should enable you to get a popup dialog with kbluetoothd that asks you for a pin number. (Default for headsets usually is 0000)

Modules: I installed btsco-0.5 (bluetooth alsa) and loaded the modules snd_bt_sco and sco (sudo modprobe snd-bt-sco && modprobe sco).

When you have all this in place and bt-applet running correctly in the background you can just pair the device. kbluetoothd might not detect it at first but running btsco -v mac_adress_for_your_headset will fix that (adress can be found with hcitool scan). It should automatically detect your headset from now on.

This will enable the old drivers so if you have a A2DP headset you got to do some more (look at [http://bluetooth-alsa.sourceforge.net/build.html](http://bluetooth-alsa.sourceforge.net/build.html)) I haven't gotten to the A2DP part yet myself.

Thanx man! Still have to (on Fiesty) btsco -v when I wanna connetct but that is no big deal.

---

### Post by PartisanEntity on 2007-04-08
Hello, anyone have a good how to for those who don't use kubuntu?

---

### Post by Aetherius on 2007-04-10
the howto can be applied to gnome (ubuntu), just ignore the kbluetoothd business, bluez etc is stil relevant. bluetooth-applet will suffice if you need a tray applet. for obex transfers install gnome-bluetooth and run gnome-obex-server to be receptive to files and gnome-obex-send to send them ;)

of course you can still follow the howto to the letter if you want, won't break ya

---

### Post by PartisanEntity on 2007-04-10
im trying to get my bluetooth headset to work with ubuntu so i can use it with skype. when i put my headset into pairing mode nothing happens in ubuntu. (i have already successfuly paired my cellphone with ubuntu through bluetooth so i know it works in theory).

---

### Post by Verplrke on 2007-04-12
Hello, Im trying to get Bluetooth Alsa to work with Amarok (Xine-engine).

They had this on the website at [http://bluetooth-alsa.sourceforge.net/build.html](http://bluetooth-alsa.sourceforge.net/build.html)
> If you are using KDE (ex: Kubuntu) you could also use kaffeine to play your multimedia files. In order to do so you need to edit the .kde/share/apps/kaffeine/xine-config file in your home directory. Find the 'audio.driver' parameter and change it to 'alsa'. You also need to change the 'audio.device.alsa_front_device' parameter and change it to 'a2dpd'.

So  I went looking in .kde/share/apps/amarok xine-config . The bluetooth-alsa website used 'a2dpd', I tried changing default to 'a2dpd' and 'snd_bt_sco' but that didn't work.

This is the code of the xine-config file
```
# device used for stereo output
# string, default: plug:front:default
audio.device.alsa_front_device:default
```

Perhaps I can lookup the exact name in some alsa-configuration file but I wouldn't know where to look for one of those.

Perhaps a simple solution to download amarok-xmms but i can't find the debian file.

---

### Post by bullant on 2007-04-25
> **hexnet said:**
> I have having this exact same problem with my Motorola H500. Everything seems to be going great up to the point where I hit play. The headset beeps once and then nothing. Interestingly the little slider bar in XMMS stops (as does the song timer) at exactally 2 seconds (my buffer is also 2 seconds). No information yet as to what I can do about it though.

Had the same problem with a Sony-Ericsson HBH-PV700 headset connecting to a Bluetooth USB dongle. Solution was to move the dongle from the USB port on my monitor and plug it in directly into a USB port on the PC. Seems the sound won't traverse a USB hub which the monitor was acting as.

---

### Post by Roner on 2007-04-29
An updated howto for bluetooth headsets on Feisty is [here]("http://ubuntuforums.org/showthread.php?t=426828&highlight=feisty+bluetooth+headset").

---

### Post by emil10001 on 2007-05-02
@Verplrke
Assuming that you have set everything else up properly and know that the a2dpd output is working properly, then all you need to do in amarok is go into the Settings -> Configure Amarok -> Engine  and make sure that output is set to "alsa," and the mono and stereo fields are set to a2dpd. 

I was initially having issues getting things sent to the proper place, but found that when i built and installed the "plugz," it didn't put some of the libs in the correct location. See: [http://ubuntuforums.org/showthread.php?p=2571844](http://ubuntuforums.org/showthread.php?p=2571844)

-John

---

### Post by dpreacher on 2007-05-29
i needed a little help with the pin-helper app.

there seems to be a lot of pin helper apps... like kbluepin, bluez-pin n something called link_key (not sure). i am using kde n got bluez-utils n kbluetooth...do i get kbluepin separately. how do i set either of these as the pin-helper. when kbluetooth tries to connect to nokia 6670 i get a prompt for enterin pin on phone n i enter 1234. some site had suggested to make 2 files one being the /etc/bluetooth/pin containin the code and the other being a shell script outputtin the contents of /etc/bluetooth/pin which is '1234' (without the quotes). 
anyways, after i enter the pin the konqueror window fails after some time and the error returned is timer has exceeded the timeout value (300).


all help appreciated

---

### Post by shoki on 2007-05-29
> **Peepsalot said:**
> Has anyone gotten a linksys CIT200 Skype phone to work in linux?

 Any luck?

---

### Post by Cresho on 2007-05-31
thanks for this post, i was able to get my bluetooth working.  On my razr, i had to do this last step to get it working.

then for pin problems and correction, install this and reboot.

sudo aptitude install bluez-passkey-gnome

after the reboot, i was able to pair.

---

### Post by Lgndryhr on 2007-07-13
I followed this howto but was unsuccessful in getting my cell phone to connect properly. I am using a Belkin Model #: F8T012 USB Bluetooth Dongle.

I did some of the things listed [here](http://ubuntuforums.org/showthread.php?t=359275) as well as what I found [here](http://www.linuxquestions.org/questions/showthread.php?t=185978). I got as far as them paring the first time on my samsung a727 then my cell said it couldn't find the processes or something. Now my cell can't connect. They see each other but just wont connect now. Any ideas?

Then Upon running Bluetooth File Sharing 0.8.0 my cell connected and says browsing files... and my dongle is blinking which means it is talking/sending info to the cell, I hope.
It continued to blink and my cell continued to say the same thing for 10 minutes but nothing happened so I stopped it.

Then upon reading here I was able to get it to connect to my computer and pair but my cell is trying to send files and it just sits there and says browsing files while my computer awaits a transfer.

---

### Post by Lgndryhr on 2007-07-13
does no one have any idea how to get this to work?

---

### Post by rvernica on 2007-11-12
Did anyone managed to get a Motorola H300 working?

I got mine set up and paired up but I cannot hear any sound, just a "sssssssssssssss".

Any suggestions are welcome.

Thanks.

---

### Post by rockprincess on 2007-11-14
what are your skype configurations, rvernica?

also have you made sure the mic and mic boost is on in the sound control panels? are you using kde or gnome?

---

### Post by bzzz on 2007-12-08
Hello.

I'm wondering if someone managed to get some wire headsets connected to the PC via a phone.
So, I have a SE w810i with the stock headset (not bluetooth). I managed to get the phone's bluetooth working with ubuntu, now I'm wondering if I can play some music or make skype calls from the PC and use the headsets from the bluetooth connected phone.
Hope you got the point, my english sucks. Thanks.:guitar:

---

