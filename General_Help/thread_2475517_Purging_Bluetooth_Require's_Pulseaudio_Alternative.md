---
title: "Purging Bluetooth Require's Pulseaudio Alternative"
date: 2022-05-30
forum: General Help
---

### Post by wyattwhiteeagle on 2022-05-30
I use Youtube, Netflix, Hulu, Disney+, Spotify and *.mp3 files.

All of the above uses Pulseaudio.

Purging all of Bluetooth also purges Pulseaudio.

I've read that Pipwire is a good alternative for Pulseadio, but all of the suggesting user's mention that they use Pipewire for the bluetooth capabilities.

Looking in Muon Package Manager, I didn't see anything bluetooth associated with Pipewire.

Is Pipewire a good non-bluetooth alternative for pulseaudio?

Is there a pulseaudio alternative which isn't a snap that doesn't require bluetooth?

---

### Post by HermanAB on 2022-05-30
Hmm, I don’t know what you got against BT and Pulseaudio, they both work well enough for most people.  However, if you must, you can just use plain old ALSA, which also works well enough for many people.  

The Pulseaudio sound server is only really needed when your sound system changes dynamically, as happens when using BT devices.

---

### Post by #&amp;thj^% on 2022-05-30
> **wyattwhiteeagle said:**
> 

I've read that Pipwire is a good alternative for Pulseadio, but all of the suggesting user's mention that they use Pipewire for the bluetooth capabilities.

Is Pipewire a good non-bluetooth alternative for pulseaudio?


I find it much better:
```
wpctl status
PipeWire 'pipewire-0' [0.3.51, me@arch-me, cookie:3824252965]
 &#9492;&#9472; Clients:
        32. xfce4-pulseaudio-plugin             [0.3.51, me@arch-me, pid:987]
        33. pipewire-pulse                      [0.3.51, me@arch-me, pid:1034]
        34. WirePlumber                         [0.3.51, me@arch-me, pid:1031]
        35. WirePlumber [export]                [0.3.51, me@arch-me, pid:1031]
        63. xdg-desktop-portal                  [0.3.51, me@arch-me, pid:10490]
        64. virt-manager                        [0.3.51, me@arch-me, pid:109469]
        65. virt-manager                        [0.3.51, me@arch-me, pid:109469]
        66. Strawberry device finder            [0.3.51, me@arch-me, pid:888940]
        70. strawberry                          [0.3.51, me@arch-me, pid:888940]
        79. wpctl                               [0.3.51, me@arch-me, pid:891185]

Audio
 &#9500;&#9472; Devices:
 &#9474;      31. HDA NVidia                          [alsa]
 &#9474;      49. UOEOS Laptop Dock                   [alsa]
 &#9474;      53. Family 17h/19h HD Audio Controller  [alsa]
 &#9474;      73. SRS-XB22                            [bluez5]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;      42. Family 17h/19h HD Audio Controller Analog Stereo [vol: 0.74]
 &#9474;      44. UOEOS Laptop Dock Digital Stereo (IEC958) [vol: 0.74]
 &#9474;  *   74. SRS-XB22                            [vol: 0.60]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;      43. UOEOS Laptop Dock Digital Stereo (IEC958) [vol: 0.74]
 &#9474;  *   52. Family 17h/19h HD Audio Controller Analog Stereo [vol: 0.74]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:
        68. strawberry                                                  
             71. output_FR       > SRS-XB22:playback_FR
             72. output_FL       > SRS-XB22:playback_FL

Video
 &#9500;&#9472; Devices:
 &#9474;      50. Integrated Camera                   [v4l2]
 &#9474;      51. Integrated Camera                   [v4l2]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   56. Integrated Camera                  
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    bluez_output.F8_DF_15_7F_64_73.a2dp-sink
         1. Audio/Source  alsa_input.pci-0000_04_00.6.analog-stereo


```
You will still need all the Bluetooth packages though.
Using the same format as the ALSA monitor, the configuration file bluetooth.lua.d/50-bluez-config.lua is charged to configure the Bluetooth devices and nodes created by WirePlumber.

---

### Post by guiverc on 2022-05-30
> **wyattwhiteeagle said:**
> 
Is Pipewire a good non-bluetooth alternative for pulseaudio?

Pulse Audio is a Sound/Audio server.

PipeWire is a media server, which includes Audio, Video ... thus encompasses more.

