---
title: "Menu URL links in Wine"
date: 2006-11-24
forum: General Help
---

### Post by firenewt on 2006-11-24
Links in menus and within wine programs aren't working. All the terminal says is "usage: winebrowser URL". 

Typing out 'winebrowser [a url]' will work, it will open the link on the default browser.

Without this, some science programs are useless because there is no way to get the URL. How to get links to work within the wine programs?

---

### Post by g21k5 on 2007-02-21
The problem is in the file .wine/system.reg

replace all occurrences of 

```
@="winebrowser"
```

with

```
@="winebrowser %1"
```

and you are done.:) 

Greetings,
gü

---

### Post by pt123 on 2007-07-08
Thanks

Do you know why it is like this and do they plan on fixiing it?

Previous WINE versions I didn't have this problem

---

### Post by g21k5 on 2007-08-03
I have no idea why this happend. I'm not a developer of wine so maybe it would be a good idea to fill a bug-report on winehq.

greetings,
gü

---

