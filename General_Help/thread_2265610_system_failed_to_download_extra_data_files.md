---
title: "system failed to download extra data files"
date: 2015-02-16
forum: General Help
---

### Post by bgman on 2015-02-16
Someone closed the thread and told me not to post duplicate threads. I did not post duplicate threads. My first attempt wound up in the wrong forum. If you don't want to help, I understand. After all, who would want to waste time with someone that can't solve this simple problem. Please just ignore me if you wish. Thanks!!

My question:

I keep getting a message that my system failed to download extra data   files, specifically the ttf-mscorefonts-installer. I do not want to   complete the download, I'm very happy that the ms fonts are not   installed. The last thing I want is anything from microsoft installed on   my new computer.

I just want the message to stop appearing. Can this be accomplished?

Running Ubuntu 14.10, cinnmon 2.4.6 on a System 76 laptop.

Many thanks to any and all that can help!!

Bob

---

### Post by Elfy on 2015-02-16
First - it was a duplicate thread - the other open one is here [http://ubuntuforums.org/showthread.php?t=2265584](http://ubuntuforums.org/showthread.php?t=2265584). In the same place as this one;) I've closed that one too.

Now, it often happens with the mscorefonts, you've tried to install ubuntu-restricted-extras I am assuming. The agreement for those often ends up hidden and missed during installation

Uninstall that ttf package - and it should stop pestering you. 

Open a terminal and 

```
sudo apt-get purge ttf-mscorefonts-installer
```

or use your GUI tool.

---

### Post by bgman on 2015-02-17
Thank you so much!!

---

