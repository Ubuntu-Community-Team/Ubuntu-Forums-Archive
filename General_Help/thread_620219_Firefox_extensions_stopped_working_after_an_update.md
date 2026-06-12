---
title: "Firefox extensions stopped working after an update"
date: 2007-11-22
forum: General Help
---

### Post by kthdsn on 2007-11-22
A couple of days ago update notifier appeared with some updates.  As usual, I accepted them all.  One of them was a firefox ubuntu update.  Since this update I've had some problems with a couple of my firefox extensions.

The facebook toolbar no longer does anything when I click the login to facebook button.  It used to pop up a login window.

The Gmail Notifier extension no longer logs me into gmail.  The log in window appears but doesn't actually do anything.  Also, when I open firefox I get the following error:

TypeError: Components.classes['@mozilla.org/GMailNotifier;1'] has no properties

Both extensions worked fine before the recent update, and all of my other extensions are working normally (including Google Reader Notifier, web dev toolbar and several others).

I would appreciate it if someone could help me work out how to get these extensions working, particularly the Gmail Notifier one.  Would removing the extension and reinstalling it help?  I'm not really sure what else to try.

Thanks,

Kate

---

### Post by science4sail on 2007-11-22
Try reinstalling them.

Did you acidentally go to Firefox 3? A lot of extensions don't work there yet.

---

### Post by kthdsn on 2007-11-22
I tried reinstalling both extensions but their behaviour is the same, I'm still getting the same errors.

I haven't gone to firefox 3, my about page tells me this:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.8) Gecko/20071022 Ubuntu/7.10 (gutsy) Firefox/2.0.0.8

---

### Post by science4sail on 2007-11-22
Apparently,[ other people have also been seeing problems with 2.008]("http://developer.mozilla.org/devnews/index.php/2007/10/22/firefox-2008-update-to-be-updated/"). Try following the instructions under "Bug 396695".

---

### Post by kthdsn on 2007-11-22
Thank you, that fixed everything! :)

---

### Post by sudhu on 2007-11-28
Had the same issue. The bug fix worked for me too.

---

