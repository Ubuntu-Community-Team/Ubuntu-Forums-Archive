---
title: "Ubuntu Keeps Deleting My Browser Cookies"
date: 2021-05-21
forum: General Help
---

### Post by artcarney on 2021-05-21
I always "tell" my web browsers by their settings to not delete their cookies.

I was running Edge but got very tired when after about two days or so I had to log into all my web sites again (such as Facebook, Twitter, etc).

So I switched to Chrome but then I had the exact same problem. At this point I thought it was just a Chrome thing as Edge is based on Chrome.

So I switched to Firefox two days ago. Just now, I was once again logged out of all my websites AGAIN.

What is causing this and how do I correct it?

Running Ubuntu 21.04 on a PC.

---

### Post by dragonfly41 on 2021-05-21
I don't know the reason. 
But, as a precaution. I would install in (say) Chrome the extensions
OneTab and SessionBuddy to backup your sessions.
Also Zotero is good to keep url's with notes.

---

### Post by grahammechanical on 2021-05-21
Why do you assume that Ubuntu is causing the problem? I have yet to find a setting in Ubuntu Settings that will allow the deletion of cookie and passwords. Check Preferences>Privacy settings of the web browser. In Firefox it is in that settings page that we can tell Firefox to delete cookies and site data when Firefox is closed. It is also where we tell Firefox to ask to save logins and passwords for web sites. If we do not tick that box I do not think that Firefox would store the login details for that site.

Regards

---

### Post by artcarney on 2021-05-22
I've been running Linux in one form or another since the mid-1990's and I've never seen this. Just now I was running Chrome and suddenly in mid-session I wasn't logged in ANYWHERE anymore.

The reason I think Linux is causing this is because M$ Edge also is displaying the exact same problem. The big surprise to me is Firefox is ALSO getting it's cookies deleted.

---

### Post by dragonfly41 on 2021-05-24
Have you tested your theory by creating a new Ubuntu user account (guest) and testing browser(s) 
in guest account to see if cookies are lost/retained?

---

### Post by artcarney on 2021-05-24
Thanks. That's going to be one of my next steps. Currently I've tried using another desktop environment (that wasn't it) and turning off extensions. I've already eliminated the browser, I've tried both Firefox and Chrome.

---

### Post by &amp;KyT$0P# on 2021-05-24
Are you sure this is cookies being deleted?
Are you sure this isn't your IP address being changed?

---

### Post by artcarney on 2021-05-25
Well, after MUCH experimentation I finally concluded it was my password manager, LastPass. I disabled my extensions on Chrome and slowly enabled them, one by one. When I enabled LastPass, the problem returned.

I'm not sure why it's causing problems, it's settings are EXACTLY like on my windows machine and my Mac laptop. All use Chrome, all sync everything. While there are settings in LastPass that will delete your cookies, not are set to "on".

I've used this manager for years and this is the first time I've had any problems.

Time to find a new password manager that will work on all three of my computers and my iPhone.

grahammechanical was correct in that it wasn't Ubuntu itself.

---

