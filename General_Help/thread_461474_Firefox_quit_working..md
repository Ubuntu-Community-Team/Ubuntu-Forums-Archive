---
title: "Firefox quit working."
date: 2007-06-01
forum: General Help
---

### Post by lonegeek on 2007-06-01
I was just using firefox, closed it out, and now it no longer opens. It says loading firefox and then nothing happens.

I've completely removed it and reinstalled it with both terminal and synaptic.

What do I need to do?

---

### Post by kellemes on 2007-06-02
Startup FireFox from terminal and watch the output.

---

### Post by lonegeek on 2007-06-02
> zach@zach-desktop:~$ firefox
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
                 AllPeers initiated successfully
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
Segmentation fault (core dumped)


How can I remove AllPeers?

---

### Post by kellemes on 2007-06-03
This is from another thread..

```
Type
arun@arun-desktop:~$ firefox -safe-mode

You will have a dialog giving a few options.

Do not load your plugins. And once your firefox is up, uninstall or disable All Peers.
All Peers knows that there is a bug in there and they are already working on it.

```

---

