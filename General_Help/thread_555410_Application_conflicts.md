---
title: "Application conflicts?"
date: 2007-09-20
forum: General Help
---

### Post by jeffjohn on 2007-09-20
Well; I was attracted for all the usual reasons to the Linux concept and high-level support from ministers and national governments; however after a three month trial, I have to say that I can not recommend it for professional work.  As a file server on my network it is stable, reliable and faultless.  The 'supplied' Office-type applications ditto.

BUT almost anything using the i/net, including Firefox, with the apparent exception of aMSN and File Manager, seems totally flakey!  Music playing crashes; Skype does not work, Opera disconnects, and so on and on.

I love the Server functionality and will continue to build on it, but all 'valuable' work is being done exclusively on the XP Windows PCs, as is this input!

Does anyone find it as stable as it should be?  The Linux coding is probably the 'best' so I assume it is a problem with conflicts and third-party add-ons.

Written reluctantly, but there again I have bought the books, spent many hours adapting from Unix, and really given it a good bash.  Is there a 'guaranteed' route that others can recommend that will work 24/7 ??

Thanks for your considered advice, Jeff  (Dr Jeff J Purcell, JJP_Consulting)

---

### Post by ramjet_1953 on 2007-09-20
Did you post specific error messages and seek help on this, or other forums?

For me, Firefox works faultlessly, Opera ditto, all music players work fine and  I've been using Skype without issue.

My experience has been one of stability and reliability on the desktop.

Might I suggest that you are having issues with your particular hardware / installation that are not necessarily common across all systems?

Regards,
Roger :cool:

---

### Post by jeffjohn on 2007-09-20
thanks Ramjet -no error codes or faults as such were displayed just random re-booting and internet disconnects; I'll think hard about your hardware/set up comments.  thanks again jeff

---

### Post by ramjet_1953 on 2007-09-20
If you try running the applications by opening up a terminal and typing in the application's start-up name, you will then be able to see in the terminal any errors.

ie if you are having problems with firefox web browser, type firefox in a terminal.

Regards,
Roger 8)

---

### Post by jeffjohn on 2007-09-20
Right!  I did not know I could do that....does this mean something to you?  Msg after tring to download music file:-  thanks Jeff

Message: mSrc: 
** Message: mCache: 0
** Message: mControllerHidden: 0
** Message: mShowStatusbar: 0
** Message: mHidden: 1
** Message: mAudioOnly: 0
** Message: mAutostart: 1, mRepeat: 0
** Message: Launching: /usr/lib/totem/totem-plugin-viewer --plugin-type gmp --user-agent Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20061201 Firefox/2.0.0.6 (Ubuntu-feisty) --mimetype video/x-msvideo --hidden 
** Message: Viewer spawned, PID 6000
** Message: GetValue variable 14 (e)
** Message: Viewer DBus interface name is 'org.gnome.totem.PluginViewer_6000'
** Message: NameOwnerChanged old-owner '' new-owner ':1.14'
** Message: Viewer now connected to the bus
** Message: ViewerSetup
** Message: ViewerReady
** Message: NameOwnerChanged old-owner '' new-owner ':1.14'
** Message: Already have owner, why are we notified again?
** Message: Viewer state: STOPPED

---

### Post by kerry_s on 2007-09-20
> **jeffjohn said:**
> Right!  I did not know I could do that....does this mean something to you?  Msg after tring to download music file:-  thanks Jeff

Message: mSrc: 
** Message: mCache: 0
** Message: mControllerHidden: 0
** Message: mShowStatusbar: 0
** Message: mHidden: 1
** Message: mAudioOnly: 0
** Message: mAutostart: 1, mRepeat: 0
** Message: Launching: /usr/lib/totem/totem-plugin-viewer --plugin-type gmp --user-agent Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20061201 Firefox/2.0.0.6 (Ubuntu-feisty) --mimetype video/x-msvideo --hidden 
** Message: Viewer spawned, PID 6000
** Message: GetValue variable 14 (e)
** Message: Viewer DBus interface name is 'org.gnome.totem.PluginViewer_6000'
** Message: NameOwnerChanged old-owner '' new-owner ':1.14'
** Message: Viewer now connected to the bus
** Message: ViewerSetup
** Message: ViewerReady
** Message: NameOwnerChanged old-owner '' new-owner ':1.14'
** Message: Already have owner, why are we notified again?
** Message: Viewer state: STOPPED


