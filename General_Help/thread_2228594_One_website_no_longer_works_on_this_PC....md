---
title: "One website no longer works on this PC..."
date: 2014-06-08
forum: General Help
---

### Post by secuono on 2014-06-08
I've been able to use Webs.com before, up until last week. It suddenly won't work and I haven't done any upgrades or changes to the computer at all. 

This is what I need to get to, to edit my site. 
[http://members.webs.com/s/sitebuilder/](http://members.webs.com/s/sitebuilder/)

I can go to the regular site, no issues. 
[http://www.webs.com/](http://www.webs.com/)

But if I try to sign in, it goes back to the slow loading and never getting anywhere! 

Loading icon slowly swirls around for ages, eventually a blank window with-

 " This webpage is not available " pops up. 
Click on MORE button-

"Chromium could not load the webpage because members.webs.com took too long to respond. The website may be down, or you may be experiencing issues with your Internet connection.
Check your Internet connection.
Check any cables and reboot any routers, modems, or other network devices you may be using.
Allow Chromium to access the network in your firewall or antivirus settings.
If it is already listed as a program allowed to access the network, try removing it from the list and adding it again.
If you use a proxy server...
Check your proxy settings or contact your network administrator to make sure the proxy server is working. If you don't believe you should be using a proxy server: Go to the Chromium menu > Settings > Show advanced settings... > Change proxy settings... and make sure your configuration is set to "no proxy" or "direct."
Error code: ERR_CONNECTION_TIMED_OUT"


How can I get it working again? Is there some new update the website did that now makes me need to update something to work?
I'm using Chromium browser, if that matters any.

I really don't want to have to BUY another computer with Windows on it just to be able to use this site again....

---

### Post by buzzingrobot on 2014-06-08
> **secuono said:**
> 

I really don't want to have to BUY another computer with Windows on it just to be able to use this site again....

That's a bit extreme.

Chromium is telling you that the server it's trying to access is not responding. While it's certainly possible that something else is going on, the overwhelming odds are that the server is offline, for maintenance or due to a malfunction.

If it is offline, any other browser should produce similar results.  If not, and you can access the server in another browser, then you might look at Chromium's settings.

---

### Post by sgage on 2014-06-08
Have you tried it with Firefox or some other browser? That would be my first line of trouble-shooting.

---

### Post by Rex Bouwense on 2014-06-08
sgage and buzzingrobot offer excellent advice.  If you cannot get to any sites I would suspect a problem with your browser.  It more likely however that the server is the problem and has nothing to do with your computer.

---

### Post by LastDino on 2014-06-08
Those ''web builder tool'' are taking way too long to load for me too, I tried that with both FF and Chrome. Like everyone has said, I don't think it is Ubuntu's fault though. I wasn't getting anything downloaded or download speed indicator was showing  ''0 to minimum Kb/s'' when I was loading that site, which means; there is problem at their end.

---

### Post by secuono on 2014-06-08
It's been all week like that. 
Just installed Firefox, it's still trying to load...
This sucks. =( I wonder what the issue is on their end...

Thanks all, guess I'll just wait it out or email them later today.

---

### Post by secuono on 2014-06-08
Thanks all.
I found their help page and this thread-
[http://webs.zendesk.com/entries/36118780-Unable-to-Access-Webs-com-Your-site-or-Images-not-Appearing-on-your-site-SUPPORT-637?page=4#post_22597040](http://webs.zendesk.com/entries/36118780-Unable-to-Access-Webs-com-Your-site-or-Images-not-Appearing-on-your-site-SUPPORT-637?page=4#post_22597040)


Looks like lots of people are still having issues....

---

### Post by Rsxhawk on 2014-06-09
You could always add google's DNS servers to your network configuration as a backup in case your ISP's DNS servers are having issues.  I know just recently my wife was trying to browse certain sites using Chrome on her macbook but had more or less the same issue you speak of, "the webpage is not available".  I tested this by seeing the same issue on my wired pc (running Ubuntu) as well so I simply added 8.8.8.8 as a backup DNS server on her macbook's network properties and voila, the page loaded immediately.  Sometimes issues like this have nothing to do with your operating system.  Sometimes its a situation like mine where the internet link to my ISP was fine, my internal network was fine, but my ISP's DNS servers were not functioning correctly at that time so requests for web-site names could not be resolved.  I'm not saying this is what happened in your case, it could very well be an issue with the provider of the website.  I'm just offering a backup method to ensure you can at least resolve DNS names via multiple sources.

---

### Post by CharlesA on 2014-06-09
Funny thing, [http://members.webs.com](http://members.webs.com) redirects to [http://webs.com](http://webs.com)

I can't access the site builder from my VPS either, so my bet is they move that resource elsewhere and their server isn't set to respond with a 404 error.

This may be helpful:
[http://support.webs.com/webs/topics/how_to_update_to_sitebuilder_3](http://support.webs.com/webs/topics/how_to_update_to_sitebuilder_3)

---

