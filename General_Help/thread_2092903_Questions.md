---
title: "Questions"
date: 2012-12-09
forum: General Help
---

### Post by anon_private on 2012-12-09
What does it mean if a version of Ubuntu is unsupported?

Is it true that downloading an operating system using wifi is unlikely to be successful, due to errors (often unrecognised)?


Thanks

---

### Post by alexandari on 2012-12-09
Ubuntu has normal and long term releases (LTS) . The long term releases are more stable (in theory). When a version is unsupported,means that Ubuntu have moved on supporting the next releases,which means you won't be able to download updates,packages etc etc for that release in particular. The wifi thing sounds ridicilous

---

### Post by Impavidus on 2012-12-09
I don't know about the error rate of wifi connections versus wired connections, but if you check the md5 sum after downloading you should detect any errors so you can just try again. No problem with unrecognised errors.

---

### Post by anon_private on 2012-12-09
> **alexandari said:**
> Ubuntu has normal and long term releases (LTS) . The long term releases are more stable (in theory). When a version is unsupported,means that Ubuntu have moved on supporting the next releases,which means you won't be able to download updates,packages etc etc for that release in particular. The wifi thing sounds ridicilous


Thanks for responding.

If someone wanted to download an application say abiword with an unsupported version of Ubuntu should that be possible?

I have failed to connect to abiword at the software centre with an unsupported version of ubuntu. Is this to be expected?

Thanks

---

### Post by Impavidus on 2012-12-09
> **anon_private said:**
> Thanks for responding.

If someone wanted to download an application say abiword with an unsupported version of Ubuntu should that be possible?

I have failed to connect to abiword at the software centre with an unsupported version of ubuntu. Is this to be expected?

Thanks
Yes, that's possible and yes, that's to be expected.

If you're using an unsupported version of ubuntu you can only download, install and update software manually, which is such a nasty way of doing things that you'd better avoid it by having a supported version of ubuntu. In an unsupported version the software centre is useless.

---

### Post by Paddy Landau on 2012-12-09
If you are worried about the quality of your Internet connection, try using Torrent to download Ubuntu.

Torrent automatically checks the MD5 sum, and automatically restarts the download from where it left off if your Internet connection is interrupted. It guarantees that when it finishes, your file is uncorrupted.

Find the Ubuntu torrents at the [alternative downloads page]("http://www.ubuntu.com/download/desktop/alternative-downloads"); scroll down to BitTorrent and select either desktop-i386 (for 32-bit) or desktop-amd64 (for 64-bit).

(BTW, please use a descriptive title for your post. "Questions" does not tell us what the post is about.)

---

### Post by Sef on 2012-12-09
> What does it mean if a version of Ubuntu is unsupported?


Usually Ubuntu is supported for 18 months. After that no more updates, so a hole in the system would not be updated.

LTS (Long-Term Support) were originally for 5 years server and 3 years on the desktop. However, with Ubuntu 12.04, both the server and the desktop are supported for 5 years.

---

### Post by oldos2er on 2012-12-09
> **anon_private said:**
> If someone wanted to download an application say abiword with an unsupported version of Ubuntu should that be possible?


Yes, it's possible using old releases repositories, [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

But the best solution is to upgrade to a supported version of Ubuntu. If you have a lower spec computer you could try Xubuntu or Lubuntu, 12.04.

---

### Post by Kirk Schnable on 2012-12-09
> **Impavidus said:**
> I don't know about the error rate of wifi connections versus wired connections, but if you check the md5 sum after downloading you should detect any errors so you can just try again. No problem with unrecognised errors.

When downloading with a TCP protocol like HTTP, error rate of the connection is irrelevant because TCP performs its own integrity checks on every packet, and asks for it to be retransmitted if it is corrupted. 

