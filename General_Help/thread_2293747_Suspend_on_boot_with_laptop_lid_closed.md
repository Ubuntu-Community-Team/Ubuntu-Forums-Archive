---
title: "Suspend on boot with laptop lid closed"
date: 2015-09-07
forum: General Help
---

### Post by eddie28 on 2015-09-07
Hello. I am using a laptop *with a closed lid* as a remote media centre. When I remotely try to boot my Lubuntu laptop with a Wake-On-LAN packet, it boots and then immediately suspends. I need to send it a second packet for it to wake up and stay on. I have already adjusted the settings to make sure the laptop does nothing when the lid is closed, no suspending, no locking the screen, nothing. If, as a test, I try to boot it with the lid open then the first magic packet will turn on the computer and it will stay on without that initial suspension.

But I want the lid to stay closed. What can I do to make this happen?

I've read the following (unanswered) post on this subject matter. There were some interesting comments but unfortunately they did not work for me.: [http://askubuntu.com/questions/476151/laptop-goes-to-sleep-right-after-boot-with-lid-closed-and-external-monitor-conne](http://askubuntu.com/questions/476151/laptop-goes-to-sleep-right-after-boot-with-lid-closed-and-external-monitor-conne)

Many thanks in advance for any help you can offer!

---

### Post by Ben_Shaver on 2015-09-07
Under your monitor settings, do you have the display in the laptop disabled? I've had similar issues with a similar setup. :)

---

### Post by patlkli on 2015-09-07
So, did you try out the solution in [this Ask Ubuntu answer]("http://askubuntu.com/a/474357")?

---

### Post by Ben_Shaver on 2015-09-07
Ah, no, disabling the built in display fixed my issues...

---

### Post by eddie28 on 2015-09-10
Hello, sorry for the slow reply, for some reason I wasn't getting email notifications of your posts.

Changing logind.conf didn't work for me. What did end up working was to use a different program for sending the magic packet... weird? Maybe the new program I'm using (an android app called Wake On LAN) somehow registers that the computer's gone back to sleep on boot and sends it another packet immediately?? I don't understand... but I suppose if it aint broke...

---

### Post by eddie28 on 2015-11-23
Hello. Having said that I was happy with my "broken" solution, I have now accumulated enough annoyance for its nuances and unreliability that I'd like to get to the bottom of this. So, to recap:
- My original post still describes the problem correctly.
- I have tried disabling the "built-in" display under monitor settings - to no effect.
- I have tried the solution described at: [http://askubuntu.com/a/474357](http://askubuntu.com/a/474357) - to no effect.

Could someone please help me to diagnose and solve this?

---

### Post by tgalati4 on 2015-11-23
Take wire cutters and cut off the nib that pushes the lid switch.  Obviously, the lid switch is controlling the sleep behavior, ignoring it in software is not working, so it is probably controlled by the ACPI in BIOS.  Some computers use a magnet switch, so cut out the magnet.  That you will have to research. 

You are using a laptop in a manner it was not designed to be used--as a media server, with the lid closed.

---

### Post by eddie28 on 2015-11-24
Hmmm... I was worried it might come to that. Thanks for the advice! Here goes nothing...

---

### Post by eddie28 on 2016-02-03
Hello. I decided against working at the laptop with a set of pliers in the end and just tolerated it for a little longer. Then, yesterday I decided (for various other reasons) to delete Lubuntu and install Ubuntu 14.04.3 LTS. I had a go at [this solution]("http://askubuntu.com/questions/474352/system-logs-me-off-after-i-close-laptops-screen/474357#474357") (which as described in my original post did *not *work with my Lubuntu installation) and amazingly it works on this Ubuntu installation. Great! No idea what about Lubuntu means that this doesn't work there, but I'm happy it works now!

---

