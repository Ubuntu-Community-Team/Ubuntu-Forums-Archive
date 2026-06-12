---
title: "Install SUSE's version of GAIM on my ubuntu"
date: 2007-05-21
forum: General Help
---

### Post by martinrandau on 2007-05-21
I installed SUSE 10.2 just for fun on one of my partition (very bad overall compared to ubuntu I have to say) and noticed a lot of nice features in GAIM that are not present in ubuntu's gaim. For example, notification when chat partner closes the chat window, latest messages above current chat and number of missed messages in panel.

So I am thinking, is it possible to install suse's rpm gaim on ubuntu. I assume it's available on some packman repository site or elsewhere.

What complications will this involve? What program do I use to convert rpm to deb?

Any help appreciated!

---

### Post by Happy_Man on 2007-05-21
hold up... all those options are available in our GAIM.... go into GAIM Preferences (tools --> preferences), under the sounds tab, there is a whole slew on sound option under sound events. Now, if you're still wanting SuSE's gaim, find the .rpm, save it to your Desktop, and then open a terminal, (Applications --> Accessories --> Terminal) and type this:

```
sudo apt-get install alien
cd Desktop
alien <filename of .rpm here>

```

and then install the resulting .deb. Done!

---

### Post by martinrandau on 2007-05-21
Thanks for your reply!

I'm pretty sure the features I'm looking for are not available in the ubuntu edition. By notification I mean text-notification, not sound. And the other features I mentioned can't be found either.

I did what you suggested and have the deb file on my desktop. 

However, I notice that it will install in /opt/gnome/bin/gaim while the ubuntu one is in /usr/bin/gaim. This will cause problems for sure, won't it?

---

### Post by Happy_Man on 2007-05-22
Nope, so long as you remove the Ubuntu version first.

---

### Post by martinrandau on 2007-05-22
Well removing the ubuntu version will also remove ubuntu-desktop among other things. I do not want that...

Anyway, I just installed the latest pidgin and now have the features mentioned.

Thanks for your help!

---

### Post by paul2112 on 2007-05-23
Gandhi is the man you quote.

---

