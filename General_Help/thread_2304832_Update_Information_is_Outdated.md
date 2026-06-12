---
title: "Update Information is Outdated"
date: 2015-11-30
forum: General Help
---

### Post by leo47 on 2015-11-30
Hi,

I found another thread where someone was experiencing this same problem, but for me, I can't figure would which box to untick in order to solve my problem. I have that the little icon on the top of my screen telling me that the update information is outdated. I'm assuming it's a problem with one of the repositories. When I sudo apt-get update I get the following errors:

W: Failed to fetch [http://ppa.launchpad.net/gnomebaker/stable/ubuntu/dists/oneiric/Release](http://ppa.launchpad.net/gnomebaker/stable/ubuntu/dists/oneiric/Release)  Unable to find expected entry 'deb-src/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://ppa.launchpad.net/gnomebaker/stable/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/gnomebaker/stable/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gnomebaker/stable/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/gnomebaker/stable/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found


I'm assuming I fix this problem by going System Settings->Software & Updates->Other Software and then unticking one of these boxes, but based on the errors I can't work out which one to untick. Here is a screenshot of the Software & Updates window.

[IMG]http://i68.tinypic.com/29wthdh.png[/IMG]

Any help is greatly appreciated.

---

### Post by matt_symes on 2015-11-30
Hi

In your attached picture, you want to uncheck the fourth one from the top and the last one you can see at the bottom. I.E All the ones that are checked and contain the text gnomebaker.

Then update.

Post back any errors.

EDIT: Welcome to the forums :)

Kind regards

---

### Post by slickymaster on 2015-11-30
> **leo47 said:**
> Hi,

I found another thread where someone was experiencing this same problem, but for me, I can't figure would which box to untick in order to solve my problem. I have that the little icon on the top of my screen telling me that the update information is outdated. I'm assuming it's a problem with one of the repositories. When I sudo apt-get update I get the following errors:

[B][COLOR=#ff0000]W: Failed to fetch [/COLOR][[COLOR=#ff0000]http://ppa.launchpad.net/gnomebaker/stable/ubuntu/dists/oneiric/Release[/COLOR]]("http://ppa.launchpad.net/gnomebaker/stable/ubuntu/dists/oneiric/Release")[COLOR=#ff0000]  Unable to find expected entry 'deb-src/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [/COLOR][[COLOR=#ff0000]http://ppa.launchpad.net/gnomebaker/stable/ubuntu/dists/trusty/main/binary-amd64/Packages[/COLOR]]("http://ppa.launchpad.net/gnomebaker/stable/ubuntu/dists/trusty/main/binary-amd64/Packages")[COLOR=#ff0000]  404  Not Found

W: Failed to fetch [/COLOR][[COLOR=#ff0000]http://ppa.launchpad.net/gnomebaker/stable/ubuntu/dists/trusty/main/binary-i386/Packages[/COLOR]]("http://ppa.launchpad.net/gnomebaker/stable/ubuntu/dists/trusty/main/binary-i386/Packages")[COLOR=#ff0000]  404  Not Found
[/COLOR][/B]

I'm assuming I fix this problem by going System Settings->Software & Updates->Other Software and then unticking one of these boxes, but based on the errors I can't work out which one to untick. Here is a screenshot of the Software & Updates window.

[IMG]http://i68.tinypic.com/29wthdh.png[/IMG]

Any help is greatly appreciated.
The ones I highlighted in red are the ones you need to uncheck.

---

### Post by leo47 on 2015-11-30
Thanks guys! Problem solved!

---

