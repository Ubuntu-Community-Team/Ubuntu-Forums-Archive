---
title: "Problem with Flash Player on Firefox and Chromium"
date: 2014-06-20
forum: General Help
---

### Post by amjjawad on 2014-06-20
Hi,

I'm using Ubuntu GNOME 14.04 LTS amd64 - Kernel: 3.13.0-29-generic.

Firefox: 30
Chromium: Version 34.0.1847.116 Ubuntu 14.04 aura (260972)
Flash: flashplugin-installer 11.2.202.378ubuntu0.14.04.1

I always install
```
ubuntu-restricted-extras
```
After each and every installation I do ...

I have always enjoyed using both Chromium and Firefox side by side (I always need two browsers at the same time) without any problem but with 14.04, I'm having some weird/odd problems and not sure what is wrong? what has changed? is it flash? or is it the system?

Problems like:
[LIST=1]
[*]Gmail and Gmail Plug-ins. 
[*]Facebook does not work correctly unless I refresh, sometimes more than one time. Examples: clicking on a picture will not open it, home page is not refreshing unless I manually refresh it, can't easily upload pictures, etc. 
[*]Stream/videos websites not 100% usable. Example: [http://www.naruget.net/](http://www.naruget.net/) - when I try to maximize the screen, I can't, it won't let me. 
[/LIST]

These on both Chromium and Firefox.

Not sure what is wrong? I guess this is the first time I face such issues at the same time on two different browsers.

Thanks!

---

### Post by amjjawad on 2014-06-21
Chromium is worse than Firefox on Ubuntu GNOME 14.04. Despite the fact that Flash is installed, it is still asking for the latest verson:

[ATTACH=CONFIG]254127[/ATTACH]

This is on Facebook. I was trying to watch a video and that is what I got.


I tried to install Flash from the previous link (on the above screenshot):

[ATTACH=CONFIG]254128[/ATTACH]

But that did NOT change the fact that I still can NOT watch anything on Facebook using Chromium.

What is weird too, if I want to use Launchpad on Chromium, I just can't do:

Right Click > Copy link address

I just can't have totally different menu 

[ATTACH=CONFIG]254129[/ATTACH]

This is on Chromium on both 12.04 and 14.04 as well. Chromium version 34.

On Firefox, I don't have the right click issue.

As for Chromium, I'm not sure if this is the solution:
[https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash)
I have never tried it.

As for Firefox, I'm not sure what should I do?

I insist that I have never had problems with previous versions of both Chromium and Firefox and still not sure what is going on in my case ...

---

### Post by Impavidus on 2014-06-21
Concerning flash and facebook: Facebook wants the latest version of flash, which is at version 14 or so, and which is not available for Linux. There's no way to fix this in Firefox. Blame Adobe for not providing a recent version for Linux or Facebook for demanding it. I don't know about your other issues.

---

### Post by amjjawad on 2014-06-22
> **Impavidus said:**
> Concerning flash and facebook: Facebook wants the latest version of flash, which is at version 14 or so, and which is not available for Linux. There's no way to fix this in Firefox. Blame Adobe for not providing a recent version for Linux or Facebook for demanding it. I don't know about your other issues.

Hello and thanks for posting :)

Actually, this is not 100% correct. I don't have problems on Firefox for example or Google Chrome on Xubuntu 12.04 except this issue on Chromium:

[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1325498](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1325498)

While on Firefox and mainly Chromium on Ubuntu GNOME 14.04 LTS, I'm having this issue explained on this thread.

Blaming people is not helpful at all, with all due respect. I do understand what you mean but that won't fix my issue nor anyone's issue here :)
We, as FOSS Community 'must' fix that instead of complaining. This is what I think after 4 years of being super active in the FOSS world with different project. 
At my first days, I was blaming Linux and FOSS. After a year, I started to blame the other side (Microsoft, etc). Now, I understand that blaming will do nothing at all except getting into useless arguments.

On the other hand, I just gave this a try:

[https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash)

And Chromium on Ubuntu GNOME 14.04 is a bit better BUT still I need to do some actions twice like when I upload a picture or open a link ... so it is not yet okay but at least, I don't have this for now:

[ATTACH=CONFIG]254152[/ATTACH]

Thanks!

P.S.
On Ubuntu GNOME 14.04, I use only Firefox and Chromium as explained on my first post.

On my other system (Xubuntu 12.04), I'm using Firefox, Chrome and I keep Chromium. Chromium was causing a lot of troubles so I installed Chrome and everything is okay now on Xubuntu as far as I can tell.

My issue on this thread is with Ubuntu GNOME, not Xubuntu.

---

### Post by amjjawad on 2014-07-04
Hi,

Sadly, I'm still suffering from the same issue and didn't find a way to fix that until now.

Perhaps it is time for FOSS World to get rid of Adobe Flash once and for all. The Q is when?!

---

### Post by Bucky Ball on 2014-07-04
Pepperflash is where you go. 'pepperflashplugin-nonfree' is what you want and it's in the repositories. Search for and install. Will take you to Flash 12.**.

This will fix up Chromium, but won't matter a jot to Firefox or anything else. It is 'exclusively Google'. Firefox will remain at Flash 11.2.

---

### Post by bobnn on 2014-10-27
So I just upgraded to 14.04 - after upgrade, neither Firefox nor GoogleChrome could play Facebook vids - they would both hang the browser.

After doing the pepperflashplugin-nonfree thing, though, Chromium can.  Strange, but I'll take a workaround when I can get it.

At least youtube is going to HTML5 - they've progressed nicely at what must be a massive job.

---

### Post by Bucky Ball on 2014-10-27
@bobnn: This is a support area of the forum and you've posted on a thread that hasn't seen action for nearly four months. If you'd like support with anything, please post a new thread with a descriptive thread title. Thanks and good luck.

*Thread closed.*

---

