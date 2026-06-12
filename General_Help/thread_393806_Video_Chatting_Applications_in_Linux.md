---
title: "Video Chatting Applications in Linux"
date: 2007-03-26
forum: General Help
---

### Post by groovomata on 2007-03-26
Hello Linux people:
I love using unbuntu, however in the area of video chatting applications, it still seems to be deficient to Windows. Unfortunately, for me, this is critical as I live in Brazil and most of my friends and family are in Canada and video chatting is a great way to keep in contact. However, if I can, I'd love to get rid of my Windows partition.
I was wondering, what the best video chatting applications are in Linux? Which ones are cross platform with Windows? Most importantly, which ones can connect to the main msn, skype and yahoo networks?
Thanks, and all the best,
Erik.

---

### Post by louis_nichols on 2007-03-26
Well. For skype there's... skype. :) Unfortunatelly it doesn't have video support.

Kopete has good support for webcams in yahoo and MSN. I only tested yahoo and was very pleased, so I can;t say about MSN's quality.

There's also Ekiga, said to work with windows messenger, but I was never able to make that work.

For yahoo there's also [gyache]("http://www.phrozensmoke.com/projects/pyvoicechat/"), with webcam, voice AND audibles support.

There are others for msn too, but I can't remember them right now.

---

### Post by rolando2424 on 2007-03-26
Amsn also allows you to use the Webcam, but it doesn't have sound support (I think it does in a new version they're working :D).

Wasn't there a Gaim project that aimed at creating video and audio support for Gaim?

---

### Post by louis_nichols on 2007-03-26
> **rolando2424 said:**
> Wasn't there a Gaim project that aimed at creating video and audio support for Gaim?

Yes, there was gaim-vv, but development on it has been stopped. Last time I saw their homepage (maybe more than a year ago), it said the functionalities will be incorporated into gaim, but I haven't seen any news on this on the official gaim site.

---

### Post by shamrock_uk on 2007-05-06
Kopete works fine with msn. Also Feisty was the first distro to recognise my webcam (thanks guys!). The light level is much lower than with windows (yes, even after changing settings etc) but I can't really complain :)

The only thing to watch out for is it took several tries of 'send webcam' until it took.

---

### Post by groovomata on 2007-05-06
I successfully video chatted with a windows computer using amsn for video and skype for sound.
Erik.

---

### Post by groovomata on 2007-08-02
Hello Linux People again!
I'm returning back to Canada from Brazil in late August and will need a video chatting option to communicate with people in Brazil. I would really prefer to buy one of those Dell Laptops (if they're available) however it all depends on a simple solution that my wife, a windows user, can understand. I did succeed in video chatting amsn to MSN using skype for sound, but was never able to do it again. I'm going to try Kopete, however I was wondering if anyone else knows of a simple and reliable video chatting solution between linux and windows computers?
Thanks,
Erik.

---

### Post by louis_nichols on 2007-08-03
> **groovomata said:**
> Hello Linux People again!
I'm returning back to Canada from Brazil in late August and will need a video chatting option to communicate with people in Brazil. I would really prefer to buy one of those Dell Laptops (if they're available) however it all depends on a simple solution that my wife, a windows user, can understand. I did succeed in video chatting amsn to MSN using skype for sound, but was never able to do it again. I'm going to try Kopete, however I was wondering if anyone else knows of a simple and reliable video chatting solution between linux and windows computers?
Thanks,
Erik.

Did you try ekiga? I think if you google a little bit, you'll find some howto's about pairing it with Windows Messenger.

---

### Post by YannickDefais on 2007-08-03
Hi,

Ekiga was build for audio and video chat, since 6 years now. Ekiga only use industry standards (SIP and H.323), thus is highly compatible.

