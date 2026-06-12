---
title: "install script for linuxcnc"
date: 2013-01-31
forum: General Help
---

### Post by tjamscad on 2013-01-31
I have hacked together an install script for linuxcnc that works on Ubuntu 12.04 LTS. I am getting Do you want to continue [Y/n]? during the script running. What do I need to put in my script so that it just works and doesn&#8217;t ask questions

[http://pastebin.com/embed_js.php?i=8JbQWZ9L](http://pastebin.com/embed_js.php?i=8JbQWZ9L)

---

### Post by omeomi on 2013-01-31
First of all, you know you can just put all the packages in 1 apt-get install command right?

Second, use -y to avoid the [Y/n] part:
```
sudo apt-get install -y package_name
```

---

### Post by tjamscad on 2013-01-31
> **omeomi said:**
> First of all, you know you can just put all the packages in 1 apt-get install command right?]

Yes, but i found that on some machines there are files that it doesnt like and it would stop the whole install. 

Thanks for the tip "-y"

---

