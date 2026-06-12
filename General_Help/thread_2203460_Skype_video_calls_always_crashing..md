---
title: "Skype video calls always crashing."
date: 2014-02-03
forum: General Help
---

### Post by d4m1r on 2014-02-03
Hey guys, I've been having this problem with Skype for MONTHS so other people must have to....Basically, Skype crashes 100% when doing a video-to-video call. Sometimes within 1min sometimes after 3-4min. Audio only calls and if Skype is only active in the background don't make it crash. Apparently in the older version than the current available on Skype.com, many many people had this problem and it was related to a dependency problem in 12.04 and 13.04. I was hoping the most recent update/release would therefore fix it, and it did fix that issue but now Skype is crashing because of a new bug;

"Skype crashed with sigabrt in raise()"

[IMG]http://i.imgur.com/OdzJ3uC.png[/IMG]


Anyone know wtf is going on with Skype or how to fix this?!? Skype version 4.2.0.13 under Ubuntu 12.04 LTS (x64).

---

### Post by d4m1r on 2014-02-04
Nobody elses Skype is crashing like this? :-?

---

### Post by kschiff on 2014-02-05
I'm having similar issue on 13.10 w/4.2.0.13 Video calls randomly crash... I can be going for 30+ minutes sometimes and then it just dies. I just tried some of the settings suggested in this thread to see whether they help (can't report yet)...

[http://community.skype.com/t5/Linux/Skype-4-0-on-Ubuntu-12-04-crashes-and-logs-me-out/td-p/818438](http://community.skype.com/t5/Linux/Skype-4-0-on-Ubuntu-12-04-crashes-and-logs-me-out/td-p/818438)

---

### Post by d4m1r on 2014-02-05
That is an older thread but let me know if it helps any....Are you getting a similar error or?

---

### Post by kschiff on 2014-02-05
I haven't been recording the crashes or looking at the logs as they occur, but will pay attention next time. It's intermittent for me... I can keep a video call going for a while, but then it will die.

---

### Post by ortermagic on 2014-02-15
I have exactly the same problem with skype crashing and have been trying for the past two weeks to find a solution.
Sorry I can't help but I thought I would register solidarity with you. I have loaded mint in case it was ubuntu based but it still happens there. I've trawled all over the internet for a cure,
I have tried every offered solution I can find. I've now set up a google hangouts account (all I have to do now is persuede all my contacts to do likewise)

---

### Post by d4m1r on 2014-02-15
Seems like there are plenty of us out there with this problem even with the newest released version but still no solution :(

Mint will most likely have the same problem because it is based on Ubuntu. FYI, I have made a few configuration changes to skype that apparently might be the caused based on my crashlog so I'll report back if it is anymore stable after I give it a whirl again...

---

### Post by ortermagic on 2014-02-15
Thankyou any advice or help would be appreciated...

---

### Post by d4m1r on 2014-02-15
FINALLY....seems like I have solved this issue (largely). I was on a 5min video to video call and it crashed with a new error message. Seems like a dependency issue again like in the previous version which was supposedly fixed in this new version but isn't (error: package not installed) BUT I launched it again and **for the first time since installing 12.04**, I was able to have a normal video to video chat on skype for more than 2-3min....Mine actually lasted 1.5 hours and did not crash :D

How?

1) install [pulseaudio volume control]("https://apps.ubuntu.com/cat/applications/pavucontrol/") package

2) skype > options > sound devices > set everything to pulseaudio server (local) and then make a test call to make sure your audio is working

3) uncheck "allow skype to automatically adjust my mixer levels"

4) skype > options > video devices > uncheck "disable auto exposure"

Hopefully it works for others as well if they are experiencing the same issue.

---

