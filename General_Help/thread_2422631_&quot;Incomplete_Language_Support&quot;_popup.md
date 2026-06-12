---
title: "&quot;Incomplete Language Support&quot; popup"
date: 2019-07-10
forum: General Help
---

### Post by Skaperen on 2019-07-10
i continue to get a "Incomplete Language Support" popup every time i boot up despite having gone through the installation steps ("Run this action now") it has a button for and tried to (re-)select my language (it doesn't let me select any).  perhaps all language support is missing.  i installed _Xubuntu_ from the 1474953216 byte 18.04.2 ISO (SHA256 below) on a 8GB USB memory stick.  i'd like to fix whatever is wrong and not have this popup anymore.  i did a dist-upgrade a couple hours ago.

there are 5 old threads here that match this topic, all closed, but none really get to a solution.  do i need to install more packages?  what actually triggers this popup?

the SHA256 of that ISO is _cd48e3eb8bd0dce035556553d0c96edb3d8fc91ed735ce43fb85d99b273b97da_.

---

### Post by #&amp;thj^% on 2019-07-12
The missing packages can be seen if installing the full language support in Terminal:
```

sudo apt install $(check-language-support)
```
"check-language-support - returns the list of missing packages in order to provide a complete language environment"

---

### Post by Skaperen on 2019-07-14
check-language-support outputs 1 blank line.  that seems to tell me i have full language support already installed.

---

