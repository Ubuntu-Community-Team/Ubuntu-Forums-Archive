---
title: "Ubuntu 18.04 bionic all repositories for offline."
date: 2023-02-27
forum: General Help
---

### Post by cwoelfle on 2023-02-27
I have 2 ubuntu 18.04 systems. One has internet, the other does not. I need to update the packages on the offline one. I have read several posts regarding apt-mirror and apt-offline and apache and all that, but I cant do what most of them suggest since both systems are on seperate networks. I need some advice on how I can download the entire ubuntu repo to a usb so I can move it to the offline system and install all the packages that I need. Is this even possible? If so how would I go about this?

---

### Post by TheFu on 2023-02-27
> **cwoelfle said:**
> I have 2 ubuntu 18.04 systems. One has internet, the other does not. I need to update the packages on the offline one. I have read several posts regarding apt-mirror and apt-offline and apache and all that, but I cant do what most of them suggest since both systems are on seperate networks. I need some advice on how I can download the entire ubuntu repo to a usb so I can move it to the offline system and install all the packages that I need. Is this even possible? If so how would I go about this?

In theory, if you run Synaptic on those systems, it can create a list of dependencies needed.
Standard support for 18.04 ends in a few months and it will only be harder and harder to move to one of the newer, supported, released when that happens - at least without paying.  It is time, actually, it is last minute, for moving to a newer release. We have about two months. I'm in the same boat with you, BTW.  Moved 2 systems last week.  10 more to go.

---

### Post by ActionParsnip on 2023-02-28
Why 18.04? It goes end of life at at the end of April this year....You could use this as a catalyst to wipe the install off and do a clean install of Jammy. Jammy is LTS and supported until April 2027

---

### Post by cwoelfle on 2023-02-28
> **TheFu said:**
> In theory, if you run Synaptic on those systems, it can create a list of dependencies needed.
Standard support for 18.04 ends in a few months and it will only be harder and harder to move to one of the newer, supported, released when that happens - at least without paying. It is time, actually, it is last minute, for moving to a newer release. We have about two months. I'm in the same boat with you, BTW. Moved 2 systems last week. 10 more to go.

> **ActionParsnip said:**
> Why 18.04? It goes end of life at at the end of April this year....You could use this as a catalyst to wipe the install off and do a clean install of Jammy. Jammy is LTS and supported until April 2027


Because that is what my company has approved. To put it in one word Bureaucracy. I don't have control over what version. I have to implement the security measures for it. But since I am struggling to get all the packages, that is proving to be quite hard.

Do you folks have any advice to help me with my situation?

---

### Post by ActionParsnip on 2023-02-28
Bionic has about 5 weeks of support left

---

### Post by mIk3_08 on 2023-02-28
I was one fan of this 18.04. But sad to say it is near to end. We need now to move on. Moving on is always part of our life. Regards and cheers.

---

### Post by cwoelfle on 2023-02-28
> **ActionParsnip said:**
> Bionic has about 5 weeks of support left

How much support is left is not relevant to this post.

---

### Post by TheFu on 2023-02-28
> **cwoelfle said:**
> 
Do you folks have any advice to help me with my situation?

I haven't worked in air-gapped networks in over a decade, so no.  One of our systems has always been running apt-cacher-ng which becomes a caching and proxy server for systems that cannot directly access the internet.

However, if I were in your situation - and I have been - I'd get a written "acceptance of risk" letter signed by someone with the authority to sign that risk acceptances for the company.  That's usually a corporate officer.  The letter doesn't need to be long. 1 paragraph is find, with addendums showing the supported periods for whatever release is required.  Many times, I've been thanked by the CIO for letting them know about the issue, since nobody else wanted to tell them.  If they don't know about it, then they can't work the problem.  In this specific situation, paid support is available for 18.04 through their ESM offer.  [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)

A few months ago, someone else here asked the solution for offline driver updates.  For most of us, it is a chicken/egg problem.  After suggesting a $10 USB dongle, I did some research and found a few possible options that didn't require internet for the specific machine.  Synaptic was one of them, but that's a GUI, so not really available to a server.  There were some scripts that would gather a list of dependencies and generate all the packages needed to be pulled for any packages not already on the system.  There are flaws with this.

You could mirror the repos used completely, then place that mirror somewhere that the off-line system(s) can access, modify the APT repos to point at it.  I'm a little vague on how to accomplish this, but I know that apt-cacher-ng does allow pre-loading packages to a specific location.  For example:
```
$ ls -l /var/cache/apt-cacher-ng/uburep/pool
total 12
drwxr-sr-x 47 apt-cacher-ng apt-cacher-ng 4096 Feb 15 12:26 main/
drwxr-sr-x  5 apt-cacher-ng apt-cacher-ng 4096 Jan 10 15:31 restricted/
drwxr-sr-x 48 apt-cacher-ng apt-cacher-ng 4096 Feb 28 08:30 universe/
```

