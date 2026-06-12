---
title: "Is it normal for a program to occupy occupy 243.6MB in memory?"
date: 2007-10-13
forum: General Help
---

### Post by Thyme on 2007-10-13
Is it normal for a program to occupy occupy 243.6MB in memory? Firefox is occupying that much currently and second is Nautilus at 21MB .. Recently firefox has also been hanging alot while carrying out normal tasks ..

Thanks :)

---

### Post by prince_niceguy on 2007-10-13
ya it is normal for firefox... if you want to cut down on memory then remove some of the extensions that you do not need and also change the number of pages to keep in memory for going back and forth ... use the extension fasterfox or use about:config in the address bar of firefox...

as i speak firefox is taking

virtual - 155m  
resident - 57m  
shared - 21m S    2  5.8   0:14.28 firefox-bin

---

### Post by Thyme on 2007-10-13
Thanks, that makes sense... It's just that all the hanging is really getting to me. Nevertheless, I suppose persistence pays off ..

---

### Post by cmargolin on 2007-10-15
Firefox unfortunately leaks memory as you use it, so you should restart it after a while.

---

### Post by Crooksey on 2007-10-15
^ Firefox has alot of memory leaks, use epiphany, in my opinion a very fast and functional gtk client.

---

### Post by aliencam on 2007-10-15
it helps a *little bit* if you go to "about:config" in the address bar, then right-click and make a new string that is boolean.  then for the name of the strong type "config.trim_on_minimize" without the quotes, and click ok, then choose "true".  this appears to work a little bit for me on ubuntu, but it has a HUGE effect while using windows.  

You could also switch to "swiftfox" which is an optimized version of firefox for each processor type for linux.  The major problem with it is that it is not open source, which kind of defeats the attitude of firefox, but other than that everything works the same (your extensions stay and such) .  

right now I use swiftfox, it is noticibly faster.  if you want to check it out the link is [http://getswiftfox.com](http://getswiftfox.com)

---

### Post by Cable on 2007-10-15
Or you could try [Swiftweasel]("http://swiftweasel.sourceforge.net/").  It's basically based on the same idea as Swiftfox except it's open source.

---

