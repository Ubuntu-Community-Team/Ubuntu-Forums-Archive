---
title: "Shut down hang Failed to send watchdog1 notification message"
date: 2023-01-30
forum: General Help
---

### Post by monkeybrain20122 on 2023-01-30
Hi,

This  is a weird problem. I was trying to compile maxima from source, the whole things went smoothly but when I did checkinstall it failed and the acted strangely. I couldn't bring up the terminal or anything. I shut it down and then get stuck with message 
```

systemd-journald:failed to send watchdog1 notification message: transport endpoint is not connected
```

I am sure it has something to do with maxima. I experienced this once before and I thought it was coincident, but it happened again. I have installed a bunch of other packages this way without issues. It is a btrfs system if it helps.

Last time I hard shut down and I rebooted to a kernel panic and have to reinstore. I don't want to this again.  

Thanks.

---

### Post by monkeybrain20122 on 2023-01-30
So I reboot and stuck at [end kernel panic - not syncing : attept tp kill init! exitcode=0x00000100 ]--

---

### Post by monkeybrain20122 on 2023-01-30
I boot up from a live usb and try to chroot into it, but it can't run chroot

```
sudo mount /dev/nvme0n1p2 /mnt -o subvol=@
sudo mount /dev/nvme0n1p1 /mnt/boot/efi
sudo mount --rbind /proc /mnt/proc
sudo mount --rbind /sys /mnt/sys
sudo mount --rbind /home /mnt/home
sudo mount --rbind /dev /mnt/dev
sudo chroot /mnt
chroot: failed to run command &#8216;/bin/bash&#8217;: No such file or directory

```

However 

```
$ls /mnt/bin/bash
/mnt/bin/bash
```

so it is there.


[B]Edited
[/B]
```
ldd /mnt/bin/bash
    linux-vdso.so.1 (0x00007ffcbb9ce000)
    libtinfo.so.6 => /lib/x86_64-linux-gnu/libtinfo.so.6 (0x00007efead943000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007efead71b000)
    /lib64/ld-linux-x86-64.so.2 (0x00007efeadae7000)
```

So I did
```
sudo mount --rbind /lib /mnt/lib
sudo mount --rbind /lib64 /mnt/lib64
```

Now chroot works.

---

### Post by monkeybrain20122 on 2023-01-30
so I have reinstalled the system. It will probably takes me a lot longer to trouble shoot it. Everything seems ok. But I have these boot errors that might of might not existed before (because I never checked) 

```
kernel: No Arguments are initialized for method [_CPC]
 kernel: ACPI Error: Aborting method \_SB.PR01._CPC due to previous error (AE_NOT_FOUND) (20210730/psparse-529)
 kernel: ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PR00._CPC], AE_NOT_FOUND (20210730/psargs-330)
```

What is "due to previous error"?

and this

```
audit[613]:AVC apparmor=="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="libreoffice-soffice//gpg" pid=613 comm>
apparmor.systemd[468]: Error: At least one profile failed to load
systemd[1]: apparmor.service: Main process exited, code=exited, status=1/FAILURE
systemd[1]: apparmor.service: Failed with result 'exit-code'.
systemd[1]: Failed to start Load AppArmor profiles.



```

Otherwise everything is working normally.

---

### Post by #&amp;thj^% on 2023-01-30
> **monkeybrain20122 said:**
> so I have reinstalled the system. It will probably takes me a lot longer to trouble shoot it. Everything seems ok. But I have these boot errors that might of might not existed before (because I never checked) 

```
kernel: No Arguments are initialized for method [_CPC]
 kernel: ACPI Error: Aborting method \_SB.PR01._CPC due to previous error (AE_NOT_FOUND) (20210730/psparse-529)
 kernel: ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PR00._CPC], AE_NOT_FOUND (20210730/psargs-330)
```

What is "due to previous error"?

No answer to your question but: [https://bugzilla.kernel.org/show_bug.cgi?id=213023](https://bugzilla.kernel.org/show_bug.cgi?id=213023)
To get rid of these messages while booting, you can add loglevel=3 to GRUB_CMDLINE_LINUX_DEFAULT in etc/default/grub, so that it will look like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash loglevel=3"

```
then update grub using command:
```
 sudo update-grub
```

Note that, adding 'loglevel=3' simply disables the non-critical error but doesn't resolve it. 
> **monkeybrain20122 said:**
> 
and this

```
audit[613]:AVC apparmor=="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="libreoffice-soffice//gpg" pid=613 comm>
apparmor.systemd[468]: Error: At least one profile failed to load
systemd[1]: apparmor.service: Main process exited, code=exited, status=1/FAILURE
systemd[1]: apparmor.service: Failed with result 'exit-code'.
systemd[1]: Failed to start Load AppArmor profiles.



```

Otherwise everything is working normally.
You found stuff I've not seen in quite sometime:
```
sudo apparmor_status --verbose
```

---

### Post by monkeybrain20122 on 2023-01-30
Hi,

```
sudo apparmor_status --verbose
[sudo] password for mb: 
apparmor module is loaded.
28 profiles are loaded.
26 profiles are in enforce mode.
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince//sanitized_helper
   /usr/bin/man
   /usr/bin/redshift
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/NetworkManager/nm-dhcp-helper
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/lightdm/lightdm-guest-session
   /usr/lib/lightdm/lightdm-guest-session//chromium
   /usr/sbin/cups-browsed
   /usr/sbin/cupsd
   /usr/sbin/cupsd//third_party
   /{,usr/}sbin/dhclient
   libreoffice-senddoc
   libreoffice-soffice//gpg
   libreoffice-xpdfimport
   lsb_release
   man_filter
   man_groff
   nvidia_modprobe
   nvidia_modprobe//kmod
   tcpdump
2 profiles are in complain mode.
   libreoffice-oosplash
   libreoffice-soffice
0 profiles are in kill mode.
0 profiles are in unconfined mode.
9 processes have profiles defined.
9 processes are in enforce mode.
   /usr/bin/redshift (2127) 
   /usr/sbin/cups-browsed (1305) 
   /usr/sbin/cupsd (919) 
   /usr/lib/cups/notifier/dbus (958) /usr/sbin/cupsd
   /usr/lib/cups/notifier/dbus (959) /usr/sbin/cupsd
   /usr/lib/cups/notifier/dbus (960) /usr/sbin/cupsd
   /usr/lib/cups/notifier/dbus (961) /usr/sbin/cupsd
   /usr/lib/cups/notifier/dbus (2029) /usr/sbin/cupsd
   /usr/lib/cups/notifier/dbus (2030) /usr/sbin/cupsd
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
0 processes are in mixed mode.
0 processes are in kill mode.

```

---

### Post by monkeybrain20122 on 2023-01-30
So I figured out what has caused my initial problem. Had I figured it out last night I don't have to reinstall the system, checkinstall is the culprit. Oh well

Good news is that it is not a hardware issue. Basically checkinstall broke the system by messing up the symlinks and the workaround (from launchpad link) is to make the .deb first and then safely install it.

[https://github.com/giuliomoro/checkinstall/issues/4](https://github.com/giuliomoro/checkinstall/issues/4)
[https://bugs.launchpad.net/ubuntu/+source/checkinstall/+bug/1847582](https://bugs.launchpad.net/ubuntu/+source/checkinstall/+bug/1847582)

---

### Post by monkeybrain20122 on 2023-01-31
@1fallen The apparmor issue turned out to be caused by me forgetting to purge snapd when I apt removed it. Usually I purged it but I was a bit confused and tired when reinstalling the system.

[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1773515](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1773515)

running 
```
sudo dpkg --purge snapd
```

fixed it

---

