---
title: "Should I delete"
date: 2021-05-14
forum: General Help
---

### Post by rami-sohaji on 2021-05-14
Ok , I am basiclly an amuture , I want to know if I should remove any of these

---

### Post by ActionParsnip on 2021-05-14
What is the output of:
```

lsb_release -a;uname -a

```

---

### Post by rami-sohaji on 2021-05-14
@[[COLOR=#000000]ActionParsnip[/COLOR]]("https://ubuntuforums.org/member.php?u=1079078")
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.10
Release:	20.10
Codename:	groovy
Linux LEAGUE 5.8.0-53-generic #60-Ubuntu SMP Thu May 6 07:46:32 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by deadflowr on 2021-05-14
You don't have to do anything.
All the entries unchecked are disabled so they have no bearing on the system.

Deleting them completely is up to you.

---

### Post by grahammechanical on 2021-05-14
Whether you should or should not de-activate the Canonical Partners repository is up to you. On one of my installs (20.04) I do not have that repository checked. If you have the Partners repository checked and you de-activate it any software installed through that repository may not get updated.

Deleting the Partners repository is not necessary in my opinion. It is just an address to a software source/server. If it is not activated the update/upgrade process will not look to that address for any software updates. Until activated it remains only an address in a kind of address book where certain software is stored.

Without that repository listed as a software source you will not be able to install any software from that repository until you list that repository as a software source. It is up to you what you do. In the future you may want to install software from that repository and then you will be wondering why Ubuntu cannot do what you want.

> The Canonical Partner repository offers some proprietary applications        that don't cost any money to use but are closed source. They include        software like Adobe Flash Plugin. Software in this       repository will appear in Ubuntu Software search results       but won't be installable until this repository is enabled.

[https://help.ubuntu.com/stable/ubuntu-help/addremove-sources.html.en](https://help.ubuntu.com/stable/ubuntu-help/addremove-sources.html.en)

Regards

---

### Post by ajgreeny on 2021-05-14
The only packages in the partner repos for 20.04 are the Adobe flashplugin and the two versions of adobe-flash-properties all of which are no longer supported by Adobe so will be even more of a security risk than many users believed them to be in the past.

So there really is no point in enabling the partner repos any more; I wonder why they are even available now.

---

### Post by Impavidus on 2021-05-15
Most sources in that list are already disabled. You can completely remove them to get rid of the visual clutter in that window, but removing has no other benefits and makes it harder to put them back, if you ever change your mind.

Only 4 sources in that list are enabled. The first is Google's repository for Chrome, which is added automatically if you install Chrome. Keep it, if you use Chrome, as that is where upgrades for Chrome come from.

Then there are 3 PPAs: bookworm, elementary-os and fingerprint. I haven't checked what software they provide. If you use them, keep them. If you don't use them, disable them.

---

