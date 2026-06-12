---
title: "Hardy Java - FF Yes, Swiftweasel No"
date: 2008-04-29
forum: General Help
---

### Post by drs305 on 2008-04-29
Solved: Apparently swiftweasel wasn't seeing the installed java. I added the following and it started working. Read on if you can't get swiftweasel working in 32 bit hardy but ff does.
```

sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins

```

*****

Original Post:
I can't get swiftweasel to run java in hardy (32-bit) after updating via synaptic. To access my company's site in previous versions I had to use sun java. After installing hardy, I had to remove openjdk and icedtea and install/keep sun-java6 to get the site to work with firefox. The apps I currently have installed are sun-java6-bin, sun-java6-jre, sun-java6-fonts, and sun-java6-plugin. Firefox 3.0b runs java fine. 

I cannot get swiftweasel to run the site (proprietary to company, so I can't give the address). It worked fine in swiftweasel/gutsy. When I try to open the page I get the missing plugin message, saying I need to install jre. It is already installed and reinstalling doesn't help.

I have:
Tried running with both icedtea, openjdk and java6 all installed.
Each separately removed and reinstalled.
Removed and reinstalled swiftweasel, versions 2.0.0.12 and 2.0.0.14.  (pentiumm for a laptop celeron)
Still can't get it to work.
I've enabled the swiftweasel repository. My laptop is a celeron m. Since there is no listing for that one, I currently have installed swiftweasel-pentiumm 2.0.0.14.

It's probably something as simple as a link, but I need some help getting it done. And if it is a link, I'd like the command or details on how to make it if possible.

Thanks for your help.

---

### Post by Absolom on 2008-05-01
Well that fixed it for me thank ou so much it's been annoing me ever since m upgrade.

---

### Post by c0oL-SG on 2008-05-28
Great tip! Thanks man!:KS

---

