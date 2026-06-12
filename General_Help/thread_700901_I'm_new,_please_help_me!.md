---
title: "I'm new, please help me!"
date: 2008-02-18
forum: General Help
---

### Post by vanflyheight13 on 2008-02-18
Thanks for taking the time to read this!

My name's Tom, I'm 17 and I've just dug out my linux box from under my bed and upgraded it to 7.10 using the install disk.

I want to use it as a media center for my room, I have it hooked up to a 19 inch HDTV, working on surround sound (can't afford it right now).

Anyway, on to my problem. The linux box is not networked, I don't have and can't afford another WiFi addon, so I've been trying to install the plugins to enable me to play MP3's and other media files. No success so far.

I've downloaded the codecs rhythmbox suggested and moved them to the linux box, but when I try to install them from the CD it says it's not a Debian file or something similar, but when I try to compile it myself it says there isn't a makefile and that no target is specified.

I'm expecting I'll get flamed somewhat... but if anyone could help me here by providing a guide or a download location that would be very very helpful.

Thanks!

PS: I've been trying since 8pm, it's now 1:10am, I'm shattered! :(

---

### Post by y-lee on 2008-02-18
Please see [Restricted formats]("https://help.ubuntu.com/community/RestrictedFormats") for help on installing MP3 support :)

If you need any help following directions there post back.

---

### Post by jrusso2 on 2008-02-18
I got a wifi card the other day for $7.95.  If you look around you can find them very cheap

---

### Post by vanflyheight13 on 2008-02-18
> **jrusso2 said:**
> I got a wifi card the other day for $7.95.  If you look around you can find them very cheap

I currently only have £2.35 to my name and a few coppers lying around... plus my knowledge on Ubuntu compatible wifi cards is extremely limited but I will look into that later. :)

---

### Post by tact on 2008-02-18
Hey there...  

I doubt anyone will flame you at all.   I have no experience with the kind of problem you are facing but have seen several threads on the topic of "how to get software packages from repositories without a network connection" or "how to build your own repo on a CD" etc....

Maybe you can do a search on some of those terms and find good info?   Sorry I cannot give directions first hand.

---

### Post by vanflyheight13 on 2008-02-18
> **y-lee said:**
> Please see [Restricted formats]("https://help.ubuntu.com/community/RestrictedFormats") for help on installing MP3 support :)

If you need any help following directions there post back.

It may be just me, but when I went to do that on my computer it wouldn't work because I have no internet connection to download the packages.

---

### Post by y-lee on 2008-02-18
Sorry I misunderstood you I thought networked meant networked to other local computers not that you didn't have an internet connection.

From [another thread here]("http://ubuntuforums.org/showthread.php?p=170680#post170680")


> **UbuWu said:**
> A few months ago, when I didn't have an internet connection yet on my computer, I had a lot of trouble trying to install software on ubuntu. Now I am trying to make a little howto on doing this. The following is what I thought of so far, please give your comments on how it could be done better:

First of all, you need the correct package index files (the files that are updated when you type apt-get update). If you have a dial-up internet connection this should be easy, just use apt-get update. If you don't have an internetconnection at all, you will probably have to find someone who has the same ubuntu version installed as you. The files are stored in /var/lib/apt/lists. You need all the files starting with archive.ubuntu.com_ubuntu_dists_hoary (assuming you are running hoary/5.04). Put them in your own /var/lib/apt/lists directory.

Then the typing the following line in a terminal window will give you the files you need to download:
```
apt-get -qq --print-uris install ***packagename*** | cut -d\' -f2
```
Replace ***packagename*** with the name of the package you want to install.
You can add >filelist to the end of the line to make a file containing all the urls, which you can easily download on any pc with linux using wget -i filelist.

Download all the files and put them in one directory. Then go to the directory and type: 'dpkg-scanpackages . /dev/null | gzip > Packages.gz'
Burn all the files in the directory on a cd.
On your own pc type 'apt-cdrom add'.
Then you are all set and can use apt-get install ***packagename*** to install the package.

Alternatively you can install all the individual package files with dpkg -i filename.deb

