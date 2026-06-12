---
title: "Thunderbird in background"
date: 2008-06-03
forum: General Help
---

### Post by SpenceMakesSense on 2008-06-03
Does anyone know how to get thunderbird to run in background. So I can get constant updates of EMAILs. If I have to use a different client I have no problem doing so.

---

### Post by sdennie on 2008-06-03
I'm not completely sure what you mean but, it sounds like you want a mail notification utility.  Maybe try:

```

sudo apt-get install mail-notification

```

I think that then installs in Applications->Internet.

---

### Post by jocko on 2008-06-03
I've done it by installing alltray:```

sudo apt-get install alltray
```It allows you to start any program in the background and keep it as an icon in the notification area.
Add it to your session (System --> Settings --> Sessions --> Add):
```
Name: Thunderbird
Command: alltray thunderbird -na
Comment: Whatever you like
```(I use thunderbird, but I'm sure it will work with any email client)

---

### Post by SpenceMakesSense on 2008-06-03
Alltray kind of worked but when I log in it shows thunderbird and when I try to Exit out it sits there. And I cant start any other programs. BUt I did notice the thunderbird icon in the panel.

---

