---
title: "How Do I Enable All Filesystems In GParted?"
date: 2016-03-27
forum: General Help
---

### Post by grace3 on 2016-03-27
Hello,

How do I enable all filesystems in gparted; many are grayed out?

Thanks

---

### Post by Bucky Ball on 2016-03-27
Which ones exactly? Attach a screenshot to a post (Adv Reply and use the paperclip icon) so we can have a look.

---

### Post by grace3 on 2016-03-27
> **Bucky Ball said:**
> Which ones exactly? Attach a screenshot to a post (Adv Reply and use the paperclip icon) so we can have a look.

These appear to be:

exfat
f2fs
hfs
hfst
jfs
nilfs2
reiser4
reiserfs
ufs

Please see attachment.[ATTACH=CONFIG]268015[/ATTACH]

---

### Post by Bucky Ball on 2016-03-27
Still don't follow you. You are about to format your ntfs partition /dev/sda7 in that screenshot! I don't think you want to do that ... or do you? You are not enabling all filesystems, whatever that is.

What exactly are you trying to do here? You're setup look fine from what I can see of it (most of the details are hidden behind your dropdown screen, though). Are you having problems or ... ? :-k 

Bottom line here is that where you are in the screenshot is about to obliterate all data on sda7 by reformatting it to another filesystem type.

---

### Post by yetimon_64 on 2016-03-27
exfat and ufs are the only 2 here I can't get enabled. First shut down gparted then for the rest on your list run the following command in a terminal to install the necessary support packages ...

```
sudo apt-get install f2fs-tools hfsprogs hfsutils jfsutils nilfs-tools reiserfsprogs reiser4progs
```
When the installation finishes open gparted again then check which have changed.
See the attached screenshot, as I note above with exfat and ufs even installing their support packages won't enable them in gparted.

Edit: sorry OP, I initially mistyped a few of the package names by adding an extra "-", now corrected.

---

### Post by Bucky Ball on 2016-03-27
Ah, now I follow you. Doh! You want the greyed ones to be available to use to format your partitions. There's reasons they are not available, but I'm off out for awhile so no time to dig.

---

### Post by Dennis N on 2016-03-27
For some file systems, file system creation has no support in gparted (version 0.25.0):
exfat, f2fs, hfs, hfs+

For some file systems, all or some operations are supported provided extra support packages are installed:
2 examples:
hfs requires hfsprogs (providing limited support) 
reiserfs needs reiserfsprogs and reiserfs-utils  (providing complete support)

You can find this information yourself in **View > File System Support**.

---

### Post by yetimon_64 on 2016-03-27
> **Dennis N said:**
> ...
reiserfs needs reiserfsprogs and reiserfs-utils  (providing complete support)...

Is that the right package name for reiserfs full support, "reiserfs-utils"? I can't seem to find it here, I was going to add it to the above code box for the OP if I did find it ...
> ```
yetiman:~ $ apt-cache policy reiserfs-utils
N: Unable to locate package reiserfs-utils
```

Edit: good point about the limited support on some filesystems Dennis N, regarding the info in "**View > File System Support**".

---

### Post by Dennis N on 2016-03-27
> Is that the right package name for reiserfs full support, "reiserfs-utils"?
This is the package name the gparted chart gives. But, it is not in the repositories (working from 14.04). Only two packages start with "reiser":

```
dmn@Zotac:~$ apt-get -s install reiser
reiser4progs   reiserfsprogs
```

Perhaps either one mentioned in the chart is sufficient?

---

### Post by yetimon_64 on 2016-03-27
> **Dennis N said:**
> ...This is the package name the gparted chart gives...

Not on my install of gparted with the chart, only just checked the "View > File system support" fully, and it isn't even shown here. On 14.04 here as well :confused: Seems I got the needed 2 by using synaptic and "trial and error", thanks for pointing out the chart though, very useful to know that now.

See screenshot attached, no utils package for the reiser packages.
> 
Perhaps either one mentioned in the chart is sufficient?         Looks as if both are needed for the OP's request.

---