As discussed in the Wikipedia article about TCP:
[http://en.wikipedia.org/wiki/Transmission_Control_Protocol#Reliable_transmission]("http://en.wikipedia.org/wiki/Transmission_Control_Protocol#Reliable_transmission")

Or as explained in this TCP joke:
> A TCP packet walks into a bar, and says to the bartender "I'd like a beer."  The bartender asks "You wanted a beer?" The TCP packet responds "Yes, I'd like a beer."

I'd tell you a UDP joke too, but you probably wouldn't get it...

---

### Post by anon_private on 2012-12-09
> **Kirk Schnable said:**
> When downloading with a TCP protocol like HTTP, error rate of the connection is irrelevant because TCP performs its own integrity checks on every packet, and asks for it to be retransmitted if it is corrupted. 

As discussed in the Wikipedia article about TCP:
[http://en.wikipedia.org/wiki/Transmission_Control_Protocol#Reliable_transmission]("http://en.wikipedia.org/wiki/Transmission_Control_Protocol#Reliable_transmission")

Or as explained in this TCP joke:


I'd tell you a UDP joke too, but you probably wouldn't get it...

And then the bar tender gives him a scotch.

---

### Post by anon_private on 2012-12-09
Can Windows applications be run using a LiveCD?

In Lubuntu 12.04 how can I enable the English (UK) keyboard?

---

### Post by 1clue on 2012-12-09
The wifi error rate thing is either a myth or a left-over from when wifi was experimental.  I've downloaded distros over wifi for more than a decade with no problem.

If the distro is unsupported, then give a serious thought to scraping it off and putting on something more recent.

I use xubuntu on fast hardware just for its simplity, but it's also a very lightweight environment that works well with older hardware.

---

### Post by Paddy Landau on 2012-12-10
> **anon_private said:**
> Can Windows applications be run using a LiveCD?
Windows applications can be run using a product called WINE and, optionally, using PlayOnLinux to make it easy for you.

But…

WINE is far from perfect. Most Windows applications will not run on Linux; many will run but with problems; and a few will run perfectly. Refer to the [WINE database]("http://appdb.winehq.org/") to see if the application you want has been tested.

Live CD: You would have to install WINE (and PlayOnLinux, if you want it), and run from there. It is likely to run very slowly from a Live CD. Windows itself, of course, does not have a Live CD.

> **1clue said:**
> I've downloaded distros over wifi for more than a decade with no problem.I had a problem only once, and it turned out to be the mirror at fault, not the wi-fi.

> **1clue said:**
> I use xubuntu on fast hardware just for its simplity, but it's also a very lightweight environment that works well with older hardware.
Lubuntu is even lighter than Xubuntu, suitable for very low-spec computers. Or try [Bodhi]("http://bodhilinux.com/") (based on Ubuntu) for an even lighter distro.

---

### Post by vasa1 on 2012-12-10
> **anon_private said:**
> Can Windows applications be run using a LiveCD?

In Lubuntu 12.04 how can I enable the English (UK) keyboard?
I understand that it maybe convenient for you to have all your questions answered in just one thread and with that in mind, **Questions** seems an appropriate title for this thread.
However, it may benefit others if you ask one question per thread with appropriately informative titles.

---

### Post by 3rdalbum on 2012-12-10
> **Kirk Schnable said:**
> When downloading with a TCP protocol like HTTP, error rate of the connection is irrelevant because TCP performs its own integrity checks on every packet, and asks for it to be retransmitted if it is corrupted. 

As discussed in the Wikipedia article about TCP:
[http://en.wikipedia.org/wiki/Transmission_Control_Protocol#Reliable_transmission]("http://en.wikipedia.org/wiki/Transmission_Control_Protocol#Reliable_transmission")


True, but there is one situation that's not covered. If the wifi card gets disconnected from the router, your download will stop and probably won't be able to be resumed even after reconnection.

The good news is, you can use Bittorrent. It split files up into small segments invisibly for download. If your wifi link gets disrupted, you might only lose the small 64 kilobyte section you were currently downloading, and when you have the connection back Bittorrent will always continue right where it left off.

BTW, love the UDP joke.

---

### Post by anon_private on 2012-12-11
> **oldos2er said:**
> Yes, it's possible using old releases repositories, [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

But the best solution is to upgrade to a supported version of Ubuntu. If you have a lower spec computer you could try Xubuntu or Lubuntu, 12.04.

Hi,

Thanks for responding.

I have had a look at the repository and note that old versions of Ubuntu can be downloaded, but what about the applications that can be added to the older versions.

For example, suppose that someone had Ubuntu version 9.10 and decided that they would like to add abiword to their applications.

How would one go about this.

Best wishes

Happy Christmas

A

---

### Post by anon_private on 2012-12-11
I have Lubuntu on a USB stick.

When I try to boot  it I get get a black screen and writing all down.

This may occur on a few occasions and then it boots up as if nothing was wrong.

In addition, if I run say Ubuntu 9.1 as a liveCD and after working logout. If I then boot Lubuntu from the USB stick it often boots as if nothing is wrong (I boot using the Unetbootin facility).

Any idea why am I am experincing this problem.

I use a Dell PC and have a NVidia Geforce 7300 Turbocache video card.

Could the probelm be due to the fact that the OS is not installed on the hard disk - I doubt it?

Am I right in assuming that if I installed the OS to the hard disk I would experience the same problem?

Thanks

A

---

### Post by Paddy Landau on 2012-12-11
> **anon_private said:**
> I have had a look at the repository and note that old versions of Ubuntu can be downloaded, but what about the applications that can be added to the older versions.
Provided that the version of Ubuntu is still supported, you can download applications from the Ubuntu Software Centre as normal. However, the older the Ubuntu version, the older the application version. If you are installing from scratch, we strongly recommend either the latest LTS (12.04) if you need long-term stability, or the latest version (12.10) if you want the leading-edge.

> **anon_private said:**
> I have Lubuntu on a USB stick…
Please don't mix questions in a single thread. It gets confusing, and the people who are best suited to answering your question will not see it.

Start a new thread, with a properly-descriptive title, for your new problem.

---

### Post by mastablasta on 2012-12-11
> **anon_private said:**
> For example, suppose that someone had Ubuntu version 9.10 and decided that they would like to add abiword to their applications.

 
you can:
 
- point your sources to old releases
- compile abiword from source or use a .deb file if they have one
 
12.04 is supported for 5 years so it means you will get repositories until 2017

---

### Post by Kirk Schnable on 2012-12-13
> **3rdalbum said:**
> True, but there is one situation that's not covered. If the wifi card gets disconnected from the router, your download will stop and probably won't be able to be resumed even after reconnection.
Yeah... but in any likelihood, if this did happen, you'd be stuck with an ISO that's obviously the wrong size.  If you check the size before burning, or better yet, check it against the MD5 hash on the Ubuntu download server, you can be pretty confident your download was a success.

> **3rdalbum said:**
> BTW, love ___ UDP ____.
Me too!

---

