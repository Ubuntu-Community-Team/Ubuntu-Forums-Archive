---
title: "No Software updates in over a week now ..."
date: 2016-01-01
forum: General Help
---

### Post by GreysonB on 2016-01-01
...is everybody drunk all the time or what?

:D

I only ask because I seem to be having a few new problems after updating to the latest release.

Since  -- 3.13.0-74-generic   -- I have been having a host of brand new problems.

I know, you need a lot more information - but, if it's just me then I must have done something stupid.

So- is it just me?

---

### Post by Bucky Ball on 2016-01-01
Without being more specific there is no way of giving you any support. The problems you're having would be a start ...

No idea if the title of your thread relates to one of the problems.

---

### Post by GreysonB on 2016-01-02
OK, it's mostly Adobe Flash, which was running fine before the update - now keeps crashing.

If I am patient with it then I can just tell it to reload Flash and after a while it will play just fine.  But these crashes have become a constant thing now.

But there are other things.  Web pages now will simply not load.  Most of the usual web pages load with no problem, but if I am surfing to a new area - those pages just time out.  Again, this did not happen before the last update.

---

### Post by monkeybrain20122 on 2016-01-02
You didn't tell us which Ubuntu (14.04, 15.04 or 15.10) do you use and which browser. It is kind of difficult for people to understand your problem without this crucial information.

I assume you are using Firefox? Have you checked with a new profile? To do this, close Firefox, open the file browser, press ctrl+h or choose show hidden files from menu, find the folder .mozilla (note the "." in front) change it to something else like .mozilla-bk, then re-open FF and go to those pages and see if it still crashes. If it doesn't then it is something in your settings, if it still crashes then it is something system. To revert to the old profile, close FF,  delete .mozilla and rename .mozilla-bk back to .mozilla.

---

### Post by Bucky Ball on 2016-01-02
Also, have you added any add-ons/extensions in Firefox? If so, switch them off. Still a problem? If no, add back one by one until there is. When there is, you have your culprit.

---

### Post by ajgreeny on 2016-01-02
Also which version of flash?

I use the freshplayerplugin very successfully with my firefox installation, giving me flash version 20.0.0.267 even in firefox, which otherwise would be using version 11.2.202.559.

---

### Post by buzzingrobot on 2016-01-02
In case your system is consistently using a mirror that is offline or is not itself updating correctly, open "Software & Updates", go to the first tab on the left -- "Ubuntu Software" -- open the dropdown list labeled "Download from:", select "Other", and let it determine the best mirror for you to use.

Running "sudo apt-get update" and "sudo apt-get upgrade" in a terminal will display errors, if any are generated, during the update.

---

### Post by GreysonB on 2016-01-02
I'm sorry - the latest version is not specific enough?

It's the LTS version.

Honestly - these problems are not problems.   I just don't want the Linux community to start nit picking like Windows did - and they lost a very important part of the Internet when they did.

Again  -- I am not complaining.   I just wanted to know if there are any problems with the last update.

But, my machine is fine.

---

### Post by lisati on 2016-01-02
> **GreysonB said:**
> I'm sorry - the latest version is not specific enough?

It's the LTS version.

Things change, and information included in discussions such as this can become out of date surprisingly quickly. Perhaps people are thinking ahead to a time in a year or two, or even six months from now, when expressions "the latest version" or "the latest LTS version" refer to completely different versions to what was originally intended.

---

### Post by grahammechanical on 2016-01-02
> is everybody drunk all the time or what?

Canonical engineers get 2 weeks vacation at this time of year. I run the development branch and I update daily and there are usually a lot of updates to download but over the holiday period there has been very little to be downloaded. And I do not begrudge Linux and Ubuntu developers a vacation.

I would not expect an LTS version to receive a lot of updates. A fresh install or an upgrade would bring in everything that has been lined up. 

And Adobe flash player is proprietary software. The flashplugin installer is open source software but that just extracts whatever is available in the Google Chrome browser.

Regards

---

### Post by GreysonB on 2016-01-02
Nobody here begrudges anybody vacation time.  In fact, I have been out of work the past two weeks.

(Probably how I found the time to get picky...)

I'm just trying to feed back to the community.  As I was saying everything was working fine until I updated.  I've been using Linux Ubuntu for over ten years now so I understand the ups and downs.

And - I understand about Flash.  It does work, it just wants to complain while it does.

In case I haven't said it recently - Great Job You Guys!!  

I know how tough it can be to keep up with computers (and, OMG, cell phones) so Happy New Year to All!!

---

