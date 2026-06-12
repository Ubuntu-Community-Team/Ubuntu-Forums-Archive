---
title: "Online Accounts: Unable to access Nextcloud due to expired certificate which is wrong"
date: 2021-10-10
forum: General Help
---

### Post by uichael on 2021-10-10
Hello,

I'm running Ubuntu 20.04.2 on my Laptop. I'm using Ubuntu's integrated "Online Accounts"-Settings to access my own nextcloud-Server, which worked absolutely fine until now. Now it won't connect anymore, it says that my nextcloud server's certificate has expired - which is not true, i did run 'certbot renew' via CLI on the server and it stated that it doesn't need renewal until december. Accessing the server via any other of my devices (Browser on Windows, Windows Client, Android Client) is also working fine. So it's pretty clear that there is no problem with the nextcloud server's certificate, but with my Laptop / Ubuntu's Online Account thing.

What can i do? Happy for any suggestions.

---

### Post by TheFu on 2021-10-10
Is the system fully patched?  Wasn't there a new CAcert package deployed which updated all our certs.

Got a bunch of new CA files on Sep 22, so something must have changed.  Look in /usr/share/ca-certificates/mozilla/  . 

My nextcloud isn't having issues, well, unless you think webdav as a protocol sucks.  Any webdav connection is like a denial of service attack here.  Over 60 seconds to use tab completion or just do an ls.

---

### Post by uichael on 2021-10-11
Hello The Fu,

Thank you for answering. I'm not sure i did get everything since i'm a hell of a noob (with a lot nerve, given the fact i went on having a own nextcloud server). I also experienced that connecting via webdav is no option (neither ubunto nor windows, for different reasons, ubuntu webdav takes in fact ages to load, if any). So i was very happy with the neat online account integration in ubuntu.

So, did i get you right with you saying that i should see if my ubuntu system has all the updates and that i should look in the [COLOR=#000000]/usr/share/ca-certificates/mozilla/  folder for....what exactly? Again, sorry, noob..[/COLOR]

---

### Post by TheFu on 2021-10-11
> **uichael said:**
> Hello The Fu,

Thank you for answering. I'm not sure i did get everything since i'm a hell of a noob (with a lot nerve, given the fact i went on having a own nextcloud server). I also experienced that connecting via webdav is no option (neither ubunto nor windows, for different reasons, ubuntu webdav takes in fact ages to load, if any). So i was very happy with the neat online account integration in ubuntu.

So, did i get you right with you saying that i should see if my ubuntu system has all the updates and that i should look in the [COLOR=#000000]/usr/share/ca-certificates/mozilla/  folder for....what exactly? Again, sorry, noob..[/COLOR]

Are the files old or recent?  Look at the atime and ctime timestamps.

> Got a bunch of new CA files on Sep 22, so something must have changed. Look in /usr/share/ca-certificates/mozilla/ .


As for being up-to-date, just run
```
sudo apt update
sudo apt full-upgrade 

```every week and that will keep your system patched. If there are any errors or things that look bad in the output, STOP!  Fix it ASAP.  When a system can't be patched, it is like a tiny like in your roof.  Tiny leaks always get worse. They never magically fix themselves. The same applies to Linux patching.  It will never get corrected by magic.

---

### Post by uichael on 2021-10-12
Hello the Fu,

the update just did it - i could think of that myself actually ;)

i googled and did run 'sudo apt-get update && sudo apt-get dist-upgrade' which actually did end up in some major 550MB+ update. So it was about time...ehem. Nextcloud Online Acounts integration works nice again.

Will keep it updated from now on....sorry to bother and thanks again!

MK

---

### Post by TheFu on 2021-10-12
a) if this is solved, please use the thread tools button in the upper-right to choose that - "SOLVED".
b) Ubuntu doesn't automatically "update" the repos like some other linux distros do.  Good or bad, that's a matter of opinion.  If you patch weekly, like you should, then it doesn't become an issue.

"dist-upgrade" is an unfortunate name for the **apt** or **apt-get** option. It is the same as "full-upgrade"
There are a few other commands that need to be run from time to time too. Be certain you do those as well. An article I wrote about 10 yrs ago was picked up by a popular website ... I've updated that article about once every other year with the latest information. It is here: [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) last update was May of this year.  Do those things on your desktops. Many are preventive maintenance - to avoid problems.  That is always better than having to fix an issue.

---

