---
title: "Apt-get download speed VERY slow"
date: 2007-01-08
forum: General Help
---

### Post by HarrisonHopkins on 2007-01-08
I have a laptop running Edgy Eft. Whenever I use apt-get to install something, the download is in the bytes speed, not the kilobyte speed. For most of the download, it will say two hours, then at the very end, it decides to speed up. This is for every package. Is there anyway that I can fix this?

---

### Post by llamakc on 2007-01-08
Show us your /etc/apt/sources.list file.

---

### Post by HarrisonHopkins on 2007-01-08
> 
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


That is it. I have tried resetting my router and my modem, but it didn't help.

---

### Post by ciscosurfer on 2007-01-08
> **HarrisonHopkins said:**
> That is it. I have tried resetting my router and my modem, but it didn't help.First, comment out the first line that reads:  			 				

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted and make it look like:  			 				

#deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted  (with a pound sign in front of the line).

Second, the repos you are trying to hit, may be running hard (lots of users or is currently running slow -- although, I just hit those repos just fine), or they may be down altogether.

So, to recap: add the # in on the first line, save the file, and then try to update and upgrade again....or update and try intsalling a new .deb

Good Luck

PS Unless you have you Edgy CD or DVD in your drive, there is no need to have the first line there (unless you are on a slow connection, etc.).   The bottom line is that apt is trying to pull files from the disc instead of the web.

---

### Post by HarrisonHopkins on 2007-01-08
Ok, I will do that in 2 hours, when my 2883kb file finishes downloading...

---

### Post by mdurham on 2007-01-08
try removing the "us." in the url's and see what happens. What country are you in?

---

### Post by llamakc on 2007-01-08
FWIW I am IN the US and the us.archive* seem to be slow. I installed to another machine yesterday and had a similiar problem. Edit out the "us." from your sources.list lines and try again.

HINT: You can interrupt a partial download in APT, edit the sources, restart the update/upgrade/dist-upgrade and it will pick up where you left off. No reason to wait on slow repositories.

---

### Post by HarrisonHopkins on 2007-01-08
I just removed the US, restarted the script, and all the remaining downloads were at 500kb/s. Thanks for all the help!

---

### Post by Ubuntoofun4you on 2007-01-08
:KS  When you install edgy--- "us." is automatically loaded into your repo source file

This serves two purposes (1) to help get you the fastest downloads for your geopraphical location
 (2) to prevent copyright infringement;

If you are pinging the us. servers for package files that will install such programs as "Automatix"
( which is illegal to run in the States)

  Then you will get a connection anywhere from 2000b to 9000b/sec

It is a mandatory slowdown that Ubuntu enforces to cover their butt from lawsuits from the GIANT monopoly we known as XXXXsoft.

Now you know why us. repos go slow... you may have codecs running on your BOX that aren't 100% legal
THIS WILL CHANGE OVER TIME

---

### Post by ciscosurfer on 2007-01-08
> **Ubuntoofun4you said:**
> :KS  When you install edgy--- "us." is automatically loaded into your repo source file

This serves two purposes (1) to help get you the fastest downloads for your geopraphical location
 (2) to prevent copyright infringement;The "us." is a subdomain for the United States.  Period.  If you want faster speeds that correspond to your geography, then you can modify "us." with, for example, "fr." if you live in France.  Or, you can pick an entirely separate mirror altogether: [https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive)

