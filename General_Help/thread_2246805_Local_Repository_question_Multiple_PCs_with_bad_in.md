---
title: "Local Repository question: Multiple PCs with bad internet connection"
date: 2014-10-03
forum: General Help
---

### Post by DVD-R on 2014-10-03
I apologize if this is the wrong section of the forum for this question.....if so, please feel to move it.

I have a situation where I have multiple PCs which I want to maintain Ubuntu in.
But the internet service is terrible!!
When it is running, users have to be careful not to download data or access streaming-data, as it slows down usage for other users.

I would like to investigate the possibility of downloading a full copy of the Ubuntu 12.04 repository into a thumb drive.
And then when I need to add an application to any one of the PCs, I can simply plug in the thumb drive and use apt to install the application.
I know I will have to configure the sources.list file to look for the thumb drive, and I will probably have to be careful to only have that one thumb drive plugged in, so that its mounting matches what is in the sources.list file.

Has anyone ever done anything like this?
Sincere thanks!!!

---

### Post by varunendra on 2014-10-06
> **DVD-R said:**
> I would like to investigate the possibility of downloading a full copy of the Ubuntu 12.04 repository into a thumb drive.
....
Has anyone ever done anything like this?

In fact there are full tutorials for doing this. But if you mean 'complete' repository mirror, be aware that the current repository sizes are above 35 GB (perhaps even close to 50 GB now).

You should also know that there are trusted services that can provide you a DVD set of the repositories for a marginal price (for those who don't have super fast internet connections, it actually becomes cheaper to just order a set of these DVDs).

But if you still want to do it yourself, here is a good tutorial : [http://www.zyxware.com/articles/2657/how-to-mirror-the-entire-ubuntu-software-repository-locally-and-to-create-your-own-ubuntu-repository-dvds](http://www.zyxware.com/articles/2657/how-to-mirror-the-entire-ubuntu-software-repository-locally-and-to-create-your-own-ubuntu-repository-dvds)

The above tutorial is from one of such services who provide these repository DVDs. It is India based and once I personally ordered a 7-DVD set of Ubuntu Studio 9.04 + full repositories which actually cost me about just as much as the cost of blank DVDs + normal courier charges.

Official Ubuntu Wiki : [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

However, if you know or can guess ALL the packages that your users may ever need on the concerned version of Ubuntu, I personally recommend using AptOnCD method. I personally use it frequently, and except for some minor glitches *sometimes* (which I now know how to take care of in advance), it works really smooth : [https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)

---

### Post by DVD-R on 2014-10-23
Thank you very much Varun!
I've contacted the ZYXWare people and asked about the cost of the repository in U.S. currency.

Actually, I maybe kind of close to being able to do it myself....but I'm confused about how the Repository files are configured.
For example:   [http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/](http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/)  has the three index files (Packages, Packages.gz and Release)
Its pretty easy to see that those files are pertinent to Ubuntu "Precise".
But one has to navigate up the server path to get to the actual package folders:
[http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/) ( Main, Multiverse, Restricted, and Universe)
I'm getting the impression that there is only one repository of packages, which are used for all Ubuntu versions because those folders where the actual packages are are not distro specific.
I can use WGET to download package files from [http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/)
But I'm not sure that those files are applicable to "Precise".
What am I missing??
Thanks!!  :-]

---

### Post by deadflowr on 2014-10-23
Instead of something like apt offline, you might look into setting up an apt-cache server
[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)

Basically, the one machine will update the repos, and all others will update from that.
Locally.
Keeping it so only one machine needs to connect to the 'net
If that helps.

---

