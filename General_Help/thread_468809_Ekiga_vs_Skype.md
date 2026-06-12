---
title: "Ekiga vs Skype"
date: 2007-06-09
forum: General Help
---

### Post by lamadredelsapo on 2007-06-09
Which one is best? I am used to Skype because it is what I had in Windows. Would anyone recommend ekiga over skype, or should I keep skype?

---

### Post by pickarooney on 2007-06-09
Skype is very buggy in Linux and constantly causes system freezes if you're logged in for a while and someone calls you. Development seems to have been frozen on version 1.3.*
However, as everyone else I know uses Skype and I can't get Ekiga to work properly (or wengaphone, or Gizmo...) it's the best of a bad lot.

*edit - spoke too soon, seems there's a 1.4 alpha version available since end of May!

---

### Post by mifi on 2007-06-09
> **pickarooney said:**
> Skype is very buggy in Linux and constantly causes system freezes if you're logged in for a while and someone calls you. Development seems to have been frozen on version 1.3.*
Not my experiences at all. I am running 1.3.0.53_API without any difficulties. on two machines with Ubuntu 7.04.
> **pickarooney said:**
> 
However, as everyone else I know uses Skype and I can't get Ekiga to work properly (or wengaphone, or Gizmo...) it's the best of a bad lot.

It depends on who you want to call. Skype does not use the open standard communication. Skype clients can only talk to other Skype client, because the protocol is proprietary.

mifi

---

### Post by trippinnik on 2007-06-09
Yeah, skype has worked well for me as well.  I haven't tried Ekiga cause I don't know anyone who has it.  I was also using the alpha build of skype 1.4 it actually seemed pretty good.

---

### Post by highenergy on 2007-06-09
Hi,
I have to questions.

 1- Does Skype supports video conferencing under Linux? Many of my friends uses Skype under Windows. I want to able to make video conferencing with them.

 2- Is Ekiga available under Windows? If so can two Ekiga users one under Windows and the other under Linux do video conferencing? 


regards

---

### Post by drpaul on 2007-06-09
Skype doesn't support video for Linux yet.

Ekiga seems to have video working, but I haven't tried it [can't convince the people to whom I talk to install it]. I think there is a version for Windows.

Paul

---

### Post by ramjet_1953 on 2007-06-09
Skype works fine on my system and voice quality has been the same as Windows.

If you require the ability to call landlines, you have only two options:

1. Skype

2. WangoPhone

WangoPhone does have video and encrypted call abilities.

The problem with it may be just convincing your friends to change over from Skype, so that you can call them..

Regards,
Roger :cool:

---

### Post by YannickDefais on 2007-07-25
Hi,

Skype is proprietary protocol, thus to call PC-to-PC you can only use skype. No compatibility at all.

Ekiga uses the standard VoIP SIP protocol, thus it has a huge compatibility list compared with Skype:
[Which programs work with Ekiga ?]("http://wiki.ekiga.org/index.php/Which_programs_work_with_Ekiga_%3F") All calls from PC-to-PC are free.