### Post by ortermagic on 2014-02-17
If that (#9) worked for you d4m1r then we have different problems. 
 I have tried all your suggested solutions many times over the past few weeks.
It simply isnt that easy, my solution, when I need to comunicate with my son in Canada  has been to convert to Google Hangouts, which actually works.
It's a bit of a drag doing it that way tho because Google make you jump through hoops and want you to load stuff onto their database (for supposedly commercial reasons) but it works.
You can have several contacts on one video call which is novel. I will try Skype again later when it's fixed, hangouts will have to suffice in the meantime...maybe I will get to like it even.

---

### Post by d4m1r on 2014-02-18
Well that is was fixed it for me, so I guess the root of your issues is different from my own....

Does it give you any errors when it crashes? Are you using a Logitech USB webcam by any chance?

---

### Post by ortermagic on 2014-02-22
Yes I am using a logitech usb web cam but it works with cheese and google hang outs (tho i am not really too keen on google hangouts)

---

### Post by d4m1r on 2014-02-22
I am 90% sure this issue is caused by using Skype with a Logitech USB webcam.....Watch the "on" light while on a Skype call, it will blink off and on randomly while on the call and it usually stays off for a longer period of time before Skype crashes.

It did in my case atleast and I don't think both of using a Logitech USB webcam is a coincidence....

---

### Post by ortermagic on 2014-02-22
Thanks for the input, I have just reinstalled 12.04 on my spare hdd so I will try skype on that once i have got around to installing it, I am hoping the issue is down to using saucy or trusty on the other hd.

---

### Post by ortermagic on 2014-02-22
Well I have installed skype again from the skype website (linux 64 12.04 precise) loaded it through the software centre, got a crash after 3 minutes usage, sent in a crash report to cannonical via the crash popup it seem it's already logged as a bug, cant find the crash report at the moment.

---

### Post by d4m1r on 2014-02-22
> **ortermagic said:**
> Thanks for the input, I have just reinstalled 12.04 on my spare hdd so I will try skype on that once i have got around to installing it, I am hoping the issue is down to using saucy or trusty on the other hd.

My theory is the HDD/version of Ubuntu won't matter and your Skype video calls with still crash if using the Logitech USB webcam but try and let us know :)

---

### Post by ortermagic on 2014-02-22
Out of curiosity, what inexpensive web cam do you think I should buy?
Oh I have just found a possible way out of this using this tutorial found on a mint forum, I dont know if it will work but next time I skype my son in Canada will find out

[http://community.linuxmint.com/tutorial/view/219](http://community.linuxmint.com/tutorial/view/219)

---

### Post by d4m1r on 2014-02-22
> **ortermagic said:**
> Out of curiosity, what inexpensive web cam do you think I should buy?

Even after all this...I still normally recommend Logitech. If you want to try another brand, Microsoft actually make decent and cheap webcams (lifecams?) too but no idea if they are supported under Ubuntu...

---

### Post by ortermagic on 2014-02-23
I went out and bought a new microsoft webcam (life-cam hd 3000) and still no joy. Fed up with it now.

---

### Post by d4m1r on 2014-02-23
> **ortermagic said:**
> I went out and bought a new microsoft webcam (life-cam hd 3000) and still no joy. Fed up with it now.

Sucks to hear....Do you have the same light problem I described with your Logitech webcam under Ubuntu?

I too got tired pretty quickly of having to boot into Windows 7 just to use Skype.

---

### Post by ortermagic on 2014-02-24
Update... Yesterday I reformatted the 12.04 drive (only because I had lost track with all the adjustments i'd made using the terminal) Then on my other hd I tried to skype using the 13.04 installation and the new webcam, got the same quiet shutdown effect.
 However the good news is that undeterred I restarted and grubbed into my 13.10/14.04 (hybrid) install and lo and behold Skype worked, and I was able to maintain an hour long communication, I don't know why, but at the present time all's well. I will be running an update later just hoping that I wont have a relapse.
 As for your question about the light on the logitec camera I cant really say whether the light was on or not since I was never aware of it, perhaps it was off. My problem may well have been a faulty cam, coupled to my increasingly desperate attempts to get it going using web gleaned terminal cures that might have caused conflicts.
I will try out skype again later today when my son logs on in Ontario, hopefully it will still work.

---

### Post by ortermagic on 2014-03-03
I have just discovered by accident that in my case Skype would not work when using the fglrx driver, I swapped over to the xorg driver and everything works as it should.
It would have saved me hours if I had looked at that in the first place (so maybe there's a glitch in fglrx).

---

