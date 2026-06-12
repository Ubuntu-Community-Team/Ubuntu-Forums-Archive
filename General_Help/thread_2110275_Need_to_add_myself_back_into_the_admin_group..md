---
title: "Need to add myself back into the admin group."
date: 2013-01-29
forum: General Help
---

### Post by Gotti on 2013-01-29
Here's a fun one. After disabling lightdm and booting directly to a command line, i found that my sound wasn't working. After checking I realized I wasn't in the audio group. So I added myself in via

sudo usermod -G audio jason

Whoops. Now when I run 'groups jason' I can plainly see that audio is now the ONLY group I'm in. Fun.

Now I'm not in the sudoers file, and I can't use usermod again without using sudo. See my problem here? lol

Now I assume my next move is to boot from a liveCD and mount to my install. This leaves me with a few questions:

1. Once the CD is booted, what commands must I run to get fully mounted and ready to fix my clusterQ#$%@$?
2. What groups should I be in (aka what groups were I in before I screwed up...I never did any group editing before this so essentially I'm asking what the default groups are.
and 3. What command _should_ I have run to simply add audio in to my groups list, and not overwrite it?

Feel free to preface your answers with as much laughing and berating as you see fit. But help would be awesome too. =D

---

### Post by AstroLlama on 2013-01-29
I haven't done any extensive tweaking, though by running the command "id" i can see my username is a member of the following groups: [my user name], adm, cdrom, sudo, audio, dip, plugdev, lpadmin, sambashare

that's quite a pickle you got yourself into!

---

### Post by steeldriver on 2013-01-29
That happens a lot - it's why adduser or gpasswd are recommended for adding users to a group

Anyhow before reaching for the liveCD, you should be able to do it from recovery mode

```
# mount -o remount,rw /
# usermod -aG adm,cdrom,sudo,dip,plugdev,staff,lpadmin *username*
```I *think* those are the default groups. If you have stuff like samba then they may also be in sambashare. Obviously the initial login group should be the user private group.

---

### Post by Gotti on 2013-01-29
> **steeldriver said:**
> That happens a lot - it's why adduser or gpasswd are recommended for adding users to a group

Anyhow before reaching for the liveCD, you should be able to do it from recovery mode

```
# mount -o remount,rw /
# usermod -aG adm,cdrom,sudo,dip,plugdev,staff,lpadmin *username*
```I *think* those are the default groups. If you have stuff like samba then they may also be in sambashare. Obviously the initial login group should be the user private group.

```
jason@kaito:~$ mount -o remount, rw /
mount: only root can do that
```

:frown:

---

### Post by steeldriver on 2013-01-29
You will need to boot into recovery mode - from the grub menu

If your boot doesn't display the grub menu by default, then you will need to interrupt it by holding down the shift key 

In recovery mode you will be root

> **steeldriver said:**
> That happens a lot - it's why adduser or gpasswd are recommended for adding users to a group

Anyhow before reaching for the liveCD, you should be able to do it from [SIZE=2][COLOR=Red]**recovery mode**[/COLOR][/SIZE]

```
# mount -o remount,rw /
# usermod -aG adm,cdrom,sudo,dip,plugdev,staff,lpadmin *username*
```I *think* those are the default groups. If you have stuff like samba then they may also be in sambashare. Obviously the initial login group should be the user private group.

---

### Post by Gotti on 2013-01-29
> **steeldriver said:**
> You will need to boot into recovery mode - from the grub menu

If your boot doesn't display the grub menu by default, then you will need to interrupt it by holding down the shift key 

In recovery mode you will be root

You, good sir, are the man. Thank you.

---

### Post by steeldriver on 2013-01-29
Glad you got it fixed - for future reference, a nice safe way to do what you originally wanted to do is

```
sudo gpasswd --add *username groupname*
```If you *do* use usermod, remember to give the -a ('append') switch

```
sudo usermod -[COLOR=Red]**a**[/COLOR]G *groupname username*
```

---

