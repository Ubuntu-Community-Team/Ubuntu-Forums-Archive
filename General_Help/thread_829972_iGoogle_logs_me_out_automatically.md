---
title: "iGoogle logs me out automatically"
date: 2008-06-15
forum: General Help
---

### Post by xjgnsdof on 2008-06-15
"You have been signed out. Sign in to see your stuff."

I'm tired of seeing that in Firefox. Yes, I save my cookies. And yes, I checked "Remember me next time" when logging in for the umpteenth time. This is either a bug or a quirk for which there is an elegant solution.

---

### Post by Dougie187 on 2008-06-15
What firefox do you use? and what have you dont so far to try and fix it. Also, what do you do inbetween logging in and getting that message?

---

### Post by xjgnsdof on 2008-06-15
I use the latest Firefox 3, though I've experienced this since Beta 5.

I have done the aforementioned things (cookies and "remember me") to try and fix it. Sometimes, I do nothing at all between logging in and getting that message. It just comes up at random times; I have yet to find a pattern.

---

### Post by Dougie187 on 2008-06-15
Have you tried firefox-2 to see if it is an issue in the beta of firefox3?

---

### Post by Dougie187 on 2008-06-15
Also, when you see that message have you ever checked to see if you have a cookie from google.com?

---

### Post by xjgnsdof on 2008-06-15
Yes to the cookie. And Firefox 2 produces the same error message after inactivity, to my knowledge. Even if it didn't, I refuse to go back to the slower, less stable Firefox 2.

---

### Post by Dougie187 on 2008-06-15
No offense, but unless your using one of the release candidates, I wouldn't really say its more stable. Granted Firefox 3 will fix a lot of issues, but a beta is hardly considered more stable then a release. 

I guess you could try flushing your prefrences and seeing if that helps.
If you want to back them up, so you have them incase this doesn't help, just open a terminal and rename your ~/.mozilla folder to ~/.mozilla.bak

```
mv ~/.mozilla ~/.mozilla.bak
```
Make sure that your firefox is closed when you do this too. Also, if you use thunderbird, or any other mozilla products this will reset those prefernces as well. And to replace your preferences, just move it back.

---

### Post by xjgnsdof on 2008-06-15
How exactly do I flush my preferences?

Aside: Isn't Firefox 3 a release candidate, coming out on Tuesday? Aren't those similar in stability as a result?

---

### Post by xjgnsdof on 2008-06-15
Screw this. I never really liked iGoogle anyway. I'm using a blank page as my homepage; more reliable and much quicker-loading.

---

### Post by Dougie187 on 2008-06-15
Double Post, read the next one.

---

### Post by Dougie187 on 2008-06-15
Hey, Sorry i was gone. Anyways, the firefox3 that is in the repositories is not a release candidate, even though ff3 comes out on tuesday. The one in the repos is Beta5. Hopefully on tuesday it will be updated. Also, you can change to a release candidate from [www.getfirefox.com](www.getfirefox.com) but you have to install it yourself. also i do know that FF3 has some issues with google things, like google toolbar is not compatible yet. So it might not work until after it actually gets released. Either way.

To flush your preferences, just close all mozilla programs(firefox, thunderbird, sunbird...etc). Then open a terminal, and type the following:
```
mv ~/.mozilla/firefox ~/.mozilla/bak.firefox
```

Then you can open firefox again, and see if it works.

If it does, then its something with the settings that you had on your firefox.

If it doesn't work, or you need to get some of your preferences back, you can reinstate your previous settings by following the same steps as above, but type
```
mv ~/.mozilla/bak.firefox ~/.mozilla/firefox
```

Let me know if this works for you.

---

### Post by anlayne on 2008-08-12
I had this problem with FF3 recently and realized that it was a program called CheckGmail that logged me out every time it refreshed. I switched to cGmail and I don't have this problem anymore.

---

### Post by Noremacam on 2008-08-14
I can confirm that I have this bug while I have checkgmail installed and running.

---

### Post by Noremacam on 2008-08-14
I uninstalled checkgmail shortly after my last post, and since then the bug has dissapeared, and I'm always logged into igoogle now.

---

