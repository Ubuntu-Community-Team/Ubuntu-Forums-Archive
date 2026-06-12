---
title: "firefox goofiness"
date: 2023-11-14
forum: General Help
---

### Post by zxcvb on 2023-11-14
I just installed Ubuntu 23.04 with Gnome. Though I have long used Ubuntu server, (no GUI) as my principle server, I have not used Ubuntu desktop as my daily driver for over a decade – and even then I used Kubuntu. (I have always preferred , and still use kde on my other OpenSuse & Fedora machines.)

However, I quite like the handsome and useful new Gnome desktop on 23.04.  One thing which keeps me from adopting it as my daily driver is the Firefox setup.

I like to be able to manually work on Firefox to salvage or repair a fugged-up Firefox. It’s quick and easy to repair. (I tend to keep about 24 tabs open, so once in a while, Firefox stumbles...)

In the other newest major distributions I can still access my profile from the  ~/.mozilla folder.

I can not locate anything approximating a standard profile folder on Ubuntu’s Gnome/Wayland structure .. a deeply buried and fractured business it is --under about 12 sub-directories!

I choose to have as little to do with Google as possible – so logging into any Google accounts and syncing  etc. is not my choice for repair. 
Is there an alternative solution to this?

Thanks for any insights...

---

### Post by deadflowr on 2023-11-14
Firefox profile is in the snap > firefox > common> .mozilla > firefox  directory.

---

### Post by zxcvb on 2023-11-14
deadflower, thank you!

1st time with snap..I&#8217;ve always stayed with distro pkg managers.

You know, from my home ~/ I looked under .config, .local, and snap &#8211;though I only went down, I think, 3 levels, and then jumped over to /usr and found that long string before abandoning it&#8230;

I also didn&#8217;t use* find*&#8230;duh!

Whew...drivin&#8217; too fast!

---