The package you are hunting for is of course ubuntu-restricted-extras. But you need an internet connection somewhere on another machine to do this.

---

### Post by vanflyheight13 on 2008-02-18
> **y-lee said:**
> 
The package you are hunting for is of course ubuntu-restricted-extras. But you need an internet connection somewhere on another machine to do this.

I've installed the package, yet when I try to play MP3's I'm still greeted with the error message that I need the two gstreamer plugins I was trying to compile (unsucessfully) myself. :(

---

### Post by y-lee on 2008-02-18
> **vanflyheight13 said:**
> I've installed the package, yet when I try to play MP3's I'm still greeted with the error message that I need the two gstreamer plugins I was trying to compile (unsucessfully) myself. :(

Try to use the above advice to install the gstreamer plugins.

What exactly were they? For Gusty maybe these, [gstreamer0.10-plugins-base]("http://packages.ubuntu.com/gutsy/libs/gstreamer0.10-plugins-base")?

---

### Post by vanflyheight13 on 2008-02-18
> **y-lee said:**
> Try to use the above advice to install the gstreamer plugins.

What exactly were they? For Gusty maybe these, [gstreamer0.10-plugins-base]("http://packages.ubuntu.com/gutsy/libs/gstreamer0.10-plugins-base")?

The plugins it said I needed were "GStreamer-extra-plugins" and "GStreamer-ffmpeg-vidro-plugin"...

this is starting to feel like a bad nightmare. :P

---

### Post by y-lee on 2008-02-18
> The plugins it said I needed were "GStreamer-extra-plugins" and "GStreamer-ffmpeg-vidro-plugin"...

this is starting to feel like a bad nightmare. :P

[ [SOLVED] where is the GStreamer extra plugins at?]("http://ubuntuforums.org/showthread.php?t=689933") 

and [gstreamer0.10-ffmpeg]("http://packages.ubuntu.com/gutsy/libs/gstreamer0.10-ffmpeg") is maybe the other.

To install these you are going to have to try to use the method given above and unfortunately all dependencies are going to have to be met. I have never tried to install without internet connection before. 

Sorry it can't be easier, I'm looking and trying as best I can.

---

### Post by y-lee on 2008-02-18
Yeah I think I'm right you need [all the dependencies satisfied]("https://answers.launchpad.net/ubuntu/+question/13111"), so for ubuntu-restricted-extras you said you installed it. How did you install it?

Did you met all the dependencies listed [here]("http://packages.ubuntu.com/gutsy/metapackages/ubuntu-restricted-extras") and all the dependecies listed for each of them.

I'm starting to agree with you it sounds like a nightmare :(

---

### Post by vanflyheight13 on 2008-02-18
> **y-lee said:**
> [ [SOLVED] where is the GStreamer extra plugins at?]("http://ubuntuforums.org/showthread.php?t=689933") 

and [gstreamer0.10-ffmpeg]("http://packages.ubuntu.com/gutsy/libs/gstreamer0.10-ffmpeg") is maybe the other.

To install these you are going to have to try to use the method given above and unfortunately all dependencies are going to have to be met. I have never tried to install without internet connection before. 

Sorry it can't be easier, I'm looking and trying as best I can.

I've followed the instructions there for the VLC player, but after I do the "./compile" and type "make", nothing happens, just an error telling me "make: *** No rule to make target `install'. Stop."

Thanks for all the help, I really appreciate it!

---

### Post by vanflyheight13 on 2008-02-18
> **y-lee said:**
> Yeah I think I'm right you need all the dependencies satisfied, so for ubuntu-restricted-extras you said you installed it. How did you install it?

Did you met all the dependencies listed [here]("http://packages.ubuntu.com/gutsy/metapackages/ubuntu-restricted-extras") and all the dependecies listed for each of them.

I'm starting to agree with you it sounds like a nightmare :(

WTF I need to install all of them??!?!?! *sobs uncontrollably*

---

### Post by bodhi.zazen on 2008-02-18
Consider a distro with the codics pre-installed such as Mint

Mint is Ubuntu + a few codics.

---

### Post by y-lee on 2008-02-18
> 've followed the instructions there for the VLC player, but after I do the "./compile" and type "make", nothing happens, just an error telling me "make: *** No rule to make target `install'. Stop."

