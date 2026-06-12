---
title: "Gutsy GNOME login takes a long time"
date: 2007-10-21
forum: General Help
---

### Post by phibit on 2007-10-21
I have an HP DV2120ca laptop with Gutsy AMD64 running, and every since my upgrade from Feisty, logging in to GDM takes unusually long.

The boot speed itself is fine, but when I get to the login screen and enter my password, it spends a good minute just displaying the beige background with nothing else. This problem occurs with or without compiz enabled.

Anyone else have this problem or know of a fix?

---

### Post by markp1989 on 2007-10-21
i have the same problem

---

### Post by phibit on 2007-10-21
It's harsh, but right now I'm messing around with my System > Sessions, disabling stuff as I go. Perhaps it's trackerd, the new indexing service?

---

### Post by phibit on 2007-10-21
Okay I broke down and tried to just disable everything in System > Preferences > Sessions, and still no change, so that's not the issue. GRRRR!

---

### Post by styxie on 2007-10-21
I've got the same problem here. It might be that /etc/usplash.conf has the wrong values (mine said 1280x1024, and my laptop screen is 1280x800) so I've changed them, but I've yet to test this.

---

### Post by chrisccoulson on 2007-10-21
> **styxie said:**
> I've got the same problem here. It might be that /etc/usplash.conf has the wrong values (mine said 1280x1024, and my laptop screen is 1280x800) so I've changed them, but I've yet to test this.

I think the OP is referring to the time taken for the desktop to appear after entering their password at the GDM screen. Therefore, I don't think usplash resolution would affect this.

To the OP: Have you tried creating a fresh user account to see if it takes just as long to log in with it. That may give you an idea as to whether it's related to your user profile or something system-wide. A minute does seem a bit excessive for the desktop to appear.

I have had problems with excessive log in times in GNOME before. In my case, it was caused by a networking problem. You could try switching to a terminal before you log in (CTRL+ALT+F1), logging in and doing ifconfig to see if you have a loopback interface (lo) listed. My problems were due to their being no loopback interface caused by a failure to start networking.

---

### Post by styxie on 2007-10-21
> **chrisccoulson said:**
> I think the OP is referring to the time taken for the desktop to appear after entering their password at the GDM screen. Therefore, I don't think usplash resolution would affect this.

To the OP: Have you tried creating a fresh user account to see if it takes just as long to log in with it. That may give you an idea as to whether it's related to your user profile or something system-wide.

Yes you're right, I mixed up the topics. However, I do also suffer from this.

---

### Post by KRavEN on 2007-10-22
If you did an upgrade, try removing evms.  You can tell for sure if you ctrl-alt-f1 and see scrolling messages from device-mapper.

---

### Post by phibit on 2007-10-22
> **chrisccoulson said:**
> 
To the OP: Have you tried creating a fresh user account to see if it takes just as long to log in with it. That may give you an idea as to whether it's related to your user profile or something system-wide. A minute does seem a bit excessive for the desktop to appear.

I have had problems with excessive log in times in GNOME before. In my case, it was caused by a networking problem. You could try switching to a terminal before you log in (CTRL+ALT+F1), logging in and doing ifconfig to see if you have a loopback interface (lo) listed. My problems were due to their being no loopback interface caused by a failure to start networking.

Thanks for the suggestions. Logging in as a different user yields the same slow loading. I've checked my ifconfig and i do have a loopback happening, so that's not the issue either. I'm not sure what do to with this point, there doesn't seem to be much documentation on this problem, and it's not something that's UNBEARABLE, so I can deal with it until someone comes up with a fix.

---

### Post by frodon on 2007-10-22
Try this ;) :
[http://ubuntuforums.org/showpost.php?p=3568252&postcount=2](http://ubuntuforums.org/showpost.php?p=3568252&postcount=2)

---

### Post by phibit on 2007-10-22
Thanks frodon, but this isn't a usplash issue, or at least i don't think. I can see the splash fine. The problem is with my gdm login, so after i'm presented with the login screen.

---

### Post by bach on 2007-10-22
I am having the same problem. Suggestions are welcome.

---

### Post by yostral on 2007-10-22
Yep, same here too...

---

### Post by julep on 2007-10-22
I'm experiencing the same issue, takes too long to get the desktop started. I noticed that I have two instances of GDM running. Is that normal?

./J

---

### Post by spotdog14 on 2007-10-22
Im glad that i searched, because i am having the same problem.

---

### Post by tehtrk on 2007-10-23
Before anyone else mentions usplash ( [http://ubuntuforums.org/showthread.php?p=3568252#post3568252](http://ubuntuforums.org/showthread.php?p=3568252#post3568252) ), this seems to be a separate issue. 

What is being described is Gnome taking unusually long to load (loads background or bg color instantly, then takes a very long time to load panels and applets. In my case, gnome is displaying it's first panel 2-3 minutes after logging on from GDM vs the 2-5 seconds it used to take on Feisty. 

I watched htop from a separate console to see if anything was taking up a lot of CPU time while I was waiting, and didn't notice anything. The CPU was almost idle. 

I suggest if you are having this problem, post some information about what you are running. This may help weed out the issue by comparing system similarities. 

I will start with the basics and then move on to lspci dumps etc. 
[B]
_Hardware:_
[LIST]
[*]HP/Compaq Presario C303NR (C300 Series) Laptop
[*]Intel Celeron Processor
[*]intel i810 video (i915 driver? I thought it was i810...)
[*]conexant audio
[*]broadcom wireless (not using NDISwrapper)
[*]Realtek LAN
[/LIST]

_Software:_
[LIST]
[*]Ubuntu Gutsy Early Release (with kernel 2.6.20-16 (ubuntu) or 2.6.22-10 (ubuntu) or 2.6.22-14 (vanilla) or kernel 2.6.22 (vanilla and ck1)
[*]Gnome with or without openbox --replace
[*]cpufreq with p4_clockmod
[*]Gnome System Monitor applet
[*]CPU Frequency Scaling Monitor applet (with setuid root)
[/LIST][/B]

[COLOR="Red"]Seeing _LOTS_ of /usr/sbin/console-kit-daemon processes (62!!) Just saw that...

I Believe THAT to be related to this: [http://ubuntuforums.org/showthread.php?p=3600578](http://ubuntuforums.org/showthread.php?p=3600578) [/COLOR]


_Output of lspci_
```


00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

```

lsmod
Module                  Size  Used by
nls_cp437               6784  1 
isofs                  36284  1 
udf                    85252  0 
michael_mic             3584  6 
arc4                    2944  6 
ecb                     4480  6 
blkcipher               6784  1 ecb
ieee80211_crypt_tkip    12032  3 
af_packet              23816  4 
binfmt_misc            12680  1 
ppdev                  10116  0 
cpufreq_ondemand        9228  0 
rfcomm                 40856  2 
l2cap                  25856  11 rfcomm
bluetooth              55908  4 rfcomm,l2cap
capability              5896  0 
ipv6                  268960  10 
i915                   25472  2 
drm                    81044  3 i915
tc1100_wmi              8068  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
asus_acpi              17308  0 
sbs                    15652  0 
battery                10756  0 
button                  8720  0 
ac                      6020  0 
backlight               7040  1 asus_acpi
video                  16388  0 
container               5248  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
dock                   10268  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
p4_clockmod             6692  0 
speedstep_lib           6148  1 p4_clockmod
freq_table              5792  3 cpufreq_ondemand,cpufreq_stats,p4_clockmod
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  2 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
bcm43xx               126824  0 
psmouse                38920  0 
ieee80211softmac       31360  1 bcm43xx
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ieee80211              34760  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,ieee80211
serio_raw               7940  0 
snd                    54020  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  2 snd
intel_agp              26140  1 
agpgart                35400  3 drm,intel_agp
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
evdev                  11008  4 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sd_mod                 23428  3 
8139too                27648  0 
usbhid                 26592  0 
hid                    27392  1 usbhid
sg                     36252  0 
sr_mod                 17060  1 
cdrom                  37664  1 sr_mod
generic                 5124  0 [permanent]
ata_generic             9092  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ahci                   22020  2 
ata_piix               15492  1 
libata                125720  3 ata_generic,ahci,ata_piix
scsi_mod              142348  4 sd_mod,sg,sr_mod,libata
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  4 usbhid,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
commoncap               8192  1 capability
fuse                   46612  1 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit


```

Edit: Meanwhile running matchbox desktop until this gets resolved. It's spartan for a main desktop, but it's crazy fast!!

---

### Post by tehtrk on 2007-10-23
Bump

---

### Post by Lizzy on 2007-10-23
Same problem here and i don't even have fancy/compiz/beryl-eyecandy running, cause it doesn't with my graphics card ;-) ......

---

### Post by sefs on 2007-10-23
same problem here.

---

### Post by dpar on 2007-10-23
+1

---

### Post by Nicu Alecu on 2007-10-23
Me 2! on an (relatively) ancient NX9010 ...

---

### Post by nickless on 2007-10-23
Same problem  on my Dell Inspiron 9400 :(
Takes about 30-40 seconds to load after login.
Using Compiz Fusion on Gutsy

---

### Post by #Reistlehr- on 2007-10-23
I started a thread on this the other day, with one reply.

My sig has my laptop specs in it.

I'm not that moody about it, because hey, it still works, just takes a long time. I filed a bug report too, let me go find the link.

---

### Post by cowanh00 on 2007-10-24
I'm having this problem on my Dell Latitude D620. I have Compiz enabled as well as a load of screenlets and the AWN dock. Even when I disable everything on startup it still takes so long to get from after I enter my password to getting to a working desktop. It was much quicker on Feisty!

---

### Post by frodon on 2007-10-24
Think to comment bug reports with your experience :
[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544)

---

### Post by yyz on 2007-10-24
I'm having the same problem too.

---

### Post by Caffeine_Junky on 2007-10-24
> **phibit said:**
> I have an HP DV2120ca laptop with Gutsy AMD64 running, and every since my upgrade from Feisty, logging in to GDM takes unusually long.

The boot speed itself is fine, but when I get to the login screen and enter my password, it spends a good minute just displaying the beige background with nothing else. This problem occurs with or without compiz enabled.

Anyone else have this problem or know of a fix?

Yep's, same here.   I don't see it as a problem, just something that has been left-out/removed from this release,  it has been this way since T3 was put out.   Maybe it will be addressed soon.  I hope it will be, because looking at a "blank beige screen" between login and desktop seems a little bit untidy IMO


Edit: 
I found a way to change the colour of the "Blank Beige Screen" that is displayed while Gnome is loading:

> 1) Open /etc/gdm/PreSession/Default with your favorite text editor using sudo:

sudo gedit /etc/gdm/PreSession/Default

2) Find the line that says BACKCOLOR="#DAB082" and change it to the HEX color of your choice. I wanted mine black so mine says BACKCOLOR="#000000".

3) Save the file and reboot!    *snipped*  

ps: My Gnome loading time is normal (same time to load as feisty) it is just that there is no splash on it, just a blank screen.

---

### Post by dpar on 2007-10-24
> **frodon said:**
> Think to comment bug reports with your experience :
[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544)

Comments have been sent:)

---

### Post by commonlyUNIQU3 on 2007-10-24
+1 

Dell Latitude D820

---

### Post by nickless on 2007-10-24
Is it possible to change at least the color anywhere? :D setting a picture would be nice too...

---

### Post by #Reistlehr- on 2007-10-24
> **nickless said:**
> Is it possible to change at least the color anywhere? :D setting a picture would be nice too...

Go to Administration -> Login Window -> Local  and there is a thing that syas Background Color

My desktop BG is blue untill it hangs. Then it goes to the ugly brown/tan. One thing i noticed too, is if you do nosmp in the boot line, the desktop will load, then disappear, only to reappear after a lifetime of waiting.

---

### Post by mahousaru on 2007-10-24
Can those who have long boot times after the usplash has loaded check

/etc/network/interfaces 

and check that it only has 

```

auto lo                                                                         
iface lo inet loopback  

```

if it has others like

auto eth0
auto eth1
auto ra0
auto wlan0

try remming them out with a # and seeing if that helps

---

### Post by spotdog14 on 2007-10-24
I was hoping that when i saw an update for GDM in the update thing this morning that everything would be right with the world, but instead... a lot of the same old same old.

Just for the record, i have an Asus S5n laptop that is a 1.5Ghz P-M with 768mb of RAM and an 80gig HDD with Integrated Intel graphics.

---

### Post by Stochastic on 2007-10-24
> **mahousaru said:**
> Can those who have long boot times after the usplash has loaded check

/etc/network/interfaces 

and check that it only has 

```

auto lo                                                                         
iface lo inet loopback  

```

if it has others like

auto eth0
auto eth1
auto ra0
auto wlan0

try remming them out with a # and seeing if that helps


I had 'auto eth0' in my list, but after commenting it out and rebooting, GNOME wouldn't load.  It's now uncommented again.

And in your first line I think you may be misinterpreting the issue, it's not after the usplash loads that the hang or long load time is occurring, it's after loggin in through GDM and before GNOME fully loads.

---

### Post by #Reistlehr- on 2007-10-24
@mah: Nope already tried that no good.

I think it has more to it than the network manager. 

> 
[   47.736195] ppdev: user-space parallel port driver
[   47.933344] audit(1193248588.507:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5411 profile="/usr/sbin/cupsd"
[   53.170791] Failure registering capabilities with primary security module.
[   54.010138] Bluetooth: L2CAP ver 2.8
[   54.010143] Bluetooth: L2CAP socket layer initialized
[   54.015364] Bluetooth: RFCOMM socket layer initialized
[   54.015441] Bluetooth: RFCOMM TTY layer initialized
[   54.015443] Bluetooth: RFCOMM ver 1.8
[   80.867874] NET: Registered protocol family 17
[   84.613741] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  100.953988] wlan0: no IPv6 routers present


looking between, [   54.015443] Bluetooth: RFCOMM ver 1.8
[   80.867874] NET: Registered protocol family 17, which is when it seems to hang, but i have no way of proving it. I tried to disabled bluetooth in the sessions window, but it's being loaded somehwere else. Anyone know how to disable bluetooth so i can troubleshoot some more?

Perhaps it has something to do with the audit statement?

---

### Post by spotdog14 on 2007-10-24
> **#Reistlehr- said:**
> @mah: Nope already tried that no good.

I think it has more to it than the network manager. 



looking between, [   54.015443] Bluetooth: RFCOMM ver 1.8
[   80.867874] NET: Registered protocol family 17, which is when it seems to hang, but i have no way of proving it. I tried to disabled bluetooth in the sessions window, but it's being loaded somehwere else. Anyone know how to disable bluetooth so i can troubleshoot some more?

Perhaps it has something to do with the audit statement?

I seem to have the same problem with the Bluetooth loading, i dont even have bluetooth on my laptop, and i keep telling it to stop running but it seems to start itself again. That might be the issue at least on my system since i dont have bluetooth.

---

### Post by nickless on 2007-10-24
Well that is strange... Bluetooth is enabled on my machine as well and I know I have turned it off!
Also this HowTo seemed to have stripped some of the loading time after GDM login, but maybe I am mistaken, because I think this shouldn't have any inpact:
[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)

---

### Post by pasouza on 2007-10-24
Bluetooth is not the problem... I turned it off (on /etc/init.d) and still take about 70 seconds to load.  
```

[   34.088000] apm: BIOS not found.
[   38.480000] Failure registering capabilities with primary security module.
[  146.136000] NET: Registered protocol family 17
[  149.756000] ieee80211_crypt: registered algorithm 'WEP'
[  150.160000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  167.944000] eth1: no IPv6 routers present
```

---

### Post by phibit on 2007-10-24
How many of you are using AMD64? Seems like the Gutsy AMD64 is buggy...

---

### Post by Ricardo_V on 2007-10-24
> **phibit said:**
> How many of you are using AMD64? Seems like the Gutsy AMD64 is buggy...

I don't think it's an AMD related bug (right distro installed?) cause I have it too in my INTEL processor. I just started searching for this problem today and it's too bad I don't have my notebook here to try.

---

### Post by mysticmatrix on 2007-10-24
I was having same trouble on a upgraded version of Ubuntu 7.10 from 7.04.
[http://ubuntuforums.org/showthread.php?t=563530](http://ubuntuforums.org/showthread.php?t=563530)

However, then I made a fresh reinstall from CD and the problem disappeared.

Seems that reinstall is only option for us.

---

### Post by yostral on 2007-10-24
I've already done a fresh install. Problem is still here.

---

### Post by Nonno Bassotto on 2007-10-24
52 seconds for me... :(

---

### Post by spotdog14 on 2007-10-24
> **yostral said:**
> I've already done a fresh install. Problem is still here.

Yah i did a fresh install as well.

---

### Post by Stochastic on 2007-10-24
> **phibit said:**
> How many of you are using AMD64? Seems like the Gutsy AMD64 is buggy...

I have a Compaq AMD 64 turion single core with 2gig of ram running an upgraded UbuntuStudio Feisty i386 lowlatency to Gutsy i386 realtime and I'm getting roughly a 70 to 80 sec hang (one of the only major bugs I've encountered).

---

### Post by mahousaru on 2007-10-24
@Stochastic - Ah sorry my bad English, I meant those who eliminated the usplash as the problem (as that is a easier problem to solve)

To eliminate bluetooth as the cause how about blacklisting the bluetooth module?

I don't have bluetooth on my lappy, but the steps I would take would be

```

lsmod

```

You should get a list of all the modules loaded like
```

Module                  Size  Used by
nls_iso8859_1           5120  0 
vfat                   14080  0 
fat                    54300  1 vfat
iptable_filter          3968  0 
ip_tables              13924  1 iptable_filter
x_tables               16260  1 ip_tables

:
snip

```

Look for what looks like the bluetooth module, then add to the file /etc/modprobe.d/blacklist the following line

blacklist modulename

*Change modulename to what ever is bluetooth looking*

**Make sure you have a live cd available to reverse any changes if it goes horribly wrong**

---

### Post by malel on 2007-10-24
I have the exact same problem. It gets to the sign in panel and goes to sleep for a while before bringing up the rest of the OS.

---

### Post by #Reistlehr- on 2007-10-24
Hey, Everyone, can you post everything in your dmesg output?

> 
[   43.651031] eth0: no link during initialization.
[   47.791236] NET: Registered protocol family 10
[   47.791322] lo: Disabled Privacy Extensions
[   47.791491] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   47.791508] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.617770] lp: driver loaded but no devices found
[   48.681977] ppdev: user-space parallel port driver
[B][   48.892899] audit(1193283622.589:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5433 profile="/usr/sbin/cupsd"
[   52.863533] Failure registering capabilities with primary security module.[/B]
[   84.110622] NET: Registered protocol family 17
[   87.895355] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  106.584004] wlan0: no IPv6 routers present


I disabled bluetooth, and it still happend, but it seems to be happening around this point in bold above. Perhaps this is the problem? I want to see fi everyone has it

Edit:: This seems to be part of a different problem. Lol.. Shoulda staye on feisty

---

### Post by #Reistlehr- on 2007-10-25
Pointing something out in my last post:

requested_mask="a"

isnt the reqeusted mask supposed to be a permission? r, w, or x? is a supposed to be append?

anyone know how to turn off aaparmor or whatever it's called?

---

### Post by cowanh00 on 2007-10-25
> **#Reistlehr- said:**
> Hey, Everyone, can you post everything in your dmesg output from 40-100+?


The line you have highlighted in bold I have in my dmesg as well.

---

### Post by ePirate on 2007-10-25
> **nickless said:**
> Same problem  on my Dell Inspiron 9400 :(
Takes about 30-40 seconds to load after login.
Using Compiz Fusion on Gutsy

I have the EXACT same problem. My pc isn't exactly bad either

AMD athlon 64 x2 4200+
2gb ddr2 ram
250 GB sata baracuda 7200rpm hdd
radeon 9600 :(

---

### Post by oobuntoo on 2007-10-25
I've installed Gutsy on two different systems, one laptop and one desktop, and both are having the same problem. I don't even get the login splash on either one of them, just the nasty brown/orange background shows up for about a minute (which is too damn long for logging in), then gnome desktop appears. I'm going to do a fresh install with the final release cd to see if it fixes the problem.

---

### Post by nowshining on 2007-10-25
once u get into the desktop do the following open up a terminal and type

sudo killall nautilus

:)

if not then go thru ur home folder and remove useless junk and enable seeing of hidden files and go thru the .gonf file and remove useless junk or even better remove the whole .gonf folder and logout and backin and then re-set everything..

---

### Post by Nonno Bassotto on 2007-10-25
Why killing Nautilus should be useful when you have already done the login?

And why do you want people to remove all their settings instead of finding out where the problem is?

---

### Post by nowshining on 2007-10-25
> **Nonno Bassotto said:**
> Why killing Nautilus should be useful when you have already done the login?

And why do you want people to remove all their settings instead of finding out where the problem is?

oh and the folder is .gconf

:) oh the nautilus in Gutsy is a known problem to use 100 percent CPU at RANDOM yes RANDOM times.... also cleaning out the home folder if u did an upgrade - which I should of mentioned will help due to old prefs, etc.. :) and I did it and it worked wonders..

---

### Post by spotdog14 on 2007-10-25
> **#Reistlehr- said:**
> Hey, Everyone, can you post everything in your dmesg output from 40-100+?



I disabled bluetooth, and it still happend, but it seems to be happening around this point in bold above. Perhaps this is the problem? I want to see fi everyone has it

> [   25.260000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   25.260000] apm: overridden by ACPI.
[   25.516000] Failure registering capabilities with primary security module.
[   25.972000] Bluetooth: Core ver 2.11
[   25.972000] NET: Registered protocol family 31
[   25.972000] Bluetooth: HCI device and connection manager initialized
[   25.972000] Bluetooth: HCI socket layer initialized
[   26.028000] Bluetooth: L2CAP ver 2.8
[   26.028000] Bluetooth: L2CAP socket layer initialized
[   26.136000] Bluetooth: RFCOMM socket layer initialized
[   26.140000] Bluetooth: RFCOMM TTY layer initialized
[   26.140000] Bluetooth: RFCOMM ver 1.8
[   29.084000] [drm] Initialized drm 1.1.0 20060810
[   29.088000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 18
[   29.088000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   29.088000] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   62.488000] NET: Registered protocol family 17
[   62.988000] ieee80211_crypt: registered algorithm 'WEP'
[   72.364000] NET: Registered protocol family 10
[   72.364000] lo: Disabled Privacy Extensions
[   72.364000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   82.904000] eth1: no IPv6 routers present


Here is mine, i went back a little farther because of the stupid bluetooth.

---

### Post by Nonno Bassotto on 2007-10-25
Here you have mine:
```

[   40.523377] iTCO_vendor_support: vendor-support=0
[   40.554698] Linux agpgart interface v0.102 (c) Dave Jones
[   40.615078] input: PC Speaker as /class/input/input3
[   40.620326] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   40.626810] agpgart: Detected an Intel 915GM Chipset.
[   40.627773] agpgart: Detected 7932K stolen memory.
[   40.962408] agpgart: AGP aperture is 256M @ 0xc0000000
[   41.024124] ieee80211_crypt: registered algorithm 'NULL'
[   41.065114] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   41.065119] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   41.081895] Yenta: CardBus bridge found at 0000:02:06.0 [103c:30c4]
[   41.081926] Yenta: Using CSCINT to route CSC interrupts to PCI
[   41.081928] Yenta: Routing CardBus interrupts to PCI
[   41.081935] Yenta TI: socket 0000:02:06.0, mfunc 0x01be1b32, devctl 0x44
[   41.128741] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   41.128746] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   41.315852] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   41.315858] Socket status: 30000006
[   41.315862] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   41.315870] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   41.315874] cs: IO port probe 0x2000-0x2fff: clean.
[   41.316131] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd05fffff
[   41.316135] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[   41.316684] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 21
[   41.316749] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   41.394654] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   41.457711] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   41.462749] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   41.463594] parport_pc 00:02: reported by Plug and Play ACPI
[   41.464036] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   41.465665] pnp: Device 00:02 disabled.
[   41.522130] intel_rng: FWH not detected
[   41.607376] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   41.713680] ieee80211_crypt: registered algorithm 'WEP'
[   41.792402] ACPI: PCI Interrupt 0000:00:1e.2[B] -> GSI 17 (level, low) -> IRQ 17
[   41.792430] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   42.026774] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207
[   42.028563] cs: IO port probe 0x3e0-0x4ff: clean.
[   42.029299] cs: IO port probe 0x820-0x8ff: clean.
[   42.029891] cs: IO port probe 0xc00-0xcf7: clean.
[   42.030637] cs: IO port probe 0xa00-0xaff: clean.
[   42.102909] intel8x0_measure_ac97_clock: measured 50986 usecs
[   42.102915] intel8x0: clocking to 48000
[   42.324586] lp: driver loaded but no devices found
[   42.367021] Adding 682688k swap on /dev/sda5.  Priority:-1 extents:1 across:682688k
[   42.729425] EXT3 FS on sda3, internal journal
[   43.304079] NET: Registered protocol family 17
[   43.480139] kjournald starting.  Commit interval 5 seconds
[   43.480428] EXT3 FS on sda4, internal journal
[   43.480434] EXT3-fs: mounted filesystem with ordered data mode.
[   45.945218] input: Power Button (FF) as /class/input/input5
[   45.945478] ACPI: Power Button (FF) [PWRF]
[   45.947242] input: Sleep Button (CM) as /class/input/input6
[   45.947518] ACPI: Sleep Button (CM) [C1CE]
[   45.948225] input: Lid Switch as /class/input/input7
[   45.948450] ACPI: Lid Switch [C1CF]
[   46.069574] ACPI: Battery Slot [C15E] (battery present)
[   46.192007] ACPI: AC Adapter [C15D] (on-line)
[   46.208258] No dock devices found.
[   46.252950] ACPI: Video Device [C054] (multi-head: yes  rom: no  post: no)
[   46.732125] NET: Registered protocol family 10
[   46.732230] lo: Disabled Privacy Extensions
[   48.795637] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.829026] [drm] Initialized drm 1.1.0 20060810
[   52.838027] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 20
[   52.840828] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   52.906957] ppdev: user-space parallel port driver
[   53.499694] audit(1193324060.309:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4850 profile="/usr/sbin/cupsd"
[   54.373421] apm: BIOS not found.
[   54.649130] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   54.728985] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   54.745509] NFSD: starting 90-second grace period
[   56.735039] Failure registering capabilities with primary security module.
[   57.088184] eth1: no IPv6 routers present

```

---

### Post by nickless on 2007-10-25
> **nowshining said:**
> oh and the folder is .gconf

:) oh the nautilus in Gutsy is a known problem to use 100 percent CPU at RANDOM yes RANDOM times.... also cleaning out the home folder if u did an upgrade - which I should of mentioned will help due to old prefs, etc.. :) and I did it and it worked wonders..

Well our problem is not random and we have already tried logging in with newly created users and it didn't change a thing, so I guess this wouldn't work anyways...

---

### Post by #Reistlehr- on 2007-10-25
Ok. Here is where i stand.

I installed Gutsy, fresh clean install, on my two HP laptop computers, both AMD64. I then installed it on my desktop, clean, with the i386 kernel.

The desktop boots fine, the two laptops dont. The laptops have a message in their dmesg:
```
[   53.940709] Failure registering capabilities with primary security module.
```


The desktop does not have anything of that reference.

Also, not everyone has an audit on cupsd daemon which can be represented by this line:
```

[   48.061440] audit(1193327106.369:3):  type=1502 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5308 profile="/usr/sbin/cupsd"

```

I want to see the WHOLE dmesg's now. So keep em posting. I think i might be onto something.

---

### Post by spotdog14 on 2007-10-25
> **#Reistlehr- said:**
> Ok. Here is where i stand.

I installed Gutsy, fresh clean install, on my two HP laptop computers, both AMD64. I then installed it on my desktop, clean, with the i386 kernel.

The desktop boots fine, the two laptops dont. The laptops have a message in their dmesg:
```
[   53.940709] Failure registering capabilities with primary security module.
```


The desktop does not have anything of that reference.

Also, not everyone has an audit on cupsd daemon which can be represented by this line:
```

[   48.061440] audit(1193327106.369:3):  type=1502 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5308 profile="/usr/sbin/cupsd"

```

I want to see the WHOLE dmesg's now. So keep em posting. I think i might be onto something.

Here are is all of mine:

> [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002f740000 (usable)
[    0.000000]  BIOS-e820: 000000002f740000 - 000000002f750000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002f750000 - 000000002f800000 (ACPI NVS)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 759MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 194368) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   194368
[    0.000000]   HighMem    194368 ->   194368
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   194368
[    0.000000] On node 0 totalpages: 194368
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1486 pages used for memmap
[    0.000000]   Normal zone: 188786 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F5010 checksum 0
[    0.000000] ACPI: RSDP 000F5010, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 2F740000, 0030 (r1 A M I  OEMRSDT   1000525 MSFT       97)
[    0.000000] ACPI: FACP 2F740200, 0081 (r2 A M I  OEMFACP   1000525 MSFT       97)
[    0.000000] ACPI: DSDT 2F740360, 65FA (r1  0ABBD 0ABBD001        1 MSFT  2000001)
[    0.000000] ACPI: FACS 2F750000, 0040
[    0.000000] ACPI: APIC 2F740300, 0054 (r1 A M I  OEMAPIC   1000525 MSFT       97)
[    0.000000] ACPI: OEMB 2F750040, 004D (r1 A M I  OEMBIOS   1000525 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 2f800000:d0800000)
[    0.000000] Built 1 zonelists.  Total pages: 192850
[    0.000000] Kernel command line: root=UUID=deb9be79-8cb5-429d-a7d8-31865a8e581c ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 600.044 MHz processor.
[   13.420968] Console: colour VGA+ 80x25
[   13.421512] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   13.422453] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   13.467431] Memory: 759052k/777472k available (2015k kernel code, 17780k reserved, 916k data, 364k init, 0k highmem)
[   13.467456] virtual kernel memory layout:
[   13.467459]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   13.467463]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   13.467467]     vmalloc : 0xf0000000 - 0xff7fe000   ( 247 MB)
[   13.467471]     lowmem  : 0xc0000000 - 0xef740000   ( 759 MB)
[   13.467474]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   13.467478]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   13.467482]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   13.467491] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.467573] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   13.547578] Calibrating delay using timer specific routine.. 1201.21 BogoMIPS (lpj=2402431)
[   13.547630] Security Framework v1.0.0 initialized
[   13.547642] SELinux:  Disabled at boot.
[   13.547676] Mount-cache hash table entries: 512
[   13.547945] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 00000180 00000000 00000000
[   13.547973] CPU: L1 I cache: 32K, L1 D cache: 32K
[   13.547981] CPU: L2 cache: 2048K
[   13.547987] CPU: After all inits, caps: afe9fbff 00000000 00000000 00002040 00000180 00000000 00000000
[   13.548010] Compat vDSO mapped to ffffe000.
[   13.548034] Checking 'hlt' instruction... OK.
[   13.563819] SMP alternatives: switching to UP code
[   13.564214] Freeing SMP alternatives: 11k freed
[   13.564863] Early unpacking initramfs... done
[   14.514512] ACPI: Core revision 20070126
[   14.514682] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.536715] CPU0: Intel(R) Pentium(R) M processor 1.50GHz stepping 08
[   14.536766] Total of 1 processors activated (1201.21 BogoMIPS).
[   14.536908] ENABLING IO-APIC IRQs
[   14.537138] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   14.683324] Brought up 1 CPUs
[   14.683553] Booting paravirtualized kernel on bare hardware
[   14.683642] Time: 12:35:59  Date: 09/25/107
[   14.683685] NET: Registered protocol family 16
[   14.683842] EISA bus registered
[   14.683861] ACPI: bus type pci registered
[   14.684130] PCI: Using configuration type 1
[   14.684135] Setting up standard PCI resources
[   14.691669] ACPI: EC: Look up EC in DSDT
[   14.692055] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   14.728555] ACPI: Interpreter enabled
[   14.728562] ACPI: (supports S0 S1 S3 S4 S5)
[   14.728619] ACPI: Using IOAPIC for interrupt routing
[   14.744207] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   14.744320] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.744374] PCI: Probing PCI hardware (bus 00)
[   14.745021] PCI: Enabled i801 SMBus device
[   14.745032] PCI quirk: region e400-e47f claimed by ICH4 ACPI/GPIO/TCO
[   14.745041] PCI quirk: region ec00-ec3f claimed by ICH4 GPIO
[   14.745612] PCI: Transparent bridge - 0000:00:1e.0
[   14.745827] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.746144] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   14.755062] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 11 12)
[   14.755623] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 12) *0, disabled.
[   14.756138] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 12)
[   14.756648] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 7 12)
[   14.757157] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 12) *0, disabled.
[   14.757668] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 12) *0, disabled.
[   14.758179] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 12) *0, disabled.
[   14.758690] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 12)
[   14.759136] ACPI: Power Resource [GFAN] (off)
[   14.759151] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.759171] pnp: PnP ACPI init
[   14.759197] ACPI: bus type pnp registered
[   14.765879] pnp: PnP ACPI: found 12 devices
[   14.765885] ACPI: ACPI bus type pnp unregistered
[   14.765897] PnPBIOS: Disabled by ACPI PNP
[   14.765995] PCI: Using ACPI for IRQ routing
[   14.766002] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.766115] NET: Registered protocol family 8
[   14.766121] NET: Registered protocol family 20
[   14.766244] pnp: 00:08: ioport range 0xe800-0xe80f has been reserved
[   14.766254] pnp: 00:08: iomem range 0xfec00000-0xfecfffff has been reserved
[   14.766263] pnp: 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[   14.766276] pnp: 00:09: iomem range 0xffb80000-0xffbfffff has been reserved
[   14.766285] pnp: 00:09: iomem range 0xfff80000-0xffffffff has been reserved
[   14.766298] pnp: 00:0a: iomem range 0xffc00000-0xfff7ffff has been reserved
[   14.766312] pnp: 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   14.766320] pnp: 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[   14.766329] pnp: 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[   14.766338] pnp: 00:0b: iomem range 0x100000-0x2f7fffff could not be reserved
[   14.767234] Time: tsc clocksource has been installed.
[   14.797040] PCI: Bus 2, cardbus bridge: 0000:01:03.0
[   14.797046]   IO window: 0000c000-0000c0ff
[   14.797054]   IO window: 0000c400-0000c4ff
[   14.797063]   PREFETCH window: 34000000-37ffffff
[   14.797071]   MEM window: 38000000-3bffffff
[   14.797079] PCI: Bus 6, cardbus bridge: 0000:01:03.1
[   14.797085]   IO window: 0000cc00-0000ccff
[   14.797092]   IO window: 00001000-000010ff
[   14.797100]   PREFETCH window: 3c000000-3fffffff
[   14.797109]   MEM window: 40000000-43ffffff
[   14.797116] PCI: Bridge: 0000:00:1e.0
[   14.797122]   IO window: c000-cfff
[   14.797131]   MEM window: fe700000-fe8fffff
[   14.797140]   PREFETCH window: de500000-de6fffff
[   14.797158] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   14.797183] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 17 (level, low) -> IRQ 16
[   14.797207] ACPI: PCI Interrupt 0000:01:03.1[B] -> GSI 18 (level, low) -> IRQ 17
[   14.797236] NET: Registered protocol family 2
[   14.835267] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   14.835396] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   14.838270] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   14.839297] TCP: Hash tables configured (established 131072 bind 65536)
[   14.839304] TCP reno registered
[   14.851535] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   15.758110]  it is
[   16.717090] Freeing initrd memory: 7026k freed
[   16.717759] audit: initializing netlink socket (disabled)
[   16.717785] audit(1193315759.664:1): initialized
[   16.722639] VFS: Disk quotas dquot_6.5.1
[   16.722761] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.722960] io scheduler noop registered
[   16.722966] io scheduler anticipatory registered
[   16.722972] io scheduler deadline registered
[   16.723011] io scheduler cfq registered (default)
[   16.723041] Boot video device is 0000:00:02.0
[   16.723437] isapnp: Scanning for PnP cards...
[   17.077597] isapnp: No Plug & Play device found
[   17.131176] Real Time Clock Driver v1.12ac
[   17.131384] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.132639] ACPI: PCI Interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 16
[   17.132655] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[   17.133916] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.134406] input: Macintosh mouse button emulation as /class/input/input0
[   17.134583] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   17.137757] i8042.c: Detected active multiplexing controller, rev 1.1.
[   17.139046] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.139057] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   17.139064] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   17.139072] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   17.139079] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   17.139483] mice: PS/2 mouse device common for all mice
[   17.139851] EISA: Probing bus 0 at eisa.0
[   17.139864] Cannot allocate resource for EISA slot 1
[   17.139906] EISA: Detected 0 cards.
[   17.140103] TCP cubic registered
[   17.140130] NET: Registered protocol family 1
[   17.140177] Using IPI No-Shortcut mode
[   17.140517]   Magic number: 11:205:583
[   17.140590]   hash matches device ptyc1
[   17.141048] Freeing unused kernel memory: 364k freed
[   17.334101] input: AT Translated Set 2 keyboard as /class/input/input1
[   18.618236] AppArmor: AppArmor initialized<5>audit(1193315761.664:2):  type=1505 info="AppArmor initialized" pid=1193
[   18.638947] fuse init (API version 7.8)
[   18.652172] Failure registering capabilities with primary security module.
[   18.662941] ACPI: Transitioning device [FN00] to D3
[   18.662948] ACPI: Transitioning device [FN00] to D3
[   18.662957] ACPI: Fan [FN00] (off)
[   18.674803] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   18.674816] ACPI: Processor [CPU1] (supports 8 throttling states)
[   18.725787] ACPI: Thermal Zone [THRM] (29 C)
[   19.751318] usbcore: registered new interface driver usbfs
[   19.751366] usbcore: registered new interface driver hub
[   19.751413] usbcore: registered new device driver usb
[   19.753370] USB Universal Host Controller Interface driver v3.0
[   19.753485] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 18
[   19.753504] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   19.753513] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   19.753772] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   19.753809] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000d480
[   19.754048] usb usb1: configuration #1 chosen from 1 choice
[   19.754110] hub 1-0:1.0: USB hub found
[   19.754123] hub 1-0:1.0: 2 ports detected
[   19.857539] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   19.857561] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   19.857570] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   19.857620] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   19.857659] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[   19.857883] usb usb2: configuration #1 chosen from 1 choice
[   19.857954] hub 2-0:1.0: USB hub found
[   19.857969] hub 2-0:1.0: 2 ports detected
[   19.903216] SCSI subsystem initialized
[   19.917176] libata version 2.21 loaded.
[   19.961480] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 17
[   19.961500] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   19.961509] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   19.961570] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   19.961609] uhci_hcd 0000:00:1d.2: irq 17, io base 0x0000d880
[   19.961830] usb usb3: configuration #1 chosen from 1 choice
[   19.961894] hub 3-0:1.0: USB hub found
[   19.961908] hub 3-0:1.0: 2 ports detected
[   20.066593] ata_piix 0000:00:1f.1: version 2.11
[   20.066617] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   20.066629] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 17
[   20.066687] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   20.066813] scsi0 : ata_piix
[   20.066898] scsi1 : ata_piix
[   20.067161] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   20.067170] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   20.229615] ata1.00: ATA-6: HTS424040M9AT00, MA2OA71A, max UDMA/100
[   20.229625] ata1.00: 78140160 sectors, multi 16: LBA48 
[   20.245614] ata1.00: configured for UDMA/100
[   20.406900] scsi 0:0:0:0: Direct-Access     ATA      HTS424040M9AT00  MA2O PQ: 0 ANSI: 5
[   20.411525] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20
[   20.411548] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   20.411557] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   20.411615] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   20.411670] ehci_hcd 0000:00:1d.7: debug port 1
[   20.411681] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   20.411704] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfebff800
[   20.415578] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.415766] usb usb4: configuration #1 chosen from 1 choice
[   20.415845] hub 4-0:1.0: USB hub found
[   20.415860] hub 4-0:1.0: 6 ports detected
[   20.509835] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   20.580475] 8139cp 0000:01:04.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   20.580487] 8139cp 0000:01:04.0: Try the "8139too" driver instead.
[   20.591150] ACPI: PCI Interrupt 0000:01:03.2[C] -> GSI 16 (level, low) -> IRQ 18
[   20.644080] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[18]  MMIO=[fe8ff000-fe8ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   20.657544] 8139too Fast Ethernet driver 0.9.28
[   20.657610] ACPI: PCI Interrupt 0000:01:04.0[A] -> GSI 16 (level, low) -> IRQ 18
[   20.658003] eth0: RealTek RTL8139 at 0xf0054800, 00:11:d8:8b:f2:60, IRQ 18
[   20.658010] eth0:  Identified 8139 chip type 'RTL-8101'
[   20.776821] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   20.776850] sd 0:0:0:0: [sda] Write Protect is off
[   20.776858] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.776895] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.777003] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   20.777026] sd 0:0:0:0: [sda] Write Protect is off
[   20.777033] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.777068] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.777080]  sda: sda1 sda2 sda3 sda4
[   20.817203] sd 0:0:0:0: [sda] Attached SCSI disk
[   20.839228] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.316000] Marking TSC unstable due to: possible TSC halt in C2.
[    7.320000] Time: acpi_pm clocksource has been installed.
[    7.732000] Attempting manual resume
[    7.732000] swsusp: Resume From Partition 8:4
[    7.732000] PM: Checking swsusp image.
[    7.732000] PM: Resume from disk failed.
[    7.764000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    7.764000] EXT3-fs: write access will be enabled during recovery.
[    8.320000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800032b97d2]
[   13.276000] kjournald starting.  Commit interval 5 seconds
[   13.276000] EXT3-fs: sda1: orphan cleanup on readonly fs
[   13.276000] ext3_orphan_cleanup: deleting unreferenced inode 36165
[   13.276000] ext3_orphan_cleanup: deleting unreferenced inode 36161
[   13.276000] ext3_orphan_cleanup: deleting unreferenced inode 36159
[   13.328000] ext3_orphan_cleanup: deleting unreferenced inode 36157
[   13.420000] ext3_orphan_cleanup: deleting unreferenced inode 36152
[   13.420000] ext3_orphan_cleanup: deleting unreferenced inode 36148
[   13.420000] ext3_orphan_cleanup: deleting unreferenced inode 36146
[   13.420000] ext3_orphan_cleanup: deleting unreferenced inode 36144
[   13.420000] ext3_orphan_cleanup: deleting unreferenced inode 36142
[   13.536000] ext3_orphan_cleanup: deleting unreferenced inode 36139
[   13.540000] ext3_orphan_cleanup: deleting unreferenced inode 36137
[   13.540000] ext3_orphan_cleanup: deleting unreferenced inode 36135
[   13.540000] ext3_orphan_cleanup: deleting unreferenced inode 36131
[   13.552000] ext3_orphan_cleanup: deleting unreferenced inode 936018
[   13.552000] ext3_orphan_cleanup: deleting unreferenced inode 935965
[   13.552000] ext3_orphan_cleanup: deleting unreferenced inode 32724
[   13.556000] EXT3-fs: sda1: 16 orphan inodes deleted
[   13.556000] EXT3-fs: recovery complete.
[   13.564000] EXT3-fs: mounted filesystem with ordered data mode.
[   22.192000] Clocksource tsc unstable (delta = -122790734 ns)
[   25.352000] Linux agpgart interface v0.102 (c) Dave Jones
[   25.456000] agpgart: Detected an Intel 855GM Chipset.
[   25.456000] agpgart: Detected 8060K stolen memory.
[   25.468000] agpgart: AGP aperture is 128M @ 0xf0000000
[   27.756000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   27.772000] iTCO_vendor_support: vendor-support=0
[   27.804000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   27.804000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0xe460)
[   27.804000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   27.848000] intel_rng: FWH not detected
[   27.956000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.576000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x116eb1, caps: 0xa04713/0x0
[   28.612000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   29.616000] input: PC Speaker as /class/input/input3
[   29.816000] Yenta: CardBus bridge found at 0000:01:03.0 [1043:1824]
[   29.944000] Yenta: ISA IRQ mask 0x04b8, PCI irq 16
[   29.944000] Socket status: 30000006
[   29.944000] Yenta: Raising subordinate bus# of parent bus (#01) from #01 to #05
[   29.944000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[   29.944000] cs: IO port probe 0xc000-0xcfff: clean.
[   29.944000] pcmcia: parent PCI bridge Memory window: 0xfe700000 - 0xfe8fffff
[   29.944000] pcmcia: parent PCI bridge Memory window: 0xde500000 - 0xde6fffff
[   29.944000] Yenta: CardBus bridge found at 0000:01:03.1 [1043:1824]
[   30.072000] Yenta: ISA IRQ mask 0x04b8, PCI irq 17
[   30.072000] Socket status: 30000006
[   30.072000] Yenta: Raising subordinate bus# of parent bus (#01) from #05 to #09
[   30.072000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[   30.072000] cs: IO port probe 0xc000-0xcfff: clean.
[   30.072000] pcmcia: parent PCI bridge Memory window: 0xfe700000 - 0xfe8fffff
[   30.072000] pcmcia: parent PCI bridge Memory window: 0xde500000 - 0xde6fffff
[   30.076000] ieee80211_crypt: registered algorithm 'NULL'
[   30.080000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   30.080000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   30.108000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   30.108000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   30.108000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 18 (level, low) -> IRQ 17
[   30.108000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   30.500000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   31.044000] cs: IO port probe 0x100-0x3af: clean.
[   31.044000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   31.044000] cs: IO port probe 0x820-0x8ff: clean.
[   31.048000] cs: IO port probe 0xc00-0xcf7: clean.
[   31.048000] cs: IO port probe 0xa00-0xaff: clean.
[   31.048000] cs: IO port probe 0x100-0x3af: clean.
[   31.052000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   31.052000] cs: IO port probe 0x820-0x8ff: clean.
[   31.052000] cs: IO port probe 0xc00-0xcf7: clean.
[   31.052000] cs: IO port probe 0xa00-0xaff: clean.
[   31.128000] PCI: Enabling device 0000:00:1f.5 (0005 -> 0007)
[   31.128000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 16
[   31.128000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   31.544000] intel8x0_measure_ac97_clock: measured 54916 usecs
[   31.544000] intel8x0: clocking to 48000
[   32.100000] lp: driver loaded but no devices found
[   32.212000] Adding 1951856k swap on /dev/sda4.  Priority:-1 extents:1 across:1951856k
[   32.780000] EXT3 FS on sda1, internal journal
[   36.876000] kjournald starting.  Commit interval 5 seconds
[   36.880000] EXT3 FS on sda3, internal journal
[   36.880000] EXT3-fs: mounted filesystem with ordered data mode.
[   39.012000] No dock devices found.
[   39.156000] input: Power Button (FF) as /class/input/input4
[   39.156000] ACPI: Power Button (FF) [PWRF]
[   39.200000] input: Sleep Button (CM) as /class/input/input5
[   39.200000] ACPI: Sleep Button (CM) [SLPB]
[   39.224000] input: Lid Switch as /class/input/input6
[   39.224000] ACPI: Lid Switch [LID]
[   39.452000] ACPI: AC Adapter [AC0] (off-line)
[   39.560000] Asus Laptop ACPI Extras version 0.30
[   39.600000]   S5N model detected, supported
[   39.680000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   39.744000] ACPI: Battery Slot [BAT0] (battery present)
[   41.144000] ppdev: user-space parallel port driver
[   41.320000] eth0: link down
[   41.660000] audit(1193330199.415:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4555 profile="/usr/sbin/cupsd"
[   41.724000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   41.724000] apm: overridden by ACPI.
[   41.936000] Failure registering capabilities with primary security module.
[   42.208000] Bluetooth: Core ver 2.11
[   42.208000] NET: Registered protocol family 31
[   42.208000] Bluetooth: HCI device and connection manager initialized
[   42.208000] Bluetooth: HCI socket layer initialized
[   42.264000] Bluetooth: L2CAP ver 2.8
[   42.264000] Bluetooth: L2CAP socket layer initialized
[   42.360000] Bluetooth: RFCOMM socket layer initialized
[   42.360000] Bluetooth: RFCOMM TTY layer initialized
[   42.360000] Bluetooth: RFCOMM ver 1.8
[   45.448000] [drm] Initialized drm 1.1.0 20060810
[   45.448000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 18
[   45.452000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   45.452000] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   75.776000] NET: Registered protocol family 17
[   95.448000] NET: Registered protocol family 10
[   95.448000] lo: Disabled Privacy Extensions
[   95.448000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  107.764000] eth1: no IPv6 routers present


---

### Post by nickless on 2007-10-25
Better use nopaste or something simliar :D
here is mine:
[http://nopaste.info/ed09779502.html](http://nopaste.info/ed09779502.html)

---

### Post by Nonno Bassotto on 2007-10-25
I noticed I have something called "User folders update" in my session, which loads xdg-user-dirs-gtk-update. What is it for?

---

### Post by mgmiller on 2007-10-25
It takes me 45 seconds to go from login to my desktop, used to take about 15 seconds in Feisty.

```
Hey, Everyone, can you post everything in your dmesg output from 40-100+?

```
 You later asked for the whole dmesg, so here it is:

```
marty@tux:~$ dmesg
[    0.000000] Linux version 2.6.22-14-386 (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 Sun Oct 14 22:36:54 GMT 2007 (Ubuntu 2.6.22-14.46-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffc0000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 524208) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524208
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524208
[    0.000000] On node 0 totalpages: 524208
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292529 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FA7C0 checksum 0
[    0.000000] ACPI: RSDP 000FA7C0, 0021 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 7FFB0100, 003C (r1 A M I  OEMXSDT   6000530 MSFT       97)
[    0.000000] ACPI: FACP 7FFB0290, 00F4 (r3 A M I  OEMFACP   6000530 MSFT       97)
[    0.000000] ACPI: DSDT 7FFB03F0, 3A3E (r1  A0036 A0036001        1 MSFT  100000D)
[    0.000000] ACPI: FACS 7FFC0000, 0040
[    0.000000] ACPI: APIC 7FFB0390, 0052 (r1 A M I  OEMAPIC   6000530 MSFT       97)
[    0.000000] ACPI: OEMB 7FFC0040, 003F (r1 A M I  OEMBIOS   6000530 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7f780000)
[    0.000000] Built 1 zonelists.  Total pages: 520113
[    0.000000] Kernel command line: root=UUID=5a835667-ffe7-484e-8788-88159f8ee87b ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2004.739 MHz processor.
[   37.159656] Console: colour VGA+ 80x25
[   37.160051] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   37.160462] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   37.210575] Memory: 2067340k/2096832k available (1929k kernel code, 28232k reserved, 877k data, 348k init, 1179328k highmem)
[   37.210584] virtual kernel memory layout:
[   37.210585]     fixmap  : 0xfffa8000 - 0xfffff000   ( 348 kB)
[   37.210587]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   37.210588]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   37.210589]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   37.210590]       .init : 0xc03c0000 - 0xc0417000   ( 348 kB)
[   37.210591]       .data : 0xc02e25d5 - 0xc03bda04   ( 877 kB)
[   37.210592]       .text : 0xc0100000 - 0xc02e25d5   (1929 kB)
[   37.210595] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   37.210641] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   37.290541] Calibrating delay using timer specific routine.. 4013.81 BogoMIPS (lpj=8027639)
[   37.290566] Security Framework v1.0.0 initialized
[   37.290572] SELinux:  Disabled at boot.
[   37.290578] Mount-cache hash table entries: 512
[   37.290673] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   37.290679] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   37.290682] CPU: L2 Cache: 512K (64 bytes/line)
[   37.290684] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   37.290693] Compat vDSO mapped to ffffe000.
[   37.290702] CPU: AMD Athlon(tm) 64 Processor 3200+ stepping 00
[   37.290707] Checking 'hlt' instruction... OK.
[   37.307027] Early unpacking initramfs... done
[   37.605447] ACPI: Core revision 20070126
[   37.605494] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   37.607584] ENABLING IO-APIC IRQs
[   37.607899] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   37.753870] Booting paravirtualized kernel on bare hardware
[   37.753952] Time: 23:31:21  Date: 09/24/107
[   37.753968] NET: Registered protocol family 16
[   37.754026] EISA bus registered
[   37.754042] ACPI: bus type pci registered
[   37.754673] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   37.754675] PCI: Using configuration type 1
[   37.754677] Setting up standard PCI resources
[   37.761723] ACPI: EC: Look up EC in DSDT
[   37.764793] ACPI: Interpreter enabled
[   37.764795] ACPI: (supports S0 S1 S3 S4 S5)
[   37.764808] ACPI: Using IOAPIC for interrupt routing
[   37.769889] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   37.769897] PCI: Probing PCI hardware (bus 00)
[   37.770660] PCI: enabled onboard AC97/MC97 devices
[   37.770884] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   37.778471] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 14 15)
[   37.778552] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 *11 14 15)
[   37.778631] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 14 15)
[   37.778709] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *7 10 11 14 15)
[   37.778787] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   37.778866] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   37.778945] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   37.779024] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   37.779081] Linux Plug and Play Support v0.97 (c) Adam Belay
[   37.779089] pnp: PnP ACPI init
[   37.779095] ACPI: bus type pnp registered
[   37.781493] pnp: PnP ACPI: found 11 devices
[   37.781495] ACPI: ACPI bus type pnp unregistered
[   37.781498] PnPBIOS: Disabled by ACPI PNP
[   37.781530] PCI: Using ACPI for IRQ routing
[   37.781532] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   37.786775] NET: Registered protocol family 8
[   37.786777] NET: Registered protocol family 20
[   37.786820] pnp: 00:05: ioport range 0x680-0x6ff has been reserved
[   37.786823] pnp: 00:05: ioport range 0x290-0x297 has been reserved
[   37.786828] pnp: 00:07: iomem range 0xfec00000-0xfec00fff has been reserved
[   37.786831] pnp: 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[   37.786834] pnp: 00:07: iomem range 0xfff80000-0xffffffff could not be reserved
[   37.786839] pnp: 00:0a: iomem range 0x0-0x9ffff could not be reserved
[   37.786841] pnp: 00:0a: iomem range 0xc0000-0xdffff could not be reserved
[   37.786844] pnp: 00:0a: iomem range 0xe0000-0xfffff could not be reserved
[   37.786846] pnp: 00:0a: iomem range 0x100000-0x7ffeffff could not be reserved
[   37.789763] Time: tsc clocksource has been installed.
[   37.816984] PCI: Bridge: 0000:00:01.0
[   37.816985]   IO window: disabled.
[   37.816989]   MEM window: f9f00000-fbffffff
[   37.816992]   PREFETCH window: e0000000-f8ffffff
[   37.817006] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   37.817017] NET: Registered protocol family 2
[   37.853677] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   37.854049] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   37.854982] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   37.855240] TCP: Hash tables configured (established 131072 bind 65536)
[   37.855243] TCP reno registered
[   37.865754] checking if image is initramfs... it is
[   38.316941] Switched to high resolution mode on CPU 0
[   38.451614] Freeing initrd memory: 7465k freed
[   38.451889] audit: initializing netlink socket (disabled)
[   38.451902] audit(1193268681.132:1): initialized
[   38.451944] highmem bounce pool size: 64 pages
[   38.453134] VFS: Disk quotas dquot_6.5.1
[   38.453145] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   38.453216] io scheduler noop registered
[   38.453217] io scheduler anticipatory registered
[   38.453219] io scheduler deadline registered
[   38.453232] io scheduler cfq registered (default)
[   38.453243] PCI: VIA PCI bridge detected. Disabling DAC.
[   46.439848] 0000:00:10.4 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   46.439962] Boot video device is 0000:01:00.0
[   46.440068] isapnp: Scanning for PnP cards...
[   46.793477] isapnp: No Plug & Play device found
[   46.809813] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   46.809894] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   46.810013] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   46.810421] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   46.810614] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   46.811040] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   46.811188] input: Macintosh mouse button emulation as /class/input/input0
[   46.811275] PNP: No PS/2 controller found. Probing ports directly.
[   46.811648] serio: i8042 KBD port at 0x60,0x64 irq 1
[   46.811651] serio: i8042 AUX port at 0x60,0x64 irq 12
[   46.811746] mice: PS/2 mouse device common for all mice
[   46.811819] EISA: Probing bus 0 at eisa.0
[   46.811827] Cannot allocate resource for EISA slot 1
[   46.811852] EISA: Detected 0 cards.
[   46.811984] TCP cubic registered
[   46.812000] NET: Registered protocol family 1
[   46.812019] Using IPI Shortcut mode
[   46.812179]   Magic number: 11:746:555
[   46.812254]   hash matches device ptya1
[   46.812315]   hash matches device PNP0C0F:06
[   46.812574] Freeing unused kernel memory: 348k freed
[   48.009658] fuse init (API version 7.8)
[   48.014982] Capability LSM initialized
[   48.035852] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
[   48.049534] md: linear personality registered for level -1
[   48.053555] md: multipath personality registered for level -4
[   48.057408] md: raid0 personality registered for level 0
[   48.061770] md: raid1 personality registered for level 1
[   48.065566] raid5: automatically using best checksumming function: pIII_sse
[   48.085205]    pIII_sse  :  6308.000 MB/sec
[   48.085207] raid5: using function: pIII_sse (6308.000 MB/sec)
[   48.153160] raid6: int32x1    854 MB/s
[   48.221024] raid6: int32x2    872 MB/s
[   48.288910] raid6: int32x4    735 MB/s
[   48.356885] raid6: int32x8    531 MB/s
[   48.424677] raid6: mmxx1     1615 MB/s
[   48.492555] raid6: mmxx2     2968 MB/s
[   48.560449] raid6: sse1x1    1501 MB/s
[   48.628336] raid6: sse1x2    2489 MB/s
[   48.696225] raid6: sse2x1    2521 MB/s
[   48.764129] raid6: sse2x2    3373 MB/s
[   48.764130] raid6: using algorithm sse2x2 (3373 MB/s)
[   48.764133] md: raid6 personality registered for level 6
[   48.764135] md: raid5 personality registered for level 5
[   48.764136] md: raid4 personality registered for level 4
[   48.785178] md: raid10 personality registered for level 10
[   49.285994] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 16 (level, low) -> IRQ 16
[   49.352121] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[f9500000-f95007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   49.362353] SCSI subsystem initialized
[   49.366298] libata version 2.21 loaded.
[   49.367128] sata_promise 0000:00:08.0: version 2.07
[   49.367167] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 18 (level, low) -> IRQ 17
[   49.367177] sata_promise 0000:00:08.0: PATA port found
[   49.381815] usbcore: registered new interface driver usbfs
[   49.381834] usbcore: registered new interface driver hub
[   49.381848] usbcore: registered new device driver usb
[   49.382389] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   49.391627] scsi0 : sata_promise
[   49.391668] scsi1 : sata_promise
[   49.391688] scsi2 : sata_promise
[   49.391709] ata1: SATA max UDMA/133 cmd 0xf8838200 ctl 0xf8838238 bmdma 0x00000000 irq 17
[   49.391713] ata2: SATA max UDMA/133 cmd 0xf8838280 ctl 0xf88382b8 bmdma 0x00000000 irq 17
[   49.391716] ata3: PATA max UDMA/133 cmd 0xf8838300 ctl 0xf8838338 bmdma 0x00000000 irq 17
[   49.432830] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   49.432835] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   49.436999] USB Universal Host Controller Interface driver v3.0
[   49.858382] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   49.866755] ata1.00: ATA-7: ST3250823AS, 3.03, max UDMA/133
[   49.866758] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   49.882711] ata1.00: configured for UDMA/133
[   50.349592] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   50.357953] ata2.00: ATA-7: ST3250823AS, 3.03, max UDMA/133
[   50.357955] ata2.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   50.373931] ata2.00: configured for UDMA/133
[   50.529393] scsi 0:0:0:0: Direct-Access     ATA      ST3250823AS      3.03 PQ: 0 ANSI: 5
[   50.529683] scsi 1:0:0:0: Direct-Access     ATA      ST3250823AS      3.03 PQ: 0 ANSI: 5
[   50.529969] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 18
[   50.530001] skge 1.11 addr 0xf9900000 irq 18 chip Yukon-Lite rev 9
[   50.530173] skge eth0: addr 00:11:d8:f3:78:13
[   50.530247] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 18 (level, low) -> IRQ 17
[   50.530255] ohci_hcd 0000:00:0d.0: OHCI Host Controller
[   50.530485] ohci_hcd 0000:00:0d.0: new USB bus registered, assigned bus number 1
[   50.530496] ohci_hcd 0000:00:0d.0: irq 17, io mem 0xf9a00000
[   50.541315] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   50.541329] sd 0:0:0:0: [sda] Write Protect is off
[   50.541332] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   50.541343] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   50.541386] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   50.541392] sd 0:0:0:0: [sda] Write Protect is off
[   50.541395] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   50.541404] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   50.541408]  sda: sda1 sda2 <<6>usb usb1: configuration #1 chosen from 1 choice
[   50.615059] hub 1-0:1.0: USB hub found
[   50.615068] hub 1-0:1.0: 3 ports detected
[   50.615386]  sda5 >
[   50.615778] sd 0:0:0:0: [sda] Attached SCSI disk
[   50.615908] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   50.615917] sd 1:0:0:0: [sdb] Write Protect is off
[   50.615919] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   50.615930] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   50.615963] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   50.615969] sd 1:0:0:0: [sdb] Write Protect is off
[   50.615971] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   50.615981] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   50.615983]  sdb:<7>ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d8000032b607]
[   50.637562]  sdb1
[   50.637805] sd 1:0:0:0: [sdb] Attached SCSI disk
[   50.641022] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   50.641038] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   50.717096] ACPI: PCI Interrupt 0000:00:0d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   50.717111] ohci_hcd 0000:00:0d.1: OHCI Host Controller
[   50.717130] ohci_hcd 0000:00:0d.1: new USB bus registered, assigned bus number 2
[   50.717148] ohci_hcd 0000:00:0d.1: irq 19, io mem 0xf9b00000
[   50.802756] usb usb2: configuration #1 chosen from 1 choice
[   50.802777] hub 2-0:1.0: USB hub found
[   50.802785] hub 2-0:1.0: 2 ports detected
[   50.894156] EXT3-fs: INFO: recovery required on readonly filesystem.
[   50.894159] EXT3-fs: write access will be enabled during recovery.
[   50.904851] ACPI: PCI Interrupt 0000:00:0d.2[C] -> GSI 16 (level, low) -> IRQ 16
[   50.904863] ehci_hcd 0000:00:0d.2: EHCI Host Controller
[   50.904885] ehci_hcd 0000:00:0d.2: new USB bus registered, assigned bus number 3
[   50.928674] ehci_hcd 0000:00:0d.2: irq 16, io mem 0xf9c00000
[   50.928683] ehci_hcd 0000:00:0d.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   50.928767] usb usb3: configuration #1 chosen from 1 choice
[   50.928787] hub 3-0:1.0: USB hub found
[   50.928795] hub 3-0:1.0: 5 ports detected
[   51.032608] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 20
[   51.032632] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   51.032653] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 4
[   51.032709] ehci_hcd 0000:00:10.4: irq 20, io mem 0xf9e00000
[   51.032722] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   51.032790] usb usb4: configuration #1 chosen from 1 choice
[   51.032809] hub 4-0:1.0: USB hub found
[   51.032816] hub 4-0:1.0: 8 ports detected
[   51.136507] sata_via 0000:00:0f.0: version 2.2
[   51.136540] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 21
[   51.136599] sata_via 0000:00:0f.0: routed to hard irq line 11
[   51.136664] scsi3 : sata_via
[   51.136698] scsi4 : sata_via
[   51.136715] ata4: SATA max UDMA/133 cmd 0x0001d000 ctl 0x0001c802 bmdma 0x0001b800 irq 21
[   51.136718] ata5: SATA max UDMA/133 cmd 0x0001c400 ctl 0x0001c002 bmdma 0x0001b808 irq 21
[   51.304041] usb 3-4: new high speed USB device using ehci_hcd and address 2
[   51.339982] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   51.444248] usb 3-4: configuration #1 chosen from 1 choice
[   51.551643] ata5: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   51.562306] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   51.562322] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 21
[   51.562331] VP_IDE: chipset revision 6
[   51.562333] VP_IDE: not 100% native mode: will probe irqs later
[   51.562343] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   51.562350]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[   51.562361]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[   51.562367] Probing IDE interface ide0...
[   51.867137] usb 4-3: new high speed USB device using ehci_hcd and address 3
[   52.018008] usb 4-3: configuration #1 chosen from 1 choice
[   52.087019] hda: TSSTcorpCD/DVDW TS-H552U, ATAPI CD/DVD-ROM drive
[   52.170520] kjournald starting.  Commit interval 5 seconds
[   52.170531] EXT3-fs: sda1: orphan cleanup on readonly fs
[   52.193677] ext3_orphan_cleanup: deleting unreferenced inode 21758069
[   52.217843] ext3_orphan_cleanup: deleting unreferenced inode 807491
[   52.239434] ext3_orphan_cleanup: deleting unreferenced inode 16760925
[   52.259490] ext3_orphan_cleanup: deleting unreferenced inode 17334275
[   52.265964] ext3_orphan_cleanup: deleting unreferenced inode 17334274
[   52.273377] EXT3-fs: sda1: 5 orphan inodes deleted
[   52.273379] EXT3-fs: recovery complete.
[   52.374998] EXT3-fs: mounted filesystem with ordered data mode.
[   52.442219] usb 4-7: new high speed USB device using ehci_hcd and address 5
[   52.576461] usb 4-7: configuration #1 chosen from 1 choice
[   52.757967] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   52.758256] Probing IDE interface ide1...
[   53.620411] hdc: ASUS DVD-E616P3, ATAPI CD/DVD-ROM drive
[   53.956445] ide1 at 0x170-0x177,0x376 on irq 15
[   53.957059] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 20
[   53.957070] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   53.957093] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 5
[   53.957114] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000d400
[   53.957203] usb usb5: configuration #1 chosen from 1 choice
[   53.957226] hub 5-0:1.0: USB hub found
[   53.957232] hub 5-0:1.0: 2 ports detected
[   54.059690] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 20
[   54.059697] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   54.059713] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 6
[   54.059730] uhci_hcd 0000:00:10.1: irq 20, io base 0x0000d800
[   54.059807] usb usb6: configuration #1 chosen from 1 choice
[   54.059824] hub 6-0:1.0: USB hub found
[   54.059829] hub 6-0:1.0: 2 ports detected
[   54.163499] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 20
[   54.163505] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   54.163518] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 7
[   54.163535] uhci_hcd 0000:00:10.2: irq 20, io base 0x0000e000
[   54.163607] usb usb7: configuration #1 chosen from 1 choice
[   54.163624] hub 7-0:1.0: USB hub found
[   54.163629] hub 7-0:1.0: 2 ports detected
[   54.267331] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 20
[   54.267336] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   54.267351] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 8
[   54.267368] uhci_hcd 0000:00:10.3: irq 20, io base 0x0000e400
[   54.267441] usb usb8: configuration #1 chosen from 1 choice
[   54.267458] hub 8-0:1.0: USB hub found
[   54.267463] hub 8-0:1.0: 2 ports detected
[   54.299230] usb 5-1: new low speed USB device using uhci_hcd and address 2
[   54.481267] usb 5-1: configuration #1 chosen from 1 choice
[   54.978141] usb 6-2: new low speed USB device using uhci_hcd and address 2
[   55.259656] usb 6-2: configuration #1 chosen from 1 choice
[   63.994682] skge eth0: enabling interface
[   65.017041] NET: Registered protocol family 10
[   65.017128] lo: Disabled Privacy Extensions
[   65.017174] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   65.424190] Linux agpgart interface v0.102 (c) Dave Jones
[   65.425299] agpgart: Detected AGP bridge 0
[   65.429479] agpgart: AGP aperture is 128M @ 0xd8000000
[   65.660445] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[   65.660799] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   65.930646] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   66.029642] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   66.496892] Real Time Clock Driver v1.12ac
[   66.519203] input: PC Speaker as /class/input/input1
[   66.544455] nvidia: module license 'NVIDIA' taints kernel.
[   66.940604] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   66.940819] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   67.089189] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[   67.089198] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 22
[   67.354399] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   67.354407] Uniform CD-ROM driver Revision: 3.20
[   67.356075] hdc: ATAPI 48X DVD-ROM drive, 512kB Cache<4>hdc: drive side 80-wire cable detection failed, limiting max speed to UDMA33
[   67.356080] 
[   67.394252] usbcore: registered new interface driver hiddev
[   67.408962] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /class/input/input2
[   67.409006] input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.0-1
[   67.465453] input: Chicony Saitek Eclipse II Keyboard as /class/input/input3
[   67.465493] input: USB HID v1.11 Keyboard [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:10.1-2
[   67.632270] input: Chicony Saitek Eclipse II Keyboard as /class/input/input4
[   67.632337] input,hiddev96: USB HID v1.11 Device [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:10.1-2
[   67.632351] usbcore: registered new interface driver usbhid
[   67.632354] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   67.632738] usbcore: registered new interface driver xpad
[   67.632741] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   67.673017] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1088
[   67.673037] usbcore: registered new interface driver usblp
[   67.673040] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   67.673413] usbcore: registered new interface driver libusual
[   67.837498] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   68.142723] Initializing USB Mass Storage driver...
[   68.142796] scsi5 : SCSI emulation for USB Mass Storage devices
[   68.142839] usb-storage: device found at 5
[   68.142841] usb-storage: waiting for device to settle before scanning
[   68.142853] usbcore: registered new interface driver usb-storage
[   68.142855] USB Mass Storage support registered.
[   68.340892] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[   68.340902] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   68.341027] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
[   68.341161] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   69.553322] lp: driver loaded but no devices found
[   69.821260] w83627hf: Found W83627THF chip at 0x290
[   69.997215] Adding 2650684k swap on /dev/sda5.  Priority:-1 extents:1 across:2650684k
[   70.102201] EXT3 FS on sda1, internal journal
[   73.133132] usb-storage: device scan complete
[   73.134506] scsi 5:0:0:0: Direct-Access     Generic                CF 1.4F PQ: 0 ANSI: 0 CCS
[   73.135745] scsi 5:0:0:1: Direct-Access     Generic                MS 1.4F PQ: 0 ANSI: 0 CCS
[   73.136997] scsi 5:0:0:2: Direct-Access     Generic            MMC/SD 1.4F PQ: 0 ANSI: 0 CCS
[   73.138241] scsi 5:0:0:3: Direct-Access     Generic                SM 1.4F PQ: 0 ANSI: 0 CCS
[   73.139273] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[   73.139304] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   73.140267] sd 5:0:0:1: [sdd] Attached SCSI removable disk
[   73.140297] sd 5:0:0:1: Attached scsi generic sg3 type 0
[   73.141266] sd 5:0:0:2: [sde] Attached SCSI removable disk
[   73.141294] sd 5:0:0:2: Attached scsi generic sg4 type 0
[   73.142262] sd 5:0:0:3: [sdf] Attached SCSI removable disk
[   73.142290] sd 5:0:0:3: Attached scsi generic sg5 type 0
[   74.878166] kjournald starting.  Commit interval 5 seconds
[   74.878180] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   74.881560] EXT3 FS on sdb1, internal journal
[   74.881562] EXT3-fs: recovery complete.
[   74.881676] EXT3-fs: mounted filesystem with ordered data mode.
[   75.928497] eth0: no IPv6 routers present
[   77.969503] No dock devices found.
[   78.036150] input: Power Button (FF) as /class/input/input5
[   78.040082] ACPI: Power Button (FF) [PWRF]
[   78.065096] input: Power Button (CM) as /class/input/input6
[   78.065301] ACPI: Power Button (CM) [PWRB]
[   78.081066] input: Sleep Button (CM) as /class/input/input7
[   78.081271] ACPI: Sleep Button (CM) [SLPB]
[   78.467661] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (version 2.00.00)
[   78.468779] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   82.363349] ppdev: user-space parallel port driver
[   85.235703] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   85.235716] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   85.235792] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   88.286118] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   88.286122] apm: overridden by ACPI.
[   88.480021] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   88.590687] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   88.616947] NFSD: starting 90-second grace period
[   92.571522] Capability LSM initialized
[   92.965904] Bluetooth: Core ver 2.11
[   92.966024] NET: Registered protocol family 31
[   92.966027] Bluetooth: HCI device and connection manager initialized
[   92.966030] Bluetooth: HCI socket layer initialized
[   93.097988] Bluetooth: L2CAP ver 2.8
[   93.097992] Bluetooth: L2CAP socket layer initialized
[   93.182553] Bluetooth: RFCOMM socket layer initialized
[   93.182668] Bluetooth: RFCOMM TTY layer initialized
[   93.182671] Bluetooth: RFCOMM ver 1.8
[   97.940147] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 8332.743434] usb 5-2: new full speed USB device using uhci_hcd and address 3
[ 8332.913502] usb 5-2: configuration #1 chosen from 2 choices
[ 8332.976262] cdc_acm 5-2:1.0: ttyACM0: USB ACM device
[ 8332.979650] usbcore: registered new interface driver cdc_acm
[ 8332.979767] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
[46951.008567] usb 5-2: USB disconnect, address 3
[91444.431935] usb 4-7: reset high speed USB device using ehci_hcd and address 5
[95333.097095] usb 5-2: new full speed USB device using uhci_hcd and address 4
[95333.267725] usb 5-2: configuration #1 chosen from 2 choices
[95333.270692] cdc_acm 5-2:1.0: ttyACM0: USB ACM device
marty@tux:~$
```

---

### Post by sefs on 2007-10-26
I aslo noticed that during this state that little rounded rectangle graphic where you can see various things loading does not appear any longer.

---

### Post by cowanh00 on 2007-10-26
> **sefs said:**
> I aslo noticed that during this state that little rounded rectangle graphic where you can see various things loading does not appear any longer.

I read somewhere else that the Splash screen has been disabled in Gutsy by default as it was slowing up Gnome loading!! :lolflag:

---

### Post by Vaan on 2007-10-26
You would think they would actually test these things out before releasing Gutsy. Now I wish I almost didn't upgrade and just stuck with Feisty.

I could understand if it was some problem with a driver or video card or something, but a problem with GNOME itself is somewhat careless in my opinion.

---

### Post by Ricardo_V on 2007-10-26
Well I reinstalled ubuntu 7.10 on my notebook without being connected to any network. When I get to the point of chooseing to confugre the network with DHCP I decide not to configure it now so it passes and I don't know if that would help or what but that way it no longer takes too much time to start the whole desktop. That is really good. And it does not hang in tomboy (85%) :)

---

### Post by sirjimmus on 2007-10-27
I am having this problem too, it seemed to just appear out of the blue without me modifying my system at all.  
Enter username and password, press enter then generally have to wait 50-70 seconds with the beige screen and mouse cursor before my icons/panels/wallpaper load up.

Did anyone find a solution for this?

---

### Post by Depressed Man on 2007-10-27
> **Vaan said:**
> You would think they would actually test these things out before releasing Gutsy. Now I wish I almost didn't upgrade and just stuck with Feisty.

I could understand if it was some problem with a driver or video card or something, but a problem with GNOME itself is somewhat careless in my opinion.

They likely did realize it. They just decided it wasn't a big enough problem to warrant delaying its release since they can fix it later. 

And mgmiller, there are code tags that will put the entire thing in a box so it won't stretch the forum out. They're [code*]whatever you want goes in here [/code*]. Without the *. Nothing wrong with what you did, it's just..distracting.

---

### Post by mgmiller on 2007-10-27
> And mgmiller, there are code tags that will put the entire thing in a box so it won't stretch the forum out. They're [code*]whatever you want goes in here [/code*]. Without the *. Nothing wrong with what you did, it's just..distracting.

Sorry, I didn't think about that.  You are quite right.  When I came back here, I found my own post annoying. :lolflag:

I promise to be good next time.

---

### Post by yostral on 2007-10-27
> **mgmiller said:**
> I promise to be good next time.
You can Edit it :).

---

### Post by oni5115 on 2007-10-27
Not sure how to get those messages, but I too am having this problem where the screen goes beige and I have to sit and wait for my desktop to load after login.  It is very annoying, especially since my theme is all nice and dark and then my screen goes bright orange.  :mad:

Not sure where to find the data everyone has been posting.  I've tried it with and without Compiz-Fusion.  Seems to be the only issue I've really had so far.

---

### Post by Nonno Bassotto on 2007-10-27
Write
```
dmesg
```
in a terminal.

---

### Post by sleepykit on 2007-10-27
+1 on this issue. Gnome is being a difficult child since I upgraded to Gutsy. I ran dmesg but didn't see any lines that looked like the highlighted one a few pages back. 

*sigh*

---

### Post by #Reistlehr- on 2007-10-27
can you post it anyway?

Im looking for a few things in it

Thanks

---

### Post by sleepykit on 2007-10-27
```
[   40.904000] Failure registering capabilities with primary security module.
[   45.136000] PM: Writing back config space on device 0000:09:00.0 at offset c (was 7fff0000, writing 0)
[   45.992000] NET: Registered protocol family 17
[   50.224000] NET: Registered protocol family 10
[   50.224000] lo: Disabled Privacy Extensions
[   50.224000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   50.224000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   53.056000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   53.172000] ieee80211_crypt: registered algorithm 'TKIP'
[   63.132000] eth1: no IPv6 routers present

```

---

### Post by RealNitro on 2007-10-27
I'm experiencing the same behaviour. My system is a MacBook, I upgraded from Feisty to Gutsy beta. Dmesg pasted [here](http://dpaste.com/23533/).

---

### Post by skymera on 2007-10-27
ok so i havent got a mutant install.

im having a slow boot too.

any ideas?

---

### Post by ThrobbingBrain66 on 2007-10-27
I can't help with the slow booting problems, but I can help with the login screen being brown/orange/whatever color it is:

```
gksudo gedit /etc/gdm/PreSession/Default
```

Scroll to the bottom of the file and change the value of BACKCOLOR in line 61 to whatever color you want it to be.

EDIT:  Thanks to nickless for correcting my error!

---

### Post by nickless on 2007-10-28
Great! :D

(but you have to write default with a capital D ;) )
```
gksudo gedit /etc/gdm/PreSession/Default
```

---

### Post by Partyboi2 on 2007-10-28
Here is mine

```
 [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
[    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f56f0
[    0.000000] Entering add_active_range(0, 0, 196592) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196592
[    0.000000]   HighMem    196592 ->   196592
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196592
[    0.000000] On node 0 totalpages: 196592
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1503 pages used for memmap
[    0.000000]   Normal zone: 190993 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7020 checksum 0
[    0.000000] ACPI: RSDP 000F7020, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 2FFF3000, 002C (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: FACP 2FFF3040, 0074 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: DSDT 2FFF30C0, 3AB4 (r1 GBT    AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 2FFF0000, 0040
[    0.000000] ACPI: APIC 2FFF6B80, 0068 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
[    0.000000] Built 1 zonelists.  Total pages: 195057
[    0.000000] Kernel command line: root=UUID=3747d6f7-02dd-4934-ba91-d383bdf7dc64 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2412.382 MHz processor.
[   21.715823] Console: colour VGA+ 80x25
[   21.716500] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   21.717173] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   21.733968] Memory: 767756k/786368k available (2015k kernel code, 17932k reserved, 916k data, 364k init, 0k highmem)
[   21.733979] virtual kernel memory layout:
[   21.733980]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   21.733982]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   21.733983]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   21.733985]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
[   21.733987]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   21.733988]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   21.733989]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   21.733993] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   21.734035] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   21.813971] Calibrating delay using timer specific routine.. 4828.56 BogoMIPS (lpj=9657124)
[   21.813999] Security Framework v1.0.0 initialized
[   21.814007] SELinux:  Disabled at boot.
[   21.814021] Mount-cache hash table entries: 512
[   21.814178] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   21.814192] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   21.814196] CPU: L2 cache: 512K
[   21.814198] CPU: Hyper-Threading is disabled
[   21.814201] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000
[   21.814214] Compat vDSO mapped to ffffe000.
[   21.814229] Checking 'hlt' instruction... OK.
[   21.830075] SMP alternatives: switching to UP code
[   21.830282] Freeing SMP alternatives: 11k freed
[   21.830601] Early unpacking initramfs... done
[   22.160070] ACPI: Core revision 20070126
[   22.160134] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.164320] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 07
[   22.164364] Total of 1 processors activated (4828.56 BogoMIPS).
[   22.164470] ENABLING IO-APIC IRQs
[   22.164654] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   22.309492] Brought up 1 CPUs
[   22.309629] Booting paravirtualized kernel on bare hardware
[   22.309710] Time: 21:26:51  Date: 09/28/107
[   22.309738] NET: Registered protocol family 16
[   22.309856] EISA bus registered
[   22.309872] ACPI: bus type pci registered
[   22.321718] PCI: PCI BIOS revision 2.10 entry at 0xfb1b0, last bus=1
[   22.321721] PCI: Using configuration type 1
[   22.321723] Setting up standard PCI resources
[   22.323994] ACPI: EC: Look up EC in DSDT
[   22.327790] ACPI: Interpreter enabled
[   22.327795] ACPI: (supports S0 S1 S4 S5)
[   22.327818] ACPI: Using IOAPIC for interrupt routing
[   22.333569] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.333576] PCI: Probing PCI hardware (bus 00)
[   22.333792] Enabling SiS 96x SMBus.
[   22.334477] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.351749] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   22.351864] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   22.351978] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   22.352091] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   22.352205] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   22.352323] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   22.352440] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   22.352555] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   22.352668] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.352682] pnp: PnP ACPI init
[   22.352696] ACPI: bus type pnp registered
[   22.356115] pnp: PnP ACPI: found 14 devices
[   22.356118] ACPI: ACPI bus type pnp unregistered
[   22.356125] PnPBIOS: Disabled by ACPI PNP
[   22.356191] PCI: Using ACPI for IRQ routing
[   22.356195] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.363238] NET: Registered protocol family 8
[   22.363241] NET: Registered protocol family 20
[   22.363325] pnp: 00:00: iomem range 0xcfc00-0xcffff has been reserved
[   22.363329] pnp: 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   22.363332] pnp: 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   22.363335] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   22.365390] Time: tsc clocksource has been installed.
[   22.393698] PCI: Bridge: 0000:00:01.0
[   22.393700]   IO window: disabled.
[   22.393707]   MEM window: e4000000-e5ffffff
[   22.393713]   PREFETCH window: d0000000-dfffffff
[   22.393743] NET: Registered protocol family 2
[   22.433369] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.433537] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   22.435291] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   22.435983] TCP: Hash tables configured (established 131072 bind 65536)
[   22.435991] TCP reno registered
[   22.445510] checking if image is initramfs... it is
[   22.896825] Switched to high resolution mode on CPU 0
[   23.114713] Freeing initrd memory: 7112k freed
[   23.115168] audit: initializing netlink socket (disabled)
[   23.115187] audit(1193606812.028:1): initialized
[   23.117615] VFS: Disk quotas dquot_6.5.1
[   23.117687] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.117803] io scheduler noop registered
[   23.117806] io scheduler anticipatory registered
[   23.117808] io scheduler deadline registered
[   23.117827] io scheduler cfq registered (default)
[   23.117878] Boot video device is 0000:01:00.0
[   23.118058] isapnp: Scanning for PnP cards...
[   23.471591] isapnp: No Plug & Play device found
[   23.506666] Real Time Clock Driver v1.12ac
[   23.506778] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.506884] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.507157] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   23.507990] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.508448] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   23.509402] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.509677] input: Macintosh mouse button emulation as /class/input/input0
[   23.509780] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   23.510090] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.510097] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.510295] mice: PS/2 mouse device common for all mice
[   23.510423] EISA: Probing bus 0 at eisa.0
[   23.510432] Cannot allocate resource for EISA slot 1
[   23.510460] EISA: Detected 0 cards.
[   23.510682] TCP cubic registered
[   23.510700] NET: Registered protocol family 1
[   23.510727] Using IPI No-Shortcut mode
[   23.510905]   Magic number: 11:731:450
[   23.511521] Freeing unused kernel memory: 364k freed
[   23.556106] input: AT Translated Set 2 keyboard as /class/input/input1
[   24.747150] AppArmor: AppArmor initialized<5>audit(1193606813.528:2):  type=1505 info="AppArmor initialized" pid=1184
[   24.757737] fuse init (API version 7.8)
[   24.763410] Failure registering capabilities with primary security module.
[   24.784746] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   25.422445] SCSI subsystem initialized
[   25.428498] libata version 2.21 loaded.
[   25.431922] pata_sis 0000:00:02.5: version 0.5.1
[   25.432082] scsi0 : pata_sis
[   25.432137] scsi1 : pata_sis
[   25.432261] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   25.432267] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   25.468557] usbcore: registered new interface driver usbfs
[   25.468590] usbcore: registered new interface driver hub
[   25.468618] usbcore: registered new device driver usb
[   25.488804] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   25.539585] 8139too Fast Ethernet driver 0.9.28
[   25.620467] Floppy drive(s): fd0 is 1.44M
[   25.659081] ata1.00: Host Protected Area detected:
[   25.659084]  current size: 312579695 sectors
[   25.659085]  native size: 312581808 sectors
[   25.661212] ata1.00: native size increased to 312581808 sectors
[   25.661216] ata1.00: ATA-6: WDC WD1600JB-00GVC0, 08.02D08, max UDMA/100
[   25.661219] ata1.00: 312581808 sectors, multi 16: LBA48 
[   25.661575] ata1.01: Host Protected Area detected:
[   25.661577]  current size: 78163247 sectors
[   25.661578]  native size: 78165360 sectors
[   25.661844] ata1.01: native size increased to 78165360 sectors
[   25.661847] ata1.01: ATA-6: ST340014A, 3.54, max UDMA/100
[   25.661849] ata1.01: 78165360 sectors, multi 16: LBA48 
[   25.679079] ata1.00: configured for UDMA/100
[   25.693871] ata1.01: configured for UDMA/100
[   25.697825] FDC 0 is a post-1991 82077
[   26.169372] ata2.00: ATAPI: BENQ    DVD DD DW1640, BSHB, max UDMA/33
[   26.169380] ata2.01: ATAPI: HL-DT-ST GCE-8520B, 1.03, max UDMA/33
[   26.341167] ata2.00: configured for UDMA/33
[   26.512720] ata2.01: configured for UDMA/33
[   26.512871] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600JB-00G 08.0 PQ: 0 ANSI: 5
[   26.513393] scsi 0:0:1:0: Direct-Access     ATA      ST340014A        3.54 PQ: 0 ANSI: 5
[   26.515649] scsi 1:0:0:0: CD-ROM            BENQ     DVD DD DW1640    BSHB PQ: 0 ANSI: 5
[   26.516244] scsi 1:0:1:0: CD-ROM            HL-DT-ST CD-RW GCE-8520B  1.03 PQ: 0 ANSI: 5
[   26.516743] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
[   26.516761] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   26.517124] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   26.517148] ohci_hcd 0000:00:03.0: irq 16, io mem 0xe7001000
[   26.544356] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   26.544416] sd 0:0:0:0: [sda] Write Protect is off
[   26.544419] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.544469] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.544548] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   26.544560] sd 0:0:0:0: [sda] Write Protect is off
[   26.544563] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.544584] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.544591]  sda: sda1
[   26.557273] sd 0:0:0:0: [sda] Attached SCSI disk
[   26.557490] sd 0:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
[   26.557506] sd 0:0:1:0: [sdb] Write Protect is off
[   26.557509] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   26.557531] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.557587] sd 0:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
[   26.557600] sd 0:0:1:0: [sdb] Write Protect is off
[   26.557603] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   26.557623] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.557627]  sdb: sdb1 sdb2 <<6>usb usb1: configuration #1 chosen from 1 choice
[   26.574580] hub 1-0:1.0: USB hub found
[   26.574593] hub 1-0:1.0: 2 ports detected
[   26.593298]  sdb5 >
[   26.593917] sd 0:0:1:0: [sdb] Attached SCSI disk
[   26.598746] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   26.598773] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   26.598795] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[   26.598817] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[   26.654285] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   26.654292] Uniform CD-ROM driver Revision: 3.20
[   26.654627] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   26.656254] sr1: scsi3-mmc drive: 40x/52x writer cd/rw xa/form2 cdda tray
[   26.656531] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   26.676522] ACPI: PCI Interrupt 0000:00:03.1[b] -> GSI 21 (level, low) -> IRQ 17
[   26.676543] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   26.676573] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   26.676592] ohci_hcd 0000:00:03.1: irq 17, io mem 0xe7002000
[   26.734384] usb usb2: configuration #1 chosen from 1 choice
[   26.734419] hub 2-0:1.0: USB hub found
[   26.734432] hub 2-0:1.0: 2 ports detected
[   26.836291] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 18
[   26.836312] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   26.836343] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   26.836362] ohci_hcd 0000:00:03.2: irq 18, io mem 0xe7003000
[   26.894181] usb usb3: configuration #1 chosen from 1 choice
[   26.894215] hub 3-0:1.0: USB hub found
[   26.894228] hub 3-0:1.0: 2 ports detected
[   26.996250] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 19
[   26.996268] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   26.996304] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   26.996343] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[   26.996355] ehci_hcd 0000:00:03.3: irq 19, io mem 0xe7004000
[   27.043783] Attempting manual resume
[   27.043788] swsusp: Resume From Partition 8:21
[   27.043790] PM: Checking swsusp image.
[   27.050585] PM: Resume from disk failed.
[   27.075178] kjournald starting.  Commit interval 5 seconds
[   27.075194] EXT3-fs: mounted filesystem with ordered data mode.
[   27.139765] usb 2-2: new full speed USB device using ohci_hcd and address 2
[   27.139794] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.139923] usb usb4: configuration #1 chosen from 1 choice
[   27.139956] hub 4-0:1.0: USB hub found
[   27.139966] hub 4-0:1.0: 6 ports detected
[   27.243929] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 17 (level, low) -> IRQ 20
[   27.244246] eth0: RealTek RTL8139 at 0xf083a000, 00:50:fc:98:3a:dd, IRQ 20
[   27.244249] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   27.874898] usb 2-2: new full speed USB device using ohci_hcd and address 3
[   28.090727] usb 2-2: configuration #1 chosen from 1 choice
[   35.629648] Linux agpgart interface v0.102 (c) Dave Jones
[   35.719174] agpgart: Detected SiS chipset - id:1606
[   35.723059] agpgart: AGP aperture is 64M @ 0xe0000000
[   35.771723] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.822965] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.870739] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x1400
[   36.593599] nvidia: module license 'NVIDIA' taints kernel.
[   36.856406] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
[   36.856699] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   36.928406] input: PC Speaker as /class/input/input2
[   37.108093] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   37.501560] eth1: register 'cdc_ether' at usb-0000:00:03.1-2, CDC Ethernet Device, 00:14:04:01:f7:98
[   37.501586] usbcore: registered new interface driver cdc_ether
[   37.592221] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[   37.595059] parport_pc 00:0a: reported by Plug and Play ACPI
[   37.595107] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   37.823946] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 22
[   38.146750] intel8x0_measure_ac97_clock: measured 52911 usecs
[   38.146754] intel8x0: clocking to 48000
[   38.704836] lp0: using parport0 (interrupt-driven).
[   38.779507] Adding 1646620k swap on /dev/sdb5.  Priority:-1 extents:1 across:1646620k
[  113.222202] EXT3 FS on sdb1, internal journal
[  115.495151] No dock devices found.
[  115.639400] input: Power Button (FF) as /class/input/input4
[  115.644577] ACPI: Power Button (FF) [PWRF]
[  115.685683] input: Power Button (CM) as /class/input/input5
[  115.690820] ACPI: Power Button (CM) [PWRB]
[  115.732788] input: Sleep Button (CM) as /class/input/input6
[  115.737942] ACPI: Sleep Button (CM) [FUTS]
[  118.869806] eth0: link down
[  119.900809] ppdev: user-space parallel port driver
[  121.368950] audit(1193567310.771:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4796 profile="/usr/sbin/cupsd"
[  121.470367] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  121.470530] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  121.470683] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  122.175866] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  122.175873] apm: overridden by ACPI.
[  122.742686] Failure registering capabilities with primary security module.
[  123.121985] Bluetooth: Core ver 2.11
[  123.122135] NET: Registered protocol family 31
[  123.122139] Bluetooth: HCI device and connection manager initialized
[  123.122143] Bluetooth: HCI socket layer initialized
[  123.255256] Bluetooth: L2CAP ver 2.8
[  123.255262] Bluetooth: L2CAP socket layer initialized
[  123.397900] Bluetooth: RFCOMM socket layer initialized
[  123.398040] Bluetooth: RFCOMM TTY layer initialized
[  123.398044] Bluetooth: RFCOMM ver 1.8
[  128.150584] NET: Registered protocol family 17
[  130.828553] NET: Registered protocol family 10
[  130.828763] lo: Disabled Privacy Extensions
[  130.828897] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  141.220955] eth1: no IPv6 routers present
karl@karl-desktop:~$ 


```

---

### Post by gregili on 2007-10-28
Same problem on my Acer Aspire 1522Wlmi
Takes about 40 seconds to load after login.
Using Compiz Fusion on Gutsy.Upgraded from Feisty.

Here is my dmsg too..

```

[    0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: root=UUID=db8864f9-30a4-4f90-b891-31dbaaf37f73 ro quiet splash vga=791
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff70000 (usable)
[    0.000000]  BIOS-e820: 000000003ff70000 - 000000003ff7a000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff7a000 - 000000003ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff80000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 262000) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6A60 checksum 0
[    0.000000] ACPI: RSDP 000F6A60, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 3FF73FDE, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 3FF79E56, 0084 (r2 AMDK8  PTLTW     6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 3FF7400E, 5E48 (r1  VIA   PTL_ACPI  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FF7AFC0, 0040
[    0.000000] ACPI: SSDT 3FF79EDA, 00D6 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: APIC 3FF79FB0, 0050 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003ff70000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 262000) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000003ff70000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   262000
[    0.000000] On node 0 totalpages: 261903
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1124 pages reserved
[    0.000000]   DMA zone: 2819 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3526 pages used for memmap
[    0.000000]   DMA32 zone: 254378 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d8000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d8000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bffe0000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 257197
[    0.000000] Kernel command line: root=UUID=db8864f9-30a4-4f90-b891-31dbaaf37f73 ro quiet splash vga=791
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   11.443439] time.c: Detected 1801.071 MHz processor.
[   11.443489] Console: colour dummy device 80x25
[   11.443507] Checking aperture...
[   11.443510] CPU 0: aperture @ d0000000 size 256 MB
[   11.460595] Memory: 1021404k/1048000k available (2274k kernel code, 26208k reserved, 1181k data, 296k init)
[   11.460658] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   11.537350] Calibrating delay using timer specific routine.. 3605.46 BogoMIPS (lpj=7210922)
[   11.537396] Security Framework v1.0.0 initialized
[   11.537409] SELinux:  Disabled at boot.
[   11.537519] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   11.538780] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   11.539366] Mount-cache hash table entries: 256
[   11.539547] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   11.539550] CPU: L2 Cache: 1024K (64 bytes/line)
[   11.539553] CPU 0/0 -> Node 0
[   11.539575] SMP alternatives: switching to UP code
[   11.539800] Freeing SMP alternatives: 24k freed
[   11.540956] Early unpacking initramfs... done
[   11.876016] ACPI: Core revision 20070126
[   11.876082] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   12.005233] Using local APIC timer interrupts.
[   12.060705] result 12507445
[   12.060707] Detected 12.507 MHz APIC timer.
[   12.060901] Brought up 1 CPUs
[   12.061269] NET: Registered protocol family 16
[   12.061353] ACPI: bus type pci registered
[   12.061361] PCI: Using configuration type 1
[   12.062040] ACPI: EC: Look up EC in DSDT
[   12.062600] ACPI: EC: GPE=0x0b, ports=0x66, 0x62
[   12.063839] ACPI: Interpreter enabled
[   12.063842] ACPI: (supports S0 S3 S4 S5)
[   12.063854] ACPI: Using IOAPIC for interrupt routing
[   12.085606] ACPI: EC: GPE=0x0b, ports=0x66, 0x62
[   12.085653] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.085658] PCI: Probing PCI hardware (bus 00)
[   12.086212] PCI quirk: region 4000-407f claimed by vt8235 PM
[   12.086216] PCI quirk: region 8100-810f claimed by vt8235 SMB
[   12.086535] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.096681] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *10, disabled.
[   12.096753] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *10, disabled.
[   12.096841] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *11, disabled.
[   12.096909] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *11, disabled.
[   12.096998] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 12 14 15) *10
[   12.097087] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 12 14 15)
[   12.097174] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *11 12 14 15)
[   12.097264] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   12.097337] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.097346] pnp: PnP ACPI init
[   12.097355] ACPI: bus type pnp registered
[   12.108740] pnp: PnP ACPI: found 11 devices
[   12.108743] ACPI: ACPI bus type pnp unregistered
[   12.108790] PCI: Using ACPI for IRQ routing
[   12.108793] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   12.108801] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[   12.108893] NET: Registered protocol family 8
[   12.108895] NET: Registered protocol family 20
[   12.108943] agpgart: Detected AGP bridge 0
[   12.117488] agpgart: AGP aperture is 256M @ 0xd0000000
[   12.117580] pnp: 00:05: iomem range 0xe0000-0xfffff could not be reserved
[   12.117585] pnp: 00:05: iomem range 0xfff00000-0xffffffff could not be reserved
[   12.117588] pnp: 00:05: iomem range 0xffee0000-0xffefffff has been reserved
[   12.117592] pnp: 00:05: iomem range 0xfec00000-0xfec00fff has been reserved
[   12.117599] pnp: 00:06: ioport range 0x600-0x60f has been reserved
[   12.117601] pnp: 00:06: ioport range 0x1c0-0x1cf has been reserved
[   12.117604] pnp: 00:06: ioport range 0x4d0-0x4d1 has been reserved
[   12.117608] pnp: 00:06: ioport range 0xfe10-0xfe11 has been reserved
[   12.117612] pnp: 00:06: iomem range 0xfec00000-0xfec00fff has been reserved
[   12.117615] pnp: 00:06: iomem range 0xfee00000-0xfee00fff could not be reserved
[   12.117901] PCI: Failed to allocate mem resource #6:20000@f0000000 for 0000:01:00.0
[   12.117907] PCI: Bridge: 0000:00:01.0
[   12.117908]   IO window: disabled.
[   12.117913]   MEM window: c1000000-c1ffffff
[   12.117916]   PREFETCH window: e0000000-efffffff
[   12.117920] PCI: Bus 2, cardbus bridge: 0000:00:0b.0
[   12.117923]   IO window: 00002000-000020ff
[   12.117927]   IO window: 00002400-000024ff
[   12.117930]   PREFETCH window: 50000000-53ffffff
[   12.117934]   MEM window: 54000000-57ffffff
[   12.117938] PCI: Bus 6, cardbus bridge: 0000:00:0b.1
[   12.117940]   IO window: 00002800-000028ff
[   12.117944]   IO window: 00002c00-00002cff
[   12.117948]   PREFETCH window: 58000000-5bffffff
[   12.117951]   MEM window: 5c000000-5fffffff
[   12.117967] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   12.117983] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 17
[   12.117992] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   12.118001] PCI: Enabling device 0000:00:0b.1 (0000 -> 0003)
[   12.118004] ACPI: PCI Interrupt 0000:00:0b.1[B] -> GSI 18 (level, low) -> IRQ 18
[   12.118014] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   12.118063] NET: Registered protocol family 2
[   12.120797] Time: tsc clocksource has been installed.
[   12.156825] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   12.157161] TCP established hash table entries: 131072 (order: 9, 3145728 bytes)
[   12.160372] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   12.161551] TCP: Hash tables configured (established 131072 bind 65536)
[   12.161555] TCP reno registered
[   12.172902] checking if image is initramfs... it is
[   12.819562] Freeing initrd memory: 7245k freed
[   12.827421] audit: initializing netlink socket (disabled)
[   12.827436] audit(1193580032.240:1): initialized
[   12.829294] VFS: Disk quotas dquot_6.5.1
[   12.829346] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   12.829434] io scheduler noop registered
[   12.829437] io scheduler anticipatory registered
[   12.829439] io scheduler deadline registered
[   12.829532] io scheduler cfq registered (default)
[   12.829545] PCI: VIA PCI bridge detected. Disabling DAC.
[   12.830569] Boot video device is 0000:01:00.0
[   12.853760] Real Time Clock Driver v1.12ac
[   12.853855] Linux agpgart interface v0.102 (c) Dave Jones
[   12.853858] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.854031] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   12.854917] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.855139] input: Macintosh mouse button emulation as /class/input/input0
[   12.855205] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   12.859137] i8042.c: Detected active multiplexing controller, rev 1.1.
[   12.860332] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.860336] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   12.860339] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   12.860342] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   12.860344] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   12.860583] mice: PS/2 mouse device common for all mice
[   12.860704] TCP cubic registered
[   12.860772] NET: Registered protocol family 1
[   12.860993] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   12.861002] Freeing unused kernel memory: 296k freed
[   12.924104] input: AT Translated Set 2 keyboard as /class/input/input1
[   14.045218] AppArmor: AppArmor initialized<5>audit(1193580033.460:2):  type=1505 info="AppArmor initialized" pid=1211
[   14.050758] fuse init (API version 7.8)
[   14.055237] Failure registering capabilities with primary security module.
[   14.160924] ACPI: Thermal Zone [THRS] (42 C)
[   14.251736] ACPI: Thermal Zone [THRC] (58 C)
[   14.861269] ACPI: PCI Interrupt 0000:00:0b.2[C] -> GSI 19 (level, low) -> IRQ 19
[   14.911442] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[c0005800-c0005fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   14.931859] usbcore: registered new interface driver usbfs
[   14.931885] usbcore: registered new interface driver hub
[   14.931908] usbcore: registered new device driver usb
[   14.932641] USB Universal Host Controller Interface driver v3.0
[   14.932750] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
[   14.932763] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   14.932944] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   14.932975] uhci_hcd 0000:00:10.0: irq 21, io base 0x00001c20
[   14.933103] usb usb1: configuration #1 chosen from 1 choice
[   14.933131] hub 1-0:1.0: USB hub found
[   14.933140] hub 1-0:1.0: 2 ports detected
[   14.961446] SCSI subsystem initialized
[   14.966715] libata version 2.21 loaded.
[   15.038141] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 21
[   15.038156] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   15.038182] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   15.038206] uhci_hcd 0000:00:10.1: irq 21, io base 0x00001c40
[   15.038335] usb usb2: configuration #1 chosen from 1 choice
[   15.038363] hub 2-0:1.0: USB hub found
[   15.038372] hub 2-0:1.0: 2 ports detected
[   15.145973] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 21
[   15.145988] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   15.146016] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   15.146039] uhci_hcd 0000:00:10.2: irq 21, io base 0x00001c60
[   15.146149] usb usb3: configuration #1 chosen from 1 choice
[   15.146179] hub 3-0:1.0: USB hub found
[   15.146186] hub 3-0:1.0: 2 ports detected
[   15.255603] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 21
[   15.256293] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   15.256368] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   15.256409] ehci_hcd 0000:00:10.3: irq 21, io mem 0xc0006800
[   15.256416] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   15.256515] usb usb4: configuration #1 chosen from 1 choice
[   15.256547] hub 4-0:1.0: USB hub found
[   15.256554] hub 4-0:1.0: 6 ports detected
[   15.366796] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   15.366802] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   15.367363] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   15.367441] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   15.367444] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[   15.367454] VP_IDE: chipset revision 6
[   15.367456] VP_IDE: not 100% native mode: will probe irqs later
[   15.367467] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[   15.367476]     ide0: BM-DMA at 0x1c80-0x1c87, BIOS settings: hda:DMA, hdb:pio
[   15.367488]     ide1: BM-DMA at 0x1c88-0x1c8f, BIOS settings: hdc:DMA, hdd:pio
[   15.367495] Probing IDE interface ide0...
[   15.789292] hda: TOSHIBA MK6025GAS, ATA DISK drive
[   16.184893] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000ae40506103b22]
[   16.460654] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   16.472528] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   16.509872] Probing IDE interface ide1...
[   16.679421] usb 2-1: configuration #1 chosen from 1 choice
[   16.928081] usb 2-2: new full speed USB device using uhci_hcd and address 3
[   17.110948] usb 2-2: configuration #1 chosen from 1 choice
[   17.121563] usbcore: registered new interface driver hiddev
[   17.160972] input: HID 1241:1166 as /class/input/input2
[   17.160992] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:10.1-1
[   17.161011] usbcore: registered new interface driver usbhid
[   17.161015] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   17.375733] hdc: TSSTcorpCD/DVDW TS-L532A, ATAPI CD/DVD-ROM drive
[   18.066621] ide1 at 0x170-0x177,0x376 on irq 15
[   18.075227] r8169 Gigabit Ethernet driver 2.2LK loaded
[   18.075255] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 22 (level, low) -> IRQ 22
[   18.075268] PCI: Disallowing DAC for device 0000:00:0c.0
[   18.075534] eth0: RTL8169sb/8110sb at 0xffffc200001ee400, 00:0a:e4:a6:01:42, XID 10000000 IRQ 22
[   18.082934] hda: max request size: 128KiB
[   18.090548] hda: 117210240 sectors (60011 MB), CHS=65535/16/63, UDMA(100)
[   18.091620] hda: cache flushes supported
[   18.091663]  hda: hda2 hda3 < hda5 hda6 hda7 >
[   18.247223] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   18.247234] Uniform CD-ROM driver Revision: 3.20
[   18.705823] kjournald starting.  Commit interval 5 seconds
[   18.705835] EXT3-fs: mounted filesystem with ordered data mode.
[   31.268458] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.339324] Yenta: CardBus bridge found at 0000:00:0b.0 [1025:006e]
[   31.339341] Yenta: Using CSCINT to route CSC interrupts to PCI
[   31.339343] Yenta: Routing CardBus interrupts to PCI
[   31.339348] Yenta TI: socket 0000:00:0b.0, mfunc 0x010a1b22, devctl 0x64
[   31.529340] input: PC Speaker as /class/input/input3
[   31.574407] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   31.574412] Socket status: 30000006
[   31.574789] Yenta: CardBus bridge found at 0000:00:0b.1 [1025:006e]
[   31.574802] Yenta: Using CSCINT to route CSC interrupts to PCI
[   31.574804] Yenta: Routing CardBus interrupts to PCI
[   31.574809] Yenta TI: socket 0000:00:0b.1, mfunc 0x010a1b22, devctl 0x64
[   31.810219] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[   31.810225] Socket status: 30000006
[   31.810477] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.903549] irda_init()
[   31.903575] NET: Registered protocol family 23
[   32.144760] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9248b1, caps: 0x904713/0x4000
[   32.171325] Linux video capture interface: v2.00
[   32.183589] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   32.186630] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   32.186658] nsc-ircc, chip->init
[   32.186667] nsc-ircc, Found chip at base=0x02e
[   32.186693] nsc-ircc, driver loaded (Dag Brattli)
[   32.186700] nsc_ircc_open(), can't get iobase of 0x2f8
[   32.186728] nsc-ircc, Found chip at base=0x02e
[   32.186754] nsc-ircc, driver loaded (Dag Brattli)
[   32.186756] nsc_ircc_open(), can't get iobase of 0x2f8
[   32.186912] pnp: Device 00:0a disabled.
[   32.186978] parport_pc 00:09: reported by Plug and Play ACPI
[   32.187051] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   32.751095] nvidia: module license 'NVIDIA' taints kernel.
[   33.011284] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   33.011578] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
[   33.074088] zc0301: V4L2 driver for ZC0301[P] Image Processor and Control Chip v1:1.07
[   33.074147] usb 2-2: ZC0301[P] Image Processor and Control Chip detected (vid/pid 0x041E:0x401C)
[   33.099773] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 22
[   33.104180] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   33.163122] usb 2-2: No supported image sensor detected
[   33.163158] usbcore: registered new interface driver zc0301
[   33.285633] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
[   33.502001] usbcore: registered new interface driver gspca
[   33.502007] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   33.612653] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
[   33.612786] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   34.504225] lp0: using parport0 (interrupt-driven).
[   34.618741] ndiswrapper version 1.45 loaded (smp=yes)
[   34.750965] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
[   34.751642] ndiswrapper: driver neti2220x64 (,17/01/2005,3.03.12.2006) loaded
[   34.751852] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 21 (level, low) -> IRQ 21
[   34.785244] ndiswrapper: using IRQ 21
[   34.990388] wlan0: ethernet device 00:0e:9b:94:07:4f using NDIS driver: neti2220x64, version: 0x30003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 17FE:2220.5.conf
[   34.990410] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   34.994882] usbcore: registered new interface driver ndiswrapper
[   35.680010] EXT3 FS on hda5, internal journal
[   36.592372] kjournald starting.  Commit interval 5 seconds
[   36.592462] EXT3 FS on hda6, internal journal
[   36.592468] EXT3-fs: mounted filesystem with ordered data mode.
[   38.033547] ACPI: Battery Slot [BAT0] (battery present)
[   38.336449] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   38.385645] ACPI: AC Adapter [AC] (on-line)
[   38.410281] No dock devices found.
[   38.454028] input: Power Button (FF) as /class/input/input5
[   38.458284] ACPI: Power Button (FF) [PWRF]
[   38.487425] input: Lid Switch as /class/input/input6
[   38.491658] ACPI: Lid Switch [LID]
[   38.520709] input: Sleep Button (CM) as /class/input/input7
[   38.524921] ACPI: Sleep Button (CM) [SLPB]
[   38.754151] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
[   38.754196] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x2
[   38.754199] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6
[   38.754202] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x12
[   38.755666] powernow-k8: ph2 null fid transition 0xa
[   40.819141] r8169: eth0: link up
[   40.826076] ttyS1: LSR safety check engaged!
[   42.801303] ppdev: user-space parallel port driver
[   43.128513] audit(1193572862.787:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4957 profile="/usr/sbin/cupsd"
[   43.661851] Marking TSC unstable due to cpufreq changes
[   43.662971] Time: acpi_pm clocksource has been installed.
[   43.754865] Failure registering capabilities with primary security module.
[   44.100507] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   44.100519] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   44.100571] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   44.376186] Bluetooth: Core ver 2.11
[   44.376243] NET: Registered protocol family 31
[   44.376245] Bluetooth: HCI device and connection manager initialized
[   44.376248] Bluetooth: HCI socket layer initialized
[   44.386403] Bluetooth: L2CAP ver 2.8
[   44.386407] Bluetooth: L2CAP socket layer initialized
[   44.635955] Bluetooth: RFCOMM socket layer initialized
[   44.636041] Bluetooth: RFCOMM TTY layer initialized
[   44.636044] Bluetooth: RFCOMM ver 1.8
[   45.441217] NET: Registered protocol family 10
[   45.441379] lo: Disabled Privacy Extensions
[   45.441519] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   47.229921] NET: Registered protocol family 17
[   54.380938] eth0: no IPv6 routers present
[   64.353620] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
[   64.655536] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (7)
[   64.681910] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (9)
[   64.682180] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (14)
[   64.682454] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (13)
[   64.682725] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (16)
[   64.682999] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (11)
[   64.683272] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (6)
[  161.599113] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
[  165.945700] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
[  199.448302] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  199.448913] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  199.449527] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  199.450142] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  199.450984] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  199.450987] psmouse.c: issuing reconnect request
[  498.615806] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  498.616418] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  498.617032] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  498.617647] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  498.619149] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  498.619152] psmouse.c: issuing reconnect request
[  679.519430] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  679.520042] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  679.520654] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  679.523339] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[  679.523953] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  679.523956] psmouse.c: issuing reconnect request
[  692.279604] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  947.212200] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[  947.213524] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  947.218460] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.

```

---

### Post by mgmiller on 2007-10-28
> You can Edit it 

Thanks Yostral, I edited it and I feel much better now.  :grin:

---

### Post by soro2005 on 2007-10-28
Here comes my dmesg. It's also taking quite a while for Gnome to boot. Particularly long when trackerd kicks in, but also when there's nothing new to be indexed:

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d4000 - 00000000000d8000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005dee0000 (usable)
[    0.000000]  BIOS-e820: 000000005dee0000 - 000000005deea000 (ACPI data)
[    0.000000]  BIOS-e820: 000000005deea000 - 000000005df00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005df00000 - 0000000060000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] 606MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 384736) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   384736
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   384736
[    0.000000] On node 0 totalpages: 384736
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1213 pages used for memmap
[    0.000000]   HighMem zone: 154147 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6930 checksum 0
[    0.000000] ACPI: RSDP 000F6930, 0014 (r0 TOSCPL)
[    0.000000] ACPI: RSDT 5DEE43E1, 0038 (r1 TOSCPL    o&#65533;f&#65533;  6040000  LTP        0)
[    0.000000] ACPI: FACP 5DEE9EEC, 0074 (r1 TOSCPL MONTARA   6040000 PTL        50)
[    0.000000] ACPI: DSDT 5DEE4C53, 5299 (r1 TOSCPL MONTARAG  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 5DEFAFC0, 0040
[    0.000000] ACPI: APIC 5DEE9F98, 0068 (r1 INTEL  MONTARA   6040000 LOHR       64)
[    0.000000] ACPI: SSDT 5DEE480A, 02B9 (r1  PmRef  Cpu0Ist     3000 INTL 20030224)
[    0.000000] ACPI: SSDT 5DEE4632, 01D8 (r1  PmRef  Cpu0Cst     3001 INTL 20030224)
[    0.000000] ACPI: SSDT 5DEE4419, 0219 (r1  PmRef    CpuPm     3000 INTL 20030224)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9ec10000)
[    0.000000] Built 1 zonelists.  Total pages: 381731
[    0.000000] Kernel command line: root=UUID=fcf39cd5-68c0-420f-a14a-aeb8c9f10a75 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1698.651 MHz processor.
[    8.753898] Console: colour VGA+ 80x25
[    8.754274] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.754739] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.834753] Memory: 1513428k/1538944k available (2015k kernel code, 24280k reserved, 916k data, 364k init, 621440k highmem)
[    8.834763] virtual kernel memory layout:
[    8.834764]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    8.834766]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.834767]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    8.834768]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.834770]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    8.834771]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[    8.834772]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[    8.834776] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.834837] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    8.914754] Calibrating delay using timer specific routine.. 3399.34 BogoMIPS (lpj=6798687)
[    8.914794] Security Framework v1.0.0 initialized
[    8.914809] SELinux:  Disabled at boot.
[    8.914826] Mount-cache hash table entries: 512
[    8.915008] CPU: After generic identify, caps: afe9fbbf 00000000 00000000 00000000 00000180 00000000 00000000
[    8.915024] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.915027] CPU: L2 cache: 2048K
[    8.915031] CPU: After all inits, caps: afe9fbbf 00000000 00000000 00002040 00000180 00000000 00000000
[    8.915042] Compat vDSO mapped to ffffe000.
[    8.915059] Checking 'hlt' instruction... OK.
[    8.930910] SMP alternatives: switching to UP code
[    8.931236] Freeing SMP alternatives: 11k freed
[    8.931565] Early unpacking initramfs... done
[    9.294954] ACPI: Core revision 20070126
[    9.295025] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.330109] CPU0: Intel(R) Pentium(R) M processor 1.70GHz stepping 06
[    9.330132] Total of 1 processors activated (3399.34 BogoMIPS).
[    9.330269] ENABLING IO-APIC IRQs
[    9.330446] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.474033] Brought up 1 CPUs
[    9.474134] Booting paravirtualized kernel on bare hardware
[    9.474195] Time: 10:10:55  Date: 09/28/107
[    9.474216] NET: Registered protocol family 16
[    9.474293] EISA bus registered
[    9.474305] ACPI: bus type pci registered
[    9.474689] PCI: PCI BIOS revision 2.10 entry at 0xfd952, last bus=2
[    9.474691] PCI: Using configuration type 1
[    9.474693] Setting up standard PCI resources
[    9.481293] ACPI: EC: Look up EC in DSDT
[    9.482934] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[    9.483969] ACPI: Interpreter enabled
[    9.483972] ACPI: (supports S0 S3 S4 S5)
[    9.483987] ACPI: Using IOAPIC for interrupt routing
[    9.526962] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[    9.527005] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.527014] PCI: Probing PCI hardware (bus 00)
[    9.527421] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    9.527425] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[    9.527900] PCI: Transparent bridge - 0000:00:1e.0
[    9.527963] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.528143] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    9.534350] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    9.534439] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    9.534525] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    9.534611] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    9.534696] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 *4 5 6 7 10 12 14 15)
[    9.534782] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    9.534867] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    9.534954] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 *3 4 5 6 7 11 12 14 15)
[    9.535039] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.535051] pnp: PnP ACPI init
[    9.535058] ACPI: bus type pnp registered
[    9.554027] pnp: PnP ACPI: found 8 devices
[    9.554029] ACPI: ACPI bus type pnp unregistered
[    9.554033] PnPBIOS: Disabled by ACPI PNP
[    9.554071] PCI: Using ACPI for IRQ routing
[    9.554074] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.560287] NET: Registered protocol family 8
[    9.560289] NET: Registered protocol family 20
[    9.560341] pnp: 00:04: iomem range 0xfec10000-0xfec1ffff could not be reserved
[    9.561880] Time: tsc clocksource has been installed.
[    9.590554] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[    9.590556]   IO window: 00003800-000038ff
[    9.590560]   IO window: 00003c00-00003cff
[    9.590564]   PREFETCH window: 70000000-73ffffff
[    9.590568]   MEM window: 78000000-7bffffff
[    9.590571] PCI: Bridge: 0000:00:1e.0
[    9.590574]   IO window: 3000-3fff
[    9.590579]   MEM window: e0200000-e02fffff
[    9.590583]   PREFETCH window: 70000000-73ffffff
[    9.590594] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.590608] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[    9.590621] NET: Registered protocol family 2
[    9.629815] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.629888] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    9.631408] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.632055] TCP: Hash tables configured (established 131072 bind 65536)
[    9.632059] TCP reno registered
[    9.641959] checking if image is initramfs... it is
[   10.093165] Switched to high resolution mode on CPU 0
[   10.351687] Freeing initrd memory: 7561k freed
[   10.352113] audit: initializing netlink socket (disabled)
[   10.352131] audit(1193566255.096:1): initialized
[   10.352212] highmem bounce pool size: 64 pages
[   10.353974] VFS: Disk quotas dquot_6.5.1
[   10.354023] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.354122] io scheduler noop registered
[   10.354124] io scheduler anticipatory registered
[   10.354126] io scheduler deadline registered
[   10.354141] io scheduler cfq registered (default)
[   10.354159] Boot video device is 0000:00:02.0
[   10.354369] isapnp: Scanning for PnP cards...
[   10.707609] isapnp: No Plug & Play device found
[   10.730881] Real Time Clock Driver v1.12ac
[   10.730989] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.731607] ACPI: PCI Interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 17
[   10.731615] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[   10.732134] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.732378] input: Macintosh mouse button emulation as /class/input/input0
[   10.732449] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   10.732713] i8042.c: Detected active multiplexing controller, rev 1.1.
[   10.732759] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.732763] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   10.732766] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   10.732768] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   10.732771] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   10.732937] mice: PS/2 mouse device common for all mice
[   10.733176] EISA: Probing bus 0 at eisa.0
[   10.733185] Cannot allocate resource for EISA slot 1
[   10.733188] Cannot allocate resource for EISA slot 2
[   10.733190] Cannot allocate resource for EISA slot 3
[   10.733210] EISA: Detected 0 cards.
[   10.733381] TCP cubic registered
[   10.733400] NET: Registered protocol family 1
[   10.733426] Using IPI No-Shortcut mode
[   10.733615]   Magic number: 11:803:174
[   10.733646]   hash matches device ttyr0
[   10.733743]   hash matches device device:0a
[   10.733962] Freeing unused kernel memory: 364k freed
[   10.812139] input: AT Translated Set 2 keyboard as /class/input/input1
[   11.937553] AppArmor: AppArmor initialized<5>audit(1193566256.596:2):  type=1505 info="AppArmor initialized" pid=1235
[   11.945499] fuse init (API version 7.8)
[   11.950734] Failure registering capabilities with primary security module.
[   11.963554] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   11.963560] ACPI: Processor [CPU0] (supports 8 throttling states)
[   11.963571] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   11.978627] md: linear personality registered for level -1
[   11.982822] md: multipath personality registered for level -4
[   11.986806] md: raid0 personality registered for level 0
[   11.991339] md: raid1 personality registered for level 1
[   11.995233] raid5: automatically using best checksumming function: pIII_sse
[   12.014348]    pIII_sse  :  4422.000 MB/sec
[   12.014351] raid5: using function: pIII_sse (4422.000 MB/sec)
[   12.082294] raid6: int32x1    569 MB/s
[   12.150155] raid6: int32x2    676 MB/s
[   12.218156] raid6: int32x4    502 MB/s
[   12.285964] raid6: int32x8    456 MB/s
[   12.353869] raid6: mmxx1     1685 MB/s
[   12.421776] raid6: mmxx2     1998 MB/s
[   12.489708] raid6: sse1x1    1238 MB/s
[   12.557571] raid6: sse1x2    2051 MB/s
[   12.625494] raid6: sse2x1    2236 MB/s
[   12.693382] raid6: sse2x2    2492 MB/s
[   12.693384] raid6: using algorithm sse2x2 (2492 MB/s)
[   12.693387] md: raid6 personality registered for level 6
[   12.693389] md: raid5 personality registered for level 5
[   12.693391] md: raid4 personality registered for level 4
[   12.718052] md: raid10 personality registered for level 10
[   13.115715] usbcore: registered new interface driver usbfs
[   13.115739] usbcore: registered new interface driver hub
[   13.115757] usbcore: registered new device driver usb
[   13.116540] USB Universal Host Controller Interface driver v3.0
[   13.116605] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.116616] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   13.116620] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   13.116818] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   13.116843] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001820
[   13.116947] usb usb1: configuration #1 chosen from 1 choice
[   13.116970] hub 1-0:1.0: USB hub found
[   13.116976] hub 1-0:1.0: 2 ports detected
[   13.194377] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   13.220787] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   13.220801] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   13.220805] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   13.220828] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   13.220854] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00001840
[   13.220952] usb usb2: configuration #1 chosen from 1 choice
[   13.220977] hub 2-0:1.0: USB hub found
[   13.220984] hub 2-0:1.0: 2 ports detected
[   13.247501] SCSI subsystem initialized
[   13.252862] libata version 2.21 loaded.
[   13.324619] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   13.324632] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   13.324637] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   13.324659] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   13.324685] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00001860
[   13.324781] usb usb3: configuration #1 chosen from 1 choice
[   13.324806] hub 3-0:1.0: USB hub found
[   13.324813] hub 3-0:1.0: 2 ports detected
[   13.429127] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20
[   13.429142] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   13.429146] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   13.429172] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   13.429204] ehci_hcd 0000:00:1d.7: debug port 1
[   13.429211] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   13.429223] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xe0100000
[   13.433103] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.433180] usb usb4: configuration #1 chosen from 1 choice
[   13.433205] hub 4-0:1.0: USB hub found
[   13.433213] hub 4-0:1.0: 6 ports detected
[    4.536000] Marking TSC unstable due to: possible TSC halt in C2.
[    4.556000] Time: acpi_pm clocksource has been installed.
[    4.576000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 21
[    4.628000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[e0201000-e02017ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.632000] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    4.632000] 8139cp 0000:02:01.0: Try the "8139too" driver instead.
[    4.648000] 8139too Fast Ethernet driver 0.9.28
[    4.648000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 21 (level, low) -> IRQ 22
[    4.648000] eth0: RealTek RTL8139 at 0xf887a800, 00:0f:b0:38:62:b9, IRQ 22
[    4.648000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.648000] ata_piix 0000:00:1f.1: version 2.11
[    4.648000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    4.648000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[    4.648000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.648000] scsi0 : ata_piix
[    4.648000] scsi1 : ata_piix
[    4.648000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    4.648000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    4.812000] ata1.00: ATA-6: TOSHIBA MK1234GAX, AC001A, max UDMA/100
[    4.812000] ata1.00: 234441648 sectors, multi 16: LBA48 
[    4.820000] ata1.00: configured for UDMA/100
[    5.024000] usb 4-3: new high speed USB device using ehci_hcd and address 2
[    5.140000] ata2.00: ATAPI: MATSHITADVD-RAM UJ-820S, 1.50, max UDMA/33
[    5.156000] usb 4-3: configuration #1 chosen from 1 choice
[    5.156000] hub 4-3:1.0: USB hub found
[    5.156000] hub 4-3:1.0: 4 ports detected
[    5.312000] ata2.00: configured for UDMA/33
[    5.312000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1234GA AC00 PQ: 0 ANSI: 5
[    5.312000] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-820S  1.50 PQ: 0 ANSI: 5
[    5.324000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    5.324000] sd 0:0:0:0: [sda] Write Protect is off
[    5.324000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.324000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.324000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    5.324000] sd 0:0:0:0: [sda] Write Protect is off
[    5.324000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.324000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.324000]  sda: sda1 sda2 sda4 < sda5 sda6 sda7 sda8 >
[    5.408000] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.412000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.412000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.428000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.428000] Uniform CD-ROM driver Revision: 3.20
[    5.428000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.716000] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    5.780000] Attempting manual resume
[    5.780000] swsusp: Resume From Partition 8:5
[    5.780000] PM: Checking swsusp image.
[    5.784000] PM: Resume from disk failed.
[    5.784000] swsusp: Basic memory bitmaps created
[    5.796000] swsusp: Basic memory bitmaps freed
[    5.816000] kjournald starting.  Commit interval 5 seconds
[    5.816000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.888000] usb 3-1: configuration #1 chosen from 1 choice
[    5.904000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f4a6540a9ad]
[   16.284000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.312000] Netfilter messages via NETLINK v0.30.
[   16.324000] nf_conntrack version 0.5.0 (8192 buckets, 65536 max)
[   17.956000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.960000] agpgart: Detected an Intel 855GM Chipset.
[   17.960000] agpgart: Detected 32636K stolen memory.
[   17.968000] agpgart: AGP aperture is 128M @ 0xe8000000
[   18.864000] iTCO_vendor_support: vendor-support=0
[   19.004000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   19.012000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   19.012000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   19.072000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.076000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.184000] usbcore: registered new interface driver hiddev
[   19.196000] input: Logitech Optical USB Mouse as /class/input/input2
[   19.196000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.2-1
[   19.196000] usbcore: registered new interface driver usbhid
[   19.196000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   19.440000] input: PS/2 Mouse as /class/input/input3
[   19.456000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   19.576000] intel_rng: FWH not detected
[   19.736000] ieee80211_crypt: registered algorithm 'NULL'
[   19.748000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   19.748000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   19.764000] Yenta: CardBus bridge found at 0000:02:04.0 [1179:ff01]
[   19.764000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   19.764000] Yenta: Routing CardBus interrupts to PCI
[   19.764000] Yenta TI: socket 0000:02:04.0, mfunc 0x89501212, devctl 0x44
[   19.784000] sdhci: Secure Digital Host Controller Interface driver
[   19.784000] sdhci: Copyright(c) Pierre Ossman
[   19.864000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   19.864000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   20.028000] Yenta: ISA IRQ mask 0x0060, PCI irq 16
[   20.028000] Socket status: 30000006
[   20.028000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   20.028000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   20.028000] cs: IO port probe 0x3000-0x3fff: clean.
[   20.028000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[   20.028000] pcmcia: parent PCI bridge Memory window: 0x70000000 - 0x73ffffff
[   20.028000] sdhci: SDHCI controller found at 0000:02:04.2 [1524:0550] (rev 0)
[   20.028000] ACPI: PCI Interrupt 0000:02:04.2[B] -> GSI 17 (level, low) -> IRQ 17
[   20.028000] mmc0: SDHCI at 0xe0202000 irq 17 DMA
[   20.032000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 23
[   20.052000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   20.256000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   20.256000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
[   20.256000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   20.380000] cs: IO port probe 0x100-0x3af: clean.
[   20.384000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   20.384000] cs: IO port probe 0x820-0x8ff: clean.
[   20.384000] cs: IO port probe 0xc00-0xcf7: clean.
[   20.384000] cs: IO port probe 0xa00-0xaff: clean.
[   21.084000] intel8x0_measure_ac97_clock: measured 55466 usecs
[   21.084000] intel8x0: clocking to 48000
[   21.988000] lp: driver loaded but no devices found
[   22.160000] omnibook: Driver version 2.20070211-trunk.
[   22.160000] omnibook: Forced load with EC type 12.
[   22.188000] omnibook: check_default_state timeout.
[   22.188000] omnibook: EC state check failure, please report.
[   22.188000] omnibook: LCD backlight turn off at console blanking is enabled.
[   22.220000] omnibook: Enabled features: blank bluetooth display dmi version lcd temperature wifi throttling.
[   22.248000] Adding 1638556k swap on /dev/sda5.  Priority:-1 extents:1 across:1638556k
[   22.708000] EXT3 FS on sda8, internal journal
[   24.492000] kjournald starting.  Commit interval 5 seconds
[   24.492000] EXT3 FS on sda6, internal journal
[   24.492000] EXT3-fs: mounted filesystem with ordered data mode.
[   24.520000] kjournald starting.  Commit interval 5 seconds
[   24.520000] EXT3 FS on sda7, internal journal
[   24.520000] EXT3-fs: mounted filesystem with ordered data mode.
[   25.732000] ACPI: AC Adapter [ACAD] (on-line)
[   25.812000] ACPI: Battery Slot [BAT1] (battery present)
[   25.828000] No dock devices found.
[   25.912000] input: Power Button (FF) as /class/input/input5
[   25.916000] ACPI: Power Button (FF) [PWRF]
[   25.964000] input: Lid Switch as /class/input/input6
[   25.968000] ACPI: Lid Switch [LID]
[   26.016000] input: Power Button (CM) as /class/input/input7
[   26.020000] ACPI: Power Button (CM) [PWRB]
[   26.124000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   28.644000] eth0: link down
[   30.340000] [drm] Initialized drm 1.1.0 20060810
[   30.388000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   30.388000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   30.388000] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   31.784000] ppdev: user-space parallel port driver
[   32.336000] audit(1193580687.194:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4770 profile="/usr/sbin/cupsd"
[   36.960000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   36.960000] apm: overridden by ACPI.
[   46.124000] Clocksource tsc unstable (delta = -222604351 ns)
[   49.336000] Failure registering capabilities with primary security module.
[   49.748000] Bluetooth: Core ver 2.11
[   49.748000] NET: Registered protocol family 31
[   49.748000] Bluetooth: HCI device and connection manager initialized
[   49.748000] Bluetooth: HCI socket layer initialized
[   49.800000] Bluetooth: L2CAP ver 2.8
[   49.800000] Bluetooth: L2CAP socket layer initialized
[   49.964000] Bluetooth: RFCOMM socket layer initialized
[   49.964000] Bluetooth: RFCOMM TTY layer initialized
[   49.964000] Bluetooth: RFCOMM ver 1.8
[   50.600000] NET: Registered protocol family 10
[   50.600000] lo: Disabled Privacy Extensions
[   50.600000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   50.600000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   78.612000] NET: Registered protocol family 17
[   78.760000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   89.056000] eth1: no IPv6 routers present
[  107.228000] eth1: no IPv6 routers present
[  136.980000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  138.420000] ieee80211_crypt: registered algorithm 'WEP'
[  138.780000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  155.616000] eth1: no IPv6 routers present
```

---

### Post by loud_tiger on 2007-10-28
same

---

### Post by Metaleks on 2007-10-28
I guess I'll add my name to this ever-growing list.  Boot-time is horrible.

I too, like the majority of you, am using 64 bit Gutsy (Intel Core 2 Duo for me).

---

### Post by Nonno Bassotto on 2007-10-28
Do you mean boot time or login time? This thread is about the login (from when you enter your username and password to when you get a usable desktop).

---

### Post by #Reistlehr- on 2007-10-28
Ok. I think i see two seperate problems emerging.

Problem one: You get your gnome-panel, your taskbar, and nothing else except a mouse. You have no wall papper, and you have no functionality for however many seconds. You can see some icons in the start bar.

Problem two: After you login, you have absolutly no GUI on the desktop. It goes from the login screen, to nothing for however long, (The average complaint is 30 seconds). You may notice a flash of the panel, but that's it untill the desktop is created. You have a mouse, but no functionality.

They both seem to be problems with xsession it seems. ALthough, uninstalling ccsm (compizconfig-setting-manager) seems to fix the problem, but taht means no cool effects. 

I'm in the proccess of examining multiple working, and non working xsession logs, a long with dmesg scripts, to see what the cause of the problem might be. I'll be working on this for some more time, to see what i can find. 

So far, there have been no updates to the bug report even though the list is ever growing. 

I'll update you all when i find some more useful information. 

(I can't reproduce this bug on i386, but i can on AMD64, on a total of 4 machines (2 x86_64, 2 i386)

---

### Post by neilbags on 2007-10-28
I get this problem too. After upgrading from 7.04 to 7.10 It hangs while loading gnome after I log in with my username and password.

I am running x86_64.
I've tried with a new user but have the same problem.
I've tried with and without nvidia-glx and with and without compiz.
I've tried disabling everything that starts with gnome (System->Administration->Settings).

Here is my dmesg:
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: root=/dev/md0 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fe8ac00 (usable)
[    0.000000]  BIOS-e820: 000000003fe8ac00 - 000000003fe8cc00 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fe8cc00 - 000000003fe8ec00 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fe8ec00 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 160) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261770) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FEC30 checksum 0
[    0.000000] ACPI: RSDP 000FEC30, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 000FCB47, 0054 (r1 DELL    WS 670         7 ASL        61)
[    0.000000] ACPI: FACP 000FCBAB, 0074 (r1 DELL    WS 670         7 ASL        61)
[    0.000000] ACPI: DSDT FFFD8BC3, 3116 (r1   DELL    dt_ex     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 3FE8AC00, 0040
[    0.000000] ACPI: SSDT FFFDBCD9, 00A7 (r1   DELL    st_ex     1000 MSFT  100000D)
[    0.000000] ACPI: APIC 000FCC1F, 00AA (r1 DELL    WS 670         7 ASL        61)
[    0.000000] ACPI: BOOT 000FCCC9, 0028 (r1 DELL    WS 670         7 ASL        61)
[    0.000000] ACPI: ASF! 000FCCF1, 0067 (r16 DELL    WS 670         7 ASL        61)
[    0.000000] ACPI: MCFG 000FCD58, 003E (r1 DELL    WS 670         7 ASL        61)
[    0.000000] ACPI: HPET 000FCD96, 0038 (r1 DELL    WS 670         7 ASL        61)
[    0.000000] ACPI: SSDT 3FE8AC40, 01B7 (r1 DpgPmm  Cpu0Ist       11 INTL 20030522)
[    0.000000] ACPI: SSDT 3FE8B049, 01B7 (r1 DpgPmm  Cpu1Ist       11 INTL 20030522)
[    0.000000] ACPI: SSDT 3FE8B452, 01B7 (r1 DpgPmm  Cpu2Ist       11 INTL 20030522)
[    0.000000] ACPI: SSDT 3FE8B85B, 01B7 (r1 DpgPmm  Cpu3Ist       11 INTL 20030522)
[    0.000000] ACPI: SSDT 3FE8BC64, 0244 (r1 DpgPmm    CpuPm       10 INTL 20030522)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003fe8a000
[    0.000000] Entering add_active_range(0, 0, 160) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261770) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000003fe8a000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      160
[    0.000000]     0:      256 ->   261770
[    0.000000] On node 0 totalpages: 261674
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1124 pages reserved
[    0.000000]   DMA zone: 2820 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3522 pages used for memmap
[    0.000000]   DMA32 zone: 254152 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x06] enabled)
[    0.000000] Processor #6
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x09] address[0xfec80000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 9, address 0xfec80000, GSI 24-47
[    0.000000] ACPI: IOAPIC (id[0x0a] address[0xfec80800] gsi_base[48])
[    0.000000] IOAPIC[2]: apic_id 10, address 0xfec80800, GSI 48-71
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] SMP: Allowing 8 CPUs, 6 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 256972
[    0.000000] Kernel command line: root=/dev/md0 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   14.053532] time.c: Detected 3790.747 MHz processor.
[   14.055189] Console: colour VGA+ 80x25
[   14.055206] Checking aperture...
[   14.055215] Calgary: detecting Calgary via BIOS EBDA area
[   14.055217] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   14.064870] Memory: 1019980k/1047080k available (2274k kernel code, 26716k reserved, 1181k data, 296k init)
[   14.064911] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=8, Nodes=1
[   14.143110] Calibrating delay using timer specific routine.. 7586.24 BogoMIPS (lpj=15172498)
[   14.143141] Security Framework v1.0.0 initialized
[   14.143148] SELinux:  Disabled at boot.
[   14.143276] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   14.143986] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   14.144305] Mount-cache hash table entries: 256
[   14.144434] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   14.144437] CPU: L2 cache: 2048K
[   14.144439] CPU 0/0 -> Node 0
[   14.144441] using mwait in idle threads.
[   14.144443] CPU: Physical Processor ID: 0
[   14.144444] CPU: Processor Core ID: 0
[   14.144453] CPU0: Thermal monitoring enabled (TM1)
[   14.144464] SMP alternatives: switching to UP code
[   14.144760] Early unpacking initramfs... done
[   14.399841] ACPI: Core revision 20070126
[   14.415018] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.485724] Using local APIC timer interrupts.
[   14.512094] result 12469491
[   14.512095] Detected 12.469 MHz APIC timer.
[   14.514989] SMP alternatives: switching to SMP code
[   14.515113] Booting processor 1/2 APIC 0x6
[   14.525609] Initializing CPU#1
[   14.602884] Calibrating delay using timer specific routine.. 7581.64 BogoMIPS (lpj=15163295)
[   14.602893] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   14.602895] CPU: L2 cache: 2048K
[   14.602897] CPU 1/6 -> Node 0
[   14.602899] CPU: Physical Processor ID: 3
[   14.602900] CPU: Processor Core ID: 0
[   14.602908] CPU1: Thermal monitoring enabled (TM2)
[   14.603210]                   Intel(R) Xeon(TM) CPU 3.80GHz stepping 03
[   14.603291] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   14.626885] Brought up 2 CPUs
[   14.949788] migration_cost=1809
[   14.950012] NET: Registered protocol family 16
[   14.950099] ACPI: bus type pci registered
[   14.950107] PCI: Using configuration type 1
[   14.951209] ACPI: EC: Look up EC in DSDT
[   14.974758] ACPI: System BIOS is requesting _OSI(Linux)
[   14.974760] ACPI: Please test with "acpi_osi=!Linux"
[   14.974761] Please send dmidecode to linux-acpi@vger.kernel.org
[   14.982722] ACPI: Interpreter enabled
[   14.982726] ACPI: (supports S0 S1 S3 S4 S5)
[   14.982744] ACPI: Using IOAPIC for interrupt routing
[   15.040523] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.040536] PCI: Probing PCI hardware (bus 00)
[   15.041016] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   15.041019] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[   15.041241] PCI: PXH quirk detected, disabling MSI for SHPC device
[   15.041276] PCI: PXH quirk detected, disabling MSI for SHPC device
[   15.041922] PCI: Transparent bridge - 0000:00:1e.0
[   15.041978] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.042366] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   15.044363] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1.PCI2._PRT]
[   15.046315] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1.PCI3._PRT]
[   15.048318] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[   15.048548] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI5._PRT]
[   15.048775] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI6._PRT]
[   15.461142] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   15.461435] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   15.461724] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   15.462013] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   15.462298] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   15.462590] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   15.462876] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   15.463166] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[   15.463294] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.463305] pnp: PnP ACPI init
[   15.463313] ACPI: bus type pnp registered
[   15.488912] pnp: PnP ACPI: found 12 devices
[   15.488915] ACPI: ACPI bus type pnp unregistered
[   15.488966] PCI: Using ACPI for IRQ routing
[   15.488968] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.489051] NET: Registered protocol family 8
[   15.489053] NET: Registered protocol family 20
[   15.489068] PCI-GART: No AMD northbridge found.
[   15.489073] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   15.489077] hpet0: 3 64-bit timers, 14318180 Hz
[   15.490124] pnp: 00:01: ioport range 0x800-0x85f has been reserved
[   15.490127] pnp: 00:01: ioport range 0xc00-0xc7f has been reserved
[   15.490129] pnp: 00:01: ioport range 0x860-0x8ff could not be reserved
[   15.490433] PCI: Bridge: 0000:01:00.0
[   15.490435]   IO window: disabled.
[   15.490438]   MEM window: disabled.
[   15.490441]   PREFETCH window: disabled.
[   15.490446] PCI: Bridge: 0000:01:00.2
[   15.490448]   IO window: d000-dfff
[   15.490452]   MEM window: dfd00000-dfefffff
[   15.490456]   PREFETCH window: 50000000-500fffff
[   15.490458] Time: tsc clocksource has been installed.
[   15.490464] PCI: Bridge: 0000:00:02.0
[   15.490466]   IO window: d000-dfff
[   15.490470]   MEM window: dfd00000-dfefffff
[   15.490473]   PREFETCH window: 50000000-500fffff
[   15.490477] PCI: Bridge: 0000:00:03.0
[   15.490478]   IO window: disabled.
[   15.490482]   MEM window: dfc00000-dfcfffff
[   15.490485]   PREFETCH window: disabled.
[   15.490489] PCI: Bridge: 0000:00:04.0
[   15.490490]   IO window: disabled.
[   15.490494]   MEM window: dd000000-dfbfffff
[   15.490497]   PREFETCH window: c0000000-cfffffff
[   15.490501] PCI: Bridge: 0000:00:1e.0
[   15.490502]   IO window: disabled.
[   15.490506]   MEM window: dcf00000-dcffffff
[   15.490510]   PREFETCH window: disabled.
[   15.490524] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   15.490529] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   15.490543] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   15.490556] PCI: Setting latency timer of device 0000:01:00.2 to 64
[   15.490564] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 16 (level, low) -> IRQ 16
[   15.490568] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   15.490577] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   15.490581] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   15.490588] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   15.490597] NET: Registered protocol family 2
[   15.523413] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   15.523847] TCP established hash table entries: 131072 (order: 9, 3145728 bytes)
[   15.525440] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   15.526075] TCP: Hash tables configured (established 131072 bind 65536)
[   15.526078] TCP reno registered
[   15.535547] checking if image is initramfs... it is
[   16.035738] Freeing initrd memory: 7513k freed
[   16.040112] Simple Boot Flag at 0x7a set to 0x1
[   16.040484] audit: initializing netlink socket (disabled)
[   16.040495] audit(1193663645.952:1): initialized
[   16.042444] VFS: Disk quotas dquot_6.5.1
[   16.042495] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   16.042576] io scheduler noop registered
[   16.042578] io scheduler anticipatory registered
[   16.042580] io scheduler deadline registered
[   16.042668] io scheduler cfq registered (default)
[   16.059767] Boot video device is 0000:05:00.0
[   16.059895] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   16.059922] Allocate Port Service[0000:00:02.0:pcie00]
[   16.060005] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   16.060031] Allocate Port Service[0000:00:03.0:pcie00]
[   16.060109] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   16.060135] Allocate Port Service[0000:00:04.0:pcie00]
[   16.082102] Real Time Clock Driver v1.12ac
[   16.082190] Linux agpgart interface v0.102 (c) Dave Jones
[   16.082193] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.082285] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.082404] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   16.082950] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.083157] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   16.083791] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.084006] input: Macintosh mouse button emulation as /class/input/input0
[   16.084084] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[   16.086965] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.086970] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.087130] mice: PS/2 mouse device common for all mice
[   16.087274] TCP cubic registered
[   16.087284] NET: Registered protocol family 1
[   16.087503] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   16.087511] Freeing unused kernel memory: 296k freed
[   16.125068] input: AT Translated Set 2 keyboard as /class/input/input1
[   17.263930] AppArmor: AppArmor initialized<5>audit(1193663647.176:2):  type=1505 info="AppArmor initialized" pid=1209
[   17.269187] fuse init (API version 7.8)
[   17.273201] Failure registering capabilities with primary security module.
[   17.307090] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   17.307102] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   17.307114] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   17.307125] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   17.307137] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   17.307151] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   17.317582] md: linear personality registered for level -1
[   17.320492] md: multipath personality registered for level -4
[   17.323397] md: raid0 personality registered for level 0
[   17.326385] md: raid1 personality registered for level 1
[   17.329007] raid5: automatically using best checksumming function: generic_sse
[   17.345563]    generic_sse:  5789.000 MB/sec
[   17.345565] raid5: using function: generic_sse (5789.000 MB/sec)
[   17.413533] raid6: int64x1   1859 MB/s
[   17.481517] raid6: int64x2   2666 MB/s
[   17.549476] raid6: int64x4   2826 MB/s
[   17.617451] raid6: int64x8   2116 MB/s
[   17.685418] raid6: sse2x1    2852 MB/s
[   17.753365] raid6: sse2x2    4158 MB/s
[   17.821340] raid6: sse2x4    3958 MB/s
[   17.821342] raid6: using algorithm sse2x2 (4158 MB/s)
[   17.821344] md: raid6 personality registered for level 6
[   17.821345] md: raid5 personality registered for level 5
[   17.821347] md: raid4 personality registered for level 4
[   17.836652] md: raid10 personality registered for level 10
[   18.278651] usbcore: registered new interface driver usbfs
[   18.278685] usbcore: registered new interface driver hub
[   18.285817] usbcore: registered new device driver usb
[   18.288822] USB Universal Host Controller Interface driver v3.0
[   18.288900] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   18.288913] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   18.288916] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   18.289091] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   18.289122] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[   18.289247] usb usb1: configuration #1 chosen from 1 choice
[   18.289272] hub 1-0:1.0: USB hub found
[   18.289278] hub 1-0:1.0: 2 ports detected
[   18.333221] SCSI subsystem initialized
[   18.337023] libata version 2.21 loaded.
[   18.352626] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   18.352629] Copyright (c) 1999-2006 Intel Corporation.
[   18.357548] Floppy drive(s): fd0 is 1.44M
[   18.378227] FDC 0 is a post-1991 82077
[   18.397200] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   18.397212] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   18.397216] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   18.397394] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   18.397420] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[   18.397821] usb usb2: configuration #1 chosen from 1 choice
[   18.398001] hub 2-0:1.0: USB hub found
[   18.398007] hub 2-0:1.0: 2 ports detected
[   18.505129] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   18.505138] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   18.505141] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   18.505321] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   18.505343] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[   18.505746] usb usb3: configuration #1 chosen from 1 choice
[   18.505935] hub 3-0:1.0: USB hub found
[   18.505941] hub 3-0:1.0: 2 ports detected
[   18.613108] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   18.613115] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   18.613119] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   18.613304] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   18.613324] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ff20
[   18.613747] usb usb4: configuration #1 chosen from 1 choice
[   18.613944] hub 4-0:1.0: USB hub found
[   18.613949] hub 4-0:1.0: 2 ports detected
[   18.722974] ata_piix 0000:00:1f.1: version 2.11
[   18.722991] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   18.723032] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   18.723119] scsi0 : ata_piix
[   18.723166] scsi1 : ata_piix
[   18.723192] ata1: PATA max UDMA/133 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x000000000001ffa0 irq 14
[   18.723196] ata2: PATA max UDMA/133 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x000000000001ffa8 irq 15
[   18.723214] ata1: port disabled. ignoring.
[   19.175890] ata2.01: ATAPI: SONY    DVD RW DRU-710A, BY01, max UDMA/66
[   19.175897] ata2.01: limited to UDMA/33 due to 40-wire cable
[   19.347819] ata2.01: configured for UDMA/33
[   19.348719] scsi 1:0:1:0: CD-ROM            SONY     DVD RW DRU-710A  BY01 PQ: 0 ANSI: 5
[   19.349170] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   19.349188] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[   19.349223] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   19.349271] scsi2 : ata_piix
[   19.349514] scsi3 : ata_piix
[   19.349723] ata3: SATA max UDMA/133 cmd 0x000000000001fe00 ctl 0x000000000001fe12 bmdma 0x000000000001fea0 irq 18
[   19.349726] ata4: SATA max UDMA/133 cmd 0x000000000001fe20 ctl 0x000000000001fe32 bmdma 0x000000000001fea8 irq 18
[   19.515917] ata3.00: ATA-6: ST3160827AS, 3.42, max UDMA/133
[   19.515922] ata3.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 0/32)
[   19.536696] ata3.00: configured for UDMA/133
[   19.703844] ata4.00: ATA-6: ST3160827AS, 3.42, max UDMA/133
[   19.703847] ata4.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 0/32)
[   19.724662] ata4.00: configured for UDMA/133
[   19.724762] scsi 2:0:0:0: Direct-Access     ATA      ST3160827AS      3.42 PQ: 0 ANSI: 5
[   19.725194] scsi 3:0:0:0: Direct-Access     ATA      ST3160827AS      3.42 PQ: 0 ANSI: 5
[   19.725605] ACPI: PCI Interrupt 0000:06:0c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.775798] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[dcffb800-dcffbfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   19.776934] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
[   19.777581] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   19.777588] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   19.777643] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   19.777685] ehci_hcd 0000:00:1d.7: debug port 1
[   19.777691] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   19.777704] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800
[   19.781590] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   19.781687] usb usb5: configuration #1 chosen from 1 choice
[   19.781715] hub 5-0:1.0: USB hub found
[   19.781721] hub 5-0:1.0: 8 ports detected
[   19.791168] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   19.791174] Uniform CD-ROM driver Revision: 3.20
[   19.791229] sr 1:0:1:0: Attached scsi CD-ROM sr0
[   19.791404] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   19.791416] sd 2:0:0:0: [sda] Write Protect is off
[   19.791418] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.791437] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.791481] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   19.791492] sd 2:0:0:0: [sda] Write Protect is off
[   19.791494] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.791518] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.791522]  sda:<5>sr 1:0:1:0: Attached scsi generic sg0 type 5
[   19.794344] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   19.794365] scsi 3:0:0:0: Attached scsi generic sg2 type 0
[   19.807592]  sda1 sda2
[   19.808186] sd 2:0:0:0: [sda] Attached SCSI disk
[   19.808519] sd 3:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   19.809053] sd 3:0:0:0: [sdb] Write Protect is off
[   19.809055] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   19.809076] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.809125] sd 3:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   19.809136] sd 3:0:0:0: [sdb] Write Protect is off
[   19.809138] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   19.809155] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.809159]  sdb: sdb1 sdb2
[   19.817107] sd 3:0:0:0: [sdb] Attached SCSI disk
[   19.887866] ACPI: PCI Interrupt 0000:03:0d.0[A] -> GSI 49 (level, low) -> IRQ 49
[   19.948529] md: md0 stopped.
[   19.953390] md: bind<sda2>
[   19.953573] md: bind<sdb2>
[   19.953594] md: md0: raid array is not clean -- starting background reconstruction
[   19.959742] raid1: raid set md0 active with 2 out of 2 mirrors
[   19.959800] md: resync of RAID array md0
[   19.959803] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[   19.959806] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
[   19.959811] md: using 128k window, over a total of 155790272 blocks.
[   20.155478] e1000: 0000:03:0d.0: e1000_probe: (PCI-X:100MHz:64-bit) 00:04:23:c9:2a:fa
[   20.189900] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   20.189936] ACPI: PCI Interrupt 0000:03:0d.1[B] -> GSI 50 (level, low) -> IRQ 50
[   20.458495] e1000: 0000:03:0d.1: e1000_probe: (PCI-X:100MHz:64-bit) 00:04:23:c9:2a:fb
[   20.470063] Attempting manual resume
[   20.470067] swsusp: Resume From Partition 8:1
[   20.470068] PM: Checking swsusp image.
[   20.470234] PM: Resume from disk failed.
[   20.477831] ReiserFS: md0: found reiserfs format "3.6" with standard journal
[   20.477845] ReiserFS: md0: using ordered data mode
[   20.481366] ReiserFS: md0: journal params: device md0, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   20.481963] ReiserFS: md0: checking transaction log (md0)
[   20.493933] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
[   20.493973] ACPI: PCI Interrupt 0000:03:0e.0[A] -> GSI 48 (level, low) -> IRQ 48
[   20.546273] ReiserFS: md0: Using r5 hash to sort names
[   20.762718] e1000: 0000:03:0e.0: e1000_probe: (PCI-X:100MHz:64-bit) 00:14:22:2b:c5:22
[   20.801291] e1000: eth2: e1000_probe: Intel(R) PRO/1000 Network Connection
[   21.044601] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[802b0014c5222200]
[   28.738999] e1000: eth2: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   30.062984] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.065073] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.179835] EDAC MC: Ver: 2.0.1 Oct 14 2007
[   30.181185] EDAC e752x: tolm = 40000, remapbase = ffc000, remaplimit = 0
[   30.181251] EDAC MC0: Giving out device to e752x_edac E7525: DEV 0000:00:00.0
[   30.948587] NET: Registered protocol family 10
[   30.948698] lo: Disabled Privacy Extensions
[   30.948877] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.949025] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   31.023350] intel_rng: FWH not detected
[   31.056397] parport_pc 00:09: reported by Plug and Play ACPI
[   31.056447] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   31.105587] input: PC Speaker as /class/input/input2
[   31.360064] input: PS2++ Logitech TrackMan as /class/input/input3
[   31.381357] iTCO_vendor_support: vendor-support=0
[   31.382542] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   31.382612] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   31.382621] iTCO_wdt: No card detected
[   31.545419] nvidia: module license 'NVIDIA' taints kernel.
[   31.812782] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.812793] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   31.812934] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
[   31.969817] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
[   31.971096] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   32.390841] intel8x0_measure_ac97_clock: measured 55166 usecs
[   32.390845] intel8x0: clocking to 48000
[   33.250258] lp0: using parport0 (interrupt-driven).
[   33.351072] Adding 497972k swap on /dev/sdb1.  Priority:-1 extents:1 across:497972k
[   33.351365] Adding 497972k swap on /dev/sda1.  Priority:-2 extents:1 across:497972k
[   41.898839] eth2: no IPv6 routers present
[   48.098021] No dock devices found.
[   48.161556] input: Power Button (FF) as /class/input/input4
[   48.161805] ACPI: Power Button (FF) [PWRF]
[   48.162964] input: Power Button (CM) as /class/input/input5
[   48.163191] ACPI: Power Button (CM) [VBTN]
[   52.534743] ppdev: user-space parallel port driver
[   53.041440] audit(1193624083.866:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5119 profile="/usr/sbin/cupsd"
[   53.270349] NET: Registered protocol family 17
[   57.715912] Bluetooth: Core ver 2.11
[   57.715985] NET: Registered protocol family 31
[   57.715988] Bluetooth: HCI device and connection manager initialized
[   57.715994] Bluetooth: HCI socket layer initialized
[   57.832939] Bluetooth: L2CAP ver 2.8
[   57.832945] Bluetooth: L2CAP socket layer initialized
[   57.959380] Bluetooth: RFCOMM socket layer initialized
[   57.959397] Bluetooth: RFCOMM TTY layer initialized
[   57.959401] Bluetooth: RFCOMM ver 1.8
[   62.062074] ip_tables: (C) 2000-2006 Netfilter Core Team
```

---

### Post by mahousaru on 2007-10-29
*grasping at straws*

Is anyone with the slow login to desktop (long brown screen) got the firewall (iptabes) configured?  If so can you try disabling it.  I remember ages ago I borked my suse desktop login with a misconfigured firewall and it took ages for the desktop to appear.

---

### Post by neilbags on 2007-10-29
I'm not running a firewall:

```
neil@shroom:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
fail2ban-ssh  tcp  --  anywhere             anywhere            multiport dports ssh,sftp 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   
```      

```
neil@shroom:~$ sudo iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```

---

### Post by Vaan on 2007-10-29
Here's the output of my dmesg hoping this issue will get solved soon.

```

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d8000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
[    0.000000]  BIOS-e820: 000000001ff70000 - 000000001ff7d000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ff7d000 - 000000001ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 000000002ff80000 - 0000000030000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6470
[    0.000000] Entering add_active_range(0, 0, 130928) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130928
[    0.000000]   HighMem    130928 ->   130928
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130928
[    0.000000] On node 0 totalpages: 130928
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 990 pages used for memmap
[    0.000000]   Normal zone: 125842 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6500 checksum 0
[    0.000000] ACPI: RSDP 000F6500, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 1FF79185, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 1FF7CEED, 0074 (r1 HP     Chinook   6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 1FF791B5, 3D38 (r1     HP    SB200  6040000 INTL 20030509)
[    0.000000] ACPI: FACS 1FF7FFC0, 0040
[    0.000000] ACPI: APIC 1FF7CF61, 0068 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: SSDT 1FF7CFC9, 0037 (r1 PTLTD  ACPIHT    6040000  LTP        1)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:2 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
[    0.000000] Built 1 zonelists.  Total pages: 129906
[    0.000000] Kernel command line: root=UUID=7d26db87-88c9-46fa-bd14-991f3e87f674 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 3000.223 MHz processor.
[   11.650426] Console: colour VGA+ 80x25
[   11.650951] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   11.651331] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   11.663829] Memory: 507660k/523712k available (2015k kernel code, 15528k reserved, 916k data, 364k init, 0k highmem)
[   11.663839] virtual kernel memory layout:
[   11.663840]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   11.663841]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   11.663842]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   11.663843]     lowmem  : 0xc0000000 - 0xdff70000   ( 511 MB)
[   11.663844]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   11.663845]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   11.663846]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   11.663849] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   11.663888] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   11.743836] Calibrating delay using timer specific routine.. 6003.61 BogoMIPS (lpj=12007221)
[   11.743862] Security Framework v1.0.0 initialized
[   11.743870] SELinux:  Disabled at boot.
[   11.743883] Mount-cache hash table entries: 512
[   11.744024] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   11.744036] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   11.744039] CPU: L2 cache: 512K
[   11.744041] CPU: Physical Processor ID: 0
[   11.744044] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000
[   11.744055] Compat vDSO mapped to ffffe000.
[   11.744069] Checking 'hlt' instruction... OK.
[   11.759928] SMP alternatives: switching to UP code
[   11.760417] Early unpacking initramfs... done
[   12.029608] ACPI: Core revision 20070126
[   12.029684] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   12.859536] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   12.859560] SMP alternatives: switching to SMP code
[   12.859716] Booting processor 1/1 eip 3000
[   12.869834] Initializing CPU#1
[   12.946770] Calibrating delay using timer specific routine.. 6000.67 BogoMIPS (lpj=12001347)
[   12.946780] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   12.946791] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   12.946793] CPU: L2 cache: 512K
[   12.946795] CPU: Physical Processor ID: 0
[   12.946798] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000
[   12.947090] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   12.947129] Total of 2 processors activated (12004.28 BogoMIPS).
[   12.947189] ENABLING IO-APIC IRQs
[   12.947361] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   12.987034] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   12.987066] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   12.987069] ...trying to set up timer as Virtual Wire IRQ... works.
[   13.134746] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   13.154744] Brought up 2 CPUs
[   13.230256] migration_cost=166
[   13.230467] Booting paravirtualized kernel on bare hardware
[   13.230529] Time: 19:23:38  Date: 09/28/107
[   13.230569] NET: Registered protocol family 16
[   13.230701] EISA bus registered
[   13.230708] ACPI: bus type pci registered
[   13.230781] PCI: PCI BIOS revision 2.10 entry at 0xfd968, last bus=2
[   13.230783] PCI: Using configuration type 1
[   13.230785] Setting up standard PCI resources
[   13.238644] ACPI: EC: Look up EC in DSDT
[   13.244462] ACPI: EC: GPE=0x06, ports=0x66, 0x62
[   13.245385] ACPI: Interpreter enabled
[   13.245390] ACPI: (supports S0 S3 S4 S5)
[   13.245411] ACPI: Using IOAPIC for interrupt routing
[   13.302748] ACPI: EC: GPE=0x06, ports=0x66, 0x62
[   13.302808] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.302820] PCI: Probing PCI hardware (bus 00)
[   13.303832] PCI: Transparent bridge - 0000:00:14.4
[   13.303970] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.304071] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[   13.304150] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   13.306325] ACPI: PCI Interrupt Link [LNK0] (IRQs 5 10 11) *0, disabled.
[   13.306412] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 10 11) *0, disabled.
[   13.306509] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 10 11) *0, disabled.
[   13.306594] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 10 11) *0, disabled.
[   13.306711] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.306731] pnp: PnP ACPI init
[   13.306744] ACPI: bus type pnp registered
[   13.338465] pnp: PnP ACPI: found 10 devices
[   13.338469] ACPI: ACPI bus type pnp unregistered
[   13.338474] PnPBIOS: Disabled by ACPI PNP
[   13.338560] PCI: Using ACPI for IRQ routing
[   13.338564] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.343883] NET: Registered protocol family 8
[   13.343886] NET: Registered protocol family 20
[   13.343997] pnp: 00:07: ioport range 0x200-0x20f has been reserved
[   13.344000] pnp: 00:07: ioport range 0xc14-0xc14 has been reserved
[   13.344003] pnp: 00:07: ioport range 0xc50-0xc52 has been reserved
[   13.344006] pnp: 00:07: ioport range 0xc6c-0xc6c has been reserved
[   13.344009] pnp: 00:07: iomem range 0xe4000-0xfffff could not be reserved
[   13.344011] pnp: 00:07: iomem range 0x100000-0x1fffffff could not be reserved
[   13.344014] pnp: 00:07: iomem range 0xe8000000-0xe8000fff has been reserved
[   13.344017] pnp: 00:07: iomem range 0xfff80000-0xffffffff could not be reserved
[   13.346438] Time: tsc clocksource has been installed.
[   13.374416] PCI: Bridge: 0000:00:01.0
[   13.374420]   IO window: 9000-9fff
[   13.374423]   MEM window: e8100000-e81fffff
[   13.374427]   PREFETCH window: f0000000-f7ffffff
[   13.374442] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[   13.374444]   IO window: 0000a800-0000a8ff
[   13.374448]   IO window: 0000ac00-0000acff
[   13.374452]   PREFETCH window: 40000000-43ffffff
[   13.374457]   MEM window: 4c000000-4fffffff
[   13.374461] PCI: Bus 4, cardbus bridge: 0000:02:04.1
[   13.374463]   IO window: 00001000-000010ff
[   13.374467]   IO window: 00001400-000014ff
[   13.374471]   PREFETCH window: 44000000-47ffffff
[   13.374475]   MEM window: 50000000-53ffffff
[   13.374479] PCI: Bridge: 0000:00:14.4
[   13.374482]   IO window: a000-afff
[   13.374486]   MEM window: e8200000-e82fffff
[   13.374490]   PREFETCH window: 40000000-47ffffff
[   13.374525] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 17 (level, low) -> IRQ 16
[   13.374545] ACPI: PCI Interrupt 0000:02:04.1[B] -> GSI 16 (level, low) -> IRQ 17
[   13.374563] NET: Registered protocol family 2
[   13.414574] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   13.414634] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   13.414790] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   13.414900] TCP: Hash tables configured (established 16384 bind 16384)
[   13.414902] TCP reno registered
[   13.426650] checking if image is initramfs... it is
[   13.873987] Switched to high resolution mode on CPU 0
[   13.874096] Switched to high resolution mode on CPU 1
[   13.971725] Freeing initrd memory: 7119k freed
[   13.972266] audit: initializing netlink socket (disabled)
[   13.972286] audit(1193599418.200:1): initialized
[   13.975008] VFS: Disk quotas dquot_6.5.1
[   13.975092] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   13.975229] io scheduler noop registered
[   13.975231] io scheduler anticipatory registered
[   13.975233] io scheduler deadline registered
[   13.975250] io scheduler cfq registered (default)
[   13.975300] Boot video device is 0000:01:05.0
[   13.975537] isapnp: Scanning for PnP cards...
[   14.328222] isapnp: No Plug & Play device found
[   14.358495] Real Time Clock Driver v1.12ac
[   14.358621] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.359388] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 5 (level, low) -> IRQ 5
[   14.359397] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   14.360109] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.360424] input: Macintosh mouse button emulation as /class/input/input0
[   14.360526] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   14.369416] i8042.c: Detected active multiplexing controller, rev 1.1.
[   14.379237] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.379243] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   14.379246] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   14.379249] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   14.379252] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   14.379519] mice: PS/2 mouse device common for all mice
[   14.380175] EISA: Probing bus 0 at eisa.0
[   14.380183] Cannot allocate resource for EISA slot 1
[   14.380202] Cannot allocate resource for EISA slot 8
[   14.380204] EISA: Detected 0 cards.
[   14.380404] TCP cubic registered
[   14.380424] NET: Registered protocol family 1
[   14.380452] Using IPI No-Shortcut mode
[   14.380871]   Magic number: 11:966:395
[   14.381711] Freeing unused kernel memory: 364k freed
[   14.428122] input: AT Translated Set 2 keyboard as /class/input/input1
[   15.973998] AppArmor: AppArmor initialized<5>audit(1193599420.200:2):  type=1505 info="AppArmor initialized" pid=1194
[   16.099369] fuse init (API version 7.8)
[   16.105350] Failure registering capabilities with primary security module.
[   16.134473] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   16.134496] ACPI: CPU1 (power states: C1[C1] C2[C2])
[   16.139734] ACPI: Thermal Zone [THRM] (34 C)
[   16.933000] usbcore: registered new interface driver usbfs
[   16.933039] usbcore: registered new interface driver hub
[   16.933076] usbcore: registered new device driver usb
[   16.934164] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   16.934212] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 18
[   16.934231] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   16.934469] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   16.934493] ohci_hcd 0000:00:13.0: irq 18, io mem 0xe8001000
[   16.980166] SCSI subsystem initialized
[   16.988040] libata version 2.21 loaded.
[   17.067704] 8139too Fast Ethernet driver 0.9.28
[   17.076419] usb usb1: configuration #1 chosen from 1 choice
[   17.076464] hub 1-0:1.0: USB hub found
[   17.076480] hub 1-0:1.0: 3 ports detected
[   17.179006] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 18
[   17.179037] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   17.179078] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   17.179099] ohci_hcd 0000:00:13.1: irq 18, io mem 0xe8002000
[   17.238846] usb usb2: configuration #1 chosen from 1 choice
[   17.238899] hub 2-0:1.0: USB hub found
[   17.238916] hub 2-0:1.0: 3 ports detected
[   17.342828] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 16 (level, low) -> IRQ 17
[   17.342856] ohci_hcd 0000:02:07.0: OHCI Host Controller
[   17.342902] ohci_hcd 0000:02:07.0: new USB bus registered, assigned bus number 3
[   17.342934] ohci_hcd 0000:02:07.0: irq 17, io mem 0xe8206000
[   17.428459] usb usb3: configuration #1 chosen from 1 choice
[   17.428521] hub 3-0:1.0: USB hub found
[   17.428539] hub 3-0:1.0: 3 ports detected
[   17.531112] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   17.581377] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   17.581386] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   17.582915] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[e8208000-e82087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   17.583087] ACPI: PCI Interrupt 0000:02:07.1[B] -> GSI 18 (level, low) -> IRQ 19
[   17.583119] ohci_hcd 0000:02:07.1: OHCI Host Controller
[   17.583172] ohci_hcd 0000:02:07.1: new USB bus registered, assigned bus number 4
[   17.583201] ohci_hcd 0000:02:07.1: irq 19, io mem 0xe8207000
[   17.668236] usb usb4: configuration #1 chosen from 1 choice
[   17.668293] hub 4-0:1.0: USB hub found
[   17.668316] hub 4-0:1.0: 2 ports detected
[   17.770612] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 19 (level, low) -> IRQ 18
[   17.771051] eth0: RealTek RTL8139 at 0xe081c800, 00:0f:b0:01:c1:d8, IRQ 18
[   17.771055] eth0:  Identified 8139 chip type 'RTL-8101'
[   17.775026] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   17.775988] ACPI: PCI Interrupt 0000:02:07.2[C] -> GSI 19 (level, low) -> IRQ 18
[   17.776013] ehci_hcd 0000:02:07.2: EHCI Host Controller
[   17.776088] ehci_hcd 0000:02:07.2: new USB bus registered, assigned bus number 5
[   17.776205] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   17.776222] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
[   17.776235] ATIIXP: chipset revision 0
[   17.776240] ATIIXP: not 100% native mode: will probe irqs later
[   17.776254]     ide0: BM-DMA at 0x8060-0x8067, BIOS settings: hda:DMA, hdb:pio
[   17.776274]     ide1: BM-DMA at 0x8068-0x806f, BIOS settings: hdc:DMA, hdd:pio
[   17.776294] Probing IDE interface ide0...
[   17.798253] ehci_hcd 0000:02:07.2: irq 18, io mem 0xe8208c00
[   17.850125] usb 3-2: new low speed USB device using ohci_hcd and address 2
[   17.850133] ehci_hcd 0000:02:07.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.850311] usb usb5: configuration #1 chosen from 1 choice
[   17.850362] hub 5-0:1.0: USB hub found
[   17.850376] hub 5-0:1.0: 5 ports detected
[   18.062077] hda: ST9120821A, ATA DISK drive
[   18.733279] hda: selected mode 0x45
[   18.733588] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   18.735426] Probing IDE interface ide1...
[   18.853304] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[463f020064664058]
[   18.897119] usb 3-2: new low speed USB device using ohci_hcd and address 3
[   19.113972] usb 3-2: configuration #1 chosen from 1 choice
[   19.420612] usb 4-2: new full speed USB device using ohci_hcd and address 2
[   19.468723] hdc: HL-DT-ST DVD+RW GCA-4040N, ATAPI CD/DVD-ROM drive
[   19.729365] usb 4-2: configuration #1 chosen from 1 choice
[   19.733738] usbcore: registered new interface driver hiddev
[   19.753589] input: Logitech USB Mouse as /class/input/input2
[   19.753630] input: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:02:07.0-2
[   19.753663] usbcore: registered new interface driver usbhid
[   19.753668] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   19.808249] hdc: selected mode 0x22
[   19.808417] ide1 at 0x170-0x177,0x376 on irq 15
[   19.822794] hda: max request size: 512KiB
[   19.824317] hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[   19.824503] hda: cache flushes supported
[   19.824588]  hda: hda1 hda2 hda3 < hda5 >
[   19.885481] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   19.885499] Uniform CD-ROM driver Revision: 3.20
[   20.076006] floppy0: no floppy controllers found
[   20.193721] Attempting manual resume
[   20.193725] swsusp: Resume From Partition 3:5
[   20.193727] PM: Checking swsusp image.
[   20.193930] PM: Resume from disk failed.
[   20.240654] kjournald starting.  Commit interval 5 seconds
[   20.240671] EXT3-fs: mounted filesystem with ordered data mode.
[   29.707256] eth0: link down
[   30.658249] NET: Registered protocol family 10
[   30.658408] lo: Disabled Privacy Extensions
[   30.658503] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.401956] Linux agpgart interface v0.102 (c) Dave Jones
[   31.479131] agpgart: Detected Ati IGP9100/M chipset
[   31.484938] agpgart: AGP aperture is 32M @ 0xea000000
[   31.515390] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.518381] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.757074] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   31.945304] ieee80211_crypt: registered algorithm 'NULL'
[   32.007372] Yenta: CardBus bridge found at 0000:02:04.0 [103c:006b]
[   32.007393] Yenta: Enabling burst memory read transactions
[   32.007401] Yenta: Using CSCINT to route CSC interrupts to PCI
[   32.007405] Yenta: Routing CardBus interrupts to PCI
[   32.007412] Yenta TI: socket 0000:02:04.0, mfunc 0x01111d22, devctl 0x64
[   32.133897] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   32.133905] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   32.237229] Yenta: ISA IRQ mask 0x0ed8, PCI irq 16
[   32.237235] Socket status: 30000086
[   32.237242] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   32.237247] cs: IO port probe 0xa000-0xafff: clean.
[   32.237614] pcmcia: parent PCI bridge Memory window: 0xe8200000 - 0xe82fffff
[   32.237620] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x47ffffff
[   32.374673] Yenta: CardBus bridge found at 0000:02:04.1 [103c:006b]
[   32.374695] Yenta: Using CSCINT to route CSC interrupts to PCI
[   32.374699] Yenta: Routing CardBus interrupts to PCI
[   32.374706] Yenta TI: socket 0000:02:04.1, mfunc 0x01111d22, devctl 0x64
[   32.400409] bcm43xx driver
[   32.522072] input: PC Speaker as /class/input/input3
[   32.577556] input: PS/2 Mouse as /class/input/input4
[   32.597618] input: AlpsPS/2 ALPS GlidePoint as /class/input/input5
[   32.604878] Yenta: ISA IRQ mask 0x0ed8, PCI irq 17
[   32.604884] Socket status: 30000006
[   32.604889] Yenta: Raising subordinate bus# of parent bus (#02) from #04 to #07
[   32.604897] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   32.604903] cs: IO port probe 0xa000-0xafff: clean.
[   32.605274] pcmcia: parent PCI bridge Memory window: 0xe8200000 - 0xe82fffff
[   32.605280] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x47ffffff
[   32.636365] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 18 (level, low) -> IRQ 19
[   32.924273] parport_pc 00:09: reported by Plug and Play ACPI
[   32.924306] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   32.993359] Bluetooth: Core ver 2.11
[   32.993473] NET: Registered protocol family 31
[   32.993476] Bluetooth: HCI device and connection manager initialized
[   32.993481] Bluetooth: HCI socket layer initialized
[   33.005459] Bluetooth: HCI USB driver ver 2.9
[   33.007135] usbcore: registered new interface driver hci_usb
[   33.240968] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 5 (level, low) -> IRQ 5
[   33.355080] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 5 (level, low) -> IRQ 5
[   33.702290] cs: IO port probe 0x100-0x3af: clean.
[   33.703368] cs: IO port probe 0x100-0x3af: clean.
[   33.704432] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
[   33.704899] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
[   33.705366] cs: IO port probe 0x820-0x8ff: clean.
[   33.705756] cs: IO port probe 0x820-0x8ff: clean.
[   33.706147] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xcd0-0xcd7
[   33.706530] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xcd0-0xcd7
[   33.707042] cs: IO port probe 0xa00-0xaff: clean.
[   33.707618] cs: IO port probe 0xa00-0xaff: clean.
[   35.653035] floppy0: no floppy controllers found
[   36.389644] lp0: using parport0 (interrupt-driven).
[   36.452396] p4-clockmod: P4/Xeon(TM) CPU On-Demand Clock Modulation available
[   36.557735] Adding 626492k swap on /dev/hda5.  Priority:-1 extents:1 across:626492k
[   36.990199] EXT3 FS on hda2, internal journal
[   39.990455] No dock devices found.
[   40.034977] input: Power Button (FF) as /class/input/input6
[   40.035010] ACPI: Power Button (FF) [PWRF]
[   40.035086] input: Lid Switch as /class/input/input7
[   40.035110] ACPI: Lid Switch [LID]
[   40.035166] input: Power Button (CM) as /class/input/input8
[   40.035190] ACPI: Power Button (CM) [PWRB]
[   40.276625] ACPI: Battery Slot [BAT1] (battery present)
[   40.341033] ACPI: AC Adapter [ACAD] (on-line)
[   40.355414] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   70.975052] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   71.631497] [drm] Initialized drm 1.1.0 20060810
[   71.646703] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 16 (level, low) -> IRQ 17
[   71.650943] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   71.787485] ppdev: user-space parallel port driver
[   72.712231] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   72.712257] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   72.712278] agpgart: Putting AGP V3 device at 0000:01:05.0 into 8x mode
[   74.228135] [drm] Setting GART location based on new memory map
[   74.228150] [drm] Loading R200 Microcode
[   74.228203] [drm] writeback test succeeded in 1 usecs
[  100.080394] audit(1193613905.566:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5160 profile="/usr/sbin/cupsd"
[  161.657742] apm: BIOS not found.
[  167.518871] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[  168.082546] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  168.102317] NFSD: starting 90-second grace period
[  171.298700] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  171.298741] vboxdrv: Successfully done.
[  171.921574] vmmon: module license 'unspecified' taints kernel.
[  171.936925] /dev/vmmon[5793]: VMCI: Driver initialized.
[  171.939464] /dev/vmmon[5793]: Module vmmon: registered with major=10 minor=165
[  171.941796] /dev/vmmon[5793]: Initial HV check: anyNotCapable=1 anyUnlocked=0 anyEnabled=0 anyDisabled=0
[  171.941848] /dev/vmmon[5793]: Module vmmon: initialized
[  172.294371] /dev/vmnet: open called by PID 5822 (vmnet-bridge)
[  172.294471] /dev/vmnet: hub 0 does not exist, allocating memory.
[  172.294885] /dev/vmnet: port on hub 0 successfully opened
[  172.298580] bridge-eth0: enabling the bridge
[  172.298635] bridge-eth0: up
[  172.298769] bridge-eth0: already up
[  172.298802] bridge-eth0: attached
[  172.755428] /dev/vmnet: open called by PID 5838 (vmnet-dhcpd)
[  172.756275] /dev/vmnet: hub 1 does not exist, allocating memory.
[  172.757555] /dev/vmnet: port on hub 1 successfully opened
[  172.890583] /dev/vmnet: open called by PID 5849 (vmnet-dhcpd)
[  172.891415] /dev/vmnet: hub 8 does not exist, allocating memory.
[  172.892583] /dev/vmnet: port on hub 8 successfully opened
[  172.943913] /dev/vmnet: open called by PID 5854 (vmnet-natd)
[  172.944034] /dev/vmnet: port on hub 8 successfully opened
[  174.284230] Failure registering capabilities with primary security module.
[  174.963384] Bluetooth: L2CAP ver 2.8
[  174.963433] Bluetooth: L2CAP socket layer initialized
[  175.148220] Bluetooth: RFCOMM socket layer initialized
[  175.150688] Bluetooth: RFCOMM TTY layer initialized
[  175.150742] Bluetooth: RFCOMM ver 1.8
[  175.412140] /dev/vmnet: open called by PID 6119 (vmnet-netifup)
[  175.413405] /dev/vmnet: port on hub 1 successfully opened
[  175.445524] /dev/vmnet: open called by PID 6118 (vmnet-netifup)
[  175.447735] /dev/vmnet: port on hub 8 successfully opened
[  179.035977] SoftMAC: Open Authentication completed with 00:0d:0b:04:ea:71
[  179.049893] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  180.430609] NET: Registered protocol family 17
[  186.024742] vmnet8: no IPv6 routers present
[  186.084661] vmnet1: no IPv6 routers present
[  189.473403] eth1: no IPv6 routers present
[  265.122437] ieee80211_crypt: registered algorithm 'WEP'
[  279.451063] eth1: no IPv6 routers present
[  390.737659] /dev/vmmon[6699]: Module vmmon: unloaded
[  391.499531] bridge-eth0: down
[  391.499567] bridge-eth0: detached
[  569.322968] /dev/vmmon[7080]: VMCI: Driver initialized.
[  569.323523] /dev/vmmon[7080]: Module vmmon: registered with major=10 minor=165
[  569.323805] /dev/vmmon[7080]: Initial HV check: anyNotCapable=1 anyUnlocked=0 anyEnabled=0 anyDisabled=0
[  569.323814] /dev/vmmon[7080]: Module vmmon: initialized
[  569.667195] /dev/vmnet: open called by PID 7111 (vmnet-bridge)
[  569.667635] /dev/vmnet: hub 0 does not exist, allocating memory.
[  569.668077] /dev/vmnet: port on hub 0 successfully opened
[  569.668415] bridge-eth0: enabling the bridge
[  569.668801] bridge-eth0: up
[  569.669058] bridge-eth0: already up
[  569.669071] bridge-eth0: attached
[  570.217971] /dev/vmnet: open called by PID 7126 (vmnet-dhcpd)
[  570.218196] /dev/vmnet: hub 1 does not exist, allocating memory.
[  570.218390] /dev/vmnet: port on hub 1 successfully opened
[  570.247223] /dev/vmnet: open called by PID 7136 (vmnet-dhcpd)
[  570.247630] /dev/vmnet: hub 8 does not exist, allocating memory.
[  570.248045] /dev/vmnet: port on hub 8 successfully opened
[  570.308167] /dev/vmnet: open called by PID 7141 (vmnet-natd)
[  570.308626] /dev/vmnet: port on hub 8 successfully opened
[  579.132519] /dev/vmnet: open called by PID 7171 (vmnet-netifup)
[  579.132555] /dev/vmnet: port on hub 1 successfully opened
[  580.380344] /dev/vmnet: open called by PID 7185 (vmnet-netifup)
[  580.380383] /dev/vmnet: port on hub 8 successfully opened
[  590.056908] vmnet1: no IPv6 routers present
[  590.440534] vmnet8: no IPv6 routers present

```

Also on a side note, I use an external monitor (1600x1200) and every time I boot up the logon screen is the resolution of my internal notebook screen (1280x800) instead of my external monitor resolution and it's a bit of a nuisance. Anyone else have this issue? I'm thinking it has something to do with XRandR but I'm not sure.

---

### Post by gregili on 2007-10-29
Yesterday i followed these threads and improved both my boot time and login time.Maybe it works for you too ..

[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)
[http://ubuntuforums.org/showthread.php?t=565651&highlight=improve+boot](http://ubuntuforums.org/showthread.php?t=565651&highlight=improve+boot)

---

### Post by Nonno Bassotto on 2007-10-29
Thank you for your tips, but the point here is not to improve our login time. The point is that there is some bug that made it increase from a few seconds to 52 seconds (for me). I'd rather not tweak my computer to improve login time: I just want it to work as expected.

---

### Post by BlueSkyNIS on 2007-10-29
Same problem here: P4 3GHz HT 1G of RAM NV8600GT
Takes about 30-40 seconds to load after login. Hard disk activity during this time is huge, HD lamp is constantly ON.
Using Compiz Fusion on Gutsy.

---

### Post by yostral on 2007-10-29
> **#Reistlehr- said:**
> So far, there have been no updates to the bug report even though the list is ever growing. 

Right.
So peolple, if you want this problem to be solved faster (maybe..), please confirm and try to help too on [Launchpad, bug #151544]("https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544").

Thanks :).

---

### Post by frodon on 2007-10-29
BTW, do you all issue this long session login time using the gnome failsafe session ?

---

### Post by #Reistlehr- on 2007-10-30
Ok. In Failsafe Gnome, it still took some time, but it basically seemed to come right up.

Altering the session script made no change.

Changing the session from xclient to gnome made no change.

Disabling compiz made no change. Although, i still think compiz is part of the problem. 

Keyring manager, doesn't ask me for a password, whcih is nice, but it's odd behavior for keyring manager. 

There is no gnome-splash screen, even after install, gnome-splash-manager.

I cannot log out, and log back in, or restart x. On re-log in, it will just sit on the desktop, with nothing. Only thing to do is to restart gracefully, since i can access vty's. 

My session file
```


[Default]
0,id=117f000101000119375950400000059790000
0,RestartStyleHint=1
0,Priority=40
0,Program=gnome-volume-manager
0,CurrentDirectory=/home/mike
0,CloneCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-vuFDxi/ 
0,RestartCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-vuFDxi/ --sm-client-id 117f000101000119375950400000059790000 --screen 0 
1,id=117f000101000119375951100000059790004
1,RestartStyleHint=2
1,Priority=5
1,Program=vino-session
1,CurrentDirectory=/home/mike
1,CloneCommand=vino-session --sm-config-prefix /vino-session-cUvnig/ 
1,RestartCommand=vino-session --sm-config-prefix /vino-session-cUvnig/ --sm-client-id 117f000101000119375951100000059790004 --screen 0 
#2,id=117f000101000119375951200000059790005
#2,RestartStyleHint=1
#2,Program=update-notifier
#2,CurrentDirectory=/home/mike
#2,CloneCommand=update-notifier --sm-config-prefix /update-notifier-4RG3wg/ 
#2,RestartCommand=update-notifier --sm-config-prefix /update-notifier-4RG3wg/ --sm-client-id 117f000101000119375951200000059790005 --screen 0 
#3,id=117f000101000119375951200000059790006
#3,Program=gnome-power-manager
#3,CurrentDirectory=/home/mike
#3,CloneCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-u2Ikvg/ 
#3,RestartCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-u2Ikvg/ --sm-client-id 117f000101000119375951200000059790006 --screen 0 
4,id=117f000101000119375950400000059790002
4,RestartStyleHint=2a
4,Priority=40
4,Program=nautilus
4,CurrentDirectory=/home/mike
4,CloneCommand=nautilus --sm-config-prefix /nautilus-yiyu9u/ 
4,RestartCommand=nautilus --sm-config-prefix /nautilus-yiyu9u/ --sm-client-id 117f000101000119375950400000059790002 --screen 0 --load-session /home/mike/.nautilus/saved-session-WW2T0T 
#5,id=117f000101000119375983500000059790008
#5,Program=rhythmbox
#5,CurrentDirectory=/home/mike
#5,CloneCommand=rhythmbox --sm-config-prefix /rhythmbox-NetXLg/ 
#5,RestartCommand=rhythmbox --sm-config-prefix /rhythmbox-NetXLg/ --sm-client-id 117f000101000119375983500000059790008 --screen 0 
6,id=117f000101000119375950800000059790003
6,RestartStyleHint=0
6,Priority=10
6,CloneCommand=compiz 
6,RestartCommand=compiz --sm-client-id 117f000101000119375950800000059790003 
##7,id=117f000101000119376207500000059790009
#7,Program=term
#7,CurrentDirectory=/home/mike
#7,CloneCommand=term --sm-config-prefix /term-bCu3Ig/ 
#7,RestartCommand=gnome-terminal --sm-config-prefix /term-bCu3Ig/ --sm-client-id 117f000101000119376207500000059790009 --screen 0 --window-with-profile-internal-id=Default --show-menubar --role=gnome-terminal-7015--1270705764-1193762076 --active --geometry 80x24+1077+27 --title mike@AngryLinux:\\ ~/.gnome2 --working-directory /home/mike/.gnome2 --zoom 1 
8,id=117f000101000119375950400000059790001
8,RestartStyleHint=2
8,Priority=40
8,Program=gnome-panel
8,CurrentDirectory=/home/mike
8,CloneCommand=gnome-panel --sm-config-prefix /gnome-panel-otpS7j/ 
8,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-otpS7j/ --sm-client-id 117f000101000119375950400000059790001 --screen 0 
9,RestartCommand=gnome-at-visual -s 
10,RestartCommand=restricted-manager --check 
11,RestartCommand=gdesklets 
#12,RestartCommand=trackerd 
#13,RestartCommand=xdg-user-dirs-gtk-update 
#14,RestartCommand=gnome-volume-manager --sm-disable 
#15,RestartCommand=nm-applet --sm-disable 
num_clients=16

```
(Anyone know what vino-session is?)

My .xsession-errors file
```


(process:6106): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:6110): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/AngryLinux:/tmp/.ICE-unix/6103
** Message: Starting remote desktop server
Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 10de:0398 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
Initializing gnome-mount extension


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0
** Message: failed to load session from /home/mike/.nautilus/saved-session-WW2T0T
Starting gdesklets-daemon...

Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
(gnome-panel:6252): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -7 and height 27

Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
                                        
Connected to daemon in 14829 milliseconds.

(flock-bin:6929): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

```

FTR - i have gdesklets enabled, but i've tried all the permutation with and without it, and it is not a factor.

---

### Post by TheExplorer on 2007-10-30
I've found the following in my lsdev output:

snd_emu10k1
ac97_bus

I have Creative SB Live and an AC'97 onboard soundcard. Is it possible? 'Cause I have switched off the above mentioned onboard device in bios.

I dunno, maybe it could be the reason too when two sound systems load up fighting for the Gnome :)

---

### Post by dmontalvao on 2007-10-30
I am only replying to keep in touch. I have the same issue, and don't know how to solve it. The most strange thing is that Gutsy Pre-release seemed to work better than the final version in many of these aspects.

---

### Post by #Reistlehr- on 2007-10-30
@dmontalvao

That was exactly what i was thinking.

I think i see something.

Can everyone post their .xsession-errors file in their home directory? (~/.xsession-errors

---

### Post by fjgaude on 2007-10-30
Here's mine for what it is worth. I never looked at it before:


[PHP](process:6647): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:6651): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 20: [[: not found
SESSION_MANAGER=local/sunshine:/tmp/.ICE-unix/6644


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0
Initializing gnome-mount extension
evolution-alarm-notify-Message: Setting timeout for 79780 1193875200 1193795420
evolution-alarm-notify-Message:  Wed Oct 31 17:00:00 2007

evolution-alarm-notify-Message:  Tue Oct 30 18:50:20 2007

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2800056 (Buddy List)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Initializing gnome-mount extension
Window manager warning: last_focus_time (4090216873) is greater than comparison timestamp (4065041010).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Window manager warning: last_user_time (4090228068) is greater than comparison timestamp (4065041010).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
Window manager warning: 0x3e00020 (frank@suns) appears to be one of the offending windows with a timestamp of 4090064363.  Working around...
Window manager warning: 0x1e000a7 (General He) appears to be one of the offending windows with a timestamp of 4089518053.  Working around...
Window manager warning: 0xe00003 (Bottom Exp) appears to be one of the offending windows with a timestamp of 4090178652.  Working around...
Window manager warning: 0xe00029 (Top Expand) appears to be one of the offending windows with a timestamp of 4090206709.  Working around...
Window manager warning: 0x2800056 (Buddy List) appears to be one of the offending windows with a timestamp of 4089493399.  Working around...
Window manager warning: 0x1200021 (Desktop) appears to be one of the offending windows with a timestamp of 4090183631.  Working around...
Window manager warning: 0x1000021 (etc - File) appears to be one of the offending windows with a timestamp of 4089886782.  Working around...
Window manager warning: 0x3200022 (10/03/2007) appears to be one of the offending windows with a timestamp of 4089892162.  Working around...
Window manager warning: 0x40000d8 (Inbox - Th) appears to be one of the offending windows with a timestamp of 4090197353.  Working around...
Window manager warning: 0x4400003 (Time and D) appears to be one of the offending windows with a timestamp of 4090228068.  Working around...[/PHP]

---

### Post by GraFF on 2007-10-30
[PHP]
(process:5827): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:5831): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
FreeFontPath: FPE "/usr/share/fonts/X11/misc/" refcount is 2, should be 1; fixing.
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
SESSION_MANAGER=local/graff-laptop:/tmp/.ICE-unix/5824
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald

** (x-session-manager:5824): WARNING **: Host name lookup failure on localhost.
Can't open /etc/wifi-radar.conf.
Are you root?
** Message: Not starting remote desktop server
Screen is composited.
LOADED : /usr/share/applications/firefox.desktop
LOADED : /usr/share/applications/pidgin.desktop
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
LOADED : /usr/share/applications/ooo-writer.desktop
evolution-alarm-notify-Message: Setting timeout for 3183 1193781600 1193778417
evolution-alarm-notify-Message:  Wed Oct 31 00:00:00 2007

evolution-alarm-notify-Message:  Tue Oct 30 23:06:57 2007

LOADED : /usr/share/applications/evolution.desktop
LOADED : /usr/share/applications/gnome-terminal.desktop
LOADED : /usr/share/applications/kde/amarok.desktop
LOADED : /usr/share/applications/vlc.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/trash.desktop
Initializing gnome-mount extension
alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1870 (alarm_queue_init)
alarm-queue.c:200 (queue_midnight_refresh) - Refresh at Wed Oct 31 00:00:00 2007
 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/graff/.evolution/calendar/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/graff/.evolution/calendar/local/system - Calendar Open Async... 0x6e06a0
alarm-notify.c:220 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:462 (alarm_notify_add_calendar) contacts:/// - Calendar Open Async... 0x6e3e40
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/graff/.evolution/tasks/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/graff/.evolution/tasks/local/system - Calendar Open Async... 0x6eee80
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/graff/.evolution/memos/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/graff/.evolution/memos/local/system - Calendar Open Async... 0x6efc20
alarm-notify.c:393 (cal_opened_cb) file:///home/graff/.evolution/calendar/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:393 (cal_opened_cb) file:///home/graff/.evolution/tasks/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x6d8b90: Received at thread 42044950
alarm-queue.c:2003 (alarm_queue_add_async) - 0x6e06a0
alarm-queue.c:581 (load_alarms_for_today) - From Tue Oct 30 23:07:05 2007
 to Tue Oct 30 23:07:05 2007

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x6d8b90: Replied to GUI thread
alarm-notify.c:349 (alarm_msg_received) - 0x6ecb00: Received at thread 42044950
alarm-queue.c:2003 (alarm_queue_add_async) - 0x6eee80
alarm-queue.c:581 (load_alarms_for_today) - From Tue Oct 30 23:07:05 2007
 to Tue Oct 30 23:07:05 2007

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x6ecb00: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) file:///home/graff/.evolution/memos/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x6c6d70: Received at thread 42044950
alarm-queue.c:2003 (alarm_queue_add_async) - 0x6efc20
alarm-queue.c:581 (load_alarms_for_today) - From Tue Oct 30 23:07:05 2007
 to Tue Oct 30 23:07:05 2007

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x6c6d70: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) contacts:/// - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x6f1220: Received at tLaunched application : 6082

(avant-window-navigator:5954): Wnck-CRITICAL **: wnck_application_get_name: assertion `WNCK_IS_APPLICATION (app)' failed

(avant-window-navigator:5954): Wnck-CRITICAL **: wnck_application_get_name: assertion `WNCK_IS_APPLICATION (app)' failed

(avant-window-navigator:5954): Wnck-CRITICAL **: wnck_application_get_name: assertion `WNCK_IS_APPLICATION (app)' failed

(avant-window-navigator:5954): Wnck-CRITICAL **: wnck_application_get_name: assertion `WNCK_IS_APPLICATION (app)' failed

(avant-window-navigator:5954): Wnck-CRITICAL **: wnck_application_get_name: assertion `WNCK_IS_APPLICATION (app)' failed

(avant-window-navigator:5954): Wnck-CRITICAL **: wnck_application_get_name: assertion `WNCK_IS_APPLICATION (app)' failed

(avant-window-navigator:5954): Wnck-CRITICAL **: wnck_application_get_name: assertion `WNCK_IS_APPLICATION (app)' failed

(avant-window-navigator:5954): Gtk-CRITICAL **: gtk_widget_queue_draw: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:5954): Gtk-CRITICAL **: gtk_widget_queue_draw: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:5954): Gtk-CRITICAL **: gtk_widget_queue_draw: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:5954): Gtk-CRITICAL **: gtk_widget_queue_draw: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:5954): Gtk-CRITICAL **: gtk_widget_queue_draw: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:5954): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(avant-window-navigator:5954): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GtkWidget'

(awn-applet-activation:5974): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(awn-applet-activation:5974): GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(awn-applet-activation:5974): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(awn-applet-activation:5974): GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(awn-applet-activation:5974): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(awn-applet-activation:5974): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(awn-applet-activation:5974): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(awn-applet-activation:5974): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
: malformed file name or URI.

** (gedit:6152): CRITICAL **: gedit_utils_make_canonical_uri_from_shell_arg: assertion `*str != '\0'' failed
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSScreen is composited.
LOADED : /usr/share/applications/firefox.desktop
LOADED : /usr/share/applications/pidgin.desktop
LOADED : /usr/share/applications/ooo-writer.desktop
LOADED : /usr/share/applications/evolution.desktop
LOADED : /usr/share/applications/gnome-terminal.desktop
LOADED : /usr/share/applications/kde/amarok.desktop
LOADED : /usr/share/applications/vlc.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/trash.desktop
Launched application : 6173

(awn-applet-activation:5974): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'
fetchDevices
Lock acquired for devices thread
Devices thread started
Connecting (devices)
Fetching devices
Closing connection (devices)
Releasing devices lock
Got devices
queryPPDs
Lock acquired for PPDs thread
PPDs thread started
Connecting (PPDs)
Fetching PPDs
Closing connection (PPDs)
Releasing PPDs lock[/PHP]

---

### Post by cowanh00 on 2007-10-30
Here is mine:

[PHP]
(process:5716): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:5720): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/etc/X11/Xsession.d/40guidance-displayconfig_restore: line 11: /usr/bin/displayconfig-restore: No such file or directory
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/cowanh00-laptop:/tmp/.ICE-unix/5713
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
[sudo] password for cowanh00:
[sudo] password for cowanh00:
Initializing gnome-mount extension
** Message: Not starting remote desktop server


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0
Screen is composited.
APPLET : /usr/lib/awn/applets/showdesktop.desktop
APPLET : /usr/lib/awn/applets/main-menu.desktop
APPLET : /usr/lib/awn/applets/stack.desktop
APPLET : /usr/lib/awn/applets/media-control.desktop
APPLET : /usr/lib/awn/applets/separator.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/separator.desktop
APPLET : /usr/lib/awn/applets/awn-system-monitor.desktop
APPLET : /usr/lib/awn/applets/PySwitcher.desktop
APPLET : /usr/lib/awn/applets/trash.desktop
APPLET : /usr/lib/awn/applets/quit-applet.desktop
evolution-alarm-notify-Message: Setting timeout for 5809 1193785200 1193779391
evolution-alarm-notify-Message:  Wed Oct 31 00:00:00 2007

evolution-alarm-notify-Message:  Tue Oct 30 22:23:11 2007

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
CachingBackend: Loading instances from cache
CachingBackend: Loading <Gmail1>
Creating new entry for GmailScreenlet in /tmp/screenlets/screenlets.running
Loading instances in: /home/cowanh00/.config/Screenlets/Gmail/default/
File: Gmail1.ini
Creating new instance: 
UPDATING SHAPE
UPDATING SHAPE
Set options in GmailScreenlet
Traceback (most recent call last):
  File "/home/cowanh00/.screenlets/Gmail/GmailScreenlet.py", line 296, in <module>
    screenlets.session.create_session(GmailScreenlet)
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 392, in create_session
CachingBackend: Loading instances from cache
CachingBackend: Loading <Slideshow1>
Creating new entry for SlideshowScreenlet in /tmp/screenlets/screenlets.running
Loading instances in: /home/cowanh00/.config/Screenlets/Slideshow/default/
File: Slideshow1.ini
Creating new instance: 
UPDATING SHAPE
UPDATING SHAPE
Traceback (most recent call last):
  File "/usr/local/share/screenlets/Slideshow/SlideshowScreenlet.py", line 348, in <module>
    screenlets.session.create_session(SlideshowScreenlet)
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 392, in create_session
alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1870 (alarm_queue_init)
alarm-queue.c:200 (queue_midnight_refresh) - Refresh at Wed Oct 31 00:00:00 2007
 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/cowanh00/.evolution/calendar/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/cowanh00/.evolution/calendar/local/system - Calendar Open Async... 0x80c64b0
alarm-notify.c:220 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:462 (alarm_notify_add_calendar) contacts:/// - Calendar Open Async... 0x80e6e00
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/cowanh00/.evolution/tasks/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/cowanh00/.evolution/tasks/local/system - Calendar Open Async... 0x80e6e40
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/co    session.start()
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 177, in start
    if self.__load_instances():
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 319, in __load_instances
    self.__restore_options_from_backend(sl, self.path+filename)
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 345, in __restore_options_from_backend
    setattr(screenlet, opt.name, opt.on_import(opts[o]))
  File "/home/cowanh00/.screenlets/Gmail/GmailScreenlet.py", line 81, in __setattr__
    self.update()
  File "/home/cowanh00/.screenlets/Gmail/GmailScreenlet.py", line 95, in update
    self.check()
  File "/home/cowanh00/.screenlets/Gmail/GmailScreenlet.py", line 117, in check
    self.ga.login()
  File "/home/cowanh00/.screenlets/Gmail/libgmail.py", line 348, in login
    session.start()
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 177, in start
    if self.__load_instances():
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 314, in __load_instances
    sl = self.create_instance(id=filename[:-4], enable_saving=False)
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 106, in create_instance
    sl = self.screenlet(id=id, session=self, **keyword_args)
  File "/usr/local/share/screenlets/Slideshow/SlideshowScreenlet.py", line 94, in __init__
    self.engine = self.engine
  File "/usr/local/share/screenlets/Slideshow/SlideshowScreenlet.py", line 105, in __setattr__
    self.update()
  File "/usr/local/share/screenlets/Slideshow/SlideshowScreenlet.py", line 255, in update
    self.set_image (self.fetch_image())
  File "/usr/local/share/screenlets/Slideshow/SlideshowScreenlet.py", line 189, in fetch_image
    zodiacfd = urlopen('http://www.flickr.com/explore/interesting/7days/')
  File "/usr/lib/python2.5/urllib2.py", line 124, in urlopen
wanh00/.evolution/memos/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/cowanh00/.evolution/memos/local/system - Calendar Open Async... 0x80e9d40
alarm-notify.c:393 (cal_opened_cb) file:///home/cowanh00/.evolution/calendar/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:393 (cal_opened_cb) file:///home/cowanh00/.evolution/tasks/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80cdb80: Received at thread b4da8b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80c64b0
alarm-queue.c:581 (load_alarms_for_today) - From Tue Oct 30 22:23:29 2007
 to Tue Oct 30 22:23:29 2007

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80cdb80: Replied to GUI thread
alarm-notify.c:349 (alarm_msg_received) - 0x80e6628: Received at thread b4da8b90
alarm-queue.c:2003 (alarm_q
** (awn-applet-activation:5928): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed
    pageData = self._retrievePage(req)
  File "/home/cowanh00/.screenlets/Gmail/libgmail.py", line 384, in _retrievePage
    resp = self.opener.open(req)
  File "/usr/lib/python2.5/urllib2.py", line 381, in open

** (awn-applet-activation:5928): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed
    return _opener.open(url, data)
  File "/usr/lib/python2.5/urllib2.py", line 381, in open
    response = self._open(req, data)
  File "/usr/lib/python2.5/urllib2.py", line 399, in _open
    response = self._open(req, data)
  File "/usr/lib/python2.5/urllib2.py", line 399, in _open
    '_open', req)
  File "/usr/lib/python2.5/urllib2.py", line 360, in _call_chain
    '_open', req)
  File "/usr/lib/python2.5/urllib2.py", line 360, in _call_chain
    result = func(*args)
    result = func(*args)
  File "/usr/lib/python2.5/urllib2.py", line 1115, in https_open
  File "/usr/lib/python2.5/urllib2.py", line 1107, in http_open

** (awn-applet-activation:5928): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5928): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5928): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed
    return self.do_open(httplib.HTTPSConnection, req)
  File "/usr/lib/python2.5/urllib2.py", line 1082, in do_open
    raise URLError(err)
urllib2.URLError: <urlopen error (-5, 'No address associated with hostname')>

** (awn-applet-activation:5928): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed
    return self.do_open(httplib.HTTPConnection, req)
  File "/usr/lib/python2.5/urllib2.py", line 1082, in do_open
    raise URLError(err)
urllib2.URLError: <urlopen error (-2, 'Name or service not known')>

** (awn-applet-activation:5928): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5928): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5928): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5928): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5928): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5928): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5928): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5928): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5928): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5928): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed
ueue_add_async) - 0x80e6e40
alarm-queue.c:581 (load_alarms_for_today) - From Tue Oct 30 22:23:29 2007
 to Tue Oct 30 22:23:29 2007

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80e6628: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) file:///home/cowanh00/.evolution/memos/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80eae98: Received at thread b4da8b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80e9d40
alarm-queue.c:581 (load_alarms_for_today) - From Tue Oct 30 22:23:29 2007
 to Tue Oct 30 22:23:29 2007

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80eae98: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) contacts:/// - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarmmonitor callback

(awn-applet-activation:5936): Gtk-CRITICAL **: gtk_table_resize: assertion `n_cols > 0 && n_cols < 65536' failed

(awn-applet-activation:5936): Gtk-CRITICAL **: gtk_table_resize: assertion `n_rows > 0 && n_rows < 65536' failed
monitor callback

(PySwitcher.py:5944): Wnck-CRITICAL **: update_client_list: assertion `reentrancy_guard == 0' failed

(awn-applet-activation:5926): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(awn-applet-activation:5926): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

** (awn-applet-activation:5926): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5926): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5926): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5926): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5926): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5926): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5926): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5926): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5926): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5926): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5926): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5926): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5926): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5926): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5926): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5926): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed
monitor callback
monitor callback
  PID TTY          TIME CMD
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback

(PySwitcher.py:5944): Wnck-CRITICAL **: update_client_list: assertion `reentrancy_guard == 0' failed
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback

(PySwitcher.py:5944): Wnck-CRITICAL **: update_client_list: assertion `reentrancy_guard == 0' failed
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback

(PySwitcher.py:5944): Wnck-CRITICAL **: update_client_list: assertion `reentrancy_guard == 0' failed
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
checking for valid crashreport now
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
<gtk.gdk.Pixbuf object at 0x82ffb44 (GdkPixbuf at 0x83b06e8)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x83b0928)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x83b0678)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x841c880)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x841c998)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x841caf8)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x841c848)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x841c8f0)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x83b0678)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x83b0ac0)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x841caf8)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x83b0ac0)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x841c880)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x83b0ac0)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x841ca18)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x841c848)>
<gtk.gdk.Pixbuf object at 0x82ffmonitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
*** CLB *** Initializing Google Browser Sync...
*** CLB *** Instanciating core objects...
*** CLB *** Registering with XPCOM...
*** CLB *** Adding categories...
*** CLB *** Google Browser Sync initialized succesfully!
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback

(PySwitcher.py:5944): Wnck-CRITICAL **: update_client_list: assertion `reentrancy_guard == 0' failed
monitor callback

(PySwitcher.py:5944): Wnck-CRITICAL **: update_client_list: assertion `reentrancy_guard == 0' failed
JACK tmpdir identified as [/dev/shm]
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
JACK tmpdir identified as [/dev/shm]
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
JACK tmpdir identified as [/dev/shm]
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
JACK tmpdir identified as [/dev/shm]
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
JACK tmpdir identified as [/dev/shm]
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
JACK tmpdir identified as [/dev/shm]
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
JACK tmpdir identified as [/dev/shm]
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
JACK tmpdir identified as [/dev/shm]
monitor callback
monitor callback
monitor callback

(PySwitcher.py:5944): Wnck-CRITICAL **: update_client_list: assertion `reentrancy_guard == 0' failed
monitor callback
monitor callback
monitor callback
JACK tmpdir identified as [/dev/shm]
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
c34 (GdkPixbuf at 0x841c8b8)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x83b0928)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x841c848)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x83b0928)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x841c880)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x8437988)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x8437a40)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x8437ab0)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x8437b20)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x8437b90)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x8437c48)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x8437c10)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x8437b58)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x8437a78)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x8437a08)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x841c880)>
<gtk.gdk.Pixbuf object at 0x82ffc34 (GdkPixbuf at 0x84378a8)>
<gmonitor callback
JACK tmpdir identified as [/dev/shm]
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
JACK tmpdir identified as [/dev/shm]
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback

(PySwitcher.py:5944): Wnck-CRITICAL **: update_client_list: assertion `reentrancy_guard == 0' failed
JACK tmpdir identified as [/dev/shm]
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
JACK tmpdir identified as [/dev/shm]
monitor callback
monitor callback
monitor callback
monitor callback
JACK tmpdir identified as [/dev/shm]
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
JACK tmpdir identified as [/dev/shm]
monitor callback
monitor callback
monitor callback
JACK tmpdir identified as [/dev/shm]
monitor callback
monitor callback
JACK tmpdir identified as [/dev/shm]
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
JACK tmpdir identified as [/dev/shm]
monitor callback
monitor callback
monitor callback
monitor callback
JACK tmpdir identified as [/dev/shm]
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback

(PySwitcher.py:5944): Wnck-CRITICAL **: update_client_list: assertion `reentrancy_guard == 0' failed
JACK tmpdir identified as [/dev/shm]
** Message: Failed to write /home/cowanh00/flickr.jpg to thumbnail pixbuf loader: Unrecognised image file format
monitor callback
** Message: Failed to write /home/cowanh00/flickr.jpg to thumbnail pixbuf loader: Unrecognised image file format
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback

(PySwitcher.py:5944): Wnck-CRITICAL **: update_client_list: assertion `reentrancy_guard == 0' failed
monitor callback
monitor callback
monitor callback
monitor callback
JACK tmpdir identified as [/dev/shm]
** Message: Failed to write /home/cowanh00/flickr.jpg to thumbnail pixbuf loader: Unrecognised image file format
monitor callback
** Message: Failed to write /home/cowanh00/flickr.jpg to thumbnail pixbuf loader: Unrecognised image file format
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback[/PHP]

Wow mine is long! Is it supposed to be this long?

---

### Post by Showan2 on 2007-10-30
I too have this issue on my Gusty laptop (32bit):

Toshiba Sattelite pro,
P4M 2.2 ghz, Intel VGA (I think 855 chipset)
No Desktop Effects

But not on my Gutsy Desktop (64 bit):

CD 1.83 Ghz; 7600 GS
No Desktop Effects

They have more or less the same packages installed.

Weird bug, isn't it?

---

### Post by daniel_victoria on 2007-10-30
Here is my .xsession-erros


```
(process:5396): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:5400): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
SESSION_MANAGER=local/mancalinha:/tmp/.ICE-unix/5393
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5835 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
** Message: Not starting remote desktop server


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0
Initializing gnome-mount extension
evolution-alarm-notify-Message: Setting timeout for 14818 1193796000 1193781182
evolution-alarm-notify-Message:  Wed Oct 31 00:00:00 2007

evolution-alarm-notify-Message:  Tue Oct 30 19:53:02 2007

alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1870 (alarm_queue_init)
alarm-queue.c:200 (queue_midnight_refresh) - Refresh at Wed Oct 31 00:00:00 2007
 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/daniel/.evolution/calendar/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/daniel/.evolution/calendar/local/system - Calendar Open Async... 0x80b2f50
alarm-notify.c:220 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:462 (alarm_notify_add_calendar) contacts:/// - Calendar Open Async... 0x80c7e30
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/daniel/.evolution/tasks/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/daniel/.evolution/tasks/local/system - Calendar Open Async... 0x80ccbd0
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/daniel/.evolution/memos/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/daniel/.evolution/memos/local/system - Calendar Open Async... 0x80c7f80
alarm-notify.c:393 (cal_opened_cb) file:///home/daniel/.evolution/calendar/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80d36b0: Received at thread b2deeb90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80b2f50
alarm-notify.c:393 (cal_opened_cb) file:///home/daniel/.evolution/tasks/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:393 (cal_opened_cb) contacts:/// - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-queue.c:581 (load_alarms_for_today) - From Tue Oct 30 19:53:14 2007
 to Tue Oct 30 19:53:14 2007

alarm-queue.c:518 (load_alarms) 
alarm-notify.c:393 (cal_opened_cb) file:///home/daniel/.evolution/memos/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:349 (alarm_msg_received) - 0x80b5098: Received at thread b2deeb90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80ccbd0
alarm-notify.c:337 (alarm_msgport_replied) - 0x80d36b0: Replied to GUI thread
alarm-queue.c:581 (load_alarms_for_today) - From Tue Oct 30 19:53:15 2007
 to Tue Oct 30 19:53:15 2007

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:349 (alarm_msg_received) - 0x80d08f8: Received at thread b2deeb90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80c7e30
alarm-notify.c:337 (alarm_msgport_replied) - 0x80b5098: Replied to GUI thread
alarm-queue.c:581 (load_alarms_for_today) - From Tue Oct 30 19:53:15 2007
 to Tue Oct 30 19:53:15 2007

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:349 (alarm_msg_received) - 0x80d1960: Received at thread b2deeb90
alarm-queue.c:2003 (alarm_queue_add_asyn
(gnome-panel:5465): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -15 and height 24
FG: isPreferred(application/x-bittorrent,[object Object])
FG: _shouldIntercept(application/x-bittorrent)

** (gnome-app-install:5906): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1261: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)
FG: isPreferred(application/x-bittorrent,[object Object])
FG: _shouldIntercept(application/x-bittorrent)
```

---

### Post by Nonno Bassotto on 2007-10-30
Here you have mine

```


(process:5516): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:5520): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Leibniz:/tmp/.ICE-unix/5513

** (x-session-manager:5513): WARNING **: Host name lookup failure on localhost.
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

(process:5704): Gnome-CRITICAL **: gnome_program_module_register: assertion `module_info' failed


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0
** Message: Server desktop remoto non avviato
Initializing gnome-mount extension
evolution-alarm-notify-Message: Setting timeout for 80733 1193871600 1193790867
evolution-alarm-notify-Message:  Thu Nov  1 00:00:00 2007

evolution-alarm-notify-Message:  Wed Oct 31 01:34:27 2007

  PID TTY          TIME CMD
alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1870 (alarm_queue_init)
alarm-queue.c:200 (queue_midnight_refresh) - Refresh at Thu Nov  1 00:00:00 2007
 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/andrea/.evolution/calendar/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/andrea/.evolution/calendar/local/system - Calendar Open Async... 0x80c5540
alarm-notify.c:220 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:462 (alarm_notify_add_calendar) contacts:/// - Calendar Open Async... 0x80ee6a0
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/andrea/.evolution/tasks/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/andrea/.evolution/tasks/local/system - Calendar Open Async... 0x80ee550
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/andrea/.evolution/memos/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/andrea/.evolution/memos/local/system - Calendar Open Async... 0x80ee860
alarm-notify.c:393 (cal_opened_cb) file:///home/andrea/.evolution/calendar/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80f7630: Received at thread b3de6b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80c5540
alarm-queue.c:581 (load_alarms_for_today) - From Wed Oct 31 00:00:00 2007
 to Wed Oct 31 00:00:00 2007

alarm-queue.c:518 (load_alarms) 
alarm-notify.c:393 (cal_opened_cb) file:///home/andrea/.evolution/tasks/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:349 (alarm_msg_received) - 0x80f1b48: Received at thread b3de6b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80ee550
alarm-notify.c:337 (alarm_msgport_replied) - 0x80f7630: Replied to GUI thread
alarm-queue.c:581 (load_alarms_for_today) - From Wed Oct 31 00:00:00 2007
 to Wed Oct 31 00:00:00 2007

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80f1b48: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) file:///home/andrea/.evolution/memos/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80f5880: Received at thread b3de6b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80ee860
alarm-queue.c:581 (load_alarms_for_today) - From Wed Oct 31 00:00:00 2007
 to Wed Oct 31 00:00:00 2007

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80f5880: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) contacts:/// - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

---

### Post by Partyboi2 on 2007-10-30
Here is mine
```

(process:5304): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:5308): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/karl-desktop:/tmp/.ICE-unix/5301
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0171 (rev a3) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
Initializing gnome-mount extension


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
** Message: Not starting remote desktop server
Screen is composited.
APPLET : /usr/lib/awn/applets/notification-area.desktop
APPLET : /usr/lib/awn/applets/trash.desktop
LOADED : /home/karl/.config/awn/launchers/awn_launcher.desktop
LOADED : /home/karl/.config/awn/launchers/awn_launcher-3.desktop
LOADED : /home/karl/.config/awn/launchers/awn_launcher-4.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/showdesktop.desktop
APPLET : /usr/lib/awn/applets/quit-applet.desktop
APPLET : /usr/lib/awn/applets/main-menu.desktop
APPLET : /usr/lib/awn/applets/stack.desktop
Throttle level is 0
evolution-alarm-notify-Message: Setting timeout for 83851 1193875200 1193791349
evolution-alarm-notify-Message:  Thu Nov  1 11:00:00 2007

evolution-alarm-notify-Message:  Wed Oct 31 11:42:29 2007


(awn-applet-activation:5486): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width 26 and height -21

** (showdesktop.py:5514): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5512): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (showdesktop.py:5514): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5512): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (showdesktop.py:5514): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5512): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (showdesktop.py:5514): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5512): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (showdesktop.py:5514): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5512): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (showdesktop.py:5514): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5512): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (showdesktop.py:5514): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5512): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (showdesktop.py:5514): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5512): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (showdesktop.py:5514): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5512): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (showdesktop.py:5514): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5512): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (showdesktop.py:5514): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5512): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (showdesktop.py:5514): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5512): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (showdesktop.py:5514): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5512): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (showdesktop.py:5514): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5512): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (showdesktop.py:5514): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5512): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed
monitor callback
monitor callback

** (quit-applet.py:5518): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (quit-applet.py:5518): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (quit-applet.py:5518): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (quit-applet.py:5518): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (quit-applet.py:5518): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (quit-applet.py:5518): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (quit-applet.py:5518): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (quit-applet.py:5518): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (quit-applet.py:5518): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (quit-applet.py:5518): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (quit-applet.py:5518): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (quit-applet.py:5518): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (quit-applet.py:5518): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (quit-applet.py:5518): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed
alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1870 (alarm_queue_init)
alarm-queue.c:200 (queue_midnight_refresh) - Refresh at Thu Nov  1 11:00:00 2007
 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/karl/.evolution/calendar/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/karl/.evolution/calendar/local/system - Calendar Open Async... 0x80bb630
alarm-notify.c:220 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:462 (alarm_notify_add_calendar) contacts:/// - Calendar Open Async... 0x80d4ab0
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/karl/.evolution/tasks/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/karl/.evolution/tasks/local/system - Calendar Open Async... 0x80d4b00
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/karl/.evolution/me
** (quit-applet.py:5518): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed
mos/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/karl/.evolution/memos/local/system - Calendar Open Async... 0x80d6e40
alarm-notify.c:393 (cal_opened_cb) file:///home/karl/.evolution/calendar/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80dc310: Received at thread b45c5b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80bb630
alarm-queue.c:581 (load_alarms_for_today) - From Wed Oct 31 11:42:36 2007
 to Wed Oct 31 11:42:36 2007

alarm-queue.c:518 (load_alarms) 
alarm-notify.c:393 (cal_opened_cb) file:///home/karl/.evolution/tasks/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:349 (alarm_msg_received) - 0x80d7d20: Received at thread b45c5b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80d4b00
alarm-notify.c:337 (alarm_msgport_replied) - 0x80dc310: Replied to GUI thread
alarm-queue.c:581 (load_alarms_for_today) - From Wed Oct 31 11:42:36 2007
 to Wed Oct 31 11:42:36 2007

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80d7d20: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) contacts:/// - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80d7cb8: Received at thread b45c5b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80d4ab0
alarm-notify.c:393 (cal_opened_cb) file:///home/karl/.evolution/memos/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-queue.c:581 (load_alarms_for_today) - From Wed Oct 31 11:42:36 2007
 to Wed Oct 31 11:42:36 2007

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:349 (alarm_msg_received) - 0x80d4e40: Received at thread b45c5b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80d6e40
alamonitor callback
monitor callback
monitor callback
  PID TTY          TIME CMD

(awn-applet-activation:5486): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width 26 and height -21
monitor callback

(awn-applet-activation:5510): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(awn-applet-activation:5510): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

** (awn-applet-activation:5510): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5510): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5510): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5510): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5510): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5510): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5510): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed
monitor callback

** (awn-applet-activation:5510): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5510): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5510): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5510): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5510): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5510): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:5510): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (avant-window-navigator:5475): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
Launched application : 5590
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
CachingBackend: Loading instances from cache
CachingBackend: Loading <ClearCalendar1>
Error in screenlets.session.connect_daemon: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.ScreenletsDaemon was not provided by any .service files
Creating new entry for ClearCalendarScreenlet in /tmp/screenlets/screenlets.running
Loading instances in: /home/karl/.config/Screenlets/ClearCalendar/default/
File: ClearCalendar1.ini
Creating new instance: 
UPDATING SHAPE
UPDATING SHAPE
Set options in ClearCalendarScreenlet
UPDATING SHAPE
Restored instances from session 'default' ...
CachingBackend: Saving <#ClearCalendar1> :) ...
OK
CachingBackend: Saving <#ClearCalendar1> :) ...
OK
CachingBackend: Saving <#ClearCalendar1> :) ...
OK
CachingBackend: Saving <#ClearCalendar1> :) ...
OK
CachingBackend: Saving <#ClearCalendar1> :) ...
OK
CachingBackend: Saving <#ClearCalendar1> :) ...
OK
CachingBackend: Saving <#ClearCalendar1> :) ...
OK
CachingBackend: Saving <#ClearCalendar1> :) ...
OK
CachingBackend: Saving <#Cmonitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback

** (avant-window-navigator:5475): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback
monitor callback

** (avant-window-navigator:5475): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed
```

---

### Post by The Noble on 2007-10-31
Aye, I have the same problem. I am on an intel Pentium 4 laptop and compiz seemed to cause the problem. I seem to remember that the problems started after AWN was installed. It's not bad anymore, now that I stopped using compiz for the time being. Sadly don't have enough time to do some testing, but add me to the list.

---

### Post by RealNitro on 2007-10-31
My .xsession-errors has 2874 lines. It contains some info about my system that's private, but here are some parts of it:
[PHP]
(process:6408): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:6412): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/etc/X11/Xsession.d/40guidance-displayconfig_restore: 11: /usr/bin/displayconfig-restore: not found
SESSION_MANAGER=local/...:/tmp/.ICE-unix/6405
Checking for Xgl: not present. 

** (gsynaptics-init:6490): WARNING **: Using synclient
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: Unknown parameter CoastingSpeedThreashold
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Initializing gnome-mount extension
Throttle level is 0
evolution-alarm-notify-Message: Setting timeout for 9250 1193785200 1193775950
evolution-alarm-notify-Message:  Wed Oct 31 00:00:00 2007

evolution-alarm-notify-Message:  Tue Oct 30 21:25:50 2007

DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1870 (alarm_queue_init)
alarm-queue.c:200 (queue_midnight_refresh) - Refresh at Wed Oct 31 00:00:00 2007
 
alarm-notify.c:220 (load_calendars) - Loading Calendar file: ...
[... more tracker stuff ...]
DCOPClient::attachInternal. Attach failed Could not open network socket
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
kbuildsycoca running...
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
Rhythmbox: could not connect to socket
Rhythmbox: No such file or directory
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kdecore (KProcess): WARNING: _attachPty() 16

(gnome-panel:6461): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -15 and height 24
Error: can't open /var/run/openct/status: No such file or directory
[... this last line is repeated many, many times ...]
ERROR: Inotify watch on ... has failed
[... some more Inotify errors ...]
Error: can't open /var/run/openct/status: No such file or directory
[... above line repeated for the rest of the document ...]
...Too much output, ignoring rest...
[/PHP]

---

### Post by Arthur Archnix on 2007-10-31
Sorry, no help here, I only wanted to say that I've noticed a regression from Feisty to Gutsy with respect to boot time. Specifically, the time it takes for a usable desktop to appear after entering login info has at least doubled, though it is not a minute or so like some people are experiencing.

I've removed bluetooth, laptop-mode-tools, apmd and evolution. Not to solve the problem, just thought I'd mention it to rule those out.

Could it be a change in an X script run at boot? And just to ask again, people have tried removing compiz and not experienced a benefit? I removed compiz before, but then I couldn't get metacity going without running metacity --replace in a terminal, probably unrelated. Can't remember what it did to boot time.

I run a 32bit gutsy on intel hardware, pretty standard laptop config.

---

### Post by dmontalvao on 2007-10-31
LMAO!!! I think this will be a very hard thread to read! :D

[PHP](process:22215): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:22219): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 20: [[: not found
stdin: is not a tty
SESSION_MANAGER=local/DMS-Ubuntu:/tmp/.ICE-unix/22212
Checking for Xgl: not present. 
Initializing gnome-mount extension
Detected PCI ID for VGA: 00:02.0 0300: 8086:3582 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: 
** (nautilus:22263): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:22263): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:22263): WARNING **: Can not get _NET_WORKAREA

** (nautilus:22263): WARNING **: Can not determine workarea, guessing at layout
present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
** Message: Not starting remote desktop server

** (update-notifier:22410): WARNING **: not starting because user is not in admin group

evolution-alarm-notify-Message: Setting timeout for 24640 1193443200 1193418560
evolution-alarm-notify-Message:  Sat Oct 27 01:00:00 2007

evolution-alarm-notify-Message:  Fri Oct 26 18:09:20 2007

Throttle level is 0
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :20.0
Window manager warning: Failed to read saved session file /root/.metacity/sessions/default0.ms: Failed to open file '/root/.metacity/sessions/default0.ms': No such file or directory
CalDAV Eplugin starting up ...
(evolution:22513): e-data-server-DEBUG: Loaded default categories
alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1870 (alarm_queue_init)
alarm-queue.c:200 (queue_midnight_refresh) - Refresh at Sat Oct 27 01:00:00 2007
 
alarm-notify.c:161 (list_changed_cb) - Adding Calendar file:///root/.evolution/calendar/local/system
alarm-notify.c:462 (alarm_notify_add_calendar) file:///root/.evolution/calendar/local/system - Calendar Open Async... 0x80d6840
alarm-notify.c:161 (list_changed_cb) - Adding Calendar contacts:///
alarm-notify.c:462 (alarm_notify_add_calendar) contacts:/// - Calendar Open Async... 0x80db250
alarm-notify.c:161 (list_changed_cb) - Adding Calendar file:///root/.evolution/memos/local/system
alarm-notify.c:462 (alarm_notify_add_calendar) file:///root/.evolution/memos/local/system - Calendar Open Async... 0x80d6930
alarm-notify.c:161 (list_changed_cb) - Adding Calendar file:///root/.evolution/tasks/local/system
alarm-notify.c:462 (alarm_notify_add_calendar) file:///root/.evolution/tasks/local/system - Calendar Open Async... 0x80e15c0
alarm-notify.c:393 (cal_opened_cb) contacts:/// - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80e0738: Received at thread b55bab90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80db250
alarm-queue.c:581 (load_alarms_for_today) - From Fri Oct 26 18:12:27 2007
 to Fri Oct 26 18:12:27 2007

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80e0738: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) file:///root/.evolution/memos/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80e2360: Received at thread b55bab90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80d6930
alarm-queue.c:581 (load_alarms_for_today) - From Fri Oct 26 18:12:27 2007
 to Fri Oct 26 18:12:27 2007

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80e2360: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) file:///root/.evolution/tasks/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80e2360: Received at thread b55bab90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80e15c0
alarm-queue.c:581 (load_alarms_for_today) - From Fri Oct 26 18:12:27 2007
 to Fri Oct 26 18:12:27 2007

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80e2360: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) file:///root/.evolution/calendar/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80dc990: Received at thread b55bab90
alarm-queue.c:2003 (alarm_que(evolution:22513): e-data-server-DEBUG: Saving categories to "/root/.evolution/categories.xml"[/PHP]

---

### Post by frodon on 2007-10-31
For the record, once i used the "gnome-session-save" command i had the extreme long login problem or exactly after 2 minutes waiting the end of the login process i killed the xserver.
Then i got the idea to put back my feisty session file and i got back to normal except that if i save my session i know i will get the problem on next login.

So i don't know for you but in my case the problem is directly related to the session file and the way gutsy write it, but for the moment i'm not 100% convinced my problem and yours are the same.

---

### Post by dmontalvao on 2007-10-31
Has anyone tried this?

[http://easylinux.info/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://easylinux.info/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)

---

### Post by tact on 2007-10-31
I had the slow loading problem and googled around and found a comment about ensuring that your /etc/hosts file is set up properly.

Apparently your machine's host name should be on the localhost line.   I adjusted my hosts file and saw a huge increase in speed to a useable desktop.

examples

simple /etc/hosts
```

127.0.0.1 localhost  
127.0.1.1 your_machine_name

```

If you are on a domain as well -  a not so simple /etc/hosts
```

127.0.0.1 localhost.your.domain.local localhost  
127.0.1.1 your_machine_name.your.domain.local your_machine_name

```

leave other lines alone (all the ipv6 stuff).

---

### Post by mgmiller on 2007-10-31
Interesting file, I never looked at it before.  Mine was so long the last line said:
"...Too much output, ignoring rest..."

There were hundreds of identical lines referring to an authentication error in mail-notify.  I changed the config in that to a different authentication type for the mail server I need to read and all the errors stopped.  I then erased the contents of my .xsession-errors file and rebooted.

It took 60 seconds from log in to desktop.  Here is the new, improved and current .xsession-errors log file:


```
(process:5786): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:5790): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
INFO: imwheel started (pid=5853)
SESSION_MANAGER=local/tux:/tmp/.ICE-unix/5783
Warning: Only changing the first 7 of 11 buttons.
INFO: imwheel(pid=5853) killed.
INFO: imwheel started (pid=5907)
Unrecognized wheel action in config. Ignoring action.
Left
Unrecognized wheel action in config. Ignoring action.
Right
Unrecognized wheel action in config. Ignoring action.
Thumb1
Unrecognized wheel action in config. Ignoring action.
Thumb2
Unrecognized wheel action in config. Ignoring action.
Left
Unrecognized wheel action in config. Ignoring action.
Right
Unrecognized wheel action in config. Ignoring action.
Left
Unrecognized wheel action in config. Ignoring action.
Right
Unrecognized wheel action in config. Ignoring action.
Thumb1
Unrecognized wheel action in config. Ignoring action.
Thumb1
Unrecognized wheel action in config. Ignoring action.
Thumb2
Unrecognized wheel action in config. Ignoring action.
Thumb2
Unrecognized wheel action in config. Ignoring action.
Thumb1
Unrecognized wheel action in config. Ignoring action.
Thumb2
Unrecognized wheel action in config. Ignoring action.
Thumb1
Unrecognized wheel action in config. Ignoring action.
Thumb2
Unrecognized wheel action in config. Ignoring action.
Thumb1
Unrecognized wheel action in config. Ignoring action.
Thumb2
Unrecognized wheel action in config. Ignoring action.
Thumb1
Unrecognized wheel action in config. Ignoring action.
Thumb2
Unrecognized wheel action in config. Ignoring action.
Left
Unrecognized wheel action in config. Ignoring action.
Right
Unrecognized wheel action in config. Ignoring action.
Thumb1
Unrecognized wheel action in config. Ignoring action.
Thumb1
Unrecognized wheel action in config. Ignoring action.
Thumb2
Unrecognized wheel action in config. Ignoring action.
Thumb2
Unrecognized wheel action in config. Ignoring action.
Left
Unrecognized wheel action in config. Ignoring action.
Thumb1
Unrecognized wheel action in config. Ignoring action.
Thumb1
Unrecognized wheel action in config. Ignoring action.
Thumb2
Unrecognized wheel action in config. Ignoring action.
Left
Unrecognized wheel action in config. Ignoring action.
Right
Unrecognized wheel action in config. Ignoring action.
Thumb1
Unrecognized wheel action in config. Ignoring action.
Thumb2
Unrecognized wheel action in config. Ignoring action.
Thumb1
Unrecognized wheel action in config. Ignoring action.
Thumb2
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:02e0 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: 

Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0
present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Starting gdesklets-daemon...

Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]Checking for FBConfig: 
Connecting to daemon [          ###]present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]Initializing nautilus-image-converter extension

Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]Initializing gnome-mount extension

Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]evolution-alarm-notify-Message: Setting timeout for 52713 1193889600 1193836887
evolution-alarm-notify-Message:  Thu Nov  1 00:00:00 2007

evolution-alarm-notify-Message:  Wed Oct 31 09:21:27 2007


Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]Initializing nautilus-open-terminal extension

Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1870 (alarm_queue_init)
alarm-queue.c:200 (queue_midnight_refresh) - Refresh at Thu Nov  1 00:00:00 2007
 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/marty/.evolution/calendar/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/marty/.evolution/calendar/local/system - Calendar Open Async... 0x80da170
alarm-notify.c:220 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:462 (alarm_notify_add_calendar) contacts:/// - Calendar Open Async... 0x80da190
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/marty/.evolution/tasks/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/marty/.evolution/tasks/local/system - Calendar Open Async... 0x80e4a50
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/marty/.evoluti
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]on/memos/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/marty/.evolution/memos/local/system - Calendar Open Async... 0x80e8910
alarm-notify.c:393 (cal_opened_cb) file:///home/marty/.evolution/calendar/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80ea400: Received at thread b4678b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80da170
alarm-queue.c:581 (load_alarms_for_today) - From Wed Oct 31 09:21:40 2007
 to Wed Oct 31 09:21:40 2007

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80ea400: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) file:///home/marty/.evolution/tasks/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80e6960: Received at thread b4678b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80e4
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]a50
alarm-queue.c:581 (load_alarms_for_today) - From Wed Oct 31 09:21:40 2007
 to Wed Oct 31 09:21:40 2007

alarm-queue.c:518 (load_alarms) 
alarm-notify.c:393 (cal_opened_cb) contacts:/// - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:393 (cal_opened_cb) file:///home/marty/.evolution/memos/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:349 (alarm_msg_received) - 0x80e9788: Received at thread b4678b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80da190
alarm-notify.c:337 (alarm_msgport_replied) - 0x80e6960: Replied to GUI thread
alarm-queue.c:581 (load_alarms_for_today) - From Wed Oct 31 09:21:41 2007
 to Wed Oct 31 09:21:41 2007

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:349 (alarm_msg_received) - 0x80e3708: Received at thread b4678b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80
Connecting to daemon [         ### ]
Connecting to daemon [          ###]
Connecting to daemon [         ### ]
Connecting to daemon [        ###  ]
Connecting to daemon [       ###   ]
Connecting to daemon [      ###    ]
Connecting to daemon [     ###     ]
Connecting to daemon [    ###      ]
Connecting to daemon [   ###       ]
Connecting to daemon [  ###        ]
Connecting to daemon [ ###         ]
Connecting to daemon [###          ]
Connecting to daemon [ ###         ]
Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
Connecting to daemon [    ###      ]
Connecting to daemon [     ###     ]
Connecting to daemon [      ###    ]
Connecting to daemon [       ###   ]
Connecting to daemon [        ###  ]
Connecting to daemon [         ### ]
Connecting to daemon [          ###]/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

Connecting to daemon [         ### ]
                                        
Connected to daemon in 29140 milliseconds.

(gnome-panel:5876): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -4 and height 24

** (gnome-panel:5876): WARNING **: Failed to get pixmap 14680493,-1,-1

** (gnome-panel:5876): WARNING **: Failed to get pixmap 14680493,-1,-1

** (gnome-panel:5876): WARNING **: Failed to get pixmap 14680493,-1,-1

** (gnome-panel:5876): WARNING **: Failed to get pixmap 14680493,-1,-1
```

---

### Post by #Reistlehr- on 2007-10-31
(You can turn off 3rd button emulation in xorg.conf? right? argh)

Ok, one thing i've been testing out, only it's seemed to not help THAT much, just cut a few minutes, is, use the command
```
rm -rf ~/.nautilus/*
``` 
This will remove all the nautilus sessions 

@dm: That's a fix for a different bug. That is for long boot time, before GDM is initialized. 
@tact: First thing i tried, lol, didnt work :(

Frodon, from all the research i've been doing, i think there are atleast 2 problems, with like symptoms, and people just keep getting them confussed, or don't know the difference.

I think a few variations of the bug are,

[LIST=1]
[*]1After login, you have no desktop. No gnome-splash, no keyring manager, no gnome-panel, and only a mouse. You are stuck on this screen for say, 60 seconds, untill your panels, wallpaper and other appear.
[*]2The second is, you have your panel, no functionality, no icons, no wallpaper, none of the above except a mouse, and your non-functioning panel. After about 60 seconds, alverything will binge and finally appear at once.
[*]3You get your gnome-splash screen, possibly a flash of the gnome-panel, but no wallpaper. You have a moveable mouse, but that's it. If Compiz is enabled, it is most likley the problem.
[/LIST]

---

### Post by cowanh00 on 2007-10-31
> **#Reistlehr- said:**
> 
[LIST=1]
[*]1After login, you have no desktop. No gnome-splash, no keyring manager, no gnome-panel, and only a mouse. You are stuck on this screen for say, 60 seconds, untill your panels, wallpaper and other appear.
[/LIST]

You have summed up my problem exactly here (except it is about 40-50 seconds for me). I've noticed quite a number of people on here have posted that they're using 64 bit. I do have a 64 bit Dual Core Intel processor but I'm running a 32 bit version of Ubuntu.

---

### Post by frodon on 2007-10-31
Please think to post your experience and session files to the launchpad bug report, it will be more useful than posting here since many ubuntu developers only use launchpad :
[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544)

---

### Post by tact on 2007-10-31
Just to repeat my posting a day or so ago...  if your gnome desktop is taking a long time to get you to a useable desktop - check your hosts file.

When I googled the same problem some time back I found this link to a bug that goes back at least to Feisty...  

[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/94048](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/94048)

worked for me.  much faster now

---

### Post by sleepykit on 2007-10-31
Xsession-errors
```
(process:5789): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:5793): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/lionheart:/tmp/.ICE-unix/5786
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Initializing gnome-mount extension
```
I couldn't find that process after the fact...

---

### Post by #Reistlehr- on 2007-10-31
If anyone has a working setup, can you post the .xsession-errors from the wroking setup

---

### Post by nickless on 2007-11-01
> **tact said:**
> Just to repeat my posting a day or so ago...  if your gnome desktop is taking a long time to get you to a useable desktop - check your hosts file.

When I googled the same problem some time back I found this link to a bug that goes back at least to Feisty...  

[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/94048](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/94048)

worked for me.  much faster now

Didn't help...

---

### Post by pasokon on 2007-11-01
*Here is my .xsessions-errors* From login to a useable desktop it takes about 50 seconds. In my newbie humble opinion this is too long!:(

Also, I edited my name out here and MORE IMPORTANTLY put in italics what may be a problem?

Something weird is going on with a metacity file?
_____________________________________________________________________________________
(process:5903): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5907): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/etc/X11/Xsession.d/40guidance-displayconfig_restore: 11: /usr/bin/displayconfig-restore: not found
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/scim.
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
Smart Common Input Method 1.4.7

Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
FreeFontPath: FPE "/usr/share/fonts/X11/misc/" refcount is 2, should be 1; fixing.
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
GTK Panel of SCIM 1.4.7

Starting SCIM as daemon ...
SCIM has been successfully launched.
Xlib:  extension "XEVIE" missing on display ":1.0".
SESSION_MANAGER=local/proteusbox:/tmp/.ICE-unix/5900
Window manager warning: Failed to read saved session file */home/**username**/.metacity/sessions/default0.ms: Failed to open file '/home/**username**/.metacity/sessions/default0.ms': No such file or directory*
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald

---

### Post by thalavoy on 2007-11-02
Any one tried running (from terminal) 'sudo fc-cache' to see if this made any difference?

---

### Post by mgmiller on 2007-11-02
> Also, I edited my name out here and MORE IMPORTANTLY put in italics what may be a problem?

Something weird is going on with a metacity file?

That error does not appear in my .xsessions-errors file, but I still have the long long wait for desktop.

What does appear to be common to everyone are the several "Refusing to initialize GTK+" errors and warnings at the beginning of the file.

---

### Post by ocian on 2007-11-02
> **mgmiller said:**
> 

What does appear to be common to everyone are the several "Refusing to initialize GTK+" errors and warnings at the beginning of the file.
I have been following this thread and I was wondering about that too. I don't think that is what is making it load slow, but who knows at this point. 

I have found some weird lines in my xsession-errors
```
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Failed to read saved session file /home/ianmac/.metacity/sessions/default0.ms: Failed to open file '/home/ianmac/.metacity/sessions/default0.ms': No such file or directory
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
** Message: Not starting remote desktop server
```

and

```
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing gnome-mount extension

** (gnome-panel:5183): WARNING **: Invalid borders specified for theme pixmap:
** (gnome-panel:5183): WARNING **: invalid source position for horizontal gradient

```

---

### Post by Arthur Archnix on 2007-11-02
I'm not sure if this is related, but I can't change my background colour that appears while the desktop is loading. I've changed my desktop background to black. I've also changed my login screen background colour to black. Once I successfully enter my username and password, the background changes to default brown, then once desktop is loaded black. So where is Ubuntu getting this information from and why? And could this lookup be the cause of the slowdown?

EDit: I'm not asking for troubleshooting help with this strange problem, I'm mentioning it in case it helps narrow down the source of the problem for the slow logins.

---

### Post by ocian on 2007-11-02
Arthur,

I've noticed the flash of brown background screen also....

---

### Post by Stingrey on 2007-11-02
I seem to have fixed this issue for myself. For anyone who wants to try this out - do not use the .gtkrc file while logging in. I disabled it by going to the login window preferences. Using .gtkrc somehow slows down the entire x-session-manager process, which makes it look as if compiz is at fault. YMMV.

EDIT: I sacrificed compiz fusion as well to get all the speed I wanted.

EDIT #2: Problem recurs when I'm not connected to any network. Hmm this is really funny now.

---

### Post by #Reistlehr- on 2007-11-02
Ok guys, and gals, this is what i have come up with:

It seems that there are two problems that people are getting confused. I myself, had a hard time distinguishing the differences between them. Well, here is what I have seemed to have come up with:

Problem 1: There is a problem with network manager after login. I don't know exactly why, but i am speculating that it has to do with Ubuntu and IPv6, or perhaps it's trying to get a DHCP address on a device that isnt present/intiated. For example, on my laptop, when i plug in the ethernet cable, and my wireless is turned on, i do not experience any problem. When i either turn off my wireless of unplug the ethernet, the problem persists. But, it's not 100% of the time, that this affects me. This seems be be affecting the i386 people more.

Problem 2: Compiz. It seems that this bug is more dominant in AMD64. When i have normal effects enabled, the problem does not exists, but as soon as ccsm (compizconfig-settings-manager) is installed, and used, compiz begins to lag GDM on startup.

It also seems that these two problems can exist together, in which they overlap one another. I have spent the past 2 days, if you could tell I have not been very active in trying hundred of permutations in attempting to narrow this down a little bit. 

Things that stuck out from logs, but rulled irrelevant:
	
	1. AppArmor - Didn't exist in feisty by default, causes multiple audits in the system init sequence. Removing AppArmor from booting up, the problem still exists.
	
	2. Session Errors: As pasokon has pointed out, xsession cannot init a saved session. This is not a problem. the command: **rm -rf .nautilus/*** or **rm -rf .metacity/sessions/*** will fix this. All it is are sessions saved states that are supposed to make it more of a *out-of-box-experience*. (i think). But this is not related to gnome's sessions. Which brings me to the next point.
	
	3. Gnome-Sessions: Thought to be the culprit on day three. But, it wasnt. There is a bug however, on clean installs, where gnome-session-manager incorrectly or fails to save a session log, for inclusion on next boot. The command, gnome-session-save however will save the current session, when run from the command line. Note: Has been known to cause more problems, lol.
	
	4. Network-Manager: I spent a lot of time on this, installing, removing, editing, and tweaking network manager, and 3rd party apps to see if this has any influence on this problem. Which is what helped me determine the possibilities of two problems, that are alike in much simularity.
	
	5. Compiz.real: I figured this could be a problem when i saw the line */usr/bin/compiz.real (video) * as ocian has pointed out. Now, this is not what was causing it. A simple fix, is to uncheck the box in the Advanced Desktop Appearance Settings window (ccsm) that handles Video Playback, in the Utility category.
	
	6. xgl not present: This is a log in xsession for nvidia users. Not a problem, as it's a module/extension for ati cards. 
	
	7. Xclient-scripts: Whether a new user is logging in, xclient scripts are enabled or disabled, the problem is still existant in gnome. 

	8. mgmiller: refusal GTK+ messages. Don't know what it means, i would like to know, but they exist on working setups.

	9. Bluetooth: Seems to be causing problems for a lot of people. It's loading bluetooth on computers that don't even have bluetooth. It's a pain to remove. 

So my conclusion so far is that two problems are present. Some have one problem, some have the other, some have both. 

A few fix ideas:

Disable compiz. Remove ccsm.

Comment out non-loopback (lo) devices in /etc/network/interfaces

Change the ugly brown background to something nicer while you wait:
```

gksudo gedit /etc/gdm/PreSession/Default 

Look for:
BACKCOLOR="#DAB082"

And change, DAB082 to a color of your choice. For a black background try:
BACKCOLOR="#000000"

Save, and restart!

```

[NOTE] This is only relevant to those who are having the compiz issue. And... I'm still looking. Seems that once compizconfig-settings-manager is installed, the problem is prevailiant. Whether it is a network or compiz problem. Even if you disabled compiz, it's like whatever changes it made are still active. One thing to suggest possibly, is to deactivate dbus plugin in the ccsm. Hopefully that works.

Keywords:
	ccsm - compizconfig-settings-manager - needed to run compiz completely in gutsy. Not included by default, requires apt-getting. Can be accessed from Advanced Appearance Settings Manager ? i think.

So, hopefully i'm on the right track. I'll see what else i can come up with.

---

### Post by allo2u on 2007-11-02
Edit: my post is not needed anymore. I'm experiencing the same problem. 
Great job you did there #Reistlehr-, I might try your solutions if i have time for it.
I hope you get some assistance from the devs.

---

### Post by mgmiller on 2007-11-04
> **Stingrey said:**
> I seem to have fixed this issue for myself. For anyone who wants to try this out - do not use the .gtkrc file while logging in. I disabled it by going to the login window preferences. Using .gtkrc somehow slows down the entire x-session-manager process, which makes it look as if compiz is at fault. YMMV.

EDIT: I sacrificed compiz fusion as well to get all the speed I wanted.

EDIT #2: Problem recurs when I'm not connected to any network. Hmm this is really funny now.

I assume you are referring to the GtkRc file: entry on the general tab of the login preferences applet.

Mine is not now, nor has it ever been checked.  The grayed out choice next to it says "none", but I still have the log in delay problem.

---

### Post by mgmiller on 2007-11-04
#Reistlehr- You proposed:

> And... I'm still looking. Seems that once compizconfig-settings-manager is installed, the problem is prevailiant. Whether it is a network or compiz problem. Even if you disabled compiz, it's like whatever changes it made are still active. 

I have one machine that was a clean install of feisty that was upgraded to Gutsy.  It never had the CCSM installed on it and the effects are kept at the lowest or middle level.  This machine also exhibits the long logon bug.

---

### Post by Arthur Archnix on 2007-11-04
@#Reistlehr: A++, would read again!!

Seriously, thanks for all that hard work. Completely uninstalling compiz from the system and setting metacity as the default in gconf restored my snappy login. Your colour change thing helped too. I think that should be filed as a bug though. There's no reason why that colour shouldn't be configurable through a gui. This is Ubuntu after all, and anyone who changes the login background, and desktop background, should expect to not see anymore browntown.

EDIT: I just thought of a second change from Feisty to Gutsy. They changed the default wm from metacity to compiz. What would happen if you set metacity as the default wm and then started compiz as a session custmization, restoring the old feisty behaviour? Has anyone tried this?

---

### Post by #Reistlehr- on 2007-11-04
Ok guys, so i've been doing even more work.I think i might have made another breakthrough. It seems that everytime i enable my restricted drivers, for nvidia, or wireless firmware. I'm going to explore this a little bit more, and i'll repost when i find out more.

But there are DEFINETLY 2 problems existing here. 1 Compiz issue, and 1 network issue. 

I'm gonna find out which one is which.

---

### Post by #Reistlehr- on 2007-11-04
Ok Update:

I have two laptops here running side by side. I have a default image I made, so I don't have to wait to reinstall. I think these hard drives have been used more than, erm, got to keep it clean ;-). Well here is a summary of my logs, from this weekend. I&#8217;ll also update the launch pad post after I get some feedback from some of you.

Well, I&#8217;ve been working on this problem quite a bit. Mostly because i was laid off and have no job :D but that's beside the point he he. Here are my findings from this weekend.

Fresh install, it works like it should before any 3rd party or any desired files/settings are applied. It works whether or not any internet connection is supplied. So this was my starting point.

Next what i did, was keep two stop watches next to their respective notebook (i don&#8217;t feel like hosing my server yet), and i made a log on my other desktop of what was going on.

So, Laptop 1, i installed nVidia, AND the Wireless firmware drivers. It was nice, because in gutsy, by downloading the firmware from the restricted drivers module it works, but this is partly when the problem started occurring. 

So Laptop 2, i kept as my control and let it run for a little, restarted, never installed any 3rd party apps or setting changes. I let it sit off for a little bit, turned it back on. Repeated. Every time, on a stock install, it booted fine.

Laptop1, on the other hand, was not so happy. So after installing both restricted drivers, the problem started occurring. Uh-oh. So, the next thing I did was remove both restricted drivers, and guess what, the problem was no longer existent. The next step was to power cycle the laptop randomly a few times to make sure the problem couldn&#8217;t be confirmed again, with both drivers disabled. And luckily, it did not reoccur. 

Now I knew where the two problems were most likely originating from.  I went back to laptop 2 and installed the nVidia drivers. (ATI Users, don&#8217;t worry, just read).  On laptop 1, I enabled the wireless firmware. 

Results &#8211; Laptop 2 (nVidia) could reproduce the problem.
	   Laptop 1 (wireless) could  not reproduce the problem.
Now, each time I would install/uninstall a driver during this test, I would repeat it 4 times, with and without a hard wired Ethernet connection.  

So it seems that there are definitely two problems here. One is a Compiz error, and the other seems to be an nVidia bug. The dmesg output that would seem to link the login lag to the eth devices, was a little misleading, as it is irrelevant. Some of you though, might have a 3rd problem, which would have the effects of this bug. That would be extremely discerning to myself, as I can&#8217;t put any input on that.

The next thing on my agenda, for laptop2, (which was the laptop with out the problem), was to install the official nVidia drivers, *** supplied by nVidia. I wanted to see if this would cause the same problem as the nvidia-glx-new drivers. So I installed the build-essential package, just to be safe, and tested it out. It did not have an impact.

So I went into VTY1, stopped gnome, and selected NO for nvidia&#8217;s 32-bit OpenGL Library. Install was successful.  I ran sudo nvidia-xconfig &#8211;add-argb-glx-visuals afterwards, went into run level 6 for a restart, and restarted the computer. Hmm and it seemed that X wouldn&#8217;t start. Lol. Well, I played around got  it to install, and the problem still existed.

Ok, well  this is starting to feel like I&#8217;m back in high school  typing a research paper on the ethics and morals of good vs. evil that were expressed in Lord Of The Flies, and what Ralphy symbolically meant. 
It seems as if there is a problem with nVidia and Gnome2.20. I&#8217;d like somebody to go into their xorg.conf file, and change their video driver from nvidia, to nv (After disabling Compiz) to see if it speeds up this process.

For my laptops, the average working desktop load time was 8.43 seconds. With the bug it dropped between 23 and 47 seconds, randomly. 

So, it seems as if some users are experiencing a problem with nVidia drivers, others with Compiz itself, and other with what seems to be a networking problem  (Not 100% sure about the networking).  Any input greatly appreciated.

Edit: Furthermore, to backup my theory of these horrid nVidia drivers from the repo, When you install the official driver from nvidia, this problem still exists. Another note is, Compiz forces you to use the Restricted drivers, which i can successfully point to this problem.

---

### Post by #Reistlehr- on 2007-11-04
> **Arthur Archnix said:**
> 
EDIT: I just thought of a second change from Feisty to Gutsy. They changed the default wm from metacity to compiz. What would happen if you set metacity as the default wm and then started compiz as a session custmization, restoring the old feisty behaviour? Has anyone tried this?

Good idea, i think i might try that.

---

### Post by sleepykit on 2007-11-05
Thought I'd let you: I went ahead and reinstalled Gutsy from scratch on my Inspiron 1420 laptop and the problem has not returned since.  The upgrage seems to have been the cause of the problem for me, as a fresh install is working fine (and with far fewer issues at the outset).

---

### Post by Partyboi2 on 2007-11-05
[quote=#Reistlehr-;3708008]Ok Update:

It seems as if there is a problem with nVidia and Gnome2.20. I’d like somebody to go into their xorg.conf file, and change their video driver from nvidia, to nv (After disabling Compiz) to see if it speeds up this process.
.

I disabled Compiz and then changed .xorg file to nv and rebooted, but I didnt really notice much difference then when nvidia was set as the video driver. Maybe a couple of sec different, but pretty much the same time for both of them from login to desktop appearing (30's approx.)
Don't give up keep at it :lolflag:

---

### Post by loko on 2007-11-05
> **#Reistlehr- said:**
> Ok Update:

It seems as if there is a problem with nVidia and Gnome2.20. I’d like somebody to go into their xorg.conf file, and change their video driver from nvidia, to nv (After disabling Compiz) to see if it speeds up this process.

Thank you for your investigation. But i have to tell you that this bug must be more than just a nvidia-bug. It seems to be more essential affecting the graphics-system. because i have intel 945GM graphics and also suffer at this bug.

---

### Post by cowanh00 on 2007-11-05
> **loko said:**
> Thank you for your investigation. But i have to tell you that this bug must be more than just a nvidia-bug. It seems to be more essential affecting the graphics-system. because i have intel 945GM graphics and also suffer at this bug.

I have an Intel Graphics card on my laptop too and I have this problem. Thanks for all the help so far.

---

### Post by frodon on 2007-11-05
The first thing to try for anyone having this bug is to login using the gnome failsafe session, if you don't have the long login issue when you are login the failsafe session then there's something in your session file which makes the login really long, typically an apps that doesn't play well when added in the session startup scripts.
If your login using the failsafe session is still long then the problem should not be in the session file.

---

### Post by mal on 2007-11-05
Anyone with very slow login with on-board intel graphics, I suggest you go into bios and increase the video memory allocations.  This worked for me.

Mal

---

### Post by loko on 2007-11-05
> **mal said:**
> Anyone with very slow login with on-board intel graphics, I suggest you go into bios and increase the video memory allocations.  This worked for me.

Mal

how high did you increase it?

---

### Post by cowanh00 on 2007-11-05
> **mal said:**
> Anyone with very slow login with on-board intel graphics, I suggest you go into bios and increase the video memory allocations.  This worked for me.

Mal

I have 256 MB of Video allocation which is already high. I don't think this is to do with the problem. In Feisty I had no problems.

---

### Post by mal on 2007-11-05
> **loko said:**
> how high did you increase it?

On my system, there were 3 different settings related to video memory.  I took them generally out to max to see what happened.  It certainly fixed the problem, but I might go back and fine tune to see how low they can go without causing problems.

Mal

---

### Post by xzero1 on 2007-11-05
I seem to have both problems but he system hangs indefinitely. The cause is clearly network related as one can see in the syslog output. Notice I am using the latest kernel 2.6.23.1 but the problem occurs in the generic gusty kernel as well. I have a more complete syslog if requested. Hopefully, thiis code will be of help.

```
lspci output
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7600 GT (rev a2)
02:08.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
02:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
02:0b.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
```

```
dmesg output
[    0.000000] Linux version 2.6.23.1-hydra (root@keith-desktop) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sat Oct 27 17:58:52 CDT 2007
[    0.000000] Command line: root=UUID=b50f91ac-6b12-4109-b9e5-2fd700e30a85 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 262128) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000F69F0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 3FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: FACP 3FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: DSDT 3FFF30C0, 4AC4 (r1 NVIDIA AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 3FFF0000, 0040
[    0.000000] ACPI: APIC 3FFF7BC0, 007C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 2 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003fff0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 262128) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000003fff0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   262128
[    0.000000] On node 0 totalpages: 262031
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1144 pages reserved
[    0.000000]   DMA zone: 2799 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3527 pages used for memmap
[    0.000000]   DMA32 zone: 254505 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 31656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order.  Total pages: 257304
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=b50f91ac-6b12-4109-b9e5-2fd700e30a85 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[   20.266930] time.c: Detected 2210.119 MHz processor.
[   20.268786] Console: colour VGA+ 80x25
[   20.268789] console [tty0] enabled
[   20.268804] Checking aperture...
[   20.268806] CPU 0: aperture @ e0000000 size 64 MB
[   20.281022] Memory: 990496k/1048512k available (2328k kernel code, 57628k reserved, 1193k data, 308k init)
[   20.281070] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   20.360866] Calibrating delay using timer specific routine.. 4422.94 BogoMIPS (lpj=8845880)
[   20.360903] Security Framework v1.0.0 initialized
[   20.360911] SELinux:  Disabled at boot.
[   20.360998] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   20.361942] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   20.362424] Mount-cache hash table entries: 256
[   20.362586] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   20.362588] CPU: L2 Cache: 1024K (64 bytes/line)
[   20.362591] CPU 0/0 -> Node 0
[   20.362593] CPU: Physical Processor ID: 0
[   20.362595] CPU: Processor Core ID: 0
[   20.362619] SMP alternatives: switching to UP code
[   20.363158] ACPI: Core revision 20070126
[   20.406451] Using local APIC timer interrupts.
[   20.451669] result 12557496
[   20.451670] Detected 12.557 MHz APIC timer.
[   20.452914] SMP alternatives: switching to SMP code
[   20.453214] Booting processor 1/2 APIC 0x1
[   20.463732] Initializing CPU#1
[   20.541174] Calibrating delay using timer specific routine.. 4420.50 BogoMIPS (lpj=8841014)
[   20.541180] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   20.541182] CPU: L2 Cache: 1024K (64 bytes/line)
[   20.541184] CPU 1/1 -> Node 0
[   20.541186] CPU: Physical Processor ID: 0
[   20.541187] CPU: Processor Core ID: 1
[   20.541300] AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ stepping 02
[   20.544759] Brought up 2 CPUs
[   20.545088] NET: Registered protocol family 16
[   20.545250] ACPI: bus type pci registered
[   20.545314] PCI: Using configuration type 1
[   20.546311] ACPI: EC: Look up EC in DSDT
[   20.552168] ACPI: Interpreter enabled
[   20.552171] ACPI: (supports S0 S1 S4 S5)
[   20.552182] ACPI: Using IOAPIC for interrupt routing
[   20.560146] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.560677] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.560813] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   20.561070] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[   20.603444] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   20.603601] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.603753] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[   20.604466] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   20.604617] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   20.604762] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[   20.604914] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[   20.605065] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.605218] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.605370] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.605521] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.605674] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   20.605825] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[   20.605976] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.606128] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.606280] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.606438] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.606595] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.606770] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   20.606931] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   20.607094] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   20.607254] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   20.607361] ACPI: PCI Interrupt Link [APC5] (IRQs *16)
[   20.607525] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[   20.607693] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
[   20.607855] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
[   20.608019] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[   20.608182] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
[   20.608346] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[   20.608456] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
[   20.608618] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[   20.608772] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[   20.608937] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[   20.609100] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[   20.609270] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22) *0, disabled.
[   20.609440] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22) *0, disabled.
[   20.609552] ACPI: Power Resource [ISAV] (on)
[   20.609590] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.609611] pnp: PnP ACPI init
[   20.609617] ACPI: bus type pnp registered
[   20.613378] pnp: PnP ACPI: found 10 devices
[   20.613381] ACPI: ACPI bus type pnp unregistered
[   20.613547] PCI: Using ACPI for IRQ routing
[   20.613550] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.613559] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[   20.624705] NET: Registered protocol family 8
[   20.624706] NET: Registered protocol family 20
[   20.624760] agpgart: Detected AGP bridge 0
[   20.624765] agpgart: Setting up Nforce3 AGP.
[   20.628264] agpgart: AGP aperture is 64M @ 0xe0000000
[   20.640708] pnp: 00:00: ioport range 0x1000-0x107f has been reserved
[   20.640711] pnp: 00:00: ioport range 0x1080-0x10ff has been reserved
[   20.640714] pnp: 00:00: ioport range 0x1400-0x147f has been reserved
[   20.640716] pnp: 00:00: ioport range 0x1480-0x14ff has been reserved
[   20.640718] pnp: 00:00: ioport range 0x1800-0x187f has been reserved
[   20.640720] pnp: 00:00: ioport range 0x1880-0x18ff has been reserved
[   20.640727] pnp: 00:01: iomem range 0xd0000-0xd3fff has been reserved
[   20.640730] pnp: 00:01: iomem range 0xf0000-0xf7fff could not be reserved
[   20.640732] pnp: 00:01: iomem range 0xf8000-0xfbfff could not be reserved
[   20.640734] pnp: 00:01: iomem range 0xfc000-0xfffff could not be reserved
[   20.641028] PCI: Bridge: 0000:00:0b.0
[   20.641029]   IO window: disabled.
[   20.641033]   MEM window: e4000000-e6ffffff
[   20.641035]   PREFETCH window: d0000000-dfffffff
[   20.641040] PCI: Bridge: 0000:00:0e.0
[   20.641042]   IO window: c000-cfff
[   20.641044]   MEM window: e7000000-e8ffffff
[   20.641045]   PREFETCH window: e9000000-e9ffffff
[   20.641054] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   20.641095] NET: Registered protocol family 2
[   20.644677] Time: acpi_pm clocksource has been installed.
[   20.676701] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   20.677028] TCP established hash table entries: 131072 (order: 9, 3145728 bytes)
[   20.679811] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   20.680741] TCP: Hash tables configured (established 131072 bind 65536)
[   20.680745] TCP reno registered
[   20.692797] checking if image is initramfs... it is
[   23.658906] Freeing initrd memory: 38558k freed
[   23.693483] audit: initializing netlink socket (disabled)
[   23.693499] audit(1194251609.392:1): initialized
[   23.695669] VFS: Disk quotas dquot_6.5.1
[   23.695716] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   23.695798] io scheduler noop registered
[   23.695799] io scheduler anticipatory registered
[   23.695801] io scheduler deadline registered
[   23.695885] io scheduler cfq registered (default)
[   23.751409] Boot video device is 0000:01:00.0
[   23.770212] Real Time Clock Driver v1.12ac
[   23.770304] Linux agpgart interface v0.102
[   23.770306] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.770400] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.770503] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   23.770864] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.771415] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   23.772027] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.772164] input: Macintosh mouse button emulation as /class/input/input0
[   23.772276] PNP: No PS/2 controller found. Probing ports directly.
[   24.027096] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.027289] mice: PS/2 mouse device common for all mice
[   24.027466] TCP cubic registered
[   24.027472] NET: Registered protocol family 1
[   24.027664] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   24.027673] Freeing unused kernel memory: 308k freed
[   25.223361] fuse init (API version 7.8)
[   25.772205] usbcore: registered new interface driver usbfs
[   25.772230] usbcore: registered new interface driver hub
[   25.773103] usbcore: registered new device driver usb
[   25.773919] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.773941] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.775184] NFORCE3-250: IDE controller at PCI slot 0000:00:08.0
[   25.775285] NFORCE3-250: chipset revision 162
[   25.775287] NFORCE3-250: not 100% native mode: will probe irqs later
[   25.775290] NFORCE3-250: BIOS didn't set cable bits correctly. Enabling workaround.
[   25.775294] NFORCE3-250: 0000:00:08.0 (rev a2) UDMA133 controller
[   25.775301]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   25.775311]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   25.775318] Probing IDE interface ide0...
[   25.787029] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   26.065339] hda: Maxtor 6L300R0, ATA DISK drive
[   26.345141] hdb: Maxtor 6Y120P0, ATA DISK drive
[   26.402528] hda: selected mode 0x46
[   26.404145] hdb: selected mode 0x46
[   26.404260] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   26.426187] Probing IDE interface ide1...
[   27.164562] hdc: LITE-ON DVDRW SHM-165P6S, ATAPI CD/DVD-ROM drive
[   27.836257] hdc: host side 80-wire cable detection failed, limiting max speed to UDMA33
[   27.836261] hdc: selected mode 0x42
[   27.836552] ide1 at 0x170-0x177,0x376 on irq 15
[   27.849526] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[   27.849533] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 22
[   27.849976] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   27.849983] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   27.850409] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   27.850432] ohci_hcd 0000:00:02.0: irq 22, io mem 0xea001000
[   27.857928] SCSI subsystem initialized
[   27.865306] libata version 2.21 loaded.
[   27.910675] usb usb1: configuration #1 chosen from 1 choice
[   27.910769] hub 1-0:1.0: USB hub found
[   27.910777] hub 1-0:1.0: 4 ports detected
[   28.016511] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[   28.016519] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 21
[   28.017054] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   28.017063] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   28.016798] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   28.016824] ohci_hcd 0000:00:02.1: irq 21, io mem 0xea002000
[   28.077465] usb usb2: configuration #1 chosen from 1 choice
[   28.077488] hub 2-0:1.0: USB hub found
[   28.077496] hub 2-0:1.0: 4 ports detected
[   28.183697] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[   28.183705] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 20 (level, high) -> IRQ 20
[   28.184152] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   28.184159] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   28.184222] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   28.184256] ehci_hcd 0000:00:02.2: debug port 1
[   28.184259] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[   28.184271] ehci_hcd 0000:00:02.2: irq 20, io mem 0xea003000
[   28.184276] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.184379] usb usb3: configuration #1 chosen from 1 choice
[   28.184404] hub 3-0:1.0: USB hub found
[   28.184412] hub 3-0:1.0: 8 ports detected
[   28.291962] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   28.291971] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   28.292494] skge 1.11 addr 0xe8000000 irq 19 chip Yukon-Lite rev 9
[   28.292675] skge eth0: addr 00:14:85:0c:a6:af
[   28.303061] hda: max request size: 512KiB
[   28.309122] hda: Host Protected Area detected.
[   28.309125] 	current capacity is 586112591 sectors (300089 MB)
[   28.309126] 	native  capacity is 586114704 sectors (300090 MB)
[   28.321988] hda: Host Protected Area disabled.
[   28.321993] hda: 586114704 sectors (300090 MB) w/16384KiB Cache, CHS=36483/255/63, UDMA(133)
[   28.323534] hda: cache flushes supported
[   28.323575]  hda: hda1 hda2 hda3 hda4 < hda5 >
[   28.358947] hdb: max request size: 128KiB
[   28.359068] hdb: 240121728 sectors (122942 MB) w/7936KiB Cache, CHS=65535/16/63, UDMA(133)
[   28.359196] hdb: cache flushes supported
[   28.359213]  hdb: hdb1 hdb2 hdb3
[   28.387383] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   28.387394] Uniform CD-ROM driver Revision: 3.20
[   28.826570] kjournald starting.  Commit interval 5 seconds
[   28.826123] EXT3-fs: mounted filesystem with ordered data mode.
[   29.239024] usb 3-7: new high speed USB device using ehci_hcd and address 4
[   29.371354] usb 3-7: configuration #1 chosen from 1 choice
[   29.371414] hub 3-7:1.0: USB hub found
[   29.371516] hub 3-7:1.0: 4 ports detected
[   29.782607] usb 1-3: new low speed USB device using ohci_hcd and address 3
[   30.005548] usb 1-3: configuration #1 chosen from 1 choice
[   30.314228] usb 2-3: new low speed USB device using ohci_hcd and address 2
[   30.537166] usb 2-3: configuration #1 chosen from 1 choice
[   30.742046] usb 3-7.1: new full speed USB device using ehci_hcd and address 5
[   30.869153] usb 3-7.1: configuration #1 chosen from 1 choice
[   37.669528] input: PC Speaker as /class/input/input1
[   37.806626] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   37.806646] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2000
[   37.962081] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   38.013701] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   38.137265] input: Power Button (FF) as /class/input/input2
[   38.137297] ACPI: Power Button (FF) [PWRF]
[   38.137347] input: Power Button (CM) as /class/input/input3
[   38.137371] ACPI: Power Button (CM) [PWRB]
[   38.678600] usbcore: registered new interface driver hiddev
[   38.687315] input: CHICONY USB Keyboard as /class/input/input4
[   38.687365] input: USB HID v1.10 Keyboard [CHICONY USB Keyboard] on usb-0000:00:02.0-3
[   38.693930] input: CHICONY USB Keyboard as /class/input/input5
[   38.693983] input: USB HID v1.10 Mouse [CHICONY USB Keyboard] on usb-0000:00:02.0-3
[   38.700943] input: Logitech USB Receiver as /class/input/input6
[   38.700995] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.1-3
[   38.701008] usbcore: registered new interface driver usbhid
[   38.701011] drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   38.737202] Linux video capture interface: v2.00
[   38.916840] nvidia: module license 'NVIDIA' taints kernel.
[   39.172270] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   39.172280] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 16
[   39.172579] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
[   39.205635] usblp0: USB Bidirectional printer dev 5 if 0 alt 1 proto 2 vid 0x03F0 pid 0x3002
[   39.205663] usbcore: registered new interface driver usblp
[   39.514449] bttv: driver version 0.9.17 loaded
[   39.514455] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   39.514516] bttv: Bt8xx card found (0).
[   39.514785] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   39.514794] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   39.514805] bttv0: Bt878 (rev 2) at 0000:02:0a.0, irq: 18, latency: 32, mmio: 0xe9000000
[   39.514813] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   39.514816] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   39.514848] bttv0: gpio: en=00000000, out=00000000 in=00fffffb [init]
[   39.517351] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   39.542439] tveeprom 2-0050: Hauppauge model 38101, rev B226, serial# 1362074
[   39.542442] tveeprom 2-0050: tuner model is Temic 4036FY5 (idx 26, type 8)
[   39.542444] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   39.542446] tveeprom 2-0050: audio processor is None (idx 0)
[   39.542448] tveeprom 2-0050: has no radio
[   39.542449] bttv0: Hauppauge eeprom indicates model#38101
[   39.542451] bttv0: tuner type=8
[   39.542483] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   39.542969] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   39.543433] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   39.664278] tuner 2-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   39.664303] tuner 2-0061: type set to 8 (Temic NTSC (4036 FY5))
[   39.664306] tuner 2-0061: type set to 8 (Temic NTSC (4036 FY5))
[   39.676466] bttv0: registered device video0
[   39.676487] bttv0: registered device vbi0
[   39.676507] bttv0: PLL: 28636363 => 35468950 .. ok
[   39.707627] ACPI: PCI Interrupt 0000:02:0a.1[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   39.709689] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   39.709696] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   39.710292] cmipci: no OPL device at 0x388, skipping...
[   39.784578] bt878: AUDIO driver version 0.0.0 loaded
[   40.110125] lp: driver loaded but no devices found
[   40.375745] it87: Found IT8712F chip at 0x290, revision 5
[   40.490731] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ processors (2 cpu cores) (version 2.00.00)
[   40.490323] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
[   40.490327] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[   40.539298] Adding 1550264k swap on /dev/hdb3.  Priority:-1 extents:1 across:1550264k
[   40.945596] EXT3 FS on hda2, internal journal
[   42.441799] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
[   42.452862] No dock devices found.
[   43.309955] skge eth0: enabling interface
[   44.751969] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   44.751985] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   44.752006] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   45.234585] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
[   45.796042] ppdev: user-space parallel port driver
[   46.601959] Capability LSM initialized
[   49.641743] NET: Registered protocol family 17
[   50.906254] skge eth0: disabling interface
[   50.907480] skge eth0: enabling interface
[   51.673919] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
[   58.774795] NET: Registered protocol family 10
[   58.774912] lo: Disabled Privacy Extensions
[   67.142845] eth0: no IPv6 routers present
```
```

relevant syslog output:
Nov  5 08:12:22 keith-desktop kernel: [   39.973298] skge eth0: enabling interface
Nov  5 08:12:22 keith-desktop kernel: [   40.718370] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Nov  5 08:12:22 keith-desktop kernel: [   40.718387] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Nov  5 08:12:22 keith-desktop kernel: [   40.718408] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Nov  5 08:12:22 keith-desktop kernel: [   41.752192] ppdev: user-space parallel port driver
Nov  5 08:12:22 keith-desktop kernel: [   41.915841] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
Nov  5 08:12:22 keith-desktop kernel: [   42.156203] Capability LSM initialized
Nov  5 08:12:23 keith-desktop gdm[6323]: WARNING: gdm_auth_user_add: /home/keith/.Xauthority is not owned by uid 1000. 
Nov  5 08:12:24 keith-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Nov  5 08:12:24 keith-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Nov  5 08:12:24 keith-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Nov  5 08:12:24 keith-desktop NetworkManager: <info>  Activation (eth0) started... 
Nov  5 08:12:24 keith-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  5 08:12:24 keith-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov  5 08:12:24 keith-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov  5 08:12:24 keith-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov  5 08:12:24 keith-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov  5 08:12:24 keith-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov  5 08:12:24 keith-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  5 08:12:24 keith-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov  5 08:12:24 keith-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov  5 08:12:25 keith-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Nov  5 08:12:25 keith-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Nov  5 08:12:25 keith-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov  5 08:12:26 keith-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Nov  5 08:12:26 keith-desktop kernel: [   44.722393] NET: Registered protocol family 17
Nov  5 08:12:30 keith-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov  5 08:12:30 keith-desktop dhclient: DHCPACK from 192.168.1.1
Nov  5 08:12:30 keith-desktop kernel: [   46.318921] skge eth0: disabling interface
Nov  5 08:12:30 keith-desktop kernel: [   46.320122] skge eth0: enabling interface
Nov  5 08:12:30 keith-desktop kernel: [   46.321532] ------------[ cut here ]------------
Nov  5 08:12:30 keith-desktop kernel: [   46.321535] kernel BUG at drivers/net/skge.c:2517!
Nov  5 08:12:30 keith-desktop kernel: [   46.321537] invalid opcode: 0000 [1] SMP 
Nov  5 08:12:30 keith-desktop kernel: [   46.321540] CPU 0 
Nov  5 08:12:30 keith-desktop kernel: [   46.321541] Modules linked in: af_packet binfmt_misc capability commoncap ppdev ac video output sbs dock container battery powernow_k8 cpufreq_stats it87 hwmon_vid eeprom parport_pc lp parport bt878 snd_bt87x snd_cmipci snd_seq_dummy gameport tuner snd_seq_oss snd_pcm_oss snd_mixer_oss snd_pcm tvaudio snd_opl3_lib snd_hwdep snd_mpu401_uart bttv snd_seq_midi snd_seq_midi_event video_buf ir_common snd_seq compat_ioctl32 i2c_algo_bit snd_rawmidi btcx_risc tveeprom snd_timer snd_seq_device videodev v4l2_common usblp snd snd_page_alloc soundcore v4l1_compat nvidia(P) button k8temp i2c_nforce2 shpchp pci_hotplug i2c_core pcspkr evdev ext3 jbd mbcache ide_cd cdrom ide_disk ata_generic libata usbhid hid scsi_mod amd74xx ehci_hcd skge ide_core ohci_hcd usbcore thermal processor fan fuse
Nov  5 08:12:30 keith-desktop kernel: [   46.321587] Pid: 7152, comm: ifconfig Tainted: P        2.6.23.1-hydra #1
Nov  5 08:12:30 keith-desktop kernel: [   46.321589] RIP: 0010:[_end+127994811/2130250520]  [_end+127994811/2130250520] :skge:skge_up+0x813/0x820
Nov  5 08:12:30 keith-desktop kernel: [   46.321598] RSP: 0018:ffff81002cc77d58  EFLAGS: 00010206
Nov  5 08:12:30 keith-desktop kernel: [   46.321600] RAX: ffff810034776000 RBX: 0000000000000000 RCX: ffffc200001b0434
Nov  5 08:12:30 keith-desktop kernel: [   46.321602] RDX: 0000000000000000 RSI: ffffc200001b0420 RDI: ffff8100379bb740
Nov  5 08:12:30 keith-desktop kernel: [   46.321605] RBP: ffff8100379bb000 R08: 0000000034708000 R09: ffff810034301f00
Nov  5 08:12:30 keith-desktop kernel: [   46.321607] R10: ffffc200001b0828 R11: 0000000000000001 R12: ffff8100379bb740
Nov  5 08:12:30 keith-desktop kernel: [   46.321609] R13: ffff810034301f00 R14: 0000000000000000 R15: 0000000000000000
Nov  5 08:12:30 keith-desktop kernel: [   46.321612] FS:  00002b4fe1b046e0(0000) GS:ffffffff80571000(0000) knlGS:0000000000000000
Nov  5 08:12:30 keith-desktop kernel: [   46.321615] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Nov  5 08:12:30 keith-desktop kernel: [   46.321617] CR2: 000000000063c0d8 CR3: 000000002cc23000 CR4: 00000000000006e0
Nov  5 08:12:30 keith-desktop kernel: [   46.321619] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Nov  5 08:12:30 keith-desktop kernel: [   46.321621] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Nov  5 08:12:30 keith-desktop kernel: [   46.321624] Process ifconfig (pid: 7152, threadinfo ffff81002cc76000, task ffff8100342f0ea0)
Nov  5 08:12:30 keith-desktop kernel: [   46.321626] Stack:  0000000000000246 ffff810000000000 ffff8100379bb228 0000000000000000
Nov  5 08:12:30 keith-desktop kernel: [   46.321630]  ffff810034301f3c 0000000000000000 00004000379bb740 0000000000004000
Nov  5 08:12:30 keith-desktop kernel: [   46.321634]  0000000000001043 ffff81003470c000 ffff8100379bb780 00000000000005d4
Nov  5 08:12:30 keith-desktop kernel: [   46.321637] Call Trace:
Nov  5 08:12:30 keith-desktop kernel: [   46.321648]  [_end+128000747/2130250520] :skge:skge_change_mtu+0x63/0x80
Nov  5 08:12:30 keith-desktop kernel: [   46.321655]  [dev_set_mtu+53/112] dev_set_mtu+0x35/0x70
Nov  5 08:12:30 keith-desktop kernel: [   46.321659]  [dev_ioctl+672/928] dev_ioctl+0x2a0/0x3a0
Nov  5 08:12:30 keith-desktop kernel: [   46.321669]  [sock_ioctl+218/576] sock_ioctl+0xda/0x240
Nov  5 08:12:30 keith-desktop kernel: [   46.321674]  [do_ioctl+47/160] do_ioctl+0x2f/0xa0
Nov  5 08:12:30 keith-desktop kernel: [   46.321678]  [vfs_ioctl+116/720] vfs_ioctl+0x74/0x2d0
Nov  5 08:12:30 keith-desktop kernel: [   46.321683]  [sys_ioctl+149/176] sys_ioctl+0x95/0xb0
Nov  5 08:12:30 keith-desktop kernel: [   46.321688]  [system_call+126/131] system_call+0x7e/0x83
Nov  5 08:12:30 keith-desktop kernel: [   46.321695] 
Nov  5 08:12:30 keith-desktop kernel: [   46.321695] 
Nov  5 08:12:30 keith-desktop kernel: [   46.321696] Code: 0f 0b eb fe 66 0f 1f 84 00 00 00 00 00 41 57 41 56 41 55 41 
Nov  5 08:12:30 keith-desktop kernel: [   46.321703] RIP  [_end+127994811/2130250520] :skge:skge_up+0x813/0x820
Nov  5 08:12:30 keith-desktop kernel: [   46.321708]  RSP <ffff81002cc77d58>
Nov  5 08:12:31 keith-desktop kernel: [   47.100619] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
Nov  5 08:14:04 keith-desktop NetworkManager: <info>  Device 'eth0' DHCP transaction took too long (>99s), stopping it. 
Nov  5 08:14:04 keith-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 7104
Nov  5 08:14:04 keith-desktop dhclient: killed old client process, removed PID file
Nov  5 08:14:05 keith-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Nov  5 08:14:05 keith-desktop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth0 
Nov  5 08:14:05 keith-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
Nov  5 08:14:05 keith-desktop NetworkManager: <info>  No DHCP reply received.  Automatically obtaining IP via Zeroconf. 
Nov  5 08:14:05 keith-desktop NetworkManager: <info>  Activation (eth0) failure scheduled... 
Nov  5 08:14:05 keith-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
Nov  5 08:14:05 keith-desktop NetworkManager: <info>  Activation (eth0) failed. 
Nov  5 08:14:05 keith-desktop NetworkManager: <info>  Deactivating device eth0. 
Nov  5 08:17:01 keith-desktop /USR/SBIN/CRON[7280]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  5 08:32:22 keith-desktop -- MARK --
Nov  5 08:32:50 keith-desktop kernel: [  602.484925] SysRq : Keyboard mode set to XLATE
Nov  5 08:32:53 keith-desktop kernel: [  604.138290] SysRq : Emergency Sync
Nov  5 08:32:53 keith-desktop kernel: [  604.137991] Emergency Sync complete
Nov  5 08:32:56 keith-desktop exiting on signal 15
Nov  5 08:33:53 keith-desktop syslogd 1.4.1#21ubuntu3: restart.
```

---

### Post by phonky on 2007-11-05
I'm running gutsy on a macbook pro, thus with

> 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6473 (8.37.6)


I'm having the long login too (#1 I guess: get to hear the login song, but screen stays black for a long time, until I get the desktop).

But when I use a failsafe session, the login is very fast. I'm not into testing all
permutations of settings, though, sorry. I have compiz enabled, and even avant. But I rely on the investigations of other people that this isn't the problem.

But I also get
> (process:5980): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

in .xsession-errors and

> 
[   25.065795] Failure registering capabilities with primary security module.

in dmesg.

But these come now after failsafe session....
I personally guess trackerd to be the culprit, but don't blame me on this...

Deep respect for those debugging...thank you

---

### Post by frodon on 2007-11-05
@phonky, in your case the problem is in your session parameters for sure.
I bet that it is compiz which makes your login really long, swicth back to metacity and save your session (don't forget to check the Gconf keys to be sure) then login and see if there's a difference, if yes then the problem for you is having compiz in the startup session scripts.

---

### Post by #Reistlehr- on 2007-11-05
Yeah but like i said, there are DEFINETLY multiple problems here. And everyone is getting them confussed, although they show similar affects.

I am experiencing a problem with the nVidia drivers one two of my laptops and i have a compiz issue on my desktop as with a few other users.
Some are experiencing problems with the XClient Scripots
A few have a problem with Sessions.

Either some people are completley attempting to help narrow this bug, or the reasons causing it keep getting bigger. hehe

@Loco, the nvidia problem seems to be only one of the problems, as i have stated people are having the same sort of effect form mulitple problems realier in the thread.

@frodon: the failue registering capabilities... message in dmesg i dont think has anything to do with compiz. If youare on metacity, you'll notice that you still get that message along with the GTK+ Refusal in xsession-error. My AMD64 kernels have the failure to register message while my i386 does not report anything like that, and the i386 has the compiz bugs.

Everyone do this if you can/want
```

sudo apt-get install gnome-splashscreen-manager 

```
Open a terminal
```

gnome-splashscreen-manager

```
Then check the box to Show Splashscreen On Startup

Logout and log back in. What does the splashscreen report to you. I bet most of you it will say Compiz.

---

### Post by frodon on 2007-11-05
> **#Reistlehr- said:**
> @frodon: the failue registering capabilities... message in dmesg i dont think has anything to do with compiz. If youare on metacity, you'll notice that you still get that message along with the GTK+ Refusal in xsession-error. My AMD64 kernels have the failure to register message while my i386 does not report anything like that, and the i386 has the compiz bugs.I have tested this in the past with xcompmgr and xfwm4 both gave me long login time if they are in the session file, xfwm4 (the xfce WM) still give me long login time if i set it to start on session startup.
It is for these reasons that i advice to anyone with compiz and long login to at least try with metacity thus it allows to exclude any compiz problems.

In addtiion i found out that the Gconf keys about the WM used are not always up to date which may cause some problems, especially because the gnome-session-save command is looking at the Gconf keys.

---

### Post by #Reistlehr- on 2007-11-05
Very true. I don't even have compiz installed since the nVidia restricted drivers caused the problem on my machine. But i dont know how long i can go without the drivers =/.  But i can say that after i upgraded form Feisty the first time Compiz was causing my problems.  

So agreed, anyone experiencing this problem should definetly disable compiz before helping trouble shoot.

---

### Post by hayesbcaj on 2007-11-05
I'm having the slow login problem as well. If I log in with the failsafe gnome session it flies. What does that mean? Can I get all my settings the same as failsafe?
Edit: compiz is disabled.
Edit: I've also noticed that if I logout then log back in it is very quick. It is only slow if I reboot.

---

### Post by #Reistlehr- on 2007-11-05
> **hayesbcaj said:**
> I'm having the slow login problem as well. If I log in with the failsafe gnome session it flies. What does that mean? Can I get all my settings the same as failsafe?
Edit: compiz is disabled.

From the way it looks, you're experiencing the session bug portion.

---

### Post by phonky on 2007-11-06
> **hayesbcaj said:**
> 
Edit: I've also noticed that if I logout then log back in it is very quick. It is only slow if I reboot.

Good spot! I have the same effect - even if compiz is ENABLED! Can it only be the session then???

---

### Post by pasokon on 2007-11-06
I would like to comment and say that although I am very happy that #Reistlehr has thought long and well about the problems of this thread, I have tested one solution and not had good luck with it.

#Reistlehr -"Comment out non-loopback (lo) devices in /etc/network/interfaces" 

As far as this goes as one way to decrease login time in fact for me it had the opposite effect:

Commenting out all non-loopback devices in /etc/network/interfaces :

```

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

Having done this I restarted. Login time was horrendously log but I endure the five minutes it took to login and the black screen with just a cursor blinking that I face after the GDM login screen. 

"This is just the system getting used to the other network devices being commented out," I thought. 

Logging out the same session, logout out time was so long (over ten minutes) that I held the power button on my computer and force-shutdown the machine.

Is this just my computer and network connection situation? What's going on with this.

I uncommented the other devices and am happier with my situation, so what happened?

---

### Post by #Reistlehr- on 2007-11-06
> **pasokon said:**
> 

I uncommented the other devices and am happier with my situation, so what happened?

You're probably going to want to leave them as the way they originally were.
ex:
```

auto eth1
#iface eth1 inet dhcp

```

Like i said it's a troubleshooting step, and for some people, it worked. This is starting to get hectic with the multiple problems in this one thread. hehe.

---

### Post by #Reistlehr- on 2007-11-06
For those of you experiencing the nvidia bug, i createda bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/160535](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/160535)

---

### Post by spotdog14 on 2007-11-06
my /etc/network/networkinterfaces is as followed:

```
auto lo
iface lo inet loopback
```

Should i change it to inet dhcp?

---

### Post by janko on 2007-11-06
I think I am in the "session bug" group of people... any suggestion about that??

Jan

---

### Post by mikawber on 2007-11-06
I'm having this issue too! It takes about 2-3 minutes for gnome to load up after signing in. Is there a fix for this?

Sorry I don't have time to read all 17 pages.

---

### Post by Arthur Archnix on 2007-11-06
> I'm having this issue too! It takes about 2-3 minutes for gnome to load up after signing in. Is there a fix for this?

Sorry I don't have time to read all 17 pages. 

Definitely maybe. Sorry I can't be more precise. I didn't have time to read the entire description of your problem.

---

### Post by Rinzwind on 2007-11-06
+1 for me too.

Might this be something -->

/var/log$ more Xorg.0.log | grep EE
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

ATI X300 != AIGLX ?

---

### Post by plr4ever on 2007-11-06
I am experiencing the same problem, and i have narrowed it down to the nvidia bug. When i disable desktop effects, it boots more than twice as fast. It login time is not affected when i logout and login again with compiz enabled.

Also, when i run [compiz --replace] in a terminal after booting with metacity, i get this:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0393 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
inotify_add_watch: No such file or directory
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by mikawber on 2007-11-06
> **Arthur Archnix said:**
> Definitely maybe. Sorry I can't be more precise. I didn't have time to read the entire description of your problem.

no need to be prick, I have the same problem as most people. Why should I create a long post explaining the same stuff?

---

### Post by #Reistlehr- on 2007-11-06
I have done some more research. Installing the nvidia-glx-new package for some, creates a session bug. By logging in with Failsafe Gnome -> the login time is normal.

---

### Post by xzero1 on 2007-11-07
I have indefinite stalls as shown in my previous post. Don't know if it is the same problem(s) being considered here (I still think it is). but it has just happened when booting with the Gusty 7.10 live cd -- no compiz, no nvidia no restricted drivers. All the error messages seemed to be network related. This bug seems to be random, though it may have a better chance of occurring when the computer has been off for a while. Since everyone else seems to only have a delayed login, could bootchart be used to isolate their problem?

---

### Post by hayesbcaj on 2007-11-07
Here's my boot chart. I don't understand it but maybe someone can take a look and see if something jumps out. If 34 seconds is the time from pushing the power button then I'm thinking my boot time is pretty quick. Imagine what it could be if there was no delay after gdm splash screen. Does this chart display that delay?
Thanks.

Edit: Does this chart show usplash running twice?

---

### Post by xzero1 on 2007-11-07
I'm certainly no expert on bootchart, I just thought it would help. There is an entire thread with bootcharts posted by other users. It might help to compare your bootchart to some of these.
[http://ubuntuforums.org/showthread.php?t=531453&highlight=bootchart]("http://ubuntuforums.org/showthread.php?t=531453&highlight=bootchart")

---

### Post by Rinzwind on 2007-11-07
bootchart: 25 secondes until it reaches xorg,conf
But it stops when it reaches gnome login and we need the part behind login.

---

### Post by Rinzwind on 2007-11-07
Ok I spent almost 4 days trying to find what's bugging my gnome and I give up.

I am going for a
1. fresh reinstall including /home 
2. before installing software like xgl and compiz I'll have several reboots to see if it re-occurs.

I'll be back in about 20 minutes on a fresh install :)

---

### Post by Rinzwind on 2007-11-07
Vanilla Gutsy with 1 alteration: I inserted my WPA2 key to get to the forum.
From the enter at the password up to the showing of the top panel: 19 seconds.
Can someone say if that's fast/normal/average/slow?

-- more comming.
EDIT 1:

vanilla: 19 sec

Remark: something weird happend: Compiz is working out of the box. Before I had to install xgl-server and this is the 1st time appearance/visual_effects has 'normal' set as true.EDIT: It's very slow and sluggish. Turned it off and chose none. After a reboot it started with the 'composite extension not available' message.
Plus Usplash worked too. Not more naggig of the wrong picture size.

Deleted bottom panel; added all that to the top panel.

Removed: fast user swiching: 19 sec
Removed: tracker: 18 seconds
Installed: Restricted Driver (ATI Accelerated Driver):
13 seconds.
Doing a 2nd reboot: 13 seconds
(me like! me like! :-) )


Software update (suggested by update-manager):
compiz 
compiz-core
compiz-gnome
compiz-plugins
cupsys
cupsys-bsd
cupsys-common
firefox
ghostscript
ghostscript-x
gnome-screensaver
gnome-system-monitor
ubufox
tz-data
libc6
libdecoration0

BRB

EDIT 2: still 13 seconds or there about.

(all checks are done with a shutdown in between)
(all timed with a stopwatch and rounded to 1 second)

- No warnings in any log
- 1 error in the logs: 
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

So this is definatly not an issue involving slow gnome start-up!

Nothing weird inside dmesg too.

and then for the big finaly: 
compiz-manager with everything with it.

---

### Post by fjgaude on 2007-11-07
> **Rinzwind said:**
> From the enter at the password up to the showing of the top panel: 19 seconds.
Can someone say if that's fast/normal/average/slow?


Seems fast to me. My system, with lots of drives and 4400+ dual AMD does it in 32 seconds. But the md raid5 must take some time to setup, also gkrellm, and pidgin. My boot drive is a Seagate perpendicular, late model, fast at seq read of 77 MB/sec.

Using metacity, no compiz...

---

### Post by Rinzwind on 2007-11-07
> **fjgaude said:**
> Seems fast to me. My system, with lots of drives and 4400+ dual AMD does it in 32 seconds. But the md raid5 must take some time to setup, also gkrellm, and pidgin. My boot drive is a Seagate perpendicular, late model, fast at seq read of 77 MB/sec.

Using metacity, no compiz...

Noted and thank you for the info! :) 

Without tracker I can get it down to 13 seconds :) 
Very fast and very nice.

I am now setting up everything on my system I normally use.
I expect that if anything goes wrong itll be with xglserver and compiz.
brb and will edit above post :)

---

### Post by Stingrey on 2007-11-07
Went back to Feisty here, a few days back. Just thought you folks might want to take a look at this [thread]("http://ubuntuforums.org/showthread.php?p=3651885"). Seems like a Gutsy proposed update might solve the problem.

---

### Post by fjgaude on 2007-11-07
I did have tracker installed and it has been that way for weeks. It took about a day for it to index all my files. So my time of 32 seconds includes tracker. Also notice I have VMware kernel mod and I think that takes time too. I'm sure the connect to the Internet is also a hog, loading gkrellm and all the things it sets up, like temps and what nots.

In bootchart I noticed that my CPU never topped out. Seems the disk I/O is the worse time hog. I will be upgrading to an Hitachi 134 MB/sec seq read drive before Christmas. I don't believe in booting from a raid array.

---

### Post by fjgaude on 2007-11-07
> **Stingrey said:**
> Went back to Feisty here, a few days back. Just thought you folks might want to take a look at this [thread]("http://ubuntuforums.org/showthread.php?p=3651885"). Seems like a Gutsy proposed update might solve the problem.

I'm installing the pre-release proposed items now... will see what happens.

---

### Post by Rinzwind on 2007-11-07
eh pre-released proposal? Que? Nani? What's that? Wasda?

---

### Post by fjgaude on 2007-11-07
> **Rinzwind said:**
> eh pre-released proposal? Que? Nani? What's that? Wasda?

Well, if you go to System/Adminstration/Software Sources/Updates you will find a usually unchecked item called "Pre-released updates (gutsy-proposed)". I usually don't have it checked but I did just now and got 87 file updates, GDM being one of them.

I can't say if anything is faster... but I'm satisfied I didn't break the system. <smile>

As the proposed fixes are fully tested and work, then they will come along as updates in due time.

---

### Post by Rinzwind on 2007-11-07
Ok

Well here's my final result:

I now have compiz -with- the freewin/3d windows, 3d atlatis, tile plugins and gnome takes 20/21 seconds.

---

### Post by ton145 on 2007-11-08
Sometime I have the same problem. But in my case, it happened when the computer is not connected to the network and can't find the DNS server.
When I remove the DNS entry in Network Applet, it became fast again..

---

### Post by Stingrey on 2007-11-08
Some more information to add to the confusion.
Installed Gutsy once again. No problems before installing the first updates. Chose not to install updates for Compiz and CUPS (apparently CUPS seems to have some problem with AppArmour).
Things are smooth now after multiple reboots. Hope I havent spoken too soon.

Some of the error messages that appear in the log files seem to be false positives to possible problems.
I still get the following error :

```
Nov  9 07:57:33 reynolds-laptop kernel: [   15.527413] Failure registering capabilities with primary security module.
```

Bluetooth also doesnt seem to be causing any problems even though it is being loaded.

```
Nov  9 07:57:34 reynolds-laptop kernel: [   22.564000] Bluetooth: HCI device and connection manager initialized
Nov  9 07:57:34 reynolds-laptop kernel: [   22.564000] Bluetooth: HCI socket layer initialized
Nov  9 07:57:34 reynolds-laptop kernel: [   22.592000] Bluetooth: L2CAP ver 2.8
Nov  9 07:57:34 reynolds-laptop kernel: [   22.592000] Bluetooth: L2CAP socket layer initialized
Nov  9 07:57:34 reynolds-laptop kernel: [   22.648000] Bluetooth: RFCOMM socket layer initialized
Nov  9 07:57:34 reynolds-laptop kernel: [   22.648000] Bluetooth: RFCOMM TTY layer initialized
Nov  9 07:57:34 reynolds-laptop kernel: [   22.648000] Bluetooth: RFCOMM ver 1.8
```

No problems even when disconnected off the network. Will keep checking this place if I can help.

---

### Post by IamAcoconut on 2007-11-09
I've had this issue since the very first boot. So much for the updates - they're not the case.

---

### Post by SomeGuyDude on 2007-11-10
Pre-released things did nothing for me either. It's driving me crazy because that was one of my big beefs with Vista as well and it's one of the last remaining issues outside of some sound problems.

---

### Post by Piour on 2007-11-10
i dont know if it is related and if it can help. All was very slow to me after upgrading to 7.10 (starting a session, scrolling under firefox, opening a new terminal, etc ...). I removed xgl-server and now all seems to be fine.

computer : dell d420

---

### Post by Vogateer on 2007-11-10
Add me to the list of people having this problem.

I did install a new theme and compizconfig-settings-manager, and installed the svn of Avant Window Navigator, but creating a new user that doesn't use AWN or the new theme solves nothing.

As someone else mentioned, with the new user, I notice the panels coming up for a second, then they disappear and it takes a while to come back up. The initial appearance of the gnome panels are about where I would expect a normal gnome login to be (I've been using it since Dapper, so it "feels" like startup should finish there), but then the panels disappear and it takes a long time to come back. On the first user I created, it takes about 45 seconds to boot to the GDM screen, and about a minute to get gnome started. It is painful.

Booting into a failsafe Gnome takes login time down from a full minute to about 18 seconds for complete loading of everything in the panels, which seems about right. So it appears I'm experiencing the session bug.

I don't think I can provide any more information than others have provided, but I'm vaguely familiar with the command line, and I can try to help a bit, though this is someone else's laptop I'm working on, and I'm sure they'd like it back before too long. ;)

On the bright side, if this problem is resolved, I'll have far too much fun with all the fantastic compiz effects. It's working great on this laptop once gnome gets started. The built-in intel graphics just seems perfect for compiz. Hooray for open source drivers!

---

### Post by Vogateer on 2007-11-10
Well, maybe I was wrong about it being a session bug. I got rid of desktop effects altogether, and just started up with metacity, and things are going much faster now. I have the intel built-in graphics card, and a clean install. I can wait for the effects later when the bugs are squashed, but I would like to help provide information for the bug squashing, though my command line skills aren't such that I'd be of much help. :(

---

### Post by SomeGuyDude on 2007-11-12
> **Vogateer said:**
> Well, maybe I was wrong about it being a session bug. I got rid of desktop effects altogether, and just started up with metacity, and things are going much faster now. I have the intel built-in graphics card, and a clean install. I can wait for the effects later when the bugs are squashed, but I would like to help provide information for the bug squashing, though my command line skills aren't such that I'd be of much help. :(

It's slower with Compiz/etc to login, but it was still slow as balls even fresh. Whereas it used to be a 30 second delay, now it's nearly a minute. A solid minute of just sitting there looking at a beige screen after a 10-15 second boot. Damn annoying.

---

### Post by pasokon on 2007-11-13
This is probably a newbie thing to write but I wonder why, as far as I can remember I have never had to stare at the "stupid beige screen." My screen is black and I think always has been. Could this be related to my version of Gutsy being the product of updates i.e.  Feisty--->Gutsy Beta---->Gutsy Final ? 

Some people a few pages back wanted to know how to change the "stupid beige screen" was there any luck with that from anyone and is it just a matter of going to System-->Admin---Login Window and changing the background color of the LOCAL tab?

:)

---

### Post by nickless on 2007-11-14
Yeah, it worked for me, I now have a nice black screen :D
But changing the background color in the login window settings won't change that beige screen, thats why I asked, how to change it earlier. It only changes the background of the login, so when I booted I got a black background in gdm, then a beige screen until my black wallpaper showed up. That was pretty ugly, now it at least looks a lot smoother ;)

---

### Post by lavinog on 2007-11-14
Has anyone tried killing nautilus when gnome is loading to see if it speeds things up.
I have noticed that if a network share is mapped and that share is unavailable there will be a delay in logging in.
Since people are claiming that gusty is having name resolution issues, there could be a connection.

---

### Post by beasty on 2007-11-15
couldn't it be possible that gnome-panel is a bit f*cked ? cause when i look @ some xsessions outputs it gives errors and when my client logged in earlier i had a 97% cpu usage for 'gnome-panel' then i killed it ... i returned in gnome and it loaded normaly (gnome) 

kr

---

### Post by beasty on 2007-11-15
doing a kill -9 gnome-panel in tty1 as logged in user seems to get it working when you get a black screen

---

### Post by spotdog14 on 2007-11-15
> **pasokon said:**
> This is probably a newbie thing to write but I wonder why, as far as I can remember I have never had to stare at the "stupid beige screen." My screen is black and I think always has been. Could this be related to my version of Gutsy being the product of updates i.e.  Feisty--->Gutsy Beta---->Gutsy Final ? 

Some people a few pages back wanted to know how to change the "stupid beige screen" was there any luck with that from anyone and is it just a matter of going to System-->Admin---Login Window and changing the background color of the LOCAL tab?

:)

no not for me.

---

### Post by trannypunk on 2007-11-15
hp dv2415us, same problem.

I used add/remove and installed Splash Screen. Using the application I enabled and activated my splash screen (which was listed but not active).

Now at login I have a splash screen for a second. It shows gnome sound manager (or something like that) and then goes to the blank screen.

I think it shaved a bit of time off, but maybe just having the splash to look at for a second has fooled me.

Thoughts?

---

### Post by arrizaba on 2007-11-15
For me the fix already posted in the forum (see below) works like a charm...

>  Re: Gutsy GNOME login takes a long time
I had the slow loading problem and googled around and found a comment about ensuring that your /etc/hosts file is set up properly.

Apparently your machine's host name should be on the localhost line. I adjusted my hosts file and saw a huge increase in speed to a useable desktop.

examples

simple /etc/hosts
Code:

127.0.0.1 localhost  
127.0.1.1 your_machine_name

If you are on a domain as well - a not so simple /etc/hosts
Code:

127.0.0.1 localhost.your.domain.local localhost  
127.0.1.1 your_machine_name.your.domain.local your_machine_name

leave other lines alone (all the ipv6 stuff).

---

### Post by spotdog14 on 2007-11-15
> **arrizaba said:**
> For me the fix already posted in the forum (see below) works like a charm...

This is what mine says.... 

```
127.0.0.1	localhost
127.0.1.1	Asus-S5n

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by mgmiller on 2007-11-16
My /etc/hosts looks a bit different.  Is this because I have a static IP?

I am not on a domain.

```
127.0.0.1 localhost.localdomain localhost tux

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet ip6-localnet
ff00::0 ip6-mcastprefix ip6-mcastprefix
ff02::1 ip6-allnodes ip6-allnodes
ff02::2 ip6-allrouters ip6-allrouters
ff02::3 ip6-allhosts ip6-allhosts

# The following lines are desirable for IPv6 capable hosts
# (added automatically by netbase upgrade)

::1 ip6-localhost ip6-loopback
```

---

### Post by Neobuntu on 2007-11-16
I just went through 20 pages and can't find a solution to the gnome panel loading slowly.

I have an update that is "forbidden".

My system is starting to act wonky. The mouse is moving slowly and Firefox is not closing.

I checked my CPU temp and it's fine. fsck is fine.

Any one know what's going on?

---

### Post by mahousaru on 2007-11-17
I just had this issue appear on one of my boxes.  The problem for me to solve it was I had a kernel update that I neglected to reboot :p, a samba update which started throwing up errors and when I rebooted I had slowish uplash screed and it closing early to show some of the boot up dialogue (no errors) and then on login gdm took ages.  

I was in despair as I had too many changes between the last reboot, I fiddled with the xorg.conf as my screen resolution refresh was not sticking.  After 3 or 4 changes and several reboots I then remembered I set the wired connection with a static IP address instead of via dhcp.  I changed it back to dhcp and suddenly it is all fast again.

Dunno if this helps anyone, but normally I set static ips with the auto statement in /etc/network/interfaces, but this was the first time I tried it using the nm-applet.

---

### Post by boast on 2007-11-18
oh, good. I'm not the only one experiencing slow desktop loading. (although my bootchart shows 30 seconds)

My 6 month old windows xp partiton loads to desktop faster...

---

### Post by vampire666eng on 2007-11-18
I have to wait 2:50 minutes to load.

I installed uBuntu 7.10, and from the start the system isn't really responsive.
I mean the login (after I entered username and password) takes a lot of time (far more then 7.04), the programs takes a lot of time loading...even selecting options as "print" a document in OpenOffice or starting the terminal takes ages.

The hard disk is not even working hard during all this...it seams that the system is in idle and then all of a sudden (after some time), the program/process starts.

My specs are:
AMD64 3000+
2GB RAM
6600GT 128MB RAM

This is the time I have to wait before having uBuntu ready:

- From selecting uBuntu in Grub ---> to uBuntu disaplaying login username: 1min 2sec (1:02)

- From selecting pw login to complete desktop ---> 1min 35sec (1:35)

Total time: 2min 37sec (2:37) (obviously not considering the time I spend digiting username and password)

I find it a "bit" too much considering my specs.

EDIT; I tried other times and the total time is 2:50.

EDIT2: added bootchart (that should take in consideration only the things before the login)...isn't that awful?

[Image link]("http://ubuntuforums.org/attachment.php?attachmentid=50088&d=1194978683")

dmesg


```
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f38c0
[    0.000000] Entering add_active_range(0, 0, 524272) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524272
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524272
[    0.000000] On node 0 totalpages: 524272
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292593 pages, LIFO batch:31
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7F00 checksum 0
[    0.000000] ACPI: RSDP 000F7F00, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 7FFF3040, 0030 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FFF30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FFF3180, 61DF (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FFF0000, 0040
[    0.000000] ACPI: MCFG 7FFF9480, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FFF93C0, 006E (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Built 1 zonelists.  Total pages: 520177
[    0.000000] Kernel command line: root=UUID=dfdd5b47-b217-41e6-be2c-bed1e6a2281e ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1809.313 MHz processor.
[   21.631021] spurious 8259A interrupt: IRQ7.
[   21.632888] Console: colour VGA+ 80x25
[   21.633231] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   21.633608] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   21.701077] Memory: 2067704k/2097088k available (2015k kernel code, 28136k reserved, 916k data, 364k init, 1179584k highmem)
[   21.701088] virtual kernel memory layout:
[   21.701089]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   21.701091]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   21.701092]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   21.701093]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   21.701095]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   21.701096]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   21.701097]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   21.701100] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   21.701136] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   21.781020] Calibrating delay using timer specific routine.. 3620.90 BogoMIPS (lpj=7241808)
[   21.781045] Security Framework v1.0.0 initialized
[   21.781051] SELinux:  Disabled at boot.
[   21.781064] Mount-cache hash table entries: 512
[   21.781174] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000000 00000000 00000001
[   21.781183] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.781185] CPU: L2 Cache: 512K (64 bytes/line)
[   21.781188] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000000 00000000 00000001
[   21.781198] Compat vDSO mapped to ffffe000.
[   21.781208] Checking 'hlt' instruction... OK.
[   21.797113] SMP alternatives: switching to UP code
[   21.797278] Freeing SMP alternatives: 11k freed
[   21.797531] Early unpacking initramfs... done
[   22.114468] ACPI: Core revision 20070126
[   22.114540] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.117723] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 00
[   22.117739] Total of 1 processors activated (3620.90 BogoMIPS).
[   22.117875] ENABLING IO-APIC IRQs
[   22.118057] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   22.264259] Brought up 1 CPUs
[   22.264359] Booting paravirtualized kernel on bare hardware
[   22.264398] Time: 20:41:29  Date: 10/13/107
[   22.264417] NET: Registered protocol family 16
[   22.264482] EISA bus registered
[   22.264491] ACPI: bus type pci registered
[   22.269016] PCI: PCI BIOS revision 3.00 entry at 0xfa950, last bus=5
[   22.269018] PCI: Using configuration type 1
[   22.269020] Setting up standard PCI resources
[   22.272764] ACPI: EC: Look up EC in DSDT
[   22.278418] ACPI: Interpreter enabled
[   22.278420] ACPI: (supports S0 S3 S4 S5)
[   22.278434] ACPI: Using IOAPIC for interrupt routing
[   22.287853] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.287858] PCI: Probing PCI hardware (bus 00)
[   22.288229] PCI: Transparent bridge - 0000:00:09.0
[   22.288472] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.288736] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   22.354199] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   22.354378] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.354556] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   22.354733] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.354910] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.355088] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   22.355264] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.355442] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   22.355620] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   22.355796] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.355974] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   22.356159] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   22.356336] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.356522] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   22.356710] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   22.356897] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.357093] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   22.357282] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   22.357470] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   22.357658] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   22.357785] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   22.357979] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   22.358173] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   22.358370] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   22.358563] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[   22.358756] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   22.358950] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   22.359143] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   22.359337] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   22.359537] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   22.359738] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   22.359938] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   22.360036] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.360044] pnp: PnP ACPI init
[   22.360054] ACPI: bus type pnp registered
[   22.365280] pnp: PnP ACPI: found 15 devices
[   22.365282] ACPI: ACPI bus type pnp unregistered
[   22.365285] PnPBIOS: Disabled by ACPI PNP
[   22.365326] PCI: Using ACPI for IRQ routing
[   22.365330] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.365354] PCI: Cannot allocate resource region 3 of device 0000:05:00.0
[   22.416079] NET: Registered protocol family 8
[   22.416081] NET: Registered protocol family 20
[   22.416132] pnp: 00:00: ioport range 0x4000-0x407f has been reserved
[   22.416135] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[   22.416138] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[   22.416140] pnp: 00:00: ioport range 0x4480-0x44ff has been reserved
[   22.416143] pnp: 00:00: ioport range 0x4800-0x487f has been reserved
[   22.416146] pnp: 00:00: ioport range 0x4880-0x48ff has been reserved
[   22.416157] pnp: 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
[   22.416161] pnp: 00:0e: iomem range 0xd1800-0xd3fff has been reserved
[   22.416164] pnp: 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
[   22.416167] pnp: 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
[   22.416170] pnp: 00:0e: iomem range 0xfc000-0xfffff could not be reserved
[   22.419973] Time: tsc clocksource has been installed.
[   22.446345] PCI: Bridge: 0000:00:09.0
[   22.446347]   IO window: a000-afff
[   22.446350]   MEM window: fe900000-fe9fffff
[   22.446353]   PREFETCH window: fea00000-feafffff
[   22.446356] PCI: Bridge: 0000:00:0b.0
[   22.446358]   IO window: 9000-9fff
[   22.446361]   MEM window: fe800000-fe8fffff
[   22.446363]   PREFETCH window: fe700000-fe7fffff
[   22.446366] PCI: Bridge: 0000:00:0c.0
[   22.446368]   IO window: 8000-8fff
[   22.446371]   MEM window: fe600000-fe6fffff
[   22.446373]   PREFETCH window: fe500000-fe5fffff
[   22.446376] PCI: Bridge: 0000:00:0d.0
[   22.446378]   IO window: 7000-7fff
[   22.446380]   MEM window: fe400000-fe4fffff
[   22.446383]   PREFETCH window: fe300000-fe3fffff
[   22.446390] PCI: Bridge: 0000:00:0e.0
[   22.446392]   IO window: 6000-6fff
[   22.446395]   MEM window: f4000000-fbffffff
[   22.446397]   PREFETCH window: d0000000-dfffffff
[   22.446404] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   22.446411] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   22.446416] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   22.446422] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   22.446427] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   22.446438] NET: Registered protocol family 2
[   22.483901] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.484006] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   22.485116] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   22.485507] TCP: Hash tables configured (established 131072 bind 65536)
[   22.485509] TCP reno registered
[   22.495965] checking if image is initramfs... it is
[   22.947108] Switched to high resolution mode on CPU 0
[   23.116601] Freeing initrd memory: 7055k freed
[   23.116917] audit: initializing netlink socket (disabled)
[   23.116928] audit(1194986489.120:1): initialized
[   23.116982] highmem bounce pool size: 64 pages
[   23.118417] VFS: Disk quotas dquot_6.5.1
[   23.118459] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.118534] io scheduler noop registered
[   23.118536] io scheduler anticipatory registered
[   23.118538] io scheduler deadline registered
[   23.118550] io scheduler cfq registered (default)
[   23.118578] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[   23.118585] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.118590] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[   23.118597] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.118602] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[   23.118609] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.118614] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[   23.118621] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.118628] Boot video device is 0000:05:00.0
[   23.118689] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   23.118706] assign_interrupt_mode Found MSI capability
[   23.118708] Allocate Port Service[0000:00:0b.0:pcie00]
[   23.118761] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   23.118777] assign_interrupt_mode Found MSI capability
[   23.118779] Allocate Port Service[0000:00:0c.0:pcie00]
[   23.118825] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   23.118841] assign_interrupt_mode Found MSI capability
[   23.118843] Allocate Port Service[0000:00:0d.0:pcie00]
[   23.118889] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   23.118904] assign_interrupt_mode Found MSI capability
[   23.118906] Allocate Port Service[0000:00:0e.0:pcie00]
[   23.118994] isapnp: Scanning for PnP cards...
[   23.470988] isapnp: No Plug & Play device found
[   23.489694] Real Time Clock Driver v1.12ac
[   23.489775] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.489854] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.489974] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   23.490374] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.490548] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   23.491069] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.491206] input: Macintosh mouse button emulation as /class/input/input0
[   23.491263] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   23.494381] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.494386] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.494520] mice: PS/2 mouse device common for all mice
[   23.494602] EISA: Probing bus 0 at eisa.0
[   23.494615] Cannot allocate resource for EISA slot 4
[   23.494620] Cannot allocate resource for EISA slot 6
[   23.494622] Cannot allocate resource for EISA slot 7
[   23.494624] Cannot allocate resource for EISA slot 8
[   23.494626] EISA: Detected 0 cards.
[   23.494704] TCP cubic registered
[   23.494715] NET: Registered protocol family 1
[   23.494733] Using IPI No-Shortcut mode
[   23.494881]   Magic number: 15:262:700
[   23.495220] Freeing unused kernel memory: 364k freed
[   23.538046] input: AT Translated Set 2 keyboard as /class/input/input1
[   24.740800] AppArmor: AppArmor initialized<5>audit(1194986490.620:2):  type=1505 info="AppArmor initialized" pid=1363
[   24.747067] fuse init (API version 7.8)
[   24.751737] Failure registering capabilities with primary security module.
[   24.755942] ACPI: Fan [FAN] (on)
[   24.760702] ACPI: Processor [CPU0] (supports 8 throttling states)
[   24.761842] ACPI: Thermal Zone [THRM] (39 C)
[   25.340841] usbcore: registered new interface driver usbfs
[   25.340862] usbcore: registered new interface driver hub
[   25.340881] usbcore: registered new device driver usb
[   25.341480] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   25.341833] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   25.341840] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[   25.341851] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   25.341854] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   25.341969] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   25.341983] ohci_hcd 0000:00:02.0: irq 16, io mem 0xfebff000
[   25.370519] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.370524] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.390946] SCSI subsystem initialized
[   25.395282] libata version 2.21 loaded.
[   25.402532] usb usb1: configuration #1 chosen from 1 choice
[   25.402556] hub 1-0:1.0: USB hub found
[   25.402565] hub 1-0:1.0: 10 ports detected
[   25.503070] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   25.503080] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 17
[   25.503089] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   25.503092] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   25.503119] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   25.503142] ehci_hcd 0000:00:02.1: debug port 1
[   25.503145] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   25.503154] ehci_hcd 0000:00:02.1: irq 17, io mem 0xfebfe000
[   25.503159] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.503218] usb usb2: configuration #1 chosen from 1 choice
[   25.503242] hub 2-0:1.0: USB hub found
[   25.503248] hub 2-0:1.0: 10 ports detected
[   25.527794] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   25.606568] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   25.606585] NFORCE-CK804: chipset revision 162
[   25.606587] NFORCE-CK804: not 100% native mode: will probe irqs later
[   25.606591] NFORCE-CK804: BIOS didn't set cable bits correctly. Enabling workaround.
[   25.606593] NFORCE-CK804: BIOS didn't set cable bits correctly. Enabling workaround.
[   25.606598] NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
[   25.606604]     ide0: BM-DMA at 0xe800-0xe807, BIOS settings: hda:DMA, hdb:DMA
[   25.606612]     ide1: BM-DMA at 0xe808-0xe80f, BIOS settings: hdc:DMA, hdd:DMA
[   25.606619] Probing IDE interface ide0...
[   25.666299] FDC 0 is a post-1991 82077
[   26.005748] hda: LITE-ON DVD SOHD-167T, ATAPI CD/DVD-ROM drive
[   26.285252] hdb: MAXTOR 6L080J4, ATA DISK drive
[   26.341478] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   26.356529] Probing IDE interface ide1...
[   27.091832] hdc: PIONEER DVD-RW DVR-111L, ATAPI CD/DVD-ROM drive
[   27.874456] hdd: HL-DT-ST DVDRAM GSA-4120B, ATAPI CD/DVD-ROM drive
[   27.931840] ide1 at 0x170-0x177,0x376 on irq 15
[   27.940988] sata_nv 0000:00:07.0: version 3.4
[   27.941381] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   27.941389] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 18
[   27.941394] sata_nv 0000:00:07.0: Using ADMA mode
[   27.941427] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   27.941517] scsi0 : sata_nv
[   27.941728] scsi1 : sata_nv
[   27.941881] ata1: SATA max UDMA/133 cmd 0xf883e480 ctl 0xf883e4a0 bmdma 0x0001d400 irq 18
[   27.941885] ata2: SATA max UDMA/133 cmd 0xf883e580 ctl 0xf883e5a0 bmdma 0x0001d408 irq 18
[   27.962711] hda: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[   27.962718] Uniform CD-ROM driver Revision: 3.20
[   27.963839] hdb: max request size: 128KiB
[   27.963980] hdb: 156355584 sectors (80054 MB) w/1819KiB Cache, CHS=65535/16/63, UDMA(133)
[   27.964149] hdb: cache flushes supported
[   27.964172]  hdb:<6>hdc: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2000kB Cache, UDMA(66)
[   27.971141]  hdb1 hdb2 hdb3 hdb4 <<6>hdd: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   27.991274]  hdb5 >
[   28.348066] Attempting manual resume
[   28.348069] swsusp: Resume From Partition 3:67
[   28.348071] PM: Checking swsusp image.
[   28.356989] PM: Resume from disk failed.
[   28.385862] kjournald starting.  Commit interval 5 seconds
[   28.385872] EXT3-fs: mounted filesystem with ordered data mode.
[   28.405485] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   28.421800] ata1.00: ATA-7: HDS724040KLSA80, KFAOAC6A, max UDMA/133
[   28.421804] ata1.00: 781422768 sectors, multi 16: LBA48 
[   28.445757] ata1.00: configured for UDMA/133
[   28.912567] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   28.920752] ata2.00: ATA-6: ST3120827AS, 3.42, max UDMA/133
[   28.920755] ata2.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   28.936708] ata2.00: configured for UDMA/133
[   28.936785] scsi 0:0:0:0: Direct-Access     ATA      HDS724040KLSA80  KFAO PQ: 0 ANSI: 5
[   28.936792] ata1: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   28.936872] scsi 1:0:0:0: Direct-Access     ATA      ST3120827AS      3.42 PQ: 0 ANSI: 5
[   28.936877] ata2: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   28.937302] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[   28.937310] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 19
[   28.937314] sata_nv 0000:00:08.0: Using ADMA mode
[   28.937348] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   28.937415] scsi2 : sata_nv
[   28.937446] scsi3 : sata_nv
[   28.937497] ata3: SATA max UDMA/133 cmd 0xf8850480 ctl 0xf88504a0 bmdma 0x0001c000 irq 19
[   28.937500] ata4: SATA max UDMA/133 cmd 0xf8850580 ctl 0xf88505a0 bmdma 0x0001c008 irq 19
[   29.247972] ata3: SATA link down (SStatus 0 SControl 300)
[   29.559424] ata4: SATA link down (SStatus 0 SControl 300)
[   29.559865] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   29.559869] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 16
[   29.559875] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   29.559881] forcedeth: using HIGHDMA
[   30.078983] eth0: forcedeth.c: subsystem: 0105b:0ca2 bound to 0000:00:0a.0
[   36.386302] NET: Registered protocol family 10
[   36.386379] lo: Disabled Privacy Extensions
[   37.493635] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   37.493660] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4d00
[   37.927546] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   37.927551] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 17
[   37.927568] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   38.248154] intel8x0_measure_ac97_clock: measured 54739 usecs
[   38.248158] intel8x0: clocking to 46919
[   38.336731] sd 0:0:0:0: [sda] 781422768 512-byte hardware sectors (400088 MB)
[   38.336743] sd 0:0:0:0: [sda] Write Protect is off
[   38.336746] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   38.336759] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.336807] sd 0:0:0:0: [sda] 781422768 512-byte hardware sectors (400088 MB)
[   38.336815] sd 0:0:0:0: [sda] Write Protect is off
[   38.336817] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   38.336829] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.336834]  sda: sda1 < sda5 >
[   38.610770] sd 0:0:0:0: [sda] Attached SCSI disk
[   38.610853] sd 1:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   38.610864] sd 1:0:0:0: [sdb] Write Protect is off
[   38.610866] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   38.610879] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.610916] sd 1:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   38.610924] sd 1:0:0:0: [sdb] Write Protect is off
[   38.610926] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   38.610938] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.610941]  sdb:<6>pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   38.626413] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   38.831161]  sdb1 sdb2 < sdb5 >
[   38.983033] sd 1:0:0:0: [sdb] Attached SCSI disk
[   39.108106] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   39.108136] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   39.186399] Linux agpgart interface v0.102 (c) Dave Jones
[   39.227931] nvidia: module license 'NVIDIA' taints kernel.
[   39.546710] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   39.546720] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 20
[   39.546728] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   39.546948] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   40.019783] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[   40.022875] parport_pc 00:0a: reported by Plug and Play ACPI
[   40.022920] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   40.024985] input: PC Speaker as /class/input/input3
[   40.944341] lp0: using parport0 (interrupt-driven).
[   40.991809] Adding 2931852k swap on /dev/hdb3.  Priority:-1 extents:1 across:2931852k
[   41.373075] EXT3 FS on hdb2, internal journal
[   41.927834] kjournald starting.  Commit interval 5 seconds
[   41.928073] EXT3 FS on hdb5, internal journal
[   41.928077] EXT3-fs: mounted filesystem with ordered data mode.
[   43.349586] No dock devices found.
[   43.424295] input: Power Button (FF) as /class/input/input4
[   43.428449] ACPI: Power Button (FF) [PWRF]
[   43.462571] input: Power Button (CM) as /class/input/input5
[   43.466687] ACPI: Power Button (CM) [PWRB]
[   43.847390] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
[   43.847421] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[   43.847424] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[   46.649385] eth0: no IPv6 routers present
[   54.981972] ppdev: user-space parallel port driver
[   65.157731] audit(1194982931.908:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=6751 profile="/usr/sbin/cupsd"
[   75.196486] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   75.196491] apm: overridden by ACPI.
[   75.384560] Failure registering capabilities with primary security module.
[   75.553991] Bluetooth: Core ver 2.11
[   75.554275] NET: Registered protocol family 31
[   75.554278] Bluetooth: HCI device and connection manager initialized
[   75.554281] Bluetooth: HCI socket layer initialized
[   75.565649] Bluetooth: L2CAP ver 2.8
[   75.565653] Bluetooth: L2CAP socket layer initialized
[   75.644059] Bluetooth: RFCOMM socket layer initialized
[   75.644349] Bluetooth: RFCOMM TTY layer initialized
[   75.644352] Bluetooth: RFCOMM ver 1.8
[   56.812000] Marking TSC unstable due to: cpufreq changes.
[   56.816000] Time: acpi_pm clocksource has been installed.
[   57.144000] Clocksource tsc unstable (delta = -148960904 ns)
alain@VAMPIRE666-ubuntu:~$ 

```
By the way when I select the uBuntu Op in the grub I notice a line error.....
"Cannot allocate resource region 3"....and something else, The error it's too fast and I can't read it. :-(

EDIT3: I'm sorry if I'm posting here what I already posted on a dedicated thread.

---

### Post by blackvd on 2007-11-18
In the same boat here. I feel like I didn't really notice this till after my last update at which point my system started running sluggish altogether. Curious about that app bootchart everyone is using. I couldn't find it in the repo so I d/led the package for it. After I installed it it never showed up in my menu. 

My system specs are:

Dell Inspiron 6400
Intel Duo Core 1.86
1 GB ram
nVidia GeForce Go 7300 256MB

---

### Post by Mitsuhashi on 2007-11-19
I don't know if this can help, but I noticed that the login time is long (about 1 minute and 30 seconds for me) only at the first login after a boot.
After a succesfully login, if I end my session and try to login again, it takes only 12 seconds...

---

### Post by vampire666eng on 2007-11-19
> **blackvd said:**
> [...]Curious about that app bootchart everyone is using. I couldn't find it in the repo so I d/led the package for it. After I installed it it never showed up in my menu. 
[...]Hi. To install the boot-chart:
```
sudo apt-get install bootchart
```
Then reboot and look in /var/log/bootchart. As far as I know there's no menu coming up. Once you finished with it remove it from the system (otherwise you'll be full of boot-charts taking up your disk space  as every time you reboot it will create one).

---

### Post by mskadu on 2007-11-19
Hi,

This is a  brand new install of v7.10 running on a Intel Mobile Pentium 4 with 1 Gig RAM and ATI Radeon 9200. I am able to see the login screen. However, when I get login screen I end up with the brown desktop. No menu, nothing. No disk activity either. I do hear the startup sound. And my mouse is movable till the very end. Oh, and yes - my CPU fan starts going crazy after a while (dunno if thats related)

Having done through the previous pages of this post (phew!), I have now done the following:

1. Tried changing the /etc/hosts (nope)
2.  Tried removing the sessions (nope)
3. apt-get "removed" compiz-core and tracker (just in case) .. but (nope)
4. Tried running the Gnome safe session. Still no change.


So, am I facing the same problem as you guys (since I don't get a working desktop at the end) or something completely different??

I can't post dmesg/ .xsession-errors/ etc since I cant get into the desktop.

Any suggestions on what I try next?:confused:

I've already added my comments to the launchpad bugs mentioned before.

---

### Post by janko on 2007-11-19
> **Mitsuhashi said:**
> I don't know if this can help, but I noticed that the login time is long (about 1 minute and 30 seconds for me) only at the first login after a boot.
After a successful login, if I end my session and try to login again, it takes only 12 seconds...
I'm also quite sure that the problem that is not involved in video card issues it's a GNOME problem, if I do the first login in Xfce it loads the desktop fast. Then i try GNOME and it takes about a minute. And If I retry a second login in GNOME is fast... my conclusion is: it's not generally the second time i login that its fast, it's only the second time in GNOME that is fast, so the problem is likely to be Gnome.
Jan

---

### Post by mikawber on 2007-11-19
> **janko said:**
> I'm also quite sure that the problem that is not involved in video card issues it's a GNOME problem, if I do the first login in Xfce it loads the desktop fast. Then i try GNOME and it takes about a minute. And If I retry a second login in GNOME is fast... my conclusion is: it's not generally the second time i login that its fast, it's only the second time in GNOME that is fast, so the problem is likely to be Gnome.
Jan

I noticed too that after my first login, any login after that loads up extremely fast. 

I don't know if this is related to the same issue but after doing a new install of Gutsy on my desktop, the session freezes for about 20 seconds after I click the shutdown button. Anybody know the reason for this? Thanks

---

### Post by Arthur Archnix on 2007-11-20
I'm no longer having the problem, so I can't help out on this thread. I can tell you that I've removed compiz completely. Ubuntu/Gnome have done something to their startup with 2.2 I think. If you read this [thread]("http://gnomesupport.org/forums/viewtopic.php?t=2366") you'll note that at least four files have their fingers in the start-up pile. Perhaps if this could be streamlined as per the comments in the thread.

---

### Post by daniel_victoria on 2007-11-24
This tread has been going on for ages and still no answer. Has anybody been able to fix this? Any clues as to what is going on?

---

### Post by LinuxGuy1234 on 2007-11-24
Ahem...
```
sudo apt-get remove gdm xdm+
```

---

### Post by boast on 2007-11-24
> **daniel_victoria said:**
> This tread has been going on for ages and still no answer. Has anybody been able to fix this? Any clues as to what is going on?

Confirmed with low priority :confused::(

[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544)

---

### Post by shane2peru on 2007-11-24
I too am having this problem.  Very annoying, it is very much like Windows and the slowness it takes for their desktop to load.  Maybe some Windows code leaked into Linux. :lolflag:

Shane

---

### Post by MR.UNOWEN on 2007-11-24
I'm having the same issue. I tried removing the bluetooth manager as some have recommended, but the problem is still there. Also when the login screen loads, it loads in a blocky way. Starts out as an orange screen, then block by block the login screen shows up. My system should be able load it with no issue, desktop effects work without an issue?

---

### Post by skymera on 2007-11-24
> **LinuxGuy1234 said:**
> Ahem...
```
sudo apt-get remove gdm xdm+
```

whats up with that?

i just read every signle post and nothing, no answers.

hmm

---

### Post by rainwalker on 2007-11-24
I don't know if someone has already said this, but I read something in the past posts about a brief flickering appearance of the panels after logging in and I think that has to do with Compiz Fusion starting up. Before Gutsy, my panels/window borders/etc. would disappear when enabling visual effects, so I think that's what's causing it.
Therefore, I don't think the slow loading after logging in has to do with Compiz Fusion. I think that the desktop has already loaded, but then Compiz Fusion is immediately started, which makes it seem like the desktop is still loading when really it's just Compiz Fusion starting up.

---

### Post by MR.UNOWEN on 2007-11-25
sudo apt-get remove gdm xdm+

What does that do....  ?
I never jump to any sudo commands before I know what I'm doing and that command looks questionable. Can someone tell me what the hell that does?

---

### Post by rainwalker on 2007-11-25
> **MR.UNOWEN said:**
> sudo apt-get remove gdm xdm+

What does that do....  ?
I never jump to any sudo commands before I know what I'm doing and that command looks questionable. Can someone tell me what the hell that does?

All I can tell is that is will uninstall GDM (the login screen) and XDM (X display manager). I don't have XDM installed, but I don't see how uninstalling GDM would help in any way...

---

### Post by mrming on 2007-11-25
Just wanted to say that I also have this problem on AMD 64 with Nvidia graphics (on board). Disabling compiz fixes it for me (System > Preferences > Desktop Effects). While I like swishy desktop effects as much as the next man, life's too short for this kind of caper.

---

### Post by vampire666eng on 2007-11-25
> **boast said:**
> Confirmed with low priority :confused::(

[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544)
Heh, that's not good, but I guess that our favorite coders have other things on their schedule to fix before this.

---

### Post by frodon on 2007-11-25
Many of the problems listed in this thread are completely different, so this bug report is almost unusable because most of the comments are not accurate.
This is why this bug report won't get fixed IMO, all the different problems need to be reported separately with details and log files to have a chance to get fixed. As long as this is not done there's IMO no chance to see this moving before the next release.

---

### Post by vampire666eng on 2007-11-25
Ouch, next release....but that makes sense. :)

So you would suggest us to all report the problems we are encountering opening a ticket in the link below?
[https://bugs.launchpad.net/~ubuntu-bugs/](https://bugs.launchpad.net/~ubuntu-bugs/)

---

### Post by allstar1971 on 2007-11-25
I too, have the slow desktop boot problem. It is frustrating. I noticed a while ago, someone had made a script that you could use to replace the one on your computer. (Can't remember what it was and didn't back it up, although I thought I did), after replacing the file, I no longer had the slow boot to desktop problem.

This issue needs fixed soon. It appears a lot of people have the same problem.

---

### Post by boast on 2007-11-25
> **frodon said:**
> Many of the problems listed in this thread are completely different, so this bug report is almost unusable because most of the comments are not accurate.
This is why this bug report won't get fixed IMO, all the different problems need to be reported separately with details and log files to have a chance to get fixed. As long as this is not done there's IMO no chance to see this moving before the next release.

checking the ubuntu mailiing lists, 
[COLOR="DarkOrange"]
i discovered many others to be having problems with the
ubuntu package of compiz.  i think the wrapper script 'compiz' is
sending the wrong params to 'compiz.real'.  i had no problems whatsoever
when using metacity, with the exception of the logout bug, but that is
independent of the window manager.  all bootcharts showed the same boot
times for both metacity and compiz (compiz a few sec longer for obvious
reasons).  basically, all my apps were loading and my desktop was
"there", i just couldnt see it until something 'snapped' it back, about
the time it was completely loaded.  the reason the gnome-panels showed
for a brief period was because the window manager (compiz.real) had not
yet been started.  notice on that bootchart above, compiz.real starts
less than 2 seconds after gnome-panel.  i think this may be the problem
for everyones 'slow startup'.  its not really slow, compiz.real is being
mis configured by the wrapper script (compiz) or something along that
line, and the gui environment is temporarily killed when compiz.real is
actualy initiated.[/COLOR]

---

### Post by frodon on 2007-11-25
> **vampire666eng said:**
> Ouch, next release....but that makes sense. :)

So you would suggest us to all report the problems we are encountering opening a ticket in the link below?
[https://bugs.launchpad.net/~ubuntu-bugs/](https://bugs.launchpad.net/~ubuntu-bugs/)Opening a bug report for each specific problem (if one is not already opened yet) which have as concequence long login time would help for sure but obviously that suppose to investigate a little bit to find the exact cause of your long login time.

---

### Post by rainwalker on 2007-11-25
> **boast said:**
> checking the ubuntu mailiing lists, 

i discovered many others to be having problems with the
ubuntu package of compiz.  i think the wrapper script 'compiz' is
sending the wrong params to 'compiz.real'.  i had no problems whatsoever
when using metacity, with the exception of the logout bug, but that is
independent of the window manager.  all bootcharts showed the same boot
times for both metacity and compiz (compiz a few sec longer for obvious
reasons).  basically, all my apps were loading and my desktop was
"there", i just couldnt see it until something 'snapped' it back, about
the time it was completely loaded.  the reason the gnome-panels showed
for a brief period was because the window manager (compiz.real) had not
yet been started.  notice on that bootchart above, compiz.real starts
less than 2 seconds after gnome-panel.  i think this may be the problem
for everyones 'slow startup'.  its not really slow, compiz.real is being
mis configured by the wrapper script (compiz) or something along that
line, and the gui environment is temporarily killed when compiz.real is
actualy initiated.

Ah! That's what I'm talking about!

---

### Post by vampire666eng on 2007-11-25
> **frodon said:**
> Opening a bug report for each specific problem (if one is not already opened yet) which have as concequence long login time would help for sure but obviously that suppose to investigate a little bit to find the exact cause of your long login time.
Ok. Thanks for the clarification. :)

---

### Post by #Reistlehr- on 2007-11-25
Just for those who didn't read the rest of the thread and started posting:

Here is the main bug report:

[https://bugs.launchpad.net/ubuntu/+s...e2/+bug/151544](https://bugs.launchpad.net/ubuntu/+s...e2/+bug/151544)
And as frodon said, it's generically unusable, as multiple problems are causing the same results.

Nvidia Bug Report:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/160535](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/160535)

Someone should post a compiz bug report or find one in relation to this problem

Also, there is a session problem that results in this problem

Lastley, there is a IPv6/networking problem that results in these symptoms.

If anyone finds a bug report, please post it, and i will ammend it to this post.

---

### Post by shane2peru on 2007-11-25
> **rainwalker said:**
> All I can tell is that is will uninstall GDM (the login screen) and XDM (X display manager). I don't have XDM installed, but I don't see how uninstalling GDM would help in any way...

    Ok, this will remove XDM and GDM and leave you with a system without GUI if you don't have kde installed.  Not advisable.

> **#Reistlehr- said:**
> Just for those who didn't read the rest of the thread and started posting:

Here is the main bug report:

[https://bugs.launchpad.net/ubuntu/+s...e2/+bug/151544](https://bugs.launchpad.net/ubuntu/+s...e2/+bug/151544)
And as frodon said, it's generically unusable, as multiple problems are causing the same results.

Nvidia Bug Report:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/160535](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/160535)


That is funny because there really hasn't been any clear ways of troubleshooting it either.  I don't have compiz because my Intel graphics driver is Blacklisted.  It is not a network problem I have watched the boot up process.  So what exactly are the other problems that could be causing this?  I'm becoming less and less impressed with Gutsy.  It seems like it is riddled with little problems that are not major, but annoying.   (This has been only one of the minor problems I have had this time.)  I have been around since Breezy days.  Any more troubleshooting ideas would be appreciated.  I have installed Xfce desktop and am learning the ins and outs of that desktop.  

Shane

---

### Post by LinuxGuy1234 on 2007-11-25
> **rainwalker said:**
> All I can tell is that is will uninstall GDM (the login screen) and XDM (X display manager). I don't have XDM installed, but I don't see how uninstalling GDM would help in any way...

No, really it uninstalls gdm and installs xdm.

---

### Post by LinuxGuy1234 on 2007-11-25
> **shane2peru said:**
> Ok, this will remove XDM and GDM and leave you with a system without GUI if you don't have kde installed.  Not advisable.



That is funny because there really hasn't been any clear ways of troubleshooting it either.  I don't have compiz because my Intel graphics driver is Blacklisted.  It is not a network problem I have watched the boot up process.  So what exactly are the other problems that could be causing this?  I'm becoming less and less impressed with Gutsy.  It seems like it is riddled with little problems that are not major, but annoying.   (This has been only one of the minor problems I have had this time.)  I have been around since Breezy days.  Any more troubleshooting ideas would be appreciated.  I have installed Xfce desktop and am learning the ins and outs of that desktop.  

Shane

Oh, notice the + (which means install) at the end of xdm.
Plain XDM can do logins without fuss. Or just don't execute it.

---

### Post by rainwalker on 2007-11-25
> **LinuxGuy1234 said:**
> No, really it uninstalls gdm and installs xdm.

Oohhh, okay, I didn't know it would install it. 
Still, what's the point?

---

### Post by Arthur Archnix on 2007-11-25
My experience after four installs of Gutsy has been that removing Compiz and setting metacity as default window manager, as well as removing tracker, returned behaviour to feisty performance levels. On my last install however I setup an encrypted system using the alternate cd and notice slower times between login and desktop. I expect that the delay is caused by the extra time involved in decrypting the system the first time, though I'm clearly no expert on the matter.

Anyway, if you're running an encrypted system you should expect a general system wide performance hit for disk intensive tasks like loading the desktop the first time. Logging out and back in is not affected since (again, I'm guessing here) much of needed info is still loaded in ram.

/two cents.

---

### Post by IamAcoconut on 2007-11-26
> **Arthur Archnix said:**
> Anyway, if you're running an encrypted system you should expect a general system wide performance hit for disk intensive tasks like loading the desktop the first time. Logging out and back in is not affected since (again, I'm guessing here) much of needed info is still loaded in ram.

I'm using encrypted filesystem too. But I've been actually using it since edgy, and performance wasn't noticably affected until Gutsy, so I wouldn't associate the lag with encryption.

---

### Post by vampire666eng on 2007-11-26
******Possible FIX.****** (I got it fixed on my pc)

I had the same exact problem. 

Then I installed xamp for Linux (following the instructions on the page below):
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)
When I started xamp with the command "/opt/lampp/lampp start" I received an error saying that I had some problems in my "/etc/host" (or it was "/etc/host.conf" ---> I wasn't paying much attention 	:???:) and a message saying that it was trying to fix the problem.
After that all my system was responsive as it should be, and the long time to boot was considerately shortened.

I don't know how this was fixed (and I'm not even sure that the problem is based on/only on the "/ect/host"). I leave it to the uBuntu coders to figure it out. But is has something to do with etc/host and xamp was able to fix it.

Thanks for the attention.

Regards,
vampire666

******Possible FIX.******

---

### Post by skymera on 2007-11-26
i'll tyry that too :)

thnaks

---

### Post by vampire666eng on 2007-11-26
Cool.
I hope that this can help the community.

P.S. I sent a comment here: 
[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544)

---

### Post by anibalojeda on 2007-11-27
Just reporting the same issue here.

The GNOME desktop takes very long time to load during the system boot, i.e. the first time. Log out and login again is faster than light, though. Feisty is significantly faster at startup time.

This after a clean install.

---

### Post by vampire666eng on 2007-11-27
Has anyone tried "my fix"?

Maybe it helps others. :-)

---

### Post by Nonno Bassotto on 2007-11-27
Not yet, because in your post you are talking about the boot time, which is not the topic of the thread. Did you want to refer to the login time?

---

### Post by vampire666eng on 2007-11-27
Doh! Sorry about that.

The fix that worked for me is for the long boot after the log in (wierd behaviour on the desktop, system not responsive, long boot time).
I don't know if this effect also the login problem, but they might be connected. I don't know. Sorry.

The problem I experienced and solved was this:
[http://ubuntuforums.org/showthread.php?t=581644](http://ubuntuforums.org/showthread.php?t=581644)

---

### Post by frodon on 2007-11-27
Just for those who don't read the whole thread, we are repeating the same thing over and over :
[http://ubuntuforums.org/showpost.php?p=3676658&postcount=115](http://ubuntuforums.org/showpost.php?p=3676658&postcount=115)

First thing to do if you issue this is to fix your /etc/host if needed and disable compiz to see if it is the problem.

@#Reistlehr-, would you be interested to write together a thread which summurize the different things to try first before posting for those who have this problem and which would clear some misunderstanding (for example between boot time issues and login time issues) ?
I think it would be useful since users don't read threads although they already contains most of the answers

Everyone with this problem please read or perform a search in this thread before posting, some solutions have already been proposed depending of the cause of your long login time.

---

### Post by bsulzen on 2007-11-27
If I do a fresh install of Gutsy the long login time presents itself. To correct the problem, I did a fresh install of Feisty, updated all available patches, and then updated the system to Gutsy using the Update Manager in Feisty.

Yes, it takes a long time! I have used this method a few times and it has worked everytime.

---

### Post by anibalojeda on 2007-11-27
> **bsulzen said:**
> If I do a fresh install of Gutsy the long login time presents itself. To correct the problem, I did a fresh install of Feisty, updated all available patches, and then updated the system to Gutsy using the Update Manager in Feisty.

Yes, it takes a long time! I have used this method a few times and it has worked everytime.


This thing is buggy guys.. sorry.

This is the price of being for free ;-)

Ubuntu 7.10 have some small minors bug after default install. They are kind of annoying..

I think this login problem is hardware related. When i install it on my PC at home i got the same issues as mentioned on this topic. Take long to log in..

Installing the same CD at work & everything works perfect. Is the choice of looking for hours for a solutions of wasting some extra seconds of your life ;-) anyway after the first log in, if you log out you can login fast again.. is only related to the first time after boot.

Im going to choose to live with it.. i really don't have the time to investigate this problem, sending logs & checking this forum for a fix. I just want my computer for daily use

---

### Post by boast on 2007-11-27
[http://live.gnome.org/GnomePerformance/LoginTime](http://live.gnome.org/GnomePerformance/LoginTime)

---

### Post by sweetsinse on 2007-11-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/128803](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/128803) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				hi all. *glad* to see this is slightly irritating to others as well, especially after the speed/success of feisty...

> ...i discovered many others to be having problems with the
ubuntu package of compiz. i think the wrapper script 'compiz' is
sending the wrong params to 'compiz.real'. i had no problems whatsoever
when using metacity, with the exception of the logout bug, but that is
independent of the window manager. all bootcharts showed the same boot
times for both metacity and compiz (compiz a few sec longer for obvious
reasons). basically, all my apps were loading and my desktop was
"there", i just couldnt see it until something 'snapped' it back, about
the time it was completely loaded. the reason the gnome-panels showed
for a brief period was because the window manager (compiz.real) had not
yet been started. notice on that bootchart above, compiz.real starts
less than 2 seconds after gnome-panel. i think this may be the problem
for everyones 'slow startup'. its not really slow, compiz.real is being
mis configured by the wrapper script (compiz) or something along that
line, and the gui environment is temporarily killed when compiz.real is
actualy initiated...

haha well i wrote that there 'quote' on the launchpad website :p, damn i love the internet and its ability to sPrEaD & RiPpLe... government should be modeled after both the internet and open source software, but i digress...

first, i will mention that i have since reinstalled gutsy on my thinkpad t43 (intel integrated graphics) and am no longer seeing the 'flickering' gnome-panels with compiz, although login times have still not decreased at all with a virgin install.  still no problems when using metacity, although all around login times are a serious regression from fasty fiery fleety feisty :).. i was using compiz-fusion on feisty with no problems (trevino), and have also read that people compiling compiz-fusion on gutsy and using the included 'make-fusion' script are not having any problems either.

also, when looking at the 'compiz' wrapper script, it tries to point to '/usr/local/bin' and '/usr/local/lib/compiz'.  neither exist on a virgin gutsy install.  real locations are the same minus the 'local' folder... i.e. '/usr/bin' and '/usr/lib/compiz'---unfortunately changing this seems to have no effect...

other things i have tried:
verifying /etc/host configuration before GDM login via tty
echoing 'nameserver 0.0.0.0' to resolv.conf via rc.local to avoid problematic nameservers while roaming
bareboneing all session apps down to gnome-power-manager alone (to avoid logout bug{freeze})
creating a new user to test any profile settings issues
killing ipv6 altogether via /etc/modprobe.d/aliases (change 'ipv6' to 'off')

nothing has alleviated the *real* issue (compared to feisty)...whatever it may be

here are the bootcharts i was referring to in my 'quote':
metacity:
[http://sweetsinsemilla.googlepages.com/metacity-pwrMAN-quick_and_nofreeze.png](http://sweetsinsemilla.googlepages.com/metacity-pwrMAN-quick_and_nofreeze.png)
[http://sweetsinsemilla.googlepages.com/metacity-noapps-quick_but_freeze.png](http://sweetsinsemilla.googlepages.com/metacity-noapps-quick_but_freeze.png)
**[http://sweetsinsemilla.googlepages.com/gutsy-20071115-2.png](http://sweetsinsemilla.googlepages.com/gutsy-20071115-2.png)
compiz:
[http://sweetsinsemilla.googlepages.com/compizdefault_plugins-pwrMAN-slow_an.png](http://sweetsinsemilla.googlepages.com/compizdefault_plugins-pwrMAN-slow_an.png)
[http://sweetsinsemilla.googlepages.com/compizdbus-workarounds-pwrMAN-slow_a.png](http://sweetsinsemilla.googlepages.com/compizdbus-workarounds-pwrMAN-slow_a.png)
**[http://sweetsinsemilla.googlepages.com/gutsy-20071115-7.png](http://sweetsinsemilla.googlepages.com/gutsy-20071115-7.png)

now some background on these charts--basically, i ran the bootchart app longer by removing its 'kill' script from init.d and making a link on my desktop to run it instead.  so all i had to do was click the link, enter my sudo password, and the bootchart would end at that moment.  the interesting thing to note is the time between x-session-manager (login) and gnome-terminal (when i saw the desktop link and actually clicked it).  look at the **'ed links above for both metacity and compiz.  i had to wait about 3-5 seconds longer for compiz to activate the link... but thats not even the weird part.  with metacity, gnome panels loaded within 3-5 seconds after login and STAYED VISIBLE the entire time, until i could see/launch the link.  compiz 'flickered' some panels, then went back to beige for 15+ seconds (connecting to a wireless network and EVERYTHING) before becoming visible.  with compiz, i saw nothing until i saw everything (all apps fully loaded).  with metacity, i could watch everything (icons/background/etc.) actually load up individually.

if you are seeing HD activity during this 'blank' time, my guess is you are experiencing something similar to me.  if you do not see any HD activity, you may have another issue (i.e. network) as your computer seems to be timing out at some point during login vs still loading apps.  some of our problem seems to be attributed to simply not being able to 'see' our desktop while it loads vs. the login actually being 'slow'. although, in all cases, my logins are far less than a minute so anyone in the 1-2 min range may be having more serious problems.

additionally, i do not experience these 'flickering' issues or any weirdness whatsoever with the gutsy livecd, and the applets/desktop icons/background seem to load in a different order.  not sure why everything is kosher on the cd but not after install..is something universally wrong with the install script??..

my next attempt will be what someone else has mentioned in this thread.. install virgin feisty with all updates, then upgrade to gutsy and see what happens.. somewhat redundant but oh well i dont know what else to do.  good luck; will return with results.

peace

launchpad:
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/128803](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/128803)
[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544)

---

### Post by daniel_victoria on 2007-11-28
> **frodon said:**
> 

First thing to do if you issue this is to fix your /etc/host if needed and disable compiz to see if it is the problem.


My /etc/hosts is correct so I'd like to try disabling compiz. How do I do that? It's not just removing the desktop effects is it? I have to replace it with metacity right?

---

### Post by frodon on 2007-11-28
This should do it :
[https://help.ubuntu.com/7.10/desktop-effects/C/compiz-configure.html](https://help.ubuntu.com/7.10/desktop-effects/C/compiz-configure.html)

---

### Post by meastp on 2007-11-30
Disabling Compiz solved the long login for me. Still a bug, though.

---

### Post by frankzen on 2007-12-06
Well I guess everybody went away :) 
I never used to have this bug, but it developed today...right after I ran profile on the kernel command line. Is that a clue? Dunno.

I have to wait 60 to 90 seconds looking at a crappy background before the desktop loads. But then it loads quickly :)

I disabled Compiz (didn't work with my card anyway), renamed the hidden gnome directories in home, reinstalled parts of the desktop and gdm, and swore a lot.

Still got the long delay.

---

### Post by boast on 2007-12-07
> **frankzen said:**
> Well I guess everybody went away :) 
I never used to have this bug, but it developed today....

it randomly happened to me..


welcome to the club :popcorn:

---

### Post by mahousaru on 2007-12-07
Just had it happen to me again on my EeePC.  First time I installed it no problems, I had to use the original Xandros so I restored it and when I reinstalled Gutsy with the same procedure as before I got the super long delay after the splash finished and I got a delay after logging in. It also had random 100 cpu spurts every so often.  I found it was the ttf-opensymbol bug causing it.  

yct's post crediting to PaulFr fixed it for me.

> 
touch /tmp/current_time
sudo find /usr/share/fonts /usr/share/X11/fonts /var/lib/defoma/fontconfig.d ~/.fonts ~/.fontconfig /usr/local/share/fonts -newer /tmp/current_time -exec touch {} \;
sudo dpkg --configure --pending


[https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/136769](https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/136769)

---

### Post by Karnidon on 2007-12-09
This only showed up after a clean install, then the 4 compiz updates that Update Manager recommended last week.  remove & reinstall compiz = no improvement.  A bug in the updates?

The fix for me was the /etc/hosts edit.

--freezing login--
127.0.0.1 localhost
127.0.1.1 <hostname>
-- --

--quick login--
127.0.0.1 localhost <hostname>


-- --
not sure what wrote the first hostfile - don't know what 127.0.1.1 was intended for 

Good look.  Looking forward to more stability and productivity than the Vista pita on this machine.

 :cl

---

### Post by frankzen on 2007-12-09
Mine just fixed itself a day or two ago. A bunch of Kernel modules came in in an update and the system started working normally after a reboot. Still don't know what fixed it  but I am assuming it was one of the modules. I had done everything I could think of and nothing worked. My problems started when I tried a suggestion I found somewhere here in the forums to re-profile my system bu putting profile on the kernel command line. After that it went real wonky.



Good luck to everyone here.

---

### Post by canoemoose on 2007-12-14
Hmm.  I had this problem since Feisty days.  I updated my /etc/hosts file and this has drastically improved my login times.  Times are 25 seconds from reboot, 14 seconds if previouly logged on.  Not too bad, but does the difference between logged on/rebooted times indicate I also have the profiles problem??  All users on my machine are the same.
<tangent>
Just gotta sort out boot times now, but this is covered elsewhere.  My Ubuntu box is currently outstripped by an XP box...:twisted:...but the XP box has much better specs.
</tangent>
I would like the log on times to be more like the times for a 6.06 install on an old laptop I have kicking about somewhere.  From memory this was more or less instant but as I have b*gg*r*d the hard drive I cant find out...but that's another story!:lolflag:

---

### Post by HeWhoE on 2007-12-20
The resolution in my /etc/usplash.conf file matches my screen resolution, 1280x800.  It must be something else.

---

### Post by frankzen on 2007-12-20
> **HeWhoE said:**
> The resolution in my /etc/usplash.conf file matches my screen resolution, 1280x800.  It must be something else.


In my reading of the net...there are dozens of reasons Gutsy will do this. It's a very buggy version of Ubuntu. And the devs have been silent on this and some other bugs . Sorry I can't help.

---

### Post by dseybert on 2007-12-22
So is there no fix for this issue yet?

---

### Post by frodon on 2007-12-22
Yes depending of the root cause of you long login time.

---

### Post by dseybert on 2007-12-22
How can I determine my root cause?

---

### Post by frodon on 2007-12-22
Reading the posts of this thread, most of the possible cause are detailed as well as the way to find them.

---

### Post by rainwalker on 2007-12-22
> **frodon said:**
> Reading the posts of this thread, most of the possible cause are detailed as well as the way to find them.

Oh my...26 pages of posts?

---

### Post by dseybert on 2007-12-22
> **rainwalker said:**
> Oh my...26 pages of posts?

That's kind of what I was thinking. I started reading them and got through the first 9 pages and gave up. I'm still a noob and got a bit confused at what some of the suggestions were. I was hoping someone could summarize it for me or give me a systematic approach to follow based on what was found.  I guess that's asking too much.

---

### Post by frodon on 2007-12-22
You are somewhat asking someone to do the effort you don't want to do so i guess you won't have many answers.
It's a bit like saying, "there's too much pages to read, could you read them and summarize them for me so i don't spend time on this".

I'm scared that you will have no other choice than reading some pages and providing some details to get your issue fixed.
You shouldn't expect any problem to be solved if you don't want to spend time on it, if you want some help the minimum is to read a little bit on the topic and provide details like :

your version of ubuntu, what you tweaked, do you use compiz or metacity, wifi or wired network, scripts added to session startup, ...

---

### Post by rainwalker on 2007-12-22
> **frodon said:**
> You are somewhat asking someone to do the effort you don't want to do so i guess you won't have many answers.
It's a bit like saying, "there's too much pages to read, could you read them and summarize them for me so i don't spend time on this".

I'm scared that you will have no other choice that reading some pages and providing some details to get your issue fixed.
You shouldn't expect any problem to be solved if you don't want to spend time on it, if you want some help the minimum is to read a little bit on the topic and provide details like :

your version of ubuntu, what you tweaked, do you use compiz or metacity, wifi or wired network, scripts added to session startup, ...

I actually have read them, but it is a lot for someone who may not want (or be able to) devote the time to read it all.
I agree with what you're saying, though.

---

### Post by frodon on 2007-12-22
dseybert, start from here :
[http://ubuntuforums.org/showthread.php?t=585635&page=14](http://ubuntuforums.org/showthread.php?t=585635&page=14)

And investigate a little bit considering what you have installed.

---

### Post by dseybert on 2007-12-22
Ok, I'm running a Sony Vaio with an ATI Mobility Radeon 9200 graphics card and have the long login problem. I checked the screen resolution in /etc/usplash.conf, but this did not correct the problem. I completely removed Compiz from my system and  it seems to have fixed the problem. I then re-installed Compiz, keeping Metacity as default. Again a quick login. I re-enabled Compiz and back to the slow login. The menu bar at the bottom pops up for a second with the black background (changed via page 14), then disappears for about 20-30 seconds before coming back with the rest of the desktop.

Should I try the xamp thing mentioned back on page 24?

---

### Post by frodon on 2007-12-23
The bottom menu bar problem is a known compiz issue (surely solved in latest version) so i think that there's nothing to do for this except installing the latest compiz version.
The slow login due to compiz enabled is a problem that many users have unfortunately. Compiz is still in active development and this is a perfect example of annoying bugs present in this version of compiz.

To summarize i think that you have 2 choices :
1- use metacity which is bug free at this level
2- update your compiz to the latest version (can be painful to upgrade to next ubuntu version if you do this).

---

### Post by ghostlines on 2007-12-25
Just wanted to say that i was experiencing this same problem. It started to occur after i was having trouble getting the latest tracker 0.64 to work properly.  I then tried to open nautilus from the terminal and i got this error ->> 

error while loading shared libraries: libtrackerclient.so.0: cannot open shared object file: No such file or directory

i then reinstalled tracker even though it still doesn't work, but the symlink is there so ubuntu now boots like normal. Not sure if this helped anyone but just incase i still shared it.

---

### Post by antiemptyv on 2007-12-26
i am currently having this issue.  i'm not sure if it matter, but it only takes the extra long time the first time i login.  when i ctrl+alt+bksp out of x and login again, it's quite speedy.

---

### Post by Nimaran on 2008-01-03
I've been suffering form this bug for a while and someone was talking a while ago about something with the network and loop backs, what was that and could that improve loading time?

Also, people of great knowledge out there, do you think this bug will be fixed by the next release of Ubuntu?

Mine seemed to speed up when I disabled compiz is that a bug that compiz slowed it down, or is it just a sacrifice (which I won't make) that one has for having the effects enabled?

---

### Post by rainwalker on 2008-01-03
> **Nimaran said:**
> Also, people of great knowledge out there, do you think this bug will be fixed by the next release of Ubuntu?

I'm almost positive it will, especially because the next release is going to be an LTS (long-term support) one.

---

### Post by #Reistlehr- on 2008-01-07
I've been skimming through the forums every now and then to see if anyone has ever isolated the problem slightly better than i did, and it seems that you are all at the same spot. I've been working on a fix for my nvidia issue. It seems that reverting to an older driver and changing a few configs around fixed the problem for me. I was happy to finally be able to use compiz, gutsy, and not have to wait an hour to load up </exageration>. Unfortunatly, i can't help solve the other problems as i am not experiencing them, and don't have the hardware configuration to re-create the problem.

But a Summary of this thread for those who, don't want to read the 28 pages :-D (cause im a nice guy and people might stop posting the same questions over and over)

**How To Isolate Your Problem**
NOTE: Before you start, disable Compiz, if enabled.
     Does the problem exist before you login to Ubuntu (Enter your username and password?)
          A: Yes - Check your usplash.conf file and fix the resolution.
          B: No - Continue reading

     Do you have an nVidia based chipset/graphics card?
          A: Yes - If you experience this problem with nvidia's drivers installed, and compiz disabled, continue reading. If enableing 3rd party programs causes this issue to become affected, continue reading. 
          B: No - Continue reading.

     Do you have a Radeon video card/chipset?
          A: Yes - Make sure to run the newest drivers which fixes numerous bugs
          B: No - Continue reading.

     Install the gnome-splash-manager package. Restart Linux. (Google for more info if you need). AFter you install the gnome-splash-manager, which is the utility that will launch a KDE type of splash to tell you what gnome is currently loading. Pay attention to it, if it appears (if done correctly, and youare expiriencing only part of the problem.) Can you read/ see the icon for the utility that was last loaded before the problem occured?
          A: Yes - This means you are problably expiriencing a problem with the session manager. Last time i checked, there was a few bugs beeing worked out with the last release.
          B: No - Continue reading.

     If you have answered yes to any of these, and you attempted to fix them, and were successful, enable compiz.
     If you you were experiencing a problem, and couldnt fix it, enable compiz, because compiz is not the problem.
     
     Does your router support IPv6?
          A: Yes - COntinue.
          B: No - Google or search the forums on how to disbale ipv6 in ubuntu. (It requires editing files.)

     If you reached here, and the problem still exists, with or without compiz enabled, then you might be experiencing network issues. Try fixing the loopback, and your hosts file (if i remember, it miss lables your hostname which can cause a hang.) I cant help support past this, since i cant recreate the problem.

A file to keep an eye on is, ~/.xsession-errors 

Happy new year (belated).

---

### Post by #Reistlehr- on 2008-01-07
The motherboard on 2 of my HP Laptops went from a power surge, (moral of the story is to make sure you replace your surge protectors once every 6 months, thank god i have my UPS on my 2 servers though). 

So, when i receive the updated replacement, which should have newer hardware, i will reinstall, and see what new problems i can re-create.

---

### Post by pototo on 2008-01-08
> **#Reistlehr- said:**
> 
     Install the gnome-splash-manager package. Restart Linux. (Google for more info if you need). AFter you install the gnome-splash-manager, which is the utility that will launch a KDE type of splash to tell you what gnome is currently loading. Pay attention to it, if it appears (if done correctly, and youare expiriencing only part of the problem.) Can you read/ see the icon for the utility that was last loaded before the problem occured?
          A: Yes - This means you are problably expiriencing a problem with the session manager. Last time i checked, there was a few bugs beeing worked out with the last release.
          B: No - Continue reading.


I've tried this, and I've found that the splash screen is stuck (40 segs aprox.) with "gnome-volume-manager". So I've removed it from the session manager. But next time I boot this message is still there, so I've removed it using "sudo apt-get remove --purge gnome-volume-manager", but once again, the message is still there.

---

### Post by #Reistlehr- on 2008-01-09
> **pototo said:**
> I've tried this, and I've found that the splash screen is stuck (40 segs aprox.) with "gnome-volume-manager". So I've removed it from the session manager. But next time I boot this message is still there, so I've removed it using "sudo apt-get remove --purge gnome-volume-manager", but once again, the message is still there.

Do you have any NTFS partitions on your drive?

Also, an idea would be to comment out lines for the non-root partitions in /etc/fstab

---

### Post by pototo on 2008-01-09
> **#Reistlehr- said:**
> Do you have any NTFS partitions on your drive?

Yes, I have an NTFS partition.

> **#Reistlehr- said:**
>  Also, an idea would be to comment out lines for the non-root partitions in /etc/fstab

Tried this. Now the splash is stuck in the first icon (windows manager), and the booting time is the same as it was.:(

---

### Post by misfitpierce on 2008-01-09
Alot of ppl noticed slow down in 7.10. Mine is not slow and is about same as 7.04 but 8.04 is supposed to streamline it and cache startup to make startup even faster than 7.04 from what I hear. Should be nice. :)

---

### Post by oioi on 2008-01-10
I had just done a fresh install of Gutsy on my laptop (Asus A3G, Intel Pentium), and encountered the same problem. 

But it was not the login screen that took a long time; after starting up, it took me > 3 mins to reach the login screen. Once I typed in my user name and password, the Gnome desktop quickly showed. 

Trying "Ctrl-Alt-F1" during start-up each time did help, but a permanent solution finally came up after searching. 
Firstly I edited the file /etc/usplash.conf and changed the resolution to xres=1024, yres=768 (was xres=1280, yres=1024).
Then update the usplash theme:
"sudo update-usplash-theme usplash-theme-ubuntu"

The boot time came down to < 1min after that. Neat! :KS

Sorry I've forgot where I got the solution from! Please pardon the repetition if it has been described before!

---

### Post by #Reistlehr- on 2008-01-10
@pototo - can you post your dmesg output?

---

### Post by pototo on 2008-01-11
> **#Reistlehr- said:**
> @pototo - can you post your dmesg output?

Here it is:
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3900
[    0.000000] Entering add_active_range(0, 0, 524000) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524000
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524000
[    0.000000] On node 0 totalpages: 524000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292323 pages, LIFO batch:31
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7810 checksum 0
[    0.000000] ACPI: RSDP 000F7810, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 7FEE3040, 0030 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FEE3180, 6786 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FEE0000, 0040
[    0.000000] ACPI: MCFG 7FEE9A40, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FEE9980, 007C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
[    0.000000] Built 1 zonelists.  Total pages: 519907
[    0.000000] Kernel command line: root=UUID=b13acf28-9d7e-49e0-9eb7-a510b1438a67 ro quiet splash locale=es_ES elevator=cfq
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2640.251 MHz processor.
[   21.068418] spurious 8259A interrupt: IRQ7.
[   21.069569] Console: colour VGA+ 80x25
[   21.070126] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   21.070561] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   21.129428] Memory: 2066080k/2096000k available (2015k kernel code, 28772k reserved, 916k data, 364k init, 1178496k highmem)
[   21.129436] virtual kernel memory layout:
[   21.129437]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   21.129438]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   21.129439]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   21.129440]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   21.129441]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   21.129442]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   21.129443]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   21.129445] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   21.129480] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   21.209328] Calibrating delay using timer specific routine.. 5283.69 BogoMIPS (lpj=10567388)
[   21.209356] Security Framework v1.0.0 initialized
[   21.209364] SELinux:  Disabled at boot.
[   21.209375] Mount-cache hash table entries: 512
[   21.209504] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   21.209511] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.209513] CPU: L2 Cache: 512K (64 bytes/line)
[   21.209515] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   21.209524] Compat vDSO mapped to ffffe000.
[   21.209536] Checking 'hlt' instruction... OK.
[   21.225467] SMP alternatives: switching to UP code
[   21.225742] Freeing SMP alternatives: 11k freed
[   21.226000] Early unpacking initramfs... done
[   21.466328] ACPI: Core revision 20070126
[   21.466391] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.485819] CPU0: AMD Athlon(tm) 64 Processor 3500+ stepping 00
[   21.485832] Total of 1 processors activated (5283.69 BogoMIPS).
[   21.485955] ENABLING IO-APIC IRQs
[   21.486127] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   21.632466] Brought up 1 CPUs
[   21.632557] Booting paravirtualized kernel on bare hardware
[   21.632596] Time:  9:58:09  Date: 00/11/108
[   21.632614] NET: Registered protocol family 16
[   21.632674] EISA bus registered
[   21.632682] ACPI: bus type pci registered
[   21.636980] PCI: PCI BIOS revision 3.00 entry at 0xfa880, last bus=5
[   21.636981] PCI: Using configuration type 1
[   21.636983] Setting up standard PCI resources
[   21.639316] ACPI: EC: Look up EC in DSDT
[   21.643942] ACPI: Interpreter enabled
[   21.643944] ACPI: (supports S0 S1 S4 S5)
[   21.643954] ACPI: Using IOAPIC for interrupt routing
[   21.650562] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.650567] PCI: Probing PCI hardware (bus 00)
[   21.650870] PCI: Transparent bridge - 0000:00:09.0
[   21.651080] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.651281] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   21.696967] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 10 11) *0, disabled.
[   21.697106] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 10 11) *0, disabled.
[   21.697244] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 10 11)
[   21.697380] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 10 11) *0, disabled.
[   21.697516] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 10 11) *0, disabled.
[   21.697653] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 *5 7 10 11)
[   21.697794] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 10 11) *0, disabled.
[   21.697931] ACPI: PCI Interrupt Link [LMAC] (IRQs *3 4 5 7 10 11)
[   21.698071] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 *7 10 11)
[   21.698208] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 10 *11)
[   21.698344] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 *7 10 11)
[   21.698481] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 *10 11)
[   21.698617] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 10 11) *0, disabled.
[   21.698760] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 *10 11)
[   21.698905] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 10 *11)
[   21.699049] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 10 11) *0, disabled.
[   21.699200] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   21.699345] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   21.699489] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   21.699633] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   21.699732] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   21.699881] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   21.700029] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   21.700177] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   21.700328] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[   21.700477] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0
[   21.700625] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   21.700772] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   21.700920] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   21.701073] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   21.701226] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   21.701380] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   21.800189] ACPI: Power Resource [PFAN] (off)
[   21.800194] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.800202] pnp: PnP ACPI init
[   21.800207] ACPI: bus type pnp registered
[   21.803797] pnp: PnP ACPI: found 12 devices
[   21.803798] ACPI: ACPI bus type pnp unregistered
[   21.803801] PnPBIOS: Disabled by ACPI PNP
[   21.803841] PCI: Using ACPI for IRQ routing
[   21.803845] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.852805] NET: Registered protocol family 8
[   21.852807] NET: Registered protocol family 20
[   21.852852] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[   21.852854] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[   21.852856] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[   21.852858] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[   21.852860] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[   21.852862] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[   21.852869] pnp: 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
[   21.852872] pnp: 00:0b: iomem range 0xcc800-0xcffff has been reserved
[   21.852874] pnp: 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
[   21.852876] pnp: 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[   21.852878] pnp: 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[   21.855965] Time: tsc clocksource has been installed.
[   21.883004] PCI: Bridge: 0000:00:09.0
[   21.883005]   IO window: a000-afff
[   21.883008]   MEM window: fde00000-fdefffff
[   21.883010]   PREFETCH window: fdf00000-fdffffff
[   21.883012] PCI: Bridge: 0000:00:0b.0
[   21.883013]   IO window: 9000-9fff
[   21.883015]   MEM window: fdd00000-fddfffff
[   21.883017]   PREFETCH window: fdc00000-fdcfffff
[   21.883019] PCI: Bridge: 0000:00:0c.0
[   21.883020]   IO window: 8000-8fff
[   21.883022]   MEM window: fdb00000-fdbfffff
[   21.883024]   PREFETCH window: fda00000-fdafffff
[   21.883026] PCI: Bridge: 0000:00:0d.0
[   21.883028]   IO window: 7000-7fff
[   21.883030]   MEM window: fd900000-fd9fffff
[   21.883031]   PREFETCH window: fd800000-fd8fffff
[   21.883035] PCI: Bridge: 0000:00:0e.0
[   21.883037]   IO window: 6000-6fff
[   21.883039]   MEM window: f8000000-fbffffff
[   21.883041]   PREFETCH window: d0000000-dfffffff
[   21.883047] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   21.883053] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   21.883057] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   21.883061] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   21.883065] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   21.883076] NET: Registered protocol family 2
[   21.919878] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   21.920041] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   21.921679] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   21.922201] TCP: Hash tables configured (established 131072 bind 65536)
[   21.922203] TCP reno registered
[   21.931914] checking if image is initramfs... it is
[   22.382858] Switched to high resolution mode on CPU 0
[   22.402642] Freeing initrd memory: 7691k freed
[   22.402973] audit: initializing netlink socket (disabled)
[   22.402986] audit(1200045489.112:1): initialized
[   22.403040] highmem bounce pool size: 64 pages
[   22.404153] VFS: Disk quotas dquot_6.5.1
[   22.404189] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.404261] io scheduler noop registered
[   22.404263] io scheduler anticipatory registered
[   22.404264] io scheduler deadline registered
[   22.404274] io scheduler cfq registered (default)
[   22.418717] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[   22.418723] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   22.418728] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[   22.418733] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   22.418738] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[   22.418743] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   22.418747] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[   22.418753] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   22.418758] Boot video device is 0000:05:00.0
[   22.418815] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   22.418829] assign_interrupt_mode Found MSI capability
[   22.418831] Allocate Port Service[0000:00:0b.0:pcie00]
[   22.418869] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   22.418882] assign_interrupt_mode Found MSI capability
[   22.418883] Allocate Port Service[0000:00:0c.0:pcie00]
[   22.418921] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   22.418934] assign_interrupt_mode Found MSI capability
[   22.418935] Allocate Port Service[0000:00:0d.0:pcie00]
[   22.418971] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   22.418984] assign_interrupt_mode Found MSI capability
[   22.418985] Allocate Port Service[0000:00:0e.0:pcie00]
[   22.419071] isapnp: Scanning for PnP cards...
[   22.770854] isapnp: No Plug & Play device found
[   22.786582] Real Time Clock Driver v1.12ac
[   22.786677] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.786758] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.787216] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.787652] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.787808] input: Macintosh mouse button emulation as /class/input/input0
[   22.787879] PNP: No PS/2 controller found. Probing ports directly.
[   22.790253] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.790258] serio: i8042 AUX port at 0x60,0x64 irq 12
[   22.790364] mice: PS/2 mouse device common for all mice
[   22.790438] EISA: Probing bus 0 at eisa.0
[   22.790444] Cannot allocate resource for EISA slot 1
[   22.790454] Cannot allocate resource for EISA slot 6
[   22.790455] Cannot allocate resource for EISA slot 7
[   22.790456] Cannot allocate resource for EISA slot 8
[   22.790458] EISA: Detected 0 cards.
[   22.790539] TCP cubic registered
[   22.790550] NET: Registered protocol family 1
[   22.790567] Using IPI No-Shortcut mode
[   22.790707]   Magic number: 8:190:980
[   22.790718]   hash matches device ttyc7
[   22.791188] Freeing unused kernel memory: 364k freed
[   23.948219] AppArmor: AppArmor initialized<5>audit(1200045490.612:2):  type=1505 info="AppArmor initialized" pid=1239
[   23.953178] fuse init (API version 7.8)
[   23.957475] Failure registering capabilities with primary security module.
[   24.158938] ACPI: Transitioning device [FAN] to D3
[   24.158941] ACPI: Transitioning device [FAN] to D3
[   24.158943] ACPI: Fan [FAN] (off)
[   24.162176] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   24.163462] ACPI: Invalid passive threshold
[   24.164241] ACPI: Thermal Zone [THRM] (27 C)
[   24.600715] usbcore: registered new interface driver usbfs
[   24.600734] usbcore: registered new interface driver hub
[   24.600748] usbcore: registered new device driver usb
[   24.601215] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   24.601512] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   24.601520] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[   24.601530] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   24.601533] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   24.601728] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   24.601741] ohci_hcd 0000:00:02.0: irq 16, io mem 0xfe02f000
[   24.646162] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   24.646167] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   24.655923] SCSI subsystem initialized
[   24.659169] libata version 2.21 loaded.
[   24.678753] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   24.687765] usb usb1: configuration #1 chosen from 1 choice
[   24.687784] hub 1-0:1.0: USB hub found
[   24.687793] hub 1-0:1.0: 10 ports detected
[   24.789885] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   24.789894] ACPI: PCI Interrupt 0000:00:02.1[b] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 17
[   24.789903] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   24.789905] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   24.789927] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   24.789950] ehci_hcd 0000:00:02.1: debug port 1
[   24.789952] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   24.789961] ehci_hcd 0000:00:02.1: irq 17, io mem 0xfeb00000
[   24.789965] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.790016] usb usb2: configuration #1 chosen from 1 choice
[   24.790032] hub 2-0:1.0: USB hub found
[   24.790037] hub 2-0:1.0: 10 ports detected
[   24.806614] Floppy drive(s): fd0 is 1.44M
[   24.838688] FDC 0 is a post-1991 82077
[   24.893493] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   24.893511] NFORCE-CK804: chipset revision 242
[   24.893513] NFORCE-CK804: not 100% native mode: will probe irqs later
[   24.893517] NFORCE-CK804: 0000:00:06.0 (rev f2) UDMA133 controller
[   24.893523]     ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:DMA
[   24.893532] Probing IDE interface ide0...
[   25.627610] hda: SONY DVD RW DW-G120A, ATAPI CD/DVD-ROM drive
[   25.747274] usb 1-4: new low speed USB device using ohci_hcd and address 2
[   25.963939] usb 1-4: configuration #1 chosen from 1 choice
[   26.270108] usb 1-6: new low speed USB device using ohci_hcd and address 3
[   26.298587] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   26.314114] sata_nv 0000:00:07.0: version 3.4
[   26.314439] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   26.314447] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 18
[   26.314451] sata_nv 0000:00:07.0: Using ADMA mode
[   26.314491] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   26.314602] scsi0 : sata_nv
[   26.314818] scsi1 : sata_nv
[   26.314932] ata1: SATA max UDMA/133 cmd 0xf8850480 ctl 0xf88504a0 bmdma 0x0001cc00 irq 18
[   26.314935] ata2: SATA max UDMA/133 cmd 0xf8850580 ctl 0xf88505a0 bmdma 0x0001cc08 irq 18
[   26.323233] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   26.323240] Uniform CD-ROM driver Revision: 3.20
[   26.486799] usb 1-6: configuration #1 chosen from 1 choice
[   26.489853] usbcore: registered new interface driver hiddev
[   26.499892] input: Logitech USB Receiver as /class/input/input1
[   26.499907] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-4
[   26.508817] input: Logitech USB Receiver as /class/input/input2
[   26.508826] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-6
[   26.524832] input: Logitech USB Receiver as /class/input/input3
[   26.524846] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-6
[   26.524854] usbcore: registered new interface driver usbhid
[   26.524856] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   26.780971] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   26.828652] ata1.00: ATA-7: ST3160812AS, 3.AAE, max UDMA/133
[   26.828654] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   26.895146] ata1.00: configured for UDMA/133
[   27.204021] ata2: SATA link down (SStatus 0 SControl 300)
[   27.204107] scsi 0:0:0:0: Direct-Access     ATA      ST3160812AS      3.AA PQ: 0 ANSI: 5
[   27.204113] ata1: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   27.204688] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[   27.204695] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 19
[   27.204699] sata_nv 0000:00:08.0: Using ADMA mode
[   27.204737] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   27.204818] scsi2 : sata_nv
[   27.204935] scsi3 : sata_nv
[   27.205043] ata3: SATA max UDMA/133 cmd 0xf883c480 ctl 0xf883c4a0 bmdma 0x0001b800 irq 19
[   27.205046] ata4: SATA max UDMA/133 cmd 0xf883c580 ctl 0xf883c5a0 bmdma 0x0001b808 irq 19
[   27.670985] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   27.679149] ata3.00: ATA-6: ST3120827AS, 3.42, max UDMA/133
[   27.679151] ata3.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   27.695113] ata3.00: configured for UDMA/133
[   28.006231] ata4: SATA link down (SStatus 0 SControl 300)
[   28.006308] scsi 2:0:0:0: Direct-Access     ATA      ST3120827AS      3.42 PQ: 0 ANSI: 5
[   28.006314] ata3: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   28.006921] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   28.006924] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 16
[   28.006929] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   28.006935] forcedeth: using HIGHDMA
[   28.017060] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   28.017070] sd 0:0:0:0: [sda] Write Protect is off
[   28.017072] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.017080] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.017128] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   28.017133] sd 0:0:0:0: [sda] Write Protect is off
[   28.017135] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.017142] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.017145]  sda: sda1 sda2 sda3 sda4 < sda5 >
[   28.049248] sd 0:0:0:0: [sda] Attached SCSI disk
[   28.049353] sd 2:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   28.049359] sd 2:0:0:0: [sdb] Write Protect is off
[   28.049360] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   28.049368] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.049390] sd 2:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   28.049395] sd 2:0:0:0: [sdb] Write Protect is off
[   28.049397] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   28.049404] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.049406]  sdb: sdb1 sdb2 sdb3
[   28.057655] sd 2:0:0:0: [sdb] Attached SCSI disk
[   28.060686] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   28.060701] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   28.395340] Attempting manual resume
[   28.395344] swsusp: Resume From Partition 8:5
[   28.395345] PM: Checking swsusp image.
[   28.395490] PM: Resume from disk failed.
[   28.427867] kjournald starting.  Commit interval 5 seconds
[   28.427876] EXT3-fs: mounted filesystem with ordered data mode.
[   28.525558] eth0: forcedeth.c: subsystem: 0147b:1c1a bound to 0000:00:0a.0
[   38.913245] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   38.921378] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.400648] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   39.400667] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   39.601679] input: PC Speaker as /class/input/input4
[   39.703327] parport_pc 00:09: reported by Plug and Play ACPI
[   39.703370] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   40.956861] Linux agpgart interface v0.102 (c) Dave Jones
[   41.229633] nvidia: module license 'NVIDIA' taints kernel.
[   41.498597] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   41.498606] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 20
[   41.498613] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   41.498816] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.07  Thu Dec 13 18:42:56 PST 2007
[   41.536273] usbcore: registered new interface driver lmpcm_usb
[   41.536278] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   41.709841] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   41.709846] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 17
[   41.709863] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   42.030925] intel8x0_measure_ac97_clock: measured 54476 usecs
[   42.030928] intel8x0: clocking to 46973
[   47.534396] lp0: using parport0 (interrupt-driven).
[   47.572136] Adding 2136604k swap on /dev/sda5.  Priority:-1 extents:1 across:2136604k
[   47.817320] EXT3 FS on sda3, internal journal
[   48.097484] kjournald starting.  Commit interval 5 seconds
[   48.097491] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   48.097693] EXT3 FS on sda2, internal journal
[   48.097697] EXT3-fs: mounted filesystem with ordered data mode.
[   48.889461] input: Power Button (FF) as /class/input/input5
[   48.889657] ACPI: Power Button (FF) [PWRF]
[   48.890426] input: Power Button (CM) as /class/input/input6
[   48.890618] ACPI: Power Button (CM) [PWRB]
[   48.918318] No dock devices found.
[   49.220668] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (version 2.00.00)
[   49.225117] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   52.732642] Failure registering capabilities with primary security module.
[   53.698744] ppdev: user-space parallel port driver
[   54.488129] audit(1200041921.870:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5147 profile="/usr/sbin/cupsd"
[   57.004967] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   57.004972] apm: overridden by ACPI.
[   62.122871] Bluetooth: Core ver 2.11
[   62.122992] NET: Registered protocol family 31
[   62.122994] Bluetooth: HCI device and connection manager initialized
[   62.122997] Bluetooth: HCI socket layer initialized
[   62.149863] Bluetooth: L2CAP ver 2.8
[   62.149867] Bluetooth: L2CAP socket layer initialized
[   62.258816] Bluetooth: RFCOMM socket layer initialized
[   62.258929] Bluetooth: RFCOMM TTY layer initialized
[   62.258930] Bluetooth: RFCOMM ver 1.8
[   62.329832] input: btnx keyboard as /class/input/input7
[   62.331033] input: btnx mouse as /class/input/input8
[   62.823154] NET: Registered protocol family 29
[   62.923551] 
[   62.923553] ndas: Initializing NDAS driver version 1.1.15
[   62.925706] ndas: Setting max request size to 64kbytes
[   62.925715] ndas: registering network interface eth0
[   63.125868] ndas: registered ndas device at major number 60
[   69.257860]  ndas-00508403-0: p1
[   69.275195]  ndas-00508403-0: p1 exceeds device capacity
[   69.310758] ndas: /dev/ndas-00508403-0 enabled
[   70.234866] /dev/vmmon[6036]: VMCI: Driver initialized.
[   70.236088] /dev/vmmon[6036]: Module vmmon: registered with major=10 minor=165
[   70.236389] /dev/vmmon[6036]: Initial HV check: anyNotCapable=1 anyUnlocked=0 anyEnabled=0 anyDisabled=0
[   70.236392] /dev/vmmon[6036]: Module vmmon: initialized
[   70.919158] /dev/vmnet: open called by PID 6080 (vmnet-bridge)
[   70.919423] /dev/vmnet: hub 0 does not exist, allocating memory.
[   70.919608] /dev/vmnet: port on hub 0 successfully opened
[   70.919799] bridge-eth0: enabling the bridge
[   70.919943] bridge-eth0: up
[   70.920086] bridge-eth0: already up
[   70.920088] bridge-eth0: attached
[   71.047618] /dev/vmnet: open called by PID 6097 (vmnet-netifup)
[   71.047875] /dev/vmnet: hub 1 does not exist, allocating memory.
[   71.048056] /dev/vmnet: port on hub 1 successfully opened
[   71.052381] ndas: network up. Registering vmnet1
[   71.135959] /dev/vmnet: open called by PID 6096 (vmnet-dhcpd)
[   71.136164] /dev/vmnet: port on hub 1 successfully opened
[   71.211310] /dev/vmnet: open called by PID 6118 (vmnet-dhcpd)
[   71.211512] /dev/vmnet: hub 8 does not exist, allocating memory.
[   71.211691] /dev/vmnet: port on hub 8 successfully opened
[   71.328531] /dev/vmnet: open called by PID 6123 (vmnet-natd)
[   71.328796] /dev/vmnet: port on hub 8 successfully opened
[   72.185543] /dev/vmnet: open called by PID 6209 (vmnet-netifup)
[   72.185664] /dev/vmnet: port on hub 8 successfully opened
[   72.190488] ndas: network up. Registering vmnet8
[   72.299590] attempt to access beyond end of device
[   72.299598] ndas-00508403-0: rw=0, want=321669319, limit=321668864
[   72.299601] Buffer I/O error on device ndas-00508403-0p1, logical block 40208656
[   72.299605] attempt to access beyond end of device
[   72.299607] ndas-00508403-0: rw=0, want=321669319, limit=321668864
[   72.299609] Buffer I/O error on device ndas-00508403-0p1, logical block 40208656
[   72.299618] attempt to access beyond end of device
[   72.299620] ndas-00508403-0: rw=0, want=321669487, limit=321668864
[   72.299622] Buffer I/O error on device ndas-00508403-0p1, logical block 40208677
[   72.299624] attempt to access beyond end of device
[   72.299626] ndas-00508403-0: rw=0, want=321669487, limit=321668864
[   72.299628] Buffer I/O error on device ndas-00508403-0p1, logical block 40208677
[   72.302125] attempt to access beyond end of device
[   72.302129] ndas-00508403-0: rw=0, want=321669495, limit=321668864
[   72.302131] Buffer I/O error on device ndas-00508403-0p1, logical block 40208678
[   72.302432] attempt to access beyond end of device
[   72.302435] ndas-00508403-0: rw=0, want=321669495, limit=321668864
[   72.302436] Buffer I/O error on device ndas-00508403-0p1, logical block 40208678
[   72.302757] attempt to access beyond end of device
[   72.302759] ndas-00508403-0: rw=0, want=321669495, limit=321668864
[   72.302761] Buffer I/O error on device ndas-00508403-0p1, logical block 40208678
[   72.303063] attempt to access beyond end of device
[   72.303065] ndas-00508403-0: rw=0, want=321669495, limit=321668864
[   72.303067] Buffer I/O error on device ndas-00508403-0p1, logical block 40208678
[   72.303368] attempt to access beyond end of device
[   72.303370] ndas-00508403-0: rw=0, want=321669495, limit=321668864
[   72.303372] Buffer I/O error on device ndas-00508403-0p1, logical block 40208678
[   72.303674] attempt to access beyond end of device
[   72.303676] ndas-00508403-0: rw=0, want=321669495, limit=321668864
[   72.303678] Buffer I/O error on device ndas-00508403-0p1, logical block 40208678
[   72.303980] attempt to access beyond end of device
[   72.303982] ndas-00508403-0: rw=0, want=321669495, limit=321668864
[   72.304166] attempt to access beyond end of device
[   72.304168] ndas-00508403-0: rw=0, want=321669439, limit=321668864
[   72.304352] attempt to access beyond end of device
[   72.304354] ndas-00508403-0: rw=0, want=321669487, limit=321668864
[   72.304542] attempt to access beyond end of device
[   72.304544] ndas-00508403-0: rw=0, want=321669495, limit=321668864
[   72.304728] attempt to access beyond end of device
[   72.304730] ndas-00508403-0: rw=0, want=321669495, limit=321668864

```

---

### Post by #Reistlehr- on 2008-01-11
From the end of the dmesg, looks like it's trying to read in accessable blocks/sectors.

I would suggest to run e2fsck your drive/s.

```
e2fsck -f <device>
```

-f forces a check on drives marked/flagged clean. You can add the -y option, for it there is an error, you will probably only be able to hit enter anywy.

---

### Post by pototo on 2008-01-12
> **#Reistlehr- said:**
> From the end of the dmesg, looks like it's trying to read in accessable blocks/sectors.

I would suggest to run e2fsck your drive/s.

```
e2fsck -f <device>
```-f forces a check on drives marked/flagged clean. You can add the -y option, for it there is an error, you will probably only be able to hit enter anywy.

The system is trying to read a read-only NDAS drive, used to store music and some multimedia files from a Windows XP system. I also tried uninstalling the NDAS drivers, but it had no impact on the boot time.

---

### Post by bluesrocker on 2008-01-12
Try removing Packard. :guitar:

---

### Post by rainwalker on 2008-01-14
> **#Reistlehr- said:**
> 
     Do you have a Radeon video card/chipset?
          A: Yes - Make sure to run the newest drivers which fixes numerous bugs
          B: No - Continue reading.


If you mean the restricted driver, I can't; It messes up everything when I try to use Compiz.

---

### Post by misfitpierce on 2008-01-14
Mine does not do this on my laptop, it's maybe a second longer. My friends does do this though. Ubuntu 8.04 should correct the bootup as well as login timing with cached startups which should be nice. Only a matter of time :)

---

### Post by r_mano on 2008-01-14
Hmmm. 

I have in my /etc/hosts: 

```
127.0.0.1 localhost pern
127.0.1.1 pern
```

and really I do not know from where the second line come from, or where is used (a second loopback name?). It seems that commenting that out solves the delay.

Romano

---

### Post by enigma_0Z on 2008-01-14
Has anyone found a definitive solution to this? It seems that it takes approx. 40 seconds to load after screenlets loads on my system.

And yes, I do have compiz running, but no, it's not the freeze from compiz starting--compiz starts, and then everything freezes while the desktop icons/wallpaper (nautilus?) comes up.

---

### Post by IamAcoconut on 2008-01-14
My 20sec lag starts just after logging in, and lasts until Compiz and then panels start loading (almost simultaneously). 
Using Intel's integrated graphics (855), and disabling IPv6 (through blacklist) doesn't help, nor does any other thing from #Reistlehr's list :(

---

### Post by syxbit on 2008-01-15
what can i say, gutsy is the most bug-filled ubuntu yet.
stick with the .04 releases.
Dapper (technically .06) and Feisty were much more stable for me than either edgy or gutsy

---

### Post by enigma_0Z on 2008-01-15
> **syxbit said:**
> what can i say, gutsy is the most bug-filled ubuntu yet.
stick with the .04 releases.
Dapper (technically .06) and Feisty were much more stable for me than either edgy or gutsy

When you put it that way...

It seems that that makes sense based on the names... dapper and feisty (and the upcoming hardy) suggest preparedness and attitude, whereas gutsy and edgy suggest pushing the boundaries--perhaps a less stable system, etc.

---

### Post by #Reistlehr- on 2008-01-16
> **enigma_0Z said:**
> ...whereas gutsy and edgy suggest pushing the boundaries--perhaps a less stable system, etc...

What a great way to put it.. And unfortunatly for some, pushing those boundries is too much to ask for.

Once again though to reinstate; there is no one cause for this problem. It seems that multiple causes can be traced back to a similar, common result of slow login.

---

### Post by carney1979 on 2008-01-17
I have a laptop with a dual-core processor and 2 gigs of ram, should be real fast but like all of you, Gnome boots slowly, takes about a minute.

One thing I noticed is I don't see the Gnome splash screen (NOT usplash) at all. I wonder if it's looking for a splash screen but not finding it?

David

---

### Post by gioland71 on 2008-01-21
Hi guys, 

my laptop (Compaq V2000, AMD processor - ubuntu 7.10 i386) started showing signs of the slow login issue (after entering the password, beige screen for about 2 minutes, then the gui was very slow in responding for about 2 more minutes) after I installed samba & NFS. I could isolate the problem to NFS (it also stalled the boot sequence when the NFS daemons were loaded). I noticed that my /etc/network/interfaces had my work fixed IP both for eth0 and eth1. 
The issue was present both at work (where I use a fixed IP) and at home (dhcp). I also have to use wicd for wireless because the default ubuntu network manager doesn't work with fixed IPs.
Removing NFS and commenting out the fixed IP lines in the interfaces file solved the problem for me. I still have to find out exactly which of the two caused the problem, but hopefully this will help somebody else to solve the slow login issue.

---

### Post by aashay on 2008-01-27
Did this ever get solved? I dint go through the 30 pages.. so I apologize if this question is redundant.
As an aside, network-manager doesnt seem to be the culprit as mentioned in the bug reports. An XFCE session with it starts much quicker

---

### Post by corney91 on 2008-01-27
> **aashay said:**
> Did this ever get solved? I dint go through the 30 pages.. so I apologize if this question is redundant.
As an aside, network-manager doesnt seem to be the culprit as mentioned in the bug reports. An XFCE session with it starts much quicker

Does this help?:[http://ubuntuforums.org/showthread.php?t=568995]("http://ubuntuforums.org/showthread.php?t=568995")

---

### Post by aashay on 2008-01-30
Can't say it did. Din't have the session file in the first place. Even executing "gnome-session-save" and then editing the file hardly made any difference

---

### Post by pototo on 2008-01-30
> **corney91 said:**
> Does this help?:[http://ubuntuforums.org/showthread.php?t=568995](http://ubuntuforums.org/showthread.php?t=568995)

It worked for me. I found the session file, I edited it and now my login time is about 25 secs faster.

---

### Post by p252 on 2008-02-03
I was having the same problem on my older HP Pavilion ZE4430 Laptop. 7.10 has been quite a pain. Don't know what happened since 7.04, being that 7.04 worked wonderfully. 7.10 doesn't seem to like older hardware (this laptop is old but not THAT old). Wonder if it's the fancy eye candy that tries to install by default (I really wish this was not the default, it's annoying and a waste of resources, let people install it if they so choose). Any way, I did a fresh install from Ubuntu 7.10 Alternale install cd and it works SIGNIFICANTLY better, including usplash works with no tweaking. Boot up is now quick as well as login is fast. My problem now is that the computer still runs like crap (really slow, and the fan is always blasting,even when I turn the 3d Desktop/Compiz stuff off). Like I said, I don't know what has changed, but Ubuntu 7.10 doesn't like my somewhat older hardware (not just this laptop, I have a somewhat older desktop with completely different specs that does the same thing). On the bright side, 7.10 runs beautifully on my shiny new Dell Inspiron E1505n. This is good and sad at the same time, I hate to see Ubuntu go in a direction like the other Popular OS and only work on nice new hardware. This is, as I am well aware, a view stemming from my own limited narrow experience of Ubuntu 7.10 on my older computers.

Anyway, I'd say try the alternate install cd if it has not been tried (This was a long thread, stopped reading after page 6 so not sure if this was suggested already).

---

### Post by #Reistlehr- on 2008-02-06
If you're just joining the thread, search my old posts, i summed everything up as best as possible. More than one thing cause this problem. For me, its the nvidia drivers.

@ Carney - You can install the gnome-splash-manager through apt-get if you wish. It was removed from what i read to save a few resources. Installing it makes no difference.

---

### Post by _Stevie_ on 2008-02-06
when i remove all items in the session manager it boots slightly faster, but its still unbearable.
i pretty much tried everything to fix it...
hopefully hoary will be better.

---

### Post by corney91 on 2008-02-07
> **_Stevie_ said:**
> 
hopefully hoary will be better.
You mean Hardy. It fixed it for me.

---

### Post by _Stevie_ on 2008-02-07
yep, sorry, of course i meant hardy.
im a bit careful with hardy, since its still in alpha stage.
therfore i cant install it to replace gutsy.

---

### Post by #Reistlehr- on 2008-02-07
> **corney91 said:**
> You mean Hardy. It fixed it for me.

What are you pc specs? Kernel, Arch, etc?

---

### Post by _Stevie_ on 2008-02-07
you mean me or corney91?

---

### Post by corney91 on 2008-02-07
> **#Reistlehr- said:**
> What are you pc specs? Kernel, Arch, etc?

Mine's HP-Compaq nx9020, 1.4GHz Celeron M processor, integrated graphics memory, and 1GB RAM and:
```
dan@dan-laptop:~$ uname -a
Linux dan-laptop 2.6.24-5-generic #1 SMP Thu Jan 24 19:45:21 UTC 2008 i686 GNU/Linux
```

My login was taking quite a bit longer than feisty, slightly more than XP did but now it's rapid:)

---

### Post by sweetsinse on 2008-02-07
not a solution but this is really interesting....

[http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)

found it here...

> Recently, I discovered a truly neat tutorial ([http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)) for manually using readahead to cut down my login time to 14-20 seconds in gutsy, but it is a hack on top of ubuntu, not a real solution (or at least, I would prefer for ubuntu to do it for me: [https://blueprints.launchpad.net/ubuntu/+spec/login-readahead](https://blueprints.launchpad.net/ubuntu/+spec/login-readahead))

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/128803](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/128803)

---

### Post by mgmiller on 2008-02-08
You beat me to it sweetsince, I was just about to post that link.

---

### Post by _Stevie_ on 2008-02-08
yep its some nice speedup, but still a strange, long boot-behaviour.

---

### Post by blackvd on 2008-02-12
Well I disabled compiz and rebooted. Looks like that's the problem for me as it loaded right up.

---

### Post by funnypanks on 2008-03-09
for those who can't stand the long boot time, install kde. kde takes ~15secs as opposed to -70secs with gnome. i know it seems drastic to jump ships due to load time, but it gets annoying after a while

---

### Post by _Stevie_ on 2008-03-09
well indeed, but i hope the gnome devs are aware of this and fix it.

---

### Post by enigma_0Z on 2008-03-09
I'm pretty sure it's a nautilus problem, as everything else comes up but desktop icons...

Is there a bug report that I could check on?

---

### Post by _Stevie_ on 2008-03-09
that would be here then:
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/128803](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/128803)

---

### Post by snkiz on 2008-03-20
I to have this issue what I did was watch my session properties as gnome loads, for me I seems to hang on the gnome-wm script. witch makes some sense I guess because I used gconf to switch to xfwm4. It is also listed in the session properties on its own xsession-errors say its trying to load twice. But I did this Fiesty with no problems. Also due to my switch I can't use the session splash it stays on my desktop long after gnome is finished loading. I just haven't figured out how to fix the either problem.... any ideas?

---

### Post by frodon on 2008-03-20
Loading xfwm4 on session startup instead of gnome create a really long login time i have tested this myself on my computer.
But now are you using metacity or xfwm4 ?

---

### Post by snkiz on 2008-03-20
I'm using Xfwm4 now i like it its all the transparency my box can handle and when it finialy does load it seems faster than metacity. If I kill the extra instance in the session properities it finishes loading almost right away. I miss my session splash though I had a really neat one.

---

### Post by Hachi-Roku on 2008-03-22
Im getting this long log in time too..... but only AFTER i changed a graphics driver to fix the shutdown hang problem, as suggested here.... [http://ubuntuforums.org/showthread.php?t=591229&page=8](http://ubuntuforums.org/showthread.php?t=591229&page=8)

Can this be a cause?

i can deal with the long log in time as opposed to holding the power button to turn it off.... but  both fixed would be nice :)

---

### Post by madscientist032 on 2008-03-27
Yes, Gusty does have an obnoxiously long boot time (about 2-3 minutes on my system), considering that Compiz is installed (but not enabled automatically after boot).

Is there a list of changes from Feisty to Gusty floating around somewhere? I'm sure it could be helpful with this issue.

---

### Post by #Reistlehr- on 2008-03-29
> **madscientist032 said:**
> Is there a list of changes from Feisty to Gusty floating around somewhere? I'm sure it could be helpful with this issue.

Been looking, and havent found any true documentation on it.

---

### Post by J@n on 2008-03-30
> **frodon said:**
> For the record, once i used the "gnome-session-save" command i had the extreme long login problem or exactly after 2 minutes waiting the end of the login process i killed the xserver.
Then i got the idea to put back my feisty session file and i got back to normal except that if i save my session i know i will get the problem on next login.

So i don't know for you but in my case the problem is directly related to the session file and the way gutsy write it, but for the moment i'm not 100% convinced my problem and yours are the same.

I was installing the new NVIDIA drivers which was a pain in itself. I accidently used the Save session option from within Hardy during configuration and checking. After reboot performance was terrible. I timed a wait of about 2½ minutes from login to desktop. Reading your post fixed my problem though\\:D/

That should teach me to change only one thing at a time :oops:

---

### Post by snkiz on 2008-03-31
I'm now running gutsy login started out fine, even after I switched the wm to xfwm4 (Short lag as the mcs-manager and gnome-session argue) But after tweeking my startup order (Btw didn't work reset on logon) and saving my session I'm back To stupid long login time. So I'd like to session and change the startup order from the config file but I don't know where they are saved. Anyone? I'll post the results of my litte experiment when i get home from work.

---

### Post by snkiz on 2008-03-31
Ops I ment delete my session, dam phone.

---

### Post by daniel_victoria on 2008-04-29
Has this issue been fixed in Hardy? I haven't upgraded yet and I'm not feeling very adventurous

Thanks
Daniel

---

### Post by cowanh00 on 2008-04-29
> **daniel_victoria said:**
> Has this issue been fixed in Hardy? I haven't upgraded yet and I'm not feeling very adventurous

Thanks
Daniel

Yes it seams to have fixed the issue for me.

EDIT: It should be noted that I did a clean install.

---

### Post by linuxmad on 2008-04-29
I upgraded to hardy (clean install) and I didn't notice this problem. I am running cairo-dock, still I must say the session start doesn't lag.. at least for now.

---

### Post by bertilow on 2008-04-30
This does seem to be fixed in Hardy - at least for me. I did a fresh install of Kubuntu, and I see no such lags any more. (There are of course other problems instead, new and fresh ones, never seen before...)

---

