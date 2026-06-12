---
title: "Clean Browser Chrome"
date: 2020-11-15
forum: General Help
---

### Post by travisb9218 on 2020-11-15
Dear Form,

This is simple an short when open a browser I don't want password's saved History Saved or Pins Saved on Home Page of Chrome...
Basic Every Time I Open My Browser I Would Like to See This... Basically When I First Installed Chrome... IF POSSIBLE I do not think it is  ( But I Don't Know if it's People )

[https://www.androidpolice.com/wp-content/uploads/2019/02/New-Chrome-sign-in-screen-hero.jpg](https://www.androidpolice.com/wp-content/uploads/2019/02/New-Chrome-sign-in-screen-hero.jpg)

---

### Post by TheFu on 2020-11-15
$ firejail --private {program tobe run}

This will make the underlying flle system that the program sees be empty with each invocation. Nothing can be saved from the program. Everything about the process is new, including the directories.

I don't/won't use chrome, but with chromium on 16.04, it works fantastic.  

Other constraint systems like snap packages break this ability.

---

### Post by coffeecat on 2020-11-15
@travisb9218, I've reduced the giant image in your post to a hyperlink. Please be considerate of those with limited bandwidth and those browsing the forum with small screen mobile devices, and avoid posting such unnecessarily large images. If you really need to post an image within a post, simply go to the advanced editor and use the paper-clip icon in the editor toolbar to upload your image to the forum server. That way you get a clickable thumbnail. No need to use off-site image hosting.

---

### Post by jeremy31 on 2020-11-15
Start chrome with ```
google-chrome --password-store=basic
```
See if that does what you want

---

