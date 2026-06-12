---
title: "Help for HBOGo viewing in 16.04 LTS"
date: 2016-08-20
forum: General Help
---

### Post by thegreataus on 2016-08-20
Recently, I caught a virus on an old HTPC running windows 7.  So, I decided to expand my horizons and try Ubuntu 16.04 LTS as I've started to learn some coding recently and thought it could be interesting.  So far, it works great for Youtube and most other videos.  However, you try to watch Hulu/HBOGo, and it's a no go.  It just sits there at a black screen.  I tried various solutions, like these:


1.) [https://www.maketecheasier.com/watch-hbo-now-ubuntu/](https://www.maketecheasier.com/watch-hbo-now-ubuntu/) - gives a nice write-up and how to in order to get Firefox working using pipeline and a Flash version for windows (I think).


2)  [http://www.omgubuntu.co.uk/2015/09/how-to-watch-hulu-on-ubuntu-1404-up](http://www.omgubuntu.co.uk/2015/09/how-to-watch-hulu-on-ubuntu-1404-up) - talks about updating HAL and some other digital rights stuff (DRM), very similar to this one: [http://www.howtogeek.com/239682/how-to-watch-hulu-on-ubuntu-and-other-linux-distributions/](http://www.howtogeek.com/239682/how-to-watch-hulu-on-ubuntu-and-other-linux-distributions/)


Follwing #1, I was actually able to get the video/audio to work!  However, the video works only when I force the image to occupy the whole screen, but even then the image only occupies approximately 60% of the screen and the image is cutoff, like it's trying to occupy the whole screen, but the normal playback buttons that are at the bottom occupy the other 40% of the screen, which is black (see attached image).  The playback buttons are also not functional.  I have to press the 'windows' button to bring up the application bar so I can right click on Firefox to close the whole screen down.  

[ATTACH=CONFIG]270772[/ATTACH]

Apparently I'm not the only one having this issue though: [http://www.howtogeek.com/239682/how-to-watch-hulu-on-ubuntu-and-other-linux-distributions/](http://www.howtogeek.com/239682/how-to-watch-hulu-on-ubuntu-and-other-linux-distributions/) . I read in a comment somewhere that this issue could be an issue with some of the fonts in pipeline and that causes all the playback button issues, or something to that affect, but I don't know. 


Should I downgrade 16.04 LTS to the 14 LTS where some of the workarounds were designed for?  Or have places like HBO updated their system and downgrading to use existing solutions won't work?  Just wondering!  I'd like to get it up and running and maybe help some other people out with similar issues.  I'm a long time windows user with very little coding ability and have only built computers, done nothing on the software side except install windows/etc.

---

### Post by howefield on 2016-08-20
Thread moved to the "*General Help*" forum.

---

### Post by grahammechanical on 2016-08-20
May I suggest that you look at this problem from a different direction? As I understand things you need an app to use HBOGo on a device and there is no app for Linux but there is an app for Android. So, now you need a way of running Android apps on Ubuntu.

1) Install Google Chrome browser.
2) Install a Chrome extension called Arc Welder. The purpose of Arc Welder is to allow developers of Android apps to test the Android app (apk file) on Chrome OS. But it also works on Ubuntu.
3) Download a copy of the apk file. There are sites that have copies of apk files for many Android apps.
4) Load Chrome; Run Arc Welder and direct it to the loaction of the apk file and click "Test." The app should load. Lock the app's icon to the launcher and then you will be able to load the Android app either from its icon in the launcher or its icon in the Dash without needing to load Chrome or Arc Welder.

It works. I used this for an app that comes in version for IOS, Android & Windows phones but not for Linux.

[https://developer.chrome.com/apps/getstarted_arc](https://developer.chrome.com/apps/getstarted_arc)

[https://chrome.google.com/webstore/detail/arc-welder/emfinbmielocnlhgmfkkmkngdoccbadn](https://chrome.google.com/webstore/detail/arc-welder/emfinbmielocnlhgmfkkmkngdoccbadn)

[https://www.apkfiles.com/apk-455408/hbo-go](https://www.apkfiles.com/apk-455408/hbo-go)

Regards

---

### Post by thegreataus on 2016-08-21
I'll give it a try in a little bit.  This will be specific for HBOGo, but what about other sites, like Hulu, etc, that may have similar issues?  I have seen others having issues.  I haven't tried since I basically only watch HBO shows, but I do meander to other sites like Vudu on occasion to watch movies, or even Amazon prime.

Hi Graham,

Thanks again for your help.  However, when I tried to install the apk from the link you provided, it seemed like it would try to open up the HBOGo app, but when the box came up, and then the Chrome app opened, it took me to: [http://www.surveysandpromotionsonline.com/Flow.aspx](http://www.surveysandpromotionsonline.com/Flow.aspx) - which tried to give me a Samsung phone

I tried it again, then it took me here: [http://www.electronicpromotion.com/Flow.aspx](http://www.electronicpromotion.com/Flow.aspx).

Is that like a Ubuntu version of a malware app or something?  I'm going to assume something just messed up for now.

I tried to download a couple other HBOGo extensions and use ArcWelder, and it seemed to work, then I got this alert: 

[B]"Get Google Play services
[/B]HBO GO won't run without Google Play services, which are missing from your tablet"

Google play APK will not run in ARC Welder.

On a related note to my first post, this alert keeps popping up, which is related to pipelight.  It seems like pipelight is not able to find an active download link.  Is there a way to remedy this?

[B]
"Failure to download extra data files[/B]

**The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.**

**ttf-mscorefonts-installer**

[B]The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.

[/B]**ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)**
**0% [Waiting for headers]"**

---

### Post by thegreataus on 2016-09-17
Well....thanks for all the help!

---

