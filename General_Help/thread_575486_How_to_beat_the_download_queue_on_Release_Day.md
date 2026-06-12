---
title: "How to beat the download queue on Release Day"
date: 2007-10-14
forum: General Help
---

### Post by kuby on 2007-10-14
**Contents**
 Summary
 How it started
 How to (Help yourself)
 Help others
	
**Summary**
I have downloaded Kubuntu 7.04 DVD in minutes using a 1 day old daily build, updated using jigdo. I intend to do the same on the release of Kubuntu 7.10. Below I describe what I did to accomplish that. Furthermore I suggest users to seed their iso's using torrent even if not downloaded it that way. Due to the nature of jigdo, this system works with iso's having a lot of files in them. This means it works for alternate CD's and Install/Live DVD, but not for Install/Live CDs (the latter one is mostly one 600+ MB file (a complete compressed linuxkernel with apps) plus few additional files). I'll post the exact links once I have found them on Day -1 and Release Day.
	
**How it started**
When Kubuntu 7.04 was released I (like many others) wanted to have  it as soon as possible. I realized  quickly it would take forever to have the download completed with a downloadrate of about 6 kbps.
 In parallel to http downloading the iso  I started a torrent download. But  to get that going you need several seeders and they were rare at first because so few have a complete iso to seed.
 Jigdo was the solution. I learned about it at the Debian download page. Using an earlier downloaded beta and two jigdo files I was able to create Kub 7.04 in a matter of minutes. Ironically I discovered the 'daily build' downloaded at top speed on Day -1 from [http://cdimage.ubuntu.com/kubuntu/dvd/current/](http://cdimage.ubuntu.com/kubuntu/dvd/current/) to be equal to the released one.
 
**How to (Help yourself)**
1.  Download a beta before release-day
		As no-one seems to download your own bandwidth is the limiting factor
2.  Update your iso on release-day
An iso can be considered just a (large) collection of files organized in a certain way. a distro iso is mostly packages. As the release approaches the number of packages changing compared to the previous beta will go down (less and less bugs requiring a fix). Would it he nice to just update the changed files and regenerate the iso?
Well, this is the basic principle behind jigdo.

Prerequisites:
 * Jigdo installed
 * a .jigdo file
 * a .template file 
 * an "old" iso (this is step 1)
 
  The rest is fairly easy. just follow the steps in the How-to on the jigdo homepage ([http://atterer.net/jigdo/debian-jigdo-mini-howto/index.html](http://atterer.net/jigdo/debian-jigdo-mini-howto/index.html)). It is aimed at debian, but it works for all jigdo, just adjust the place jigdo searches for files. For Kubuntu (and for all derivatives) I use [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) but I suggest to use your local archive (substitute nl. with your country abbreviation).

  Note: make sure you have mounted your iso (in M$ using e.g. DAEMON Tools, in Linux mount your iso with 
  ```
sudo mount -o loop -t iso9660 gutsy-dvd-i386.iso /mnt/oldiso
``` 
(assuming you've created directory /mnt/oldiso earlier & replace your iso-file name as required)
  
**Help others**
To help those not able to follow above steps downloading using torrent is a good alternative. But as I indicated above this doesn't work if no or few are seeding. You can help if you have obtained your copy using above steps (or any other method) by downloading a torrent and pointing your torrent client to the location of your complete iso. No or a single step is required. E.g. utorrent autochecks the file discovered and finds a complete iso and starts seeding. For ktorrent select the option 'Check Data Integrity'.

---

### Post by stinger30au on 2007-10-14
or you can upload the iso to a public torrent site so everyone can get to it

---

### Post by strabes on 2007-10-14
This is way too complicated. If everyone would simply seed the torrent then the servers wouldn't die.

The easiest way is to simply upgrade right now. Then you don't have to worry about downloading the iso on release day.

---

### Post by FredB on 2007-10-14
A very simple way : grab rc and install it. There were not a lot of changes since rc was released.

And using public torrents could help a lot !

---

### Post by kuby on 2007-10-18
No overwhelming enthousiasm for my suggestion, no problem. I have just completed the update of my Kubuntu 7.10 RC DVD using my own steps. Primary reason for this post is my promise to post the exact links for those interested.

I describe the situation for Kubuntu, but they apply also to Ubuntu, adjust locations as required. As you can see the md5sum for the release of Kubuntu 7.10 is equal to the daily. 

From [http://cdimage.ubuntu.com/kubuntu/dvd/current/MD5SUMS](http://cdimage.ubuntu.com/kubuntu/dvd/current/MD5SUMS)  (the daily)
acf811303f380d07106d8fd8b923839d *gutsy-dvd-i386.iso

From [http://cdimage.ubuntu.com/kubuntu/releases/7.10/release/MD5SUMS](http://cdimage.ubuntu.com/kubuntu/releases/7.10/release/MD5SUMS) (the release)
acf811303f380d07106d8fd8b923839d *kubuntu-7.10-dvd-i386.iso

As I mentioned in my original post, only the daily contains the jigdo+template. So you can download those two from [http://cdimage.ubuntu.com/kubuntu/dvd/current/](http://cdimage.ubuntu.com/kubuntu/dvd/current/) and update any old iso you have to 7.10. On completion simply adjust the name of the file.

The replies to my original post suggested just to install Release Candidate and upgrade from within. Good suggestion. However, I do prefer in general to conduct a clean install, furthermore I like to have at one time a complete up-to-date DVD for re-installs, but that can be done days or weeks later.

The other suggestion made is just seed to a public torrent. Apparently I didn't express myself too well, because that was exactly my suggestion. Problem in the beginning is too few seeders and too many leechers. Only after some time the number of seeders increase and can thus serve the leechers. My suggestion was to all who obtained a full iso via any means, to start seeding anyhow with the intention to boost the number of seeders.
Just to check my assumption I started torrent-download from scratch and got a disappointing 20kb (down) at most.
(BTW I am following my own recommendation and am seeding).

---

### Post by Whiffle on 2007-10-18
It took me less than an hour to download all 3 versions (i386 desktop, alternate and server) with bittorrent this morning.  Right now they're seeding...BT is definitly the way to go.

---

### Post by bodhi.zazen on 2007-10-18
Please use the torrents, it decreases the load on the Ubuntu servers and helps everyone. If you can seed, thank you ...

---

