---
title: "how to disable gnome-keyring for ssh keys in 14.10?"
date: 2014-10-29
forum: General Help
---

### Post by joolz2 on 2014-10-29
Hi everyone,

Since the upgrade to 14.10 gnome-keyring insists on handling my ssh key passwords, which is something I definitely do not want. For one password I'll use ssh-agent, for all the others no storing should be allowed.

 In previous versions I disabled it (IIRC) by changing a setting in /etc/xdg/autostart/gnome-keyring-ssh.desktop. The upgrade broke this, and I can't get gnome-keyring to not interfere.

So far I tried tweaking /etc/xdg/autostart/gnome-keyring-ssh.desktop, killing processes, chmod -x /usr/bin/gnome-keyring-3 (doesn't help), chmod -x /usr/bin/gnome-keyring-daemon (networking passwords not accessible)

TIA!

---

### Post by Andrew_Reid on 2014-11-02
I also ran into this immediately after the 14.10 upgrade. I have two solutions.

The first is fairly stupid, you just move your private SSH keys out of the .ssh directory. Then the gnome-keyring daemon can't see them, and doesn't start the SSH service.

The second is to modify the file /usr/share/upstart/sessions/gnome-keyring.conf. There's a line in there that "eval"s the gnome-keyring-daemon, I just added an argument to this, I put "-c pkcs11,secrets.gpg" on the end (inside the parentheses). This seems to work. According to the man page, it restricts the daemon to the services listed after the -c argument. It may be noteworthy that I have also removed the  /etc/xdg/autostart/gnome-keyring-daemon-ssh.desktop file. What is weird about this is that the "-c" argument does not show up on the command line for the gnome keyring daemon in the process table, and it feels slightly wrong, I have low confidence that "pcks11,secrets,gpg" is an exhaustive list of the other services it wants to cover. But, it seems to work.

---

### Post by Andy_Hieb on 2014-11-03
I was also able to disable gnome-keyring by backing up /usr/share/upstart/sessions/gnome-keyring.conf then symlinking /usr/share/upstart/sessions/gnome-keyring.conf to /dev/null .  I have no idea how advisable this may or may not be, but was just taking the [steps for disabling gnome-keyring]("https://wiki.archlinux.org/index.php/GNOME_Keyring") one step further.

[Launchpad bug 1271591]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/1271591") is related.

---

### Post by YONETANI_Tomokazu on 2014-11-05
> **Andy_Hieb said:**
> I was also able to disable gnome-keyring by backing up /usr/share/upstart/sessions/gnome-keyring.conf then symlinking /usr/share/upstart/sessions/gnome-keyring.conf to /dev/null .  I have no idea how advisable this may or may not be, but was just taking the [steps for disabling gnome-keyring]("https://wiki.archlinux.org/index.php/GNOME_Keyring") one step further.

[Launchpad bug 1271591]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/1271591") is related.

Hi,
the launchpad bug 1271591 that you just quoted mentions how to disable this new feature, and finally I could disable it with what seems to be an official way:
$ mkdir -p ~/.config/upstart
$ echo manual | tee -a ~/.config/upstart/gnome-keyring.override

it'd be better if I can use ssh-add without disabling it, though.

Thank you for the information.
YONETANI Tomokazu.

---

