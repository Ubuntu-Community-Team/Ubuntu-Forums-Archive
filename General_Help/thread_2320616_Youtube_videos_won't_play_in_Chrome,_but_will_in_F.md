---
title: "Youtube videos won't play in Chrome, but will in Firefox"
date: 2016-04-15
forum: General Help
---

### Post by Gottier on 2016-04-15
Ubuntu 14.04LTS. Up until a couple days ago everything was fine, but I think Chrome had an update, and now I can't watch Youtube videos. I can watch them using Firefox, but I really want to use Chrome. Has anyone else had this problem? How can I fix it?

I tried to uninstall Chrome and re-install it in the software center. Didn't change anything.

Also, Flash in general works in Chrome, I just can't watch youtube.

---

### Post by howefield on 2016-04-16
> **Gottier said:**
> I tried to uninstall Chrome and re-install it in the software center. Didn't change anything.

That most likely wouldn't have made any difference unless you purged the install to remove the Chrome profile folders in the /home folder.

Removing or renaming the folder..

```
/home/<user>/.config/google-chrome
```

will force Chrome to recreate it afresh as if it were a new install.

---

### Post by RobGoss on 2016-04-16
Hello and welcome, Have you try Chromium? I had to switch once I found out that the 32-bit of Google chrome was drop from Google support not sure if that has anything to go with your problem but it might be something to consider

---

### Post by Gottier on 2016-04-16
> **howefield said:**
> That most likely wouldn't have made any difference unless you purged the install to remove the Chrome profile folders in the /home folder.

Removing or renaming the folder..

```
/home/<user>/.config/google-chrome
```

will force Chrome to recreate it afresh as if it were a new install.

I tried to rename the folder, but it didn't help. Still can't see the videos. I can hear them, just not see them.

---

### Post by Gottier on 2016-04-16
> **RobGoss said:**
> Hello and welcome, Have you try Chromium? I had to switch once I found out that the 32-bit of Google chrome was drop from Google support not sure if that has anything to go with your problem but it might be something to consider

I'm on a 64 bit computer. I've used Chromium in the past. Honestly, I can't remember why I just wanted to use Chrome instead.

---

### Post by Gottier on 2016-04-16
So I did this:

```

sudo apt-get purge google-chrome-stable
sudo apt-get install google-chrome-stable

```

but still can't see the videos

---

### Post by RobGoss on 2016-04-17
What do you see when you try to view a video on YouTube what message are you greeted with?

I came across this post that might shed some light o this problem
[http://askubuntu.com/questions/301950/why-wont-youtube-videos-play-but-all-other-websites-work-fine](http://askubuntu.com/questions/301950/why-wont-youtube-videos-play-but-all-other-websites-work-fine) 

You might want to also install [B][COLOR=#111111][FONT=Ubuntu]Ubuntu Restricted Extras package

[/FONT][/COLOR][/B]```
[COLOR=#111111][FONT=Consolas]sudo apt-get install ubuntu-restricted-extras[/FONT][/COLOR]
```

Then update
```
[COLOR=#111111][FONT=Consolas]sudo apt-get  update[/FONT][/COLOR]
```

Reboot your machine after installing the **U[COLOR=#111111][FONT=Consolas]buntu-restricted-extras[/FONT][/COLOR]**

---

### Post by QLee on 2016-04-17
@ RobGoss You might want to suggest doing an update first then the install. In some cases it could make a difference and it is usually recommended to update the package lists first, with the command```
 sudo apt-get update
```

In addition, that other command you gave "sudo apt-get install update" isn't a  correct command and will fail.

---

### Post by RobGoss on 2016-04-17
> **QLee said:**
> @ RobGoss You might want to suggest doing an update first then the install. In some cases it could make a difference and it is usually recommended to update the package lists first, with the command```
 sudo apt-get update
```

In addition, that other command you gave "sudo apt-get install update" isn't a  correct command and will fail.

Thanks for pointing out the command error corrected must have over look that, Yes it's always good to update your system first it won't hurt I was thinking he would have his system updated anyways. I always update when ever I turn my machine on but then again I'm a neat freak also :cool:

---

### Post by QLee on 2016-04-17
> **RobGoss said:**
> ...I was thinking he would have his system updated anyways. I always up when ever I turn my machine on but then again I'm a neat freak also :cool:

If I remember correctly, the default setting in software updater is daily but some people don't want it to happen (sometimes metered bandwidth or other restrictions) so they turn it off. I leave mine on but if a repository is updated after your system's daily check you'll get a fault and have to do the update before the install anyway. Not a big deal either way, type a few more characters sometimes.  Cheers.

---

### Post by mcduck on 2016-04-17
Youtube shouldn't care about Flash any more, they've switched to using the HTML5 video player a good while ago. If you go to [this web page]("https://www.youtube.com/html5") with each browser, what does it say?

---

### Post by zdenek-zikan-m on 2016-04-18
I have exactly the same problem. The Youtube HTML5 test page says that all the technologies are supported by my browser. It's not only Youtube, it's all HTML5 videos that have the same problem. Running Ubuntu 15.04, Chrome  50.0.2661.75 64bit.

---

### Post by Richard_Romick on 2016-04-18
What if you go to the youtube HTML 5 site?  Are all the boxes checkmarked?

[https://www.youtube.com/html5](https://www.youtube.com/html5)

---

