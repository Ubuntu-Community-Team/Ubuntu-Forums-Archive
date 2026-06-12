---
title: "3 different pcs, 3 different kernel versions"
date: 2019-03-24
forum: General Help
---

### Post by bobptz on 2019-03-24
Hi

I have 3 pcs with ubuntu 16.04, they all have different versions of the kernel.  ie 4.4.0-75-generic, 4.4.0-134-generic, 4.4.0-143-generic.  They all have the software updater active and updating the machines.  Why don;t they all have the latest ( 4.4.0-143-generic ) kernel?

Is there a way to force the latest kernel to update?  

If I install the latest kernel from synaptic, am I going to brake the pc?

---

### Post by Autodave on 2019-03-24
First of all, that would not really concern me.  But, if I were to try and get all of them the same, I would start by running the following commands on all 3 machines:

sudo apt-get update
sudo apt-get upgrade

Then compare when that is done and report back.

---

### Post by deadflowr on 2019-03-24
Make sure they all have the linux-generic (or linux-image-generic and/or linux-headers-generic) package installed.
those are what are needed in order to get newer kernels.

Also double check via apt-get update commands that there isn't an issue with the updater functionality.

---

### Post by bobptz on 2019-03-24
> **Autodave said:**
> 
sudo apt-get update
sudo apt-get upgrade

I did run them, nothing happened.


>>>>
Make sure they all have the linux-generic (or linux-image-generic and/or linux-headers-generic) package installed.
<<<<
Yes, I think I am missing those.  Which version do I need to install (I see them not installed in synaptic).

---

### Post by yetimon_64 on 2019-03-24
> **bobptz said:**
> ...
Make sure they all have the linux-generic (or linux-image-generic and/or linux-headers-generic) package installed.
<<<<
Yes, I think I am missing those.  Which version do I need to install (I see them not installed in synaptic).

Just tick those 3 exact package names in synaptic and press "apply", not any other similar packages with extended naming, those 3 are meta-packages that will always provides the latest version for the packages they relate to.

See the attached screenshot of synaptic below and note the description it is showing for linux-headers-generic currently selected ... > This package will always depend on the latest generic kernel headers available.... installing all of these 3 packages on all your 3 installations will keep them consistent with the main linux package, kernels and headers etc.

[ATTACH=CONFIG]282845[/ATTACH]

Regards, yeti

---

### Post by bobptz on 2019-03-24
> **yetimon_64 said:**
> Just tick those 3 exact package names in synaptic and press "apply",

I did as you said.  I rebooted. Then I run :

```
sudo apt-get update
sudo apt-get upgrade

```

EDIT
The result is that now I am updated to 4.4.0-143-generic.  But not the latest , 4.15.0-46-generic, I think.

---

### Post by oldfred on 2019-03-24
If you installed the original 16.04 or 16.04.1 you stay on original kernel. Version will still say it is newer.
That is for stability and if your systems runs well, no real reason to upgrade kernel. Newer kernels were for newer systems since 5 year life.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by yetimon_64 on 2019-03-24
> **bobptz said:**
> I did as you said.  I rebooted. Then I run :

```
sudo apt-get update
sudo apt-get upgrade

```

EDIT
The result is that now I am updated to 4.4.0-143-generic.  But not the latest , 4.15.0-46-generic, I think.

The 4.4 kernels are what Xenial (16.04) supplies, the 4.15 kernels are for Bionic (18.04). You are now fully up to date now for what xenial usually supplies if all 3 installations are now on the 4.4.0-143 kernel.

Your first post only mentioned the latest 4.4 kernels, I didn't realize you wanted Bionic kernels on Xenial when answering.

It may be possible using "hwe" named packages to do so but await further advice from others if you want Bionic kernels on Xenial. I tend to stick with the kernels as supplied by the version I am using.

**Edit:** I see oldfred has posted an "enablement stack" link above for the very latest kernels. I agree there is "no real reason to upgrade kernel" for most users.

Regards, yeti.

**Edit2:** @ OP, I just noted that the image I attached above is from ubuntu mate 18.04 and you are on 16.04; I only just realized that is why you mentioned the 4.15 kernels. Sorry for not noting my release and causing some version confusion for you. My bad, oops ... :redface:

---

### Post by bobptz on 2019-03-24
Hi guys

All of my pcs are ubuntu 16.04.  Two of them have 4.4 kernels (different subversions), one has a 4.15 kernel.  They told me it has to do with the initial installation (16.04, 16.04.4 etc).

I don't want to investigate it further, I lost all day with this.

Thank you all.

---

