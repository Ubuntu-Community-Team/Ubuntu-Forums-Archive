---
title: "Youtube, CORS, other problems unique to Ubuntu - need for proprietary software?"
date: 2018-11-21
forum: General Help
---

### Post by cigtoxdoc on 2018-11-21
I have been using Ubuntu for over 10 years.  I have several PCs running 18.10 (and before that 18.04).  Some are dual boot with Win 10 64 Pro and others are dual boot with Win XP Pro SP3.  The latter includes the two most important PCs in my consulting business:  My secertary's desktop (home-bulit from components) and my DELL VOSTRO 3500 Laptop.  My business runs on evolution for e-mail, calendaring.  In terms on letting you see what you need to see, it is far better than MS Outlook.

I am not a open-source software purist.  The Ubuntu side of of each of my PCs has PDFStudioPro (Qoppa Software) installed to deal with PDF editing, etc.  PDFStudioPro 2018 is a fairly good approximation for Adobe Acrobat DC.  I also use Crossover.  I am about to invest in the Ubuntu version of Quick and Easy Web Builder 6.  However, there is a more pressing problem.

If there is a way of running youtube video under the version of Firefox that comes with 18.10, it is a secret known to only a few.  This FORUM really needs a place for instructions on how to make Firefox behave.  The same is true for websites that require CORS support.  Yes, I have tried the addon and extensions that supposedly allow Ubuntu to use those websites; however, I have not been able to make them work.  The current workaround is to carry a second lap with me: an hp 840g-1 that I purchased refurbished for $300.  It came with Win 10 64 Pro.  Is that what we really want Ubuntu to be: an OS is that falls apart when it has to do common tasks?

John

---

### Post by wildmanne39 on 2018-11-21
*Thread moved to **General Help for a more appropriate fit**.*

---

### Post by QIII on 2018-11-21
Ubuntu?  I don't see an indication that the OS is falling apart.

It sounds like the issue is with Firefox.  The version of Firefox that comes with Ubuntu is, well, Firefox.

On the other hand, it might be your video driver.

Would you provide your machine specs?  Any given model number might have different specs depending on changes the OEM makes during its life cycle.

We do have a place for questions about Firefox.  This sub-forum.

---

### Post by HermanAB on 2018-11-21
Well, if you want to watch Google cruft, why not use the Google Chrome browser?

---

### Post by cigtoxdoc on 2018-11-22
Thank you all for your replies.  Please note the following:
1.  Two years ago viewing youtube videos and videos requiring CORS (e.g., CNN.com) was not a problem using the same hardware and software (long-term support Ubuntu).
2.  The same websites can be accessed using latest version of Firefox when Win 10 is the OS without need for addons and/or extensions.
3.  Some claim on various websites that they can use Ubuntu with Firefox to view youtube videos and access CORS sites; however the posted instructions don't appear to work
4.  I have no problems viewing videos on many other sites such as abcnews, thehill, huffington post, or the videos at tm.trains.com; some sites such as 13wmaz.com require that blocking be disabled
5  It would appear that continued acceptability of Ubuntu requires that Mozilla Firefox for Ubuntu Canonical gets an update to increase compatibility with popular video sites
6. In the meantime step-by-step instructions (which addons, extensions to use, and settings) should be provided on this forum.

John

---

### Post by monkeybrain20122 on 2018-11-22
?? You don't need any special software for Youtube.

---

### Post by dragonfly41 on 2018-11-22
Do your video sites use cdn nodes ... ?

[https://support.mozilla.org/en-US/questions/1237060](https://support.mozilla.org/en-US/questions/1237060)

---

### Post by QIII on 2018-11-22
Just spun up a VM.

Chrome works.  Firefox doesn't.  The complaints are not limited to Ubuntu.

You can remove the OS itself from the list of possible culprits.

I'm researching.  If I don't get to the answer, someone else may.  For any of us to give you step-by-step instructions, we'll have to first sort out the answer.  It appears to be in Firefox's DRM setting or privacy settings.

Please bear in mind that nobody here works for Canonical and likely nobody works for Mozilla.  There may not be anyone here with a step-by-step answer to your liking just yet.  What you believe should or should not be available on the Forums does not dictate its availability.

---

### Post by Autodave on 2018-11-22
Running Firefox here gives me no issues with YouTube.  You say that several are running 18.10: did you do clean installs or did you upgrade 18.04 to 18.10?  If you upgraded, that may be your problem.  I would download 18.10 and make a boot medium from it. Boot the inop machines to that and choose to try Ubuntu. If Firefox works that way, then I would guess that the upgrading messed something up.  Personally, I learne a long time ago that upgrading isn't worth the time or aggravation. I only do clean installs of the LTS releases.

---

### Post by QIII on 2018-11-22
I recreated the issue on a fresh installation of 18.10 and have found some queries on the web about the problem that are not just about Ubuntu.

The problem is real enough.

---

### Post by cigtoxdoc on 2018-11-22
I found one solution to my problem.  Disable all extensions and add-ons except for the H264 Codec.   This means putting up with ads, however.

John

---

### Post by QIII on 2018-11-22
I had no add-ons running and I still had problems.  Still looking, but a busy weekend around here.

---

### Post by angisky on 2018-11-22
It seems it's already been proven that it's a browser issue. Why don't you migrate over? Chrome seems to be the browser with the best compatibility for most websites across every platform except iPhone. You already have a google account if you're watching youtube videos anyway. Also don't throw away the driver issue that was recommended earlier. I've had weird things happen across browsers just for running bad or outdated video card drivers.

---

### Post by QIII on 2018-11-22
Changing browsers may *avoid* the problem in the short run, but it doesn't *solve* it.  The outcome desired is that the OP be able to use the chosen package.

From what I have found so far, it is a known issue and appears to be a bug that may (or may not) be fixed soon.

---