Ekiga can register to almost any SIP provider (including Wengo and Gizmo), the rates for landline or mobile phones are generaly cheaper than Skype:
see this SIP price chart (ekiga):
[http://backsla.sh/betamax](http://backsla.sh/betamax)
and compare with Skype:
[http://www.skype.com/intl/en/products/skypeout/rates/all_rates.html](http://www.skype.com/intl/en/products/skypeout/rates/all_rates.html)

Ekiga has video and under windows XP you should have Windows Messenger (5.1) which has full compatibility (text+audio+video).

Ekiga has a much better documentation in Ubuntu:
[https://help.ubuntu.com/community/Ekiga](https://help.ubuntu.com/community/Ekiga) (heh)

Make your choice ;)

Regards,
Yannick

---

### Post by Crafty Kisses on 2007-07-25
> **lamadredelsapo said:**
> Which one is best? I am used to Skype because it is what I had in Windows. Would anyone recommend ekiga over skype, or should I keep skype?

I'd probably keep Skype, but that's just me.

---

### Post by kc5hwb on 2007-11-10
> **ramjet_1953 said:**
> Skype works fine on my system and voice quality has been the same as Windows.

If you require the ability to call landlines, you have only two options:

1. Skype

2. WangoPhone

WangoPhone does have video and encrypted call abilities.

The problem with it may be just convincing your friends to change over from Skype, so that you can call them..

Regards,
Roger :cool:


Incorrect.  You can setup Ekiga to use a voipstunt account, which allows free land-line calls anywhere.  The only catch is that you have to download and install voipstunt on a Windows box to setup your account.  But once you have it setup, you never need to launch voipstunt again, you just enter the settings into Ekiga and use it to call any landline for free, thru VS.

---

### Post by por100pre1 on 2007-11-10
> **kc5hwb said:**
> Incorrect.  You can setup Ekiga to use a voipstunt account, which allows free land-line calls anywhere.  The only catch is that you have to download and install voipstunt on a Windows box to setup your account.  But once you have it setup, you never need to launch voipstunt again, you just enter the settings into Ekiga and use it to call any landline for free, thru VS.

Yes. Ekiga, being a [SIP]("http://en.wikipedia.org/wiki/Session_Initiation_Protocol") VOIP client, can be used with many VOIP services. Once you have the SIP proxy login information you can setup Ekiga to the proxy and you are good to go. :)

---

### Post by janne_oksanen on 2007-11-19
As a quick update I'd like to mention that Skype 2.0 beta has been released for Linux and it now supports video. I've been using it since it was released and I've had no problems of any kind with it. I also tested ekiga for conference calls the other night and it doesn't seem to suppord video for those. At least for me is was audio-only. I was using the free conference rooms provided by ekiga.net (sip:501####@ekiga.net) and none of my mates could see my video stream. Ekiga also now has a default PC-to-Phone service provider and the rates for the numbers I call (Finland mobile) were some 30% cheaper than with Skype, but stii twice as much as with my cell phone. Tonight I'm going to try ekiga with my brother who has XP to see how it works in Windows. Ekiga looks very good for the price, but I still don't quite like the GUI. The keypad is ugly and huge and there's no live buddy list like with Skype and all the IM clients where you could see who's online and just click on it to call that person. I also had a crack at Wango the other day. I looks very good, but I wasn't able to get sound working so I had to give up on it for now. There were a lot of ppl in the forums with the same problem so I only assume it'll get fixed soon.

---

### Post by mahousaru on 2007-11-19
On my Celeron 1.5 I actually find that Ekiga gets very tinny if I talk too fast, whilst Skype is fine on it.  It is even fine with the video as well.  On my main Ubuntu P4 I use both.

---

### Post by aitorcalero on 2007-11-19
I would recommend Skype, because it is widely used and now verion 1.4 works fine in Ubuntu. Version 2.0 wil support video also.
It is almost impossible try to convince all my skype friends switch to Ekiga. Also Ekiga skin in Windows is pretty ugly.

---

### Post by stulesnett on 2008-03-15
I have tried both the Linux and Windows version of both applications.  I have used SKYPE for 2.5 years on MS.  The SKYPE Linux 7.10 UBUNTU product doesn't not seem ready, especially in the video area.  I have recommended SKYPE many times.

I have returned back to the Linux world and with the release of Ubuntu 7.10 found Ekiga.  I must say that EKIGA's lacks some basics in the documentation arena.  The support community does leave somethings unanswered question but with their assistance I have gotten my linux system up and used their diamondcard service for PC- to-phone service and it works.  I have not been able to get the quad windows user segment working but I keep trying.  I have 2 Linux Desktop with identical webcams and Ekiga selected 2 different driver systems which was a shock.

The window version on XP seem to run very well.  In fact, I have sent to the developers messages concerning myself and other users that have reported problems with 500 & 501 " security check failed" message received.  When the developer stated that it seems to be working for me that he MUST using the windows version which by the was working not the linux version.

I think Ekiga could develop into a superior product but it does need work and less developer attitude.  I would recommend it but only for a computer literate person.:)

---

### Post by YannickDefais on 2008-03-17
> **stulesnett said:**
> (...)
I have returned back to the Linux world and with the release of Ubuntu 7.10 found Ekiga.  I must say that EKIGA's lacks some basics in the documentation arena. 
Can you give the point you think need more documentation? I'm responsible for this part of the project.

> 
(...)
 I have 2 Linux Desktop with identical webcams and Ekiga selected 2 different driver systems which was a shock.
Is it V4L and V4L2 ? If it is, some webcams works with both API (it depends on the driver).

> 
(...)
The window version on XP seem to run very well.  In fact, I have sent to the developers messages concerning myself and other users that have reported problems with 500 & 501 " security check failed" message received.  When the developer stated that it seems to be working for me that he MUST using the windows version which by the was working not the linux version.

I think you misunderstood it:
Damien said: "Unfortunately, the Windows version is not well maintained :(" That means the windows version should be worst (if any) than the Linux version. It think the problem you experienced is also a configuration problem (STUN maybe? or temporary network issue). The Linux version is way more tested than the windows version. Beside, the code base is almost the same between both.

Regards,
Yannick

---

### Post by dboot on 2008-03-17
I've never used either but [Skype 2.0]("http://www.skype.com/download/skype/linux/") has been release for Linux with free video calling.

---

### Post by stulesnett on 2008-03-17
Hi YannickDefais,

Lets take the easy ones first.

The issue with the 2 different systems is EKIGA selection of webcam drivers FLEXCAM 100 (my general system) and something called PIXART for (my work system) both systems have the same webcams and currently are running Ubuntu 7.10 with all the UBUNTU updates.

I did understand what Damien was saying about MS WINDOWS VERSION but to date both of my Linux systems,e.i.Ekiga, seem to experience more problems than the Windows system under XP Pro.(laptop). 

Damien continued replies send things (problem and comments) to the mailing list?? which mailing list (the ekiga, gnome,ubuntu,etc.).

He then states that one must use (ekiga -d 4 > 0utput >2&D1) which by the way is in one of the pieces of documentation in one of the publication and when one does use, oh on UBUNTU you must some kind of trace like ptrace but I can't recall it's name.. and still resolution.

There are different pieces of documentation all over the place concerning Ekiga but NO central place, some examples UBUNTU installation, oh Ekiga possible for a user manual and which one of the lists??.

thanks for responding.

 (Oh by the way both my Linux systems are still failing with security check failures, Damien say they have fixed that problem.)

---

### Post by YannickDefais on 2008-03-19
Hi,

The documentation is here:
[http://wiki.ekiga.org/](http://wiki.ekiga.org/)

the part for debugging is here:
[http://wiki.ekiga.org/index.php/Debugging_Ekiga](http://wiki.ekiga.org/index.php/Debugging_Ekiga)

and the command you look for is:
[http://wiki.ekiga.org/index.php/Debugging_Ekiga#How_to_get_a_debug_output_from_Ekiga](http://wiki.ekiga.org/index.php/Debugging_Ekiga#How_to_get_a_debug_output_from_Ekiga)

I dont understand what exactly the problem with webcam is...

Are you using STUN with Ekiga  (in prefs) under Linux?

Regards,
Yannick

---

### Post by stulesnett on 2008-03-24
Yes, I am using STUN

---

### Post by rosros-3 on 2008-03-27
After getting "security check failed"  with all my calls to sip:+XXXXXXXXXXX@sip.vopstunt.com:5060,
I have removed the ":5060". Now ekiga works again with my voipstunt account.
HTH
rosros

---

### Post by ilanesh on 2008-04-04
Hi all, I use Ekiga over skype, even the skype video who they call stabe now, is so buggy it is freezing the system and demaging the installed distr,
I don`t no what is this screeming about skype always, oncle bill is watching you what yo uare doing, it is not secure at all, takes lots of bandwidth,
ekiga works perfect on Linux Mint who is based on ubuntu 7.10. video and sound good, I do my completely free pc to phone calls from it using voipuser,
ekiga to ekiga voice video calls, no problems with freezing the system, easy to use, and all of my sip clients login without any single problem,
I say, "skype go home"
on windows xp I use ooVoo, who is a thousand times better then skype, and soon we will have also oovoo for linux they work on a linux version.
oovoo is a voice video software.
as to use skype for pc to phone calls, this is ridiculous, they are so expensive, I even can call for lots more cheaper from phone to phone then from skype to phone, i used it twice for pc2phone this skype and it was too expensive for me, and also many people are frustraited with it cause theyir account on skype was stolen and they had paid outgoing calls and could not use it anymore and skype never ever rgave their money and account back.
also so many people have problems with skype, and when posting on the forum there, there is barely ever an answer, and when sending email to them hey never receive response, com on guys, they don`t care for their costumers, there are wide more better softphones out there.
I stick from now on with ekige and thats it.

---

