---
title: "Keeping a Site Streaming to record"
date: 2020-02-06
forum: General Help
---

### Post by ehud2 on 2020-02-06
I'm in need of an idea. I've downloaded the Ubuntu recorder. The timer function works great but I'm having a problem. I need to record a program that starts at 8:30 but I leave the house around 5 AM. The recorder kicks on but the site is timing out way before the program comes on. Does anyone have an idea on how to keep the site from timing out due to inactivity? Thanks.

---

### Post by QIII on 2020-02-06
Hello!

What is the "Ubuntu recorder" and what are you trying to record?

---

### Post by ehud2 on 2020-02-08
[https://app.photobucket.com/u/strangerandapilgrim/p/8a758a30-61ba-4eed-b2a8-29e4d788c074](https://app.photobucket.com/u/strangerandapilgrim/p/8a758a30-61ba-4eed-b2a8-29e4d788c074) 

[https://hosting.photobucket.com/images/gg152/strangerandapilgrim/0/Screenshot%20from%202020-02-08%2009-42-01.png](https://hosting.photobucket.com/images/gg152/strangerandapilgrim/0/Screenshot%20from%202020-02-08%2009-42-01.png)

I guess Audio Recorder is the proper name for it. My wife's uncle in Pennsylvania has a radio broadcast Sunday mornings. I've been recording it in Audacity for quite a while and then uploading it to buzzsprout to share with folks on the internet (he's a pretty popular preacher in our circle). I know the obvious thing would be have him email it to me, but he is 81 and hasn't bothered learning the new technology. 
   My problem is I go to work around 5 AM. If I begin playing from the site and set the timer on the recorder the site times out because of inactivity.
  I know there's a program put out in the Ubuntu software hoard that keeps the desktop busy, but I don't know if that's what the site is looking at. Any suggestions?

---

### Post by ehud2 on 2020-02-08
I guess Photobucket has gotten greedy, but I'm sure you can still make out the program I'm talking about.

---

### Post by TheFu on 2020-02-08
Why not use **ffmpeg** or **wget** to grab it?  Start that task at a specific time for a specific duration using **at**/**cron** and **timeout** to end the ffmpeg capture.

I do something like I've described to record TV shows from some HD Homerun network TV tuners.  Works great.  Just need to know the URL in advance.

---

### Post by coffeecat on 2020-02-08
@ehud2, I reduced your enormous image to a hyperlink. Please be mindful of those with bandwidth restrictions, and those using a mobile device to browse the forum. If you want to include an image in your post, simpy use the paperclip icon in the message editor toolbar to open the attachment facility to upload your image. That way we see a clickable thumbnail.  

However, I see that you removed the image from Photobucket as I was editing your post. 

> **ehud2 said:**
> 
I guess Audio Recorder is the proper name for it.

Rather than guessing, please tell us the exact name of the application.


> **ehud2 said:**
> 
I guess Photobucket has gotten greedy, but I'm sure you can still make out the program I'm talking about. 

Whether or not Photobucket is greedy, as before, please use the attachment facility for images. And I surely couldn't make out the name of the program before you removed the image.

---

### Post by ehud2 on 2020-02-08
> **TheFu said:**
> Why not use **ffmpeg** or **wget** to grab it?  Start that task at a specific time for a specific duration using **at**/**cron** and **timeout** to end the ffmpeg capture.

I do something like I've described to record TV shows from some HD Homerun network TV tuners.  Works great.  Just need to know the URL in advance.

Thank you! I'll have to do a little digging to get all of this (I'm always rushed because of work), but I'm going to check this out. Thanks again!

---

### Post by TheFu on 2020-02-08
The script I use comes down to 1 line:
```
$TIMEOUT ${DUR}m wget -O "$TITLE-$DATE-$CH.ts"  $URL$CH$TRANS
```

There are about 30 lines above it to get the title, channel, duration, a little error checking, but not much  ...
```
CH="$1"   # digital channel 2.1, 2.2, etc...
DUR="$2"  # in minutes
TITLE="$3" # for the filename
DATE=$(date "+%F-%H%M%S")

cd /TV/Recordings

WGET=/usr/bin/wget
TIMEOUT=/usr/bin/timeout
FFMPEG=/usr/bin/ffmpeg

```
You get the idea.

The name is tv-record. To schedule a recording, 
```
echo "~/bin/tv-record.sh 46.1 66 60_Minutes-new" | at 18:57 sun 
```
That will record the TV show 60 Minutes for 66 minutes on Sunday.  Because of the way I'm lazy about parsing shell inputs, the title cannot have spaces.  If I used getops or quotes, spaces could work. I'm lazy.

---