Those contain the different repo packages for my different APT-based systems.  Under uburep/ is where the Canonical releases and the core, backports, security, and updates repos are located for the different releases still in use here.  When I first setup apt-cacher-ng, I copied most of the existing cached .deb files into the place the README said to prevent downloading them again.  For me, having most of the packages downloaded only once was worth the effort.  Only 8G is used:
```
$ du -sh /var/cache/apt-cacher-ng/
7.4G    /var/cache/apt-cacher-ng/
```
for all the different releases.

Whether any of this is helpful do you or not, only you can say.

---

### Post by cwoelfle on 2023-02-28
> **TheFu said:**
> I haven't worked in air-gapped networks in over a decade, so no.  One of our systems has always been running apt-cacher-ng which becomes a caching and proxy server for systems that cannot directly access the internet.

However, if I were in your situation - and I have been - I'd get a written "acceptance of risk" letter signed by someone with the authority to sign that risk acceptances for the company.  That's usually a corporate officer.  The letter doesn't need to be long. 1 paragraph is find, with addendums showing the supported periods for whatever release is required.  Many times, I've been thanked by the CIO for letting them know about the issue, since nobody else wanted to tell them.  If they don't know about it, then they can't work the problem.  In this specific situation, paid support is available for 18.04 through their ESM offer.  [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)

A few months ago, someone else here asked the solution for offline driver updates.  For most of us, it is a chicken/egg problem.  After suggesting a $10 USB dongle, I did some research and found a few possible options that didn't require internet for the specific machine.  Synaptic was one of them, but that's a GUI, so not really available to a server.  There were some scripts that would gather a list of dependencies and generate all the packages needed to be pulled for any packages not already on the system.  There are flaws with this.

You could mirror the repos used completely, then place that mirror somewhere that the off-line system(s) can access, modify the APT repos to point at it.  I'm a little vague on how to accomplish this, but I know that apt-cacher-ng does allow pre-loading packages to a specific location.  For example:
```
$ ls -l /var/cache/apt-cacher-ng/uburep/pool
total 12
drwxr-sr-x 47 apt-cacher-ng apt-cacher-ng 4096 Feb 15 12:26 main/
drwxr-sr-x  5 apt-cacher-ng apt-cacher-ng 4096 Jan 10 15:31 restricted/
drwxr-sr-x 48 apt-cacher-ng apt-cacher-ng 4096 Feb 28 08:30 universe/
```



Those contain the different repo packages for my different APT-based systems.  Under uburep/ is where the Canonical releases and the core, backports, security, and updates repos are located for the different releases still in use here.  When I first setup apt-cacher-ng, I copied most of the existing cached .deb files into the place the README said to prevent downloading them again.  For me, having most of the packages downloaded only once was worth the effort.  Only 8G is used:
```
$ du -sh /var/cache/apt-cacher-ng/
7.4G    /var/cache/apt-cacher-ng/
```
for all the different releases.

Whether any of this is helpful do you or not, only you can say.

Thanks for this write up. You are correct that I am in an air gapped environment with a lot of regulations. I appreciate you actually taking the time to try and help me address my issue. I will give this a try and see if I can make any progress. I will report back any findings here.

---

### Post by TheFu on 2023-02-28
> **cwoelfle said:**
> Thanks for this write up. You are correct that I am in an air gapped environment with a lot of regulations. I appreciate you actually taking the time to try and help me address my issue. I will give this a try and see if I can make any progress. I will report back any findings here.

I worked in both secure govt environments (buildings inside Faraday cage protection) AND in extremely regulated industries.  I get it.  There are a few things like you are asking that enterprises need, but it is niche, so not address clearly.

