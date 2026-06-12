---
title: "Firefox Notification Windows"
date: 2007-11-20
forum: General Help
---

### Post by martynp on 2007-11-20
Hi All,

I hope some can help me. Since switching to Ubuntu some months ago I have noticed something in Firefox that worked in Windows but doesn't seem to in Linux.

I have a couple of extenstions --- Google Reader Notifier and Update Notifier---- as examples. In Windows when you hover over the icons added by the extensions you got a pop up/notification showing various information. With the Google Reader one you can set it to show a notification window with an unread count. None of this works under Ubuntu. I tried a new extension this morning which shows me my router status etc. This is done when you hover over the icon in the status bar but yet again... nothing.

Obviously, I have seen other programs in Ubuntu that do this quite adequately, Rythmbox and Deluge are just to of many examples.

Am I missing something here?

Do I have to do anything to get these notifications working or is an Ubuntu specific problem?

I am using the latest version of Firefox, 2.0.0.8 ,but this problem manifested itself in all other versions I have run under Ubuntu. I am using Gutsy but the issue was the same in Feisty.

Any help much appreciated.

Many Thanks

---

### Post by NT4usB on 2007-11-20
Do you get popup tooltips over the standard Firefox icons?
If not, Type:```
about:config
```in the Firefox address bar.
Search for```
browser.chrome.toolbar_tips
```
Is it set to **false**?
Double click to change it to true...
Otherwise, must be a setting in the extension somewhere... I dunno.

---

### Post by martynp on 2007-11-20
OMG.... how bad do I feel?

Your suggestion was the answer!

However, they WERE switched of in Windows and I did get the tooltips..... but who cares.... it's working

Many, many thanks!

Martyn

---

### Post by NT4usB on 2007-11-20
Glad it worked out.
Be sure to mark this thread *solved*. Look under thread tools, upper right.

---