that tells me your using totem which sucks, i recommend mplayer+codecs or vlc+mediaplayerconnectivty extension

---

### Post by dark_harmonics on 2007-09-20
I agree totem does suck. My system is really stable BTW. I just moved from being completely microsoft xp and having 0 linux experience into ubuntu linux on all my computers. 

I have had some issues, but nearly all of them at least have some posting in here that i can ask questions about or read the how-tos to fix. 

I did have one rebooting issue on my desktop computer. It was due to a faulty graphics card. It seems that windows was not utilizing it for rendering my desktop and so it wasn't as apparent. It would just crash during games. On ubuntu with compiz-fusion it was using my video card a lot more and so crashing more. I replaced the hunk of junk and the issue vanished so I'm assuming it was the hardware.

---

### Post by notwen on 2007-09-20
VLC for alllll media needs. =]  As for my system, I've been using Linux for 4ish years now and Ubuntu for the past 2 and I'm very happy with it's stability.  How are you connecting to the Internet(wired or wireless) and are you using Network Manager/Wicd/Wifi-Radar?  What version of Ubuntu are you using and what network hardware are you using?  Books can tell you more, but ppl's experience can be more useful, plus there are more likely more ppl here with info than your books have pages.  Post if you run into any issue and see if you cannot get it resolved by someone who's encountered your issue before.  =]

---

### Post by angryfirelord on 2007-09-20
> **kerry_s said:**
> that tells me your using totem which sucks...
Correction. Totem with gstreamer sucks. Totem with Xine works much better (unless you still want to be able to configure more options like in other video players).

---

### Post by jeffjohn on 2007-09-20
ok - that all sounds constructive; but there again, why do I have to set about changing the distro, as delivered on a 'mature' OS?  

 That said I would like to follow any suggestions; can someone extract the logical steps from the techno-hype for me, please.  I'll check on my hardware types later.  many thanks indeed for the support; should have asked earlier perhaps!  Jeff

---

### Post by justin whitaker on 2007-09-20
> **jeffjohn said:**
> ok - that all sounds constructive; but there again, why do I have to set about changing the distro, as delivered on a 'mature' OS?  

 That said I would like to follow any suggestions; can someone extract the logical steps from the techno-hype for me, please.  I'll check on my hardware types later.  many thanks indeed for the support; should have asked earlier perhaps!  Jeff

Well, XP gets tweaked by the end user: you don't run a dead stock install, you update the drivers for your hardware and peripherals, you add the media software and anti virus that you like, you tweak the desktop so it looks the way you want it to look....Ubuntu ships with a set of programs that are thought to be the most useful for the average user, but it's expected that you will make it your own. 

Like swapping out the backend on Totem for something other than gstreamer. In add/remove there are a bunch of mulitmedia options that you can install, the most important of which are Mplayer and VLC. These are essential tools. Those two should pick up the Xine backend, so you should be able to select that in Totem.

---

### Post by jeffjohn on 2007-09-20
Thanks justin!  to translate; I can select and add either Mplayer or VLC.  Is that sufficient?  What is all this about Xine 'backends' and selecting in Totem.  (would I be correct in thinking you write manuals!).

seriously I am most grateful! jeff

---

### Post by jeffjohn on 2007-09-20
I've had a look at HW.  The NIC is realtek RTL-8139/8139C/8139C+  and the graphics card is a GeForce MX 400 AGP

---

### Post by justin whitaker on 2007-09-20
> **jeffjohn said:**
> Thanks justin!  to translate; I can select and add either Mplayer or VLC.  Is that sufficient?

Yes, that is sufficient. There is also a "restricted extras" package that you probably want. 


> What is all this about Xine 'backends' and selecting in Totem.  (would I be correct in thinking you write manuals!).

Here is the community "manual" on Multimedia applications.

