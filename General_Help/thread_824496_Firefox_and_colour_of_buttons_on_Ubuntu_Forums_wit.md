---
title: "Firefox and colour of buttons on Ubuntu Forums with dark theme"
date: 2008-06-10
forum: General Help
---

### Post by ad_267 on 2008-06-10
Hi

I'm using the clearlooks gtk theme and have changed the colours to a darker theme. I haven't noticed this problem on any other websites yet but buttons on the ubuntu forums website appear to use the window text colour. This means they look white and I can't read them. I've attached a screenshot. Any idea how to fix this?

Cheers,
Adam

---

### Post by el-mar01 on 2008-06-18
*bump*

---

### Post by Alasdair on 2008-06-18
There is a file called userContent.css in ~/.mozilla/firefox/*your-profile*/chrome/ (IIRC) that allows you to override certain parts of webpages. You can use it to change the colors of widgets etc in order to stop them being unusable with dark themes.

I'm not on my main dark themed ubuntu machine right now, so the best I can do is to tell you to google 'userContent.css dark themes' or similar - you should get a few good results.

---

### Post by schnauzer93 on 2008-06-18
I've also been looking for a solution to this, and it seems that this fix no longer works; it used to in FF2... any ideas?

---

### Post by ad_267 on 2008-06-19
Yeah those userContent.css files were used for Firefox 2, now that firefox 3 is integrated with GTK better it isn't needed, so I think this is a different issue.

Has anyone seen this with any other websites? I've switched back to a light theme so didn't see this on any site except the Ubuntu forums.

---

### Post by el-mar01 on 2008-06-19
Here is a further screenshot of the problem:

Black on a dark background is quite unreadable .. and the problem with the buttons on the ubuntu forums is that if you change the text to white with the CSS below the text on the white background wont show up like in ad_267's post.

This fixes buttons that have a dark background but it does not fix buttons with a white background.

```
input[type="button"],
input[type="submit"],
input[type="reset"],
input[type="hidden"],
input[type="file"],
input[type="select"] {
    color: white !important
}

textarea  {
    border: 0px solid !important;
    color: white !important    
}

select  {
    color: white !important
}
```

[IMG]http://i31.tinypic.com/mm4lxw.png[/IMG]

---

### Post by el-mar01 on 2008-06-19
EDIT: Scratch that .. the problem still persists on some websites with some special type of text entry box. If anyone has found a fix for it that will be great.

---

### Post by nufros on 2008-11-12
try this Greasemonkey script... it worked for me :)

[http://userscripts.org/scripts/show/36850]("http://userscripts.org/scripts/show/36850")

---

