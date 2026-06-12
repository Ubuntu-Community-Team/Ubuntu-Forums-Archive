---
title: "Webupd8, PPA for Oracle Java8, 404, error exit"
date: 2017-10-18
forum: General Help
---

### Post by marksmarks on 2017-10-18
Please forgive me if this is in the wrong forum (or even the wrong BBS).  I don't know where else to ask.
--

The Webupd8 Oracle-java8-installer is failing to download (and thus install Java) on my Ubuntu 16.04.3 computer tonight Oct 17.  I successfully used this same Java8 installer on this same machine a few weeks ago. 

– >> I took a look at the Oracle website and apparently there is a new version released.  Java8 Update151.  Released Oct 17, 2017 << -

Is the PPA installer hard coded to a specific Java version?

I guess all I can do is watch the PPA to see when the installer for 8u151 replaces installer for 8u144 ?  Then try again?

When it failed it left me with “broken package(s)”.  I think by doing a “complete removal” (synaptic) those are gone now.

I have downloaded the new Java8 update151, however a manual install by me may really screw things up. :-(

I am not complaining. I’m thankful for the PPA.

PS: The above was after doing a bare metal install, today, followed by installing all updates.  

==
Connecting to download.oracle.com (download.oracle.com)|23.61.195.115|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2017-10-17 22:05:25 ERROR 404: Not Found.

download failed
Oracle JDK 8 is NOT installed.
dpkg: error processing package oracle-java8-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
===

---

### Post by tarunrazdan on 2017-10-18
I am also facing the same problem since yesterday. It was working a day before.

Location: [http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz?AuthParam=1508310042_a01ba9002b1a9f4cecaf9df2429fe4d0](http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz?AuthParam=1508310042_a01ba9002b1a9f4cecaf9df2429fe4d0) [following]
--2017-10-18 06:58:42--  [http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz?AuthParam=1508310042_a01ba9002b1a9f4cecaf9df2429fe4d0](http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz?AuthParam=1508310042_a01ba9002b1a9f4cecaf9df2429fe4d0)
Connecting to download.oracle.com (download.oracle.com)|23.220.203.10|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2017-10-18 06:58:43 ERROR 404: Not Found.


download failed
Oracle JDK 8 is NOT installed.
dpkg: error processing package oracle-java8-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java8-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by erandav on 2017-10-18
Same issue here.

> Resolving download.oracle.com (download.oracle.com)... 23.219.92.200, 23.219.92.226
Connecting to download.oracle.com (download.oracle.com)|23.219.92.200|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz) [following]
--2017-10-18 07:54:57--  [https://edelivery.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 104.96.237.225, 2600:1408:10:297::2d3e, 2600:1408:10:286::2d3e
Connecting to edelivery.oracle.com (edelivery.oracle.com)|104.96.237.225|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz?AuthParam=1508313417_b6895d4dcdf57334d0020f5d016135c6](http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz?AuthParam=1508313417_b6895d4dcdf57334d0020f5d016135c6) [following]
--2017-10-18 07:54:57--  [http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz?AuthParam=1508313417_b6895d4dcdf57334d0020f5d016135c6](http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz?AuthParam=1508313417_b6895d4dcdf57334d0020f5d016135c6)
Connecting to download.oracle.com (download.oracle.com)|23.219.92.200|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2017-10-18 07:54:57 ERROR 404: Not Found.

download failed
Oracle JDK 8 is NOT installed.
dpkg: error processing package oracle-java8-installer (--configure):

---

### Post by again? on 2017-10-18
> JRE Expiration Date
The JRE expires whenever a new release with security vulnerability fixes becomes available. 
Critical patch updates, which contain security vulnerability fixes, are announced one year in advance on Critical Patch Updates, Security Alerts and Third Party Bulletin. 
This JRE (version 8u144) will expire with the release of the next critical patch update scheduled for October 17, 2017.

Seems to be hardcoded in the installer.
```
PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/**8u144-b01**/090f390dda5b47b9b721c7dfaa008135/$FILENAME #must be modified for each release
```
May have to wait for Andrew to update the deb to point latest release.
Be patient. :cool:
> WebUpd8 is currently managed by one man: Andrew 
(this includes: writing articles and testing, managing the WebUpd8 PPAs and pages on Facebook, Google+, etc.).

---

### Post by andrewkew on 2017-10-18
I am having the exact same problem as well.

