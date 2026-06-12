---
title: "Wubi *buntu ISO download using BitTorrent"
date: 2007-07-13
forum: General Help
---

### Post by geekoid on 2007-07-13
How simple would it be to implement a bittorrent download within Wubi for the ISO download?  It seems the ISO downloads very slowly with the current method.  When I downloaded with uTorrent earlier, I got the ISO in minutes.

:-\"

geekoid

---

### Post by ago on 2007-07-13
We are waiting for aria2 to be stable under windows: [http://aria2.sourceforge.net/](http://aria2.sourceforge.net/)

Now the mirror is selected randomly, so your luck may vary.

---

### Post by wifiguy on 2007-07-27
"A few clicks" and a few hours because there's no torrent tracker yet. I'm downloading xbuntu -7.04 now and will have to wait 4 hours for a 686MB file while the metalink does its thing at 51kbs. Who knows how long it'll take me to get all of xbuntu? Days? Dial-up speed download on a 1Mbps ADSL line.

I was able to get Knoppix with Azureus in a lot less time, but the ISO CD I burned ran with weird idiosyncrasies so I decided to try wubi.

Not giving up on Linux yet,
wifiguy

---

### Post by wifiguy on 2007-07-27
Never mind.

After more than 4 hours of watching the metalink fiddle and diddle, I listened to my disk grind while the checksums were verified. After the "successful" installation, I attempted to reboot and was treated to a hang/freeze while xubuntu tried but failed to boot. It sat at 0% for 7 minutes in the DOS-like screen that says something like "detecting hardware" and said something at the top about detecting network hardware. I had to force a powerdown and run chkdsk from the recovery console to clean up the disk errors that result from not shutting down cleanly.

After trying to boot xubuntu again, I got a message saying that the install hadn't completed and that I should run install again. Booting into the Redmond ripoff (Windows), I double-clicked on Wubi-7.04.04.exe and got a message window about verifying the install. Then I got total silence--there's no process running that's named anything like wubi or ubuntu or xubuntu. Now, double-clicking on Wubi-7.04.04.exe does NOTHING.

This is my second extremely distasteful experience with Linux. You know, I bought a new, bigger hard drive for my old notebook PC and a new version of the Redmond ripoff on a CD 2 1/2 years ago. You know what? I put the CD into the CD-ROM drive and booted off of it. Several minutes later I had a formatted hard drive with the Redmond ripoff installed and running on my new hard drive--no problems. I didn't have to get support or consult a forum.

 I don't think I'm going to live long enough to ever see Linux made installable by mere mortals. Now I know why you have to get a company like Dell or a place like Walmart to sell PCs with Linux already installed.

I don't like Microsoft and I don't like Windows, but I've finally found an OS that's worse: Linux. I run Windows because every peripheral I buy has drivers that work with Windows; no fiddling, no diddling. When you can open up the box containing a new peripheral and find a CD inside with Linux drivers on it, give me a shout.

---

### Post by antini on 2007-07-28
> **wifiguy said:**
> "A few clicks" and a few hours because there's no torrent tracker yet. I'm downloading xbuntu -7.04 now and will have to wait 4 hours for a 686MB file while the metalink does its thing at 51kbs. Who knows how long it'll take me to get all of xbuntu? Days? Dial-up speed download on a 1Mbps ADSL line.


You sound more like a candidate for the ubuntu live CD.

To get the full speed out of the metalink, you'd need to use a metalink client that supports multi-source downloading, which is unfortunately almost every other one besides Metadl/Wubi...an easy choice is DownThemAll! Firefox extension, if you already use fx.

BUT Wubi may be using aria2 soon, which would be great. The Windows port is considered pretty stable at this point, and a new version (updated 26-Jul-07) is up at [http://smithii.com/aria2](http://smithii.com/aria2)

---

### Post by logos34 on 2007-07-28
You shouldn't have to do this but you can just download the ubuntu iso from the main site and then copy it over to /wubi/install.  That's what I did recently when I was playing around with it and didn't want to wait for the download.

---