[https://help.ubuntu.com/community/MultimediaApplications#totem-xine](https://help.ubuntu.com/community/MultimediaApplications#totem-xine)

What totem-xine does is swap out the version with a gstreamer backed for one that uses xine. 

To do that use the following command:

sudo apt-get install totem-xine

> seriously I am most grateful! jeff

No worries! We are all here to help.

---

### Post by angryfirelord on 2007-09-20
> **jeffjohn said:**
> Thanks justin!  to translate; I can select and add either Mplayer or VLC.  Is that sufficient?  What is all this about Xine 'backends' and selecting in Totem.  (would I be correct in thinking you write manuals!).

seriously I am most grateful! jeff
The backend is simply what's used to render the video. It's like the engine of a car, in this case you get two of them for totem. Gstreamer is completely open-source, where Xine is not. That's why Gstreamer is included by default in Ubuntu.

To install totem-xine:

Look at your /etc/apt/sources.list & make sure universe is enabled.

Then, type the following:
```
sudo apt-get install totem-xine
```

---

### Post by Perfect Storm on 2007-09-20
Changed the title to something less flamable. Please be more specific with thread titles. Thank you

regards
A.I. dude
Ubuntu Forum Staff

---

### Post by jeffjohn on 2007-09-20
Thanks- I followed all instructions and it went smoothly.  Now if I visit [http://www.virginmedia.com/music/pictures/toptens/guitar-riffs.php](http://www.virginmedia.com/music/pictures/toptens/guitar-riffs.php), FF crashes still:-

jeff@jeff-linux:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: NP_Initialize
** Message: NP_Initialize succeeded
** Message: totemPlugin ctor [0xad613678]
** Message: Init mimetype 'application/x-mplayer2' mode 1
** Message: Base URI is 'http://sib1.od2.com/common/product/Product.aspx?shop=16&associd=6&catno=OD2DI6007882-06'
** Message: Real mimetype for 'application/x-mplayer2' is 'video/x-msvideo'
argv[0] type application/x-mplayer2
argv[1] pluginspage [http://microsoft.com/windows/mediaplayer/en/download/](http://microsoft.com/windows/mediaplayer/en/download/)
argv[2] id WMPlay2
argv[3] name WMPlay2
argv[4] height 0
argv[5] width 0
** Message: mSrc: 
** Message: mCache: 0
** Message: mControllerHidden: 0
** Message: mShowStatusbar: 0
** Message: mHidden: 1
** Message: mAudioOnly: 0
** Message: mAutostart: 1, mRepeat: 0
** Message: Launching: /usr/lib/totem/totem-plugin-viewer --plugin-type gmp --user-agent Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20061201 Firefox/2.0.0.6 (Ubuntu-feisty) --mimetype video/x-msvideo --hidden 
** Message: Viewer spawned, PID 5941
** Message: GetValue variable 14 (e)
** Message: Viewer DBus interface name is 'org.gnome.totem.PluginViewer_5941'
** Message: NameOwnerChanged old-owner '' new-owner ':1.13'
** Message: Viewer now connected to the bus
** Message: ViewerSetup
** Message: ViewerReady
** Message: NameOwnerChanged old-owner '' new-owner ':1.13'
** Message: Already have owner, why are we notified again?
** Message: Viewer state: STOPPED


Should we have resolved this? or is something else missing from my set up??

thanks again Jeff  (be patient with me!)

---

### Post by jeffjohn on 2007-09-21
I see that 12 hours on, my FF is still up and running so I guess stability is much improved; thanks for the helpful advice!  incidentally, I see that there are loads of queries about random internet disconnect so perhaps I am not as alone as I thought you were all implying!

---

### Post by jeffjohn on 2007-09-21
any knowledge about these 'old-owner' new-owner' alerts?

---

### Post by jeffjohn on 2007-11-09
I'm obliged and very pleased to report that my previous doubts about Ubunto 7.04 were unfounded!!!  Although no deficiencies were reported, in some desperation I swapped out all my memory chips and replaced with 1GB of new RAM.  The system has now run perfectly with out a glitch for a week!  many thanks for everyone's forebearance!! I am now a true convert!!  jeffjohn

---

