---
title: "Secure web pages go doolally"
date: 2017-08-29
forum: General Help
---

### Post by Panawe on 2017-08-29
After installing Ubuntu 16.04 on a friend's old computer (not the one below) it now works okay apart from the screen becoming hazed and unusable when attempting to access secure (banking) web page. A restart is the only way of clearing it.

It looks for all the world that the video driver is playing up: the card is an Nvidia 7025 and the latest driver I can use with it is 304, which is now installed. I tried installing a later driver with disastrous results.

Is there any solution to this problem short of a new video card?

TIA

---

### Post by SeijiSensei on 2017-08-30
This site uses HTTPS.  Do you have the same problems here? What browsers and operating systems does the bank say its software runs on?

I've used NVIDIA cards for quite a long time now and don't have this problem, so I doubt the video card is the villain.

---

### Post by Panawe on 2017-08-30
He has tried three browsers, Firefox, chromium and Google Chrome, with the same result on all so the issue isn't down to the browser. Plus, when he uses Firefox on Windows XP there is no problem. I only get access to the computer now and again so I couldn&#8217;t tell you whether he can access this forum with my login.

Can you suggest and information I could gather next time I see him that might help identify the problem?

Edit: the computer concerned isn't the one described below. It's an older model though still 64 bit.

---

### Post by SeijiSensei on 2017-08-30
The fact that it runs on Windows and not on Linux tells me the bank's software isn't happy with Linux.

He could try "spoofing" his User-Agent string by telling the browser to pretend it is using Windows.  I use [UAControl]("https://addons.mozilla.org/en-US/firefox/addon/uacontrol/") for this task.  That will only work if the bank's software isn't looking for Windows-specific libraries.

---

### Post by Panawe on 2017-08-31
I did notice that his Ubuntu clock is out and I read somewhere whilst Googling this that it could be a problem. How could I ensure the clocks in both Windows and Ubuntu are synchronised?

---

### Post by SeijiSensei on 2017-08-31
Make sure they all use network servers to get their time.

That said, Windows and Linux handle time zones differently.  Most *nix systems use UTC ("Greenwich Mean Time") with a local timezone offset.  Windows uses local time.  I rarely use dual-booting anymore, preferring a VirtualBox VM for Windows, but I when did use dual booting the times reported different by the offset.

---

### Post by Panawe on 2017-08-31
Would that affect the https problem?

---

### Post by SeijiSensei on 2017-08-31
As I said, I don't think it's an HTTPS problem.  Can he go to YouTube ([https://youtube.com](https://youtube.com)) or Google ([https://google.com](https://google.com)) but not his bank?  I really can't help much more if we don't resolve that basic issue first.

---

### Post by Panawe on 2017-09-02
Okay, I only get access to the computer about once per week so my responses will be intermittent. However, a couple of questions.

1) By installing UAControl I then nominate the bank in question in some way to spoof it into thinking the computer is a Windows machine? Is this straightforward, I can't find much info on how UAControl works?

2) Simply looking at Youtube wouldn't trigger https would it? I would have to log on using my own password and ID - not a problem but just to be clear.

Thanks for your help.

Edit: I have found this script online:

> You could try installing a User-Agent spoofer in Firefox and telling the  remote site that you are using a Windows browser.  I use  UAControl ([https://addons.mozilla.org/en-us/firefox/addon/uacontrol/](https://addons.mozilla.org/en-us/firefox/addon/uacontrol/))  with the User-Agent string:

Mozilla/5.0 (Windows NT 6.1; rv:41.0) Gecko/20131011 Firefox/41.0

Is that string appropriate in this case?

---

### Post by SeijiSensei on 2017-09-03
Take a look at [http://www.useragentstring.com/index.php?id=19879](http://www.useragentstring.com/index.php?id=19879)

```
Mozilla/5.0 (Windows NT 6.1; WOW64; rv:40.0) Gecko/20100101 Firefox/40.1
```

The only problem arises when your UA string references a version of the software that is no longer supported.  Usually in that case the web site will complain, and you'll need to check for a more up-to-date string.

Both YouTube and Google default to HTTPS for everything these days.  You don't need to log in at all.

---

### Post by Panawe on 2017-09-05
Have loaded UAControl into Firefox and first indications are that it works. I had to leave before I was absolutely certain it was fixed but I'll update you in due course.

Firefox can access other https sites, including this one, without any problem.

Thanks again.

---

