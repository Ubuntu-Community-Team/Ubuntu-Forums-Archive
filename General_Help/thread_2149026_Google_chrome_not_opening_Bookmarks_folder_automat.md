---
title: "Google chrome not opening Bookmarks folder automatically."
date: 2013-05-27
forum: General Help
---

### Post by c2tarun on 2013-05-27
Hi friends,

This might seems a small problem, but is slightly annoying sometimes. I have folders in bookmarks toolbar. When I click on one folder its lists opens, but when I move pointer to other folder it doesn't opens. I have to click on that folder to open its list. This is not the case with firefox and in windows chrome also doesn't have this problem.

[ATTACH=CONFIG]243125[/ATTACH]
See in the image I clicked "Articles" it opened its lists. But when I moved my pointer to forums it is not opening. I have to click on forums to open it.

Can anyone please suggest a solution?

---

### Post by c2tarun on 2013-05-29
bump

---

### Post by mikeym on 2013-05-29
I'm not sure I entirely understand what the behaviour you're expecting is, but could it be a difference between Chrome and Chromium? Which are you using on Ubuntu? 

If it's a definite issue with Chromium not behaving as you would expect then you could open a bug report "issue" [http://code.google.com/p/chromium/issues/list](http://code.google.com/p/chromium/issues/list)

---

### Post by c2tarun on 2013-05-30
> **mikeym said:**
> I'm not sure I entirely understand what the behaviour you're expecting is, but could it be a difference between Chrome and Chromium? Which are you using on Ubuntu? 

If it's a definite issue with Chromium not behaving as you would expect then you could open a bug report "issue" [http://code.google.com/p/chromium/issues/list](http://code.google.com/p/chromium/issues/list)

I am using Google-Chrome.

Let me try to explain you my problem.

I have different folders in my bookmarks toolbar. Each and every folder have some certain category of bookmarks.
Now if I click on one folder its bookmarks are displayed in a drop down list. Now if I move my pointer to some other folder (in bookmarks toolbar) its contents should be displayed in a drop down list. But to display the content of second folder I have to click on it to display.

Try to create two folders in bookmarks toolbar and add some contents to both of them. Now click on anyone of them and move your pointer to other and then back to first. You'll understand what I am trying to say.

---

### Post by mikeym on 2013-05-30
I can see the problem now. It behaves on my system running Chromium (18.0.1025.151~r130497-0ubuntu1) in the way you suggest it should; clicking on one folder in the bookmarks bar makes the other folders open as you track your mouse across them. 

I can only suggest posting a bug to Google: [https://support.google.com/chrome/answer/95315?hl=en](https://support.google.com/chrome/answer/95315?hl=en)

---

### Post by mikeym on 2013-05-31
Actually looks like there are a number of chromium bugs reported for this issue:

[http://code.google.com/p/chromium/issues/detail?id=89594](http://code.google.com/p/chromium/issues/detail?id=89594)
[http://code.google.com/p/chromium/issues/detail?id=89850](http://code.google.com/p/chromium/issues/detail?id=89850)
[http://code.google.com/p/chromium/issues/detail?id=125550](http://code.google.com/p/chromium/issues/detail?id=125550)

I would still report it for your version.

---

