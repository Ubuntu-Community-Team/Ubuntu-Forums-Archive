---
title: "Problem running update"
date: 2022-08-31
forum: General Help
---

### Post by satimis on 2022-08-31
Hi all,

Ubuntu22.04 upgraded from Ubuntu20.04

$ lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:        22.04
Codename:       jammy
```

$ sudo apt update```

Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://security.ubuntu.com/ubuntu jammy-security InRelease
Hit:3 http://hk.archive.ubuntu.com/ubuntu jammy InRelease
Hit:4 http://hk.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:5 http://hk.archive.ubuntu.com/ubuntu jammy-backports InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
```

$ apt list --upgradable```

Listing... Done
thermald/jammy-updates 2.4.9-1ubuntu0.1 amd64 [upgradable from: 2.4.9-1]
N: There is 1 additional version. Please use the '-a' switch to see it
```

$ apt list -a```

...
....
zvbi/jammy 0.2.35-19 i386
zvmcloudconnector-api/jammy,jammy 2.0.0~b1~git2019062011.4fc9142.really.1.4.1-0ubuntu3 all
zvmcloudconnector-common/jammy,jammy 2.0.0~b1~git2019062011.4fc9142.really.1.4.1-0ubuntu3 all
zydis-tools/jammy 3.2.1-5 amd64
zynaddsubfx-data/jammy,jammy 3.0.5-2build1 all
zynaddsubfx-dssi/jammy 3.0.5-2build1 amd64
zynaddsubfx-lv2/jammy 3.0.5-2build1 amd64
zynaddsubfx-vst/jammy 3.0.5-2build1 amd64
zynaddsubfx/jammy 3.0.5-2build1 amd64
zypper-common/jammy,jammy 1.14.42-2 all
zypper-doc/jammy,jammy 1.14.42-2 all
zypper/jammy 1.14.42-2 amd64
zytrax/jammy 0+git20201215-1 amd64
zziplib-bin/jammy 0.13.72+dfsg.1-1.1 amd64
zziplib-bin/jammy 0.13.72+dfsg.1-1.1 i386

```

It is a large file.

Please advise how to fix the problem?  Thanks

Regards

---

### Post by Dennis N on 2022-08-31
> $ apt list -a
try:
```
apt list --upgradable -a
```

---

### Post by satimis on 2022-08-31
> **Dennis N said:**
> try:
```
apt list --upgradable -a
```
$ apt list --upgradable -a```

Listing... Done
thermald/jammy-updates 2.4.9-1ubuntu0.1 amd64 [upgradable from: 2.4.9-1]
thermald/jammy,now 2.4.9-1 amd64 [installed,upgradable to: 2.4.9-1ubuntu0.1]

```

Regards

---

### Post by &amp;KyT$0P# on 2022-08-31
What is the problem?  I don't see any problem in any of those outputs.

* Just ran updates on my system, and see that thermald is being kept back.  It is a phased update that our systems have not been phased into yet.  You can verify this with
```
apt-cache policy thermald
```

---

### Post by civilpolisen on 2022-09-01
```
sudo apt install thermald --fix-broken
```

I'm upgrading all of our 25-30+ servers using this command.

Depending on your network and the rest of your infrastructure, a question may occur "if you want to replace or leave a file" then choose to leave, not to replace.

---

### Post by satimis on 2022-09-01
Hi all,

Thanks for your advice.

This Ubuntu 22.04 desktop is the host of VirtualBox.   I have about 40 cloned websites running as VMs.  I must proceed with extreme care otherwise there will be lot of work for me should anything going wrong.

$ apt-cache policy thermald```

thermald:
  Installed: 2.4.9-1
  Candidate: 2.4.9-1ubuntu0.1
  Version table:
     2.4.9-1ubuntu0.1 500 (phased 40%)
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
 *** 2.4.9-1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status

```

The host is running without problem even without "2.4.9-1ubuntu0.1" installed,

Regards

---

### Post by &amp;KyT$0P# on 2022-09-01
> **civilpolisen said:**
> I'm upgrading all of our 25-30+ servers using this command.

You could spare the manual work in the long term and configure the phased updates how you want as documented [here]("https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345").

> **satimis said:**
> The host is running without problem even without "2.4.9-1ubuntu0.1" installed,

Then nothing is wrong and you can just let this be, you'll get the update when your system is phased into it.

---

### Post by satimis on 2022-09-01
> **halogen2 said:**
>  - snip -
Then nothing is wrong and you can just let this be, you'll get the update when your system is phased into it.
Yes, I'll.  Thanks.

Regards

---

