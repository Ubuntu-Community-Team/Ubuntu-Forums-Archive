---
title: "unable to type in chromium after update to 14.04"
date: 2014-04-20
forum: General Help
---

### Post by andrewgerm on 2014-04-20
Greetings all
I have updated my Lubuntu to 14.04, however I am now unable to type in the address bar or any text box on a page. If I use a bookmark, I can browse and navigate still, and I can type in other applications.

Any ideas / help appreciated.

Thanks in advance.

---

### Post by Jonathan_Traill on 2014-04-20
I had the same problem on upgrading, but I use the [SRware Iron browser]("https://www.srware.net/forum/viewtopic.php?f=18&t=7257") (which is a variant of Chromium) and the typing issue went away when I downloaded that.

That isn't really a solution to the wider problem, but it should let you use Chromium (albeit disguised as Iron).  So you get to keep all your bookmarks and you get an cool Iron icon instead of the boring Chromium one.

I think it might me a slightly older version of Chromium that Iron is based on, so if you absolutely need the most up-to-date version, this may not help at all.

Sometimes Iron does not wake up properly after installation.  Commands to remedy this are in the link above.

---

### Post by Jonathan_Traill on 2014-04-20
Other solutions have been to remove and reinstall via the command line, and switching to chrome.  [Instructions here]("http://ubuntuforums.org/showthread.php?t=2217965").

---

### Post by andrewgerm on 2014-04-20
Thank you for the link
Apologies. I had tried to search, but at the time was using my phone (browser issue, obviously)

I will try those.
As an aside, CPU usage seems to go up as well when the browser opens. Almost 100%

---

### Post by andrewgerm on 2014-04-22
Update:
By closing the input selection (Ibus) app that is running on the task bar, I am able to now successfully type in Chromium, without having to do anything else (reinstalling Chromium does not help).

On occasion I am still seeing CPU usage running at 100%, and most of the time RAM usage is around 70%.
This is without anything else running. Facebook, as an example site, has always pushed CPU usage up a bit more, but never like this. Now even without that open.

I mention that, because it does seem related, as when CPU and RAM usage are high (without starting anything else new) then input seemed to stop for Chromium. Posting this, in case it helps others.

I know this is a new release, so hopefully this is sorted soon. Will continue to monitor my system, and if I find something that fixes this, I'll post again. I swapped to Lubuntu when Ubuntu with classic Gnome started doing this (running perfectly on my old laptop, and then max CPU and RAM, and I'd have to reboot).

---

