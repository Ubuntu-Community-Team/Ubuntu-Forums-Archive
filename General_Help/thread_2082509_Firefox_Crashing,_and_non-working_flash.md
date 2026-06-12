---
title: "Firefox Crashing, and non-working flash"
date: 2012-11-09
forum: General Help
---

### Post by manji_kun on 2012-11-09
Since I've upgraded to 12.10, I've run into a few problems, most of them are solved now, but there are two that remain.

The First: no matter what i do with flash, update, re-instal, i even use flash-aid, it doesn't seem to work with youtube video's, is there another plug-in or something i need to get to make this work normally?

The Second: Firefox keeps crashing on me, usually seconds after the previous crash, and i keep sending in reports, what is the terminal code fro downloading and installing the latest version? since FF won't stay open long enough for me to do it.

---

### Post by UAdnan on 2012-11-09
Is the problem only happening on YouTube videos ? Have you tried another browser ? It might come from the browser itself ... 
Check up these.

---

### Post by manji_kun on 2012-11-09
Another browser? surely you jest! >.> i'll try google chrome or something to see.

---

### Post by mardybear on 2012-11-09
Hi manji_kun.

Are you running any add-ons that might be problematic or affect flash?

Try running Firefox with all add-ons disabled...

otherwise create a new Firefox profile...

or remove/reinstall Firefox via the software center or synaptic.

FYI: if you try a reinstall, backup but remove/rename all your previous profile info from your home directory (sorry i'm not on my linux computer, something like /home/your_home_directory/.mozilla/firefox)

mardybear

---

### Post by HiImTye on 2012-11-09
re: Flash, what is your specific issue with YouTube + Flash?
re: Firefox, try loading it in safe mode
```
firefox --safe-mode
```
then disabling all add-ons and enabling them one at a time. might help you narrow down where the problem is

---

### Post by manji_kun on 2012-11-10
Ok, so far I've put my browser in safe mode, UN-installed and re-installed firefox, and tried chromium (i couldn't find  a suitable plug-in for chromium, and firefox still crashes, and still won't play videos.

The only difference so far is I don't have YouTube open, so the browser doesn't crash as often.

---

### Post by manji_kun on 2012-11-11
Anyways, here is the crash report, maybe some of you smarter guys will know whats up from that >.>

>    	 	 	 	 	 	   Add-ons: [email]anttoolbar@ant.com:2.4.7.4,langpack-en-ZA@firefox.mozilla.org:16.0.2,langpack-en-GB@firefox.mozilla.org:16.0.2,ubufox@ubuntu.com:2.4.1,globalmenu@ubuntu.com[/email]:3.5.4,{972ce4c6-7e08-4474-a285-3208198ce6fd}:16.0.2 
 BuildID: 20121025212230  
 CrashTime: 1352626713  
 EMCheckCompatibility: true  
 Email: <removed email>  
 FramePoisonBase: 00000000f0dea000  
 FramePoisonSize: 4096  
 InstallTime: 1351858962  
 IsGarbageCollecting: 1  
 Notes: GLXtest process failed (received signal 11)  
 ProductID: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}  
 ProductName: Firefox  
 ReleaseChannel: release  
 SecondsSinceLastCrash: 13  
 StartupTime: 1352626702  
 Theme: classic/1.0  
 Throttleable: 1  
 Vendor: Mozilla
   


and this one pops up when i try to mount a hard drive, or flash drive


>    	 	 	 	 	 	   
Adding read ACL for uid 1000 to `/media/username' failed: Operation not supported
   


any idea's gents?

---

### Post by sandyd on 2012-11-11
btw, removed your email in earlier post - wouldn't want spam going there right? ;)

anyways...
> **manji_kun said:**
> Anyways, here is the crash report, maybe some of you smarter guys will know whats up from that >.>




and this one pops up when i try to mount a hard drive, or flash drive





any idea's gents?

Looks like a video card issue - what video card/drivers you using?

---

### Post by manji_kun on 2012-11-11
The e-mail doesn't matter, i use it for spam anyways, and my video card is my old GeForce i think 7700, it should be in my tag, i built this box oh, a decade ago, just now having issues.

---

### Post by mardybear on 2012-11-11
Hi again manji_kun.

I'm also no crash report expert, but noticed it indicated you're running an anttoolbar, a video add-on, so query whether you were running with all add-ons disabled when the crash occured. Try disabling all add-ons, especially anttoolbar.

You mentioned trying safe mode and reinstalling firefox but have you created a new profile. If not, i believe Firefox will still use any old junk in your existing/old profile...your home directory mozilla firefox profile doesn't get deleted during the uninstall.

Try creating a new profile or temporarily renaming your existing Firefox profile/folder (new one will automatically be created when you restart Firefox). Your old profile is located in something like /home/your_home_directory/.mozilla/firefox folder.

Oh yeah - did you really mean won't play videos, as in Flash does not work at all, or simply your Firefox crashes while playing a Flash video (ie Flash still works but is problematic)?

mardybear

---

### Post by manji_kun on 2012-11-11
> **mardybear said:**
> Hi again manji_kun.

I'm also no crash report expert, but noticed it indicated you're running an anttoolbar, a video add-on, so query whether you were running with all add-ons disabled when the crash occured. Try disabling all add-ons, especially anttoolbar.

You mentioned trying safe mode and reinstalling firefox but have you created a new profile. If not, i believe Firefox will still use any old junk in your existing/old profile...your home directory mozilla firefox profile doesn't get deleted during the uninstall.

Try creating a new profile or temporarily renaming your existing Firefox profile/folder (new one will automatically be created when you restart Firefox). Your old profile is located in something like /home/your_home_directory/.mozilla/firefox folder.

Oh yeah - did you really mean won't play videos, as in Flash does not work at all, or simply your Firefox crashes while playing a Flash video (ie Flash still works but is problematic)?

mardybear


A little bit of both, it can't play the newer video's on youtube, and it does crash, no matter what site I'm on, and i have already un-installed antbar, i noticed it was in the error, so i gave it a shot.

---

### Post by mardybear on 2012-11-12
Okay....but did you try a new profile yet ?

mardybear

---

### Post by Rebelli0us on 2012-11-12
Try disable "hardware acceleration" in Adobe Flash settings.

---

### Post by manji_kun on 2012-11-22
No, I haven't created a new profile, I'm assuming you'd have to do that through the browser it's self? the browser isn't exactly stable for me.

Unless you can do it without the browser, Which I'll just assume you can,  I had to deal with some Personal problems. so i had to put my ubuntu on hold for a while.

And another thing I've noticed is that the processor and ram usage are peaked awfully high, so it takes a while to load anything, from a video i have, to a website, ect ect.

And Lastly, I can't mount my second hard drive, it keeps giving me the error 

> Adding read ACL for uid 1000 to `/media/rokuro' failed: Operation not supported

Which I assume means that when I updated, this wasn't included on the update for some reason.

---

