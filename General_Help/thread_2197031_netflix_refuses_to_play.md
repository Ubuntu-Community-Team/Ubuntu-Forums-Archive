---
title: "netflix refuses to play"
date: 2014-01-01
forum: General Help
---

### Post by choochoousmc on 2014-01-01
Netflix refuses to play movies.  Says I got to have windows or chrome or latest version firefox
Ok why will netflix not run on Ubuntu 13.04  with latest firefox?
Ok I did a search and found others same problem but no fix.
 So is thisa netflix problem not wanting us to use Linux or is this a Linux (ubuntu)  dailure to code for Netflix.
If Ubuntu, then come on guys get with it. Get us hooked up with netflix and all the others.

My windows computer crashed once again and the factory install disks refuse to work............so what's new there?

                                    **Complete System Requirements**

             To watch instantly, you''ll need a computer that meets the following minimum requirements:
             
[LIST]
[*]Windows
[LIST]
[*]Windows Vista or Windows 7 
[*]Internet Explorer 8 or higher; or the latest version of Firefox; or the latest version of Chrome 
[*]1.2 GHz processor 
[*]512 MB RAM 
[/LIST]
  
[*]Mac
[LIST]
[*]An Intel-based Mac with OS 10.4.11 or later 
[*]Safari 4 or higher; or the latest version of Firefox; or the latest version of Chrome 
[*]1 GB RAM 
[/LIST]
  
[*]Chrome OS
[LIST]
[*]A Google Chromebook or Chromebox running Chrome OS 29 or higher 
[/LIST]
                  
[/LIST]
                          [Watch instantly home page >]("http://movies.netflix.com/WiHome")

---

### Post by QIII on 2014-01-01
It won't work because Netflix refuses to support Linux.  The question of why is one to direct at Netflix.

webud8.org has a straightforward method for installing the compholio packages, pipelight, etc., that should enable the use of Netflix and other content.

[http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)

---

### Post by David D. on 2014-01-01
The problem is that playing Netflix requires Microsoft Silverlight to run.  The same is true for the On-Demand videos from many cable/ISP providers.  Silverlight is not directly able to run under Ubuntu (and Linux in general) due to a number of issues, including DRM.  There is a work around that uses WINE.  The thread below discusses this a contains a link for installing Pipelight and being able to run Netflix.

