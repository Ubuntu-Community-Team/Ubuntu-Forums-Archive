---
title: "Installing Skype under 12.4 64 bit"
date: 2013-08-29
forum: General Help
---

### Post by Roger D on 2013-08-29
Can anyone suggest a fail-safe approach to installing Skype under 12.04 64 bit?

I'll tried all manner of things, most recently installing Ubuntu 12.04 (multiarch) from the Skype website. The Ubuntu Software Centre wasn't at all keen, but I pressed ahead, and it sort of worked very briefly - I made one successful Skype test call. Now I can see the Skype icon in Dash, but nothing happens when I click on it.

I've uninstalled the Client for Skype from the Software Centre.

It must be working for somebody.

Regards

Roger D

---

### Post by scbingham on 2013-08-29
It has been discussed in the forums, need to search a little. Skype is only 32bit, if I remember at least in one of the threads, some people have had to download some 32bit libraries to get it to work.

Good luck.

---

### Post by sammiev on 2013-08-29
I downloaded skype from here [http://www.skype.com/en/download-skype/skype-for-computer/](http://www.skype.com/en/download-skype/skype-for-computer/) and it worked right out of the box. Been using it for a few weeks now on 12.4
sammiev

---

### Post by Roger D on 2013-08-29
Well, I've just tried this again, and the Software Centre red installation bar gets to about 95% complete and then stops, showing a fresh install button.

Something wrong somewhere

---

### Post by speartip on 2013-08-29
Skype is working fine here on 12.04 64 bit.
Don't know if this will make any difference, but instead of using the software centre try using GDebi instead.
Just right click the .deb package & install using GDebi.
Software centre has given me issues in the past.

---

### Post by lah7 on 2013-08-29
Skype's a pain to install on 64-bit systems, but I found that performing the following in the terminal works on Ubuntu 13.04, but I can't see why it wouldn't also work on 12.04 too.

[COLOR=#b22222]If you've got it installed, you may wish to uninstall it if you wish to do a re-installation this way.[/COLOR]

_**Here's the method I use and seems to work.**_

**1. **Open the terminal and download the latest Skype:
```
wget http://www.skype.com/go/getskype-linux-beta-ubuntu-64
```
A file named [COLOR=#0000cd]*"getskype-linux-beta-ubuntu-64"*[/COLOR] has been downloaded in your home directory. This is the latest Skype package.

**Now for the installation of various packages...**
**2. **Add the 32-bit architecture:
```
sudo dpkg --add-architecture i386
sudo apt-get update
```

**3. **Install some essential 32-bit packages:
```
sudo apt-get -f install -y
sudo apt-get install sni-qt:i386 -y
```

**4. **Install the Skype package:
```
sudo dpkg --install getskype-linux-beta-ubuntu-64
```
*(Note: If you was to use the software centre for installation, you should add ".deb" at the end)*

Skype should hopefully now be working! :)
[B]
Optional: [/B]If you want Skype to integrate into Unity better, I suggest installing the Skype Wrapper. Note that this is** third party** and **isn't officially supported** by Skype or Microsoft.

This article sums it up: [http://www.omgubuntu.co.uk/2011/11/skype-wrapper-0-4-adds-unity-features-menu-avatars-and-extra-settings/](http://www.omgubuntu.co.uk/2011/11/skype-wrapper-0-4-adds-unity-features-menu-avatars-and-extra-settings/)

```
sudo add-apt-repository ppa:skype-wrapper/ppa
sudo apt-get update
sudo apt-get install skype-wrapper
```

Likewise, other problems with Skype could be caused by all sorts, like crackling and stutter audio is caused by pulseaudio, and without compiz, skype video might not work correctly and such.

I hope this works for you.

---

### Post by Roger D on 2013-08-30
Thanks - I'll give this a go.

What's the "NameOfThePackage" in this context?

---

### Post by lah7 on 2013-08-30
> **Roger D said:**
> What's the "NameOfThePackage" in this context?

Sorry, I should of pointed that out. If you was to download the URL through a browser, it uses the latest file name, but I just realised wget just leaves it simply "[COLOR=#000000][FONT=Ubuntu Mono]getskype-linux-beta-ubuntu-64"
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg --install [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]getskype-linux-beta-ubuntu-64[/FONT][/COLOR]
```

I've edited my previous post to reflect this error.

---

### Post by Linuxisfast on 2013-08-30
Skype installs and works fine under Ubuntu 12.04 when installed via software center. Just enable partner repository in software sources.

---

### Post by Roger D on 2013-08-30
This sounds very promising - I'm all for trying to keep things simple, but:

I've opened Ubuntu Software Centre>Edit>Software soucres, clicked on the 'other software' tab, clicked on 'Canonical Partners' and 'Canonical Partners, (Source Code)', closed and re-started my system but the trouble is I can't find Skype or Client for Skype anywhere ins the Software Centre. In particular, under All Software, Canonical Partners is empty.

---

### Post by lah7 on 2013-08-30
I haven't seen Skype in the software centre for a long time (unless it's just Ubuntu 13.04). I believe it was (or is, possibly) but that was the really old beta version. The latest version is currently** 4.2.0.11-1 **at this time of writing.

My previous post doesn't add any repository, so it means manually updating it. I just upgraded mine, I've been using 4.1.0.20 for quite some time.

---

### Post by plucky on 2013-08-30
> **Roger D said:**
> This sounds very promising - I'm all for trying to keep things simple, but:

I've opened Ubuntu Software Centre>Edit>Software soucres, clicked on the 'other software' tab, clicked on 'Canonical Partners' and 'Canonical Partners, (Source Code)', closed and re-started my system but the trouble is I can't find Skype or Client for Skype anywhere ins the Software Centre. In particular, under All Software, Canonical Partners is empty.

You need to reload the repository .list files using ```
sudo apt-get update
``` after you added the Partner repository.
Then see if it is in the  Software Centre.


Good Luck

---

### Post by jhondoty on 2013-08-30
Thanks [**[COLOR=#000000]lah7[/COLOR]**]("http://ubuntuforums.org/member.php?u=1726297"), I was suffering with the same problem. I will try this.

---

### Post by Roger D on 2013-08-30
Ah... have finally cracked this. I went to:[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype) and followed the instructions about installing from the repository, and after a bit of tweaking with the PulseAudio volumen control, all is working.

Thanks for everybody's help.

Roger D

---

### Post by Xubuntist on 2014-03-16
> **plucky said:**
> You need to reload the repository .list files using ```
sudo apt-get update
``` after you added the Partner repository.
Then see if it is in the  Software Centre.

i did this and now skype 4.2.0.11 is displayed and is now installing
just finished installing and logged in and seems to work properly
xubuntu 13.10
thank you for your help

---

