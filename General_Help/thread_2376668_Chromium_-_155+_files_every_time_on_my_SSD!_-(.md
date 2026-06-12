---
title: "Chromium - 155+ files every time on my SSD! :-("
date: 2017-11-04
forum: General Help
---

### Post by makem2 on 2017-11-04
I have just reinstalled xubuntu 16.4 which was initially installed with a separate /home folder many moons ago and has been reinstalled several times since.

Many moons ago I was using Firefox as my web browser and succeeded in moving the cache to a ramdisk. Each time I reinstall, and prepare a new ramdisk Firefox uses the ramdisk without my intervention for it's cache (nice Firefox)

That suggests that many moons ago I set that up and the settings are in my /home folder. Can I find them? I can not!

Why do I want to find them? Well I prefer Chromium now but if I cannot get it to stop bashing my SSD then I will have to abandon it.

I have tried creating a symlink and also tried to find where to put a 'switch' in Chromiums start script but no go, It insists on avoiding all my attempts.

I ask if anyone can help me stay with Chromium please.

---

### Post by efflandt on 2017-11-05
I don't know if this will help you, but it is suggestions to minimize write actions of Chrome (along with other hints for SSD in Ubuntu/Mint/Debian):
[https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Limit-the-write-actions-of-Chrome](https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Limit-the-write-actions-of-Chrome)

---

### Post by makem2 on 2017-11-05
> **efflandt said:**
> I don't know if this will help you, but it is suggestions to minimize write actions of Chrome (along with other hints for SSD in Ubuntu/Mint/Debian):
[https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Limit-the-write-actions-of-Chrome](https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Limit-the-write-actions-of-Chrome)

Thank you, except for allocating unused space and TRIM I have implemented those suggestions.

I have stopped using Chrome until I find a solution.

It is as bad as WhatsApp on my phone, no way to move media files to SD card.

---

### Post by makem2 on 2017-11-07
The only way I can think of doing it would be:

1. Make a directory in a ramdisk which is created at boot
2. Add a switch to the chromium command line Exec pointing to that directory

I have no idea how to do that now. Previously you could do something like:

sudo gedit /etc/rc.local
Add the following lines:
mkdir /tmp/chromium
mount -t tmpfs -o size=1024M,mode=0744 tmpfs /tmp/chromium/
chmod 777 /tmp/chrome/ -R

But rc.local no longer is used.

---

### Post by Holger_Gehrke on 2017-11-07
According to [this document]("https://chromium.googlesource.com/chromium/src/+/master/docs/user_data_dir.md#User-Cache-Directory"), Chromium adheres to the XDG-Standard. So you could either set XDG_CACHE_HOME globally to put the caches of all programs obeying this standard -- not only chromium's -- on your RAM-disk or set this variable in a script that starts chromium. Other sources on the web mention an option '--disk-cache-dir <PathToCacheDirectory>' which is supposed to allow you to set the directory to use.

Holger

---

### Post by makem2 on 2017-11-07
> **Holger_Gehrke said:**
> According to [this document]("https://chromium.googlesource.com/chromium/src/+/master/docs/user_data_dir.md#User-Cache-Directory"), Chromium adheres to the XDG-Standard. So you could either set XDG_CACHE_HOME globally to put the caches of all programs obeying this standard -- not only chromium's -- on your RAM-disk or set this variable in a script that starts chromium. Other sources on the web mention an option '--disk-cache-dir <PathToCacheDirectory>' which is supposed to allow you to set the directory to use.

Holger


Exec=[/opt/google/chrome]/chromium –disk-cache-dir=”/tmp/chrome/”

Would be a way to add a switch but I have no idea where this path [/opt/google/chrome] now is.

---

### Post by vasa1 on 2017-11-07
/opt is for google-chrome. For chromium-browser, try```
which chromium-browser
```

---

### Post by makem2 on 2017-11-07
[http://manpages.ubuntu.com/manpages/zesty/man1/psd.1.html](http://manpages.ubuntu.com/manpages/zesty/man1/psd.1.html)

Worth investigation?

---

### Post by makem2 on 2017-11-07
> **vasa1 said:**
> /opt is for google-chrome. For chromium-browser, try```
which chromium-browser
```

Very good, thanks

---

### Post by vasa1 on 2017-11-07
> **makem2 said:**
> [http://manpages.ubuntu.com/manpages/zesty/man1/psd.1.html](http://manpages.ubuntu.com/manpages/zesty/man1/psd.1.html)

Worth investigation?

Very much so for those on 17.04+. It doesn't appear to be available for 16.04 :(

---

### Post by makem2 on 2017-11-07
> **vasa1 said:**
> Very much so for those on 17.04+. It doesn't appear to be available for 16.04 :(

Thats a pity.

I tried updating to 17.04 but had nothing but trouble with wireless. I had to give it up and will wait until it is more mature.

---