[http://ubuntuforums.org/showthread.php?t=2194449]("http://ubuntuforums.org/showthread.php?t=2194449")

---

### Post by choochoousmc on 2014-01-01
yea I just found that out. Finally got through to them.
They claim silverlight is more secure than Linux. hahahahah not!
Claim they are working on a plugin that will work with any OS.
Don't hold your breath waiting. They're in bed with bill gates.
So does HULU or any other streaming service work with Linux 
besides youtube?
I live in the sticks no regular TV and dish is too expensive.
Got an android tablet that I want to wirelessly connect to TV.
But chrome is hardwired to only certain sites that signed a contract with google.
just like gate's windows and pc makers. Sign the contract or you don't get license.
thanks for the replies and the info links.
Maybe someday these know it all ceo's will wake up and reaize they are missing out 
on 20,000,000 potential customers.

---

### Post by oldos2er on 2014-01-01
Hulu works just fine for me.

---

### Post by ldra02 on 2014-02-01
Try following these instructions:

[http://www.techrepublic.com/blog/linux-and-open-source/how-to-get-netflix-streaming-on-ubuntu-1210/4019/#.](http://www.techrepublic.com/blog/linux-and-open-source/how-to-get-netflix-streaming-on-ubuntu-1210/4019/#.)

Be sure to pay attention to the part after you open the netflix desktop, where wine asks you about installing some additional components.  If you don't do this it won't work.

I have an older machine, and though the picture is slightly grainy, the playback is good enough.

---

### Post by rburkartjo on 2014-02-05
you might want to try this link. this i how i installed netflix in wine. works great it installed in the sound and video folder.

[http://www.ubuntugeek.com/install-netflix-in-ubuntu-13-1013-04-using-ppa.html](http://www.ubuntugeek.com/install-netflix-in-ubuntu-13-1013-04-using-ppa.html)

---

### Post by monkeybrain20122 on 2014-02-05
Forget about the netflix-desktop, it is outdated. Use pipelight in  a native Linux browser. It is by the same developers.

[http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)

Also need an user agent switcher on the browser. For Firefox using the user agent overrider with setting Firefox 24/Windows would work on Netflix.[https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/)

---

### Post by ezykatch2000 on 2014-02-05
I run Windows XP in Virtual Box, then no problems w watching Netflix using Firefox or IE

---

### Post by monkeybrain20122 on 2014-02-08
> **ezykatch2000 said:**
> I run Windows XP in Virtual Box, then no problems w watching Netflix using Firefox or IE

Yeah so you are running Windows, now that isn't really a solution, is it? :)

---

### Post by jonathan-l-harrison on 2014-02-16
OK
This is what I did from some searching.  I now see it is all standard stuff, but if it helps:
PS....  None of this is my work, and I take no credit for it.... works fine on all the machines i have including self builds.

Install Netflix on Ubuntu:
Here is how to install the Netflix Desktop App on Ubuntu. Open a terminal and run these commands:
```
sudo apt-add-repository ppa:ehoover/compholio
sudo apt-get update && sudo apt-get install netflix-desktop
```

Once installed, go up to the top left of your screen and open your Unity dash and search for Netflix and run the app. It will load up everything needed on the first run. After logging into your Netflix account and selecting a video to play, Silverlight should ask you to enable DRM content. Please enable. Netflix movies should work fine now.

The Netflix app starts in full screen mode.
You can exit out of the app completely by pressing ALT+F4.
You can also press F11 to exit out of full screen mode.
 
OR:
```
sudo apt-get install netflix-desktop wine-compholio
```
 
 
PIPELIGHT: USE SILVERLIGHT IN YOUR LINUX BROWSER TO WATCH NETFLIX, MAXDOME VIDEOS AND MORE
 
Pipelight is project that brings Silverlight to any Linux browser that supports the Netscape Plugin API.This solution isn't Wine-free because the browser plugin continues to use Wine however, this shouldn't have a big impact on performance: "Pipelight consists out of two parts: A Linux library which is loaded into the browser and a Windows program started in Wine. The Windows program, called pluginloader.exe, simply simulates a browser and loads the Silverlight DLLs.
 
Install Pipelight in Ubuntu
 
Before proceeding, it's strongly recommended to close your web browser.

[LIST=1]
[*]If you've installed the old Pipelight version, remove it before proceeding:
[/LIST]
```
sudo apt-get remove pipelight
```

[LIST=1]
[*]To add the Pipelight stable and Compholio PPAs and install Pipelight in Ubuntu, use the following commands:
[/LIST]
```
sudo apt-add-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install pipelight-multi
```
 

[LIST=1]
[*]Then, you can install the Silverlight plugin using the following command:-
[/LIST]
system-wide:
```
sudo pipelight-plugin --enable silverlight
```
or - for your user only:
```
pipelight-plugin --enable silverlight
```

[LIST=1]
[*]By default, this will install Silverlight 5.1, but you can install a different version, for instance 5.0, by using this command instead (don't use "sudo" if you don't want to install it system-wide):
[/LIST]
```
sudo pipelight-plugin --disable silverlight --enable silverlight5.0
```
 
Once installed, start your browser. If it doesn't work, check if Silverlight is available in your browser plugin list (e.g.: you can type "about:plugins" in the address bar).
 

[LIST=1]
[*]Update 1: Pipelight now also supports installing the Windows version of Adobe Flash. To install the Windows version of Adobe Flash, use this command:-
[/LIST]
system-wide
```
sudo pipelight-plugin --enable flash
```
for your user only:
```
pipelight-plugin --enable flash
```
To be able to use this Window Flash version, in Chrome you need to diasble the Linux native Flash and for Firefox, you need to remove any Flash plugin from your system (except this one, obviously). For more info, see the official instructions.

[LIST=1]
[*]Update 2: Pipelight now supports Widevine. To enable Widevine, use the command below:-
[/LIST]
system-wide:
```
sudo pipelight-plugin --enable widevine
```
for your user only:
```
pipelight-plugin --enable widevine
```
 

[LIST=1]
[*]If you didn't close the browser before proceeding with the installation and Silverlight doesn't work, run the following command:
[/LIST]
```
rm -rf ~/.wine-pipelight/
```
and then restart the browser.
 

[LIST=1]
[*]We're not done yet. Silverlight should be working now, but some websites such as Netflix check the browser user agent and won't allow you to play any videos since Linux isn't supported. A work-around for this is to use a browser user agent switcher:
[LIST=1]
[*]Firefox: install UAControl or User Agent Overrider extensions and use one of the following user agents:
[LIST=1]
[*]Mozilla/5.0 (Windows NT 6.1; WOW64; rv:15.0) Gecko/20120427 Firefox/15.0a1Mozilla/5.0 (Windows NT 6.1; WOW64; rv:22.0) Gecko/20100101 Firefox/22.0Mozilla/5.0 (Windows NT 6.1; rv:23.0) Gecko/20131011 Firefox/23.0
[*]Chrome: install User Agent Switcher extension and select Windows Firefox 15 from the extension preferences.
[/LIST]
[/LIST]
[/LIST]
 
That's it! If video playback is slow or laggy, try THIS work-around.

---