Check the documentation for more infos:
[https://help.ubuntu.com/community/Ekiga](https://help.ubuntu.com/community/Ekiga)

Regards,
Yannick

---

### Post by groovomata on 2007-08-03
I'd had problems in the past trying to get ekiga with NAT problems and have never successfully management to video chat with anything other than another ekiga client. I've got Wengophone 2.1.1 installed from this page (about halfway down).
[http://dev.openwengo.com/trac/openwengo/trac.cgi/wiki](http://dev.openwengo.com/trac/openwengo/trac.cgi/wiki)
I'm going to try this for now to see how it works.
Thanks!
Erik

---

### Post by physx on 2007-08-04
One option you might want to look into is OpenWengo -- GPL and has clients for both Windows and Linux (and OS X, if you'd need it).  I haven't used it myself, but it says that it supports video, and might be helpful...

Here's a link:

[http://www.openwengo.org/](http://www.openwengo.org/)

---

### Post by groovomata on 2007-08-04
That's exactly what I'm going to try. Right now I'm in Brazil and I'm going to do a test with my brother in Canada. With him on his windows computer we'll try to video chat with msn, yahoo and wengo itself and see what works. 
Thanks,
Erik.

---

### Post by groovomata on 2007-08-04
Well, I tried to video chat with wengo and we could see each other, however we couldn't hear each other. Wengophone only video chats with other wengophones, so you can only text chat with yahoo and msn. I also was unable to audio chat with skype so I clearly have a sound problem. I can play sounds on my computer, I hear sounds on skype and wengo (i.e. the logon sound, and call ringing sound) so wengo and skype for some reason cannot properly access the sound architecture of my computer to for audio chat. 
The properties of my sound volume icon says that I'm using Alsa Mixer. 
My question is, how can I troubleshoot sound problems like this in linux?
Thanks,
Erik.

---

### Post by groovomata on 2007-08-05
Well, I was able to video chat Wengo to Wengo with my brother using his windows computer but with no sound. I'm able to configure sound properly for skype to audio chat, and Ekiga seems fine too, but I cannot get sound to work with Wengo. I checked the forums and there are lots of problems with this. I even tried an alternative build of Wengo which is supposed to fix the problem but to no avail. 

Okay onwards to Ekiga. My brother is going to install the Ekiga for windows client and register himself on ekiga.net and we're going to give this a try!
I'll post our successes and failures as I strive to find a way video chat (with sound) for linux. There has got to be a way!
Cheers,
Erik.

---

### Post by YannickDefais on 2007-08-05
Hi,

Maybe this would help:
[Ekiga documentation](https://help.ubuntu.com/community/Ekiga)

Regards,
Yannick

---

### Post by groovomata on 2007-08-05
Thanks! Well to sum up my latest little adventure in the world of linux video chatting, I've discovered that Wengo worked well with another Wengo client for video but I was not able to get any audio to work with the linux versions I tried (frustrating because my brother who has Windows XP got audio to work, no problem, on his Wengo). AMSN is able to video chat well with MSN however there is currently no audio support either. My brother, who has Windows XP, also tried to install Ekiga (there is a Windows version), but it would not install. Skype, though, worked fine for me to do audio chat. So if you're chatting with someone who has a windows computer your best bet is with Skype for audio and aMSN for the video part. If the other computer has Wengo then it can provide the video part of the chat. This combination, while not totally elegant, seems to work well.
All the best,
Erik.

---

### Post by YannickDefais on 2007-08-06
Hi,

[Ekiga compatibility with other softwares on various platforms]("https://help.ubuntu.com/community/Ekiga#head-dc65c307f0ece892c8dda9784ff5f0f1bb2094e9")

[How to connect Windows Messenger 5.1 (shipped with XP) to Ekiga.net?]("http://wiki.ekiga.org/index.php/Connecting_Windows_Messenger_5.1_to_ekiga.net")

Regards,
Yannick

---

### Post by tashmooclam on 2007-09-06
I want to do the same thing with several family members. 
I wish there were something in Linux that worked. For that matter, I wish I knew which webcams worked for Linux. Mine doesn't. The Dell laptops don't have one.
Wait seems to be the only answer for now.
Good luck and keep posting about Wengophone, I want to try it too anyway.

---

### Post by YannickDefais on 2007-09-06
Hi,

Here is a list of webcams that proved to work with Ekiga:
[http://wiki.ekiga.org/index.php/Tested_hardware](http://wiki.ekiga.org/index.php/Tested_hardware)

Regards,
Yannick

---

