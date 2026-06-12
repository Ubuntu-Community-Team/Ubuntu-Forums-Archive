---
title: "Chromium is broken on Ubuntu 14.04"
date: 2016-11-15
forum: General Help
---

### Post by glennra12 on 2016-11-15
A recent update appears to have broken the Chromium browser on Ubuntu 14.04.  Numerous web pages no longer render correctly.  A couple of examples are Bloomberg.com, and the archive pages of Tumblr blogs.  This happens with the "Guest" login, so it is not a user settings issue.  I've observed it on multiple machines.  Broken pages render correctly in Firefox, so it is not a server-side problem.  Has anyone else seen this?  I don't know enough about web development or browser architecture to troubleshoot the problem further.

Bloomberg on Firefox (left)
Bloomberg on Chromium (right)

[ATTACH=CONFIG]272165[/ATTACH][ATTACH=CONFIG]272164[/ATTACH]

---

### Post by TheFu on 2016-11-16
On 16.04, bloomberg seems to be working.  Remoted into a 14.04 box, I can confirm the issue for me as well.

BTW, both are 64-bit systems and report running the same release of Chromium.
Version 53.0.2785.143
Version 53.0.2785.143 


Checked a 3rd 14.04 system (32-bit) - same issue. Interesting. 
Seeing a little output in the terminal - ```
getrlimit(RLIMIT_NOFILE) failed
```

Just started chromium outside a container on 16.04 and visited bloomberg - seeing the same issue this time. Interesting.

Do you use an add blocker or block some systems through /etc/hosts? I do.
[https://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file](https://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file)

---

### Post by mc4man on 2016-11-16
Maybe the same thing that's been showing up in chromium on a number of sites, something to do with certificates, (transparency of some sorts) so the site is considered unsafe (Ex. of directly seeing go to lowes.com
In those cases if one proceeds they get that type of page you're seeing. If I go to any link on bloomberg it becomes a bit more obvious - screen.

Not an issue in google-chrome stable, beta or canary

---

### Post by mc4man on 2016-11-16
See here - 
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1641380](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1641380)

---

