---
title: "What is the difference between xorg.conf and XF86Config-4?"
date: 2005-10-25
forum: General Help
---

### Post by Dave M G on 2005-10-25
(Note that I'm a newbie, and so please keep any advice simple to understand)

While trying to configure my Wacom tablet, I keep coming across mention of a file called XF86Config-4, or sometimes just XF86Config.

As far as I can tell by looking up information about it on the web, it does the same thing as xorg.conf.

What is the difference between xorg.conf and XF86Config-4?

Which should I be editing in order to add configurations for my Wacom tablet device?

Up until now, I've been editing my xorg.conf file, but since it's had no noticable effect, I'm wondering if it's possible that it's actually this XF86Config-4 file that is responsible for my X settings.

And, where is my XF86Config-4? I've tried running "locate" and couldn't find it.

Thank you for any assistance you may be able to provide.

---

### Post by Dr. Nick on 2005-10-25
Cant help specifically with your problems but can explain the Xf86 and xorg bit.

xorg.conf is probably what you need to be editing , before xorg was Xfree86. XF86 used to be used as the gui, but after awhile and for a few reasons it was changed to xorg.

I bet the instructions you are reading are a few years old which would explain the naming change

---

### Post by Dave M G on 2005-10-25
Thank you for that explanation.

I take that to mean that I should disregard all mention of XF86Config, and focus entirely on editing my xorg.conf file.

---

### Post by kairu0 on 2005-10-25
You should be editing xorg.conf.

And if you think that X isn't noticing your configuration changes, open up /var/log/xorg.conf (from memory - may be a little different) with a text editor and then look towards the end for information about your tablet driver loading.

---

### Post by Dr. Nick on 2005-10-26
[QUOTE=Dave M G]Thank you for that explanation.

I take that to mean that I should disregard all mention of XF86Config, and focus entirely on editing my xorg.conf file.[/QUOTE]


Yeah if it mentions XF86Config just read as xorg.conf, but realize that it may or may not work since some of th estuff may have not been implemented. I am not sure of all the differences I just know xf86 used to be used, but has been abandon in favor of xorg

---

