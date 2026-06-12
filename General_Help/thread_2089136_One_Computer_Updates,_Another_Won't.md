---
title: "One Computer Updates, Another Won't"
date: 2012-11-28
forum: General Help
---

### Post by wmichaelb on 2012-11-28
I'm running 10.04 on both my desktop and laptop. When Firefox updated to version 17 on both machines, the discovery.com web site ceased to render correctly; it became all text with no graphics. Then, after a couple of weeks, an update came through on my desktop that fixed the problem.

However, that update hasn't become available on my laptop running exactly the same version of everything. Is there some way to match repositories, certificates, etc. so that I can get Firefox up to date on both systems?
                                                             :confused:
Thanks in advance!

---

### Post by 2F4U on 2012-11-28
- Are both machines the same architecture (32/64 bit)?
- Do they use the same repositories (/etc/apt/sources.list)?
- Do they use the same mirrors?

---

### Post by wmichaelb on 2012-11-29
Interesting. Both machines are all the same, with but one difference. The laptop includes:

[http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu)

but the desktop does not. However, when I try to check, I get an error message that states:

Failred to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)
404 Not Found

Some index files failed to download, they have been ignored, or old ones used instead.

Might I ask where your Firefox upgrades come from?

Thanks!

---

### Post by plucky on 2012-11-30
> Might I ask where your Firefox upgrades come from?


I am on 10.04 64-bit and Firefox 17 which comes from the Universe repository.

Your PPA does not have any files to fetch.

See [Here](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/)

Good Luck

---

