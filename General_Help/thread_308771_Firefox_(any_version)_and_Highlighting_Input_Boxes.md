---
title: "Firefox (any version) and Highlighting Input Boxes on Click"
date: 2006-11-28
forum: General Help
---

### Post by terces on 2006-11-28
It seems that Firefox for linux (I don't have another distro handy to try it in) doesn't automatically highlight it's address bar and search bar input boxes when there is previous information there.

In Windows, I can perform a search using the built-in search box, and with that info there, if I click in it the entire box highlights and I can start typing my new search info.

In Ubuntu (with version 1.5 and 2.0 of Firefox), when I click in the box it puts the caret where I click and I have to ctrl-a to highlight the entire selection.  

I know about the ctrl-k to select and highlight the box but is there a way (in about:config?) to set it so it highlights with a mouse click? Should I direct this question to a Firefox forum instead?

---

### Post by terces on 2006-11-28
Well I found a workaround... sort of.

All I ever use the search-bar for is for a Google search so I created user.js and added:

```
// Change to normal Google search:
user_pref("keyword.URL", "http://www.google.com/search?btnG=Google+Search&q=")
```

Then I removed the search-bar so now the address bar is the search bar and does a normal Google search.  This works because whenever a blank tab is loaded the address bar is cleared of information unlike the search-bar.

---

### Post by ~LoKe on 2006-11-28
Ah, misunderstood you.

---

### Post by noynac on 2006-11-28
There is an about:config settings, and it's "browser.urlbar.clickSelectsAll." Change this from false to true, and Firefox should work as you want.

BTW, with Windows, the default for this preference is true. With Linux, it's false. Also, changing this preference affects both the address and search bars.

---

### Post by aysiu on 2006-11-28
Alternatively, you can press Control-L (highlights the entire address bar) or Control-K (highlights the entire search bar).

---