Neither really handle bluetooth (*which is used for transferring many types of data*), but are somewhat forced to use it given users like using bluetooth for speakers & other audio related purposes.

You didn't provide any release details. but Ubuntu 22.10 is expected to use PipeWire by default, eg. the latest [URL="https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue737#New_audio_server_Pipewire_coming_to_next_version_of_Ubuntu"]Ubuntu Weekly Newsletter
[/URL]

---

### Post by wyattwhiteeagle on 2022-05-31
> **HermanAB said:**
> Hmm, I don&#8217;t know what you got against BT and Pulseaudio, they both work well enough for most people.  However, if you must, you can just use plain old ALSA, which also works well enough for many people.  

The Pulseaudio sound server is only really needed when your sound system changes dynamically, as happens when using BT devices.
Is it impossible to completely get away away from bluetooth?
I don't use bluetooth intentionally.
Any blue that I may be using is because I'm unaware of it's need.

I don't have anything against pulseaudio.
However, bluetooth is a different story.

Some time ago, TheFu, as well as others, has been hacked through bluetooth.

When I was on Windows ME, I had a similar experience with bluetooth.

I feel that bluetooth is a major security hole.

So far, the only things bluetooth that can be safely removed and purged is...
```
bluez
bluez-cups
bluez-obexd
```

The bluez-cups is most likely used for printing over a wireless network.
Which I never do.
I always use a wired local connection between my laptop and the printer.

The wifi connection seems to use something bluetooth.
When I search within dpkg for all "blue" entries and purge them all...
I lose sound and the ability to connect to wifi.

I haven't found the ALSA configurations to still hear sound when pulseaudio is removed due to everything "blue" being purged.

Someone said here that some of the bluetooth stuff is needed.

---

### Post by #&amp;thj^% on 2022-05-31
I was around when TheFu reported the hack, I'm guessing around 3 to 4 years back.

Bluetooth  is a universal protocol for low power, near field communication  operating at 2.4 - 2.485 GHz using spread spectrum, frequency hopping at  1,600 hops per second (this frequency hopping is a security measure). 

The  minimum specification for Bluetooth range is 10 meters, but there is no  limit to the range that manufacturers may implement in their devices.  Many devices have ranges as long as 100 meters. With special antennas,  we can extend the range even farther.

Although much more  secure in recent years, it is still vulnerable, As are a few other programs in our daily use.

There have been three security modes for Bluetooth. These are:
[list]
    [*]Security Mode 1: No active security.

    [*]Security  Mode 2: Service level security. Centralized security manager handles  authentication, configuration, and authorization. May not be activated  by user. No device level security.

    [*]Security  Mode 3: Device level security. Authentication and encryption based on  secret key. Always on. Enforces security for low-level connection.
[/list]
Now I'm one who praises the fact that we/you have someone like TheFu. (Just a Keen knowledge of security)
Now I throw this out for your consideration, I've used a strict policy on bluetooth for over 5 yrs now and had no hacks.
You are aware you can disable it at will right?
But stay within your comfort zone, if this was a server then I whole heartily agree>>>No Bluetooth.

---

### Post by wyattwhiteeagle on 2022-06-04
> **1fallen said:**
> I was around when TheFu reported the hack, I'm guessing around 3 to 4 years back.

Bluetooth  is a universal protocol for low power, near field communication  operating at 2.4 - 2.485 GHz using spread spectrum, frequency hopping at  1,600 hops per second (this frequency hopping is a security measure). 

The  minimum specification for Bluetooth range is 10 meters, but there is no  limit to the range that manufacturers may implement in their devices.  Many devices have ranges as long as 100 meters. With special antennas,  we can extend the range even farther.

Although much more  secure in recent years, it is still vulnerable, As are a few other programs in our daily use.

There have been three security modes for Bluetooth. These are:
[LIST]
[*]Security Mode 1: No active security.
[*]Security  Mode 2: Service level security. Centralized security manager handles  authentication, configuration, and authorization. May not be activated  by user. No device level security.
[*]Security  Mode 3: Device level security. Authentication and encryption based on  secret key. Always on. Enforces security for low-level connection.
[/LIST]
Now I'm one who praises the fact that we/you have someone like TheFu. (Just a Keen knowledge of security)
Now I throw this out for your consideration, I've used a strict policy on bluetooth for over 5 yrs now and had no hacks.
You are aware you can disable it at will right?
But stay within your comfort zone, if this was a server then I whole heartily agree>>>No Bluetooth.

