---
title: "Problem with /etc/rc.local"
date: 2007-10-21
forum: General Help
---

### Post by bofphile on 2007-10-21
Hi,

I've tried to add a command to /etc/rc.local to change some settings regarding cpu frequency scaling but it doesn't work, here is my file:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo 80 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold
exit 0
```

This file is owned by roots and is executable. What could be the problem ?

Thanks.

---

### Post by bofphile on 2007-10-25
Bump. :)

---

### Post by -Zeus- on 2007-10-25
try this

[php]sudo echo 80 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold[/php]

---

### Post by nick_h on 2007-10-25
Commands in /etc/rc.local are run as root.  The OP could try adding a simple debug in the file such as:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold > file.log
```

---

### Post by bofphile on 2007-10-25
Here's the output of my file.log:
```
31
```

This is the default value. Apparently the command doesn't work but I have no idea why. :confused:

---

### Post by nick_h on 2007-10-25
I assume you placed the debug after the command used to set the value.

Does it work at the command line?

---

### Post by bofphile on 2007-10-26
I put it like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo 80 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold
cat /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold > file.log
exit 0

```

There's no file log created but it works at the command line. It seems like my /etc/rc.local doesn't execute any command at all.

---

### Post by nick_h on 2007-10-26
What do you get from:
```
ls -l /etc/rc.local
```
?

---

### Post by bofphile on 2007-10-26
This is what I get:
```
-rwxr-xr-x 1 root root 449 2007-10-26 12:04 /etc/rc.local

```

---

### Post by alastair on 2007-10-26
And if you look to see if rc.local is linked to run :

```
find /etc/rc* -name '*local*'
```

Output?

---

### Post by bofphile on 2007-10-27
I got this:
```
/etc/rc2.d/S99rc.local
/etc/rc3.d/S99rc.local
/etc/rc4.d/S99rc.local
/etc/rc5.d/S99rc.local
/etc/rc.local

```

---

### Post by nick_h on 2007-10-27
That's also what I get.  The first 4 are just symbolic links to /etc/init.d/rc.local - does this file exist?

---

### Post by bofphile on 2007-10-27
Yes the file exists.

---

### Post by bofphile on 2007-10-31
Thanks nick-h for trying to help me with my problem. Do you know where someone could help me with this issue besides this forum ?

---

### Post by nick_h on 2007-10-31
Didn't you get it working?

If not the next step would be to check the links are OK with:
```
find /etc/rc* -name '*local*' -exec ls -l '{}' \;
```

and then perhaps put a debug in /etc/init.d/rc.local

Another option for help is the IRC channel, #ubuntu on irc.freenode.net - I suggest you use xchat as a client:
```
sudo apt-get install xchat-gnome
```

This is set up to take you into the Ubuntu support channel by default when you start it.

---

### Post by digitalbenji on 2007-10-31
I think there is an easier way to do what you want, check out my thread:
[HowTo: Configure Cpu Frequency Scaling for Celeron M's with Control of the Governors]("http://ubuntuforums.org/showthread.php?t=582069")

---

### Post by bofphile on 2007-10-31
> **nick_h said:**
> Didn't you get it working?

If not the next step would be to check the links are OK with:
```
find /etc/rc* -name '*local*' -exec ls -l '{}' \;
```

and then perhaps put a debug in /etc/init.d/rc.local

Another option for help is the IRC channel, #ubuntu on irc.freenode.net - I suggest you use xchat as a client:
```
sudo apt-get install xchat-gnome
```

This is set up to take you into the Ubuntu support channel by default when you start it.

I checked the links and they are fine:

```
lrwxrwxrwx 1 root root 18 2007-10-01 21:26 /etc/rc2.d/S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root 18 2007-10-01 21:26 /etc/rc3.d/S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root 18 2007-10-01 21:26 /etc/rc4.d/S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root 18 2007-10-01 21:26 /etc/rc5.d/S99rc.local -> ../init.d/rc.local

