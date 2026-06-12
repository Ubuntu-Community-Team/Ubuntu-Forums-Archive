---
title: "just updated from Ubuntu 10.04 to Xu 12.04 getting &quot;no network connection&quot;"
date: 2013-07-15
forum: General Help
---

### Post by eival on 2013-07-15
EDIT- i just had to fully power cycle my router(actually unplug everything), you gotta be kidding me.

i had a feeling that was it when the other OS's on my machine also couldnt connect.


thanks to those who tried to help

---

### Post by eival on 2013-07-15
as soon as the OS loads it tellls me theres 100 software updates but the network popup comes up at the same time saying no connection.

my networking appears to be fine, i see eth0 but its not communicating with my wired router

i remember having this issue a few months ago but forgot the workaround, ive tried changing the network config from lo/loopback to:


auth eht0
iface eth0 inet dhcp

that didnt work, neither did |sudo dpkg-reconfigure resolvconf|

when it reboots it says waiting for network responce for 60 seconds till eventually it loads the desktop

what am i missing? the network was fine as i was installing/upgrading

---

### Post by Hadaka on 2013-07-15
hi, your /etc/network/interfaces should look like this..
```
auto lo
iface lo inet loopback
```
please post the output of..
```
rfkill list all
lsmod
lspci -nnk | grep -iA3 net
```
thanks.

---

### Post by mörgæs on 2013-07-15
It's better to ask for the post to be moved (using Report Post) than to post again and delete.
Threads merged.

---

### Post by eival on 2013-07-15
hadaka my settings does say lo and loopback. i only tried changing cause that was the most common sollution for this issue

ill run the other code now, computers in another room so i have to run back and forth :p

although i could probably set up some type of desktop share, oh well (nvm that obviously wont work since it cant even connect to the router)

---

### Post by eival on 2013-07-15
> **Hadaka said:**
> hi, your /etc/network/interfaces should look like this..
```
auto lo
iface lo inet loopback
```
please post the output of..
```
rfkill list all
lsmod
lspci -nnk | grep -iA3 net
```
thanks.

it said it didnt recognize your last code with iA3

but for lsmod and forgive the writen version

module-------------size-------------used by
usbhid------------- 36110-------------0
hid------------------ 67288-------------1 usbhid
usb_storage----470033------------0
r8169------------- 34140-------------0
mii-------------------4381------------- 1  r8169

---

### Post by Hadaka on 2013-07-15
Hi, if possible can you load the output of those commands
onto a usb stick and send them?...the -iA3 net
is one command.. lspci -nnk | grep iA3 net
and...lsmod
i really need the full print out if possible.
thanks.

---

### Post by eival on 2013-07-15
i actually thought of that an i tried plugging in both of my USB flash drives to copy over the text in a notepad and neither would mount, both worked fine on 10.04 recently, the light blinks and i actually saw it show up for a splitsecond on my desktop then disapear, so perhaps thats an issue as well.

i just saw on morgaes's sig that you should unplug anything from your USB ports before install/upgrade, i had a PS3 controller plugged in charging, maybe thats why my USB ports are messed  up?
 i was going to try unplugging that and rebooting to see if that works, and then try running the live cd of Ubuntu 10 and see if the networking works in that


how ever, what i posted is litterally all that showed up, the only other text is "-iA3" command not found

---

### Post by eival on 2013-07-15
> **Hadaka said:**
> Hi, if possible can you load the output of those commands
onto a usb stick and send them?...the -iA3 net
is one command.. lspci -nnk | grep iA3 net
and...lsmod
i really need the full print out if possible.
thanks.

wait, so the minus sign before iA3 was a mistake? ill try that now

---

### Post by eival on 2013-07-15
alright managed to save it to a cd, also when i entered grep -iA3 net it just hangs, when i dont use the minus sign it says no such directory "net"

```
$ lsmod
Module                  Size  Used by
usbhid                 36110  0 
hid                    67288  1 usbhid
usb_storage            40033  0 
r8169                  34140  0 
mii                     4381  1 r8169

$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e20] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:2a94]
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e22] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:2a94]
00:02.1 Display controller [0380]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e23] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:2a94]
00:1a.0 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
	Subsystem: Hewlett-Packard Company Device [103c:2a94]
	Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
	Subsystem: Hewlett-Packard Company Device [103c:2a94]
	Kernel driver in use: uhci_hcd
00:1a.2 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
	Subsystem: Hewlett-Packard Company Device [103c:2a94]
	Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c]
	Subsystem: Hewlett-Packard Company Device [103c:2a94]
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
	Subsystem: Hewlett-Packard Company Device [103c:2a94]
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40]
	Kernel driver in use: pcieport
00:1c.5 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6 [8086:3a4a]
	Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
	Subsystem: Hewlett-Packard Company Device [103c:2a94]
	Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
	Subsystem: Hewlett-Packard Company Device [103c:2a94]
	Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
	Subsystem: Hewlett-Packard Company Device [103c:2a94]
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a]
	Subsystem: Hewlett-Packard Company Device [103c:2a94]
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIB (ICH10) LPC Interface Controller [8086:3a18]
	Subsystem: Hewlett-Packard Company Device [103c:2a94]
00:1f.2 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1 [8086:3a20]
	Subsystem: Hewlett-Packard Company Device [103c:2a94]
	Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
	Subsystem: Hewlett-Packard Company Device [103c:2a94]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:2a94]
	Kernel driver in use: r8169
```

---

### Post by eival on 2013-07-15
also for what its worth, when i hover the mouse over the network monitor app on the toolbar it says 

<< >> Interface down

i tried booting the ubuntu 10 cd and it wasnt getting a network connection either. i factory reset the router and rebooted the computer, thats still the only device that cant connect.

maybe if i manually enter my full IP and subnet in the router and on my computer? force it to see eachother

and one other thing i thought of, when i upgraded it did hang near the end and say something to the extent of "not all files could be installed, you may have to install some applications"

i also changed my username, so my old name and all those files are still there along side the new one, perhaps that cause some type of issue?

---

### Post by Hadaka on 2013-07-15
Hi, sorry i posted the command incorrectly.
it is..
one line.
```
lspci -nnk | grep -iA3 net
```
and..
```
lsmod
```
thanks.

---

### Post by eival on 2013-07-15
> **Hadaka said:**
> Hi, sorry i posted the command incorrectly.
it is..
one line.
```
lspci -nnk | grep -iA3 net
```
and..
```
lsmod
```
thanks.

it just hangs after i do

lspci -nnk | grep -iA3 net

the cursor goes to the next line and just stays there

---

### Post by eival on 2013-07-15
nvm it loaded now

```
$ lsmod
Module                  Size  Used by
rfcomm                 38139  4 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
bluetooth             158479  10 rfcomm,bnep
snd_hda_codec_realtek   174313  1 
joydev                 17393  0 
snd_hda_intel          32719  4 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                86520  0 
serio_raw              13027  0 
i915                  428056  2 
snd                    62218  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hid_sony               12734  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
drm_kms_helper         45466  1 i915
drm                   197641  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
lp                     17455  0 
video                  19115  1 i915
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    77428  2 hid_sony,usbhid
r8169                  56368  0 
usb_storage            39646  0 
$ lspci -nnk | grep -iA3 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:2a94]
	Kernel driver in use: r8169
	Kernel modules: r8169
```

---

### Post by eival on 2013-07-15
i was poking around in the network config files and i see it looking for a 169.xxx so on IP/dns server, could that be causing an issue?

is there a way to just reset everything, outside of reinstalling the OS

---

