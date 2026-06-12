---
title: "How can I make a collection in font-manager?"
date: 2019-04-03
forum: General Help
---

### Post by jrrpnani on 2019-04-03
Hello:

I'm trying to use font-manager, but I don't know how to make a collection. I've started the program, and I'm going to the collections option. There I add a new collection, but I don't know how to add fonts to the new collection.
The program version is 0.7.4. I have used a previous version of the program in Ubuntu 16.04, and in fact I have some collection created.
Could someone give me a hand?

---

### Post by #&amp;thj^% on 2019-04-03
If I understand you, here is a few ways: [https://askubuntu.com/questions/8452/font-viewer-for-font-collectors](https://askubuntu.com/questions/8452/font-viewer-for-font-collectors)
For my collection I keep a ".fonts" folder in my home directory.
 rebuild the font cache with
```
 fc-cache -f -v
```

---

### Post by jrrpnani on 2019-04-03
When I used font-manager it was a bite different. You can use different fonts folders that you assign in font-manager, then activate the fonts you want to use (not to install). The collection you create help to have fonts in groups.
But now I can't make collections. And to activate fonts from different sources you must go to the preferences and check it, not just choose from the principal interface. If someone can help me just tell me if I doing something wrong...

---

