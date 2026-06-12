---
title: "Firefox- Random Popunder Tab"
date: 2015-01-18
forum: General Help
---

### Post by sasafrass452 on 2015-01-18
Lately, I've been seeing a browser tab that appears randomly.... even when visiting this site! The tab is advertising a way to make money with short urls. On the upper right side of the page is a button to "skip this advertisment", & clicking on it directs me to various sites. This tab has lead to at least 2 poker sites, a sports site, & one other called "videosbar.com". This tab also prompts a download of some kind. I've been trying to block this tab with AdBlock Plus, but no luck. Any suggestions to stop this? Could it actually be some type of adware on my system?

---

### Post by mooreted on 2015-01-18
Sure sounds like adware or, more specifically, a browser hijack. 

What extensions do you have installed? What are you using as your DNS servers?

You can delete the folder ~/.mozilla which contains all the extensions and settings for FireFox including your bookmarks and personal settings. You could start removing extensions one at a time and see if you can find the one causing the problem. You can also install NoScript which prevents javascript and others from running without your permission.

---

### Post by sasafrass452 on 2015-01-19
I highly doubt it's one of my extensions, I've had them all along & this didn't start until recently. I don't know what my DNS servers are. Where do I find them? What could that have to do with this issue? Is there a program you would recommend to get rid of it?

> **mooreted said:**
> Sure sounds like adware or, more specifically, a browser hijack. 

What extensions do you have installed? What are you using as your DNS servers?

You can delete the folder ~/.mozilla which contains all the extensions and settings for FireFox including your bookmarks and personal settings. You could start removing extensions one at a time and see if you can find the one causing the problem. You can also install NoScript which prevents javascript and others from running without your permission.

---

### Post by Holger_Gehrke on 2015-01-19
Try firefox in safe mode for a while by starting it from the command line with 'firefox -safe-mode'. This disables all third party extensions temporarily. If the problem does not come up, then that's a strong indicator that it **is** one of your add-ons. Might be that the author of one of your add-ons has '*gone to the dark side*' and the last update gave you this problem.

Or it might be a new way around pop-up and ad blockers (an as of today unfixed bug / security hole). 

And the DNS server is of interest because a rogue DNS could send you to a proxy that gets the page you request from the original site you want  and injects additional data and code  into the pages.

---

### Post by sasafrass452 on 2015-01-19
Well, I did take a look at my extensions & saw one that I don't remember installing(but probably did). It looks harmless, but I disabled it so I'll see what happens. If that tab is going to show up again, it shouldn't be long....

What you describe as a rogue DNS doesn't sound like the reason for this issue. As I said in my original post, it's a seperate background tab that appears at random.

> **Holger_Gehrke said:**
> Try firefox in safe mode for a while by starting it from the command line with 'firefox -safe-mode'. This disables all third party extensions temporarily. If the problem does not come up, then that's a strong indicator that it **is** one of your add-ons. Might be that the author of one of your add-ons has '*gone to the dark side*' and the last update gave you this problem.

Or it might be a new way around pop-up and ad blockers (an as of today unfixed bug / security hole). 

And the DNS server is of interest because a rogue DNS could send you to a proxy that gets the page you request from the original site you want  and injects additional data and code  into the pages.

---

### Post by bashiergui on 2015-01-19
> Is there a program you would recommend to get rid of it?As was previously stated, noscripts and adblock plus unless the issue is caused by a bad addon. I know you're convinced it can't be one of your extensions but it most likely is. As previously stated, good addons can become bad overnight.

---

### Post by sasafrass452 on 2015-01-19
I said above that I looked over my extensions(which are only a few) & disabled one that didn't look familiar. The popunder tab hasn't appeared since, so I'm hopeful it won't show up again. I'll give it a little more time to be sure....

> **bashiergui said:**
> As was previously stated, noscripts and adblock plus unless the issue is caused by a bad addon. I know you're convinced it can't be one of your extensions but it most likely is. As previously stated, good addons can become bad overnight.

---

### Post by dragonfly41 on 2015-01-19
Add YesScript to the list .. [https://addons.mozilla.org/en-US/firefox/addon/yesscript/](https://addons.mozilla.org/en-US/firefox/addon/yesscript/)

It is a javascript blacklisting tool.

---

### Post by bashiergui on 2015-01-19
> **sasafrass452 said:**
> I said above that I looked over my extensions(which are only a few) & disabled one that didn't look familiar. The popunder tab hasn't appeared since, so I'm hopeful it won't show up again. I'll give it a little more time to be sure....Good to hear. 

If it does solve your issue please come back and mark the thread as "solved".

---

