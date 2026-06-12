---
title: "Chrome browser weird white plus sign on black background being displayed"
date: 2017-02-07
forum: General Help
---

### Post by deadcool on 2017-02-07
Hello,

I came across an issue with Google Chrome. Intermittently when I click on a link, I see a weird white plus sign on a black background (screenshot enclosed). It keeps happening enough times.

Does anyone know how to fix this?

---

### Post by deadcool on 2017-02-08
Anybody?

---

### Post by leunam12 on 2017-02-09
Go to settings and uncheck "Display weird plus sign on black background".

Now, seriously, if it only happens on CHrome, have you tried purging Chrome and re-installing? That is the first thing that I would do. Maybe purge - update system - reinstall.

---

### Post by deadflowr on 2017-02-09
> Now, seriously, if it only happens on CHrome, have you tried purging Chrome and re-installing? That is the first thing that I would do. Maybe purge - update system - reinstall.

I would try replacing the chrome profile first.
To double check it's not a user setting issue.

I would simply move the chrome profile folder somewhere safe.
chrome will automatically generate a fresh profile when launched, if no profile exists.
The profile is located in /home/you/.config/google-chrome
it's a hidden folder.
You can move it anywhere outside that .config directory, or even just rename it something like google-chrome.old.

If that doesn't help fix the issue then you have the old profile and can easily move it back.

---