```

How can I put a debug in /etc/init.d/rc.local ?

Thanks

---

### Post by bofphile on 2007-10-31
> **digitalbenji said:**
> I think there is an easier way to do what you want, check out my thread:
[HowTo: Configure Cpu Frequency Scaling for Celeron M's with Control of the Governors]("http://ubuntuforums.org/showthread.php?t=582069")

I've already tried this method and unfortunately it doesn't work either. My up_threshold stays the same (31).

---

### Post by nick_h on 2007-10-31
> **bofphile said:**
> How can I put a debug in /etc/init.d/rc.local ?

Edit it with:
```
gksudo gedit /etc/init.d/rc.local
```
and add a line like:
```
echo "Running /etc/init.d/rc.local" > /home/user/test.log
```
Remove it again after the test.

---

### Post by bofphile on 2007-10-31
That's what I get in the debug file:
```
Running /etc/init.d/rc.local
```

---

### Post by nick_h on 2007-10-31
OK good.  Remove that debug and put one in /etc/rc.local

/etc/rc.local is run from /etc/init.d/rc.local if it exists and is executable.

---

### Post by bofphile on 2007-10-31
This is what I got:
```
Running /etc/rc.local
```

when I put the debug test:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo 80 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold
echo "Running /etc/rc.local" > /home/chakib/test.log
exit 0
```

---

### Post by bingoUV on 2007-10-31
but still the value in the file is not 80? Maybe the cpufreq module is not loaded at the time this command is run? Can you modify your script slightly thus, and reboot?
```

echo 80 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold
echo $? > /home/chakib/test.log
echo "Running /etc/rc.local" >> /home/chakib/test.log
lsmod >> /home/chakib/test.log
cat /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold >> /home/chakib/test.log
exit 0

```

The $? is to check whether previous command (echo) succeeded or not.

---

### Post by bofphile on 2007-11-01
Here's what I've got with your modifications:
```
0
Running /etc/rc.local
Module                  Size  Used by
binfmt_misc            12936  1 
nfsd                  220912  13 
exportfs                7040  1 nfsd
lockd                  67592  2 nfsd
sunrpc                172412  8 nfsd,lockd
ppdev                  10244  0 
button                  8976  0 
container               5504  0 
dock                   10656  0 
video                  18060  0 
sbs                    19592  0 
battery                11012  0 
ac                      6148  0 
powernow_k8            16960  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  1 
cpufreq_stats           7232  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_hda_intel         263712  0 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
ipv6                  273892  14 
sg                     36764  0 
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
joydev                 11328  0 
snd_rawmidi            25728  1 snd_seq_midi
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
sd_mod                 30336  0 
rc80211_simple          6912  1 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
lmpcm_usb               7168  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fglrx                1487340  12 
psmouse                39952  0 
rt2500pci              19072  0 
rt2x00pci              11520  1 rt2500pci
rt2x00lib              19584  2 rt2500pci,rt2x00pci
rfkill                  8208  2 rt2x00lib
i2c_ali1535             8196  0 
pcmcia                 41388  0 
snd                    54660  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
mac80211              171016  4 rc80211_simple,rt2500pci,rt2x00pci,rt2x00lib
i2c_ali15x3             9092  0 
serio_raw               8068  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
cfg80211                7304  1 mac80211
pcspkr                  4224  0 
i2c_core               26112  2 i2c_ali1535,i2c_ali15x3
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
k8temp                  6656  0 
tifm_7xx1               8576  0 
tifm_core              11268  1 tifm_7xx1
uli526x                17556  0 
eeprom_93cx6            3200  1 rt2500pci
ati_agp                10124  0 
sdhci                  18828  0 
mmc_core               28420  1 sdhci
agpgart                35016  2 fglrx,ati_agp
shpchp                 34580  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
pci_hotplug            32704  1 shpchp
evdev                  11136  5 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  4 
ata_generic             8452  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
usb_storage            73024  0 
libusual               18448  1 usb_storage
ehci_hcd               36492  0 
sata_uli                8452  0 
libata                125168  2 ata_generic,sata_uli
scsi_mod              147084  5 sbp2,sg,sd_mod,usb_storage,libata
alim15x3               12556  0 [permanent]
ide_core              116804  4 ide_cd,ide_disk,usb_storage,alim15x3
ohci_hcd               22916  0 
usbcore               138632  7 lmpcm_usb,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
80
```

---

### Post by nick_h on 2007-11-01
It looks like it's working now.

The result code from the echo command was 0 = success.
The cpufreq_ondemand module was loaded.
The cat command shows that the value was still 80 at the end of rc.local

---

### Post by bofphile on 2007-11-01
Unfortunately, it's still not working:
```
chakib@turion:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold 
31

```

---

### Post by nick_h on 2007-11-02
It looks like it was set in the /etc/rc.local file but something is setting it back later.

---

