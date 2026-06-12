---
title: "Ubuntu, Zimbra and Untangle"
date: 2008-02-05
forum: General Help
---

### Post by wjhildreth on 2008-02-05
Hello all,

I have to admit, with the discovery of Ubuntu life has been better for me in a rural hospital IT role. I use Ubuntu server to run Zimbra Open source, and since then have found Untangle. An excellent Open source project that filters, allows easy configuration of OpenVPN and a host of other things. So all in all, the Open Source folks have been a financial life saver for small hospitals with very little to non existant IT budgets. But as you are likely aware, the more you give the more some folks want.

I found myself in the CEOs office this morning receiving another request. I want an internal messaging system, where I can send employees messages, post memos and policies and procedures, etc, etc. You know the story.

Well I have been thinking about her request and am thinking that another Ubuntu server with a LAMP install. But the big question is what you use as a medium. At first I thought maybe a CMS of sorts would do what she wants, Provide private messages through forums, a place to post files and that sort of thing. The problem is that solution could keep me too busy and away from other more important things.

So my question is this, what would you suggest as a solution to meet the following requirements without overloading in features?

1) Ability for internal (only) email or messaging. 
2) A depository for shared frequently used documents (P&Ps, FAQ, FORMS)

Many thanks for your time and energy.

Warm Regards,

Joe Hildreth
Tennessee

---

### Post by bodhi.zazen on 2008-02-05
Well, why not Zimbra ? Zimbra will do it all for you (They just added IM to the opensource package, it is in Beta, but it is working). Zimba also allows public documents for your FAQ and will handle your email.

---

### Post by wjhildreth on 2008-02-05
I thought about that too, but will Zimbra run on an internal network without outside connectivity? Do I just set up an internal DNS record to point to it and leave it at that? She does not want to allow regular employees to sent and receive internet emails with it. But I will admit you are quite right, Zimbra has all the capability I am looking for.

I think your suggestion has merit and maybe I should try that.

Any other suggestions?

Warm Regards,

Joe Hildreth
Tennessee

---

### Post by haxor999 on 2008-02-08
Alternatively, one of the many open or proprietary [wiki's]("http://en.wikipedia.org/wiki/Wiki") could be what you need - they take CMS to the next level and work well as knowledge/document sharing systems in large organizations.

Couple of suggestions, based on my experience (with links)
- [Confluence]("http://www.atlassian.com/software/confluence/") (proprietary, but most featureful and may be worth the cost)
- [Dokuwiki]("http://wiki.splitbrain.org/wiki:dokuwiki") (simple and efficient)
- [MediaWiki]("http://www.mediawiki.org/") (used by wikipedia, complex and featureful)
- [TWiki]("http://twiki.org/") (also complex and featureful)

See [this link]("http://en.wikipedia.org/wiki/Comparison_of_wiki_software") for many more.

Hope that helps :)

---

