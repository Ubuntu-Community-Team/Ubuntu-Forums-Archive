---
title: "Firefox automatically closes"
date: 2006-12-07
forum: General Help
---

### Post by jaakw on 2006-12-07
Hellow. 
I installed Ubuntu (6.06) on one small office. The user of that computer (she has desktop user rights) run Firefox and open a webpage that conteined flash animation. Default Firefox does not have plugin for that reason and asked for dovnloading Shockwave player. The user don't know enything about user rights and download it and tried to inastll it. Seems it dos'd successful. After that always when Firefox opens page with flash the program closes automatically. 
Can enyone tell me how can I fix this problem?
Thanks.
Jaak

---

### Post by bscbrit on 2006-12-07
No - but I encountered the same problem 2 days ago.  I solved it by uninstalling the flash plugin.  I'm still investigating the real cause.

---

### Post by evilc on 2006-12-07
Sound like flash may not be installed, go to macromedia site and check. If it is installed you should see a small flash notice on the site page. Also check if running noscripts that will stop any second page opening.

---

### Post by bscbrit on 2006-12-07
evilc - No, my problem is that when flash _is_ installed, then Firefox bombs.  Removing flash means that I get the prompt to install the plugin, but Firefox continues to run.

---

### Post by strabes on 2006-12-07
install flash 9. [http://labs.adobe.com/technologies/flashplayer9/](http://labs.adobe.com/technologies/flashplayer9/)

put the .so in your /usr/lib/firefox/plugins directory to install it globally for all users.

---

### Post by evilc on 2006-12-07
> **bscbrit said:**
> evilc - No, my problem is that when flash _is_ installed, then Firefox bombs.  Removing flash means that I get the prompt to install the plugin, but Firefox continues to run.

With you now, there seems to be various problems with flash on diff computers, would suggest you go to firefox forum and check there. There are a lot of answers to your case. Sorry.

---

### Post by bscbrit on 2006-12-07
Problem solved, or at least the cause is identified.  I've just been experimenting.  When you get the prompt for a flash plugin and you select install, it installs the Adobe Flash Plugin but does NOT install the dependencies.  If you install Adobe Flash using synaptic it will install the missing deps and everything works the way it should.

I'm not quite sure why the install doesn't work - is it a problem with Adobe, Firefox or Ubuntu?

---

### Post by jaakw on 2006-12-08
Thanks! It worked well.

---

