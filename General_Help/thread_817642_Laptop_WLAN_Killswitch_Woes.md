---
title: "Laptop WLAN Killswitch Woes"
date: 2008-06-03
forum: General Help
---

### Post by Trainman2095 on 2008-06-03
Ack!

My laptop (HP pavilion ze4900) has a button(kill-switch?) with a light that goes on when the wlan is on, with xubuntu(8.04) its not turning on. It worked fine and dandy with windows, but now nothing. It's not a card, it's built in. internet works if i plug the ethernet cable in but otherwise no connection. I've heard of similar problems but they all had cards. Plus I don't know how to fix it.

I'm very new to Xubuntu, I installed because my laptop was hideously slow. It's faster now, but the one thing i use it for, internet, doesn't work.

I tried to reboot with the switch on, but it didn't work.

Please help...

-Train

---

### Post by Sam Lars on 2008-06-03
What type of wireless card do you have?  It should be listed in the output of
```
lspci
```
in a terminal.

---

### Post by Trainman2095 on 2008-06-03
It says
```
bash: 1spci: command not found
```

Perhaps because I don't have a card. The WLAN is built in.

---

### Post by Sam Lars on 2008-06-03
The first letter is a lower-case L, not a one.

---

### Post by jpryor68 on 2008-06-04
Many of us are now missing the wlan light. In my case, I have a built-in Intel 3945 wifi adaptor. We used to use the driver ipw3945 for this adaptor (Ubuntu packages it as a kernel module). With recent versions of Ubuntu (I don't know when the change happened, I jumped from Edgy to the Hardy alphas), we started using the new iwl3945 driver instead (also a kernel module). I'm not sure of all the reasons why the newer driver is better: I think one reason is that the old driver was proprietary, whereas the new driver is open source. Anyway, until now the iwl3945 driver has not been handling the wlan lights on laptops. Your wifi adaptor will work; the driver just won't make that light flash.

I think the 2.6.26 kernels (now at the rc stage, we'll probably see them in the fall Ubuntu release) do finally get the wlan light working again.

If you've got a different wifi adaptor, and aren't using the iwl3945 driver, then I don't know what the explanation is.

---

### Post by Sam Lars on 2008-06-04
Well the problem isn't the light as much as the switch.  I've noticed that my switch doesn't seem to affect whether the wireless works or not, so I'm thinking that he just needs to get his wireless working, since the switch does nothing.

---

### Post by Trainman2095 on 2008-06-04
Aha. now it says:

```
...
Ethernet Controller: Realtek Semicinductor RTL - 8139/8139C/8139C+ 
Card Bus Bridge: Texas Instruments PCI1410 PC Card Cardbus Controller (re v 02)

Network Controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN controller (rev 03)
```

And a bunch of other stuff that doesn't concern the Internet.

---

### Post by Sam Lars on 2008-06-04
I have a couple cards with the same chipset.
If you go to the Restricted Drivers Manager (System > Administration), does it list the driver for the card?

---

### Post by Trainman2095 on 2008-06-04
Alas. There is no Administration under System...

---

### Post by Sam Lars on 2008-06-04
How about the output of
```
iwconfig
```
in a terminal?
If it says there are no wireless extensions anywhere, then hook it up to a wired connection and install bcm43xx-fwcutter.

---

### Post by Trainman2095 on 2008-06-04
Well, it says...

```

lo            No wireless extensions

eth0          No wireless extensions

wmaster0      No wireless extensions


wlan0     IEEE 802.11g  ESSID:""
Mode: Managed  Channel:0 Access Point: Not-Associated
Tx-Power=0  dBm
Retry min limit:7   RTS thr:off   Fragment thr=2346 B
Link quality:0  Signal Level:0  Noise Level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid Misc:0  Missed Beacon:0
```

---

### Post by Sam Lars on 2008-06-04
Can you configure the network from the network icon on the panel?  You could also try going to System > Network to set it up.

---

### Post by Trainman2095 on 2008-06-04
I don't think I can. Remember, kill-switch?

And if I can...

How?

---

### Post by Sam Lars on 2008-06-04
I thought that the kill switch was doing absolutely nothing...
If you click on the network icon on the panel, what does it give you?
You should be able to go to System > Network and select the wireless card properties, enter the access point and security/password if you have it set.

---

### Post by Trainman2095 on 2008-06-04
Uhh... How?

---

### Post by Sam Lars on 2008-06-04
Can you click on the network icon?  Does it do anything?
What do you see when you go to System > Network?

---

### Post by Trainman2095 on 2008-06-05
It takes me to The Network Options Window.

---

### Post by Sam Lars on 2008-06-05
Try this:

All files that you open must be opened as root.
```
sudo mousepad /directory/file
```
Or whatever text editor you want to use instead of mousepad.

Open /etc/modules
If there's anything that says b43, delete it.
Add:
```
bcm43xx
```
Save that file and close it.
Open /etc/modprobe.d/blacklist
Find where it says something like "## Replaced by b43 ##" and it will say below that something like "blacklist bcm43xx"
Replace that line with these two lines:
```
blacklist b43
blacklist ssb
```
Save that file and close it.
I've attached an archive with the firmware for your card.  Download it, unpack it, and put all of the files inside it in /lib/firmware
For the first command, replace /home/user/Desktop with wherever you download or move the file to.
```
cd /home/user/Desktop
tar -xz libfirmware.tar.gz
sudo cp libfirmware/* /lib/firmware
```
Open your /etc/network/interfaces file and if there's anything for wlan0, replace it all with this.  If not, just add it.
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid your_essid
```
Then reboot.

---

### Post by Trainman2095 on 2008-06-05
How do I put all the libfirmware files in lib/firmware? sudo mousepad?

---

### Post by Sam Lars on 2008-06-05
Change to the directory where you downloaded the file.
```
cd /home/user/Desktop
```
Unpack the file.
```
tar -xz libfirmware.tar.gz
```
Copy all files in resulting folder to /lib/firmware.
```
sudo cp libfirmware/* /lib/firmware
```

You could also open the file manager with sudo, copy the files, and paste them into /lib/firmware.

---

### Post by Trainman2095 on 2008-06-05
Ack. Where do I find my SSID again? In my host computer? Network?

---

### Post by Sam Lars on 2008-06-05
```
iwlist scan
```
If your card is working, this command should find your wireless network and tell you all about it.

---

### Post by Trainman2095 on 2008-06-05
It says: Interface doesn't support scanning.

---

### Post by Sam Lars on 2008-06-05
Have you restarted yet?  Try that if you haven't.

---

### Post by Trainman2095 on 2008-06-05
Still Interface doesn't support scanning.

---

### Post by Sam Lars on 2008-06-06
What do you get from
```
iwconfig
ifconfig
```

---

### Post by Trainman2095 on 2008-06-06
My ESSID is "".

ifconfig gives info for eth0 and lo.

---

### Post by Sam Lars on 2008-06-06
```
sudo rmmod b43
sudo rmmod ndiswrapper
sudo rmmod bcm43xx
sudo rmmod ssb
sudo modprobe bcm43xx
```
See if it works, if it doesn't, then
```
sudo /etc/init.d/networking restart
```
If it still doesn't work, could you post everything that iwconfig says?

---

### Post by Trainman2095 on 2008-06-06
```
lo            No wireless extensions

eth0          No wireless extensions

wmaster0      No wireless extensions


wlan0     IEEE 802.11g  ESSID:""
Mode: Managed  Channel:0 Access Point: Not-Associated
Tx-Power=0  dBm
Retry min limit:7   RTS thr:off   Fragment thr=2346 B
Link quality:0  Signal Level:0  Noise Level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid Misc:0  Missed Beacon:0
```

---

### Post by Trainman2095 on 2008-06-07
I tried changing the ESSID in the code, but it didn't work.

---

### Post by Trainman2095 on 2008-06-13
Hello?

---

### Post by Sam Lars on 2008-07-02
Sorry, I was on vacation for a while, I didn't have much time to keep up around here.
Make sure you have what I mentioned [here]("http://ubuntuforums.org/showpost.php?p=5123995&postcount=18") in the correct files.  Then, what do you get from:
```
ifconfig
iwconfig
iwlist scanning
```

---