[https://ostechnix.com/fully-update-upgrade-offline-debian-based-systems/](https://ostechnix.com/fully-update-upgrade-offline-debian-based-systems/) is ```
apt-offline
```. I've never used it and don't know if this is a lead or not. Hope it works.

---

### Post by MAFoElffen on 2023-02-28
> **TheFu said:**
> 
[COLOR=#ff0000]You could mirror the repos used completely, then place that mirror somewhere that the off-line system(s) can access, modify the APT repos to point at it.  I'm a little vague on how to accomplish this[/COLOR], but I know that apt-cacher-ng does allow pre-loading packages to a specific location.  For example:

Dang. It's been years and makes me feel old... I know this answer because I used to do it... It used to be documented how to do this and how to set it up in the "Ubuntu Server Guide" (or in the Wiki somewhwere) and I don't know that anyone has mentioned anything about it since Ubuntu 20.04.

What I used to do was to setup a local network attached Apache Server for internal use only, then install the package 'apt-mirror' to replicate the Ubuntu Repo's to create a Local (Ubuntu) repo. This takes at least 250 GB of disk space for each release version.
[https://kc.jetpatch.com/hc/en-us/articles/360052181591-Setting-Up-Local-Repositories-Ubuntu-16-04-18-04-20-04](https://kc.jetpatch.com/hc/en-us/articles/360052181591-Setting-Up-Local-Repositories-Ubuntu-16-04-18-04-20-04)

Later there was the package 'debmirror', that the Ubuntu Help wiki mentioned 'apt-catcher-ng'... [https://help.ubuntu.com/community/Debmirror](https://help.ubuntu.com/community/Debmirror)

Just trying to weed through the cobwebs. (LOL)

EDIT: Remembered another path: [https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)

---

### Post by cwoelfle on 2023-03-01
> **MAFoElffen said:**
> Dang. It's been years and makes me feel old... I know this answer because I used to do it... It used to be documented how to do this and how to set it up in the "Ubuntu Server Guide" (or in the Wiki somewhwere) and I don't know that anyone has mentioned anything about it since Ubuntu 20.04.

What I used to do was to setup a local network attached Apache Server for internal use only, then install the package 'apt-mirror' to replicate the Ubuntu Repo's to create a Local (Ubuntu) repo. This takes at least 250 GB of disk space for each release version.
[https://kc.jetpatch.com/hc/en-us/articles/360052181591-Setting-Up-Local-Repositories-Ubuntu-16-04-18-04-20-04](https://kc.jetpatch.com/hc/en-us/articles/360052181591-Setting-Up-Local-Repositories-Ubuntu-16-04-18-04-20-04)

Later there was the package 'debmirror', that the Ubuntu Help wiki mentioned 'apt-catcher-ng'... [https://help.ubuntu.com/community/Debmirror](https://help.ubuntu.com/community/Debmirror)

Just trying to weed through the cobwebs. (LOL)

EDIT: Remembered another path: [https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)

This is one route, but can we do this without an apahe server? The system that has the internet is not inn anyway connected to the one that is airgapped and has no internet. that is my issue haha.

Edit: The personal repository looks very promising.

---

### Post by MAFoElffen on 2023-03-01
The personal repo, since it goes to disk in a driectory, and doesn't use a webserver, was something I used to replicate on a USB jump drive drive... Sort of. That only gets the packages of what is installed on 'that' specific machine. Very portable. But doesn't include verything in the repo's.

I did this instead: [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository) . The full copy of the online repo. Like I said, over 250 GB of data for each release version that you use, so the initial setup is going to take time. Sync / Update after that is not as long.

I used to sync the repo's from my workstation... Then I had it "to go" on that drive, to go other machines. For other machines, I just mounted the drive to /mnt, backed up the sources.list, having a copy of a sources.list, and copied in a sources.list that pointed to the folder on the mounted drive. Then I had a portable offline repo.

---

### Post by cwoelfle on 2023-03-01
> **MAFoElffen said:**
> The personal repo, since it goes to disk in a driectory, and doesn't use a webserver, was something I used to replicate on a USB jump drive drive... Sort of. That only gets the packages of what is installed on 'that' specific machine. Very portable. But doesn't include verything in the repo's.

I did this instead: [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository) . The full copy of the online repo. Like I said, over 250 GB of data for each release version that you use, so the initial setup is going to take time. Sync / Update after that is not as long.

I used to sync the repo's from my workstation... Then I had it "to go" on that drive, to go other machines. For other machines, I just mounted the drive to /mnt, backed up the sources.list, having a copy of a sources.list, and copied in a sources.list that pointed to the folder on the mounted drive. Then I had a portable offline repo.

Is there not a command you could use to download all available apt packages to one and make one that way?

---

### Post by TheFu on 2023-03-01
> **cwoelfle said:**
> Is there not a command you could use to download all available apt packages to one and make one that way?

[https://manpages.ubuntu.com/manpages/bionic/man1/apt-mirror.1.html](https://manpages.ubuntu.com/manpages/bionic/man1/apt-mirror.1.html)

---

### Post by MAFoElffen on 2023-03-01
The first link I gave you ([https://kc.jetpatch.com/hc/en-us/articles/360052181591-Setting-Up-Local-Repositories-Ubuntu-16-04-18-04-20-04](https://kc.jetpatch.com/hc/en-us/articles/360052181591-Setting-Up-Local-Repositories-Ubuntu-16-04-18-04-20-04)) goes over installing and configuring the apt-mirror package, before using the apt-mirror command... You can configure apt-mirror to send to a local drive, network share or portable USB drive.... To create a local repo. (Step #1, Tasks 6-12)

You don't have to install Apache if on some type of shared drive. The other computers just need some kind of paths to point to it in the sources.list.

---

