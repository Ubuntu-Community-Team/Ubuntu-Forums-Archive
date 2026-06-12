---
title: "Xine - no encrypted DVD playback &amp; libdvdcss"
date: 2005-10-19
forum: General Help
---

### Post by SadaraX on 2005-10-19
Hello. I am having trouble playing encrypted DVDs in xine. I know there is already a thread about this, but my question is very direct. Where can I get a copy of libdvdcss for Kubuntu 5.10? With this, I can play my dvds in xine no problem. I have tons of ubuntu repositories added to my /etc/apt/sources.list but none of them have anything like libdvdcss and its not in the hoary backports. Also, the Breezy backports have never worked for me (always get an apt error).

A link to the deb file or a working repository for 5.10 would be great. I know I could probably find this file in some debian repo, but I am trying to keep myself clean and pure ubuntu.

---

### Post by j_baer on 2005-10-19
To get the libdvdcss file I went to deb ...

See ... 

[http://debian.video.free.fr/](http://debian.video.free.fr/) 

for your choices .. 

Cheers

---

### Post by aclaunch on 2005-10-20
You can also use "sudo /usr/share/doc/libdvdread3/examples/install-css.sh" which is a script that fetches libdvdcss2 and installs it. It is in the above named directory.

Good Luck
Alan

---

### Post by SadaraX on 2005-10-21
Just for the thread information sake, I will post what I ended up doing. I found an ubuntu repository (unoffical) that had the package I wanted. It also had a version ubuntu of w32codecs. Here's the address

# Ubuntu Extra Packages - Unofficial
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main

---

### Post by ryan76 on 2005-10-21
[QUOTE=aclaunch]You can also use "sudo /usr/share/doc/libdvdread3/examples/install-css.sh" which is a script that fetches libdvdcss2 and installs it. It is in the above named directory.

Good Luck
Alan[/QUOTE]

I tried this and it said no:

root@ubuntu:/usr/share/doc/libdvdread3/examples # install-css.sh
bash: install-css.sh: command not found

command not found? I'm looking at the file! What's going on here?

---

### Post by Kirky_D on 2005-10-21
[QUOTE=ryan76]I tried this and it said no:

root@ubuntu:/usr/share/doc/libdvdread3/examples # install-css.sh
bash: install-css.sh: command not found

command not found? I'm looking at the file! What's going on here?[/QUOTE]

try

 sh /usr/share/doc/libdvdread3/examples/install-css.sh

or even using sudo rather than being root.

just a few thoughts

---

### Post by thumper on 2005-10-21
> command not found? I'm looking at the file! What's going on here?
The current directory is probably not in the path.

try ./install-css.sh

---

### Post by b0rsten on 2006-01-10
this worked fine for me (using dapper 6.04)
thanks

---

### Post by TZRick on 2006-10-28
> **aclaunch said:**
> You can also use "sudo /usr/share/doc/libdvdread3/examples/install-css.sh" which is a script that fetches libdvdcss2 and installs it. It is in the above named directory.

Good Luck
Alan

Thanks Alan! It seems like the freecontrib repositories are down (or something's wrong with my configs), but I couldn't get those to work. This script is so simple and worked!

---

### Post by rbiswas on 2006-10-29
If you are in edgy it seems that you should use

sudo /usr/share/doc/libdvdread3/install-css.sh So you should go up a directory, while in dapper it would have been in examples directory.However, you seem to have reached the examples directory, which I don't have in edgy.

---

### Post by heyheyhey on 2006-11-05
hi, I'm an absolute first timer with ubuntu and not very good with linux. Having said that I would rather fight through linux than bang my head against the windoze wall.](*,)  I don't seem to be able to get dvd play back even though i have the synaptic libdvdcss.deb installed. I've gotten the svn from videolan.org but hae hit a wall in terms of to do with it. I'm running ubuntu 6.06lts on a 64 bit intel. Any help or direction would be most appreciated.

---

### Post by SadaraX on 2006-11-05
> **heyheyhey said:**
> hi, I'm an absolute first timer with ubuntu and not very good with linux. Having said that I would rather fight through linux than bang my head against the windoze wall.](*,)  I don't seem to be able to get dvd play back even though i have the synaptic libdvdcss.deb installed. I've gotten the svn from videolan.org but hae hit a wall in terms of to do with it. I'm running ubuntu 6.06lts on a 64 bit intel. Any help or direction would be most appreciated.

Hello and welcome to freedom. :) Well, I am not running 64 bit, but maybe I can offer some help. I have got dvd playback working without compiling anything from SVN. 

About your libdvdcss, can you tell me what the exact package name is? Also, what version it is? 

I installed libdvdcss2 from the Penguin-Liberation-Front. 

URL: [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/)
Distribution: dapper

I also installed libdvdread3 and libdvdnav4. 

How are you playing the DVDs? Do you open Xine and click the "DVD" button to start playback?

---

### Post by heyheyhey on 2006-11-06
You rule, Thrity seconds of lokking at PLF has gained me another victory. Thanks heaps for your help. I often have trouble finding 64 bit debs so just being pointed to them is heaps of help. Once again thanks.

Cheers heyheyhey

---

### Post by binmugahid on 2006-11-28
I tried this on Edgy and it worked like clockwork...

sudo /usr/share/doc/libdvdread3/install-css.sh

Thanks for all the tipsters, we lears as we go along in Ubuntu and it sooo damn exciting.

Now, I know that  Windows and Mac are boring... OK, maybe not so much Mac, but Windows... sheeeesh.

Thanks fellas

---

### Post by linuxguiri on 2006-12-17
i have libdvdcss2 1.2.5-1 and libdvdread3 0.9.6-3 installed but totem-xine gives this error:

```
The source seems encrypted, and can't be read. 
Are you trying to play an encrypted DVD without libdvdcss?
```

what else can i try?

---

### Post by Azakus on 2006-12-17
Try upgrading libdvdcss, the current version is 1.2.9.

---

### Post by linuxguiri on 2006-12-17
> **Azakus said:**
> Try upgrading libdvdcss, the current version is 1.2.9.

Thanks for the idea, but where do I get the upgrade? Synaptic says 1.2.5 is the latest version.

(BTW I used  sudo /usr/share/doc/libdvdread3/install-css.sh to get libdvdcss installed.)

---

### Post by raghuprasad on 2006-12-23
I added following lines in /etc/apt/sources.list (I am using dapper):

deb [http://seveas.imbrandon.com](http://seveas.imbrandon.com) dapper-seveas all
deb-src [http://seveas.imbrandon.com](http://seveas.imbrandon.com) dapper-seveas all

Then executed following command (wget must be installed already):

wget [http://mirror.ubuntulinux.nl/1135D466.gpg](http://mirror.ubuntulinux.nl/1135D466.gpg) -O- | sudo apt-key add -

Then run the following:

sudo apt-get update
sudo apt-get install libdvdcss2

---

### Post by FrozenFOXX on 2007-03-13
Nice links but despite a message on his page about supporting amd64 it appears to do no such thing.  No dice.

---

### Post by Kadin2048 on 2007-05-24
> **binmugahid said:**
> I tried this on Edgy and it worked like clockwork...

sudo /usr/share/doc/libdvdread3/install-css.sh

Thanks for all the tipsters, we lears as we go along in Ubuntu and it sooo damn exciting.

Now, I know that  Windows and Mac are boring... OK, maybe not so much Mac, but Windows... sheeeesh.

Thanks fellas

Just a FYI ... this install.sh script is deprecated and has been removed from newer versions of libdvdread3 (I don't know why ... I think it's stupid, but since it's in some sort of unofficial repo they decided to delete the install script).

See:
[http://packages.debian.org/changelogs/pool/main/libd/libdvdread/libdvdread_0.9.7-3/changelog](http://packages.debian.org/changelogs/pool/main/libd/libdvdread/libdvdread_0.9.7-3/changelog)

Anyway ... not sure which Ubuntu versions have which version in them, but you just should be careful recommending that solution to people, because eventually it's going to stop working. The "right" way according to the Debian people is to add a mirror that includes it.

---

### Post by Benbow on 2007-05-27
I used the following from a previous reply and i am running Feisty:

 sudo /usr/share/doc/libdvdread3/install-css.sh

And received the following:

--08:51:51--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)
           => `/tmp/dvdcss-iR8363/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 (25K) [text/plain]

100%[====================================>] 25,178        89.73K/s             

08:51:51 (89.45 KB/s) - `/tmp/dvdcss-iR8363/libdvdcss.deb' saved [25178/25178]

Selecting previously deselected package libdvdcss2.
(Reading database ... 279241 files and directories currently installed.)
Unpacking libdvdcss2 (from .../dvdcss-iR8363/libdvdcss.deb) ...
Setting up libdvdcss2 (1.2.5-1) ...

Dvds now run ok but sound volume is below par.

---

