---
title: "Firefox browser bug - often can't click between tabs or X them out"
date: 2023-03-02
forum: General Help
---

### Post by jonfisher on 2023-03-02
Ubuntu 22.x user

I've tried to purge Firefox and reinstall it in various ways....

Nearly daily, when I create multiple tabs in the browser, it will not  let me click between the various "tabs" and I have to quit it and  restart it....
It will allow me to keep working in the current tab I'm in, but I can't click to another tab or even X out other tabs.

I don't want to resort to using a Google type browser - just don't know. Any one else experience this?

---

### Post by DuckHook on 2023-03-02
Generally, it is important to know your exact Ubuntu version, but I gather from your reference to 22.x that you have the same problem on multiple versions?

Starting with 22.04, Firefox moved to a snap. Even if you reinstall, you will just get a .deb stub in the repos which will then install the snap version. Many users have posted about stubborn and frustrating growing pains with the snap version of FF. Here's what I would suggest in ascending order of complexity:

[LIST=1]
[*]Export your bookmarks (and history if its important to you) for safekeeping. Copy the resulting file onto multiple places including external storage. This is for backup/recovery purposes, so don't skip it.
[*]Make sure you have proper snap privileges defined for FF. Since I don't run snap FF, you will have to rely on websearched walkthroughs for that.
[*]Clear the FF cache. If this doesn't work, then:
[*]Restore your FF to its default state. Lots of tutorials available via websearch on how to do that. If none of the above work, you may want to consider nuking the snap version of FF in favour of a proper .deb version.
[*]The easiest (but not the most versatile) is to install the standalone FF downloaded from Mozilla's website. Again, thousands of walk&#8209;throughs available with a simple websearch.
[*]Another method is to add the official Mozilla Team PPA to your system, then install any of the various FF versions you would like. Being the lazy bugger that I am, I'm not going to repeat&#8209;post. Here's a link to my walkthrough: [https://ubuntuforums.org/showthread.php?t=2438709&p=13939386#post13939386](https://ubuntuforums.org/showthread.php?t=2438709&p=13939386#post13939386)
…just ignore the LXD stuff (unless you really want to make your life more "interesting").
[/LIST]

---

### Post by jonfisher on 2023-03-02
I am going to study what you instructed after I post this:

Ubuntu version 22.04.2 LTS

Firefox version 110.0.1 (64 bit)


I am currently trying the "refresh" option at this help page:

[URL="https://support.mozilla.org/en-US/kb/troubleshoot-and-diagnose-firefox-problems#w_5-refresh-firefox"]https://support.mozilla.org/en-US/kb...efresh-firefox

Addendum:  After refreshing it, it hasn't malfunctioned again "yet."  I'll report back either way....
[/URL]

---

### Post by DuckHook on 2023-03-02
I neglected to mention that if you follow through with replacing the snap, you need to completely purge the snap version first, or else you will end up with two conflicting versions of FF on your computer.

---

### Post by jonfisher on 2023-03-03
Addendum:  After refreshing it, it hasn't malfunctioned again "yet."  I'll report back either way....

---

### Post by jonfisher on 2023-03-03
> **DuckHook said:**
> I neglected to mention that if you follow through with replacing the snap, you need to completely purge the snap version first, or else you will end up with two conflicting versions of FF on your computer.

Is there anything I can type into terminal to determine if I have more than 1 version installed.  I probably installed them with Ubuntu Software center and also with Synaptic package manager at some point...

---

### Post by DuckHook on 2023-03-03
> **jonfisher said:**
> Is there anything I can type into terminal to determine if I have more than 1 version installed.  I probably installed them with Ubuntu Software center and also with Synaptic package manager at some point...
If 22.x, then *any* of the old installation methods will install the snap version. The old real .deb version no longer exists unless you implement the PPA steps that I linked to. You needn't worry about figuring out whether it is anything other than snap.

---

### Post by jonfisher on 2023-03-03
Since refreshing, I still haven't experienced the bug(s).  I'll report back much later, after I've used it a lot...

---

### Post by DuckHook on 2023-03-03
Keeping fingers and toes crossed for you.

I do suspect that you have this one licked. I'm an optimist that way.

---

### Post by jonfisher on 2023-03-08
No problem(s) since refreshing...
Marking as solved...

---

### Post by DuckHook on 2023-03-08
Happy for you.

Good Luck and Happy Ubuntu-ing!

---

