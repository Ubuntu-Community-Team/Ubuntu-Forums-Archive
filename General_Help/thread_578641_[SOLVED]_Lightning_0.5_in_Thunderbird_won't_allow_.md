---
title: "[SOLVED] Lightning 0.5 in Thunderbird won't allow any calendar to be created"
date: 2007-10-17
forum: General Help
---

### Post by Gordonbp531 on 2007-10-17
I've installed Wubi on Windows XP - everything is great EXCEPT, I cannot create ANY calebdar AT ALL, whether local or remote using TBird 1.5 and Lightning 0.5. I go through the process, and after naming the Calendar, I click on "next" and nothing happens!

Has anyone tried this and succeeded?

---

### Post by ago on 2007-10-17
> **gendibal said:**
> I've installed Wubi on Windows XP - everything is great EXCEPT, I cannot create ANY calebdar AT ALL, whether local or remote using TBird 1.5 and Lightning 0.5. I go through the process, and after naming the Calendar, I click on "next" and nothing happens!

Has anyone tried this and succeeded?

You may want to ask in the general support forum, this forum is mostly for wubi-specific issues

---

### Post by KittyChunk on 2007-10-20
Hi gendibal, I know this isn't the correct forum to post answers to your problem, but I couldn't find it mentioned anywhere else.

I had exactly the same issue after reinstalling my laptop with Ubuntu 7.10 Gutsy yesterday - I installed Thunderbird from the repositories, transferred my backed-up profile across, and then tried to install the Lightning extension from Mozilla's add-ons site as normal. Everything seemed to work ok until I tried to add a new calendar and ran into the same problem you had.

For me, the solution was to uninstall the Lightning calendar extension, and then install the "lightning-extension" package using Synaptic (or apt, or whatever you prefer). Creating new calendars worked fine after I did that.

Reading a bit on mozilla's forums, it sounds like Tbird and Lightning are very sensitive regarding which builds work with which - that may be why Ubuntu provide their own version of the Lightning extension in the repositories, to ensure it'll work with their version of Tbird.

---

### Post by erginemr on 2007-10-31
The same problem with Lighning ver.0.7.

I was looking or a light-weight Evolution alternative, and Thunderbird + Lightning (sunbird) marriage sounded a good candidate, until I realized that you cannot create a new calendar (and therefore cannot use it). I have been using this combination already under Windows.

Installing the Lighning package from Ubuntu repositories solves he problem, but it is still ver. 0.5 and there are some improvements made in 0.7.

As also pointed out by KittyChunk above, a quick web search revealed that the culprit may be different versions of libstdc++ installed (Gutsy has ver.6). To eliminate that possibility, I have installed ver.5 too from the repositories, but no go.

Is there anyone out there who can effectively use Thunderbird with Lightning under Linux? Any ideas?

---

### Post by astx813 on 2007-11-03
Woohoo, I finally have a chance to throw in helpful guidance!  I ran into this issue, as well.  The problem I faced is that the latest version of [Provider (0.31)]("https://addons.mozilla.org/en-US/thunderbird/addon/4631") (great addon that allows you to sync your Lightning calendar with Google Calendars) requires Lightning 0.7.  The lightning-extension available in the repos is 0.5.  The broken New Calendar issue seems to come up when you manually install Lightning 0.7 with repo-installed Thunderbird.

My solution: remove the thunderbird package in Synaptic and manually reinstall the version from mozilla.com, then you're free to install whatever addons.  This breaks the "thunderbird-gnome-support" package, but that doesn't seem to be too big a problem.  I'm playing with it now to see if I can fool it into working (maybe install the thunderbird & gnome-support packages and then install the good version on top of the packaged version).  Any thoughts on that part?

P.S.  GMail Thunderbird users should check out the [recent article on Lifehacker]("http://lifehacker.com/software/geek-to-live/turn-thunderbird-into-the-ultimate-gmail-imap-client-314574.php") about tweaking your GMail IMAP in TB.  Handy hints in there.

---

### Post by erginemr on 2007-11-03
> **astx813 said:**
> Woohoo, I finally have a chance to throw in helpful guidance!  I ran into this issue, as well.  

:lolflag:

Thank you astx813. Installing from the Mozzilla site is hell of a good idea. I will give it a try.

Your above enthusiasm is also very fun. You are following Ubuntu principles, help others and let others help you. Way to go, friend... =D>

---

### Post by erginemr on 2007-11-04
I have tried installing Thunderbird from the Mozilla site and the lightning extension for my scheduling affairs. Both work flawlessly this way. 

I can recommend it to those who do not want to use Evolution, but still want to have its versatility.

Thanks astx813. =D>

---

### Post by culmore on 2008-10-04
Great tip thanks astx813. Manual install solved my problem also! :guitar:

PS Here is a link which explains how to manually install thunderbird:

[http://ubuntu-tutorials.com/2007/05/18/manually-install-thunderbird-2-ubuntu-704/](http://ubuntu-tutorials.com/2007/05/18/manually-install-thunderbird-2-ubuntu-704/)

---

