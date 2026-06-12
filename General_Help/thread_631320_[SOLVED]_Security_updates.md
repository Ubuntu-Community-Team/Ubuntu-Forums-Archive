---
title: "[SOLVED] Security updates"
date: 2007-12-04
forum: General Help
---

### Post by Mindflux0 on 2007-12-04
I just installed ubuntu and it wasn't connected to the internet, gave me a rather uninformative message saying that it couldn't download security updates and that I should do something about that.
How exactly do I update it?

Also it seems to be working fine albeit a little slow.  Do I have to install all my hardware? it doesn't appear to recognize anything.

---

### Post by cipher_nemo on 2007-12-04
Any way you can connect it to the Internet? The updater needs an Internet connection, either directly over through proxy. There are ways to transfer over the updated packages you need via a flash drive or other removable media, but that's a long, tedious, and painful process.

If you're having trouble configuring your network settings, what sort of network card/chip do you have, and how are you connecting to the Internet?

---

### Post by Mindflux0 on 2007-12-04
I have internet I just have no idea what I'm doing, I couldn't find any sort of automatic updater. (the original message was during installation)

---

### Post by forestpixie on 2007-12-04
I assume that you've now finished the install - I expect that all your repos are commented out in the sources list - you can check byt opening a terminal - in apps >accessories and putting this command in

```
cat /etc/apt/sources.list
```

if ALL the lines start with a # you need to edit them - this thread should help you to deal with it

[http://ubuntuforums.org/showthread.php?t=629621](http://ubuntuforums.org/showthread.php?t=629621)

If you're lost - post your sources list here, copy it from the terminal into a post - please use the post reply and you can highlight the text and click the # button - put's it in code

---

### Post by Mindflux0 on 2007-12-04
ok, I followed the intructions on that link, it seems to have worked, thanks.

---

### Post by forestpixie on 2007-12-04
glad I could help

---

