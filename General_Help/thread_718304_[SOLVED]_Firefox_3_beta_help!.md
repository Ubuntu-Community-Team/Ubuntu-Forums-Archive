---
title: "[SOLVED] Firefox 3 beta help!"
date: 2008-03-08
forum: General Help
---

### Post by solarwind on 2008-03-08
Hey all,

I just installed Firefox 3 beta from the repositories. So far I love it. Only one problem: no plugins. How do I install the Flash and Java plugins for my new browser?

---

### Post by Shazaam on 2008-03-08
Applications>Add/Remove, in the upper right make sure "All available applications" is set then go to "Other" Then "Ubuntu Restricted Extras" and install it.

---

### Post by solarwind on 2008-03-08
> **Shazaam said:**
> Applications>Add/Remove, in the upper right make sure "All available applications" is set then go to "Other" Then "Ubuntu Restricted Extras" and install it.

It's already installed...

---

### Post by boeing777 on 2008-03-08
go to a web site that has flash, it should prompt you to install flash?

---

### Post by solarwind on 2008-03-08
> **boeing777 said:**
> go to a web site that has flash, it should prompt you to install flash?

Tried it, didn't work, wanted me to install manually, didn't work as well.

---

### Post by boeing777 on 2008-03-08
[http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/)

---

### Post by solarwind on 2008-03-08
> **boeing777 said:**
> [http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/)

Installation failed... as I already stated...

---

### Post by boeing777 on 2008-03-08
this should help

[http://daniel1992.wordpress.com/2008/02/23/getting-flash-working-in-firefox-3/](http://daniel1992.wordpress.com/2008/02/23/getting-flash-working-in-firefox-3/)

---

### Post by solarwind on 2008-03-08
> **boeing777 said:**
> this should help

[http://daniel1992.wordpress.com/2008/02/23/getting-flash-working-in-firefox-3/](http://daniel1992.wordpress.com/2008/02/23/getting-flash-working-in-firefox-3/)

Thanks! Flash is now working, just need to get Java working...

---

### Post by boeing777 on 2008-03-08
i would recommed remove firefox 2 before installing firefox 3.  this way you wouldn't have these conflicts

---

### Post by someonestolemyname on 2008-03-09
As for uninstalling FF2 before installing FF3, I found no problems. I prefer to keep 2 around for the occasional site that has problems with the beta, or for extensions that don't work when installed in FF3.

I'm the writer of the blog post linked above. Also, for help installing incompatible extensions in FF3, try this post:

[http://daniel1992.wordpress.com/2008/02/03/how-to-install-incompatible-addons-in-firefox-3/]("http://daniel1992.wordpress.com/2008/02/03/how-to-install-incompatible-addons-in-firefox-3/")

Glad you found use in my post!

Daniel

---

### Post by solarwind on 2008-03-09
> **someonestolemyname said:**
> As for uninstalling FF2 before installing FF3, I found no problems. I prefer to keep 2 around for the occasional site that has problems with the beta, or for extensions that don't work when installed in FF3.

I'm the writer of the blog post linked above. Also, for help installing incompatible extensions in FF3, try this post:

[http://daniel1992.wordpress.com/2008/02/03/how-to-install-incompatible-addons-in-firefox-3/]("http://daniel1992.wordpress.com/2008/02/03/how-to-install-incompatible-addons-in-firefox-3/")

Glad you found use in my post!

Daniel

Haha, yeah, thanks! You might want to note this on your blog though:

Seems that when you issue the sudo cp command, symbolic links aren't being copied properly (the symbolic links to the Sun Java plugin). I had to go into the folders and link them using ln -s -f manually.

Edit: Oooh, nice digg theme.

---

### Post by someonestolemyname on 2008-03-10
Odd. I didn't install Java before, and now I see what you're saying.

However, ln -s -f libjavaplugin.so /usr/lib/firefox3/plugins/ didn't work. Any ideas?

Daniel

---

### Post by solarwind on 2008-03-10
> **someonestolemyname said:**
> Odd. I didn't install Java before, and now I see what you're saying.

However, ln -s -f libjavaplugin.so /usr/lib/firefox3/plugins/ didn't work. Any ideas?

Daniel

```
cd /usr/lib/firefox3/plugins 
```
```
ln -s -f <wherever your libjavaplugin.so is> ./
```

You **have** to do it that way.

---

### Post by someonestolemyname on 2008-03-10
Nice. Thanks for that, I'll put it in the post. I was doing it from the FF2 plugins dir =/

Daniel

---

### Post by someonestolemyname on 2008-03-10
See the attribution and tip: [http://ubuntuforums.org/showthread.php?p=4491205]("http://ubuntuforums.org/showthread.php?p=4491205")

---

### Post by solarwind on 2008-03-10
> **someonestolemyname said:**
> See the attribution and tip: [http://ubuntuforums.org/showthread.php?p=4491205]("http://ubuntuforums.org/showthread.php?p=4491205")

Nice blog. Like the theme. Where did you get the hit counter from?

---

### Post by someonestolemyname on 2008-03-10
It's just a standard Wordpress-hosted blog right now. The theme is one of the options. I made the header myself.They give a huge page called Blog Stats that gives all kinds of stats. Links to the site, referrers, outgoing links clicked, views per article, what searches were used to find my blog, etc... And of course the all-time hit count!

1000+ in the last month, 1374 since i started it.

When I get the chance I'm going to set it up somewhere else so I can cutomize more and add other things. School taking too much time right now though.

I post mostly about Ubuntu, Firefox, and the internet. The occasionally life post happens.

Daniel

---

### Post by solarwind on 2008-03-10
> **someonestolemyname said:**
> It's just a standard Wordpress-hosted blog right now. The theme is one of the options. I made the header myself.They give a huge page called Blog Stats that gives all kinds of stats. Links to the site, referrers, outgoing links clicked, views per article, what searches were used to find my blog, etc... And of course the all-time hit count!

1000+ in the last month, 1374 since i started it.

When I get the chance I'm going to set it up somewhere else so I can cutomize more and add other things. School taking too much time right now though.

I post mostly about Ubuntu, Firefox, and the internet. The occasionally life post happens.

Daniel

Ahh, I host my blog on my own host: blog.solarwind.metafy.org

How old are you by the way?

---

### Post by someonestolemyname on 2008-03-10
15. You?

---

### Post by solarwind on 2008-03-10
> **someonestolemyname said:**
> 15. You?

17.

---

