---
title: "Worrying messages in syslog"
date: 2014-10-11
forum: General Help
---

### Post by shane84 on 2014-10-11
I recently installed Ubuntu 14.04. Today, I found some scary looking messages in syslog. I wanted to know if they are a cause for worry. 

```

ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
ACPI: Battery Slot [BAT1] (battery present)

```

My battery is running fine, and when using Unity, the battery status is being displayed correctly and there is nothing unusual about the amount of battery charge left that is being displayed.

Here is another error:

```

<warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wifi: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.62': no such name

ModemManager[719]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.2': not s
upported by any plugin

```

Again, my wireless internet is working absolutely fine. 

```

[    8.661313] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[    8.661329] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver


```

Are these huge number of messages in syslog normal, or is there something to worry about? I ran a sensors-detect but with only the safe and mostly default options; could that have created trouble? I have not noticed any issues with my laptop, otherwise. Just that these errors seem scary and I am hoping it does not mean that there will be trouble in future. 

I am using an HP Pavillion m6. I am not sure if you will need this:

```

lsmod 
Module                  Size  Used by
nls_iso8859_1          12713  0 
usb_storage            62209  0 
ctr                    13049  2 
ccm                    17773  2 
rfcomm                 69160  8 
bnep                   19624  2 
binfmt_misc            17468  1 
snd_hda_codec_hdmi     46254  1 
snd_hda_codec_idt      54645  1 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
snd_hda_intel          52355  3 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
arc4                   12608  2 
kvm                   451511  0 
iwldvm                232285  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
hp_wmi                 14062  0 
ghash_clmulni_intel    13216  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
aesni_intel            55624  4 
mac80211              630653  1 iwldvm
sparse_keymap          13948  1 hp_wmi
i915                  783805  3 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17381  0 
gf128mul               14951  1 lrw
rtsx_pci_ms            18151  0 
snd_rawmidi            30144  1 snd_seq_midi
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
btusb                  32412  0 
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
iwlwifi               169932  1 iwldvm
bluetooth             391196  22 bnep,btusb,rfcomm
memstick               16966  1 rtsx_pci_ms
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
hp_accel               26012  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
drm_kms_helper         53081  1 i915
drm                   303102  4 i915,drm_kms_helper
lis3lv02d              20156  1 hp_accel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
mei_me                 18627  0 
snd                    69238  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lpc_ich                21080  0 
input_polldev          13896  1 lis3lv02d
wmi                    19177  1 hp_wmi
soundcore              12680  1 snd
mei                    82276  1 mei_me
i2c_algo_bit           13413  1 i915
video                  19476  1 i915
intel_smartconnect     12619  0 
serio_raw              13462  0 
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         23274  0 
ahci                   25819  2 
psmouse               106678  0 
r8169                  67581  0 
mii                    13934  1 r8169
libahci                32560  1 ahci
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc

```

Thanks a lot!

---

### Post by tgalati4 on 2014-10-11
Because Ubuntu (and Linux in general) supports a wide, wide range of hardware, there are lots of error and warning messages when booting.  You only need to be concerned when something is not working the way you expect.  Then you can do a forum search or a google search on the specific warning/error message to get more details on the issue.

I wouldn't worry about it.  Sensors-detect is generally safe.  Since it is poking values into support chips, it is possible that it may lock up your system while testing, but I have never heard of hardware damage from it.  The purpose of poking these chips is to return fan, temperature, and voltage data.  If sensors-detect gets a successful hit, it will remember that and prompt you to load that specific module in the future.

---

### Post by oldos2er on 2014-10-12
Moved to General Help.

---

### Post by grahammechanical on 2014-10-12
Some old sayings.

What you don't know, don't hurt you.
A little knowledge is dangerous thing.
Don't fix what ain't broke.
Don't go looking for trouble. It will find you.

You had a good install experience. You have a working OS of an awesome Linux distribution. You are yet to discover the potential in Linux to really scare the user. Be happy.

Regards.

---

