---
title: "Help? - &quot;Only One Software Management Tool is allowed to run at the same time&quot;"
date: 2007-04-21
forum: General Help
---

### Post by portach king on 2007-04-21
Hi guys, I hope one of you can help me. I installed Feisty with much enthusiasm on Thursday and the first thing I tried to do with it was get my Broadcom wireless modem working on it. So I followed this guide:
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) 
and downloaded the *.deb file for installation. That's where my trouble began. The installation just hung on me.  It did not seem to install, instead it seemed like the program had crashed. So being sensible I left it for a few minutes to be sure, but when I came back it was still exactly the same. So  force quit the installation. However now I can't install anything. Not even updates. Everytime I try to I get this dialog box message: 
"Only One Software Management Tool is allowed to run at the same time" 
Followed by another box reading: 
"E: dpkg was interupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open()failed, please report"

I have of course tried restarting the computer, however this had made no difference.

If anyone can help, I would hugely appreciate it. I'm at the point of considering reinstalling Feisty from scratch again!

---

### Post by Jussi Kukkonen on 2007-04-21
> I'm at the point of considering reinstalling Feisty from scratch again!
Don't do that. Very probably this is a minor problem.

Have you tried what the error message suggests?
```
sudo dpkg --configure -a
```
That should at least finish whatever installation was interrupted. It might not help with the first message, but try that first...

---

### Post by aliengravy on 2007-10-06
Did you sort this problem? i am currently having the same difficulty and considering re-installing linux, is that what you had to do? what is all this sudo stuff about as well? i am brand new to linux!

---

### Post by Treutwein on 2007-10-13
I had the same problem with 6.06 LTS and running "dpkg --configure -a" as root resolved the problem.

regards
    Bernhard

---

### Post by cssutto on 2007-10-13
I assume by now you have fixed the crash, to get to the cause.

I am still with 6.06.

I purchased a wireless router and installing it about ran me nuts until someone suggested wicd.

15 minutes later, I had it up and running with my #1 laptop.  It manages wireless, sets up WPA and takes care of the old dog that uses ethernet to the router.

I had no luck with the standard stuff.

---

### Post by kayel_justice on 2008-03-31
I'm having the same problem

---

### Post by kayel_justice on 2008-03-31
> **kayel_justice said:**
> I'm having the same problem

Whoa I thinked that code worked

---

### Post by woosyrmomma on 2008-05-26
That helped a lot thank you much

---

