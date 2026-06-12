---
title: "password recovery issue"
date: 2015-01-23
forum: General Help
---

### Post by Apagon on 2015-01-23
I have got 2 linux boxes (let's call them b1 & b2), with the same /etc/default/grub: 

```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

GRUB_DISABLE_LINUX_UUID=false

GRUB_DISABLE_RECOVERY=false

GRUB_INIT_TUNE="480 440 1"


```

both grub are updated
on b1: 

```
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
```

On b2: 
```
 Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
```

When accessing recovery mode at boot, then, in the recovery menu, 'drop to root shell prompt', 
I get a root prompt on b1, but on b2, I am asked for root password: 'give root password for mainteance'.

---

### Post by sudodus on 2015-01-23
Is the second one encrypted?

---

### Post by steeldriver on 2015-01-23
In my experience 'give root password for maintenance' means you have activated the root account - either because it's a distro that does that by default (Debian, Mint etc.) rather than Ubuntu, or because you chose to set a root password at some point

---

### Post by Apagon on 2015-01-23
Thank you very much guys!
to Steeldriver: when you say: 
 'give root password for maintenance' means you have activated the root account -> I am not sure to follow. As far as I understood, root account does exist but login/direct access to the root account is not allowed by default. Besides, if I issue sudo -s and whoami, it says 'root' right? So do you mean, that I would had activated direct access to the root account (I mean loging directly as root) or something else? 
Now, interesting thing, in b2 (the box which asks for root password), in /etc/shadow, there is a password. In b1 (the box showing a root prompt), in /etc/shadown, there is: root: ! :... I am just wondering whether I could put '!' in the place of the password on b2. :?

---

### Post by sudodus on 2015-01-23
Please tell us about those two operating systems - as much details as possible - distro, version, flavour etc

for example Lubuntu 14.04.1, Debian Jessie Gnome

and what might be different in the installation.

Ubuntu does not activate the root account, it uses sudo instead. But many other distros provide an activated root account.

-o-

Also please tell us if there is some kind of encryption for example 'encrypted disk' or 'encrypted home'.

Obviously, it should not be possible to read files in an encrypted system unless you provide some sort of password or passphrase. But if the system is not encrypted, you can read the files in recovery mode or when booted from another system, for example a CD/DVD/USB drive.

---

### Post by Apagon on 2015-01-23
reminder: b1 does not ask for password, b2 does.

on b1: 
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
```

On b2: 
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

```

both boxes have been installed from the same 14.04.mini.iso usb stick. Only xubuntu desktop soft was selected on both.
I do not know if it would be usefull, but b2 was disconnected from internet after the installation was performed.

On both boxes, if I issue sudo -s -> I am root. (It was the same in previous versions of Ubuntu I had). 

There is  no encryption at all on both boxes.

---

### Post by Apagon on 2015-01-23
just a typo above: b1 does not ask for a passwd, b2 does, sorry.

---

### Post by sudodus on 2015-01-23
Thanks for the clear description :-)

I must admit that I don't understand why there is a difference concerning the passwords. Let us hope steeldriver has an idea how to continue ...

---

### Post by Apagon on 2015-01-25
here is what I understand about the root account in Ubuntu. 
when you issue: sudo -s
you have root attributes without beeing root. 
Now, if you enter: 
passwd, and put root password
then 
su or su root 
you will be logged as root and you default dir is /root.

---

### Post by Apagon on 2015-01-25
sorry, I havent finished yet ...
to avoid this, you can put /usr/sbin/nologin as default shell in /etc/passwd so that you cant login as root (you still can know if the root password is good or not)
to avoid current user beeing root, you can remove his right to sudo command and create an intermediate group, wheel, and su a user in this group that will be able to sudo. You need to bring some changes in PAM as well.

---

### Post by sudodus on 2015-01-25
I suggest that you run Ubuntu with ***sudo***:

```
sudo program-name
```

or with GUI programs:

```
gksudo gui-program-name
``` or ```
sudo -H gui-program-name
``` to avoid staying as root and avoid risks associated with superuser privileges.

-o-

In rare cases you can use ```
sudo -s
``` or ```
sudo -i
``` (minus lower case i). The effect of the options -H, -s and -i is described in

```
man sudo
```

---

### Post by steeldriver on 2015-01-25
I think you're over complicating this:

[LIST]
[*]default Ubuntu, root account is locked (root password is set to '!') recovery mode drops straight to the root shell 
[*]if you enable the root account (which is equivalent to setting its password) then that password is required to access the root shell - in recovery mode as elsewhere 
[/LIST]

So Occam's razor says you (or someone else with admin or physical access) simply enabled the root account on box 2 at some point.

Like sudodus says, stick with sudo - and just re-lock the root account

```

sudo passwd -l root

```

---

