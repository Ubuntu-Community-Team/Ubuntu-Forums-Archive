---
title: "VIM - Visual column replace"
date: 2007-11-23
forum: General Help
---

### Post by KlausPaiva on 2007-11-23
Hello,
I've been using vim to make some column modifications in my files.

For example:
Ctrl + V, selecting various lines and pressing c, inserting my text and after that my text was inserted in each line.

But, after the upgrade to Gutsy, when I insert my text after pressing c, only the first line is changed. Is there any configuration I am missing here?

Thanks!

---

### Post by taurus on 2007-11-23
Maybe you need to reinstall vim-full again.

```
sudo apt-get update
sudo apt-get install vim-full
```

---

### Post by KlausPaiva on 2007-11-23
> **taurus said:**
> Maybe you need to reinstall vim-full again.

```
sudo apt-get update
sudo apt-get install vim-full
```

Thanks man! Perfect!

---

