---
title: "The URL is not valid and cannot be loaded WTF?"
date: 2006-11-25
forum: General Help
---

### Post by nu2this on 2006-11-25
Today I got a box that has that error on every time click Fx, as well as some pages.After I click the box it goes to Fx, but this is annoying. What the H*** is this & how to fix?

---

### Post by xmastree on 2006-11-25
Next time it happens, grab a screenshot so we can see what you mean...

---

### Post by DaveBorealis on 2006-11-25
Hello,

Just a couple questions to help you get an answer:
1) Where are you trying to click Fx?  (Bookmark, webpage, etc)
2) What is the url of Fx?
3) What exactly does the box say?

Best regards,
Dave

---

### Post by nu2this on 2006-11-25
OK Here it is

---

### Post by wastrel on 2006-11-25
Maybe the URL for the Firefox homepage (which Ffox tries to load whenever you start it) is broken.

Try checking the homepage setting in  Firefox,  Edit > Preferences > Main

---

### Post by temcat on 2006-11-25
If you mean that this box pops up every time you launch **Firefox**, chances are that the address of the home page in Firefox is misconfigured. In Firefox, open Edit->Preferences and check the Home Page field to see if the URL entered there is valid.

Hope this helps.

---

### Post by nu2this on 2006-11-25
That comes up on other pages even the Goodrich corp. webpage, so that's probably not it.

---

### Post by nu2this on 2006-11-25
bump

---

### Post by kerry_s on 2006-11-25
Make sure the command for the launcher is just "firefox" if it has anything after that delete it.(ie: % some letter)

---

### Post by nu2this on 2006-11-25
Do you mean properties>launcher>command? It reads firefox %u delete the %u?
This begs the question what about the other pages where it happened?
Bad news it didn't work.

---

### Post by xmastree on 2006-11-26
Ah, so it appears when you try to load firefox? Maybe something in your firefox config is broken. If you don't mind losing any bookmarks, cookies etc. try deleting the ~/.mozilla/firefox directory (use nautilus, press Ctrl-H to view hidden files).
Next time you run firefox it'll syart as if it was run for the first time.

Failing that, I'd try re-installing it with Synaptic.

---

### Post by nu2this on 2006-11-30
Sorry to have taken so long to get back. It was a theme I installed that caused the problem, just deleted the profile & marked Fx for reinstall in Synaptic. All is well now.

---

