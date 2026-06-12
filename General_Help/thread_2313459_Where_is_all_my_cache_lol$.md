---
title: "Where is all my cache? lol$"
date: 2016-02-12
forum: General Help
---

### Post by tyler91 on 2016-02-12
So I wanna know where I can find all my application caches and screen caches (Mostly for a secure system) Anything that can be useful for people to find out anything I have been doing on this computer if they ever had access to it. I already know secure deletion methods but I would like to know where some storage caches for objects created and downloaded are, packets left over from careless security features and screen data as well. I really want my computer to look as if it had been using Tails without it actually using Tails. I also want to know if there are any programs that can keep my computer from caching data that would otherwise be useless to me. I would like to keep my preferences as they are right now without changes but would also like to modify them in the future for whatever reason. If these folders are root access only, I'm pretty new to the Ubuntu game but I'm learning quickly, if there is anything special I need to do to access these folders please tell me because as of yet I have not taken any data from root access folders yet and would not know how to go about doing this as of yet. Thnx~

---

### Post by deadflowr on 2016-02-12
Most cached data is in ~/.cache directory.
No need to invoke root to clear those.
~ means home as in /home/johndoe
the dot means the folder in hidden, so
in the files program press ctrl +h to enable view hidden to see the .cache folder.

Browser cookies and history, on the other hand are usually stored in the browsers profile folder.
Chromes' for example, are stored in ~/.confgi/google-chrome.
Firefox on the other hand, are stored in ~/.mozilla/firefox.
I'm sure other browsers store theirs in other places, similar to one or the other.

---

### Post by QDR06VV9 on 2016-02-12
deadflowr's advice is good..untill you become a little more familiar with Ubuntu
> are any programs that can keep my computer from caching data..
You can't, or more like, you don't need to.
Disk caching makes the system much faster! There are no downsides, except for confusing newbies. 

Most applications doesn't use a cache without a very good reason. Browsers for example, has a cache. But this cache is of internet's objects (images, JavaScript, CSS, static content, etc) and the web page loads times are faster in subsequent visits. Other applications use cache's for storing thumbnails, frequently accessed data, etc. Those applications use in-disk caching. That cache isn't loaded in memory until the application starts, and it isn't counted as cached memory.

And for good information that should provide you with a better understanding: [https://en.wikipedia.org/wiki/Cache_%28computing%29](https://en.wikipedia.org/wiki/Cache_%28computing%29)
And another cleanup thread..
[http://www.ubuntugeek.com/how-do-i-cleanup-ubuntu.html](http://www.ubuntugeek.com/how-do-i-cleanup-ubuntu.html)

There are a few tools like [bleachbit ]("http://www.bleachbit.org/")from the repo's  that do a fair job of that.
Hope This helps Cheers and happy reading.

---

### Post by tyler91 on 2016-02-12
This. This is why Linux/Ubuntu is better. Better than Windows. #sudo foreverr~

---

### Post by tyler91 on 2016-02-12
Just as a precaution though. Is there anything that will clean up my RAM?

---

### Post by buzzingrobot on 2016-02-12
> **tyler91 said:**
>  Is there anything that will clean up my RAM?


Well... powering down will handle that quite nicely.

---

### Post by tyler91 on 2016-02-12
I really thought you had to do something but I guess not. All you have to do is power down then. Just incase though I installed sdmem. I went to this website [http://askubuntu.com/questions/153245/how-to-wipe-ram-on-shutdown-prevent-cold-boot-attacks](http://askubuntu.com/questions/153245/how-to-wipe-ram-on-shutdown-prevent-cold-boot-attacks) and created the script and I put it into my init folder but I'm not sure if it works or not. But anyways thanks for the helpp~

---

