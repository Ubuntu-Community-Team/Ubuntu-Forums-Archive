---
title: "Skype 1.3 out of beta"
date: 2006-10-06
forum: General Help
---

### Post by xinix on 2006-10-06
Skype 1.3 is out of beta. Has anyone tried it?

---

### Post by jeremy on 2006-10-06
No, and I am not about to, there is wengophone 2.0 also just out of beta, and FOSS!

---

### Post by ronmarley1 on 2006-10-06
> **xinix said:**
> Skype 1.3 is out of beta. Has anyone tried it?
I'm running version 1.3.0.50.  It starts MUCH faster than the previous version.  It used to take about 1 minute to load and login, and now it's about 5 seconds.  I've just played a bit, but here's a few other things I've noticed:
There's a Skype Test Call contact.  You call it, record a message, and then it's played back to you.  Great for testing.
It looks like they've added the conference call feature to the Linux version, but I have not tested it.
The interface is much cleaner.
It detected ALSA on it's own and runs fine so far.

---

### Post by marianom on 2006-10-06
I'm currently using the new version (1.3.0.53_API). Installed yesterday (I have a lot of segmentation faults issues with lower versions).
So far so good. However I did not fully test it.

If I encounter any problem I let you know.

---

### Post by xinix on 2006-10-06
> **jeremy said:**
> No, and I am not about to, there is wengophone 2.0 also just out of beta, and FOSS!
Good for you.  On the other hand Wengophone rates to the country I call the most don't compare to the ones I can get through Skype.

---

### Post by beercz on 2006-10-06
The new Skype (version 1.3) works fine for me :-)

---

### Post by oskarloko on 2006-10-08
Ok, works fine, good sounf support (ALSA-OSS) :)
No webcam support :(.

Yes, OpenWengo 2.0 is FOSS and supports video call Pc-Pc
But it works a little 'bad'
And I L:KS VE wengo efforts to make such a program... to Linux, Winxxx, Macxxx, and FireFox

---

### Post by arkangel on 2006-10-08
it works fine ,  the startup is faster

---

### Post by KhaaL on 2006-10-08
it works if i run it in OSS, but not through ALSA...

I wrote about the problem here and I haven't recieved any help yet (hint hint ;) )

---

### Post by marianom on 2006-10-08
I suggest trying in the Skype forums ([http://forum.skype.com/index.php?act=idx)](http://forum.skype.com/index.php?act=idx)). The develop guys are there and might help you.

---

### Post by LORD_PoLvO on 2006-10-08
i dont use skype yet lol i might give it a try :D

---

### Post by frodon on 2006-10-09
I have a really bad experience with skype 1.3, it introduces an horrible general freeze bug which seems to affect only ubuntu :
[https://launchpad.net/distros/ubuntu/+bug/58194](https://launchpad.net/distros/ubuntu/+bug/58194)

Please comment the bug report if you have the problem.

My personnal advice is to not use skype 1.3 but it's just my feeling.

---

### Post by marianom on 2006-10-09
Since I'm also with this problem I reported as suggested. (It happened with all 1.3 releases)

I'm too experiencing these issues: 1) random "segmentation faults", mainly when I leave my machine unattended for a few minutes. 2) people I call can listen to my voice but they also listen their own voices (sometimes louder than mine). I tried to configure it with the volume control ("Capture" tab") with no luck.

---

### Post by wieman01 on 2006-10-10
> **marianom said:**
> Since I'm also with this problem I reported as suggested. (It happened with all 1.3 releases)

I'm too experiencing these issues: 1) random "segmentation faults", mainly when I leave my machine unattended for a few minutes. 2) people I call can listen to my voice but they also listen their own voices (sometimes louder than mine). I tried to configure it with the volume control ("Capture" tab") with no luck.
Lovely. Same here. These developers deserve a kick in the b@#! What a waste of time, really annoying. They should do their homework and not waste other people's time. Frustrating.

---

### Post by marianom on 2006-10-10
I was told that this kind of error would be fixed with the new 1.3 release and alsa device, here:
[http://forum.skype.com/index.php?showtopic=65500](http://forum.skype.com/index.php?showtopic=65500)

But I'm still with that error which I reported again in the forums to see if somebody can help me:
[http://forum.skype.com/index.php?showtopic=65957](http://forum.skype.com/index.php?showtopic=65957)

So far, no luck. I really need it so I'll keep searching for a solution.

If I find something, I let you know.

---

### Post by wieman01 on 2006-10-10
> **marianom said:**
> I was told that this kind of error would be fixed with the new 1.3 release and alsa device, here:
[http://forum.skype.com/index.php?showtopic=65500](http://forum.skype.com/index.php?showtopic=65500)

But I'm still with that error which I reported again in the forums to see if somebody can help me:
[http://forum.skype.com/index.php?showtopic=65957](http://forum.skype.com/index.php?showtopic=65957)

So far, no luck. I really need it so I'll keep searching for a solution.

If I find something, I let you know.
Appreciate that. My problem is that I stop hearing the other party after a few minutes on the phone although they can hear me clearly.

---

### Post by bignickel on 2006-10-10
I like the faster loading, and the resolved sound issues, but I find that when I make a SkypeOut call, there's a delay of a second or two at the beginning of a call where I can hear the person I'm calling, but they can't hear me.  It wasn't present in the previous version, but it was in the beta, so I reverted.  Then apt-get updated me and the problem's still there.  It might be worth living with for the benefits that 1.3 brings though.

---

### Post by marianom on 2006-10-10
Hi there. It seems that my echo problem is fixed. Tested it for more than 30 minutes: I talked with this guy for more than 10 minutes without a problem. I then started a conference call with another one and it was ok. 

The problem seems to be that on volume control, "capture" tab, the capture equilizer was, by itself, all the way up. While I was talking I pushed it down and after a few seconds it was again at the max level. 
It's supposed that Skype should control the correct level but I cant' tell you why it persisted in stablishing it in the max.

I did the following changes during this day (I cannot tell you which one make the trick because I was trying to fix the horrible segmentation fault error and was not checking the volume control):
1- Uninstalled-installed alsa 1.0.10
2- Upgraded alsa to 1.0.12 (although I cannot be sure if it's installed since I cannot see it in Synaptic)
3- Completely removed Skype and reinstalled it.

Now the capture equilizer is ok (aprox. at 30%) and I don't need to touch it in order it stays there.

wieman01/ bignickel I suggest you the following: make a call and keep an eye on the volume control to see if you can verify a modification during the call to see if your problem is similar to mine.

---

### Post by wieman01 on 2006-10-10
Hello Marianom, 

Will test this tonight. Unluckily reinstalling ALSA is not an option for me. Reason is that "Voice over Bluetooth" won't work with the stand-alone version of ALSA, only the one that comes with the kernel. Anyway I'll keep an eye on the setting while I make phone calls tonight.

---

### Post by lodp on 2006-10-19
i've also got the freezing problem when a message/call comes in -- but i just read that disabling animated emoticons and/or incoming message sound might help... i'll give it a try and report back...

---

### Post by marianom on 2006-10-19
It does not, at least for me, I've them disabled since ever and the freeze still happens.
There is a problem in the kernel and that's it. Until somebody fix it, we'll have to deal with it.
Devs tried to contact skype devs (see: [http://forum.skype.com/index.php?showtopic=66241](http://forum.skype.com/index.php?showtopic=66241)) but I guess the communication died before even start. 

For more info see: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/53216](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/53216)
What's worse and you can read it in the report is that this kind of problem can generate a potencial DoS in our machines. IMHO, this should be treat as a security vulnerability.

---

