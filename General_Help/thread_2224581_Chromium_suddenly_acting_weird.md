---
title: "Chromium suddenly acting weird"
date: 2014-05-16
forum: General Help
---

### Post by matbluvenger on 2014-05-16
A website I use often (MLSsoccer.com) allows you to use facebook accounts to log in to comment threads and fantasy soccer games.

Today, out of the blue, I can no longer see the comments or the comment text box and I am unable to log in to the fantasy game.

It works just fine on the Windows 7 side of my rig so I figure it must be an issue on the Ubuntu 14.04 side running Chromium.

Thank you in advance for any help provided.

---

### Post by grier-devon on 2014-05-17
Are you running Chromium in Windows 7 as well or Chrome? Do you have pepper installed for chromium? Have you also tried to view the website with Firefox?

---

### Post by matbluvenger on 2014-05-17
No I haven't installed chrome. But no I haven't tried Firefox yet. I'll give that a shot when I get the chance.

---

### Post by matbluvenger on 2014-05-17
Tried it in Firefox and it worked just fine, so obviously Chromium. I uninstalled Chromium and reinstalled but that didn't help. 

So I tried installing google-chrome-stable and I can now see the comments but I still can't log in to Fantasy. Usually you click on "Start Playing" or "Login" and it'll bring up a pop-up that shows ways to login (FB, Twitter, etc.) but the pop-up never shows up.

I noticed in the address bar that it wasn't allowing cookies even though I allow cookies on that website. Could that have anything to do with it? And why would it be blocking them when I allow it?

EDIT: When I'm on a page with comments (that I can actually see now) the "Blocked Cookies" symbol goes away. What the heck....

---

### Post by bapoumba on 2014-05-17
Any extension ?
Does it work if you make a fresh user ?

---

### Post by bazsound on 2014-05-17
firefox is better anyway, ive always found chromium to be hit or miss, sometimes it would be fine then it would become unstable. last time i checked chromium uses its own version of flash plugin. Im sure there are directions to get chromium to use adobes plugin instead.

---

### Post by grier-devon on 2014-05-17
If installed on 14.04 you can install "pepper" which is the same plugin Chrome uses which is adobe. I do not advise to use the Adobe Flash plugin as it will stop working with Chromium here in the future if not already. Chromium is a hit or miss for me, like anytime on my college school portal I need to send a professor an email once I click send it crashes every time.

Chrome and Chromium have become so popular on Ubuntu is because they have a better flash plugin currently then Firefox, however that is about to change as Firefox is about to implement Flash and many other DRM type plugins to keep up with the rest of the browser market. Firefox has always rendered websites better for me and since Firefox 28 (now using 29) I notice no difference in speed from Chrome or Chromium.

---

### Post by matbluvenger on 2014-05-19
After much tinkering with regular Chrome I seem to have it figured out.

Thanks for the help everybody.

---

### Post by bapoumba on 2014-05-19
Glad to see you got it to work !
Posting what you actually did to make it work could be useful to other users reading your thread.
And thanks for marking your thread as solved :)

---

### Post by Doug_Mandell on 2014-06-06
> **matbluvenger said:**
> After much tinkering with regular Chrome I seem to have it figured out.

Thanks for the help everybody.


I've got this problem as well and haven't been able to figure it out.  This is a brand new install of 14.04, no plugins yet or anything.  I've resorted to using Firefox when I'm using the site because I haven't had a chance to dig into this yet . Could you post your solution?

---

### Post by monkeybrain20122 on 2014-06-06
> **Doug_Mandell said:**
> I've got this problem as well and haven't been able to figure it out.  This is a brand new install of 14.04, no plugins yet or anything.  I've resorted to using Firefox when I'm using the site because I haven't had a chance to dig into this yet . Could you post your solution?

[http://www.webupd8.org/2014/01/pepper-flash-player-installer-for.html](http://www.webupd8.org/2014/01/pepper-flash-player-installer-for.html)

---

### Post by matbluvenger on 2014-06-06
Basically what was happening was the cookie settings wouldn't stay permanently on chromium. I installed actual Chrom and fiddled with cookie allowances until end everything seemed to work.

---

### Post by matbluvenger on 2014-06-06
> **monkeybrain20122 said:**
> [http://www.webupd8.org/2014/01/pepper-flash-player-installer-for.html](http://www.webupd8.org/2014/01/pepper-flash-player-installer-for.html)

No this isn't really a plug in issue. But thanks for adding that. Chromium or Chrome asks you if you want to install pepper when you come to a site with flash.

---

### Post by monkeybrain20122 on 2014-06-06
You should start a new thread of your own, as not too many people would click on a thread already marked "solved" except to look for answers.

---