I was back and forth between Ubuntu and Windows 7 HP during the time TheFu and others were hacked.
My Windows ME machine was quite a bit before that...like the year 2000 to 2004.
That computer was a basic home Desktop PC with software for a small business in-home office.
I purchased it from a small engine repair specialist.
His wife at the time was using that PC to keep records, Tax info, appointments, etc.
It was actually a home pc tower computer.

The machine I have now, the bluetooth capabilities seem to be part of the network adapter wifi connection driver files.
It's a Dell Latitude E5400, Windows Vista machine.
Far from being a server machine.
It doesn't seem to have a seperate piece of hardware that supports bluetooth of it's own.

A strict policy on bluetooth with the ability to enable/disable at will?
It seems I need to look more into these practices instead of just trying to purge all bluetooth.
Where do I start?

---

### Post by #&amp;thj^% on 2022-06-04
**TL;DR** >Here is a nice article written in 10/2020 that describes the flaws first found in BlueZ:[https://www.zdnet.com/article/google-warns-of-severe-bleedingtooth-bluetooth-flaw-in-linux-kernel/](https://www.zdnet.com/article/google-warns-of-severe-bleedingtooth-bluetooth-flaw-in-linux-kernel/)

Now before going off the rails read the updated info by Google security engineer Andy Nguyen: [https://portswigger.net/daily-swig/bleedingtooth-google-drops-full-details-of-zero-click-linux-bluetooth-bug-chain-leading-to-rce](https://portswigger.net/daily-swig/bleedingtooth-google-drops-full-details-of-zero-click-linux-bluetooth-bug-chain-leading-to-rce)

Now my policy is never have Bluetooth enabled when in a public area, This is a risk in public spaces, like airports, trains, and cafés.

&#8220;Research on the Bluetooth host attack surface&#8221; otherwise seemed mostly limited to firmware or specification flaws that enabled eavesdropping or information manipulation, observed the researcher.

I'll always warn>>> updating to Linux kernel 5.9 and higher to mitigate a serious flaw Google found in the Linux Bluetooth stack.

Protect your Bluetooth devices against security risks:

While new devices are not vulnerable to attacks mentioned previously all time new exploits and security holes emerge.
The only safe measure is to keep the bluetooth turned off as much as you don&#8217;t use it, in the worst case you need it always turned on at least keep it undiscoverable despite as you saw there are tools to discover them anyway.

Tips:
Restrict permissions on the bluetooth functionalities, some applications require bluetooth access permissions, try to limit permissions on the bluetooth device as much as possible.

Another point to take in consideration is our location when we use bluetooth devices, enabling this functionality in public places full of people isn&#8217;t recommended.

And of course, you should never accept pairing requests, and if you get unknown pairing request turn off your bluetooth immediately, some attacks take place during the handshake negotiation (authentication).

Don&#8217;t use third party apps which promise to protect your bluetooth, instead keep a safe configuration as said before: turn off or hide the device.

Conclusion:

While bluetooth attacks aren&#8217;t widely used (when compared with other types of attacks like phishing or DDOS) almost every person carrying a mobile device is a potential victim, therefore in our countries most people are exposed, also through bluetooth, to sensitive data leak. 

On the other hand most manufacturers already patched devices to protect them from almost all attacks described above, but they only can issue a fix after the vulnerability was discovered and published (like with any vulnerability).

The best solution is to keep the device turned off in public spaces, since most attacks require a short range you can use the device safely in private places (Home).

To soft block at will:
```
rfkill block bluetooth


me on Sat Jun 04 at 08:32 AM in ~ branch: (HEAD) 
>> rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```
Another method:
```
sudo systemctl stop bluetooth


me on Sat Jun 04 at 08:58 AM in /etc/default branch: (HEAD) 
>> systemctl status bluetooth
&#9675; bluetooth.service - Bluetooth service
     Loaded: loaded (/usr/lib/systemd/system/bluetooth.service; disabled; vendor preset: disabled)
     Active: inactive (dead)
       Docs: man:bluetoothd(8)
Jun 04 08:58:12 arch-me systemd[1]: bluetooth.service: Deactivated successfully.
Jun 04 08:58:12 arch-me systemd[1]: Stopped Bluetooth service.

```

Or disable on boot:
```
sudo systemctl disable bluetooth
[sudo] password for me: 
Removed "/etc/systemd/system/bluetooth.target.wants/bluetooth.service".
Removed "/etc/systemd/system/dbus-org.bluez.service".

```

Can Bluetooth be secured?

You have to approve each new connection, which makes Bluetooth relatively secure. Once devices connect for the first time, the pairing is usually remembered and future connections will happen automatically, at least when both devices have Bluetooth activated and are near each other.
Is it bullet proof** Hell NO**, but with my practice on BlueZ, I don't feel the need to fear.

This is a worthwhile read, please do so: [https://vpnoverview.com/privacy/devices/bluetooth/](https://vpnoverview.com/privacy/devices/bluetooth/)
```
pacman -Qi bluez
Name            : bluez
Version         : 5.64-2
**Description     : Daemons for the bluetooth protocol stack**
Architecture    : x86_64
URL             : http://www.bluez.org/
Licenses        : GPL2
Groups          : None
Provides        : None
Depends On      : libical  dbus  glib2  alsa-lib  json-c
Optional Deps   : None
Required By     : blueman  bluez-hciconfig  bluez-qt
Optional For    : networkmanager
Conflicts With  : obexd-client  obexd-server
Replaces        : None
Installed Size  : 2.43 MiB
Packager        : Andreas Radke <snip>
Build Date      : Sat 19 Mar 2022 03:42:28 AM MDT
Install Date    : Thu 05 May 2022 09:33:11 AM MDT
Install Reason  : Explicitly installed
Install Script  : No
Validated By    : Signature


```

---

### Post by HermanAB on 2022-06-04
You can disable BT in the BIOS, or blacklist the BT kernel module. If you do that, then there is no need to futz with the audio system.

---

### Post by wyattwhiteeagle on 2022-06-07
> **HermanAB said:**
> You can disable BT in the BIOS
For me...easier said than done...
My BIOS doesn't have Bluetooth listed anywhere.

> or blacklist the BT kernel module.
I'm not sure how to blacklist something.
How do I do that?

> If you do that, then there is no need to futz with the audio system.
I sure hope something will work for me.

---

### Post by HermanAB on 2022-06-07
The below actually uses the usb core module as an example:
[https://linuxconfig.org/how-to-blacklist-a-module-on-ubuntu-debian-linux](https://linuxconfig.org/how-to-blacklist-a-module-on-ubuntu-debian-linux)

I cannot give more specific information, since my daily use machine is a Macbook.  So I’ll have to fire up a virtual machine or a Raspberry Pi for precise details.

---

### Post by HermanAB on 2022-06-07
TIMTOWTDI:
There are also many wrong and innovative ways to disable a kernel module.  For example, you can find the module and delete it, then reboot.  What isn’t there, cannot be loaded.

Or you can make a startup process that unloads the already loaded module with rmmod.

Etc…

---

### Post by wyattwhiteeagle on 2022-06-07
> **HermanAB said:**
> TIMTOWTDI:
There are also many wrong and innovative ways to disable a kernel module.  For example, you can find the module and delete it, then reboot.  What isn’t there, cannot be loaded.…
Is that an example of a wrong way to do it?

---

### Post by #&amp;thj^% on 2022-06-07
To find the mod:
```

lsmod
bluetooth             933888  6 btrtl,btmtk,btintel,btbcm,btusb
```
Or for a nice short view:
```
lsmod | grep bluetooth
bluetooth             933888  6 btrtl,btmtk,btintel,btbcm,btusb
ecdh_generic           16384  1 bluetooth
rfkill                 36864  6 iwlmvm,bluetooth,ideapad_laptop,cfg80211
crc16                  16384  2 bluetooth,ext4


```
First we unload the module from the running system if it is loaded.

```

# modprobe -r module_name         
```Then simply run:
```
# echo "blacklist module_name" >> /etc/modprobe.d/local-dontload.conf  
```

---

### Post by HermanAB on 2022-06-07
&#128514;

---

### Post by wyattwhiteeagle on 2022-06-08
dpkg -l includes only the following...everything else has been purged...
```

ii  libbluetooth3:amd64 5.64-0ubuntu1 amd64		Lib to use BlueZ Linux Bluetooth stack
rc  libkf5bluezqt-data 5.92.0-0ubuntu1 all		data files for bluez-qt

```
lsmod | grep bluetooth (Qterminal prints nothing)
```

wyatt@wyatt-latitudee5400:~$ lsmod | grep bluetooth
wyatt@wyatt-latitudee5400:~$ 

```
lsmod (bluetooth doesn't appear in the list)
```

Module                  Size  Used by
ccm                    20480  9
dell_rbtn              20480  0
snd_hda_codec_hdmi     73728  1
snd_hda_codec_idt      61440  1
snd_hda_codec_generic   102400  1 snd_hda_codec_idt
dell_laptop            32768  0
dell_wmi               20480  1 dell_laptop
snd_hda_intel          53248  3
iwldvm                294912  0
snd_intel_dspcfg       28672  1 snd_hda_intel
snd_intel_sdw_acpi     20480  1 snd_intel_dspcfg
snd_hda_codec         155648  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_idt
input_leds             16384  0
serio_raw              20480  0
joydev                 32768  0
ledtrig_audio          16384  3 snd_hda_codec_generic,dell_wmi,dell_laptop
mac80211             1228800  1 iwldvm
snd_hda_core          110592  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_idt
libarc4                16384  1 mac80211
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               139264  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
dell_smm_hwmon         24576  0
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            49152  1 snd_seq_midi
coretemp               24576  0
iwlwifi               446464  1 iwldvm
pcmcia                 73728  0
snd_seq                73728  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              40960  2 snd_seq,snd_pcm
dell_smbios            28672  2 dell_wmi,dell_laptop
snd                   102400  17 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_pcm,snd_hda_codec_idt,snd_rawmidi
kvm_intel             364544  0
dcdbas                 20480  1 dell_smbios
yenta_socket           49152  0
kvm                  1003520  1 kvm_intel
pcmcia_rsrc            24576  1 yenta_socket
soundcore              16384  1 snd
dell_wmi_descriptor    20480  2 dell_wmi,dell_smbios
sparse_keymap          16384  1 dell_wmi
wmi_bmof               16384  0
pcmcia_core            28672  3 pcmcia,pcmcia_rsrc,yenta_socket
cfg80211              958464  3 iwldvm,iwlwifi,mac80211
at24                   24576  0
mac_hid                16384  0
sch_fq_codel           20480  6
ipmi_devintf           20480  0
ipmi_msghandler       122880  1 ipmi_devintf
msr                    16384  0
parport_pc             49152  0
ppdev                  24576  0
lp                     28672  0
parport                65536  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               53248  1 ip_tables
autofs4                49152  2
btrfs                1527808  0
blake2b_generic        20480  0
xor                    24576  1 btrfs
zstd_compress         229376  1 btrfs
raid6_pq              122880  1 btrfs
libcrc32c              16384  1 btrfs
dm_mirror              24576  0
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
hid_logitech_hidpp     49152  0
hid_logitech_dj        28672  0
i915                 3043328  13
gpio_ich               16384  0
hid_generic            16384  0
i2c_algo_bit           16384  1 i915
ttm                    86016  1 i915
drm_kms_helper        307200  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            20480  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
cec                    61440  2 drm_kms_helper,i915
rc_core                65536  1 cec
usbhid                 65536  1 hid_logitech_dj
drm                   606208  12 drm_kms_helper,i915,ttm
hid                   147456  4 usbhid,hid_generic,hid_logitech_dj,hid_logitech_hidpp
firewire_ohci          49152  0
sdhci_pci              65536  0
cqhci                  36864  1 sdhci_pci
firewire_core          77824  1 firewire_ohci
lpc_ich                28672  0
crc_itu_t              16384  1 firewire_core
sdhci                  81920  1 sdhci_pci
psmouse               176128  0
ahci                   45056  1
i2c_i801               36864  0
libahci                45056  1 ahci
i2c_smbus              20480  1 i2c_i801
tg3                   192512  0
wmi                    32768  4 dell_wmi,wmi_bmof,dell_smbios,dell_wmi_descriptor
video                  53248  3 dell_wmi,dell_laptop,i915

```

---

### Post by wyattwhiteeagle on 2022-06-08
ok...
something I am unaware of has happened.

I used to see one item in dpkg -l bearing within the name "bluetooth : pulseaudio".
Now it isn't there.

Yet I still have the youtube video sounds through pulseaudio.

I'm not sure what happened.
I guess a few things went through some changes in the recent updates and full-upgrades.

---

### Post by HermanAB on 2022-06-08
Well, pulseaudio is a sound server.  It will work whether BT is there or not.  Since your concern is with BT, just kill it and leave Pulseaudio alone.

---