### Post by Dennis N on 2016-03-27
Here is screenshot of the chart from gparted 0.24.0 in my Xubuntu 14.04 and reiserfs-utils it is on that version. I was indeed working from 14.04 when I checked the repository, but working from Manjaro a few minutes before when I looked at the chart. Switched to another computer to check Ubuntu repository. The version on Manjaro was 0.25  and also had both showing. I will have to look if that package is in their repository.

Edit: Checked, and Manjaro doesn't have reiserfs-utils either. Probably gparted 0.24 and later shows the two possible options, older may not?

---

### Post by yetimon_64 on 2016-03-27
> **Dennis N said:**
> Here is screenshot of the chart from gparted 0.24.0 in my Xubuntu 14.04 and reiserfs-utils it is on that version. I was indeed working from 14.04 when I checked the repository, but working from Manjaro a few minutes before when I looked at the chart. Switched to another computer to check Ubuntu repository. The version on Manjaro was 0.25  and had both still showing.- guess they didn't change it there. I will have to look if that package is in their repository.

Aha, that makes much more sense now. Standard install of Unity 14.04 (Trusty) here with the 0.18.0-1 version from the repos. So it will make a bit of a difference package wise dependent on what distro and release the OP is using. Cheers, yeti.

> ```
yetiman:~ $ apt-cache policy gparted
gparted:
  Installed: 0.18.0-1
  Candidate: 0.18.0-1
  Version table:
 *** 0.18.0-1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by Bucky Ball on 2016-03-28
For exfat, install:

exfat-utils
exfat-fuse

That's it. Had to do it recently for an SD card I was using for some video.

---

### Post by yetimon_64 on 2016-03-28
@ Bucky Ball, If the OP is on stock unity 14.04 those 2 packages don't enable exfat support in gparted. Exfat support is currently disabled in gparted in my stock install with version 0.18.0-1. 

I suspect you are in the same position as Dennis N on Xubuntu going by your forum profile; in which case you are likely to be running the 0.24.0 version and may very well have managed to get it enabled with those 2 packages.

From my current 14.04 Unity install, with exfat disabled (greyed out) in gparted ...
> ```
yetiman:~ $ apt-cache policy exfat-fuse exfat-utils
exfat-fuse:
  Installed: 1.0.1-1
  Candidate: 1.0.1-1
  Version table:
 *** 1.0.1-1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
exfat-utils:
  Installed: 1.0.1-1
  Candidate: 1.0.1-1
  Version table:
 *** 1.0.1-1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
