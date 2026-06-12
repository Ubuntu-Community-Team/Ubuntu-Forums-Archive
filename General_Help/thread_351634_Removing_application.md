---
title: "Removing application?"
date: 2007-02-02
forum: General Help
---

### Post by Gibbs on 2007-02-02
Hello,

I'm very new to Ubuntu (infact Linux) which is why it's vital I can get on the internet. I ditched Redhat because I found it so difficult a few years ago.

Anyway I'm making progress (I think). My modem is a SpeedTouch 330 and theres lots of information regarding it on the internet.

I am trying to install it with this method [http://steve-parker.org/speedtouchconf/](http://steve-parker.org/speedtouchconf/).

I've figured out how to log in as root and run the script but I'm running into problems. I get an error "Failed modem run error 235". I have searched the internet and found the reason. Apparently it's due to a previous installation attempt (i did many when playing around).

Now the workaround, apparently, is to completely remove the installation attempt. There is an "undo" script I executed and rebooted but I still got the same error when trying to install.

The following command does nothing for me...
```
cd /root
find . -name "speedtouch*" -print
```

So I did a search with the Ubuntu search feature and deleted everything, including a module or something, and retried. It still didn't work...

There is a section in the script that says something similar to "USB modem lights will now flash". However my modem lights are already on, even prior to the installation.

I apologise if this doesn't make much sense but I really need help. With the release of Vista I want to get as far away from Windows as possible!

Thanks for any help :)

---

