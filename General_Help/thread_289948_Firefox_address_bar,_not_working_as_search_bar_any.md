---
title: "Firefox address bar, not working as search bar anymore. FF2"
date: 2006-10-31
forum: General Help
---

### Post by Kirky_D on 2006-10-31
Under firefox 1.5 i could type in the address bar something like "ebay uk" and it would take me to the uk ebay site. Now i get this error: 
[[IMG]http://img506.imageshack.us/img506/3131/snapshot1ba8.th.png[/IMG]](http://img506.imageshack.us/my.php?image=snapshot1ba8.png)

Also, say if i wanted imageshack.us (the first site on a google search of "imageshack") it would give me a site called imageshack.com which isn't what i want. 

All i want to do is type in the address bar and have it act as if it had searched google then used the first page like the i'm feeling lucky feature.

Any help out there?

Cheers all!

---

### Post by pataphysician on 2006-10-31
i'm not sure how to change the behavior of what you type in the addressbar, but a kind of workaround would be to use a quicksearch

[http://www.google.com/search?q=%s&btnI=I%27m+Feeling+Lucky](http://www.google.com/search?q=%s&btnI=I%27m+Feeling+Lucky)

if you bookmark that and give it a keyword, like "lucky," you can do

lucky imageshack

and it'll take you where you'd expect to go.

---

### Post by Kirky_D on 2006-10-31
Thanks for that!

That will have to do i suppose. I have no idea why they would take away that functionality. Unless it wasn't a function but some random thing that happened which they have now fixed. lol

---

### Post by Meph0 on 2006-11-07
I was having the same problem and found this thread using Google. After disabling all my extensions and re-enabling them 1 by 1, I found that Tabbrowser Extensions 1.3.1.1 is to blame for this behaviour. On his homepage, the author of this extensions says to be aware of minor bugs with the URL bar, so I guess he calls this minor.

Hopefully the bugs will be resolved in the next version. :)

If you don't have Tabbrowser Preferences installed, disable all your extensions and re-enable them 1 by 1 to find your pain-in-the-*** extension. :)

---

### Post by Kirky_D on 2006-11-09
Cheers for the info! I will give it a try!

---

### Post by cdmarcus on 2006-11-18
[SIZE=3]This is fairly easy to fix. Type about:config into the Location Bar (where you normally type URLs). There is a list of variables there that you can change. In the box right above the list, type "keyword.URL". Double click keyword.URL in the list, and put this into it:

**http://www.google.com/search?btnI=I%27m+Feeling+Lucky&q=**[/SIZE]

---

### Post by kerry_s on 2006-11-18
On mine it was because of tab browser preference, the features are built in to 2.0, so i just unintalled it and it's all good.

---