Looks like the problem is that the PPA is trying to download java8U144 which is now an archived version so the URL is different (accessible via [http://download.oracle.com/otn/](http://download.oracle.com/otn/) not [http://download.oracle.com/otn-pub/](http://download.oracle.com/otn-pub/))
The only versions that aren't archived and accessible via otn-pub are 151 and 152.

Like you said I think the oracle-java8-installer package is tied to u144 so if you want to use that installed from the PPA then we have to wait for them to update the version it is trying to install, or manually install Java ourselves (or use openJDK)

---

### Post by g1zmo2 on 2017-10-18
As a temporary workaround I've patched installer:


```

sudo sed -i 's|JAVA_VERSION=8u144|JAVA_VERSION=8u152|' oracle-java8-installer.*
sudo sed -i 's|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u152-b16/aa0333dd3019491ca4f6ddbe78cdb6d0/|' oracle-java8-installer.*
sudo sed -i 's|SHA256SUM_TGZ="e8a341ce566f32c3d06f6d0f0eeea9a0f434f538d22af949ae58bc86f2eeaae4"|SHA256SUM_TGZ="218b3b340c3f6d05d940b817d0270dfe0cfd657a636bad074dcabe0c111961bf"|' oracle-java8-installer.*
sudo sed -i 's|J_DIR=jdk1.8.0_144|J_DIR=jdk1.8.0_152|' oracle-java8-installer.*

```

---

### Post by polentino911 on 2017-10-18
> **g1zmo2 said:**
> As a temporary workaround I've patched installer:
```

sudo sed -i 's|JAVA_VERSION=8u144|JAVA_VERSION=8u152|' oracle-java8-installer.*
sudo sed -i 's|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u152-b16/aa0333dd3019491ca4f6ddbe78cdb6d0/|' oracle-java8-installer.*
sudo sed -i 's|SHA256SUM_TGZ="e8a341ce566f32c3d06f6d0f0eeea9a0f434f538d22af949ae58bc86f2eeaae4"|SHA256SUM_TGZ="218b3b340c3f6d05d940b817d0270dfe0cfd657a636bad074dcabe0c111961bf"|' oracle-java8-installer.*
sudo sed -i 's|J_DIR=jdk1.8.0_144|J_DIR=jdk1.8.0_152|' oracle-java8-installer.*

```

for anybody wondering from where those commands should be executed: 
```
cd [FONT=monospace][COLOR=#000000]/var/lib/dpkg/info[/COLOR][/FONT]
```

---

### Post by krownid on 2017-10-18
Thank you guys so much.  I thought I botched a script I wrote to auto install this as this was the first day I gave it a test run.  Luckily I found this before I pulled out any hair.

Thanks again g1zmo2 and polentino911.

---

### Post by marksmarks on 2017-10-18
So,... could the script(s) be modified to download all needed components >> before << starting the install?

Then the message would have been, "No changes were made to your system because we were unable to gather/download/locate all necessary components"

Personally, I'm still not sure what other changes the PPA script made to my system before it aborted on the download error.

---

### Post by pizzapoindexter on 2017-10-18
After running this in /var/lib/dpkg/info I'm still running into problems; it looks to be a sha256 mismatch, however I've even tried modifying your third sed command with the sha256sum that I have received to no avail. Getting the following error:

> As a temporary workaround I've patched installer:

```
sudo sed -i 's|JAVA_VERSION=8u144|JAVA_VERSION=8u152|' oracle-java8-installer.*
sudo sed -i 's|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u152-b16/aa0333dd3019491ca4f6ddbe78cdb6d0/|' oracle-java8-installer.*
sudo sed -i 's|SHA256SUM_TGZ="e8a341ce566f32c3d06f6d0f0eeea9a0f434f538d22af949ae58bc86f2eeaae4"|SHA256SUM_TGZ="218b3b340c3f6d05d940b817d0270dfe0cfd657a636bad074dcabe0c111961bf"|' oracle-java8-installer.*
sudo sed -i 's|J_DIR=jdk1.8.0_144|J_DIR=jdk1.8.0_152|' oracle-java8-installer.*
```


```
sha256sum mismatch jdk-8u152-linux-arm64-vfp-hflt.tar.gz
```[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]

---

### Post by rick-blacker on 2017-10-18
> **polentino911 said:**
> for anybody wondering from where those commands should be executed: 
```
cd [FONT=monospace][COLOR=#000000]/var/lib/dpkg/info[/COLOR][/FONT]
```
```

sudo sed -i 's|JAVA_VERSION=8u144|JAVA_VERSION=8u152|' oracle-java8-installer.*
sudo sed -i 's|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u152-b16/aa0333dd3019491ca4f6ddbe78cdb6d0/|' oracle-java8-installer.*
sudo sed -i 's|SHA256SUM_TGZ="e8a341ce566f32c3d06f6d0f0eeea9a0f434f538d22af949ae58bc86f2eeaae4"|SHA256SUM_TGZ="218b3b340c3f6d05d940b817d0270dfe0cfd657a636bad074dcabe0c111961bf"|' oracle-java8-installer.*
sudo sed -i 's|J_DIR=jdk1.8.0_144|J_DIR=jdk1.8.0_152|' oracle-java8-installer.*

```

I'm pretty new to the Linux world, scripting and all the Linux commands, so I may have missed something but... at the shell, I navigated into the directory specified.  I then executed each of those commands.  Now what do I do?  After running those commands one at a time, nothing happened. 

Don't laugh at me.  ;)

---

### Post by again? on 2017-10-18
Try to run the installer from webupd8 again.
```
sudo apt update 
sudo apt install oracle-java8-installer
```

---

### Post by rick-blacker on 2017-10-19
Thanks... It still failed though.

```

sudo apt install oracle-java8-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
oracle-java8-installer is already the newest version (8u144-1~webupd8~0).
0 upgraded, 0 newly installed, 0 to remove and 192 not upgraded.
6 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up oracle-java9-installer (9b181-1~webupd8~2) ...
Using wget settings from /var/cache/oracle-jdk9-installer/wgetrc
Downloading Oracle Java 9...
--2017-10-18 23:53:39--  http://download.oracle.com/otn-pub/java/jdk/9+181/jdk-9_linux-x64_bin.tar.gz
Resolving download.oracle.com (download.oracle.com)... 23.3.105.51, 23.3.105.48
Connecting to download.oracle.com (download.oracle.com)|23.3.105.51|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/9+181/jdk-9_linux-x64_bin.tar.gz [following]
--2017-10-18 23:53:40--  https://edelivery.oracle.com/otn-pub/java/jdk/9+181/jdk-9_linux-x64_bin.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 104.89.90.135, 2600:1407:21:28e::2d3e, 2600:1407:21:2ae::2d3e
Connecting to edelivery.oracle.com (edelivery.oracle.com)|104.89.90.135|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/otn-pub/java/jdk/9+181/jdk-9_linux-x64_bin.tar.gz?AuthParam=1508396140_aedbee60ca462de7916535b3ddf18d20 [following]
--2017-10-18 23:53:40--  http://download.oracle.com/otn-pub/java/jdk/9+181/jdk-9_linux-x64_bin.tar.gz?AuthParam=1508396140_aedbee60ca462de7916535b3ddf18d20
Connecting to download.oracle.com (download.oracle.com)|23.3.105.51|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2017-10-18 23:53:40 ERROR 404: Not Found.

download failed
Oracle JDK 9 is NOT installed.
dpkg: error processing package oracle-java9-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up oracle-java8-installer (8u144-1~webupd8~0) ...
Using wget settings from /var/cache/oracle-jdk8-installer/wgetrc
Downloading Oracle Java 8...
--2017-10-18 23:53:41--  http://download.oracle.com/otn-pub/java/jdk/8u152-b16/aa0333dd3019491ca4f6ddbe78cdb6d0/jdk-8u152-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 23.3.105.48, 23.3.105.51
Connecting to download.oracle.com (download.oracle.com)|23.3.105.48|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/8u152-b16/aa0333dd3019491ca4f6ddbe78cdb6d0/jdk-8u152-linux-x64.tar.gz [following]
--2017-10-18 23:53:41--  https://edelivery.oracle.com/otn-pub/java/jdk/8u152-b16/aa0333dd3019491ca4f6ddbe78cdb6d0/jdk-8u152-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 104.89.90.135, 2600:1407:21:28e::2d3e, 2600:1407:21:2ae::2d3e
Connecting to edelivery.oracle.com (edelivery.oracle.com)|104.89.90.135|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/otn-pub/java/jdk/8u152-b16/aa0333dd3019491ca4f6ddbe78cdb6d0/jdk-8u152-linux-x64.tar.gz?AuthParam=1508396141_77880196da04dab2712632e806339e2b [following]
--2017-10-18 23:53:41--  http://download.oracle.com/otn-pub/java/jdk/8u152-b16/aa0333dd3019491ca4f6ddbe78cdb6d0/jdk-8u152-linux-x64.tar.gz?AuthParam=1508396141_77880196da04dab2712632e806339e2b
Connecting to download.oracle.com (download.oracle.com)|23.3.105.48|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 189784266 (181M) [application/x-gzip]
Saving to: &#8216;jdk-8u152-linux-x64.tar.gz&#8217;

     0K ........ ........ ........ ........ ........ ........  1% 7.17M 25s
  3072K ........ ........ ........ ........ ........ ........  3% 3.27M 39s
  6144K ........ ........ ........ ........ ........ ........  4% 4.08M 40s
  9216K ........ ........ ........ ........ ........ ........  6% 3.64M 41s
 12288K ........ ........ ........ ........ ........ ........  8% 3.59M 41s
 15360K ........ ........ ........ ........ ........ ........  9% 3.65M 41s
 18432K ........ ........ ........ ........ ........ ........ 11% 2.46M 44s
 21504K ........ ........ ........ ........ ........ ........ 13% 6.67M 41s
 24576K ........ ........ ........ ........ ........ ........ 14% 3.65M 40s
 27648K ........ ........ ........ ........ ........ ........ 16% 3.70M 40s
 30720K ........ ........ ........ ........ ........ ........ 18% 3.59M 39s
 33792K ........ ........ ........ ........ ........ ........ 19% 3.65M 38s
 36864K ........ ........ ........ ........ ........ ........ 21% 3.64M 38s
 39936K ........ ........ ........ ........ ........ ........ 23% 3.58M 37s
 43008K ........ ........ ........ ........ ........ ........ 24% 3.63M 36s
 46080K ........ ........ ........ ........ ........ ........ 26% 3.65M 36s
 49152K ........ ........ ........ ........ ........ ........ 28% 3.59M 35s
 52224K ........ ........ ........ ........ ........ ........ 29% 3.60M 34s
 55296K ........ ........ ........ ........ ........ ........ 31% 2.66M 34s
 58368K ........ ........ ........ ........ ........ ........ 33% 4.25M 33s
 61440K ........ ........ ........ ........ ........ ........ 34% 3.56M 32s
 64512K ........ ........ ........ ........ ........ ........ 36% 3.72M 31s
 67584K ........ ........ ........ ........ ........ ........ 38% 3.59M 31s
 70656K ........ ........ ........ ........ ........ ........ 39% 3.61M 30s
 73728K ........ ........ ........ ........ ........ ........ 41% 3.61M 29s
 76800K ........ ........ ........ ........ ........ ........ 43% 3.63M 28s
 79872K ........ ........ ........ ........ ........ ........ 44% 3.63M 27s
 82944K ........ ........ ........ ........ ........ ........ 46% 3.62M 27s
 86016K ........ ........ ........ ........ ........ ........ 48% 2.90M 26s
 89088K ........ ........ ........ ........ ........ ........ 49% 4.88M 25s
 92160K ........ ........ ........ ........ ........ ........ 51% 2.36M 24s
 95232K ........ ........ ........ ........ ........ ........ 53% 7.78M 23s
 98304K ........ ........ ........ ........ ........ ........ 54% 3.56M 22s
101376K ........ ........ ........ ........ ........ ........ 56% 3.63M 22s
104448K ........ ........ ........ ........ ........ ........ 58% 3.60M 21s
107520K ........ ........ ........ ........ ........ ........ 59% 3.67M 20s
110592K ........ ........ ........ ........ ........ ........ 61% 3.47M 19s
113664K ........ ........ ........ ........ ........ ........ 62% 3.67M 18s
116736K ........ ........ ........ ........ ........ ........ 64% 3.77M 18s
119808K ........ ........ ........ ........ ........ ........ 66% 3.60M 17s
122880K ........ ........ ........ ........ ........ ........ 67% 3.62M 16s
125952K ........ ........ ........ ........ ........ ........ 69% 3.62M 15s
129024K ........ ........ ........ ........ ........ ........ 71% 3.61M 14s
132096K ........ ........ ........ ........ ........ ........ 72% 3.51M 13s
135168K ........ ........ ........ ........ ........ ........ 74% 3.76M 13s
138240K ........ ........ ........ ........ ........ ........ 76% 3.16M 12s
141312K ........ ........ ........ ........ ........ ........ 77% 4.21M 11s
144384K ........ ........ ........ ........ ........ ........ 79% 3.68M 10s
147456K ........ ........ ........ ........ ........ ........ 81% 3.49M 9s
150528K ........ ........ ........ ........ ........ ........ 82% 3.79M 9s
153600K ........ ........ ........ ........ ........ ........ 84% 2.26M 8s
156672K ........ ........ ........ ........ ........ ........ 86% 6.94M 7s
159744K ........ ........ ........ ........ ........ ........ 87% 3.65M 6s
162816K ........ ........ ........ ........ ........ ........ 89% 3.65M 5s
165888K ........ ........ ........ ........ ........ ........ 91% 3.61M 4s
168960K ........ ........ ........ ........ ........ ........ 92% 3.63M 4s
172032K ........ ........ ........ ........ ........ ........ 94% 3.56M 3s
175104K ........ ........ ........ ........ ........ ........ 96% 3.67M 2s
178176K ........ ........ ........ ........ ........ ........ 97% 3.65M 1s
181248K ........ ........ ........ ........ ........ ........ 99% 3.62M 0s
184320K ........ .......                                     100% 3.59M=50s

2017-10-18 23:54:31 (3.63 MB/s) - &#8216;jdk-8u152-linux-x64.tar.gz&#8217; saved [189784266/189784266]

Download done.
Removing outdated cached downloads...
update-alternatives: error: no alternatives for java
update-alternatives: using /usr/lib/jvm/java-8-oracle/jre/bin/ControlPanel to provide /usr/bin/ControlPanel (ControlPanel) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/jre/bin/java to provide /usr/bin/java (java) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/jre/bin/javaws to provide /usr/bin/javaws (javaws) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/jre/bin/jcontrol to provide /usr/bin/jcontrol (jcontrol) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/jre/bin/jjs to provide /usr/bin/jjs (jjs) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/jre/bin/keytool to provide /usr/bin/keytool (keytool) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/jre/bin/orbd to provide /usr/bin/orbd (orbd) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/jre/bin/pack200 to provide /usr/bin/pack200 (pack200) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/jre/bin/policytool to provide /usr/bin/policytool (policytool) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/jre/bin/rmid to provide /usr/bin/rmid (rmid) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/jre/bin/rmiregistry to provide /usr/bin/rmiregistry (rmiregistry) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/jre/bin/servertool to provide /usr/bin/servertool (servertool) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/jre/bin/tnameserv to provide /usr/bin/tnameserv (tnameserv) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/jre/bin/unpack200 to provide /usr/bin/unpack200 (unpack200) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/jre/lib/jexec to provide /usr/bin/jexec (jexec) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/appletviewer to provide /usr/bin/appletviewer (appletviewer) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/extcheck to provide /usr/bin/extcheck (extcheck) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/idlj to provide /usr/bin/idlj (idlj) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/jar to provide /usr/bin/jar (jar) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/jarsigner to provide /usr/bin/jarsigner (jarsigner) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/javac to provide /usr/bin/javac (javac) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/javadoc to provide /usr/bin/javadoc (javadoc) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/javafxpackager to provide /usr/bin/javafxpackager (javafxpackager) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/javah to provide /usr/bin/javah (javah) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/javap to provide /usr/bin/javap (javap) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/javapackager to provide /usr/bin/javapackager (javapackager) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/jcmd to provide /usr/bin/jcmd (jcmd) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/jconsole to provide /usr/bin/jconsole (jconsole) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/jdb to provide /usr/bin/jdb (jdb) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/jdeps to provide /usr/bin/jdeps (jdeps) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/jhat to provide /usr/bin/jhat (jhat) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/jinfo to provide /usr/bin/jinfo (jinfo) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/jmap to provide /usr/bin/jmap (jmap) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/jmc to provide /usr/bin/jmc (jmc) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/jps to provide /usr/bin/jps (jps) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/jrunscript to provide /usr/bin/jrunscript (jrunscript) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/jsadebugd to provide /usr/bin/jsadebugd (jsadebugd) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/jstack to provide /usr/bin/jstack (jstack) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/jstat to provide /usr/bin/jstat (jstat) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/jstatd to provide /usr/bin/jstatd (jstatd) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/jvisualvm to provide /usr/bin/jvisualvm (jvisualvm) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/native2ascii to provide /usr/bin/native2ascii (native2ascii) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/rmic to provide /usr/bin/rmic (rmic) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/schemagen to provide /usr/bin/schemagen (schemagen) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/serialver to provide /usr/bin/serialver (serialver) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/wsgen to provide /usr/bin/wsgen (wsgen) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/wsimport to provide /usr/bin/wsimport (wsimport) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/bin/xjc to provide /usr/bin/xjc (xjc) in auto mode
update-alternatives: using /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libnpjp2.so to provide /usr/lib/mozilla/plugins/libjavaplugin.so (mozilla-javaplugin.so) in auto mode
Oracle JDK 8 installed

#####Important########
To set Oracle JDK8 as default, install the "oracle-java8-set-default" package.
E.g.: sudo apt install oracle-java8-set-default
On Ubuntu systems, oracle-java8-set-default is most probably installed
automatically with this package.
######################

Setting up default-jre-headless (2:1.8-56ubuntu2) ...
Setting up default-jre (2:1.8-56ubuntu2) ...
Setting up default-jdk-headless (2:1.8-56ubuntu2) ...
Setting up default-jdk (2:1.8-56ubuntu2) ...
Errors were encountered while processing:
 oracle-java9-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by manuelaticudean on 2017-10-19
The workaround worked for me. Thank you!

---

### Post by g1zmo2 on 2017-10-19
@[[COLOR=#000000]rick-blacker[/COLOR]]("https://ubuntuforums.org/member.php?u=2040891")[COLOR=#000000] , [/COLOR]it seems oracle9 installer is failing and java8 is already installed

---

### Post by g1zmo2 on 2017-10-19
> **pizzapoindexter said:**
> After running this in /var/lib/dpkg/info I'm still running into problems; it looks to be a sha256 mismatch, however I've even tried modifying your third sed command with the sha256sum that I have received to no avail. Getting the following error:



```
sha256sum mismatch jdk-8u152-linux-arm64-vfp-hflt.tar.gz
```[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]

Ah, I forgot to mention that this commands works only for linux-x64 installer, it seems this sha256 value has to be updated to make installer work for amd64 ```

               SHA256SUM_TGZ="bbcf4a0805f9bcead32fd988b74cee61ef6ad90e6d1b4e0dce432ac3fd8e0168" #must be modified for each release

```

---

### Post by Mercus on 2017-10-19
The workaround works also for me, this is my ansible playbook with the fix

```

---


- name: Add Oracle Java webupd PPA
  apt_repository:
    repo: "ppa:webupd8team/java"


- name: Accept Java licence
  debconf:
    name: "oracle-java{{ java.version }}-installer"
    question: shared/accepted-oracle-license-v1-1
    vtype: select
    value: "true"


# - name: Install Oracle Java
#   apt:
#     name: "{{ item }}"
#     update_cache: yes
#     state: latest
#     force: yes
#   with_items:
#     - "oracle-java{{ java.version }}-installer"
#     - "oracle-java{{ java.version }}-set-default"


# Temporary fix for webupd8team installer issue
- name: Install Oracle Java
  block:
    - apt:
        name: "{{ item }}"
        update_cache: yes
        state: latest
        force: yes
      with_items:
        - "oracle-java{{ java.version }}-installer"
        - "oracle-java{{ java.version }}-set-default"
  rescue:
    - shell: cd /var/lib/dpkg/info && sudo sed -i 's|JAVA_VERSION=8u144|JAVA_VERSION=8u152|' oracle-java8-installer.*
    - shell: cd /var/lib/dpkg/info && sudo sed -i 's|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u152-b16/aa0333dd3019491ca4f6ddbe78cdb6d0/|' oracle-java8-installer.*
    - shell: cd /var/lib/dpkg/info && sudo sed -i 's|SHA256SUM_TGZ="e8a341ce566f32c3d06f6d0f0eeea9a0f434f538d22af949ae58bc86f2eeaae4"|SHA256SUM_TGZ="218b3b340c3f6d05d940b817d0270dfe0cfd657a636bad074dcabe0c111961bf"|' oracle-java8-installer.*
    - shell: cd /var/lib/dpkg/info && sudo sed -i 's|J_DIR=jdk1.8.0_144|J_DIR=jdk1.8.0_152|' oracle-java8-installer.*
  always:
    - apt:
        name: "{{ item }}"
      with_items:
        - "oracle-java{{ java.version }}-installer"
        - "oracle-java{{ java.version }}-set-default"

```

---

### Post by rick-blacker on 2017-10-19
> **g1zmo2 said:**
> @[[COLOR=#000000]rick-blacker[/COLOR]]("https://ubuntuforums.org/member.php?u=2040891")[COLOR=#000000] , [/COLOR]it seems oracle9 installer is failing and java8 is already installed

You're right, I didn't read it close enough.  This is good enough for now.  I don't need java9.  8 will do for now.  Thanks!

---

### Post by kerojo on 2017-10-19
> **g1zmo2 said:**
> As a temporary workaround I've patched installer:


```

sudo sed -i 's|JAVA_VERSION=8u144|JAVA_VERSION=8u152|' oracle-java8-installer.*
sudo sed -i 's|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u152-b16/aa0333dd3019491ca4f6ddbe78cdb6d0/|' oracle-java8-installer.*
sudo sed -i 's|SHA256SUM_TGZ="e8a341ce566f32c3d06f6d0f0eeea9a0f434f538d22af949ae58bc86f2eeaae4"|SHA256SUM_TGZ="218b3b340c3f6d05d940b817d0270dfe0cfd657a636bad074dcabe0c111961bf"|' oracle-java8-installer.*
sudo sed -i 's|J_DIR=jdk1.8.0_144|J_DIR=jdk1.8.0_152|' oracle-java8-installer.*

```

Just throwing in my tuppence, This worked for me!

Thanks.

+1

---

### Post by freakthegeek on 2017-10-19
The third command which g1zmo2 provided is specific to the x64 sum.

> **pizzapoindexter said:**
> 
```
sha256sum mismatch jdk-8u152-linux-arm64-vfp-hflt.tar.gz
```[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
Pizzapoindexter, it looks like you will need to change the arm64 checksum.

For you, and anyone else looking to use g1zmo2's patch, the sums to replace in the third command are:
i386: 624c090647629394ef0ee08d9d8ac5d3d5a9a60fa245fefb2eb417c36c7cb7c4
x64: e8a341ce566f32c3d06f6d0f0eeea9a0f434f538d22af949ae58bc86f2eeaae4
arm32: cbbd390e19ab4c473e05f60602ce2804db25e4e35be5ab95f4f1a2aeb5b72383
arm64: bbcf4a0805f9bcead32fd988b74cee61ef6ad90e6d1b4e0dce432ac3fd8e0168


To get my actual sum (arm32) I ran this in /var/cache/oracle-jdk8-installer
```
sha256sum jdk-8u152-linux-arm32-vfp-hflt.tar.gz
```
So my third command was:
```
sudo sed -i 's|SHA256SUM_TGZ="cbbd390e19ab4c473e05f60602ce2804db25e4e35be5ab95f4f1a2aeb5b72383"|SHA256SUM_TGZ="35ab532355c72310c4c7add2b7c7f9d1eb0e045cf59d3fd69ee08fa6a9e610f0"|' oracle-java8-installer.*
```

---

### Post by jplesko on 2017-10-20
So obviously everyone is facing this issue.  We appreciate the workaround.  Any idea how long an update will take?  My issue is that I am using vagrant images, which are built on the fly, and a manual workaround will not suffice.  Any info?

---

### Post by ville-turpeinen on 2017-10-20
This workaround worked for me, thanks!

Will updates still work automatically after this workaround, or do I have to install the fixed package again when it becomes officially available to the repository?

---

### Post by QIII on 2017-10-20
The info is this --

[webupd8]("http://www.webupd8.org/p/about.html") is one guy: Andrew.  Andrew is very meticulous and very busy.  He generously *volunteers* his time to provide a lot of very useful packages via his PPAs (Personal Package Archives, not "official repositories") and we all owe him some modicum of respect and gratitude.

I've contacted him a few times and he has been gracious and very quick to address issues.  I'm sure he is well aware of this one.  Just so you are all aware, the Java "package" from webupd8 is a group of scripts that automate the process of installing Java *from Oracle's website.*  Oracle does not allow anyone to host the actual binaries.  So if they do something -- for instance changing the urls even slightly -- Andrew's scripts will fail until he has the opportunity to update them.

Andrew has a real life like all the rest of us.  He may very well be taking a well-deserved vacation.  

You may rest assured that a fix will be available when he has time to provide it.  Please have a bit of patience and don't swamp him with questions about ETAs.  Give a hard-working fellow a break.

---

### Post by ville-turpeinen on 2017-10-20
Thanks for the info. I did not know that Oracle's Java is such a mess on Ubuntu Linux. Sounds like Oracle is not really caring to support Linux at all.

I would use OpenJDK, but a product that we use in our production servers officially supports only Oracle Java.

---

### Post by QIII on 2017-10-20
Oracle Java is not a mess on Ubuntu.  There is simply some minor and temporary issue in Andrew's PPA.  Since his PPA only automates the manual steps involved in installing Oracle Java, [Oracle Java can be installed manually]("https://sites.google.com/site/easylinuxtipsproject/java") for now.  The nice thing about webupd8 is that Andrew updates his work in such a way that you don't have to install manually every time Oracle puts out a new release.  You just do your normal updates.

If something you use depends specifically on Oracle Java, then something is amiss.  By Oracle's own decree, OpenJDK is the open source reference implementation for all things Java -- including Oracle Java.  The biggest contingent of developers of OpenJDK is composed of Oracle developers.  That is, if Oracle Java works, OpenJDK should.  If it doesn't, someone who is developing Java products is not aware of how that fits together and should not be designing things so that only Oracle Java works.  OpenJDK dictates how Oracle Java should work -- aside from some possibly proprietary OS-specific features.

---

### Post by ville-turpeinen on 2017-10-20
I appreciate Andrew's work, I did not mean to imply that what he does or does not do is a mess. But I find Oracle's lack of interest to host their Java in some public repository to be a mess. The way they officially want us to install and update Java is a mess. I think the situation that for us to have automated install and updates of Oracle Java is all depended on one's volunteer work and free time, is really a mess.

[SIZE=1]Offtopic: Software we use is third party, and their documentation strictly only mentions Oracle Java. I have succesfully ran in on OpenJDK, but in our production we simply can't take the risk that if something goes wrong, they might refuse to give us support that we are paying for.[/SIZE]

---

### Post by vandrade on 2017-10-20
I'm having the same problem when I try to create a container in docker.
here is an alternative alternative for those who need to install java in containers

```

[COLOR=#808080][I]# install java via wget site oficial oracle
[/I][/COLOR][COLOR=#808080][I]# note: JAVA_FILE_TAR, JAVA_URL_DOWNLOAD and JAVA_DIR  must be entered manually
[/I][/COLOR][COLOR=#000080]**ENV **[/COLOR][COLOR=#660e7a]***JAVA_FILE_TAR ***[/COLOR]jdk-8u151-linux-x64.tar.gz
[COLOR=#000080]**ENV **[/COLOR][COLOR=#660e7a]***JAVA_URL_DOWNLOAD ***[/COLOR][COLOR=#008000]**"http://download.oracle.com/otn-pub/java/jdk/8u151-b12/e758a0de34e24606bca991d704f6dcbf/**[/COLOR]${[COLOR=#660e7a]***JAVA_FILE_TAR***[/COLOR]}[COLOR=#008000][B]"
[/B][/COLOR][COLOR=#000080]**ENV **[/COLOR][COLOR=#660e7a]***JAVA_DIR ***[/COLOR]jdk1[COLOR=#0000ff].8.0[/COLOR]_151

[COLOR=#808080][I]# download and extract tar
[/I][/COLOR][COLOR=#000080]**RUN **[/COLOR]cd [COLOR=#000080]**/**[/COLOR]opt  [COLOR=#000080]**&& **[/COLOR]wget [COLOR=#000080]**-**[/COLOR]q [COLOR=#000080]**--**[/COLOR]no-check-certificate [COLOR=#000080]**-**[/COLOR]c [COLOR=#000080]**--**[/COLOR]header [COLOR=#008000]**"Cookie: oraclelicense=accept-securebackup-cookie" **[/COLOR]${[COLOR=#660e7a]***JAVA_URL_DOWNLOAD***[/COLOR]} \
  [COLOR=#000080]**&& **[/COLOR]tar zxvf ${[COLOR=#660e7a]***JAVA_FILE_TAR***[/COLOR]} [COLOR=#000080]**&& **[/COLOR]pwd [COLOR=#000080]**&& **[/COLOR]ls [COLOR=#000080]**-**[/COLOR]la \
[COLOR=#808080][I]   # set default java
  [/I][/COLOR][COLOR=#000080]**&& **[/COLOR]update-alternatives [COLOR=#000080]**--**[/COLOR]install [COLOR=#000080]**/**[/COLOR]usr[COLOR=#000080]**/**[/COLOR]bin[COLOR=#000080]**/**[/COLOR]java java [COLOR=#000080]**/**[/COLOR]opt[COLOR=#000080]**/**[/COLOR]${[COLOR=#660e7a]***JAVA_DIR***[/COLOR]}[COLOR=#000080]**/**[/COLOR]bin[COLOR=#000080]**/**[/COLOR]java [COLOR=#0000ff]1 [/COLOR]\
  [COLOR=#000080]**&& **[/COLOR]update-alternatives [COLOR=#000080]**--**[/COLOR]install [COLOR=#000080]**/**[/COLOR]usr[COLOR=#000080]**/**[/COLOR]bin[COLOR=#000080]**/**[/COLOR]javac javac [COLOR=#000080]**/**[/COLOR]opt[COLOR=#000080]**/**[/COLOR]${[COLOR=#660e7a]***JAVA_DIR***[/COLOR]}[COLOR=#000080]**/**[/COLOR]bin[COLOR=#000080]**/**[/COLOR]javac [COLOR=#0000ff]1 [/COLOR]\
  [COLOR=#000080]**&& **[/COLOR]update-alternatives [COLOR=#000080]**--**[/COLOR]install [COLOR=#000080]**/**[/COLOR]usr[COLOR=#000080]**/**[/COLOR]bin[COLOR=#000080]**/**[/COLOR]jar jar [COLOR=#000080]**/**[/COLOR]opt[COLOR=#000080]**/**[/COLOR]${[COLOR=#660e7a]***JAVA_DIR***[/COLOR]}[COLOR=#000080]**/**[/COLOR]bin[COLOR=#000080]**/**[/COLOR]jar [COLOR=#0000ff]1 [/COLOR]\
[COLOR=#808080][I]   # set temp env vars
  [/I][/COLOR][COLOR=#000080]**&& **[/COLOR]export JAVA_HOME=[COLOR=#000080]**/**[/COLOR]opt[COLOR=#000080]**/**[/COLOR]${[COLOR=#660e7a]***JAVA_DIR***[/COLOR]} \
  [COLOR=#000080]**&& **[/COLOR]export PATH=$[COLOR=#660e7a]***PATH***[/COLOR]:[COLOR=#000080]**/**[/COLOR]opt[COLOR=#000080]**/**[/COLOR]${[COLOR=#660e7a]***JAVA_DIR***[/COLOR]}[COLOR=#000080]**/**[/COLOR]bin:[COLOR=#000080]**/**[/COLOR]opt[COLOR=#000080]**/**[/COLOR]${[COLOR=#660e7a]***JAVA_DIR***[/COLOR]}[COLOR=#000080]**/**[/COLOR]jre[COLOR=#000080]**/**[/COLOR]bin \
  [COLOR=#000080]**&& **[/COLOR]echo [COLOR=#008000]**"export JAVA_HOME=/opt/**[/COLOR]${[COLOR=#660e7a]***JAVA_DIR***[/COLOR]}[COLOR=#008000]**" **[/COLOR][COLOR=#000080]**>> /**[/COLOR]etc[COLOR=#000080]**/**[/COLOR]environment \
  [COLOR=#000080]**&& **[/COLOR]echo [COLOR=#008000]**"export PATH=**[/COLOR]$[COLOR=#660e7a]***PATH***[/COLOR][COLOR=#008000]**:/opt/**[/COLOR]${[COLOR=#660e7a]***JAVA_DIR***[/COLOR]}[COLOR=#008000]**/bin:/opt/**[/COLOR]${[COLOR=#660e7a]***JAVA_DIR***[/COLOR]}[COLOR=#008000]**/jre/bin" **[/COLOR][COLOR=#000080]**>> /**[/COLOR]etc[COLOR=#000080]**/**[/COLOR]environment \
  [COLOR=#000080]**&& **[/COLOR]ls [COLOR=#000080]**/**[/COLOR]opt[COLOR=#000080]**/**[/COLOR]${[COLOR=#660e7a]***JAVA_DIR***[/COLOR]} [COLOR=#000080]**> /**[/COLOR]dev[COLOR=#000080]**/**[/COLOR]null [COLOR=#0000ff]2[/COLOR][COLOR=#000080]**>**[/COLOR]&[COLOR=#0000ff]1[/COLOR]
```


I hope it helps!

---

### Post by arifolth on 2017-10-20
> **g1zmo2 said:**
> As a temporary workaround I've patched installer:


```

sudo sed -i 's|JAVA_VERSION=8u144|JAVA_VERSION=8u152|' oracle-java8-installer.*
sudo sed -i  's|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u152-b16/aa0333dd3019491ca4f6ddbe78cdb6d0/|'  oracle-java8-installer.*
sudo sed -i  's|SHA256SUM_TGZ="e8a341ce566f32c3d06f6d0f0eeea9a0f434f538d22af949ae58bc86f2eeaae4"|SHA256SUM_TGZ="218b3b340c3f6d05d940b817d0270dfe0cfd657a636bad074dcabe0c111961bf"|'  oracle-java8-installer.*
sudo sed -i 's|J_DIR=jdk1.8.0_144|J_DIR=jdk1.8.0_152|' oracle-java8-installer.*

```

> **polentino911 said:**
> for anybody wondering from where those commands should be executed: 
```
cd [FONT=monospace][COLOR=#000000]/var/lib/dpkg/info[/COLOR][/FONT]
```

that did the trick for me, thanks

---

### Post by harry_i_c on 2017-10-20
The PPA has been updated within the last hour & is installing the latest version, for me that's Java 8u151.

---

### Post by shurato1982 on 2017-10-20
[QUOTE = harry_i_c; 13700489] O PPA foi atualizado na última hora e está instalando a versão mais recente, para mim, isso é Java 8u151. [/ QUOTE]

[COLOR=#212121][FONT=arial]
[/FONT][/COLOR][COLOR=#212121][FONT=arial]today? 20.10.2017?I'm trying to use the would ask for help with the commands with the error for me on ubuntu server 14.04, I'll try through the PPA one more time then ...[/FONT][/COLOR][COLOR=#212121][FONT=arial]Att[/FONT][/COLOR][COLOR=#212121][FONT=arial]today? 20.10.2017?I'm trying to use the would ask for help with the commands with the error for me on ubuntu server 14.04, I'll try through the PPA one more time then ...Att[/FONT][/COLOR]

---

### Post by shurato1982 on 2017-10-20
[COLOR=#212121][FONT=arial]today? 20.10.2017?[/FONT][/COLOR]
[COLOR=#212121][FONT=arial]I'm trying to use the would ask for help with the commands with the error for me on ubuntu server 14.04, I'll try through the PPA one more time then ...Att[/FONT][/COLOR]
[COLOR=#212121][FONT=arial]today? 20.10.2017?I'm trying to use the would ask for help with the commands with the error for me on ubuntu server 14.04, I'll try through the PPA one more time then ...Att[/FONT][/COLOR]

---

### Post by shurato1982 on 2017-10-20
[COLOR=#212121][FONT=arial]Fact !!![/FONT][/COLOR]
[COLOR=#212121][FONT=arial]Updated, thank you developer ... Thank you from Heart[/FONT][/COLOR]
[COLOR=#212121][FONT=arial]Fact !!!Updated, thank you developer ... Thank you from Heart[/FONT][/COLOR]

---

### Post by oldos2er on 2017-10-20
Please post in English, or in the appropriate [Loco team forum]("https://ubuntuforums.org/forumdisplay.php?f=183").

---

### Post by shurato1982 on 2017-10-20
> **oldos2er said:**
> Please post in English, or in the appropriate [Loco team forum]("https://ubuntuforums.org/forumdisplay.php?f=183").

Sorry Please....

---

### Post by p-ansell on 2018-01-16
> **g1zmo2 said:**
> As a temporary workaround I've patched installer:


```

sudo sed -i 's|JAVA_VERSION=8u144|JAVA_VERSION=8u152|' oracle-java8-installer.*
sudo sed -i 's|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u152-b16/aa0333dd3019491ca4f6ddbe78cdb6d0/|' oracle-java8-installer.*
sudo sed -i 's|SHA256SUM_TGZ="e8a341ce566f32c3d06f6d0f0eeea9a0f434f538d22af949ae58bc86f2eeaae4"|SHA256SUM_TGZ="218b3b340c3f6d05d940b817d0270dfe0cfd657a636bad074dcabe0c111961bf"|' oracle-java8-installer.*
sudo sed -i 's|J_DIR=jdk1.8.0_144|J_DIR=jdk1.8.0_152|' oracle-java8-installer.*

```

It happened again with Oracle removing the build 152 download files after releasing a new build. Here are the new checksums for build 162:

```

    cd /var/lib/dpkg/info
    sudo sed -i 's|JAVA_VERSION=8u151|JAVA_VERSION=8u162|' oracle-java8-installer.*
    sudo sed -i 's|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u151-b12/e758a0de34e24606bca991d704f6dcbf/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u162-b12/0da788060d494f5095bf8624735fa2f1/|' oracle-java8-installer.*
    sudo sed -i 's|SHA256SUM_TGZ="c78200ce409367b296ec39be4427f020e2c585470c4eed01021feada576f027f"|SHA256SUM_TGZ="68ec82d47fd9c2b8eb84225b6db398a72008285fafc98631b1ff8d2229680257"|' oracle-java8-installer.*
    sudo sed -i 's|J_DIR=jdk1.8.0_151|J_DIR=jdk1.8.0_162|' oracle-java8-installer.*

```

Note that webupd8 only went to 8u151 last time, not 8u152, and it is possible they will only go to 161 this time (security updates only, versus security and also bug fixes in 162).

---

### Post by rrwood on 2018-01-17
> **p-ansell said:**
> It happened again with Oracle removing the build 152 download files after releasing a new build. Here are the new checksums for build 162:

```

    cd /var/lib/dpkg/info
    sudo sed -i 's|JAVA_VERSION=8u151|JAVA_VERSION=8u162|' oracle-java8-installer.*
    sudo sed -i 's|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u151-b12/e758a0de34e24606bca991d704f6dcbf/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u162-b12/0da788060d494f5095bf8624735fa2f1/|' oracle-java8-installer.*
    sudo sed -i 's|SHA256SUM_TGZ="c78200ce409367b296ec39be4427f020e2c585470c4eed01021feada576f027f"|SHA256SUM_TGZ="68ec82d47fd9c2b8eb84225b6db398a72008285fafc98631b1ff8d2229680257"|' oracle-java8-installer.*
    sudo sed -i 's|J_DIR=jdk1.8.0_151|J_DIR=jdk1.8.0_162|' oracle-java8-installer.*

```

Note that webupd8 only went to 8u151 last time, not 8u152, and it is possible they will only go to 161 this time (security updates only, versus security and also bug fixes in 162).

Thanks, p-ansell!

As a note to others having this problem, don't forget that you have to do an "apt-get install oracle-java8-installer" before you run the sed commands, otherwise the dpkg files won't be there to patch...

---

### Post by cameronc56 on 2018-01-17
> **rrwood said:**
> Thanks, p-ansell!

As a note to others having this problem, don't forget that you have to do an "apt-get install oracle-java8-installer" before you run the sed commands, otherwise the dpkg files won't be there to patch...

So in my dockerfile with an ubuntu base image

I install oracle-java8-installer the first time (which fails but i do a || true):

```
RUN echo 'oracle-java8-installer shared/accepted-oracle-license-v1-1 boolean true' | debconf-set-selections && DEBIAN_FRONTEND=noninteractive apt-get -y install oracle-java8-installer || true
```

Then I run the ```
cd /var/lib/dpkg/info
``` and the 
```
RUN sed -i 's|JAVA_VERSION=8u151|JAVA_VERSION=8u162|' oracle-java8-installer.*
RUN sed -i 's|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u151-b12/e758a0de34e24606bca991d704f6dcbf/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u162-b12/0da788060d494f5095bf8624735fa2f1/|' oracle-java8-installer.*
RUN sed -i 's|SHA256SUM_TGZ="c78200ce409367b296ec39be4427f020e2c585470c4eed01021feada576f027f"|SHA256SUM_TGZ="68ec82d47fd9c2b8eb84225b6db398a72008285fafc98631b1ff8d2229680257"|' oracle-java8-installer.*
RUN sed -i 's|J_DIR=jdk1.8.0_151|J_DIR=jdk1.8.0_162|' oracle-java8-installer.*



``` commands

And then I install oracle-java8-installer again without ```
|| true
``` correct? Am i missing anything?

I am getting this error when running the sed commands above after installing it: 

```
Step 23/43 : RUN sed -i 's|JAVA_VERSION=8u151|JAVA_VERSION=8u162|' oracle-java8-installer.* ---> Running in 6869d66525ab
sed: can't read oracle-java8-installer.*: No such file or directory
The command '/bin/sh -c sed -i 's|JAVA_VERSION=8u151|JAVA_VERSION=8u162|' oracle-java8-installer.*' returned a non-zero code: 2

```

---

### Post by jbg91 on 2018-01-17
> **cameronc56 said:**
> So in my dockerfile with an ubuntu base image

I install oracle-java8-installer the first time (which fails but i do a || true):

```
RUN echo 'oracle-java8-installer shared/accepted-oracle-license-v1-1 boolean true' | debconf-set-selections && DEBIAN_FRONTEND=noninteractive apt-get -y install oracle-java8-installer || true
```

Then I run the ```
cd /var/lib/dpkg/info
``` and the 
```
RUN sed -i 's|JAVA_VERSION=8u151|JAVA_VERSION=8u162|' oracle-java8-installer.*
RUN sed -i 's|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u151-b12/e758a0de34e24606bca991d704f6dcbf/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u162-b12/0da788060d494f5095bf8624735fa2f1/|' oracle-java8-installer.*
RUN sed -i 's|SHA256SUM_TGZ="c78200ce409367b296ec39be4427f020e2c585470c4eed01021feada576f027f"|SHA256SUM_TGZ="68ec82d47fd9c2b8eb84225b6db398a72008285fafc98631b1ff8d2229680257"|' oracle-java8-installer.*
RUN sed -i 's|J_DIR=jdk1.8.0_151|J_DIR=jdk1.8.0_162|' oracle-java8-installer.*



``` commands

And then I install oracle-java8-installer again without ```
|| true
``` correct? Am i missing anything?

I am getting this error when running the sed commands above after installing it: 

```
Step 23/43 : RUN sed -i 's|JAVA_VERSION=8u151|JAVA_VERSION=8u162|' oracle-java8-installer.* ---> Running in 6869d66525ab
sed: can't read oracle-java8-installer.*: No such file or directory
The command '/bin/sh -c sed -i 's|JAVA_VERSION=8u151|JAVA_VERSION=8u162|' oracle-java8-installer.*' returned a non-zero code: 2

```

you should make only one RUN like

```

#java8
RUN sed 's/main$/main universe/' -i /etc/apt/sources.list \
 && apt-get update && apt-get install -y software-properties-common python-software-properties \
 && add-apt-repository ppa:webupd8team/java -y \
 && apt-get update \
 && apt-get install -y wget unzip \
 && echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections \
 && apt-get install -y oracle-java8-installer || true \
 && cd /var/lib/dpkg/info \
 && sed -i 's|JAVA_VERSION=8u151|JAVA_VERSION=8u162|' oracle-java8-installer.* \
 && sed -i 's|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u151-b12/e758a0de34e24606bca991d704f6dcbf/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u162-b12/0da788060d494f5095bf8624735fa2f1/|' oracle-java8-installer.* \
 && sed -i 's|SHA256SUM_TGZ="c78200ce409367b296ec39be4427f020e2c585470c4eed01021feada576f027f"|SHA256SUM_TGZ="68ec82d47fd9c2b8eb84225b6db398a72008285fafc98631b1ff8d2229680257"|' oracle-java8-installer.* \
 && sed -i 's|J_DIR=jdk1.8.0_151|J_DIR=jdk1.8.0_162|' oracle-java8-installer.* \
 && apt-get install -y oracle-java8-installer \
 && apt-get install -y oracle-java8-set-default

```

---

### Post by vtrang on 2018-01-18
Thanks 				 				 					 						 	[URL="https://ubuntuforums.org/member.php?u=2088127"][B][COLOR=#000000]jbg91.

[/COLOR][/B][COLOR=#000000][/COLOR][COLOR=#000000][/COLOR][/URL]I could down load now. But the error 
"sha256sum mismatch jdk-8u162-linux-i586.tar.gz" has occured. I've checked there is nothing wrong with sha256sum code eecf88dbcf7c78d236251d44350126f1297a522f2eab974b4027ef20f7a6fb24
That would be appriciated if you have any suggestion. Thanks in advance.

---

### Post by c4st0r0 on 2018-01-18
> **vtrang said:**
> Thanks                                                                                     [URL="https://ubuntuforums.org/member.php?u=2088127"][B][COLOR=#000000]jbg91.

[/COLOR][/B][/URL]I could down load now. But the error 
"sha256sum mismatch jdk-8u162-linux-i586.tar.gz" has occured. I've checked there is nothing wrong with sha256sum code eecf88dbcf7c78d236251d44350126f1297a522f2eab974b4027ef20f7a6fb24
That would be appriciated if you have any suggestion. Thanks in advance.

With the jbg91's code now I can download the java package but I'm having the same issue of vtrang...and java results not installed. Please, help.

---

### Post by sjwoodr on 2018-01-18
Luckily I had another box with 8u151 on it already and i just copied the /var/cache/oracle-jdk8-installer/* contents to the new box and then was able to install it.  If this were more than 2 boxes I was updating, it'd be a super pain.

---

### Post by kevinjcash on 2018-01-18
Is there any indication that this will be fixed in the WebUpd8 repo?

---

### Post by QIII on 2018-01-18
Andrei is a one-man-show now.  He will get it updated, but he's probably up to his armpits in alligators.

---

### Post by vtrang on 2018-01-18
I've used checksum with the file downloaded and strange that the sha256sum is completely correct. Not sure what happend here :/ but I think we have to wait to Andrei.

---

### Post by paulcb on 2018-01-20
+1 To get this working again. Rely on this for building Java docker images and our build process is blocked. [COLOR=#000000]Andrei please help :-)[/COLOR]

---

### Post by sbnwl on 2018-01-20
Andrei's contact is [email]andrew@webupd8.org[/email]

He is absent from [http://www.webupd8.org/](http://www.webupd8.org/) 
His last activity was on 25 August 2017...
I really hope he is well...

---

### Post by mkotlikov on 2018-01-21
jdk1.8.0_151 => jdk1.8.0_162 workaround for Ubuntu, tested on 16.04.

```

#!/bin/bash
set -e

add-apt-repository -y ppa:webupd8team/java
apt-get update
echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections

apt-get install -y oracle-java8-installer || true

#todo remove this kludge and the above || true when the ppa is fixed
cd /var/lib/dpkg/info
sed -i 's|JAVA_VERSION=8u151|JAVA_VERSION=8u162|' oracle-java8-installer.*
sed -i 's|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u151-b12/e758a0de34e24606bca991d704f6dcbf/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u162-b12/0da788060d494f5095bf8624735fa2f1/|' oracle-java8-installer.*
sed -i 's|SHA256SUM_TGZ="c78200ce409367b296ec39be4427f020e2c585470c4eed01021feada576f027f"|SHA256SUM_TGZ="68ec82d47fd9c2b8eb84225b6db398a72008285fafc98631b1ff8d2229680257"|' oracle-java8-installer.*
sed -i 's|J_DIR=jdk1.8.0_151|J_DIR=jdk1.8.0_162|' oracle-java8-installer.*
apt-get update

apt-get install -y oracle-java8-installer 

```

---

### Post by jeffdyke on 2018-04-17
Hola, its a been a while, but this happened to me today with 161, so the patch file for that to 172 is:

```

[COLOR=#c57633]*sudo *[/COLOR]sed -i [COLOR=#6a8759]'s|JAVA_VERSION=8u161|JAVA_VERSION=8u172|' [/COLOR]oracle-java8-installer.*
[COLOR=#c57633]*sudo *[/COLOR]sed -i [COLOR=#6a8759]'s|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u161-b12/2f38c3b165be4555a1fa6e98c45e0808/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u172-b11/a58eab1ec242421181065cdc37240b08/|' [/COLOR]oracle-java8-installer.*
[COLOR=#c57633]*sudo *[/COLOR]sed -i [COLOR=#6a8759]'s|SHA256SUM_TGZ="6dbc56a0e3310b69e91bb64db63a485bd7b6a8083f08e48047276380a0e2021e"|SHA256SUM_TGZ="28a00b9400b6913563553e09e8024c286b506d8523334c93ddec6c9ec7e9d346"|' [/COLOR]oracle-java8-installer.*
[COLOR=#c57633]*sudo *[/COLOR]sed -i [COLOR=#6a8759]'s|J_DIR=jdk1.8.0_161|J_DIR=jdk1.8.0_172|' [/COLOR]oracle-java8-installer.*

```

Hope this helps someone.  Thanks for the original post and suggestion.

---

### Post by zaflaucich on 2018-04-19
thanx man, you saved my day!

---

### Post by monkeybrain20122 on 2018-04-19
> **jeffdyke said:**
> Hola, its a been a while, but this happened to me today with 161, so the patch file for that to 172 is:

```

[COLOR=#c57633]*sudo *[/COLOR]sed -i [COLOR=#6a8759]'s|JAVA_VERSION=8u161|JAVA_VERSION=8u172|' [/COLOR]oracle-java8-installer.*
[COLOR=#c57633]*sudo *[/COLOR]sed -i [COLOR=#6a8759]'s|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u161-b12/2f38c3b165be4555a1fa6e98c45e0808/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u172-b11/a58eab1ec242421181065cdc37240b08/|' [/COLOR]oracle-java8-installer.*
[COLOR=#c57633]*sudo *[/COLOR]sed -i [COLOR=#6a8759]'s|SHA256SUM_TGZ="6dbc56a0e3310b69e91bb64db63a485bd7b6a8083f08e48047276380a0e2021e"|SHA256SUM_TGZ="28a00b9400b6913563553e09e8024c286b506d8523334c93ddec6c9ec7e9d346"|' [/COLOR]oracle-java8-installer.*
[COLOR=#c57633]*sudo *[/COLOR]sed -i [COLOR=#6a8759]'s|J_DIR=jdk1.8.0_161|J_DIR=jdk1.8.0_172|' [/COLOR]oracle-java8-installer.*

```

Hope this helps someone.  Thanks for the original post and suggestion.

172? webupd8 had an update just yesterday but it was from 161 to 171.

I did get error

I just uninstalled java-installer 161 and installed 171 then it all worked. (uninstall java-installer doesn't uninstall java)

---

### Post by baer+ on 2018-07-18
This is such a nightmare. Started happening with version 8u171. I managed to work around it by:

1. Downloading the latest 8u181 archive from Oracle, and putting it on a private S3 bucket
2. Modifying the installer to download the archive from S3

```

# generate sha256hash for the manually downloaded 8u181 archive
$ sha256  jdk-8u181-linux-x64.tar.gz
> 1845567095bfbfebd42ed0d09397939796d05456290fb20a83c476ba09f991d3

# upload the archive to S3, make sure it has the correct permissions so that the file can be downloaded
$ aws s3 cp jdk-8u181-linux-x64.tar.gz s3:.../jdk-8u181-linux-x64.tar.gz --grants read=uri=http://acs.amazonaws.com/groups/global/AllUsers full=emailaddress=

# fails with 404, but generates the package configs under /var/lib/dpkg/info/
$ sudo apt-get -y install oracle-java8-installer || true

# modify the package config
$ cd /var/lib/dpkg/info/
$ sudo sed -i 's|JAVA_VERSION=8u171|JAVA_VERSION=8u181|' oracle-java8-installer.*
$ sudo sed -i 's|SHA256SUM_TGZ=.*|SHA256SUM_TGZ="1845567095bfbfebd42ed0d09397939796d05456290fb20a83c476ba09f991d3"|' oracle-java8-installer.*
$ sudo sed -i 's|WGETRC.*|WGETRC=wgetrc wget --continue --no-check-certificate -O $FILENAME https://s3-us-west-2.amazonaws.com/<path-to-bucket>/jdk-8u181-linux-x64.tar.gz \\|' oracle-java8-installer.*
$ sudo sed -i 's|J_DIR=jdk1.8.0_171|J_DIR=jdk1.8.0_181|' oracle-java8-installer.*

# finally, install
$ sudo apt-get install -y oracle-java8-installer

```

Note that the Java archive should be removed from S3 because the license doesn't allow hosting it.

---

### Post by loade on 2018-07-18
Fix for ansible playbook:

```
- name: ORACLE JAVA | Install oracle java from ppa repository  
apt:
    pkg: "{{ item }}"
    update_cache: yes
    state: latest
    force: yes
  become: true
  become_user: root
  with_items:
    - "oracle-java{{ java_version }}-installer"
    - "oracle-java{{ java_version }}-set-default"
  ignore_errors: yes


- name: ORACLE JAVA | Fix oracle java
  shell: "{{ item }}"
  with_items:
    - cd /var/lib/dpkg/info && sed -i 's|JAVA_VERSION=8u171|JAVA_VERSION=8u181|' oracle-java8-installer.*
    - cd /var/lib/dpkg/info && sed -i 's|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u171-b11/512cd62ec5174c3487ac17c61aaa89e8/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u181-b13/96a7b8442fe848ef90c96a2fad6ed6d1/|' oracle-java8-installer.*
    - cd /var/lib/dpkg/info && sed -i 's|SHA256SUM_TGZ=.*|SHA256SUM_TGZ="1845567095bfbfebd42ed0d09397939796d05456290fb20a83c476ba09f991d3"|' oracle-java8-installer.*
    - cd /var/lib/dpkg/info && sed -i 's|J_DIR=jdk1.8.0_171|J_DIR=jdk1.8.0_181|' oracle-java8-installer.*
  become: true
  become_user: root


- name: ORACLE JAVA | Install oracle java from ppa repository
  apt:
    pkg: "{{ item }}"
    update_cache: yes
    state: latest
    force: yes
  become: true
  become_user: root
  with_items:
    - "oracle-java{{ java_version }}-installer"
    - "oracle-java{{ java_version }}-set-default"
```


Fix for bash:

```
apt-get install  oracle-java8-installer oracle-java8-set-default 

cd /var/lib/dpkg/info && sed -i 's|JAVA_VERSION=8u171|JAVA_VERSION=8u181|' oracle-java8-installer.*
sed -i 's|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u171-b11/512cd62ec5174c3487ac17c61aaa89e8/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u181-b13/96a7b8442fe848ef90c96a2fad6ed6d1/|' oracle-java8-installer.*
sed -i 's|SHA256SUM_TGZ=.*|SHA256SUM_TGZ="1845567095bfbfebd42ed0d09397939796d05456290fb20a83c476ba09f991d3"|' oracle-java8-installer.*
sed -i 's|J_DIR=jdk1.8.0_171|J_DIR=jdk1.8.0_181|' oracle-java8-installer.*

apt-get install -y oracle-java8-installer
```

---

### Post by chiefofthejojos on 2018-10-16
And now, for jdk-8u191-linux-x64.tar.gz:

```

[COLOR=#333333][FONT=&amp][COLOR=#2aa198]cd /var/lib/dpkg/info && [/COLOR][COLOR=#2AA198]sed -i 's|JAVA_VERSION=8u181|JAVA_VERSION=8u191|' oracle-java8-installer.*[/COLOR]
[COLOR=#2aa198]sed -i 's|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u181-b13/96a7b8442fe848ef90c96a2fad6ed6d1/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u191-b12/2787e4a523244c269598db4e85c51e0c/|' oracle-java8-installer.*[/COLOR]
[COLOR=#2aa198]sed -i 's|SHA256SUM_TGZ=.*|SHA256SUM_TGZ="53c29507e2405a7ffdbba627e6d64856089b094867479edc5ede4105c1da0d65"|' oracle-java8-installer.*[/COLOR]
[COLOR=#2aa198]sed -i 's|J_DIR=jdk1.8.0_181|J_DIR=jdk1.8.0_191|' oracle-java8-installer.*[/COLOR][/FONT][/COLOR]

```

Surely there must be a better way than to keep updating this manually. Maybe we could curl and parse the needed values from the download page?

---

### Post by Silent Ninja on 2018-10-17
Thanks @chiefofthejojos

I'm having issues with this since I use ansible to install Java8, and every time this changes, the ansible playbook fails, and thus the setup breaks

---

### Post by monkeybrain20122 on 2018-10-17
> **chiefofthejojos said:**
> And now, for jdk-8u191-linux-x64.tar.gz:

```

[COLOR=#333333][FONT=&amp][COLOR=#2aa198]cd /var/lib/dpkg/info && [/COLOR][COLOR=#2AA198]sed -i 's|JAVA_VERSION=8u181|JAVA_VERSION=8u191|' oracle-java8-installer.*[/COLOR]
[COLOR=#2aa198]sed -i 's|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u181-b13/96a7b8442fe848ef90c96a2fad6ed6d1/|PARTNER_URL=http://download.oracle.com/otn-pub/java/jdk/8u191-b12/2787e4a523244c269598db4e85c51e0c/|' oracle-java8-installer.*[/COLOR]
[COLOR=#2aa198]sed -i 's|SHA256SUM_TGZ=.*|SHA256SUM_TGZ="53c29507e2405a7ffdbba627e6d64856089b094867479edc5ede4105c1da0d65"|' oracle-java8-installer.*[/COLOR]
[COLOR=#2aa198]sed -i 's|J_DIR=jdk1.8.0_181|J_DIR=jdk1.8.0_191|' oracle-java8-installer.*[/COLOR][/FONT][/COLOR]

```

Surely there must be a better way than to keep updating this manually. Maybe we could curl and parse the needed values from the download page?

Not sure what you guys are talking about. Just upgraded with webupd8 with no problem at all, this is an old thread and the problem has been fixed  long times ago. 

P.S Incidentally not even see a need for Oracle's java, but it was installed a while back since there was a bug in openjdk which has been fixed.

---

### Post by jvalerio on 2018-10-17
I am also having this same issue as of today.. So it may have been a fixed issue, but it's back.

---

### Post by amarco2 on 2018-10-22
Hi,

I have generated my own script for installing java on beaglebone, and updated the sha keys and other stuff for several versions.

Not a very good script, but I think it may be helpful to others in similar situation than me

```

#!/bin/bash
#
# Cogido de https://ubuntuforums.org/showthread.php?t=2374686&page=5&

## JDK 151
PARTNER_URL_8u151=http://download.oracle.com/otn-pub/java/jdk/8u151-b12/e758a0de34e24606bca991d704f6dcbf/
#jdk-8u151-linux-arm32-vfp-hflt.tar.gz  
SHA256SUM_TGZ_8u151_arm32='"2cca3c6ffcc016ae531802202562ef20630500e134838017a6e91daac2dbb339"'
#jdk-8u151-linux-arm64-vfp-hflt.tar.gz
SHA256SUM_TGZ_8u151_arm64='"418631095498193b0918b2c86370b8fdad60abf7bf8f7e60498a5f2999106af7"'
#jdk-8u151-linux-i586.tar.gz
SHA256SUM_TGZ_8u151_i586='"8062f34f69dd1f1991bff517df52da606c53f5fa0d6677ceb46df30e93b53a70"'
#jdk-8u151-linux-x64.tar.gz
SHA256SUM_TGZ_8u151_x64='"c78200ce409367b296ec39be4427f020e2c585470c4eed01021feada576f027f"'

## JDK 161
PARTNER_URL_8u161=http://download.oracle.com/otn-pub/java/jdk/8u161-b12/2f38c3b165be4555a1fa6e98c45e0808/
#jdk-8u161-linux-arm32-vfp-hflt.tar.gz  
SHA256SUM_TGZ_8u161_arm32='"fd2881e01be04e52a7389e8458c794b0580997df4d1142eefb707468a9e0cf56"'
#jdk-8u161-linux-arm64-vfp-hflt.tar.gz
SHA256SUM_TGZ_8u161_arm64='"c7431d00a1d91dd413f4a6c5f94bf64df17d09a6369791589117767fbc7585a2"'
#jdk-8u161-linux-i586.tar.gz
SHA256SUM_TGZ_8u161_i586='"cf69617a74cccb262f06f7948f38e1c004d2663801e7724e7a7a0dabeb48d7dc"'
#jdk-8u161-linux-x64.tar.gz
SHA256SUM_TGZ_8u161_x64='"6dbc56a0e3310b69e91bb64db63a485bd7b6a8083f08e48047276380a0e2021e"'

## JDK 162
PARTNER_URL_8u162=http://download.oracle.com/otn-pub/java/jdk/8u162-b12/0da788060d494f5095bf8624735fa2f1/
#jdk-8u162-linux-arm32-vfp-hflt.tar.gz  
SHA256SUM_TGZ_8u162_arm32='"57720cc98e0dd709e8439df73d70cd1252d76f059e3e08ce0b36e8776b7bfa77"'
#jdk-8u162-linux-arm64-vfp-hflt.tar.gz
SHA256SUM_TGZ_8u162_arm64='"c84d7d32f1292b9d6b645ee286903b1b2d6881897e734c056efab8b9ab66d3a7"'
#jdk-8u162-linux-i586.tar.gz
SHA256SUM_TGZ_8u162_i586='"eecf88dbcf7c78d236251d44350126f1297a522f2eab974b4027ef20f7a6fb24"'
#jdk-8u162-linux-x64.tar.gz
SHA256SUM_TGZ_8u162_x64='"68ec82d47fd9c2b8eb84225b6db398a72008285fafc98631b1ff8d2229680257"'

## JDK 191
PARTNER_URL_8u191=http://download.oracle.com/otn-pub/java/jdk/8u191-b12/2787e4a523244c269598db4e85c51e0c
#jdk-8u191-linux-arm32-vfp-hflt.tar.gz  
SHA256SUM_TGZ_8u191_arm32='"1b9c57eed403b1299b10c529b16b7ef7f9a62d75cc9a8b0bf3827d1b55caed71"'
#jdk-8u191-linux-arm64-vfp-hflt.tar.gz
SHA256SUM_TGZ_8u191_arm64='"1f4f655e2d2d1d4263671a3fd81c9d3354613c499de43dfbc292cd982270fce5"'
#jdk-8u191-linux-i586.tar.gz
SHA256SUM_TGZ_8u191_i586='"640333e749f24428b78c2b10422f7174f8fbd0b8acde27526c195024fad8b6b6"'
#jdk-8u191-linux-x64.tar.gz
SHA256SUM_TGZ_8u191_x64='"53c29507e2405a7ffdbba627e6d64856089b094867479edc5ede4105c1da0d65"'

## JDK 192
PARTNER_URL_8u192=http://download.oracle.com/otn-pub/java/jdk/8u192-b12/750e1c8617c5452694857ad95c3ee230/
#jdk-8u192-linux-arm32-vfp-hflt.tar.gz  
SHA256SUM_TGZ_8u192_arm32='"e8de2beec5e15631e4d87351eeb660e186d283cf359a52cec5c9c677db70e43b"'
#jdk-8u192-linux-arm64-vfp-hflt.tar.gz
SHA256SUM_TGZ_8u192_arm64='"b63c84b243bcc3f8e889c104f0dfdfd96af893cc50c190e9b5045837531aa6e0"'
#jdk-8u192-linux-i586.tar.gz
SHA256SUM_TGZ_8u192_i586='"1be1d7669a36f96d90a0856ab1973dedc632bfdfdf27ccb1c2232608b73e26ce"'
#jdk-8u192-linux-x64.tar.gz
SHA256SUM_TGZ_8u192_x64='"6d34ae147fc5564c07b913b467de1411c795e290356538f22502f28b76a323c2"'


JAVA_VERSION_LATEST=8u192
PARTNER_URL_LATEST=$PARTNER_URL_8u192
SHA256SUM_TGZ_LATEST_arm32=$SHA256SUM_TGZ_8u192_arm32
SHA256SUM_TGZ_LATEST_arm64=$SHA256SUM_TGZ_8u192_arm64
SHA256SUM_TGZ_LATEST_i586=$SHA256SUM_TGZ_8u192_i586
SHA256SUM_TGZ_LATEST_x64=$SHA256SUM_TGZ_8u192_x64
J_DIR_LATEST=jdk1.8.0_192

set -e

# add-apt-repository -y ppa:webupd8team/java
sudo apt-get update
sudo echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections

sudo apt-get install -y oracle-java8-installer || true

#todo remove this kludge and the above || true when the ppa is fixed
cd /var/lib/dpkg/info

# this can be set by inspecting JAVA_VERSION on oracle-java8-installer.config, but don't know how...
JAVA_VERSION_CURRENT=8u161
PARTNER_URL_CURRENT=$PARTNER_URL_8u161
SHA256SUM_TGZ_CURRENT_arm32=$SHA256SUM_TGZ_8u161_arm32
SHA256SUM_TGZ_CURRENT_arm64=$SHA256SUM_TGZ_8u161_arm64
SHA256SUM_TGZ_CURRENT_i586=$SHA256SUM_TGZ_8u161_i586
SHA256SUM_TGZ_CURRENT_x64=$SHA256SUM_TGZ_8u161_x64
J_DIR_CURRENT=jdk1.8.0_161

sudo sed -i "s|JAVA_VERSION=$JAVA_VERSION_CURRENT|JAVA_VERSION=$JAVA_VERSION_LATEST|" oracle-java8-installer.*
sudo sed -i "s|PARTNER_URL=$PARTNER_URL_CURRENT|PARTNER_URL=$PARTNER_URL_LATEST|" oracle-java8-installer.*
sudo sed -i "s|SHA256SUM_TGZ=$SHA256SUM_TGZ_CURRENT_arm32|SHA256SUM_TGZ=$SHA256SUM_TGZ_LATEST_arm32|" oracle-java8-installer.*
sudo sed -i "s|SHA256SUM_TGZ=$SHA256SUM_TGZ_CURRENT_arm64|SHA256SUM_TGZ=$SHA256SUM_TGZ_LATEST_arm64|" oracle-java8-installer.*
sudo sed -i "s|SHA256SUM_TGZ=$SHA256SUM_TGZ_CURRENT_i586|SHA256SUM_TGZ=$SHA256SUM_TGZ_LATEST_i586|" oracle-java8-installer.*
sudo sed -i "s|SHA256SUM_TGZ=$SHA256SUM_TGZ_CURRENT_x64|SHA256SUM_TGZ=$SHA256SUM_TGZ_LATEST_x64|" oracle-java8-installer.*
sudo sed -i "s|J_DIR=$J_DIR_CURRENT|J_DIR=$J_DIR_LATEST|" oracle-java8-installer.*

sudo apt-get update

sudo apt-get install -y oracle-java8-installer



```
Regards,
Alvaro

---

