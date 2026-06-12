---
title: "Not resuming from suspend"
date: 2017-02-05
forum: General Help
---

### Post by NertSkull on 2017-02-05
I'm using sudo pm-suspend and my computer used to resume from it (most of the time).

But lately every time I suspend, it supsends fine. But when I turn back on, the computer will power on. But then just hang at a black screen.

Here is the pm-suspend.log

```
Sat Feb  4 21:28:01 EST 2017: Running hooks for suspend.Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux oak 3.19.0-78-generic #86~14.04.1-Ubuntu SMP Tue Dec 6 17:58:35 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
hid_dr                 16384  0 
ff_memless             16384  1 hid_dr
rpcsec_gss_krb5        36864  0 
nfsv4                 471040  1 
ip6table_filter        16384  0 
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  0 
ip_tables              28672  1 iptable_filter
x_tables               36864  4 ip6table_filter,ip_tables,iptable_filter,ip6_tables
pci_stub               16384  1 
vboxpci                24576  0 
vboxnetadp             28672  0 
vboxnetflt             28672  0 
vboxdrv               450560  3 vboxnetadp,vboxnetflt,vboxpci
rfcomm                 69632  0 
bnep                   20480  2 
bluetooth             491520  10 bnep,rfcomm
nfsd                  299008  2 
binfmt_misc            20480  1 
auth_rpcgss            61440  2 nfsd,rpcsec_gss_krb5
nfs_acl                16384  1 nfsd
nfs                   245760  8 nfsv4
lockd                  94208  2 nfs,nfsd
grace                  16384  2 nfsd,lockd
sunrpc                327680  20 nfs,nfsd,rpcsec_gss_krb5,auth_rpcgss,lockd,nfsv4,nfs_acl
fscache                65536  2 nfs,nfsv4
nls_iso8859_1          16384  1 
snd_hda_codec_hdmi     53248  1 
snd_hda_codec_realtek    81920  1 
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
i915_bpo             1138688  0 
intel_ips              20480  1 i915_bpo
i2c_algo_bit           16384  1 i915_bpo
snd_hda_intel          40960  5 
snd_hda_codec         139264  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
joydev                 20480  0 
snd_hwdep              20480  1 snd_hda_codec
eeepc_wmi              16384  0 
asus_wmi               24576  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0 
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
x86_pkg_temp_thermal    16384  0 
coretemp               16384  0 
kvm_intel             151552  0 
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
kvm                   479232  1 kvm_intel
dm_multipath           24576  0 
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
scsi_dh                16384  1 dm_multipath
snd_timer              32768  2 snd_pcm,snd_seq
snd                    86016  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
serio_raw              16384  0 
soundcore              16384  1 snd
mac_hid                16384  0 
i2c_hid                20480  0 
acpi_pad               20480  0 
wmi                    20480  2 mxm_wmi,asus_wmi
shpchp                 40960  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
dm_crypt               24576  1 
dm_mirror              24576  0 
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  4 i2c_hid,hid_dr,hid_generic,usbhid
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
nvidia_drm             45056  1 
nvidia_modeset        765952  5 nvidia_drm
aesni_intel           172032  2 
drm_kms_helper        131072  2 i915_bpo,nvidia_drm
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
drm                   344064  5 i915_bpo,drm_kms_helper,nvidia_drm
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 aesni_intel,ablk_helper
e1000e                237568  0 
psmouse               118784  0 
nvidia              11489280  73 nvidia_modeset
ptp                    20480  1 e1000e
pps_core               20480  1 ptp
nvme                   61440  4 
ahci                   36864  5 
libahci                32768  1 ahci
video                  20480  2 i915_bpo,asus_wmi
             total       used       free     shared    buffers     cached
Mem:      16351892   12797000    3554892     185028    2068844    5113512
-/+ buffers/cache:    5614644   10737248
Swap:     16670716        156   16670560
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Sat Feb  4 21:28:02 EST 2017: performing suspend


```

I notice there is an error in there for wpa_supplicant. Which I believe is for wireless cards.  This computer has NO wireless card. It is ethernet only.  Could that be my problem?  Is there a way to fix this?

I also sometimes open the logs and get a 'invalid characters' error from my editor and see the little white boxes (or @ in vim) where it can't read the characters.

---

