---
title: "ubuntu 22.04 wrong Libreoffice version"
date: 2023-07-20
forum: General Help
---

### Post by cscj01 on 2023-07-20
I am running Ubuntu 22.04 x64

I have a condition I have never encountered.  I use LO Base forms as a front-end to MySQL databases .  The official repository version is 7.3.7, and as far as i can tell, it will be the version for the life of 22.04.  I was having some issues with Base  crashingn frequently and decided to try the PPA veersion of LO 7.4 to see if the problem persisted.  I addred the ppa with the following ```
sudo add-apt-repository ppa:libreoffice/ppa
sudo update
sudo install
```and ended up with version 7.5.5.  The problems were worse, so I then ran the following to revert back to what I had before:```
sudo ppa-purge ppa:libreoffice/ppa
```

Lo and behold, I got 7.4.7 which is the version for 22.10.  I am at a loss as to how to get back to 7.3.7.  I know I can  uninstall LO, but I do not want to lose the forms I have created for the application I run against the databases.  So is there a way to do this that is straight forwarrd?  If not, what do I need to save so I can restore the LO Base coding I have?

---

### Post by #&amp;thj^% on 2023-07-20
Show us first 
```
sudo apt dist-upgrade -s
```
Nothing real will take place it is merely a mock run.
Also show:
```
apt policy libreoffice
```
Then can we can plot a course of action.
EDIT: I see your problem 2 versions
```
 libreoffice | 1:7.3.2-0ubuntu2                    | jammy                     | source
 libreoffice | 1:7.3.2-0ubuntu2                    | jammy/universe            | amd64, arm64, armhf, ppc64el, s390x
 libreoffice | 1:7.3.7-0ubuntu0.22.04.3            | jammy-security            | source
 libreoffice | 1:7.3.7-0ubuntu0.22.04.3            | jammy-security/universe   | amd64, arm64, armhf, ppc64el, s390x
 libreoffice | 1:7.3.7-0ubuntu0.22.04.3            | jammy-updates             | source
 libreoffice | 1:7.3.7-0ubuntu0.22.04.3            | jammy-updates/universe    | amd64, arm64, armhf, ppc64el, s390x
 libreoffice | 1:7.4.7-0ubuntu0.22.10.1~bpo22.04.1 | jammy-backports           | source
 libreoffice | 1:7.4.7-0ubuntu0.22.10.1~bpo22.04.1 | jammy-backports/universe  | amd64, arm64, armhf, ppc64el, s390x


```

---

### Post by cscj01 on 2023-07-20
```
sudo apt dist-upgrade -s
[sudo] password for butch: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  vlc-plugin-qt libvlc5 libimage-magick-perl vlc-data libvlccore9 vlc
  imagemagick vlc-bin vlc-l10n libavdevice58 ffmpeg libopenexr25
  libmagick++-6.q16-8 libpostproc55 libmagickcore-6.q16-6-extra libpano13-3
  vlc-plugin-samba libavcodec58 libimage-magick-q16-perl libpano13-bin
  libmagickwand-6.q16-6 vlc-plugin-notify libavutil56 imagemagick-6.q16
  libswscale5 libmagickcore-6.q16-6 vlc-plugin-access-extra vlc-plugin-skins2
  vlc-plugin-video-splitter libswresample3 imagemagick-6-common
  vlc-plugin-video-output libavformat58 libvlc-bin vlc-plugin-base
  vlc-plugin-visualization libavfilter7
Learn more about Ubuntu Pro at https://ubuntu.com/pro
#
# An OpenSSL vulnerability has recently been fixed with USN-6188-1 & 6119-1:
# CVE-2023-2650: possible DoS translating ASN.1 object identifiers.
# Ensure you have updated the package to its latest version.
#
The following packages have been kept back:
  gjs libgjs0g
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

```
apt policy libreoffice
libreoffice:
  Installed: (none)
  Candidate: 1:7.3.7-0ubuntu0.22.04.3
  Version table:
     1:7.4.7-0ubuntu0.22.10.1~bpo22.04.1 100
        100 http://us.archive.ubuntu.com/ubuntu jammy-backports/universe amd64 Packages
     1:7.3.7-0ubuntu0.22.04.3 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 Packages
     1:7.3.2-0ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
```

---

### Post by #&amp;thj^% on 2023-07-20
Repos look good so nothing from the PPA
run this please and copy back:
EDIT: I fixed a type o "1 :"
```
sudo apt install libreoffice 7.3.2-0ubuntu2 -s
```

---

### Post by cscj01 on 2023-07-20
Did you mean 7.3.7?  I received the following when I used 7.3.2:

sudo apt install libreoffice 7.3.2-0ubuntu2 -s
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package 7.3.2-0ubuntu2
E: Couldn't find any package by glob '7.3.2-0ubuntu2'

---

### Post by #&amp;thj^% on 2023-07-20
> **cscj01 said:**
> Did you mean 7.3.7?  I received the following when I used 7.3.2:

Yes I did, I'm doing the worst thing right now multi-tasking...lol
Good catch.

---

### Post by cscj01 on 2023-07-20
I think the format is wrong (or some characters in the string).  I get the same error with 7.3.7 as before.

---

### Post by #&amp;thj^% on 2023-07-20
I'm so sorry, as a tester I seldom install any office apps but this is proven on my end now
```
sudo apt install libreoffice7.3
```
And it looks like the jump to 7.4 is right around the corner just a heads up.

---

### Post by cscj01 on 2023-07-20
> **1fallen said:**
> I'm so sorry, as a tester I seldom install any office apps but this is proven on my end now
```
sudo apt install libreoffice7.3
```
And it looks like the jump to 7.4 is right around the corner just a heads up.

That gives me the same error.  I can get 7.3.7 from backports, but I've never used them.  Maybe they have already moved to 7.4  All my searching reveals that 7.3 has been relegated to backports.  So maybe I'll have to live with this version.  If so, I'll have to see if someone on the opendocument help web site can resolve the problem.  Thank you for your persistence and help.  If you find out anything else, let me know.  I'll leave this open for a short while.

---

### Post by #&amp;thj^% on 2023-07-20
same error? interesting.
Thanks for your kindness, if next time I promise to be more attentive. (Too many moving directions right now lol)
Please keep us updated
Best Regards

---

### Post by #&amp;thj^% on 2023-07-20
Breaking News! I in a KVM  rolled back to 7.3 by uninstalling 7.4 first. No settings or documents were lost.
Hope the same for you.

---