```

We will need to see what distro and release the OP is using for this to work by the looks of things. I am running on the usual assumption of a stock install of the latest LTS until notified otherwise by the OP. Cheers, yeti.

---

### Post by Bucky Ball on 2016-03-28
I am using Xubuntu-core 15.10. My version of exfat-utils is 1.1.1-1. extfat-fuse, 1.1.0.2.

Haven't done anything unusual, stock, and added no PPAs.

---

### Post by grace3 on 2016-03-28
> **Bucky Ball said:**
> 
Bottom line here is that where you are in the screenshot is about to obliterate all data on sda7 by reformatting it to another filesystem type.

I just did this so you could see the grayed out options. It was actually not very easy to take this photo. I had to set a timer on gnome-screenshot, then select a partition in GParted that would not break my OS if I fatfingered it, then crop the photo in GiMP. Kind of a lot of trouble actually. I have another distro that I've been experimenting with that uses different file systems, and when I tried to use gparted to check the user filesystem I noticed that that filesystem was not enabled. I punted and found a package in synaptic that looked like it might have what I needed and loaded it. Kind of like shotgunning car parts. Anyway it didn't enable everything. I just want to load the rest of the packages from synaptic or wherever, so I don't have to punt again, if I need another file system. Nicht Rocketenbau...

Danke

---

### Post by yetimon_64 on 2016-03-28
> **Bucky Ball said:**
> I am using Xubuntu-core 15.10. My version of exfat-utils is 1.1.1-1. extfat-fuse, 1.1.0.2.

Haven't done anything unusual, stock, and added no PPAs.

Yes as I suspected. The features enabled in gparted depend on what version of gparted is installed.
 
_*Are you on the same version of **gparted** as Dennis N with you being on Xubuntu, the 0.24.0 version (or higher) ?*_

As I noted earlier I am on a stock unity install of Ubuntu with the 0.18.0-1 version of gparted, with both of the exfat packages installed.

 I believe (I read a while back about version differences and features enabled) with the version of gparted in the 14.04 release, being 0.18.0-1, the functions for exfat are still greyed out when the support packages are installed. Installing the exfat packages won't necessarily enable the features unfortunately in an older version of gparted. Hope that makes a bit more sense. 

Even the packages for reiser, listed in the features window in gparted, are different between versions of gparted and the different distros used in this thread. Dennis N's version (screenshot supplied earlier) has the requirement for reiserfs-utils, my version (screenshot supplied earlier) makes NO mention of reiserfs-utils because of the differing distro, ubuntu vs xubuntu etc, and maybe because of the differing versions of gparted in use.

**@ OP**. grace3 what is your distro being used, Xubuntu or Ubuntu Unity ? And what release are you running, 14.04 the LTS release or later ?

---

### Post by Dennis N on 2016-03-28
I just installed gparted 0.25 in Xubuntu 16.04 beta1 (with all updates applied) and attached is the support grid. I interpret exfat has only the gparted support shown, regardless of other packages (none are shown). I think those other packages enable OS support of the exfat file system, not gparted support.

Edit: Then installed exfat-fuse and exfat-utils, restarted, but still had no option in gparted to format a partition with exfat fs in Partition > Format to: (still greyed out as unavailable)

---

### Post by Dennis N on 2016-03-28
_The gparted Chart is Dynamic_

The chart reflects the current state of support - with or without the packages on the right being installed. I looked at the btrfs row on the chart - it had nothing checked on mine, but had packages named on the right. I installed the btrfs-tools package, started gparted, clicked on the "rescan for supported actions" and the btrfs row changed to all green checks! Everything supported. The chart actually changes.  

exfat, however, does not change with the exfat packages - they aren't named, so don't help gparted do anything.

---

### Post by Bucky Ball on 2016-03-28
Gparted 0.2.2.0

---

### Post by grace3 on 2016-03-29
> **yetimon_64 said:**
> Yes as I suspected. The features enabled in gparted depend on what version of gparted is installed.
 
_*Are you on the same version of **gparted** as Dennis N with you being on Xubuntu, the 0.24.0 version (or higher) ?*_

As I noted earlier I am on a stock unity install of Ubuntu with the 0.18.0-1 version of gparted, with both of the exfat packages installed.

 I believe (I read a while back about version differences and features enabled) with the version of gparted in the 14.04 release, being 0.18.0-1, the functions for exfat are still greyed out when the support packages are installed. Installing the exfat packages won't necessarily enable the features unfortunately in an older version of gparted. Hope that makes a bit more sense. 

Even the packages for reiser, listed in the features window in gparted, are different between versions of gparted and the different distros used in this thread. Dennis N's version (screenshot supplied earlier) has the requirement for reiserfs-utils, my version (screenshot supplied earlier) makes NO mention of reiserfs-utils because of the differing distro, ubuntu vs xubuntu etc, and maybe because of the differing versions of gparted in use.

**@ OP**. grace3 what is your distro being used, Xubuntu or Ubuntu Unity ? And what release are you running, 14.04 the LTS release or later ?

Distro Ubuntu TT 14.04.3, GParted 0.18.0. The packages you recommended enabled everything except exfat & ufs. I still have not been able to activate these. How do I upgrade GParted? Thanks, Grace

---

### Post by yetimon_64 on 2016-03-29
> **grace3 said:**
> Distro Ubuntu TT 14.04.3, GParted 0.18.0. The packages you recommended enabled everything except exfat & ufs. I still have not been able to activate these. How do I upgrade GParted? Thanks, Grace

Did you also try installing the packages Bucky Ball noted, exfat-utils and exfat-fuse ? I have them installed here but still have the option greyed out in gparted on the 0.18.0 version in Trusty.

"ufs" is one I have never been able to enable and gave up on it a while back. I suspect upgrading to 16.04 when it comes out may possibly install a newer gparted version and may fix the exfat issue. In the meantime a PPA may possibly help for exfat.

Just checked, the "getdeb" PPA has the 0.24.0-1~getdeb1 version and may possibly help enable exfat support in gparted. Instructions for installing getdeb are [[COLOR=#0000ff]--here--[/COLOR]]("http://www.ubuntuupdates.org/ppa/getdeb_apps?dist=trusty") if you wish to try it out. I haven't tested this PPA myself and don't know how good it is, just that it can supply a much newer version of gparted than 14.04 normally supplies.

**Edit**: just for the record a PPA is a Personal Package Archive, it is not from the official repositories and you should be aware that on occasions using such sources can present some risks. Again I am not familiar with how good getdeb is, use with care in such circumstances or wait for further advice from other helpers regarding the use of the getdeb PPA.

---

### Post by Dennis N on 2016-03-29
> Distro Ubuntu TT 14.04.3, GParted 0.18.0. The packages you recommended enabled everything except exfat & ufs.
You won't be able to add capabilities that are not already shown on the **View > File System Support** chart for these two.
>  How do I upgrade GParted?
My gparted 0.24 came from here:
[http://www.ubuntuupdates.org/package/getdeb_apps/trusty/apps/getdeb/gparted](http://www.ubuntuupdates.org/package/getdeb_apps/trusty/apps/getdeb/gparted)

---

### Post by Bucky Ball on 2016-03-29
You are going to great lengths for something that you may never actually use. Is it worth upgrading Gparted from a PPA and stepping outside the Ubuntu repositories? Do you foresee a time when you are going use this functionality? Eight years on and I've never had the need. Not to say you won't. :-k

---

### Post by Dennis N on 2016-03-29
Version 0.24 has better GPT partition table support, which is why I upgraded my 14.04 to that version. It can handle partition names as well as file system labels, for one thing. I've been using the package from the included link for a long time.

---

### Post by yetimon_64 on 2016-03-29
> **Bucky Ball said:**
> You are going to great lengths for something that you may never actually use. Is it worth upgrading Gparted from a PPA and stepping outside the Ubuntu repositories? Do you foresee a time when you are going use this functionality? Eight years on and I've never had the need. Not to say you won't. :-k

+1, and PPAs do carry some risk. 

Best to weigh up needs vs potential risks in such a case OP.

---

### Post by grace3 on 2016-03-31
> **yetimon_64 said:**
> Did you also try installing the packages Bucky Ball noted, exfat-utils and exfat-fuse ? I have them installed here but still have the option greyed out in gparted on the 0.18.0 version in Trusty.

"ufs" is one I have never been able to enable and gave up on it a while back. I suspect upgrading to 16.04 when it comes out may possibly install a newer gparted version and may fix the exfat issue. In the meantime a PPA may possibly help for exfat.

Just checked, the "getdeb" PPA has the 0.24.0-1~getdeb1 version and may possibly help enable exfat support in gparted. Instructions for installing getdeb are [[COLOR=#0000ff]--here--[/COLOR]]("http://www.ubuntuupdates.org/ppa/getdeb_apps?dist=trusty") if you wish to try it out. I haven't tested this PPA myself and don't know how good it is, just that it can supply a much newer version of gparted than 14.04 normally supplies.

**Edit**: just for the record a PPA is a Personal Package Archive, it is not from the official repositories and you should be aware that on occasions using such sources can present some risks. Again I am not familiar with how good getdeb is, use with care in such circumstances or wait for further advice from other helpers regarding the use of the getdeb PPA.

exfat-utils and exfat-fuse didn't help.  I was however able to upgrade to gparted 0.24.0, which didn't buy me anything.

---

### Post by Dennis N on 2016-04-01
If you need to create an exfat file system, you instead would just make use of the exfat-utils you installed. In the terminal: **sudo mkfs.exfat /dev/sdc1** for example. Check manpage of mkfs.exfat for more information and options.

---

