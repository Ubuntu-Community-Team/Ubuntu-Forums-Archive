---
title: "Problem with Firefox: webpages not displayed correctly at all"
date: 2013-12-21
forum: General Help
---

### Post by cari.baur on 2013-12-21
Hi,

Opening firefox 26.0 in Ubuntu 12.04 today involved a surprise for me... I wanted to google something, but none of the results were displayed! I tried some other web pages and similar things happened! (Ubuntuforums.org is fine somehow...) I attached a screenshot of a random google search.
So far, I have uninstalled firefox completely and installed it again - however, with no effect. I have also deleted my configuration files and tried again - with no effect either... (I am using firefox 26.0 for more than a week now.)

Does anybody have an idea what could be wrong?

Thanks a lot!

-Cari

---

### Post by bapoumba on 2013-12-21
Maybe something is corrupt with your current profile. Please run ```
firefox -p
``` to make a new one and see if you still have the issue.

---

### Post by dragonfly41 on 2013-12-21
I have Firefox 26 running on Ubuntu 12.04.

You could try Firefox > top Menubar > Help > Troubleshooting information
and reset Firefox to its default state.

---

### Post by cari.baur on 2013-12-21
Thanks a lot for your suggestions. I tried both, but still face the same problem unfortunately...

---

### Post by dragonfly41 on 2013-12-21
And when you run Firefox in safe mode?

---

### Post by cari.baur on 2013-12-21
Thanks for your suggestion! However, no difference, I am afraid.

---

### Post by bapoumba on 2013-12-22
Any extension or plugin that would slow down page loading or prevent some part of the page to be downloaded ?
Try to clear cache and cookies and look for extensions or plugins you would not recognize.

Would another browser load the page correctly ? Any firewall ? Any error if you start it from the terminal ?

---

### Post by cari.baur on 2013-12-22
Thank you for your reply.

I tried it with all extensions and plugins disabled as well as clearing cache and cookies. In fact, I also completely uninstalled firefox and reinstalled it (see first post) - with no effect.

Yes, Chromium loads the page correctly for instance. There also is no firewall currently.
Thanks for the hint to start it from the terminal! Unfortunately, there is no error or warning (or anything else) reported in the terminal.

I suspect it is something from the ubuntu side of things. Is there something that might cause something like this?

Thanks a lot!

---

### Post by vasa1 on 2013-12-22
> **cari.baur said:**
> ...
I suspect it is something from the ubuntu side of things. Is there something that might cause something like this?
Then there'd a lot of similar complaints.

---

### Post by dragonfly41 on 2013-12-23
Some other ideas to try

What results when you use another search engine such as Bing, DuckDuckGo etc.
(Use the drop down list to select a different search engine)

You can try clearing out Firefox cache completely

you can try installing bleachbit as system tool to clear your browser caches.

You can try Firefox > Preferences > Advanced > General tab

browsing ...

untick "use hardware acceleration when available"

---

### Post by cari.baur on 2013-12-30
Thanks for your further suggestions.

> **dragonfly41 said:**
> Some other ideas to try
What results when you use another search engine such as Bing, DuckDuckGo etc.
(Use the drop down list to select a different search engine)
Basically the same result for Bing, DuckDuckGo is working. Same for youtube, etc. (not working). I am not sure, but I think everything that is not basic html or so does not work...
> **dragonfly41 said:**
> You can try clearing out Firefox cache completely
No effect.
> **dragonfly41 said:**
> you can try installing bleachbit as system tool to clear your browser caches.
Tried, but not effect.
> **dragonfly41 said:**
> You can try Firefox > Preferences > Advanced > General tab

browsing ...

untick "use hardware acceleration when available"
No effect.

---

### Post by alan-b-goldblatt on 2014-01-14
Was there ever a resolution of this?  I'm having the same problem -- many web pages are not rendering properly in Firefox 26.0.  Google Chrome works fine.  Safe mode and clearing data have no effect.  I'm experiencing the same problem on two different Ubuntu 13.10 machines, as we as on one Windows 7 machine.

Thanks everyone!

---

