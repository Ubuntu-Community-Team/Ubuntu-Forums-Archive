---
title: "downloading full web albums w/ picasa"
date: 2008-04-14
forum: General Help
---

### Post by KhaaL on 2008-04-14
Hi all

I'm trying to download a full picasa album wth picasa 2.7 for linux. Once I click the download album link, i see them flash by as picasa downloads them. However, I tried finding them and searched for them in every possible corner in my filesystem without luck. I also tried finding a setting to specify where to download them, but couldn't find such a setting either... Anyone who can help me on how I can get this working?

---

### Post by KhaaL on 2008-04-17
slight bump

---

### Post by hencke on 2008-05-24
> **KhaaL said:**
> Hi all

I'm trying to download a full picasa album wth picasa 2.7 for linux. Once I click the download album link, i see them flash by as picasa downloads them. However, I tried finding them and searched for them in every possible corner in my filesystem without luck. I also tried finding a setting to specify where to download them, but couldn't find such a setting either... Anyone who can help me on how I can get this working?

Hi KHaaL!

My pictures were downloaded to

~/Pictures/Downloaded Albums/<username>/<albumname>/

I might have specified ~/Pictures/ as the default folder at some point, but can't remember doing that. Do you have a ~/Pictures/Downloaded Albums/ folder?

I'm using Ubuntu 8.04 and when I clicked the "Download Album" link on a friends picasa page a dialog box opened after which I had to specify /usr/bin/picasa to download the album. Did others have this problem with 7.04 or 7.10? My Picasa version is 2.7 (Build 37.3615, 0) for Linux.

---

### Post by KhaaL on 2008-05-26
Heya

No, I don't have a ~/Pictures folder at all. Even if i create ~/Pictures/Downloaded Albums, downloaded albums still dosen't appear there...

---

### Post by hencke on 2008-05-27
> **KhaaL said:**
> Heya

No, I don't have a ~/Pictures folder at all. Even if i create ~/Pictures/Downloaded Albums, downloaded albums still dosen't appear there...

Hi KhaaL,

in Picasa, go to Tools > Options > General and check which folder is selected in "Save Imported Pictures In". Mine says "My Pictures" but when I click "Browse..." I see that it means "~/Pictures". If the selected folder doesn't contain anything, check that Picasa has write permissions to that folder. (If it doesn't exist, create it as the same user you use Picasa with.)

Hope that helps, but another problem could be your firewall settings. Can you upload pictures to your own albums? I don't know too much about firewalls, but this might get you started:

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

I used to use Firestarter, which is a nice graphical frontend for configuring iptables. It's in the repos, just search for "firestarter" in Synaptic or

```
sudo apt-get install firestarter
```

If you don't get the problem solved here, then you could also check the following link for suggestions:

[http://groups.google.com/group/Google-Labs-Picasa-for-Linux/](http://groups.google.com/group/Google-Labs-Picasa-for-Linux/)

They might have a bit more Picasa-expertize there. =) Whatever you do, post back here, so the rest of us know how you solved the problem. =)

---

### Post by KhaaL on 2008-05-27
> **hencke said:**
> Hi KhaaL,

in Picasa, go to Tools > Options > General and check which folder is selected in "Save Imported Pictures In". Mine says "My Pictures" but when I click "Browse..." I see that it means "~/Pictures". If the selected folder doesn't contain anything, check that Picasa has write permissions to that folder. (If it doesn't exist, create it as the same user you use Picasa with.)



Actually that did the trick. It dosen't go into the folder I specify, but in a folder with the same naming as you mentioned before. 

A bunch of thanks for your help! :KS

---

