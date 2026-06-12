---
title: "Clear a favicon in Chromium?"
date: 2015-08-08
forum: General Help
---

### Post by donsy on 2015-08-08
Is there a way to clear a favicon for a particular URL in Chromium? I removed the link tag from the HTML and cleared the cached images and files in Chromium but the favicon still appears.

---

### Post by howefield on 2015-08-08
Are you trying to refresh an old favicon or simply delete one?

They are stored in an sqlite database as far as I know so clearing cache images won't help. Sounds drastic to suggest creating a new profile but might end up less onerous than trying to remove one favicon :)

---

### Post by vasa1 on 2015-08-08
> **donsy said:**
> Is there a way to clear a favicon for a particular URL in Chromium? I removed the link tag from the HTML and cleared the cached images and files in Chromium but the favicon still appears.
Isn't the favicon part of the web page? Won't it download and display each time you visit the site?

Firefox has an all-or-none setting:
```
browser.chrome.favicons;false
browser.chrome.site_icons;false  
```

---

### Post by donsy on 2015-08-08
> **howefield said:**
> Are you trying to refresh an old favicon or simply delete one?

They are stored in an sqlite database as far as I know so clearing cache images won't help. Sounds drastic to suggest creating a new profile but might end up less onerous than trying to remove one favicon :)

I would like to simply delete the old one. Where is the sqlite database stored? I looked in ... /.cache/chromium/Default/ and subdirectories and couldn't find it.

> **vasa1 said:**
> Isn't the favicon part of the web page? Won't it download and display each time you visit the site?

Firefox has an all-or-none setting:
```
browser.chrome.favicons;false
browser.chrome.site_icons;false  
```

I deleted both the favicon.ico image and the <link ... > tag in the HTML.

I want to use Chrome/Chromium, Firefox  is not an issue.

---

### Post by vasa1 on 2015-08-08
> **donsy said:**
> ...
I deleted both the favicon.ico image and the <link ... > tag in the HTML.
...
But if you're accessing the original page won't the favicon simply be downloaded and displayed all over again? Or is this page now stored on your computer and that's what you mean when you say you've deleted the <link ...> tag in the HTML?

---

### Post by howefield on 2015-08-08
> **donsy said:**
> I would like to simply delete the old one. Where is the sqlite database stored? I looked in ... /.cache/chromium/Default/ and subdirectories and couldn't find it.

~/.local/chromium/Default/favicon

---

### Post by donsy on 2015-08-08
> **howefield said:**
> ~/.local/chromium/Default/favicon

On my system the sqlite database was in  ~/.config/chromium/Default/Favicons

I deleted it from three tables:
[LIST]
[*]favicons
[*]icon_mapping
[*]favicon_bitmaps
[/LIST]

---

### Post by howefield on 2015-08-08
Apologies, that was my mistake, it is the same path on mine on a default install - anyway glad you got it sussed.

---

