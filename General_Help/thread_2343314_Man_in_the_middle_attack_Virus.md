---
title: "Man in the middle attack? Virus?"
date: 2016-11-15
forum: General Help
---

### Post by Coriander Redgoat on 2016-11-15
Hello,

Whenever I visit banking sites I get something like 

**> Your connection is not private**

> [FONT=Ubuntu]Attackers might be trying to steal your information from [/FONT]**[www.bankofamerica.com]("http://www.bankofamerica.com")**[FONT=Ubuntu] (for example, passwords, messages, or credit cards).[/FONT]


This doesn't happen on other sites or with other computers.

What's happening? How do I fix it?

Thanks!

---

### Post by TheFu on 2016-11-15
Could be any number of issues. Cannot tell from the data provided.  Check that your DNS is correct and trustworthy - that is really a name resolution question, so any overrides that may be happening in /etc/hosts and other methods like NIS should be checked too. 

Also check that the root certificates are what you intend.  

The answers to those questions require judgment on your part.  What I would consider ok might be an issue for you or vice versa.

Or all of this could just be a configuration issue with the browser you are using. Try a different browser.  Actually, I don't do online banking from the same system I use daily.  Brian Krebs has this advice: [https://krebsonsecurity.com/2012/07/banking-on-a-live-cd/](https://krebsonsecurity.com/2012/07/banking-on-a-live-cd/) There are other ways to achieve similar security with more convenience, but not as bonehead simple as using a liveCD boot.

---

### Post by speartip on 2016-11-15
Does this happen when you visit the page? ie. the bank of america you listed above. Or only when you try & login?
If it's the former then list a few of the webpages so others can check them out. also what web browser are you using?

---

### Post by Bucky Ball on 2016-11-15
Guessing its when you try and login as just visited that link without issue.

---

### Post by oldrocker99 on 2016-11-15
Are you using [http://address](http://address), or [https://address?](https://address?)

This might help with that:[https://www.eff.org/https-everywhere%20](https://www.eff.org/https-everywhere%20)

This is from the Electronic Freedom Foundation, and they are **definitely** on your side.

---

### Post by &amp;KyT$0P# on 2016-11-15
Coriander Redgoat, are you on Chrome/Chromium?  If so, see [this]("https://ubuntuforums.org/showthread.php?t=2343147").

---

### Post by Coriander Redgoat on 2016-11-16
Thanks for the replies!

> [COLOR=#000000]Check that your DNS is correct and trustworthy - that is really a name resolution question, so any overrides that may be happening in /etc/hosts and other methods like NIS should be checked too. [/COLOR]

[COLOR=#000000]Also check that the root certificates are what you intend. [/COLOR]


I don't know how to check those.

This is a problem I see in Chromium, but it doesn't appear in Firefox.

> [COLOR=#000000]Does this happen when you visit the page? ie. the bank of america you listed above. Or only when you try & login?[/COLOR]

When I visit the page.

> [COLOR=#000000]Are you using [/COLOR][http://address]("http://address/")[COLOR=#000000], or [/COLOR][https://address?]("https://address/?")

using [http://address]("http://address/"), but [http://address]("http://address/")? also produces the same result.

The fact that it only comes up on banking and shopping websites (came up on overstock.com) is suspicious to me. Also, Amazon was slow loading on this computer but not my other one, related?

---

### Post by TheFu on 2016-11-16
If only 1 browser, then that removes the DNS question.  I think there are certs and handling of certs that are different for every browser. 
I vaguely remember that Chromium doesn't like mix-mode websites - those with both HTTPS and HTTP content. This is a good thing, but not all websites are implemented that way. When that code drops on the main Windows browsers, all those sites will get fixed.  Assuming this is actually the issue.

If you run the browser from a terminal, are there any messages to stderr or stdout? Those could be helpful in determining the root issue too - at least for someone who knows what they mean (not me).

---

### Post by courtney2 on 2016-11-17
I think it's just chromium. I can confirm the problem persists on chromium on my PC too

---

### Post by kpatz on 2016-11-17
There was an chromium update rolled out yesterday that fixes the certificate issues.  Try doing an update and see if that fixes it.

---

### Post by LifeEnemy on 2016-11-17
[COLOR=#000000]I've had the same problem on 14.04 with Amazon.com and nytimes.com (this one loaded, it just showed a bunch of plain text and broken links).[/COLOR]

[COLOR=#000000]The most recent update to chromium seems to have solved the issue though, after restarting the browser.[/COLOR]

---

### Post by Coriander Redgoat on 2016-11-19
I updated chrome and that seems to have fixed it. Thanks for the help everyone!

---

### Post by Bucky Ball on 2016-11-19
Great news. Please use Thread Tools at the top right to mark the thread as 'solved' to help others or see the blue link in my signature at the bottom of this post for how. Thanks.

---

