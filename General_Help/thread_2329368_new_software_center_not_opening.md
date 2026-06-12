---
title: "new software center not opening"
date: 2016-06-30
forum: General Help
---

### Post by rickyjoepr on 2016-06-30
Hello,

  My software center stopped loading. I did not change anything. What are the steps to troubleshoot this issue?

 I know that I can install the old software center, but I would like to use the new version

Thanks

---

### Post by RobGoss on 2016-06-30
What version of Ubuntu are you using and what are the specs for your machine?  

And what do you mean the Software center stop loading are you getting any error message?

---

### Post by Frogs Hair on 2016-06-30
Hello and Welcome

Try opening from the terminal and if there are errors post them here . Copy and paste the following command in the terminal. If it opens try using the icon again.

```
ubuntu-software 
```

---

### Post by Autodave on 2016-07-01
Mine does the same thing on all 11 machines: it opens when it feels like it. And then, when it does open, sometimes it loads and sometimes it just sits there and does nothing. I finally, when I got it to open, installed synaptic and I use that instead.

---

### Post by rickyjoepr on 2016-07-02
I am running on 16.04, the latest version. The new software center used to open fine. If i click the icon , i get the small spinning loading icon, but nothing ever happens. If i try to run from terminal, I get this error 

"(ubuntu-software:3592): Gs-WARNING **: failed to open plugin /usr/lib/gs-plugins-9/libgs_plugin_xdg_app_reviews.so: /usr/lib/gs-plugins-9/libgs_plugin_xdg_app_reviews.so: cannot open shared object file: No such file or directory"

---

### Post by howefield on 2016-07-02
> **rickyjoepr said:**
> (ubuntu-software:3592): Gs-WARNING **: failed to open plugin /usr/lib/gs-plugins-9/libgs_plugin_xdg_app_reviews.so: /usr/lib/gs-plugins-9/libgs_plugin_xdg_app_reviews.so: cannot open shared object file: No such file or directory

Looks like this bug.. [https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573052](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573052)

---

### Post by rickyjoepr on 2016-07-05
supposed to have been fixed in release today. Updated, didnt work, purged gnome-software an reinstalled, still nothing. Oh well

---

### Post by Frogs Hair on 2016-07-05
As an alternative you can install synaptic. 

```
sudo apt-get install synaptic
```

---

### Post by misfitpierce on 2016-07-05
I was also going to say just install synaptic. Its not as pretty per say, but its def more functional in my opinion.

---

### Post by brrmoot on 2016-07-05
Mine was doing the same thing. I updated and now it's working. (xubuntu 16.04) if that matters.

---

