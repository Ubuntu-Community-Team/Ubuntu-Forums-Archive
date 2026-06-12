---
title: "Need help streaming webcam to be viewed via remote browser"
date: 2014-04-24
forum: General Help
---

### Post by jon43 on 2014-04-24
Hello all,

I've been using Kubuntu and Ubuntu on my machines for a while, and this is the one thing I've still been falling back onto Windows to let me do. I like to keep a webcam running on my home desktop for my fiance and I to check in on our pets during the day. Yawcam is awesome for this, and does exactly what I'd like it to. Since I have now removed Windows from the last box in the home (yay!) I need to find a Linux solution. 

I've tried VLC, but I must be getting something wrong or not understanding some part of the instructions, because it never seems to work. I can view the cam locally, but something falls apart in the streaming process. 

I've also tried to install Windows 7 in a virtualbox and run Yawcam that way, but I can't get the cam feed from the host machine to work. 

Does anyone have a solid solution they can offer to me, in detail? I'm okay with either approach. I have the system specs to run the virtual machine with ease, so maybe it'd be best to just tweak that config and use yawcam if possible? 

Thanks guys!

Jon

---

### Post by dragonfly41 on 2014-04-24
You could install red5 video streaming server on Ubuntu.

There is red5-server as a package to be installed through Ubuntu Software Centre .. or if you can install tomcat then Red5 is a webapp.

[color=maroon][later edit]

And this explains how to connect to camera ...
[http://support.jwplayer.com/customer/portal/questions/6062709-how-to-stream-live-to-red5-](http://support.jwplayer.com/customer/portal/questions/6062709-how-to-stream-live-to-red5-)

[/color]

---

### Post by jon43 on 2014-04-24
Thanks Dragonfly- I'll check that out when I get home this evening.

---

### Post by jon43 on 2014-04-25
Dragonfly,

I checked it out but I couldn't find it in software center. Then when I went looking for it on the download section of their website, there didn't seem to be a .deb file?

As a fallback I ended up getting virtualbox *almost* working, but hit a snag getting the streaming content outside of the virtual machine. Detail on that here: [http://ubuntuforums.org/showthread.php?t=2219540&p=13000912#post13000912](http://ubuntuforums.org/showthread.php?t=2219540&p=13000912#post13000912)

---

### Post by dragonfly41 on 2014-04-25
In my Ubuntu Software Centre (12.04 LTS) it is "red5-server"

---

