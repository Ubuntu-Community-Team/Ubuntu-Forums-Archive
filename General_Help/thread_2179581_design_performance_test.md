---
title: "design performance test"
date: 2013-10-08
forum: General Help
---

### Post by lastlion on 2013-10-08
What's up.

My dad built this machine as a first time builder to run Windows 7.  He said it kept locking up and crashing and he sent it in for diagnostics/repairs once.  His conclusion was that "it's the motherboard" which I don't buy but the reviews suggest ASUS was hit and miss with this one.  Mostly hit though.

[TABLE="width: 746"]
[TR]
[TD="width: 25, align: center"][/TD]
[TD="width: 130, align: left"]A455-2881[/TD]
[TD="align: left"]ASUS M4A785-M Motherboard - AMD 785G Socket, AM2+, MicroATX, HDMI, USB 2.0, PCIe[/TD]
[/TR]
[/TABLE]

Anyway, I have it now and I installed Ubuntu and I've left it on for several days without issue.  I have performed some rudimentary tests (performance and such) and nothing is obvious.  But I'd like to do extended performance testing to push it.   It could very well be that Windows was the problem or my dad did something wrong with software that is no longer a problem.

Long story short, I'd like to run an extended system test.  Like a performance benchmark on repeat.  Maybe for 24 hours.  What do you suggest?

My first thought is to run a system performance test on repeat which would involve scripting possibly.  That's cool.  Just help me out a little with how to do it.

THANKS!

---

### Post by deadflowr on 2013-10-08
Here's one for ya
[http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)

---

### Post by QIII on 2013-10-08
Hello!

If you want a suite that covers everything from soup to nuts, you might be interested in the [Phoronix Test Suite]("http://www.phoronix-test-suite.com/").

---

### Post by QIII on 2013-10-08
Ninja'd!

---

### Post by lastlion on 2013-10-08
Checkin it out now.  Trying to figure out if I can use this machine or not.  Seems like a good box to me hate to waste it.

---

### Post by mastablasta on 2013-10-09
windows, viruses, setup, ram... all sorts of things. including - yes - the motherboard.

we had a mashicne working for a long time with windows XP working just fine but then suddenly it was shutting itself off, rebooting, giving errors on boot, blue screen. for some reason we couldnt' add a 750 GB drive to it as well. we thought first must be the power supply, then the motherboard. we had same one in it before and that one died completelly. and OS drive is 15 years old.

but funny thing was when trying to diagnose the error we did it in linux live and not a single crash or reboot. so i donwloaded a few antivirus rescue discs and sure enough they found something. one more than the other. don't know if they are actually false positives but full cleanup was performed. no crash during any of these tasks. now it just sites there. we might put linux on it see if that works. otherwise it's the motherboard. :-)

---

### Post by lastlion on 2013-10-10
I really like this Phronix suite.  I setup it up to run 100 complex tests back to back and monitored the load periodically.  Response was sluggish during the tests but seems snappy otherwise.  I think I have a good project box now, may use it for backups or something.

Thanks for the help.

---

