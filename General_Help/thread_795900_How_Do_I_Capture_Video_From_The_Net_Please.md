---
title: "How Do I Capture Video From The Net Please?"
date: 2008-05-15
forum: General Help
---

### Post by cherylholmes on 2008-05-15
Hi,

I'm runing Hardy now...what I need to know is how do I capture video's from online to save them to my hard drive?  Some people do that with YouTube and post them on their blogs...but my vet was in a news story last night and I want to save the video from the story to my hard drive and then transfer it to CD...

How do I save a video this way to hard drive from a website like the TV channels or YouTube?

Thanks! cheryl

---

### Post by empthollow on 2008-05-15
You can download a youtube video by using this website [http://keepvid.com/](http://keepvid.com/)  there is a link at the top of the page you can bookmark.  Then when you are on the page playing the video you want to save simply click the bookmark and the resulting page will give you a link to download your video.  It may sound more confusing than it actually is.  Youtube uses flv format files so you may need to convert them to something like mpeg to make them usable.  the other problem with youtube flv files - right now anyway - is that they are very low quality.  I hear youtube is working to create a high quality video option.  In any event you can save any video you don't have a direct link to with this site (at least that i've run into).  

you can use this command to convert the .flv file into an mpeg
```

ffmpeg -i filename.flv -target ntsc-dvd newfilename.mpeg
```

---

### Post by cherylholmes on 2008-05-16
Thank you but this looks way over my head...I've only been using Ubuntu since last November.  I did capture the link from the video I want to save I just don't know what to do with it now because it's the actual new video I want to save to CD so my sister can see the newstory...here it is, if anyone can tell me what to do with it now..I would appreciate it very much.  Will I be able to save the newstory to CD?

Thank you very much..cheryl

[http://link.brightcove.com/services/link/bcpid1127733498/bclid1125874529/bctid1554446299](http://link.brightcove.com/services/link/bcpid1127733498/bclid1125874529/bctid1554446299)

---

### Post by empthollow on 2008-05-16
[http://link.brightcove.com/services/player/bcpid1127733498?bclid=1125874529&bctid=1554446299]("http://link.brightcove.com/services/player/bcpid1127733498?bclid=1125874529&bctid=1554446299")

There is your download link.

goto system -> administration -> synaptic package manager
search for and install mandvd

that is the simplest burn a dvd program.
let me know if you have any more problems.

---

### Post by jespdj on 2008-05-16
You can use [http://downloadyoutubevideos.com/](http://downloadyoutubevideos.com/) to download YouTube videos as .flv files.

You can play those with for example mplayer. If you don't have mplayer, install it:
```
sudo apt-get install mplayer
```

---

### Post by cherylholmes on 2008-05-17
Thank you Jeremy but there's no "mandvd" in my Synaptic.  Any other suggestions?  Then once I have an app to do it, what do I do with this link to put it on CD or DVD?  Thanks! cheryl

---

### Post by empthollow on 2008-05-17
Sorry, i must have downloaded it from here
[http://www.getdeb.net/app/ManDVD]("http://www.getdeb.net/app/ManDVD")
pick the version of ubuntu you have (choose 32 bit if you are unsure), download and doubble click.

---

### Post by Psyker7 on 2008-05-17
I've always liked the firefox addon:
[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

Any of these suggestions will save the movie / video to disk, then simply put in a blank CD, go Places -> CD Creator, drag the file on there, and burn :D

---

### Post by empthollow on 2008-05-17
wow, that's a pretty cool extension i was unaware of.

---

### Post by stanz on 2008-05-18
I've just come across it also, and look to do the convert "this" to "that", thing.
Most of those users are still using m$ with no advice for *nix users.
Sourceforge has a CaC "Catch and Convert" program, which mentions video sites
like google & youtube specifically.
I may try it tonite...let cha know how it is.

Hope it helps..
[https://sourceforge.net/projects/cac/](https://sourceforge.net/projects/cac/)

---

### Post by bigtony on 2008-05-18
I've found the firefox extention "download helper" very easy. It installs as simply as any firefox extension and stays out of the way up in the toolbar. While you're in youtube or any other site with embedded videos, just rightclick on it's icon and it will let you choose which video you want it to download.

---

### Post by cherylholmes on 2008-05-18
Thank you very much!  I did download Mandvd.  I'll play with it today...I hope it will help me do the trick!  GetDeb site looks very intriguing.  Will explore it too.  I appreciate your help!  Thanks again! Cheryl

> **empthollow said:**
> Sorry, i must have downloaded it from here
[http://www.getdeb.net/app/ManDVD]("http://www.getdeb.net/app/ManDVD")
pick the version of ubuntu you have (choose 32 bit if you are unsure), download and doubble click.

---

### Post by cherylholmes on 2008-05-18
Thanks Parker...I did download that add-on extension the other night.  In fact, that's how I found out the website for the video in the first place!  It's a cool extension.  But I didn't know how to actually save it to cd or dvd...how to save the actual video that is..so someone else could watch it.  My sister wants to see the news story..that's why I want to put it on CD or DVD.  I hope all this stuff works to do this.  

Thanks tons to all of you!  I appreciate it very much!  cheryl


> **Psyker7 said:**
> I've always liked the firefox addon:
[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

Any of these suggestions will save the movie / video to disk, then simply put in a blank CD, go Places -> CD Creator, drag the file on there, and burn :D

---

### Post by jpietari on 2008-05-18
The program 'Miro' (sudo apt-get install miro) allows you to download and store videos.

---

### Post by logx on 2008-05-18
You can also just insert the URL in one of the many youtube-ish websites that you can find in the net.

You will need no app to download the videos and it's free!

---

### Post by cherylholmes on 2008-05-20
Would one of you please walk me through saving these videos or at least 1 of them...how I would save them to my hard drive and then to cd or dvd?  I want to make sure I do it right.  Do I need to change the formats or anything before saving them or viewing them from CD or DVD?  Will they show /play as a video instead of the location saved on hard drive?

I want to save them to CD or DVD so my sister can play them...Thank you very much...I do have the mandvd now, K3B, download helper from Firefox too.  Thank you very much for taking the time to do thid to help me!  I appreciate it..cheryl

file:///tmp/SmokeInhalation-2.wmv

[http://link.brightcove.com/services/link/bcpid1127733498/bclid1125874529/bctid1554446299]("http://link.brightcove.com/services/link/bcpid1127733498/bclid1125874529/bctid1554446299")

[http://SmokeInhalation.wmv (1.1MB)]("http://SmokeInhalation.wmv (1.1MB)")

---

### Post by empthollow on 2008-05-20
mandvd will convert the video to dvd format for you.  as long as it is reading the file you should be able to just follow the steps in the program.  also, go to synaptic and make sure you have a package called

libdvdcss2

installed, it is required for reading dvds and i think making them as well.  

1. download the video from the link i posted earlier (the firefox extension may be a good method but i have no experience with the extension) Let me know  if you are intrested in a detailed how to for downloading you video using the keepit website and i will write one for you.
2.Open mandvd, when mandvd asks for a video file select the downloaded video. (don't worry about the file type because the program will convert it for you.
3. if you get any other errors or you can't select the video you are trying to burn, post them here (because of proprietary video formats multimedia can be a bit tricky so there may be some other packages to install)

Mandvd will walk you through creating a menu and burning the dvd.

---

### Post by cherylholmes on 2008-05-20
Jeremy, I'll try what you're telling me to do, but YES, that would be so kind of you to do a HOW TO write up for me to foilow to do this the other way too!  Would you please do that for me?  And let me know what I need in Synaptic or other apps I need to dl too?

Will my sister be able to watch the DVD or CD on her windows o/s too?  Or will she need to watch them on my Linux?

I really appreciate all your help tremendously Jeremy as I'm new to Linux.  I've only been using it since last November

My printer, an HP G*% doesn't work in Hardy so eventually I may have to go back to Windows myself to have a printer that works.  It work haphazardly in Gutsy tho.  Maybe I can just go back to Gutsy instead.  I reported the bug to Launchpad but they haven't been able to fix it yet.  Been about a month or so.

I'll check and make sure I have the lib app you mentioned installed..

Please do send me a detailed howto for keep it!  I really do appreciate your help Jeremy!  Thank you..cheryl



> **empthollow said:**
> mandvd will convert the video to dvd format for you.  as long as it is reading the file you should be able to just follow the steps in the program.  also, go to synaptic and make sure you have a package called

libdvdcss2

installed, it is required for reading dvds and i think making them as well.  

1. download the video from the link i posted earlier (the firefox extension may be a good method but i have no experience with the extension) Let me know  if you are intrested in a detailed how to for downloading you video using the keepit website and i will write one for you.
2.Open mandvd, when mandvd asks for a video file select the downloaded video. (don't worry about the file type because the program will convert it for you.
3. if you get any other errors or you can't select the video you are trying to burn, post them here (because of proprietary video formats multimedia can be a bit tricky so there may be some other packages to install)

Mandvd will walk you through creating a menu and burning the dvd.

---

### Post by cherylholmes on 2008-05-20
Jeremy...libdvdcss2 isn't in my Synaptic.  Can I get it from someplace else?  Thanks! cheryl

---

### Post by _sAm_ on 2008-05-20
> **cherylholmes said:**
> Jeremy...libdvdcss2 isn't in my Synaptic.  Can I get it from someplace else?  Thanks! cheryl

You need to add the Medibuntu repos, you will find an easy howto here; [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by _sAm_ on 2008-05-20
> **cherylholmes said:**
> Hi,
How do I save a video this way to hard drive from a website like the TV channels or YouTube?

Thanks! cheryl

If you watch a video on youtube just go to /temp on your system - you will find the video there(just copy and save it in your home folder):)


Do any of you out there know if it is possible to copy a video from this site: [http://www.fabchannel.com/](http://www.fabchannel.com/) :confused:

---

### Post by cherylholmes on 2008-05-20
As usual..because nothing works for me, this didn't work either.  I'm not sure the mediubuntu is installed...and when i tried to do the install of libdvdcss2 it said dependency is unsatisfiable..whatever that means so i couldn't install it either...cheryl

---

### Post by _sAm_ on 2008-05-20
> **cherylholmes said:**
> As usual..because nothing works for me, this didn't work either.  I'm not sure the mediubuntu is installed...and when i tried to do the install of libdvdcss2 it said dependency is unsatisfiable..whatever that means so i couldn't install it either...cheryl
Check out this guide here; [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support) Did you do all it says?

---

### Post by cherylholmes on 2008-05-20
I was able to do the install using
[http://ubuntu-tutorials.com/2008/01/29/medibuntu-the-only-3rd-party-repo-i-use/](http://ubuntu-tutorials.com/2008/01/29/medibuntu-the-only-3rd-party-repo-i-use/).  So now I have the necessary things installed including the DVD playback.  cheryl

---

### Post by cherylholmes on 2008-05-20
and this one..cheryl
[http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/](http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/)

---

### Post by cherylholmes on 2008-05-21
KeepIt doesn't support Linux.:o(

---

