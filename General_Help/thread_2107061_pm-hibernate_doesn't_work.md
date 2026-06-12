---
title: "pm-hibernate doesn't work"
date: 2013-01-20
forum: General Help
---

### Post by taninamdar on 2013-01-20
Hi,
I have Kubuntu 12.04 and I have 4 GB RAM. Earlier I had 2 GB swap space and it used to work fine for hibernation (using pm-hibernate) except when I had many applications running and I tried to hibernate. It used to show not enough swap space.
So I figured I should increase swap, so I shifted it from sda5 to sda7 and expanded to 4 GB. However, now pm-hibernate does not work. When I use it, the display goes blank for a fraction of a second and comes back to where I was working on.

I'm pasting contents of /etc/fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=a79f2d70-17fd-4e2d-887b-ac3dc5d2b1c2 /               ext4    errors=remount-ro 0       1

/dev/sda7 none swap sw 0 0


If that helps.
Thanks in advance. :D

---

### Post by Toz on 2013-01-20
Your initramfs needs to know the correct UUID of your new swap file. The file: /etc/initramfs-tools/conf.d/resume should contain the new UUID. See [here]("https://help.ubuntu.com/community/UsingUUID#Resuming_from_Hibernation") for more info. You can get the UUID of your swap file by running:
```
sudo blkid
```

The hibernate log file is located at /var/log/pm-suspend.log - it may contain some relevant diagnostic information.

---

### Post by taninamdar on 2013-01-21
I changed the UUID in the file you specified to my current UUID. Still the problem persists.
Here is the last few part of the log in the cat /var/log/pm-suspend.log file, I cannot upload as the total size of log is huge.
 Here is the last part:


```
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Mon Jan 21 20:20:19 IST 2013: Finished.
Initial commandline parameters: 
Mon Jan 21 20:22:27 IST 2013: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux tan-laptop 3.2.0-36-generic-pae #57-Ubuntu SMP Tue Jan 8 22:01:06 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
uas                    17828  0 
usb_storage            39646  1 
joydev                 17393  0 
snd_hda_codec_hdmi     31775  1 
rfcomm                 38139  16 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
btusb                  17948  1 
bluetooth             158479  23 rfcomm,bnep,btusb
binfmt_misc            17292  1 
arc4                   12473  2 
snd_hda_codec_idt      60251  1 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_intel          32765  6 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                86520  0 
serio_raw              13027  0 
intel_ips              17822  0 
iwlwifi               366524  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
mac80211              436493  1 iwlwifi
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2909978  99 
cfg80211              178877  2 iwlwifi,mac80211
snd                    62218  21 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mei                    36570  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13516  1 
usbhid                 41937  0 
hid                    77428  1 usbhid
r8169                  56368  0 
video                  19068  0 
wmi                    18744  1 dell_wmi
             total       used       free     shared    buffers     cached
Mem:       3982988    1411044    2571944          0      71088     646692
-/+ buffers/cache:     693264    3289724
Swap:      4225056          0    4225056

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Selected interface 'wlan0'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
ATI Catalyst driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Mon Jan 21 20:22:29 IST 2013: performing hibernate
s2disk: Could not stat the resume device file. Reason: No such file or directory
Mon Jan 21 20:22:29 IST 2013: Awake.
Mon Jan 21 20:22:29 IST 2013: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Selected interface 'wlan0'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Mon Jan 21 20:22:31 IST 2013: Finished.

```

---

### Post by Toz on 2013-01-21
> **taninamdar said:**
> s2disk: Could not stat the resume device file. Reason: No such file or directory

Are you using s2disk (uswsusp) to hibernate? 
```
apt-cache policy uswsusp
```

If so, can you check for the existence of either of these files:
- /etc/uswsusp.conf
- /usr/share/initramfs-tools/conf.d/uswsusp
...and post back their contents. (If there is a reference to a resume partition there, it should be changed to match).

Also, is there a **resume=** parameter on your kernel boot line?
```
cat /proc/cmdline
```
...will show you your current kernel boot line

And, make sure you run:
```
sudo update-initramfs -u
```
...to rebuild the initramfs after any of these changes, then reboot.

---

### Post by taninamdar on 2013-01-22
> 
Are you using s2disk (uswsusp) to hibernate?

Nope. I use pm-hibernate.
Output of s2disk was:
```
s2disk: Could not lock myself. Reason: Cannot allocate memory
```

