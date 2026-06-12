---
title: "Kubuntu help"
date: 2007-07-27
forum: General Help
---

### Post by Smackie07 on 2007-07-27
I just downloaded Kubuntu i have ubuntu on my computer right now but im trying to use Kubuntu to delete ubuntu off my hard drive and install it but when i try doing a install it will keep beeping and then shutting the install window down on me and then i get a window about ubiquity.. and it says

> **Sorry, the program "ubiquity" closed unexpectedly.**

If you were not doing anything confidential (entering passwords or other private information). you can help to improve the application by reporting the problem. 


is there a way to fix this? 

Please help me

Thank you 
Smackie07

---

### Post by HermanAB on 2007-07-27
Did you test the disc?  Calculate the MD5 sum of the whole disc and compare it with the sum on the server you downloaded it from.  There is no point in trying to debug these issues if the disc is bad - a common problem.

Cheers,

Herman

---

### Post by Smackie07 on 2007-07-27
ok i had 1 error on cd so i redownloaded it put it on cd again and i got it installed then rebooted went to windows to play a few games of Dangerous Waters with some friends and then rebooted went to Kubuntu to start installing some programs and stuff and for some reason it will come up to a root@smackie-desktop  and i can't get passed that part i mean i tried recovery and it does the same and then i tried reinstall and its doing what it was doing last night and the cd still has no errors can someone help me here?

and can someone show me where i can download Ventrilo 2.1.4? I can't use the newest one since a group of friends we use 2.1.4 and don't support the new ones. 

Thank you 
Smackie07

---

### Post by modelmark on 2008-01-06
it' strange I had this problem so many times, how difficult can it be to burn/read a disc correctly. Isn't there some other problem ?

---

### Post by der_joachim on 2008-01-06
You can install the kubuntu desktop in your current ubuntu installation, Just open up a terminal and issue the following command
```

sudo apt-get install kubuntu-desktop

```
That way you can run Gnome and KDE alongside. If you really dislike one of them, you can remove the desktop packages by ```
sudo apt-get delete blah-desktop
``` where blah is either ubuntu or kubuntu.

You can download the Ventrilo server [here]("http://www.ventrilo.com/download.php"). There is no client (yet?), but you can try to make it work in wine. See the wine subforum for details.

---

