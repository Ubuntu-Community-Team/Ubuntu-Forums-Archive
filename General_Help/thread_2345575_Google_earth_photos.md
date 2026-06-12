---
title: "Google earth photos"
date: 2016-12-05
forum: General Help
---

### Post by robelli on 2016-12-05
I am running Ubuntu 16.04 Mate (New install) and just installed Google-earth. All is going well except the photos do not show. Just a blank white page although it does try to open as two hour glasses appear very briefly and disappear . All the libraries are the newest installed . The Google Earth version is 7.1.7.2606

---

### Post by #&amp;thj^% on 2016-12-05
How did you install it? Provide a link if that is how you installed it.
Thanks

---

### Post by robelli on 2016-12-05
I installed it by Gdebi from the following   [https://www.google.com/earth/download/ge/agree.html1.8k]("https://www.google.com/earth/download/ge/agree.html")[ ]("https://www.google.com/earth/download/ge/agree.html")[URL="https://www.google.com/earth/download/ge/agree.html"]


[/URL]

---

### Post by #&amp;thj^% on 2016-12-05
> **robelli said:**
> I installed it by Gdebi from the following   [https://www.google.com/earth/download/ge/agree.html1.8k]("https://www.google.com/earth/download/ge/agree.html")[URL="https://www.google.com/earth/download/ge/agree.html"]


[/URL]

I thought so;)  lsb-core is needed for Google Earth and lsb-core became obsolete in Ubuntu 16.04 LTS. So here is how you install lsb-core in Xenial Link Below
[http://www.debugpoint.com/2016/06/how-to-install-google-earth-in-ubuntu-16-04-lts-xenial-xerus/](http://www.debugpoint.com/2016/06/how-to-install-google-earth-in-ubuntu-16-04-lts-xenial-xerus/)
Let us know how this goes for you.

---

### Post by robelli on 2016-12-05
When I tried to install those before I was told that they were all the latest versions that I have . Do you think I should delete them and install from your recommendation

I tried to find those  but they weren't in my system so I did as you said and they all were downloaded but when I ran the last command here is what I got

```
mal@HP-Compaq-dc7900:~$ sudo apt install lsb-*.deb
[sudo] password for mal: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lsb-core_4.1+Debian13+nmu1_amd64.deb
E: Couldn't find any package by glob 'lsb-core_4.1+Debian13+nmu1_amd64.deb'
E: Couldn't find any package by regex 'lsb-core_4.1+Debian13+nmu1_amd64.deb'
E: Unable to locate package lsb-invalid-mta_4.1+Debian13+nmu1_all.deb
E: Couldn't find any package by glob 'lsb-invalid-mta_4.1+Debian13+nmu1_all.deb'
E: Couldn't find any package by regex 'lsb-invalid-mta_4.1+Debian13+nmu1_all.deb'
E: Unable to locate package lsb-security_4.1+Debian13+nmu1_amd64.deb
E: Couldn't find any package by glob 'lsb-security_4.1+Debian13+nmu1_amd64.deb'
E: Couldn't find any package by regex 'lsb-security_4.1+Debian13+nmu1_amd64.deb'
```

```
mal@HP-Compaq-dc7900:~$ wget [http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-security_4.1+Debian13+nmu1_amd64.deb](http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-security_4.1+Debian13+nmu1_amd64.deb)
--2016-12-06 14:30:58--  [http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-security_4.1+Debian13+nmu1_amd64.deb](http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-security_4.1+Debian13+nmu1_amd64.deb)
Resolving ftp.us.debian.org (ftp.us.debian.org)... 128.61.240.89, 64.50.236.52, 128.30.2.26, ...
Connecting to ftp.us.debian.org (ftp.us.debian.org)|128.61.240.89|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19968 (20K) [application/octet-stream]
Saving to: ‘lsb-security_4.1+Debian13+nmu1_amd64.deb’

lsb-security_4.1+De 100%[===================>]  19.50K  76.1KB/s    in 0.3s    

2016-12-06 14:30:59 (76.1 KB/s) - ‘lsb-security_4.1+Debian13+nmu1_amd64.deb’ saved [19968/19968]
```

```
mal@HP-Compaq-dc7900:~$ wget [http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-core_4.1+Debian13+nmu1_amd64.deb](http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-core_4.1+Debian13+nmu1_amd64.deb)
--2016-12-06 14:31:22--  [http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-core_4.1+Debian13+nmu1_amd64.deb](http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-core_4.1+Debian13+nmu1_amd64.deb)
Resolving ftp.us.debian.org (ftp.us.debian.org)... 208.80.154.15, 128.61.240.89, 64.50.233.100, ...
Connecting to ftp.us.debian.org (ftp.us.debian.org)|208.80.154.15|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44708 (44K) [application/octet-stream]
Saving to: ‘lsb-core_4.1+Debian13+nmu1_amd64.deb’

lsb-core_4.1+Debian 100%[===================>]  43.66K  86.3KB/s    in 0.5s    

2016-12-06 14:31:23 (86.3 KB/s) - ‘lsb-core_4.1+Debian13+nmu1_amd64.deb’ saved [44708/44708]
```

```
mal@HP-Compaq-dc7900:~$ wget [http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-invalid-mta_4.1+Debian13+nmu1_all.deb](http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-invalid-mta_4.1+Debian13+nmu1_all.deb)
--2016-12-06 14:31:45--  [http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-invalid-mta_4.1+Debian13+nmu1_all.deb](http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-invalid-mta_4.1+Debian13+nmu1_all.deb)
Resolving ftp.us.debian.org (ftp.us.debian.org)... 128.30.2.26, 64.50.233.100, 128.61.240.89, ...
Connecting to ftp.us.debian.org (ftp.us.debian.org)|128.30.2.26|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 20330 (20K) [application/x-debian-package]
Saving to: ‘lsb-invalid-mta_4.1+Debian13+nmu1_all.deb’

lsb-invalid-mta_4.1 100%[===================>]  19.85K  77.0KB/s    in 0.3s    

2016-12-06 14:31:46 (77.0 KB/s) - ‘lsb-invalid-mta_4.1+Debian13+nmu1_all.deb’ saved [20330/20330]
```

This is what I got when I ran the first lot so I guess that they had downloaded alright

---

### Post by #&amp;thj^% on 2016-12-05
Ok no worries. Now run the below:
```
sudo apt -f install
```
Post back any errors

---

### Post by robelli on 2016-12-05
Ran that . No errors but GE still the same . Photos blank although the "hour glass" shows up very briefly and am left with a blank

---

### Post by #&amp;thj^% on 2016-12-05
What dose this show from the terminal:
```
apt policy lsb-core
```

---

### Post by robelli on 2016-12-05
mal@HP-Compaq-dc7900:~$ apt policy lsb-core
lsb-core:
  Installed: 9.20160110ubuntu0.2
  Candidate: 9.20160110ubuntu0.2
  Version table:
 *** 9.20160110ubuntu0.2 500
        500 [http://fj.archive.ubuntu.com/ubuntu](http://fj.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
mal@HP-Compaq-dc7900:~$

---

### Post by #&amp;thj^% on 2016-12-05
Well You might need these installed also.
```
sudo apt install libfreeimage3 libgstreamer0.10-0 libgstreamer-plugins-base0.10-0
```

---

### Post by robelli on 2016-12-05
```
mal@HP-Compaq-dc7900:~$ apt policy lsb-core
lsb-core:
  Installed: 9.20160110ubuntu0.2
  Candidate: 9.20160110ubuntu0.2
  Version table:
 *** 9.20160110ubuntu0.2 500
        500 [http://fj.archive.ubuntu.com/ubuntu](http://fj.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
mal@HP-Compaq-dc7900:~$
```

Sorry got the wrong on that time here is the result of your last . Seems like I have them all 

```
mal@HP-Compaq-dc7900:~$ sudo apt install libfreeimage3 libgstreamer0.10-0 libgstreamer-plugins-base0.10-0
[sudo] password for mal: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libfreeimage3 is already the newest version (3.17.0+ds1-2).
libgstreamer-plugins-base0.10-0 is already the newest version (0.10.36-2).
libgstreamer0.10-0 is already the newest version (0.10.36-1.5ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
mal@HP-Compaq-dc7900:~$
```

---

### Post by #&amp;thj^% on 2016-12-05
Hummm? :confused: 
Well we will have to get a little rough with it then. And get the right qt-libs.
Run the Below one line at a time.
```
cd /opt/google/earth/free
sudo wget http://www.sundru.net/wordpress/sundrumisc/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz
sudo tar xvf ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz
```
And if this dose not work try rebooting to be sure everything gets loaded at start-up

---

### Post by robelli on 2016-12-05
Ran all those and there were no errors . GE still will not open the photos . I rebooted also and still the same . No photos

---

### Post by #&amp;thj^% on 2016-12-05
Can you see the lsb .deb files that we d-loaded in your home directory?
Debian13+nmu1_amd64.deb
Debian13+nmu1_amd64.deb
Debian13+nmu1_all.deb

---

### Post by robelli on 2016-12-05
These are the files I found in the Home folder

lsb-security_4.1+Debian13+nmu1_amd64.deb

lsb-core_4.1+Debian13+nmu_amd64.deb

---

### Post by #&amp;thj^% on 2016-12-05
Ok there is the problem....Do this for me.
Open terminal:
```
mkdir lsb
cd lsb
wget http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-security_4.1+Debian13+nmu1_amd64.deb
wget http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-core_4.1+Debian13+nmu1_amd64.deb
wget http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-invalid-mta_4.1+Debian13+nmu1_all.deb

```
This will create a file in your home directory with all three .deb files there.
Now be sure all 3 .deb files are there...and if they are all there in the same terminal run this:
```
sudo dpkg -i *.deb
```
Followed by:
```
sudo apt -f install
```

---

### Post by robelli on 2016-12-05
This is what I got when I ran all of the above and I found the three files in lsb dir     

```
mal@HP-Compaq-dc7900:~$ mkdir lsb
mal@HP-Compaq-dc7900:~$ cd lsb
mal@HP-Compaq-dc7900:~/lsb$ wget [http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-security_4.1+Debian13+nmu1_amd64.deb](http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-security_4.1+Debian13+nmu1_amd64.deb)
--2016-12-06 16:50:12--  [http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-security_4.1+Debian13+nmu1_amd64.deb](http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-security_4.1+Debian13+nmu1_amd64.deb)
Resolving ftp.us.debian.org (ftp.us.debian.org)... 208.80.154.15, 128.61.240.89, 64.50.236.52, ...
Connecting to ftp.us.debian.org (ftp.us.debian.org)|208.80.154.15|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19968 (20K) [application/octet-stream]
Saving to: ‘lsb-security_4.1+Debian13+nmu1_amd64.deb’

lsb-security_4.1+De 100%[===================>]  19.50K  79.2KB/s    in 0.2s    

2016-12-06 16:50:13 (79.2 KB/s) - ‘lsb-security_4.1+Debian13+nmu1_amd64.deb’ saved [19968/19968]
```

```
mal@HP-Compaq-dc7900:~/lsb$ wget [http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-core_4.1+Debian13+nmu1_amd64.deb](http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-core_4.1+Debian13+nmu1_amd64.deb)
--2016-12-06 16:50:40--  [http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-core_4.1+Debian13+nmu1_amd64.deb](http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-core_4.1+Debian13+nmu1_amd64.deb)
Resolving ftp.us.debian.org (ftp.us.debian.org)... 128.30.2.26, 208.80.154.15, 128.61.240.89, ...
Connecting to ftp.us.debian.org (ftp.us.debian.org)|128.30.2.26|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44708 (44K) [application/x-debian-package]
Saving to: ‘lsb-core_4.1+Debian13+nmu1_amd64.deb’

lsb-core_4.1+Debian 100%[===================>]  43.66K  85.1KB/s    in 0.5s    

2016-12-06 16:50:41 (85.1 KB/s) - ‘lsb-core_4.1+Debian13+nmu1_amd64.deb’ saved [44708/44708]
```

```
mal@HP-Compaq-dc7900:~/lsb$ wget [http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-invalid-mta_4.1+Debian13+nmu1_all.deb](http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-invalid-mta_4.1+Debian13+nmu1_all.deb)
--2016-12-06 16:51:03--  [http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-invalid-mta_4.1+Debian13+nmu1_all.deb](http://ftp.us.debian.org/debian/pool/main/l/lsb/lsb-invalid-mta_4.1+Debian13+nmu1_all.deb)
Resolving ftp.us.debian.org (ftp.us.debian.org)... 128.61.240.89, 64.50.233.100, 64.50.236.52, ...
Connecting to ftp.us.debian.org (ftp.us.debian.org)|128.61.240.89|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 20330 (20K) [application/octet-stream]
Saving to: ‘lsb-invalid-mta_4.1+Debian13+nmu1_all.deb’

lsb-invalid-mta_4.1 100%[===================>]  19.85K  77.2KB/s    in 0.3s    

2016-12-06 16:51:04 (77.2 KB/s) - ‘lsb-invalid-mta_4.1+Debian13+nmu1_all.deb’ saved [20330/20330]
```

```
mal@HP-Compaq-dc7900:~/lsb$ sudo dpkg -i *.deb
[sudo] password for mal: 
dpkg: warning: downgrading lsb-core from 9.20160110ubuntu0.2 to 4.1+Debian13+nmu1
(Reading database ... 231490 files and directories currently installed.)
Preparing to unpack lsb-core_4.1+Debian13+nmu1_amd64.deb ...
Unpacking lsb-core (4.1+Debian13+nmu1) over (9.20160110ubuntu0.2) ...
dpkg: warning: downgrading lsb-invalid-mta from 9.20160110ubuntu0.2 to 4.1+Debian13+nmu1
Preparing to unpack lsb-invalid-mta_4.1+Debian13+nmu1_all.deb ...
Unpacking lsb-invalid-mta (4.1+Debian13+nmu1) over (9.20160110ubuntu0.2) ...
dpkg: warning: downgrading lsb-security from 9.20160110ubuntu0.2 to 4.1+Debian13+nmu1
Preparing to unpack lsb-security_4.1+Debian13+nmu1_amd64.deb ...
Unpacking lsb-security (4.1+Debian13+nmu1) over (9.20160110ubuntu0.2) ...
Setting up lsb-invalid-mta (4.1+Debian13+nmu1) ...
Setting up lsb-security (4.1+Debian13+nmu1) ...
Setting up lsb-core (4.1+Debian13+nmu1) ...
Processing triggers for man-db (2.7.5-1) ...
mal@HP-Compaq-dc7900:~/lsb$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
mal@HP-Compaq-dc7900:~/lsb$
```

After all that I rebooted and tried GE again but still no luck with the photos just a white blank although the hour glass shows briefly as though it is trying to ope

---

### Post by #&amp;thj^% on 2016-12-05
Hey! now we are getting some where;
Now we run this as below:
```
sudo apt update
sudo apt upgrade
sudo apt full-upgrade
sudo apt -f install
```
And **if there was a kernel upgrade** in the process...it would not hurt to do another reboot.
Now fingers crossed...you should have a working GE.

---

### Post by #&amp;thj^% on 2016-12-05
> **robelli said:**
> After all that I rebooted and tried GE again but still no luck with the photos just a white blank although the hour glass shows briefly as though it is trying to ope

Patience... lets move one step at a time here...See post #22

---

### Post by robelli on 2016-12-05
I have run all those and all went well . There was a new kernel in thir and I rebooted but am sorry to say that the photos are still not opening

---

### Post by #&amp;thj^% on 2016-12-06
> **robelli said:**
> I have run all those and all went well . There was a new kernel in thir and I rebooted but am sorry to say that the photos are still not opening
I'm not sure what to tell you here...I used this method to install GE.
Screenshot Included


```
$ apt policy google-earth-stable
google-earth-stable:
  Installed: 7.1.7.2606-r0
  Candidate: 7.1.7.2606-r0
  Version table:
 *** 7.1.7.2606-r0 100
        100 /var/lib/dpkg/status

```
```
apt policy lsb-core
lsb-core:
  Installed: 4.1+Debian13+nmu1
  Candidate: 9.20160110ubuntu0.2
  Version table:
     9.20160110ubuntu0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
 *** 4.1+Debian13+nmu1 100
        100 /var/lib/dpkg/status

```
```
lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

```
The only thing I can suggest here is to reinstall google-earth-stable...and make sure you have the 64bit .Deb
Good Luck

---

### Post by robelli on 2016-12-06
1Fallen, Thank you very much for your help . I have exactly the same system on my HP Laptop and it runs with no trouble . I will do as you say and try a reinstall of GE

---

### Post by cipman-p on 2016-12-06
> **robelli said:**
> 1Fallen, Thank you very much for your help . I have exactly the same system on my HP Laptop and it runs with no trouble . I will do as you say and try a reinstall of GE

Can you check if GE is still showing the panoramio photos on your HP laptop?

I'm asking because I had GE up and running on ubuntu 16.04 for months and yesterday the panoramio pics stopped showing. I updated GE to the latest 7.1.7.2606 version and no change -- no panoramio. All other gigapan, gigapix, etc photos are showing fine.

I installed the windows 7.1.7.2606 version on windows 7 on another partition and the panoramio pics are missing as well. Same as on ubuntu, I get the white frame with a grey placeholder instead of the picture.

Can someone else please double check and confirm that he has a Google Earth version installed (on whatever OS) and the panoramio photos are still showing? Tx.

---

### Post by #&amp;thj^% on 2016-12-06
[COLOR=#ff0000]***New Information***
> Panoramio no longer available after November 4, 2016[/COLOR]

Some have had better luck with First Uninstalling Google Earth completely then reinstalling...Then instead of:
```
Just to note old instructions...Do not follow this if you are having problems with a white area where Panoramio Photos Not Showing. 
cd /opt/google/earth/free
sudo wget http://www.sundru.net/wordpress/sundrumisc/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz
```
**They instead Downloaded to their Downloads Directory**. So it would go like this:
```
cd Downloads
sudo wget http://www.sundru.net/wordpress/sundrumisc/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz
```
Then extract to:
"**/opt/google/earth/free"** folder
Hope this works for those having problems with Panoramio Photos.
And more information found here:[https://productforums.google.com/forum/#!topic/maps/_h4t6SpY_II](https://productforums.google.com/forum/#!topic/maps/_h4t6SpY_II)
||Credit for this library goes to amirpli - 2013 and Ryan C. Gordon -2006||

---

### Post by robelli on 2016-12-06
cipman-p,   I have just looked into my Laptop GE and it is not showing any photos now . Is there a problem with GE .

1fallen,      We worked hard all day yesterday and now to find that there maybe a problem with GE. I noticed that my GE on the desktop here was trying to open the photos but as I said the hour glass only showed briefly each time . Maybe I should leave the photos for a while and try with them some other time . GE itself runs perfectly . It's only the photos.

---

### Post by #&amp;thj^% on 2016-12-06
Sorry to be the Bearer of this::(
> 
Panoramio no longer available after November 4, 2016
Sources: [http://www.panoramio.com/](http://www.panoramio.com/)
[https://forums.njpinebarrens.com/threads/panoramio-no-longer-available-after-november-4-2016.11525/](https://forums.njpinebarrens.com/threads/panoramio-no-longer-available-after-november-4-2016.11525/)
Don't Kill the Messenger

---

### Post by robelli on 2016-12-06
Thank you for that . We will just have to grin and bear it I suppose . Cheers

---

### Post by cipman-p on 2016-12-07
Panoramio photos are back online!
It was a glitch from google.

---

### Post by #&amp;thj^% on 2016-12-07
Well sort of:

>  Back in 2014, we announced our intention to retire Panoramio in order to invest our efforts into improving photo-sharing experiences directly inside Google Maps. In response to your feedback, we postponed these plans and worked to add features to Maps that better support the level of engagement that you have enjoyed with Panoramio. Today, with photo upload tools in Google Maps and our Local Guides program, we are providing easy ways for you to share your photos with an active and growing community. As such, we&#8217;ve decided to move forward with closing down Panoramio. To make this transition easier, we&#8217;ll provide several options to continue sharing photos through other services. If you choose, you can also export all your data and take it somewhere else.

If you have linked your Panoramio profile with a Google account, all your Panoramio photos will be copied to the Google Album Archive at full resolution after Panoramio goes away. These copied photos will not use any of your Google storage quota. Your Panoramio photos that appear in Google Maps will continue to appear in Maps, unless you delete them later from the Maps Contributions panel. Note: You must link your Panoramio profile with a Google+ account for your photos to be automatically copied.

_**After November 4, 2016, you&#8217;ll continue to have access to your photos in Panoramio for a year, but you will no longer be able to add new photos, likes, or comments. Below, we&#8217;ve included resources to help you manage or export your data.**_

Tip: Although you&#8217;ll no longer be able to create new accounts, upload your photos, comment or like other content in Panoramio after November 4, 2016, you&#8217;ll still have access to your photos and be able to export your data until November 2017.** After that, if your Panoramio account is linked with a Google account, we'll copy your photos to the Google Album Archive so you can access them even after Panoramio is retired. **

Source: [https://www.panoramio.com/](https://www.panoramio.com/)

---

### Post by cipman-p on 2016-12-07
I've read that some time ago. My understanding was that the panoramio photos should be available as a GE layer until november 2017 as is -- i.e. without google account linking mambo-jumbo. What happened the other day was not supposed to happen -- that is to be able to access the pics on the panoramio server (if you had the links to them) but not being able to see them in GE.
Besides that, it would have been kinda stupid from google to include the panoramio layer in the latest/current GE versions (7.1.7.2606 as we speak) and then shut down panoramio API few days after that

---

### Post by robelli on 2016-12-07
Hi 1fallen,
The Photos in GE showed up this morning . Will make hay while the sun shines. GE and the photos load very quickly. Thank you very much for all the help you gave me and at least I know that all the work we did was not in vain as I know that the computer is not at fault . I looked at Google Maps and when we finally do lose  panoramio I reckon I can/will live with that . Have a Merry Xmas and a Happy New Year

---

### Post by #&amp;thj^% on 2016-12-07
> **robelli said:**
> Hi 1fallen,
The Photos in GE showed up this morning . Will make hay while the sun shines. GE and the photos load very quickly. Thank you very much for all the help you gave me and at least I know that all the work we did was not in vain as I know that the computer is not at fault . I looked at Google Maps and when we finally do lose  panoramio I reckon I can/will live with that . Have a Merry Xmas and a Happy New Year

Your very welcome and Thank You for the well wish's and right back at Ya:KS
Just a heads up expect short random breaks in this as I have been warned by the team.
Best Regards

---

