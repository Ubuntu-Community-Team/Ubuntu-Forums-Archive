---
title: "Firefox 3 beta 5 save settings temporary"
date: 2008-06-11
forum: General Help
---

### Post by HishamN on 2008-06-11
[B]Hi,

I installed firefox 3 beta 5 and uninstalled then install firefox 3 rc2 and I still have same problem!

Firefox save settings, bookmarks and proxy until I close all firefox pages then when I reopen it again it's return back to default settings with no bookmarks, proxy settings?!

How to solve this issue?[/B]

---

### Post by prince_niceguy on 2008-06-11
rename the .mozilla directory in your home to something else and then try again. That should solve the issue.

---

### Post by rubrboots on 2008-06-11
That worked!! Thanks so much!!

---

### Post by HishamN on 2008-06-12
prince_niceguy as you said it solved now, but I noticed that all my previous pages gone!

So I check the .mozilla folder and I found prefs.js file is owned by root!

So I chown it to my username and it solved now with all my previuos pages

Thanks alot for reply.

Regards

---

### Post by xamlah on 2008-06-12
hey!
relle sorry but m really new to linux!
where exactly is the .mozilla folder? =S

---

### Post by prince_niceguy on 2008-06-12
> **xamlah said:**
> hey!
relle sorry but m really new to linux!
where exactly is the .mozilla folder? =S
It is in your home directory. like my login name is prince. So my home directory would be /home/prince.

In that when you show the hidden files you will find out a folder name .mozilla. Hope that helps.

---

### Post by HishamN on 2008-06-12
Press CTRL + H then it will display all hidden files/folders.

Regards

---

