---
title: "How to install Mozilla firefox 2.0b2 in Ubuntu???"
date: 2006-09-16
forum: General Help
---

### Post by muffinhead on 2006-09-16
Hi all, I recently downloaded the 2nd Beta of firefox 2.0 to give it a try, and was quite impressed. However I'm having a problem installing it in Ubuntu 6.06 LTS Dapper Drake.


I first downloaded the linux tar.gz binary of firefox 2.0b2, and converted it into a .Deb file using sudo alien firefox.tar.gz --to-deb, so I could install it.

However when trying to install the converted .deb file, I get the following error:

```
dpkg: regarding firefox.deb containing firefox:
 mozilla-firefox-locale-en-gb conflicts with firefox (>> 1.5.z999)
  firefox (version 2.0b2-2) is to be installed.
dpkg: error processing firefox.deb (--install):
 conflicting packages - not installing firefox
Errors were encountered while processing:
 firefox.deb
```

So I then Proceeded to uninstall the previous installation that came default with Dapper Drake,  firefox 1.5.0.3 using synaptic. However that did not help, and I still got that error again.

I then manually searched for all the files of firefox left from the previous version of firefox, and manually deleted them, which also did not help.

So I try to search out the conflicting package "firefox (1.5.z999)" using the search function in ubuntu, and it doesn't find any such package or file.

Can someone help me with installing firefox 2.0 beta2? I know it's still a beta, but it works well enough for me to use, and I haven't had any problems with it yet.

Thank You, if anyone can help:)

---

### Post by Alekc on 2006-09-17
If you want to use your method (with alien) you can go in synaptic, find firefox 1.5 go in Package->Lock Package.

After that install firefox beta2 with dpkg (i'm not sure why but in this mode it installs firefox in the "/", weird...). 

For other installation methods search forum for "firefox 2 beta 2 installation" 8-)

---

### Post by muffinhead on 2006-09-17
Thanks for your reply, I just found the solution a little bit ago, after researching a bit. Sorry I posted without searching first, I honestly didn't think someone else posted about this as well.

I went to my /usr/lib/ directory, renamed previous firefox folder to firefox.old, And put the New Beta in there, and I was good to go.

I sorta forgot about this thread (I'm usually busy posting on other forums as well), And didn't notice it again till I just went looking in general discussion before I posted this message, that why I didn't reply back to say I found a solution.:wink:

---

