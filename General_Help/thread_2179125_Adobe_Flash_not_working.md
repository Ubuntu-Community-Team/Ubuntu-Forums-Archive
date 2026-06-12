---
title: "Adobe Flash not working"
date: 2013-10-06
forum: General Help
---

### Post by ventsy2 on 2013-10-06
Ubuntu 12.06 installed with the appropriate restricted extras, unfortunately I'm unable to see any flash content. Firefox 24.0 seems to be trying to load youtube but the playback never starts. I get the following error message on the console: ###!!! [Parent][RPCChannel] Error: Channel error: cannot send/recv

I found some posts suggesting this is due to an Nvidia driver problem, but I have Radeon 9550. Chromium just shows a pop up that it can't load flash.

Any ideas?
Here is some info about the system:

```
uname -a
Linux Linx01 3.2.0-54-generic-pae #82-Ubuntu SMP Tue Sep 10 20:29:22 UTC 2013 i686 athlon i386 GNU/Linux


lspci
00:00.0 Host bridge: VIA Technologies, Inc. KT880 Host Bridge (rev 80)
00:00.1 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:09.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0e.0 Communication controller: Intel Corporation 536EP Data Fax Modem
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV350 [Radeon 9550]
01:00.1 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] RV350 [Radeon 9550] (Secondary)

locate libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so

ll /usr/lib/flashplugin-installer/libflashplayer.so 
-rw-r--r-- 1 root root 17422820 Oct  6 16:14 /usr/lib/flashplugin-installer/libflashplayer.so

dpkg -l | grep flash
ii  flashplugin-installer                  11.2.202.310ubuntu0.12.04.1             Adobe Flash Player plugin installer
ii  flashplugin-nonfree-extrasound         0.0.svn2431-3ubuntu1                    Adobe Flash Player platform support library for Esound and OSS

dpkg -l | grep "ubuntu-re*"
ii  ubuntu-restricted-addons               12                                      Commonly used restricted packages for Ubuntu
ii  ubuntu-restricted-extras               57                                      Commonly used restricted packages for Ubuntu


```

Also, firefox lists Shockwave Flash 11,2,202,301 as installed and always active, file: libflashplayer.so last updated: 10/06/2013

---

### Post by Donut50 on 2013-10-08
have you tried other browsers like chromium or google chrome?
and did you have tried to reinstall flash to see if it is working again?
google chrome haves flash player built in, maybe you shoould try that one out :)

---

### Post by ventsy2 on 2013-10-08
Both Chrome & Chromium fail to load the flash plugin.

---

### Post by nigel5 on 2013-10-08
Hi ventsy2,
I've been having this problem since I returned to Linux after a 9 year hiatus.  Your problem sounded so similar to mine, I eagerly awaited any response or help you might get.  So far, nothing that helps me.  I've done in depth searches and tried so many different ideas found in the ubuntu and other discussion groups.  Like you, nothing has yet worked for me.  It's so frustrating when you've done everything that the 'professionals' tell you to do and to the letter, yet nothing.  I had a similar issue with my wireless adapter, and after a week, I found a solution and now it works.  Only thing is, Ubuntu 12.04 now treats my desktop like a laptop!  I don't know how to do that code thing you did on your original posting, otherwise I'd let you see mine, since you showed me yours!

---

### Post by whitesmith on 2013-10-08
> **ventsy2 said:**
> Ubuntu 12.06 installed with the appropriate restricted extras, unfortunately I'm unable to see any flash content. Firefox 24.0 seems to be trying to load youtube but the playback never starts.Don't know about FF but Chromium works just fine with youtube, which has made the conversion to HTML5. Note that a plugin is not required for this to work. Cheers.

---

### Post by Allavona on 2013-10-08
Remove the Adobe Flash Player via synaptic (if installed) or the software center. Once removed, get the flash player from Adobe's site itself.

---

### Post by nigel5 on 2013-10-09
Not only have I tried downloading Flash from Adobe, I've done it from the Software Centre and through Terminal.  I've tried it many times and have followed many threads in this and other venues.  Still no luck.   Further, tried installing Chrome as an alternative to Firefox, but although installation seemed to go well, when I open Chrome, it stays open just for a few seconds then disappears.  I tried this too from the terminal and the software centre, and several times, but no luck.  I just glimpsed through the excellent "Getting Started with Ubuntu 12.04" manual and got a few insights, but nothing regarding my Flash problems.

---

### Post by nigel5 on 2013-10-10
I've found a thread here: [https://answers.launchpad.net/ubuntu/+source/flashplugin-nonfree/+question/217007](https://answers.launchpad.net/ubuntu/+source/flashplugin-nonfree/+question/217007) that shows some promise regarding this resolution.

---

### Post by Yellow Pasque on 2013-10-10
> VIA Technologies, Inc. KT880
KT880 -> Socket A -> old CPU without SSE2 support -> Flash 11.2.x doesn't work
Remove all Flash packages/files you installed, close Firefox, then:
```
cd ~/.mozilla
mkdir plugins
wget https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz
tar xzf flashplayer11_1r102_63_linux.i386.tar.gz
mv libflashplayer.so plugins/
```

---

### Post by nigel5 on 2013-10-10
[ 						 							 ]("http://ubuntuforums.org/member.php?u=327594")[**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594"):
You're my hero!  I have a Socket A CPU and did what you suggested.  At least now YouTube works.  I can't get swf on all sites, but it is an improvement.  Just in case things go t**s up, how do I get rid of whatever it was I installed?  Could you give me the code to type in?  Many thanks.

---

### Post by Yellow Pasque on 2013-10-10
> **nigel5 said:**
>  Just in case things go t**s up, how do I get rid of whatever it was I installed?

Since it's not part of a package, you would just delete it:
```
rm ~/.mozilla/plugins/libflashplayer.so
```

You would also delete the tarball file (which you can do now, but unless you're hurting for disk space, I wouldn't):
```
rm ~/.mozilla/flashplayer11_1r102_63_linux.i386.tar.gz
```

---

### Post by ventsy2 on 2013-11-18
Good catch! 

I was unable to download the file from the github URL provided by [COLOR=#000000]Temüjin[/COLOR], so here is what I did to get it to work:

Clean up:
```

sudo apt-get remove adobe-flashplugin
sudo apt-get remove adobe-flash
sudo apt-get remove adobe-flashplugin-installer
find / -name "libflashplayer.so" -delete

```

You can download older versions of FP from Adobe here: [http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)
Or if you want to stick with the version [COLOR=#000000]Temüjin recommended (as I did):

[/COLOR]```

cd ~/.mozilla
mkdir plugins

wget http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip
unzip fp_11.1.102.63_archive.zip

```

Adobe are bundling versions for a few different operating systems and architectures (32 vs 64 bit) in that zip, so you need to make sure you pick the one that's right for you.
Here is what I installed for 32 bit Linux:

```

tar -xf fp_11.1.102.63_archive/11_1r102_63_32bit/flashplayer11_1r102_63_linux.i386.tar.gz
mv libflashplayer.so ./plugins/

```


Now the caveat (what you thought everything will just work??): Firefox is complaining that the version of Flash you have installed is out of date and has security vulnerability, so it won't let you use it. I'm still trying to figure out a work around that. 
Chromium doesn't care and plays flash like a champ...

---

