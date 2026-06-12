---
title: "pm-hibernate (TuxOnIce) fails to resume"
date: 2013-08-22
forum: General Help
---

### Post by cthlhu1987 on 2013-08-22
I tried to install TuxOnIce to use pm-hibernate. It brought the system down, but it froze on "resuming from <disk uuid>". Can you help me, please?
[pm-suspend.log]("http://pastebin.com/hJypepzP")
[dmesg output]("http://pastebin.com/d3EFF4KN")
```
matatabisama@matatabisama-X6815:~$ uname -a
Linux matatabisama-X6815 3.8.0-30-generic #43-Ubuntu SMP Wed Aug 21 21:07:22 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Toz on 2013-08-23
Can you provide some more information? Specifically:

[LIST=1]
[*]The make and model of your notebook
[*]The amount of ram you have:
```
free -m
```
[*]Info about your swap drive:
```
swapon -s
```
[*]Why are you using tuxonice instead of the default kernel suspend/hibernate? Does the kernel method not work?
[*]The results of the following command:
```
cat /var/log/syslog | grep PM:
```
[*]
[/LIST]

---

### Post by cthlhu1987 on 2013-08-23
> **Toz said:**
> Can you provide some more information? Specifically:
[LIST=1]
[*]The make and model of your notebook
[*]The amount of ram you have:
```
free -m
```
[*]Info about your swap drive:
```
swapon -s
```
[*]Why are you using tuxonice instead of the default kernel suspend/hibernate? Does the kernel method not work?
[*]The results of the following command:
```
cat /var/log/syslog | grep PM:
```
[*]
[/LIST]
My laptop is a Medion Razor X6815
```
matatabisama@matatabisama-X6815:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3863       3716        147          0        559       1565
-/+ buffers/cache:       1591       2272
Swap:         7810          0       7810
```
```
matatabisama@matatabisama-X6815:~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	7998460	0	-1
```
```
matatabisama@matatabisama-X6815:~$ cat /var/log/syslog | grep PM:
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bac1d000 - 00000000bad8e000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bad8f000 - 00000000badb8000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000badc8000 - 00000000bade8000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000baf16000 - 00000000bafe8000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000baffd000 - 00000000bb000000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bb000000 - 00000000bfa00000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bfa00000 - 00000000f8000000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffa00000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Aug 22 15:29:16 matatabisama-X6815 kernel: [    0.253018] PM: Registering ACPI NVS region [mem 0xbaf16000-0xbafe7fff] (860160 bytes)
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bac1d000 - 00000000bad8e000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bad8f000 - 00000000badb8000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000badc8000 - 00000000bade8000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000baf16000 - 00000000bafe8000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000baffd000 - 00000000bb000000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bb000000 - 00000000bfa00000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bfa00000 - 00000000f8000000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffa00000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Aug 22 15:48:28 matatabisama-X6815 kernel: [    0.254232] PM: Registering ACPI NVS region [mem 0xbaf16000-0xbafe7fff] (860160 bytes)
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bac1d000 - 00000000bad8e000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bad8f000 - 00000000badb8000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000badc8000 - 00000000bade8000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000baf16000 - 00000000bafe8000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000baffd000 - 00000000bb000000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bb000000 - 00000000bfa00000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bfa00000 - 00000000f8000000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffa00000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Aug 22 16:34:56 matatabisama-X6815 kernel: [    0.254352] PM: Registering ACPI NVS region [mem 0xbaf16000-0xbafe7fff] (860160 bytes)
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bac1d000 - 00000000bad8e000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bad8f000 - 00000000badb8000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000badc8000 - 00000000bade8000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000baf16000 - 00000000bafe8000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000baffd000 - 00000000bb000000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bb000000 - 00000000bfa00000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bfa00000 - 00000000f8000000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffa00000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Aug 23 15:10:30 matatabisama-X6815 kernel: [    0.253890] PM: Registering ACPI NVS region [mem 0xbaf16000-0xbafe7fff] (860160 bytes)
```
To be honest, I didn't know, that ther66e is one on-board hibernation function.:oops::oops::oops::oops::oops: How do I use it?

---

### Post by Toz on 2013-08-23
From your pm-suspend.log file, it shows that you tried a suspend/resume before the hibernate. It looks like the suspend/resume was successful. Can you confirm that it was?

Why are you using tuxonice? Is it because the kernel method (default method) didn't work?

And a few more commands:
```
sudo blkid
```
```
cat /etc/initramfs-tools/conf.d/resume
```
```
cat /etc/fstab | grep swap
```

---

### Post by Toz on 2013-08-23
> To be honest, I didn't know, that ther66e is one on-board hibernation function. How do I use it? 
What do you mean by "on-board hibernate function"?

---

### Post by cthlhu1987 on 2013-08-23
> **Toz said:**
> From your pm-suspend.log file, it shows that you tried a suspend/resume before the hibernate. It looks like the suspend/resume was successful. Can you confirm that it was?
Yes, the suspend worked, but not the hibernate.
> Why are you using tuxonice? Is it because the kernel method (default method) didn't work?
Dunno how to use it ORZ
> And a few more commands:
```
sudo blkid
```
```
matatabisama@matatabisama-X6815:~/music/etc$ sudo blkid
[sudo] password for matatabisama: Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
/dev/sda1: LABEL="WINDOWS7" UUID="010F8F3470532A79" TYPE="ntfs" 
/dev/sda2: LABEL="LINUX" UUID="6145bf54-7211-4c51-9cfc-3632402ed25a" TYPE="ext4" 
/dev/sda3: LABEL="DATA" UUID="1CD29A287150687A" TYPE="ntfs" 
/dev/sda5: UUID="f0446c23-fe54-46a8-8fd8-876b1ace57e3" TYPE="swap" 
/dev/sdb1: LABEL="LEMONTANK" UUID="781A92D63F16FA43" TYPE="ntfs" 
/dev/sdc1: LABEL="LEMONTRUCK" UUID="210CCA637D14322D" TYPE="ntfs" 
/dev/sdd1: LABEL="LEMONTREE" UUID="00B8C145B8C13A44" TYPE="ntfs"
```
> ```
cat /etc/initramfs-tools/conf.d/resume
```
```
matatabisama@matatabisama-X6815:~/music/etc$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=f0446c23-fe54-46a8-8fd8-876b1ace57e3
```
> ```
cat /etc/fstab | grep swap
```
```
matatabisama@matatabisama-X6815:~/music/etc$ cat /etc/fstab | grep swap
# swap was on /dev/sda5 during installation
UUID=f0446c23-fe54-46a8-8fd8-876b1ace57e3 none            swap    sw              0       0
```

> **Toz said:**
> What do you mean by "on-board hibernate function"?
The other method (kernel) you mentioned, the one I dunno how to use ;( ;( ;(

---

### Post by Toz on 2013-08-23
Configuration-wise, everything looks okay. Can you try this:

1. Uninstall tuxonice.

2. Run:
```
sudo update-initramfs -u
```

3. Reboot

4. Try hibernate again, and if unsuccessful, post back:
```
cat /var/log/syslog | grep PM:
```
...and the contents of /var/log/pm-suspend.log again.

---

### Post by cthlhu1987 on 2013-08-24
> **Toz said:**
> Configuration-wise, everything looks okay. Can you try this:
1. Uninstall tuxonice.
2. Run:
```
sudo update-initramfs -u
```
3. Reboot
4. Try hibernate again, and if unsuccessful, post back:
```
cat /var/log/syslog | grep PM:
```
...and the contents of /var/log/pm-suspend.log again.
It against failed to resume after hibernation ;( ;( ;(
```
matatabisama@matatabisama-X6815:~/swf$ cat /var/log/syslog | grep PM:
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bac1d000 - 00000000bad8e000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bad8f000 - 00000000badb8000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000badc8000 - 00000000bade8000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000baf16000 - 00000000bafe8000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000baffd000 - 00000000bb000000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bb000000 - 00000000bfa00000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bfa00000 - 00000000f8000000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffa00000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Aug 24 23:30:01 matatabisama-X6815 kernel: [    0.253849] PM: Registering ACPI NVS region [mem 0xbaf16000-0xbafe7fff] (860160 bytes)
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bac1d000 - 00000000bad8e000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bad8f000 - 00000000badb8000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000badc8000 - 00000000bade8000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000baf16000 - 00000000bafe8000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000baffd000 - 00000000bb000000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bb000000 - 00000000bfa00000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000bfa00000 - 00000000f8000000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffa00000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Aug 24 23:41:04 matatabisama-X6815 kernel: [    0.254125] PM: Registering ACPI NVS region [mem 0xbaf16000-0xbafe7fff] (860160 bytes)
```

[/var/log/pm-suspend.log](http://pastebin.com/uSYu55HG)

---

### Post by Toz on 2013-08-24
Can you try adding a **resume=** kernel parameter, like this:
[LIST=1]
[*]Open your grub configuration file for editing:
```
gksu leafpad /etc/default/grub
```
[*]Replace the line:
> GRUB_CMDLINE_LINUX=""
...with:
```
GRUB_CMDLINE_LINUX="resume=UUID=f0446c23-fe54-46a8-8fd8-876b1ace57e3"
```
[*]Save the file.
[*]Commit the configuration:
```
sudo update-grub
```
[*]Reboot
[*]
[/LIST]

Once rebooted, try again. If it doesn't work, can you post back:
```
cat /proc/cmdline
```
...and can I have a look at the whole /var/log/syslog file?

---

