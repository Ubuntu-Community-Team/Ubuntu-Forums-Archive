---
title: "Install Everpad in Ubuntu 16.04"
date: 2016-05-24
forum: General Help
---

### Post by kwanbis on 2016-05-24
I'm trying to install Everpad in Ubuntu 16.04. According to their website I have to do:

sudo add-apt-repository ppa:nvbn-rm/ppa
sudo apt-get update
sudo apt-get install everpad

But when I do the second line, I get:

```
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:7
W: [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:) Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:) Signature by key 3B068FB4789ABE4AEFA3BB491397BC53640DB551 uses weak digest algorithm (SHA1)
W: The repository 'http://ppa.launchpad.net/bodiltv/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/midori/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/bodiltv/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/bodiltv/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
E: Failed to fetch [http://ppa.launchpad.net/bodiltv/ppa/ubuntu/dists/xenial/main/binary-i386/Packages](http://ppa.launchpad.net/bodiltv/ppa/ubuntu/dists/xenial/main/binary-i386/Packages)  404  Not Found
E: Failed to fetch [http://ppa.launchpad.net/midori/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/midori/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
E: Failed to fetch [http://ppa.launchpad.net/midori/ppa/ubuntu/dists/xenial/main/binary-i386/Packages](http://ppa.launchpad.net/midori/ppa/ubuntu/dists/xenial/main/binary-i386/Packages)  404  Not Found
E: Failed to fetch [http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
E: Failed to fetch [http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu/dists/xenial/main/binary-i386/Packages](http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu/dists/xenial/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:7
```

And when I do the last line, I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package everpad

How can I do fix it? THANKS!

---

### Post by howefield on 2016-05-24
There is no xenial repository for [http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu](http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu) so there is no everpad package for you to get.

Seems that it is only as current as the Vivid cycle.

---

### Post by kwanbis on 2016-05-24
> **howefield said:**
> There is no xenial repository for [http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu](http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu) so there is no everpad package for you to get.

Seems that it is only as current as the Vivid cycle.
So, do I need to wait for updated packages?

And does this means that for each ubuntu release a different package is needed? That seems very unpractical.

---

### Post by howefield on 2016-05-24
> **kwanbis said:**
> So, do I need to wait for updated packages?

Well, you should really ask that of the ppa maintainer(s) but it looks like updated packages may not be very likely, there aren't any for Wily either. As I mentioned, the packages only go to the Vivid cycle. Looks like Everpads development has stopped or stalled.

Perhaps there is another ppa or alternative application ?

---

### Post by kwanbis on 2016-05-24
> **howefield said:**
> Perhaps there is another ppa or alternative application ?
I have no idea. I just want to use Evernote or an app like it. I would research it.

By the way, why is it that for each version a new app is needed? I can use apps from windows XP in windows 7, shouldn't it be the same for Linux?

---

### Post by howefield on 2016-05-24
> **kwanbis said:**
> By the way, why is it that for each version a new app is needed? I can use apps from windows XP in windows 7, shouldn't it be the same for Linux?

Well, you could use the package from the Vivid repository and it might work just as some applications might work in both XP and Windows 7, but that won't be the case for every application, windows included. For reasons of version numbers and dependancies it isn't recommended that you mix repositories. It isn't necessarily a new version of everpad that you need but one that is tested to work with the newer Ubuntu releases. 

The problem here is that development of Everpad has stalled, if you want to take the risk of something going wrong you could download the everpad deb package from the ppa and double click to install it. It might work but you won't get updates.

I don't know everpad and have never used it, I'm just trying to help you understand why you are having an issue, I have heard a few of the staff talk about Zim, I'm not sure how it compares to everpad but it might be worth taking a look at. You can install it with apt or via the Software Centre.

---

### Post by kwanbis on 2016-05-24
> **howefield said:**
> Well, you could use the package from the Vivid repository and it might work just as some applications might work in both XP and Windows 7, but that won't be the case for every application, windows included. For reasons of version numbers and dependancies it isn't recommended that you mix repositories. It isn't necessarily a new version of everpad that you need but one that is tested to work with the newer Ubuntu releases. 

The problem here is that development of Everpad has stalled, if you want to take the risk of something going wrong you could download the everpad deb package from the ppa and double click to install it. It might work but you won't get updates.

I don't know everpad and have never used it, I'm just trying to help you understand why you are having an issue, I have heard a few of the staff talk about Zim, I'm not sure how it compares to everpad but it might be worth taking a look at. You can install it with apt or via the Software Centre.
I'm on the linux side, so bear with me. I believe that most of the Windows XP apps would work today in Windows 10. Why wouldn't it be the case with linux? Is it a dependencies thing? 

Everpad appears to be a linux client for Evernote. That said, I just moved to Simplenote, but I'm still wondering about this thing you mention. With releases each 6 months it seems impractical the need to have different releases for each ubuntu version, I don't know if you understand my point.

---

### Post by Aubrey_Robertson on 2016-05-25
> **kwanbis said:**
> I'm on the linux side, so bear with me. I believe that most of the Windows XP apps would work today in Windows 10. Why wouldn't it be the case with linux? Is it a dependencies thing? 

Everpad appears to be a linux client for Evernote. That said, I just moved to Simplenote, but I'm still wondering about this thing you mention. With releases each 6 months it seems impractical the need to have different releases for each ubuntu version, I don't know if you understand my point.

You might want to try NixNote.  Apparently it's a pretty deep Evernote client which works on 16.04.

[http://www.wolffhaven45.com/blog/linux/installing-nixnote-ubuntu-16-04/](http://www.wolffhaven45.com/blog/linux/installing-nixnote-ubuntu-16-04/)

---

### Post by kwanbis on 2016-05-30
So I finally "fixed" it by using Simplenote, which provides a proper unix cliente.

---

