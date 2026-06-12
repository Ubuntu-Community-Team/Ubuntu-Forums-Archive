---
title: "Evolution Crashing in 13.04"
date: 2013-10-18
forum: General Help
---

### Post by neltnerb on 2013-10-18
Sorry if this note is a bit terse, it's been a very bad two weeks and this problem with evolution has been making an already very difficult week all the more irritating.

I upgraded recently from Ubuntu 12.10 to 13.04. Immediately when I did so, over a month ago, Evolution started crashing every 5-10 minutes with no explanation whatsoever. It's submitted a bug report at least 30 times, but I have no idea how to reference or find them so I can't provide a link to the information. This is driving me up the wall, it's losing half my emails before I manage to finish writing them, but I know of no better mail clients for Linux that can handle six different email accounts smoothly.

Please, please, please help me fix this as easily as possible. I can't deal with this anymore, and I don't understand how to use the new bugtracking system to actually find out if anyone even knows about this seemingly critical bug in the software. Am I crazy? Am I the only one this is happening to? I can't find out because I don't know my bugtracker number, or even if they're being submitted.

---

### Post by ian-weisser on 2013-10-18
Exactly where and precisely how did you report this bug 30 times?

---

### Post by neltnerb on 2013-10-20
When the program crashes, it opens a dialog that asks if I want to send a bug report. I have sent one every time it crashed, which has been at least 30 times (it only reports one time until I do a new apt-get upgrade). It doesn't do what the tool used to with taking me to a website and seems to just submit it without any more user interaction. I first thought that maybe the bug submission tool itself was broken, but I found reference to Ubuntu preferring just the raw data instead of a formal bug report so that they could prioritize solving things or something.

Basically, the whole bug submission process seems to me from reading into it to have changed, and I don't really know if what I've been sending has been received or if anyone else is having the problem, or if it's even been confirmed as a bug yet. Much less if anyone is working on it, or has a workaround. I think I may just be getting old.

---

### Post by neltnerb on 2013-10-20
Here are images of the two dialogs that come up. There is no further information after I click "Continue" and "Yes".

[IMG]http://s7.postimg.org/lbkeklhvd/Screenshot_from_2013_10_20_12_28_27.png[/IMG]

[IMG]http://s8.postimg.org/hwjnz6777/Screenshot_from_2013_10_20_12_29_27.png[/IMG]

The second message was too vague to be actionable for me, as far as I know nppdf is just a pdf viewer for the web browser, and I neither know how to tell evolution not to use it nor was the crashing related to a pdf mime type file (that I can tell).

---

### Post by neltnerb on 2013-10-29
Note: This bug still exists in Ubuntu 13.10.

---

### Post by VMC on 2013-10-29
> **neltnerb said:**
> Here are images of the two dialogs that come up. There is no further information after I click "Continue" and "Yes".

[IMG]http://s7.postimg.org/lbkeklhvd/Screenshot_from_2013_10_20_12_28_27.png[/IMG]

[IMG]http://s8.postimg.org/hwjnz6777/Screenshot_from_2013_10_20_12_29_27.png[/IMG]

The second message was too vague to be actionable for me, as far as I know nppdf is just a pdf viewer for the web browser, and I neither know how to tell evolution not to use it nor was the crashing related to a pdf mime type file (that I can tell).
Maybe the second link is there because you used Firefox to report the bug.

Also we need to know your harware, especially video card. If its nvidia and your using nouveau, that's the problem.

---

### Post by neltnerb on 2013-10-29
Fascinating, I never would have considered the graphics card to be an issue. Is there some reason that Evolution is particularly vulnerable to crashes based on video driver? I haven't seen similar problems with software such as VMware, Chrome, LibreOffice, Firefox, Pidgin, Steam, and others -- some of which I assume use the same backend API to communicate to the display.

This particular problem has actually spanned two graphics cards, both nvidia. In both cases I was using the proprietary driver. I am currently using nvidia-319-updates (I am not sure what the previous graphics card was using). Current card is seen by Ubuntu as "GeForce GTX 650/PCIe/SSE2"

I am most worried that the bug reports aren't even actually making it through if the bug reporting mechanism is silently failing (perhaps due to something like your comment about using Firefox to report the bug). I never myself opened Firefox to report anything, so whatever dialogs are appearing are being started automatically -- should I change a setting to fix that? I don't know why the bug reporting mechanism would care that Firefox is using nppdf.so in collecting data about the actual Evolution crash -- perhaps it's actually telling me that the crash is the bug reporting tool inside of Firefox?

Please let me know if there's any other hardware information that would be helpful.

lspci output is attached.

---

### Post by VMC on 2013-10-30
Do you using nouveau driver or did you install nvidia drivers?
What's the output of this terminal command ```
lsmod|egrep "nvidia|nouveau"
```

---

### Post by neltnerb on 2013-10-30
$ lsmod|egrep "nvidia|nouveau"
nvidia               8520590  65 
drm                   242354  2 nvidia

---

### Post by neltnerb on 2013-10-30
I had a thought. Does Evolution use Firefox's backend to read HTML-formatted emails? That could explain why Evolution would show an error regarding use of a Firefox plugin. I don't see the same crash in Firefox, but who knows what is going on if this is the case.

I don't typically use Firefox for anything other than reading RSS feeds (Chrome lacks integration of RSS feeds into the bookmark toolbar), and looking at about:plugins shows:

Adobe Reader 9.5
    File: nppdf.so,nppdf.so,nppdf.so
    Path: /usr/lib/mozilla/plugins/nppdf.so,/usr/lib/firefox-addons/plugins/nppdf.so,/home/neltnerb/.mozilla/plugins/nppdf.so

with three different versions of the plugin, who knows what's going on. Maybe I can just delete all three .so files and fix the issue (since why would I be reading pdf files with a plugin inside a firefox window inside Evolution...).

---

### Post by neltnerb on 2013-10-31
Well, I deleted the plugin entirely in all three locations. Evolution still crashes and requests to send a bug report, but no longer complains about nppdf.so. Still don't know if the bug report is actually being sent, nor do I know what might be causing the crash.

---

### Post by neltnerb on 2013-11-12
Resolved as per [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/1169694](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/1169694)

Removing evolution-indicator seems to have fixed the error!

---

### Post by ian-weisser on 2013-11-12
Hooray! Glad you got that sorted.

---

