---
title: "No website or youtube video"
date: 2014-04-05
forum: General Help
---

### Post by gilloz on 2014-04-05
I have two desktop computers with Ubuntu 12.04 LTS installed.  My newer computer(built 2010) works fine for youtube and website(pages) videos.  My older computer(2004) works with everything but videos on youtube and websites(pages).  My newer computer is dual boot with Windows 7 64 Bit and Ubuntu 12.04.  My old computer just got rid of Windows XP and did a fresh install of Ubuntu 12.04 with alternate CD.  No dual boot.  I have tried every suggestion I could find on this forum to make videos function in YouTube and websites or pages, but I am unable to make it work.  I've done a comparison of files, plug-ins and settings between the both computers and they appear to be identical.  Any suggestions as to what else I can check to make my old computer function on YouTube videos and videos on webpages or websites?  Any help would certainly be appreciated.  Thanks

---

### Post by Impavidus on 2014-04-05
Can you describe the hardware? I'm not sure, but the latest (last) flash seems to need some hardware features not present on every 10 year old CPU, so if you could tell us which processor is in that old computer it may help.

---

### Post by ajgreeny on 2014-04-05
Let's see the output of ```
cat /proc/cpuinfo | grep sse2
``` If there is any output it means your cpu is enabled for sse2, which is essential for the latest versions of flashplayer; if there is no output youwill not be able to use flashplayer 11.2.202.346, which is the version available from the repos.

There are workarounds for this by using an earlier flash version but let's see what that command says first.

---

### Post by gilloz on 2014-04-05
Thanks Impavidus and ajgreeny for your responses.  The CPU in my old computer is an AMD Athlon XP 2100+266 FSB Palamino, Socket A on a SOYO SYK7V Dragon Plus Mobo with 2GB PC2100 DIMM RAM.  I built it in 2001 or so.  ajgreeny, entering your Terminal code, (cat /proc/cpuinfo | grep sse2) gives me no data at all.  That doesn't look good.  I will wait for your responses.  Thanks again.

---

### Post by monkeybrain20122 on 2014-04-05
I don't recommend using old versions of flash they are  a source of security vulnerability.

For Youtube and some other popular flash video sites you can use Viewtube. [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)
Install the greasemonkey addon for Firefox, restart Firefox, then go to the above link and click "install", you should be able to play vidoes for Youtube and supported sites in Totem/vlc/mplayer (Totem is installed by default, for the other options you need to install the vlc mozilla plugin and gecko-mediaplayer from the repo) 

I would recommend Viewtube even if you could play flash as flash is heavy on cpu and it doesn't work well for old hardware.

There are also stand alone Youtube players:
1) smtube
[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)
2) minitube
Type minitube-ubuntu in the Software centre. There is another 'minitube' in the repo, it is an old version and doesn't work.

---

### Post by Larry_Klein on 2014-04-05
for youtube - there is an extention that converts to html5.

otherwise - see this 

[http://ubuntuforums.org/showthread.php?t=2215258](http://ubuntuforums.org/showthread.php?t=2215258)

---

### Post by monkeybrain20122 on 2014-04-05
> **Larry_Klein said:**
> for youtube - there is an extention that converts to html5.

otherwise - see this 

[http://ubuntuforums.org/showthread.php?t=2215258](http://ubuntuforums.org/showthread.php?t=2215258)

Except that html5 is not easy on cpu either. So I doubt that it would work too well in this instance (On Firefox html5 doesn't hardware accelerate, on Chrome it may but not for such an old machine.)

---

### Post by edcompsci on 2014-04-06
If it is a flash swf problem have you tried the hal fix?

```

rm -rf ~/.adobe
sudo rm -rf /etc/hal/fdi/preprobe
sudo rm -rf /etc/hal/fdi/information
sudo apt-get purge hal libhal1 flashplugin-installer adobe-flashplugin 
bleachbit (remove everything flash and firefox, chromium)
sudo apt-get install adobe-flashplugin hal libhal1
sudo mkdir /etc/hal/fdi/preprobe
sudo mkdir /etc/hal/fdi/information
/usr/sbin/hald --daemon=yes --verbose=yes
rm -rf ~/.adobe
sudo apt-get purge flashplugin-installer adobe-flashplugin

```

Then download the newest tarball for flash for linux from the adobe site and extract the usr folder to the /usr folder, and the .so file to /usr/lib/firefox/add-ons/plugins

---

### Post by monkeybrain20122 on 2014-04-06
> **edcompsci said:**
> If it is a flash swf problem have you tried the hal fix?

```

rm -rf ~/.adobe
sudo rm -rf /etc/hal/fdi/preprobe
sudo rm -rf /etc/hal/fdi/information
sudo apt-get purge hal libhal1 flashplugin-installer adobe-flashplugin 
bleachbit (remove everything flash and firefox, chromium)
sudo apt-get install adobe-flashplugin hal libhal1
sudo mkdir /etc/hal/fdi/preprobe
sudo mkdir /etc/hal/fdi/information
/usr/sbin/hald --daemon=yes --verbose=yes
rm -rf ~/.adobe
sudo apt-get purge flashplugin-installer adobe-flashplugin

```

Then download the newest tarball for flash for linux from the adobe site and extract the usr folder to the /usr folder, and the .so file to /usr/lib/firefox/add-ons/plugins

Hal has nothing to do with OP's problem, It is used to enable Linux flash to play drm protetcted contents (usually paid streaming services like Amazon videos)but Youtube is not drm protected.

---

### Post by tripp98 on 2014-04-06
Have you install ubuntu-restricted-extras?

Otherwise install chrome/chromium which has flash installed with it.

---

### Post by Yellow Pasque on 2014-04-06
> **tripp98 said:**
> Have you install ubuntu-restricted-extras?
Otherwise install chrome/chromium which has flash installed with it.

Those won't work without SSE2.

---

