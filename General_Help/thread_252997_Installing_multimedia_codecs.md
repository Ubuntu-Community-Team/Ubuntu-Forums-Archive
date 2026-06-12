---
title: "Installing multimedia codecs"
date: 2006-09-07
forum: General Help
---

### Post by OtubrabNad on 2006-09-07
Can someone give me a simple step-by-step procedure for installing multimedia codecs so I can play mp3 files and the like. Please don't post a link to another thread as I've been to several, tried their suggestions, and have ultimately failed. I've also tried programs like EasyLinux that are supposed to set up the codecs for you, but these efforts have also been futile. Thanks.

---

### Post by kinematic on 2006-09-07
copy'n'paste these instructions in a terminal: [http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)

---

### Post by skymt on 2006-09-07
@kinematic: The OP just said EasyUbuntu didn't work for him!

@OtubrabNad: Here's what to do:

* Run System > Administration > Software Preferences

* Under the Installation Media tab, choose Ubuntu 6.06 LTS (Binary) and click Edit

* Make sure "Restricted copyright", "Community maintained (Universe)", and "Non-free (Multiverse)" are checked.

* Go to a terminal and copy and paste the following, one at a time:```
sudo aptitude update
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-pitfdll 
sudo aptitude install gstreamer0.10-plugins-bad gstreamer0.10-plugins-base
sudo aptitude install gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly
sudo aptitude install libxine-extracodecs
wget http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb
sudo dpkg -i w32codecs_20060611-1plf1_i386.deb
rm w32codecs_20060611-1plf1_i386.deb
```

Then you'll have pretty much everything.

---

### Post by OtubrabNad on 2006-09-07
Thanks, skymt. Worked perfectly.

---

