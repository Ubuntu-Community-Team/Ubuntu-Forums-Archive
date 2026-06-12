---
title: "Suspend2 - not resuming"
date: 2007-11-04
forum: General Help
---

### Post by dixon on 2007-11-04
Hi,
I've compiled custom patched(with suspend2) kernel. Hibernating is working without any error, but when I turn on computer it starts as usual(it doesn't load the hibernated image from swap space).

I hope I explained it clear :\

Related configs:

menu.lst
```

...
title           Ubuntu 7.10, kernel 2.6.22-14-suspend2
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-suspend2 root=UUID=21573d46-ce13-4ab2-88ba-2e9692b9f1c1 ro quiet splash locale=sk_SK resume2=swap:/dev/sda5
initrd          /boot/initrd.img-2.6.22-14-suspend2
quiet
...

```hibernate.conf
```

TryMethod suspend2.conf
TryMethod disk.conf
TryMethod ram.conf

```suspend2.conf
```

### suspend2 (for Software Suspend 2)
UseSuspend2 yes
Reboot no
EnableEscape yes
DefaultConsoleLevel 1
Compressor lzf
Encryptor none
# ImageSizeLimit 200

## useful for initrd usage:
SuspendDevice swap:/dev/sda5

## Powerdown method - 3 for suspend-to-RAM, 4 for ACPI S4 sleep, 5 for poweroff
PowerdownMethod 5

## Any other /proc/software_suspend setting can be set like so:
# ProcSetting expected_compression 50

## Or traditionally like this:
# Suspend2AllSettings 0 0 2056 65535 5

## Or even from the results of hibernate --save-settings with this:
# Suspend2AllSettingsFile /etc/hibernate/suspend-settings.conf

## For filewriter:
# FilewriterLocation /suspend_file 1000
# VerifyFilewriterResume2 yes

## Specify a userui like this:
ProcSetting userui_program /usr/local/sbin/tuxoniceui_text

# Scale CPU to full speed to make sure we suspend as fast as possible.
FullSpeedCPU yes

Include common.conf

```dixon@dixon-laptop:~$ sudo swapon -s
```

Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       1502036 0       -1

```Please help somebody. I'm desperate...

---

