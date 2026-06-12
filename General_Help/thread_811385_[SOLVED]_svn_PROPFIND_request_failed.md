---
title: "[SOLVED] svn: PROPFIND request failed"
date: 2008-05-29
forum: General Help
---

### Post by amit4g on 2008-05-29
Hi,

While trying to access a SVN repository, i am getting following error message:
amit@venus:~$ svn co [https://scst.svn.sourceforge.net/svnroot/scst](https://scst.svn.sourceforge.net/svnroot/scst) scst
svn: PROPFIND request failed on '/svnroot/scst'
svn: PROPFIND of '/svnroot/scst': could not connect to server ([https://scst.svn.sourceforge.net](https://scst.svn.sourceforge.net))

i was able to access the same link([https://scst.svn.sourceforge.net/svnroot/scst](https://scst.svn.sourceforge.net/svnroot/scst))  with my browser,what is wrong here?

~amit

---

### Post by amit4g on 2008-05-29
Asked one of my friend here and the issue got resolved.

edit ~/.subversion/server 
uncomment the global proxy setting and
replace the settings(proxy server and port) with your global proxy and port settings.

~amit

---

### Post by kleinash on 2012-03-28
> **amit4g said:**
> Asked one of my friend here and the issue got resolved.

edit ~/.subversion/server 
uncomment the global proxy setting and
replace the settings(proxy server and port) with your global proxy and port settings.

~amit


Hi - this absolutely did not work for me.. :( I am new to Linux - and have gotten as far as I can find the /etc/subversion/servers file and edit under [Global] to my proxy settings - instead of using the one that was there: defaultproxy.whatever.com port 7000 - but it didnt work - i still have the message:

could not connect to server ([http://lis-ros-pkg.googlecode.com](http://lis-ros-pkg.googlecode.com)) but the server is there - and you can connect to the website..

---

### Post by kleinash on 2012-03-28
Wohooo - Its ok :) the problem was the http vs. https - even though the request was for http - it must say https - I think that Ubuntu has a problem with http for some reason.. Very cool - day 3 of Linux and loving it.. *cool status might update from time to time ;)

---

