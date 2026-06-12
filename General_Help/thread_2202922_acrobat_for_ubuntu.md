---
title: "acrobat for ubuntu"
date: 2014-01-31
forum: General Help
---

### Post by keith14 on 2014-01-31
Hi,
 I tried three different methods, as described on line, to install adobereader. All failed different reasons or error messages. I'm using ubuntu13.1 64bit. I think the readers were all 32 bit.
 Is there an acrobat that we can use in  ubuntu 64 bit, or isn't that my problem. I'm also wondering if the 32/64 bit difference made ksh fail or not work; a post I close a few days ago opting to just move forward using bash (set -o vi).
thanks,
Keith

---

### Post by bc.haynes on 2014-01-31
32-bit should run in a 64-bit environment, not vice-versa. Can you post the code you used to try to install?

---

### Post by claracc on 2014-02-01
I seems a hard job to install acroreader in ubuntu 13.10 since there is not a ppa repository with it for the 13.10 release.

You can see this thread: [http://ubuntuforums.org/showthread.php?t=2181100&page=2](http://ubuntuforums.org/showthread.php?t=2181100&page=2) , particularly, post 15,  where there are different ways to install acroreader, the successful one, seem to be to download the deb package from adobe and using gdebi (you have to installed it) to install it in order to satisfy a lot of missing dependencies.

Anycase, people doesn't recommend acroreader (because is difficult to install) but okular instead.

---

### Post by monkeybrain20122 on 2014-02-01
> **claracc said:**
> 

Anycase, people doesn't recommend acroreader (because is difficult to install) but okular instead.

And also a security risk since Adobe is no longer maintaining it, that's why it is removed from the repo. Not to mention it is slow and bloated.
@OP, why do you need Acroread?

---

### Post by keith14 on 2014-02-01
Hi,
 well I re-did the attempts to gather logs. TRY1-2 almost same if not not same, 3 uses a different approach. All software updates were made prior to trying to adobe.
BLOG:
Install Adobe Reader on Ubuntu 11.04 Natty Narwhal / Ubuntu 11.10 Oneiric Ocelot / Linux Mint
[http://askubuntu.com/questions/89127/how-do-i-install-adobe-acrobat-reader](http://askubuntu.com/questions/89127/how-do-i-install-adobe-acrobat-reader)
>cmd
<log
>sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) natty partner"
 <   (was second time no log)
>sudo apt-get update
 <   (got 157 lines all seemed ok)
>sudo apt-get install acroread
<Reading package lists... Done
<Building dependency tree
<Reading state information... Done
<Some packages could not be installed. This may mean that you have
<requested an impossible situation or if you are using the unstable
<distribution that some required packages have not yet been created
<or been moved out of Incoming.
<The following information may help to resolve the situation:
<
<The following packages have unmet dependencies:
< acroread : Depends: ia32-libs (>= 20080808) but it is not installable
<            Depends: lib32gcc1 (>= 1:4.1.1) but it is not going to be installed
<            Depends: lib32stdc++6 (>= 4.1.1) but it is not going to be installed
<E: Unable to correct problems, you have held broken packages.
<>


BLOG:
[http://askubuntu.com/questions/89127/how-do-i-install-adobe-acrobat-reader](http://askubuntu.com/questions/89127/how-do-i-install-adobe-acrobat-reader)
>cmd
<log
>sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"
 < (no log)
>sudo apt-get update
 < ( 155 lines nothing interesting)
>sudo apt-get install acroread
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 acroread : Depends: ia32-libs (>= 20080808) but it is not installable
            Depends: lib32gcc1 (>= 1:4.1.1) but it is not going to be installed
            Depends: lib32stdc++6 (>= 4.1.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


BLOG:
[http://askubuntu.com/questions/89127/how-do-i-install-adobe-acrobat-reader](http://askubuntu.com/questions/89127/how-do-i-install-adobe-acrobat-reader)
For Ubuntu 13.10 (32 or 64-bit)
Adobe Reader 9 is not in the 'Partner' repository for 13.10.
>cmd
<log
>download [http://get.adobe.com/reader/otherversions](http://get.adobe.com/reader/otherversions)
  selected-(linux,ENGLISH,9.9.5_deb_file) <download> got->AdbeRdr9.5.5-1_i386linux_enu.deb.crdownload
>sudo dpkg -i --force-architecture AdbeRdr9.5.5-1_i386linux_enu.deb
<(Reading database ... 170289 files and directories currently installed.)
<Preparing to replace adobereader-enu 9.5.5 (using AdbeRdr9.5.5-1_i386linux_enu.deb) ...
<Unpacking replacement adobereader-enu ...
<Setting up adobereader-enu (9.5.5) ...
<Processing triggers for man-db ...
>sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
>sudo apt-get install libxml2:i386 lib32stdc++6
<Reading package lists... Done
<Building dependency tree
<Reading state information... Done
<libxml2:i386 is already the newest version.
<libxml2:i386 set to manually installed.
<Some packages could not be installed. This may mean that you have
<requested an impossible situation or if you are using the unstable
<distribution that some required packages have not yet been created
<or been moved out of Incoming.
<The following information may help to resolve the situation:
<
<The following packages have unmet dependencies:
< lib32stdc++6 : Depends: gcc-4.8-base (= 4.8.1-10ubuntu8) but 4.8.1-10ubuntu9 is to be installed
<                Depends: lib32gcc1 (>= 1:4.1.1) but it is not going to be installed
<E: Unable to correct problems, you have held broken packages.
<>

thanks,
Keith

---

### Post by keith14 on 2014-02-02
Hi,
 well I tried to get kde to check out okular, things were go ok until 98% complete and update aborted. Commands used:
>sudo add-apt-repository ppa:kubuntu-ppa/backports
>sudo apt-get update
>sudo apt-get install kubuntu-desktop
This took hours to fail can I pick-up from failure or just restart?
Thanks,
Keith

---

### Post by keith14 on 2014-02-02
I'm closing this post, believing that acrobat is not happening and will re-open new one for kde install problems.tx,keith

---

### Post by SheamusPatt on 2014-03-12
It's disappointing to see that this is closed and marked "solved", when its status seems to be "won't fix". I've found that acroread is still a no-go on Trusty Tahr beta, even though it's in the default repository (contrary to monkeybrain20122's comments on Feb 1). Llaunching it on x64 results in an unsolved dependency libxml2.so.2.

There are two reasons why I prefer acroread over the default Gnome viewer [FONT=lucida console]evince[/FONT]:

- Copy graphics. Evince doesn't have this feature, but on occasion I do want to copy the graphics part of some area of a document.
- Performance. On a large, detailed document (e.g. a map), Evince is simply not up to snuff. It will spin its wheels for minutes trying to render, whereas acroread can pull up even large documents in seconds. E.g. I have a large map (5.5 Mbyte PDF file), and Evince takes 7 minutes of user time just to load. Acroread (on my Windows system, sorry but I can't test it on Ubuntu any more) brought it up in less than 30 seconds user time, and scrolling around works fairly well.

Fortunately, okular, as suggested, solves these problems. It provides graphics copy, and while its performance is still lagging that of acroread, it's a lot better than Evince.

---

### Post by andrew.46 on 2014-03-12
> **SheamusPatt said:**
> Fortunately, okular, as suggested, solves these problems. It provides graphics copy, and while its performance is still lagging that of acroread, it's a lot better than Evince.

I agree completely, I have been using okular for some time with a wide range of pdfs with absolutely no problems...

---

