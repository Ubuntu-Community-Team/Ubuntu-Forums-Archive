---
title: "How to delete an older version of Emacs?"
date: 2012-12-31
forum: General Help
---

### Post by AmadeusOK on 2012-12-31
I installed Emacs 24.1 from source and compiled in the directory /usr/local/src. But after that I got Emacs 24.2 from ppa:cassou. Now I have two versions of Emacs and I want to get rid of the older ones.

If have emacs and emacs-24.1 (both are the 24.1 version) in /usr/local/bin. And I also have emacs24-x (24.1 version) and emacs24 (24.2 version) in /usr/bin.

I want to keep only the 24.2 version and I want to delete the others. But I don't want to mess things up. Also I click the emacs icon in the laucher it opens emacs 24.1. How do I change it to emacs 24.2?

I know that there are many things I still need to learn about Linux in general. This is a very basic question. I hope anyone can give a hint. Thanks for your answer.

---

### Post by daslinkard on 2013-01-01
> **AmadeusOK said:**
> I installed Emacs 24.1 from source and compiled in the directory /usr/local/src. But after that I got Emacs 24.2 from ppa:cassou. Now I have two versions of Emacs and I want to get rid of the older ones.

If have emacs and emacs-24.1 (both are the 24.1 version) in /usr/local/bin. And I also have emacs24-x (24.1 version) and emacs24 (24.2 version) in /usr/bin.

I want to keep only the 24.2 version and I want to delete the others. But I don't want to mess things up. Also I click the emacs icon in the laucher it opens emacs 24.1. How do I change it to emacs 24.2?

I know that there are many things I still need to learn about Linux in general. This is a very basic question. I hope anyone can give a hint. Thanks for your answer.

What about completely purging emacs and then reinstalling the version you want?
```

sudo apt-get purge emacs
```

P.S.- I notice you're from Missouri, I grew up in SE MO....what area are you located?

---

