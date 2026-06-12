---
title: "&quot;Error Exit Status 2&quot;  on trying to remove Libre Office base"
date: 2014-08-27
forum: General Help
---

### Post by Richard_York on 2014-08-27
I have Ubuntu 12.04 LTS, 2.0 GiB Memory, Processor AMD Athlon(tm) 64 X2  Dual Core Processor 5200+ × 2 , 32-bit OS and 155.3 GB on Disk.

I'm advised I need to upgrade to 14.04 LTS to resolve issues with graphics card involving Libre Office, which I originally installed from Libre Office's own site rather than the onboard Ubuntu version. 
Using Synaptic Package Manager I've removed most LibreOffice elements prior to this, again following advice, to give a clear run for the upgrade. 
 - All except LibreOffice base. Here I get the message:

"E: libreoffice-base: subprocess installed post-removal script returned error exit status 2"

When I looked at the Install Upgrade to 14.04 button on the Update Manager it tells me to use sudo apt-get install -f in a terminal first.
This results in the following:


[sudo] password for richard: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclucene-contribs1 libcolamd2.7.1 lp-solve libexttextcat-2.0-0
  libclucene-core1 libexttextcat-data libhyphen0 libatk-wrapper-java
  java-common libvisio-0.0-0 icedtea-6-jre-cacao libmspub-0.0-0 libgraphite2-3
  libboost-date-time1.46.1 libcmis-0.3-3 libmythes-1.2-0 default-jre
  icedtea-netx-common ttf-sil-gentium-basic openjdk-6-jre-headless tzdata-java
  libcdr-0.0-0 openjdk-6-jre icedtea-netx icedtea-6-jre-jamvm
  openjdk-6-jre-lib nvidia-settings-304 libwps-0.2-2 libjpeg62 libhsqldb-java
  libservlet2.5-java liblangtag1 xfonts-mathml default-jre-headless
  ca-certificates-java liborcus-0.6-0 libatk-wrapper-java-jni
  liblangtag-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  libreoffice-base
0 to upgrade, 0 to newly install, 1 to remove and 4 not to upgrade.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
richard@richard-GA-MA790X-UD4:~$ 


I seem to be going in circles here, and don't understand most of them! I don't know what to do to remove Libreoffice Base, which is apparently the source of my problems, and it won't let me upgrade over it until I've removed it.
Any help to get me out of this circle, remove the broken bits, and install the upgrade will be really appreciated, please. Thanks in advance.uninstall

---

### Post by Richard_York on 2014-08-28
After sleeping on it, I restarted the computer today & got Synaptic Manager to remove all elements of Skype, which was also broken. The update manager then allowed me a "partial update", then agreed to install the Hardware Support package. Result, I'm still on 12.04 at present, and it seems to be all working again.
So it's solved in a way.
Related question: at the time of writing over 170 have viewed my question, but no answers. I'd appreciate someone telling me, preferably politely :-) what I did wrong in wording it, that got no responses. I am seriously not a geek, just a computer user glad to be away from Windows, so realise I probably ask the wrong questions!
Thanks.

---

### Post by ibjsb4 on 2014-08-28
> 170 have viewed my question, but no answers.
Libre Office is a popular subject.  To get that many hits in a short time span, tells me people are googling the WWW looking for answers to their own problems and hit on you.  So out of all those hits, probably only a few are actually people from the forum.

Why do you think 14o4 will help with your video glitch?

---

### Post by Richard_York on 2014-08-29
Thanks! When I first installed 12.04 I imported a different version of Libre Office from the default version, because that was older than the version I'd already been using on Windows. I'm told by a friendly adviser off-line that this may have created conflicts with my elderly graphics card. I don't know why. I honestly can't pretend to understand most of what I do, certainly not when it comes to making adjustments to things, so I'm dangerous to a computer OS!   But it seemed that the complete reformat and start again would give me the best chance, would be something I could succeed at, and at the same time it was worth updating to the newer Ubuntu version.
Additionally, when I came to look at it, Libre Office wasn't working even though Skype now was.
Since that last post I've done the clean reinstall, and so far Libre Office appears to work fine. I haven't yet reinstalled Skype, and at present am too busily worrying over how to get the printer to work again!
You will realise there are too many un-knowns all happening at once here :-)

---