Mirrors go up and down all the time.  Switching between multiple mirrors is generally a good idea if you want to get fast download speeds via apt (sometimes it takes a day or two for all updates to trickle-down to all mirrors from Ubuntu's main repos., so keep this in mind when updating).> If you are pinging the us. servers for package files that will install such programs as "Automatix"
( which is illegal to run in the States) Then you will get a connection anywhere from 2000b to 9000b/sec  It is a mandatory slowdown that Ubuntu enforces to cover their butt from lawsuits from the GIANT monopoly we known as XXXXsoft.This is incorrect on so many fronts:[LIST=1]
[*]You install Automatix from [www.getautomatix.com]("http://www.getautomatix.com") NOT from Ubuntu's repos.
[*]And just because you have the getautomatix repo line in your sources.list, has nothing to do with the speeds that you will get from Ubuntu's repo servers.
[*]And Automatix, as a whole, is NOT illegal to run in the US (check out the screenshot I provide below for what SHOULD NOT LEGALLY be installed if you live in the US).
[*]Mandatory slowdown?  You logic is simply flawed from your previous statement.[/LIST]> Now you know why us. repos go slow... you may have codecs running on your BOX that aren't 100% legal
THIS WILL CHANGE OVER TIMEI give up [-(

---

### Post by nix4me on 2007-01-08
Happened to me too.  I changed to the non us repository a few days ago and all has been well.

nix4me

---

### Post by medix on 2007-01-08
Hello all,
   Had it happen to me as well. The funny thing is, I have Edgy running on my office machine which is a mere *mile* from my apartment (granted, it's on a university pipe so the routing is probably a bit different) and I've had no problems with that machine, only my desktop at home. 

Removing all of the us prefixes worked just fine. 

(and yes, I believe MS is most likely at the root of this.. it's quite plauseable considering the control the currently exert on the software market)

Don't let the man get you down!

- Medix 8)

---

### Post by firezip on 2007-01-09
Thank you very much, I was wondering why my download speed was 200 b/s.

---

### Post by twshadow101 on 2007-01-09
> **HarrisonHopkins said:**
> I have a laptop running Edgy Eft. Whenever I use apt-get to install something, the download is in the bytes speed, not the kilobyte speed. For most of the download, it will say two hours, then at the very end, it decides to speed up. This is for every package. Is there anyway that I can fix this?

I am using Xubuntu Edgy Eft 6.10 and have been having the same issue.

---

### Post by wpshooter on 2007-01-09
> **llamakc said:**
> FWIW I am IN the US and the us.archive* seem to be slow. I installed to another machine yesterday and had a similiar problem. Edit out the "us." from your sources.list lines and try again.

HINT: You can interrupt a partial download in APT, edit the sources, restart the update/upgrade/dist-upgrade and it will pick up where you left off. No reason to wait on slow repositories.

I don't exactly understand this advice of removing the US from the sources list.

If this was put in there by the installation of the O/S, then I would think it is there for a reason.  Would not a better alternative be to find out what the problems is that is causing these severs to deliver information so slowly, so you could leave your system as it was configured originally ???

Thanks.

---

### Post by ciscosurfer on 2007-01-09
> **wpshooter said:**
> I don't exactly understand this advice of removing the US from the sources list.

If this was put in there by the installation of the O/S, then I would think it is there for a reason.  Would not a better alternative be to find out what the problems is that is causing these severs to deliver information so slowly, so you could leave your system as it was configured originally ???

Thanks.Read my posts earlier in this thread.  If you're still confused, post back and I'll re-explain. :D

---

### Post by amoore on 2007-01-10
> **Ubuntoofun4you said:**
> :KS  When you install edgy--- "us." is automatically loaded into your repo source file

If you are pinging the us. servers for package files that will install such programs as "Automatix"
( which is illegal to run in the States)

  Then you will get a connection anywhere from 2000b to 9000b/sec

It is a mandatory slowdown that Ubuntu enforces to cover their butt from lawsuits from the GIANT monopoly we known as XXXXsoft.

Now you know why us. repos go slow... you may have codecs running on your BOX that aren't 100% legal
THIS WILL CHANGE OVER TIME

[SIZE="6"]**Ubuntoofun4you Please STOP inciting FUD **[/SIZE]](*,)

---

### Post by orionMX on 2007-01-11
Had same problem...

Removed "us" and voila, normal d/l speeds again
Thanks

---

### Post by Kingsley on 2007-01-11
i did the opposite of what was suggested and my download speed is now back to normal.

---

### Post by ciscosurfer on 2007-01-11
> **Kingsley said:**
> i did the opposite of what was suggested and my download speed is now back to normal.And by "the opposite", you mean what?

---

### Post by drFUNK on 2007-01-11
I live in Virginia, USA and removing the 'us' gave me acceptable download speeds as well.

---

### Post by rj686 on 2007-01-12
Same here, Wisconsin USA and removing US made my downloads go WAY up.

---

### Post by wpshooter on 2007-01-12
> **HarrisonHopkins said:**
> I just removed the US, restarted the script, and all the remaining downloads were at 500kb/s. Thanks for all the help!

Is it necessary to edit this thru the terminal ?  I edited out the US in the Software Properties GUI and it did not make any difference.  When I started the update manager the downloads still came from the US URL and was same old slow as molasses speed.

Thanks.

---

### Post by keshek on 2007-01-12
> **wpshooter said:**
> Is it necessary to edit this thru the terminal ?  I edited out the US in the Software Properties GUI and it did not make any difference.  When I started the update manager the downloads still came from the US URL and was same old slow as molasses speed.

Thanks.

Yes it is necessary to use the terminal since admin privaleges are necessary to save changes, although you can still use a graphical text editor. To edit the file you can use the commannd:
```
sudo gedit /etc/apt/sources.list
```

---

### Post by Kingsley on 2007-01-16
> **ciscosurfer said:**
> And by "the opposite", you mean what?

i added "us" to the source files.

---

### Post by prsamy on 2008-01-04
I reinstalled Ubuntu 7.10 and the updates have taken so far 12 hrs and there is still about 20% left.

---

