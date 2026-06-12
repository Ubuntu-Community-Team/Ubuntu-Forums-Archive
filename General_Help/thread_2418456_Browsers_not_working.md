---
title: "Browsers not working"
date: 2019-05-07
forum: General Help
---

### Post by Macamba on 2019-05-07
Today I booted my Ubuntu 18.04.02 system. When I wanted to go onto the internet my Firefox (66.0.3) did not start. Fiddling around a bit I saw a browser window appear and disappear in a flash. I tried installing another browser (Gnome). After a reboot no Gnome browser window appears. So I have a problem going on the internet. Any1 a suggestion?

(FWIW, Atm I browse with my mobile).

---

### Post by speartip on 2019-05-07
Try renaming the .mozilla folder in your home folder to .mozillaold or something. Then see if Firefox opens & works, with a clean configuration.

---

### Post by MoebusNet on 2019-05-07
I think I saw an article stating that Mozilla had deactivated browser add-on's in an update. Might that be causing your issues since all of the browsers use the same Chrome engine now?

---

### Post by kc1di on 2019-05-07
Go to a terminal and type this command and post what error messages you get.
```
firefox %u
```

I'm not familiar with any gnome browser.  Did you mean chrome by any chance.

---

### Post by Macamba on 2019-05-09
> **speartip said:**
> Try renaming the .mozilla folder in your home folder to .mozillaold or something. Then see if Firefox opens & works, with a clean configuration.
That seemed to work. I am typing using FireFox. Import my bookmarks? How about my (tab) history

> **MoebusNet said:**
> I think I saw an article stating that Mozilla had deactivated browser add-on's in an update. Might that be causing your issues since all of the browsers use the same Chrome engine now?
That could very much be the cause of my predicament.  

> **kc1di said:**
> Go to a terminal and type this command and post what error messages you get.
```
firefox %u
```

I'm not familiar with any gnome browser.  Did you mean chrome by any chance.
You are right. It was the Chrome browser. Autocorrect? :D 
Before moving my .mozilla folder I tried your suggestion. Nothing happened. While typing this text I tried it, and was directed to [http://www.%u.com/]("http://www.%u.com/")

I see they completely changed the interface of Firefox. After importing my bookmarks they are not shown as bookmark toolbar on top of my page. Why change a winning team :mad:

Thanks all for your help.

---

