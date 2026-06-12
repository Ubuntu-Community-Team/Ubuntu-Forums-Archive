---
title: "Security question - visited site with popup ads (tinypic.com)"
date: 2014-12-23
forum: General Help
---

### Post by Nick_W on 2014-12-23
Hi,

Rather stupidly I followed a link to tinypic.com on a Google newsgroup which I generally trust.

It showed me a harmless enough picture but more worryingly a popup add appeared. Wikipedia page for tinypic suggests it is a site with a risk of viruses (obviously more a windows issue than Linux)

As soon as this happened I closed the site, and for extra security (I am aware of XSS) I changed the password on my gmail account, open at the same time.

I am using 12.04 LTS (up to date with latest updates).

Is there anything else I should do for security? Run rkhunter perhaps... anything else or do people think that is sufficient?

I've been meaning to upgrade to 14.04 for a while, perhaps now would be a time to do so as presumably an upgrade would clear any potential security concerns.

Thanks,
Nick

---

### Post by DuckHook on 2014-12-23
> **Nick_W said:**
> ...presumably an upgrade would clear any potential security concerns.Not necessarily. If a nasty script is residing in your browser cache, then nothing less than a pristine install that wipes that cache will suffice. On the other hand, there's no need to panic either. [This]("http://ubuntuforums.org/showthread.php?t=2256328&page=2&p=13187626#post13187626") recent thread dealt with similar issues, especially the part about installing security add-ons to your browser. Try installing NoScript and Better Privacy first, and see what they manage to clean out. You might be surprised at what's already there, and nothing having to do with tinypic.com. While you are at it, you may as well install the other stuff too.

BTW, your instincts are sound. Pat yourself on the back for being vigilant.

---

### Post by beep3 on 2014-12-23
> **Nick_W said:**
> Wikipedia page for tinypic suggests it is a site with a risk of viruses

Wikipedia mentions that one of the criticisms of TinyPic is that it often shows ads that link to virusses and malware - not that the website itself hosts virusses. I had a quick look at the site and I think that the pop-up you saw was one of those ads. As long as you didn't click on the ad you should be fine.

As an aside, I'd recommend Adblock Plus and Disconnect - the interwebs look a lot nicer without all the junk you get thrown at you on sites like TinyPic ;).

---

