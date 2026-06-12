---
title: "Heartbleed OpenSSL bug and do I have a problem?"
date: 2015-05-29
forum: General Help
---

### Post by Mark_in_Hollywood on 2015-05-29
I saw a tool on a Facebook page today and clicked the link. It was all Italian, so I left that page and tried to find it in English. A Google search of the keyword, brought up the company and a Hearbleed OpenSSL warning in my Chrome Browser page. See screenshot, below.

Do I have a problem by visiting the original compromised webpage? I did not send any information only saw their website's page. If I have a problem, how do I check for that and fix it?

---

### Post by grahammechanical on 2015-05-29
The heartbleed vulnerability in OpenSSL goes back more than a year. And was patched in hours of Linux developers being made aware of it. Ubuntu developers quickly provided a patched version of the OpenSSL library that corrected the hazard through the normal update channels. Then this vulnerability would have been closed by the maintainers of OpenSSL.

[http://askubuntu.com/questions/444702/how-to-patch-the-heartbleed-bug-cve-2014-0160-in-openssl](http://askubuntu.com/questions/444702/how-to-patch-the-heartbleed-bug-cve-2014-0160-in-openssl)

So, is this a new vulnerability? Has your install of 12.04 been updated in the last year? Oh, by the way it illustrates the value of having Software & Updates set to display immediately when there are security updates.

[http://heartbleed.com/](http://heartbleed.com/)

Regards.

---

### Post by Mark_in_Hollywood on 2015-05-30
grahammechanical

This is Ubuntu Trusty Tahr ver. 14.04 LTS. I keep my 'puter updated as soon as updates are available.

I have a Google Chrome browser app (Chromebleed) that shows if a site is Heartbleed vulnerable. Hence the screenshot showing the two sites. I had visited one of them, looking to buy something from it. I did not send any of my info to it, other than browsing the website's pages. The un-patched OpenSSL is at the sources website server, not mine. But by visiting the site, do I have a problem?

My Facebook page had a link to the Heartbleed vulnerable site, but I did not see the warning from Chromebleed. It was only after visiting the website that I searched for other sources of the tool they sell. It was in that way, that I saw the site, before learning it was not updated to the patched OpenSSL. 

Do I have a problem on this computer?

---

### Post by SeijiSensei on 2015-05-30
If you didn't connect to the site and transmit sensitive data over the connection, no you don't have a problem.  Remember that millions upon millions of people communicated with broken SSL servers for years, yet we never saw any widespread reports of compromises.  That doesn't mean they didn't happen, but they were probably pretty infrequent.

If those are sites that you would like to visit send an email to webmaster@domain and inform them of the problem. Tell them that your browser warned you away from their site so you can't do business with them.

---

### Post by Mark_in_Hollywood on 2015-05-31
I sent the company a tweet as they don't have direct email I also posted the screenshot there, at their youtube page and sent the site registrar the same. 

Than you, Linux/Ubuntu community.

---

