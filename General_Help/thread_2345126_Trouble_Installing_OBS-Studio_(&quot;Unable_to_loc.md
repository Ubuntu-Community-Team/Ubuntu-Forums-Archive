---
title: "Trouble Installing OBS-Studio (&quot;Unable to locate package&quot;)"
date: 2016-11-30
forum: General Help
---

### Post by neelcor on 2016-11-30
Hi,

I'm trying to install OBS-Studio but I'm receiving the following error,  "E: Unable to locate package obs-studio". I have run the commands as  listed on the OBS Github. [https://github.com/jp9000/obs-studio/wiki/Install-Instructions#linux](https://github.com/jp9000/obs-studio/wiki/Install-Instructions#linux)

```
sudo add-apt-repository ppa:obsproject/obs-studio
sudo apt-get update && sudo apt-get install obs-studio
```

This is my first time using ubuntu, excuse my naivety.. I may be missing something obvious.

```
rgsea@rgsea-desktop:~$ sudo add-apt-repository ppa:obsproject/obs-studio
[sudo] password for rgsea: 
 Latest stable release of OBS Studio
 More info: https://launchpad.net/~obsproject/+archive/ubuntu/obs-studio
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpkf9hu8ew/secring.gpg' created
gpg: keyring `/tmp/tmpkf9hu8ew/pubring.gpg' created
gpg: requesting key F425E228 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpkf9hu8ew/trustdb.gpg: trustdb created
gpg: key F425E228: public key "Launchpad PPA for obsproject" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
rgsea@rgsea-desktop:~$ sudo apt-get update && sudo apt-get install obs-studio
Hit:1 http://ppa.launchpad.net/obsproject/obs-studio/ubuntu xenial InRelease
Hit:2 http://ports.ubuntu.com xenial InRelease
Hit:3 http://ports.ubuntu.com xenial-updates InRelease
Hit:4 http://ppa.launchpad.net/ubuntu-pi-flavour-makers/ppa/ubuntu xenial InRelease
Hit:5 http://ports.ubuntu.com xenial-security InRelease
Hit:6 http://ports.ubuntu.com xenial-backports InRelease
Reading package lists... Done                      
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package obs-studio
rgsea@rgsea-desktop:~$ 

```

Thanks for your help and time.

---

### Post by oldrocker99 on 2016-11-30
Welcome to the forums!

You didn't say which version of Ubuntu you're using. The PPA you added may not have a version for the system you're running, or it's a defective PPA. A few PPAs are questionable.

In the future, please copy and paste the terminal output using (code)text(/code), using square brackets, not parentheses. That makes it easier to read, and saves forum disk space.

You also (appear?) to be running as root. This is highly unrecommended; use your normal account and sudo instead.

---

### Post by howefield on 2016-11-30
I'd suggest trying again in a few minutes, looks like it may have been issues with the ppa/launchpad.

---

### Post by neelcor on 2016-11-30
I have edited the post, I can see why it's better to display output like this.. much cleaner!

I have also added the "xubuntu" tag.

If I run *lsb_release -a*, this is my output.

```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial
```

> **howefield said:**
> I'd suggest trying again in a few minutes, looks like it may have been issues with the ppa/launchpad.

I have been at it for at least an hour, is there perhaps a way to download the repository and install it manually using the terminal?

---

### Post by howefield on 2016-11-30
> **neelcor said:**
> I have been at it for at least an hour, is there perhaps a way to download the repository and install it manually using the terminal?

The PPA or launchpad was being updated a short time ago but appears to be ok as of now. That's why I suggested trying again but yes you can download the package directly from the ppa and install locally.

[https://launchpad.net/~obsproject/+archive/ubuntu/obs-studio/+packages](https://launchpad.net/~obsproject/+archive/ubuntu/obs-studio/+packages)

---

### Post by neelcor on 2016-11-30
> **howefield said:**
> The PPA or launchpad was being updated a short time ago but appears to be ok as of now. That's why I suggested trying again but yes you can download the package directly from the ppa and install locally.

[https://launchpad.net/~obsproject/+archive/ubuntu/obs-studio/+packages](https://launchpad.net/~obsproject/+archive/ubuntu/obs-studio/+packages)

Once I've downloaded the files, what do I need to do?

---

### Post by howefield on 2016-11-30
To download the 64 bit version for Xenial, use...

```
wget https://launchpad.net/~obsproject/+archive/ubuntu/obs-studio/+files/obs-studio_0.16.2.1-544~xenial_amd64.deb -P ~/Downloads
```
and to install the package which has been downloaded into the ~/Downloads folder, use...
```
sudo apt install ~/Downloads/obs-studio_0.16.2.1-544~xenial_amd64.deb
```

If it is the 32 bit package that you need then download it with
```
wget https://launchpad.net/~obsproject/+archive/ubuntu/obs-studio/+files/obs-studio_0.16.2.1-544~xenial_i386.deb -P ~/Downloads
```

But as I said, the PPA should now be back up unless there is an issue specifically between you and connection to launchpad.

---

### Post by neelcor on 2016-11-30
I tried running the code incorporating launchpad again, but again, no success.

When I tried installing it manually, (my system has a 32 bit architecture) I was presented with the following.

```
2016-12-01 00:02:53 (717 KB/s) - ‘/home/rgsea/Downloads/obs-studio_0.16.2.1-544~xenial_i386.deb.1’ saved [2808518/2808518]

rgsea@rgsea-desktop:~$ sudo apt install ~/Downloads/obs-studio_0.16.2.1-544~xenial_i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'obs-studio:i386' instead of '/home/rgsea/Downloads/obs-studio_0.16.2.1-544~xenial_i386.deb'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 obs-studio:i386 : Depends: libavcodec-ffmpeg56:i386 (>= 7:2.4) but it is not installable or
                            libavcodec-ffmpeg-extra56:i386 (>= 7:2.4) but it is not installable
                   Depends: libavdevice-ffmpeg56:i386 (>= 7:2.4) but it is not installable
                   Depends: libavfilter-ffmpeg5:i386 (>= 7:2.4) but it is not installable
                   Depends: libavformat-ffmpeg56:i386 (>= 7:2.4) but it is not installable
                   Depends: libavutil-ffmpeg54:i386 (>= 7:2.4) but it is not installable
                   Depends: libc6:i386 (>= 2.17) but it is not installable
                   Depends: libcurl3:i386 (>= 7.16.2) but it is not installable
                   Depends: libdbus-1-3:i386 (>= 1.9.14) but it is not installable
                   Depends: libfdk-aac0:i386 (>= 0.1.1) but it is not installable
                   Depends: libfontconfig1:i386 (>= 2.11.94) but it is not installable
                   Depends: libfreetype6:i386 (>= 2.2.1) but it is not installable
                   Depends: libgcc1:i386 (>= 1:4.2) but it is not installable
                   Depends: libjack-jackd2-0:i386 (>= 1.9.5~dfsg-14) but it is not installable or
                            libjack-0.116:i386 but it is not installable
                   Depends: libpulse0:i386 (>= 0.99.1) but it is not installable
                   Depends: libqt5core5a:i386 (>= 5.5.0) but it is not installable
                   Depends: libqt5gui5:i386 (>= 5.3.0) but it is not installable or
                            libqt5gui5-gles:i386 (>= 5.3.0) but it is not installable
                   Depends: libqt5widgets5:i386 (>= 5.2.0) but it is not installable
                   Depends: libqt5x11extras5:i386 (>= 5.1.0) but it is not installable
                   Depends: libstdc++6:i386 (>= 5.2) but it is not installable
                   Depends: libswresample-ffmpeg1:i386 (>= 7:2.4) but it is not installable
                   Depends: libswscale-ffmpeg3:i386 (>= 7:2.4) but it is not installable
                   Depends: libudev1:i386 (>= 183) but it is not installable
                   Depends: libv4l-0:i386 (>= 0.5.0) but it is not installable
                   Depends: libx11-6:i386 but it is not installable
                   Depends: libx11-xcb1:i386 but it is not installable
                   Depends: libx264-148:i386 but it is not installable
                   Depends: libxcb-shm0:i386 but it is not installable
                   Depends: libxcb-xfixes0:i386 but it is not installable
                   Depends: libxcb-xinerama0:i386 but it is not installable
                   Depends: libxcb1:i386 but it is not installable
                   Depends: libxcomposite1:i386 (>= 1:0.3-1) but it is not installable
                   Depends: libxfixes3:i386 but it is not installable
                   Depends: zlib1g:i386 (>= 1:1.2.6) but it is not installable
E: Unable to correct problems, you have held broken packages.
rgsea@rgsea-desktop:~$ 


```

Thank you for your help so far.

---

### Post by neelcor on 2016-11-30
> **neelcor said:**
> I tried running the code incorporating launchpad again, but again, no success.

When I tried installing it manually, (my system has a 32 bit architecture) I was presented with the following.

```
2016-12-01 00:02:53 (717 KB/s) - ‘/home/rgsea/Downloads/obs-studio_0.16.2.1-544~xenial_i386.deb.1’ saved [2808518/2808518]

rgsea@rgsea-desktop:~$ sudo apt install ~/Downloads/obs-studio_0.16.2.1-544~xenial_i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'obs-studio:i386' instead of '/home/rgsea/Downloads/obs-studio_0.16.2.1-544~xenial_i386.deb'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 obs-studio:i386 : Depends: libavcodec-ffmpeg56:i386 (>= 7:2.4) but it is not installable or
                            libavcodec-ffmpeg-extra56:i386 (>= 7:2.4) but it is not installable
                   Depends: libavdevice-ffmpeg56:i386 (>= 7:2.4) but it is not installable
                   Depends: libavfilter-ffmpeg5:i386 (>= 7:2.4) but it is not installable
                   Depends: libavformat-ffmpeg56:i386 (>= 7:2.4) but it is not installable
                   Depends: libavutil-ffmpeg54:i386 (>= 7:2.4) but it is not installable
                   Depends: libc6:i386 (>= 2.17) but it is not installable
                   Depends: libcurl3:i386 (>= 7.16.2) but it is not installable
                   Depends: libdbus-1-3:i386 (>= 1.9.14) but it is not installable
                   Depends: libfdk-aac0:i386 (>= 0.1.1) but it is not installable
                   Depends: libfontconfig1:i386 (>= 2.11.94) but it is not installable
                   Depends: libfreetype6:i386 (>= 2.2.1) but it is not installable
                   Depends: libgcc1:i386 (>= 1:4.2) but it is not installable
                   Depends: libjack-jackd2-0:i386 (>= 1.9.5~dfsg-14) but it is not installable or
                            libjack-0.116:i386 but it is not installable
                   Depends: libpulse0:i386 (>= 0.99.1) but it is not installable
                   Depends: libqt5core5a:i386 (>= 5.5.0) but it is not installable
                   Depends: libqt5gui5:i386 (>= 5.3.0) but it is not installable or
                            libqt5gui5-gles:i386 (>= 5.3.0) but it is not installable
                   Depends: libqt5widgets5:i386 (>= 5.2.0) but it is not installable
                   Depends: libqt5x11extras5:i386 (>= 5.1.0) but it is not installable
                   Depends: libstdc++6:i386 (>= 5.2) but it is not installable
                   Depends: libswresample-ffmpeg1:i386 (>= 7:2.4) but it is not installable
                   Depends: libswscale-ffmpeg3:i386 (>= 7:2.4) but it is not installable
                   Depends: libudev1:i386 (>= 183) but it is not installable
                   Depends: libv4l-0:i386 (>= 0.5.0) but it is not installable
                   Depends: libx11-6:i386 but it is not installable
                   Depends: libx11-xcb1:i386 but it is not installable
                   Depends: libx264-148:i386 but it is not installable
                   Depends: libxcb-shm0:i386 but it is not installable
                   Depends: libxcb-xfixes0:i386 but it is not installable
                   Depends: libxcb-xinerama0:i386 but it is not installable
                   Depends: libxcb1:i386 but it is not installable
                   Depends: libxcomposite1:i386 (>= 1:0.3-1) but it is not installable
                   Depends: libxfixes3:i386 but it is not installable
                   Depends: zlib1g:i386 (>= 1:1.2.6) but it is not installable
E: Unable to correct problems, you have held broken packages.
rgsea@rgsea-desktop:~$ 


```

Thank you for your help so far.

On second thought, could it have something to do with my processor, I am running xubuntu on a Pi 3 so my architecture is most likely abnormal.

```
rgsea@rgsea-desktop:~$ sudo uname -a
Linux rgsea-desktop 4.1.19-v7+ #858 SMP Tue Mar 15 15:56:00 GMT 2016 armv7l armv7l armv7l GNU/Linux
```

---

### Post by DogMatix on 2016-11-30
You could try
```

sudo apt install -f

```

Edit:

Or maybe you should have run:
```

sudo dpkg -i ~/Downloads/obs-studio_0.16.2.1-544~xenial_i386.deb

```
rather than
```

sudo apt install ~/Downloads/obs-studio_0.16.2.1-544~xenial_i386.deb

```

---

### Post by neelcor on 2016-12-01
Still no luck, anything else I could try?

---

### Post by howefield on 2016-12-01
> **neelcor said:**
> On second thought, could it have something to do with my processor, I am running xubuntu on a Pi 3 so my architecture is most likely abnormal.

```
rgsea@rgsea-desktop:~$ sudo uname -a
Linux rgsea-desktop 4.1.19-v7+ #858 SMP Tue Mar 15 15:56:00 GMT 2016 armv7l armv7l armv7l GNU/Linux
```

There are builds for the amd64 and i386 architecture in the repository you referred to, you need one built for the arm architecture that you are running. Looks like a no go.

---

### Post by neelcor on 2016-12-01
> **howefield said:**
> There are builds for the amd64 and i386 architecture in the repository you referred to, you need one built for the arm architecture that you are running. Looks like a no go.

That's a shame, thanks for your help regardless.

---

### Post by dragonfly41 on 2016-12-01
Theory:
Depending on how important this is for you .. a possible option is ..
install VirtualBox
install into VirtualBox a version of Ubuntu as VM into which OBS-Studio can be installed
 
This does mean a heavy baggage just to run OBS-Studio.

---