Well that one you need another package build-essential. hunting for a link now.

Just take your time, some of these packages may already be installed. Check in synaptic for each one, note the ones you don't have and try to determine the deps for them all.

Does your computer have an Ethernet card and can you find an ethernet connection somewhere like a friends or something? It would be a trivial matter if you were connected.

Note: [build-essential for Gusty]("http://packages.ubuntu.com/gutsy/devel/build-essential")

---

### Post by y-lee on 2008-02-18
> **bodhi.zazen said:**
> Consider a distro with the codics pre-installed such as Mint

Mint is Ubuntu + a few codics.

Actually bodhi.zazen there has a very good point :)

---

### Post by vanflyheight13 on 2008-02-18
> **y-lee said:**
> Well that one you need another package build-essential. hunting for a link now.

Just take your time, some of these packages may already be installed. Check in synaptic for each one, note the ones you don't have and try to determine the deps for them all.

Does your computer have an Ethernet card and can you find an ethernet connection somewhere like a friends or something? It would be a trivial matter if you were connected.

Yeah, I've got a network card, I just didn't really fancy having to sit through many possibly lengthy downloads to enable MP3 playback... guess I was wrong. :)

Tomorrow I'll move the computer downstairs out of my connectionless room and set up a network... will that sort out my problems easier?

---

### Post by vanflyheight13 on 2008-02-18
> **y-lee said:**
> Actually bodhi.zazen there has a very good point :)

In your opinion which would be best for me overall? I'm a bit out of my depth here...

---

### Post by y-lee on 2008-02-18
Info on Mint linux

[LIST]
[*][Linux_Mint]("http://en.wikipedia.org/wiki/Linux_Mint") at wikipedia
[*][http://linuxmint.com/]("http://linuxmint.com/")
[*][Something you might want to read first]("http://ubuntuforums.org/showthread.php?t=699392")
[/LIST]

---

### Post by UK-Wobbie on 2008-02-18
> **vanflyheight13 said:**
> In your opinion which would be best for me overall? I'm a bit out of my depth here...

As your computer got a floppy or a CD R burner drive? Or a pen drive to put the files on to? :)

---

### Post by vanflyheight13 on 2008-02-18
> **UK-Wobbie said:**
> As your computer got a floppy or a CD R burner drive? Or a pen drive to put the files on to? :)

My PC has a CD-R drive, my laptop has a DVD-R drive...

I've started downloading the Mint .iso so if the network doesn't fix ubuntu tomorrow, I'm going for a clean install of mint. :)

---

### Post by y-lee on 2008-02-18
> In your opinion which would be best for me overall? I'm a bit out of my depth here...

I've never used Mint before but it is my understanding that mp3 support is included in the basic install. Really is ubuntu with a few extras. But still with no internet installing extra programs is going to be problematic anyway. 

I probably would advise you to try it, if you can download it and burn the CD then why not? 

What you are trying to do with ubuntu is going to take a while to set up. It would be educational but time consuming, how patient are ya?

Me I'm stubborn and I like puzzle solving but it is not for everyone. :lolflag:

---

### Post by vanflyheight13 on 2008-02-18
> **y-lee said:**
> I've never used Mint before but it is my understanding that mp3 support is included in the basic install. Really is ubuntu with a few extras. But still with no internet installing extra programs is going to be problematic anyway. 

I probably would advise you to try it, if you can download it and burn the CD then why not? 

What you are trying to do with ubuntu is going to take a while to set up. It would be educational but time consuming, how patient are ya?

Me I'm stubborn and I like puzzle solving but it is not for everyone. :lolflag:


Educational is good I suppose, I'll need to learn this at some point. As for patience... well I'll probably be up at 6am to get started, there's your answer. :lolflag:

---

### Post by y-lee on 2008-02-18
Good luck.

I gotta sleep soon myself. thanks for the fun :)

---

### Post by vanflyheight13 on 2008-02-18
> **y-lee said:**
> Good luck.

I gotta sleep soon myself. thanks for the fun :)

thanks for your time and help, sleep well! :)

---