Also, about the two files,
```

tan@tan-laptop:~$ cat /etc/uswsusp.conf
cat: /etc/uswsusp.conf: No such file or directory

tan@tan-laptop:~$ cat /usr/share/initramfs-tools/conf.d/uswsusp
# When bug 376393 gets fixed this will setup non-us keyboards in
# early userspace, necessary for punching in passphrases.
KEYMAP=y

tan@tan-laptop:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-36-generic-pae root=UUID=a79f2d70-17fd-4e2d-887b-ac3dc5d2b1c2 ro quiet splash vt.handoff=7



```

---

### Post by Toz on 2013-01-22
Is it installed?
```
apt-cache policy uswsusp
```

Try adding **RESUME=UUID=<swap_UUID>** (change <swap_UUID> to be the actually UUID of the swap partition) to /usr/share/initramfs-tools/conf.d/uswsusp as per the instructions [here]("https://help.ubuntu.com/community/UsingUUID#Resuming_from_Hibernation"). Remember to run:
```
sudo update-initramfs -u
```
...afterwards.

---

### Post by taninamdar on 2013-01-23
Yes, uswsusp is installed.
```

tan@tan-laptop:~$ apt-cache policy uswsusp 
uswsusp:
  Installed: 1.0+20110509-2ubuntu1
  Candidate: 1.0+20110509-2ubuntu1
  Version table:
 *** 1.0+20110509-2ubuntu1 0
        500 http://in.archive.ubuntu.com/ubuntu/ precise/universe i386 Packages
        100 /var/lib/dpkg/status

```
Still the problem persists even after adding UUID in /etc/initramfs-tools/conf.d/resume
:(

---

### Post by Toz on 2013-01-23
> **taninamdar said:**
> Yes, uswsusp is installed.
```

tan@tan-laptop:~$ apt-cache policy uswsusp 
uswsusp:
  Installed: 1.0+20110509-2ubuntu1
  Candidate: 1.0+20110509-2ubuntu1
  Version table:
 *** 1.0+20110509-2ubuntu1 0
        500 http://in.archive.ubuntu.com/ubuntu/ precise/universe i386 Packages
        100 /var/lib/dpkg/status

```
Still the problem persists even after adding UUID in /etc/initramfs-tools/conf.d/resume
:(

Just to confirm, did you run "sudo update-initramfs -u" afterwards?

Can you post back the contents of  /usr/share/initramfs-tools/conf.d/uswsusp and the results of:
```
sudo blkid
```

And what does the following return:
```
sudo debconf-show uswsusp
```

---

### Post by taninamdar on 2013-01-24
Yes, I did run it after execution of those commands.
Here's the output of commands which you said:
```

tan@tan-laptop:~$ cat  /usr/share/initramfs-tools/conf.d/uswsusp
# When bug 376393 gets fixed this will setup non-us keyboards in
# early userspace, necessary for punching in passphrases.
KEYMAP=y
RESUME=UUIT=79e4705f-8d08-4b1d-b1e2-f29c03ed541e
tan@tan-laptop:~$ sudo blkid
[sudo] password for tan: 
/dev/sda1: LABEL="System Reserved" UUID="5E2ABE072ABDDBE9" TYPE="ntfs" 
/dev/sda2: UUID="BAA0C8BBA0C87EFF" TYPE="ntfs" 
/dev/sda3: UUID="a79f2d70-17fd-4e2d-887b-ac3dc5d2b1c2" TYPE="ext4" 
/dev/sda5: LABEL="Torrents" UUID="01CDE50C17847F60" TYPE="ntfs" 
/dev/sda6: LABEL="Files" UUID="01CDE50C1ADFDF60" TYPE="ntfs" 
/dev/sda7: UUID="79e4705f-8d08-4b1d-b1e2-f29c03ed541e" TYPE="swap" 
/dev/sdb1: UUID="F42C-B520" TYPE="vfat" 
tan@tan-laptop:~$ sudo debconf-show uswsusp 
  uswsusp/RSA_passphrase: (password omitted)
  uswsusp/RSA_passphrase_v: (password omitted)
  uswsusp/compress: true
  uswsusp/compute_checksum: false
  uswsusp/create_RSA_key: false
  uswsusp/no_snapshot:
  uswsusp/snapshot_device:
  uswsusp/suspend_loglevel:
  uswsusp/RSA_key_file: /etc/uswsusp.key
* uswsusp/no_swap:
  uswsusp/max_loglevel:
  uswsusp/resume_device:
  uswsusp/resume_offset:
  uswsusp/shutdown_method: platform
  uswsusp/encrypt: false
  uswsusp/splash: true
  uswsusp/early_writeout: true
  uswsusp/image_size: 1876146667
  uswsusp/RSA_key_bits: 1024
* uswsusp/continue_without_swap: false
```

---

### Post by Toz on 2013-01-24
You have a typo:
> tan@tan-laptop:~$ cat  /usr/share/initramfs-tools/conf.d/uswsusp
# When bug 376393 gets fixed this will setup non-us keyboards in
# early userspace, necessary for punching in passphrases.
KEYMAP=y
RESUME=[COLOR="Red"]UUIT[/COLOR]=79e4705f-8d08-4b1d-b1e2-f29c03ed541e
..it should be "UUI**D**".

Make the change, run:
```
sudo update-initramfs -u
```
...again. Reboot. Then post back again the results of:
```
sudo debconf-show uswsusp
```

---

### Post by taninamdar on 2013-01-25
```
tan@tan-laptop:~$ sudo debconf-show uswsusp 
  uswsusp/RSA_passphrase: (password omitted)
  uswsusp/RSA_passphrase_v: (password omitted)
  uswsusp/compress: true
  uswsusp/compute_checksum: false
  uswsusp/create_RSA_key: false
  uswsusp/no_snapshot:
  uswsusp/snapshot_device:
  uswsusp/suspend_loglevel:
  uswsusp/RSA_key_file: /etc/uswsusp.key
* uswsusp/no_swap:
  uswsusp/max_loglevel:
  uswsusp/resume_device:
  uswsusp/resume_offset:
  uswsusp/shutdown_method: platform
  uswsusp/encrypt: false
  uswsusp/splash: true
  uswsusp/early_writeout: true
  uswsusp/image_size: 1876146667
  uswsusp/RSA_key_bits: 1024
* uswsusp/continue_without_swap: false

```

---

### Post by Toz on 2013-01-25
> uswsusp/resume_device:

It's not being recognized. Try this instead:

**/usr/share/initramfs-tools/conf.d/uswsusp**
Change the line to read:
```
RESUME=/dev/sda7
```

Run:
```
sudo update-initramfs -u
```

Reboot.

Again post back:
```
sudo debconf-show uswsusp
```
...and see if its recognized. It should say:
> uswsusp/resume_device: /dev/sda7

---

### Post by taninamdar on 2013-01-25
Done that, and:
```
tan@tan-laptop:~$ sudo debconf-show uswsusp 
[sudo] password for tan: 
  uswsusp/RSA_passphrase: (password omitted)
  uswsusp/RSA_passphrase_v: (password omitted)
  uswsusp/compress: true
  uswsusp/compute_checksum: false
  uswsusp/create_RSA_key: false
  uswsusp/no_snapshot:
  uswsusp/snapshot_device:
  uswsusp/suspend_loglevel:
  uswsusp/RSA_key_file: /etc/uswsusp.key
* uswsusp/no_swap:
  uswsusp/max_loglevel:
  uswsusp/resume_device:
  uswsusp/resume_offset:
  uswsusp/shutdown_method: platform
  uswsusp/encrypt: false
  uswsusp/splash: true
  uswsusp/early_writeout: true
  uswsusp/image_size: 1876146667
  uswsusp/RSA_key_bits: 1024
* uswsusp/continue_without_swap: false

```

---

### Post by Toz on 2013-01-25
Hmmmm.

A few other suggestions to try:

1. add **resume=/dev/sda7** to the kernel boot line.
2. run "sudo dpkg-reconfigure uswsusp" and answer all the questions as in the results from (sudo debconf-show uswsusp) except the "resume device" question (answer /dev/sda7)
3. Uninstall purge (sudo apt-get purge uswsusp) and resinstall uswsusp (sudo apt-get install uswsusp). 

See if one of those methods can get uswsusp to pick up the new swap.

---

### Post by taninamdar on 2013-01-25
> **Toz said:**
> 

1. add **resume=/dev/sda7** to the kernel boot line.
2. run "sudo dpkg-reconfigure uswsusp" and answer all the questions as in the results from (sudo debconf-show uswsusp) except the "resume device" question (answer /dev/sda7)

Umm, sorry if I sound noobish, but can you explain how to do the things mentioned in those two steps? :)

---

### Post by taninamdar on 2013-01-25
I tried running "sudo dpkg-reconfigure uswsusp", but it asks about the swapping options, doesn't ask about the swap partition itself.

Also, idk if this is related or not, but I was checking the /dev/sda7 from the kde partition manager if I can figure out something from there, and I found that the partition showed status as 'mounted'. The swap partition shouldn't be mounted as far as I know, right? Maybe this could help...  :neutral:

UPDATE:
I tried these 3 commands as sudo:
```

sudo swapoff /dev/sda7
sudo mkswap /dev/sda7
sudo swapon /dev/sda7

```After that, I tried
```
sudo pm-hibernate
```It did make a swap image (or whatever you call it) to /dev/sda7 and successfully hibernated, but when I tried to resume again, it showed with kde splash screen saying "resuming from /dev/sda7" for some time, but afterwards it booted normally, and the state when I hibernated was not restored.

UPDATE #2:
After 'rebooting' (unsuccessfully resuming from hibernate), I again tried running sudo pm-hibernate. But strangely, it again gave the earlier symptoms (screen going blank for a fraction of a second and coming back to where it was without hibernating). Then I again ran following commands:
```

[B]tan@tan-laptop:~$ sudo swapoff /dev/sda7
[sudo] password for tan: 
swapoff: /dev/sda7: swapoff failed: Invalid argument[/B]

tan@tan-laptop:~$ sudo mkswap /dev/sda7
Setting up swapspace version 1, size = 4225056 KiB
no label, UUID=71ee561d-3018-46df-ac01-3b27834467c2

tan@tan-laptop:~$ sudo swapon /dev/sda7

```
So I guess, across the reboots, the information about which is the swap partition is being erased? I am not sure... :-?

---

### Post by Toz on 2013-01-26
On fresh boot, before running any swap commands, is the swap active?
```
swapon -s
```

What are the contents of your /etc/fstab file?

---

### Post by taninamdar on 2013-01-26
```
tan@tan-laptop:~$ swapon -s
Filename                                Type            Size    Used    Priority
tan@tan-laptop:~$ 
```

---

### Post by Toz on 2013-01-26
> **taninamdar said:**
> ```
tan@tan-laptop:~$ swapon -s
Filename                                Type            Size    Used    Priority
tan@tan-laptop:~$ 
```

No swap file on boot. What are the contents of **/etc/fstab**?

---

### Post by taninamdar on 2013-01-26
> **Toz said:**
> No swap file on boot. What are the contents of **/etc/fstab**?

```
tan@tan-laptop:~$ sudo cat /etc/fstab
[sudo] password for tan: 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=a79f2d70-17fd-4e2d-887b-ac3dc5d2b1c2 /               ext4     errors=remount-ro       1

UUID=79e4705f-8d08-4b1d-b1e2-f29c03ed541e none swap sw 0 0

```

---

### Post by Toz on 2013-01-26
Try changing the UUID value of the swap file listing in /etc/fstab to the one that is generated when you run mkswap /dev/sda7 (UUID=71ee561d-3018-46df-ac01-3b27834467c2) and rebooting to see if you get an active swap on boot.

---

### Post by taninamdar on 2013-01-27
Did that and tried hibernating (Also ran  mkswaps /dev/sda7 and swapon /dev/sda7 as sudo and then tried hibernating. As before, it showed that it's writing on the swap partition, but when tried to resume, it showed "Resuming from /dev/sda7" and stuck there for 5 mins. So I force-closed and restarted the comp. :-?

---

### Post by Toz on 2013-01-27
> **taninamdar said:**
> (Also ran  mkswaps /dev/sda7 and swapon /dev/sda7 as sudo 
You shouldn't need to do that.

Reboot the computer and before you do anything, post back the results of:
```
swapon -s
```
...and
```
sudo debconf-show uswsusp
```
...and
```
cat /proc/cmdline
```
...and
```
sudo blkid
```

---

### Post by taninamdar on 2013-01-27
oops, sorry. Here's that:
```
tan@tan-laptop:~$ swapon -s
Filename                                Type            Size    Used    Priority
tan@tan-laptop:~$ sudo debconf-show uswsusp
[sudo] password for tan: 
  uswsusp/RSA_passphrase: (password omitted)
  uswsusp/RSA_passphrase_v: (password omitted)
* uswsusp/compress: true
* uswsusp/compute_checksum: false
  uswsusp/create_RSA_key: false
  uswsusp/no_snapshot:
* uswsusp/snapshot_device:
* uswsusp/suspend_loglevel:
  uswsusp/RSA_key_file: /etc/uswsusp.key
  uswsusp/no_swap:
* uswsusp/max_loglevel:
* uswsusp/resume_device: /dev/sda7
  uswsusp/resume_offset:
* uswsusp/shutdown_method: platform
* uswsusp/encrypt: false
* uswsusp/splash: true
* uswsusp/early_writeout: true
* uswsusp/image_size: 1876146667
  uswsusp/RSA_key_bits: 1024
* uswsusp/continue_without_swap: false
tan@tan-laptop:~$ cat /proc/cmdline 
BOOT_IMAGE=/boot/vmlinuz-3.2.0-36-generic-pae root=UUID=a79f2d70-17fd-4e2d-887b-ac3dc5d2b1c2 ro quiet splash
tan@tan-laptop:~$ sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="5E2ABE072ABDDBE9" TYPE="ntfs" 
/dev/sda2: UUID="BAA0C8BBA0C87EFF" TYPE="ntfs" 
/dev/sda3: UUID="a79f2d70-17fd-4e2d-887b-ac3dc5d2b1c2" TYPE="ext4" 
/dev/sda5: LABEL="Torrents" UUID="01CDE50C17847F60" TYPE="ntfs" 
/dev/sda6: LABEL="Files" UUID="01CDE50C1ADFDF60" TYPE="ntfs" 
/dev/sda7: UUID="3abf2b16-6ae0-430b-ae74-8656bb48cf34" TYPE="swap" 
```

---

### Post by Toz on 2013-01-27
Sorry, I should have also asked for:
```
cat /etc/fstab
```

Does the /etc/fstab swap UUID match up with the one being displayed with the "sudo blkid" command? Its odd that its not being reported with "swapon -s"

However, "sudo debconf-show uswsusp" is pointing to /dev/sda7 as the resume device. Try re-enabling the swap and see if it works.

---

### Post by taninamdar on 2013-01-28
```

tan@tan-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=a79f2d70-17fd-4e2d-887b-ac3dc5d2b1c2 /               ext4     errors=remount-ro       1

UUID=UUID=3abf2b16-6ae0-430b-ae74-8656bb48cf34 none swap sw 0 0
tan@tan-laptop:~$ sudo blkid
[sudo] password for tan: 
/dev/sda1: LABEL="System Reserved" UUID="5E2ABE072ABDDBE9" TYPE="ntfs" 
/dev/sda2: UUID="BAA0C8BBA0C87EFF" TYPE="ntfs" 
/dev/sda3: UUID="a79f2d70-17fd-4e2d-887b-ac3dc5d2b1c2" TYPE="ext4" 
/dev/sda5: LABEL="Torrents" UUID="01CDE50C17847F60" TYPE="ntfs" 
/dev/sda6: LABEL="Files" UUID="01CDE50C1ADFDF60" TYPE="ntfs" 
/dev/sda7: UUID="3abf2b16-6ae0-430b-ae74-8656bb48cf34" TYPE="swap"
```

See this. I didn't understand this part : "Try re-enabling the swap and see if it works."
Also, while googling, I found this, can it be relevant somehow?
[http://askubuntu.com/questions/246449/unable-to-resume-from-hibernation-on-boot-restarts-instead-of-resuming](http://askubuntu.com/questions/246449/unable-to-resume-from-hibernation-on-boot-restarts-instead-of-resuming)

---

### Post by Toz on 2013-01-28
> **taninamdar said:**
> ```

tan@tan-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=a79f2d70-17fd-4e2d-887b-ac3dc5d2b1c2 /               ext4     errors=remount-ro       1

UUID=UUID=3abf2b16-6ae0-430b-ae74-8656bb48cf34 none swap sw 0 0
tan@tan-laptop:~$ sudo blkid
[sudo] password for tan: 
/dev/sda1: LABEL="System Reserved" UUID="5E2ABE072ABDDBE9" TYPE="ntfs" 
/dev/sda2: UUID="BAA0C8BBA0C87EFF" TYPE="ntfs" 
/dev/sda3: UUID="a79f2d70-17fd-4e2d-887b-ac3dc5d2b1c2" TYPE="ext4" 
/dev/sda5: LABEL="Torrents" UUID="01CDE50C17847F60" TYPE="ntfs" 
/dev/sda6: LABEL="Files" UUID="01CDE50C1ADFDF60" TYPE="ntfs" 
/dev/sda7: UUID="3abf2b16-6ae0-430b-ae74-8656bb48cf34" TYPE="swap"
```
Everything matches up.

> See this. I didn't understand this part : "Try re-enabling the swap and see if it works."
I meant:
```
sudo swapon /dev/sda7
```

> Also, while googling, I found this, can it be relevant somehow?
[http://askubuntu.com/questions/246449/unable-to-resume-from-hibernation-on-boot-restarts-instead-of-resuming](http://askubuntu.com/questions/246449/unable-to-resume-from-hibernation-on-boot-restarts-instead-of-resuming)
Yes, I suggested this in post #14.

Maybe we can try this again from the top:
[LIST=1]
[*]Reboot the computer.
[*]Display the results of:
```
sudo debconf-show uswsusp
```
[*]Display the results of:
```
cat /proc/cmdline
```
[*]Display the results of:
```
sudo blkid
```
[*]Display the results of:
```
/etc/fstab
```
[*]Display the results of:
```
swapon -s
```
[/LIST]

If the results of the last command are blank, then run:
```
sudo swapon /dev/sda7
```

Then try hibernating.

---

### Post by taninamdar on 2013-02-03
```

tan@tan-laptop:~$ sudo debconf-show uswsusp
[sudo] password for tan: 
  uswsusp/RSA_passphrase: (password omitted)
  uswsusp/RSA_passphrase_v: (password omitted)
* uswsusp/compress: true
* uswsusp/compute_checksum: false
  uswsusp/create_RSA_key: false
  uswsusp/no_snapshot:
* uswsusp/snapshot_device:
* uswsusp/suspend_loglevel:
  uswsusp/RSA_key_file: /etc/uswsusp.key
  uswsusp/no_swap:
* uswsusp/max_loglevel:
* uswsusp/resume_device: /dev/sda7
  uswsusp/resume_offset:
* uswsusp/shutdown_method: platform
* uswsusp/encrypt: false
* uswsusp/splash: true
* uswsusp/early_writeout: true
* uswsusp/image_size: 1876146667
  uswsusp/RSA_key_bits: 1024
* uswsusp/continue_without_swap: false
tan@tan-laptop:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-37-generic-pae root=UUID=a79f2d70-17fd-4e2d-887b-ac3dc5d2b1c2 ro quiet splash vt.handoff=7

``````

tan@tan-laptop:~$ sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="5E2ABE072ABDDBE9" TYPE="ntfs" 
/dev/sda2: UUID="BAA0C8BBA0C87EFF" TYPE="ntfs" 
/dev/sda3: UUID="a79f2d70-17fd-4e2d-887b-ac3dc5d2b1c2" TYPE="ext4" 
/dev/sda5: LABEL="Torrents" UUID="01CDE50C17847F60" TYPE="ntfs" 
/dev/sda6: LABEL="Files" UUID="01CDE50C1ADFDF60" TYPE="ntfs" 
/dev/sda7: UUID="48188fd8-d7bb-404e-971d-4a3def1e426a" TYPE="swap" 

``````

tan@tan-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=a79f2d70-17fd-4e2d-887b-ac3dc5d2b1c2 /               ext4     errors=remount-ro       1

UUID=UUID=3abf2b16-6ae0-430b-ae74-8656bb48cf34 none swap sw 0 0

``````

tan@tan-laptop:~$ swapon -s
Filename                                Type            Size    UsedPriority

``````

tan@tan-laptop:~$ sudo swapon /dev/sda7

```Now trying to hibernate.

Edit:
sudo pm-hibernate successfully hibernated, but when tried to resume, it stuck on "resuming from /dev/sda7". Had to force close my laptop and restart.

---

### Post by Toz on 2013-02-03
The UUID from "blkid" and the one in your /etc/fstab file don't match. Change /etc/fstab swap line to read:
```
UUID=UUID=48188fd8-d7bb-404e-971d-4a3def1e426a none swap sw 0 0
```

Reboot.

Before anything, check to see that swap is now enabled:
```
swapon -s
```

If it is, try hibernating.

---

### Post by taninamdar on 2013-02-07
Well nothing was working, so after much of googling, I found that people solved this problem by removing "cryptsetup". I tried
```
sudo apt-get purge cryptsetup
```
And after that hibernation works successfully.
So, it was cryptsetup which was causing all the problems (though I don't know why).
So thanks a lot for paying attention to my thread and for helping me! ^___^ :D
Marking the thread as solved! Thanks again!

---

### Post by Toz on 2013-02-07
Interesting. Thanks for posting back the solution.

---

