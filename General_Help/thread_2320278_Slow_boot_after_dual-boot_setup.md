---
title: "Slow boot after dual-boot setup"
date: 2016-04-12
forum: General Help
---

### Post by onlineguy on 2016-04-12
I regularly run an Ubuntu 15.10 setup, I created a dual boot with Ubuntu 14.04 LTS and removed the LTS version again after two days. Since the removal I have a slow boot process for now. I disabled Plymouth to see the startup messages and identified a slow process which seems to try mounting something while timing out.

sudo journalctl:
```
...
Apr 12 16:40:33 LinuxPC kernel: gspca_main: v2.14.0 registeredApr 12 16:40:33 LinuxPC kernel: gspca_main: gspca_zc3xx-2.14.0 probing 046d:08af
Apr 12 16:40:34 LinuxPC kernel: input: gspca_zc3xx as /devices/pci0000:00/0000:00:14.0/usb1/1-4/input/input23
Apr 12 16:40:34 LinuxPC kernel: usbcore: registered new interface driver gspca_zc3xx
Apr 12 16:42:02 LinuxPC systemd[1]: dev-disk-by\x2duuid-680b446c\x2d0c8a\x2d4e79\x2d8bd4\x2d0042d322208c.device: Job dev-disk-by\x2duuid-680b446c\x2d0c8a\x2d4e79\x2d8bd4\x2d0042d322208c.device/start timed out.
Apr 12 16:42:02 LinuxPC systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-680b446c\x2d0c8a\x2d4e79\x2d8bd4\x2d0042d322208c.device.
Apr 12 16:42:02 LinuxPC systemd[1]: Dependency failed for Cryptography Setup for cryptswap1.
Apr 12 16:42:02 LinuxPC systemd[1]: Dependency failed for Encrypted Volumes.
Apr 12 16:42:02 LinuxPC systemd[1]: cryptsetup.target: Job cryptsetup.target/start failed with result 'dependency'.
Apr 12 16:42:02 LinuxPC systemd[1]: Dependency failed for dev-mapper-cryptswap1.device.
Apr 12 16:42:02 LinuxPC systemd[1]: Dependency failed for /dev/mapper/cryptswap1.
Apr 12 16:42:02 LinuxPC systemd[1]: Dependency failed for Swap.
Apr 12 16:42:02 LinuxPC systemd[1]: swap.target: Job swap.target/start failed with result 'dependency'.
Apr 12 16:42:02 LinuxPC systemd[1]: dev-mapper-cryptswap1.swap: Job dev-mapper-cryptswap1.swap/start failed with result 'dependency'.
Apr 12 16:42:02 LinuxPC systemd[1]: dev-mapper-cryptswap1.device: Job dev-mapper-cryptswap1.device/start failed with result 'dependency'.
Apr 12 16:42:02 LinuxPC systemd[1]: systemd-cryptsetup@cryptswap1.service: Job systemd-cryptsetup@cryptswap1.service/start failed with result 'dependency'.
Apr 12 16:42:02 LinuxPC systemd[1]: dev-disk-by\x2duuid-680b446c\x2d0c8a\x2d4e79\x2d8bd4\x2d0042d322208c.device: Job dev-disk-by\x2duuid-680b446c\x2d0c8a\x2d4e79\x2d8bd4\x2d0042d322208c.device/start failed with result 'timeout'.
Apr 12 16:42:02 LinuxPC systemd[1]: Reached target System Initialization.
Apr 12 16:42:02 LinuxPC systemd[1]: Listening on D-Bus System Message Bus Socket.
Apr 12 16:42:02 LinuxPC systemd[1]: Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
Apr 12 16:42:02 LinuxPC systemd[1]: Started Trigger resolvconf update for networkd DNS.
Apr 12 16:42:02 LinuxPC systemd[1]: Listening on ACPID Listen Socket...
```

What is that and how can I fix this?

---

### Post by onlineguy on 2016-04-12
Reason for the slow boot was a broken swap config, no idea what broke it but I set it up again. I think there is still something wrong here:

```
$ sudo blkid | grep swap/dev/sda3: UUID="ce72b566-7096-400c-baef-ebd27e8068be" TYPE="swap" PARTUUID="f99b27fb-35f2-420e-9992-9f801ab3ea36"
/dev/mapper/cryptswap1: UUID="88f1d3e1-a6d1-4557-aa25-05f717d5117b" TYPE="swap"

```

Now, is it encrypted or not?

fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=5a8d5ee8-b93c-4800-b1f8-85a9f1e08836 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=8BDE-27DE  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
#UUID=ce72b566-7096-400c-baef-ebd27e8068be none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```

crypttab:
```
cryptswap1 UUID=ce72b566-7096-400c-baef-ebd27e8068be /dev/urandom swap,offset=1024,cipher=aes-xts-plain64

```

---

### Post by onlineguy on 2016-04-19
I bump this one, I'd like to know what to do about my swap.

---

### Post by Cavsfan on 2016-04-19
> **onlineguy said:**
> Reason for the slow boot was a broken swap config, no idea what broke it but I set it up again. I think there is still something wrong here:

```
$ sudo blkid | grep swap/dev/sda3: UUID="ce72b566-7096-400c-baef-ebd27e8068be" TYPE="swap" PARTUUID="f99b27fb-35f2-420e-9992-9f801ab3ea36"
/dev/mapper/cryptswap1: UUID="88f1d3e1-a6d1-4557-aa25-05f717d5117b" TYPE="swap"

```

Now, is it encrypted or not?

fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=5a8d5ee8-b93c-4800-b1f8-85a9f1e08836 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=8BDE-27DE  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
[COLOR=#ff0000]#[/COLOR]UUID=ce72b566-7096-400c-baef-ebd27e8068be none            swap    sw              0       0
[COLOR=#0000ff] /dev/mapper/cryptswap1 none swap sw 0 0[/COLOR]

```

crypttab:
```
cryptswap1 UUID=ce72b566-7096-400c-baef-ebd27e8068be /dev/urandom swap,offset=1024,cipher=aes-xts-plain64

```

Edit your fstab and remove the [COLOR=#ff0000]#[/COLOR] in [COLOR=#ff0000]red[/COLOR] above. I'm not sure you need the [COLOR=#0000ff]blue[/COLOR] line after doing that. I'd put a # in front of the blue line.
But, I'm not familiar with EFI or encrypted swap partitions though.

You could try that and hopefully that'll work.  If not, OldFred can take a look at it I know he knows more about EFI and encrypted partitions than I do.

Regards

---

### Post by onlineguy on 2016-04-20
I removed the # and added a # in front of te cryptswap entry. This resulted in a graphical dialogue for cryptswap's passphrase during boot which I never had before. Even worse: there was no cursor to type. I undid the changes via shell.

---

### Post by Cavsfan on 2016-04-20
> **onlineguy said:**
> I removed the # and added a # in front of te cryptswap entry. This resulted in a graphical dialogue for cryptswap's passphrase during boot which I never had before. Even worse: there was no cursor to type. I undid the changes via shell.

Hopefully someone else familiar with encrypted swap partitions can help you then.

---

### Post by oldfred on 2016-04-20
Do not know encrypted swap either. Just that is is  not an error when  gparted says is is an error as gparted cannot see encrypted swap  partitions.

I have seem several Boot-Repair scripts with encryption  and thought there were two entries. One partition and one for the  encryption? But do not know for sure or any details.

---

