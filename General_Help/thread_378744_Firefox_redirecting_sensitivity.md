---
title: "Firefox redirecting sensitivity"
date: 2007-03-07
forum: General Help
---

### Post by jlhughes on 2007-03-07
I have found a web site that I CANNOT visit using Firefox, Mozilla or Opera from an Ubuntu machine (don't have any other flavors of Linux to test).  

HOWEVER, I have NO problem reaching this web site if I use Firefox on a Mac OSX box or WindowsXP.

When I attempt to visit mkfreeberg.webloggin.com/ or [http://webloggin.com/](http://webloggin.com/)

Firefox (and Mozilla and Opera) report:

[INDENT]The page isn't redirecting properly
   Firefox has detected that the server is redirecting the request for this address in a way that will never complete.
   *   This problem can sometimes be caused by disabling or refusing to accept
          cookies.
[/INDENT]

I have searched my settings. My default is to accept all cookies. I have specifically said to accept all cookies from this domain. Nothing works.

But if I go to a Mac or XP box and use Firefox, no error is reported.

Any ideas?  I realize this isn't an Ubuntu issue, but it is apparently limited to Linux flavors of browsers.

Thanks for any help.

---

### Post by markitect on 2007-03-07
I tried the site you mention from a readhat 9 system at work with firefox 2.0.0.2 and had the same problem, you should head over to bugzilla.mozilla.org and see if its been reported and if not report it.

---

### Post by ciscosurfer on 2007-03-07
> **jlhughes said:**
> I have found a web site that I CANNOT visit using Firefox, Mozilla or Opera from an Ubuntu machine (don't have any other flavors of Linux to test).  
 
HOWEVER, I have NO problem reaching this web site if I use Firefox on a Mac OSX box or WindowsXP.
 
When I attempt to visit mkfreeberg.webloggin.com/ or [http://webloggin.com/](http://webloggin.com/)
 
Firefox (and Mozilla and Opera) report:

[INDENT]The page isn't redirecting properly[/INDENT]

[INDENT]   Firefox has detected that the server is redirecting the request for this address in a way that will never complete.[/INDENT]

[INDENT]   *   This problem can sometimes be caused by disabling or refusing to accept[/INDENT]

[INDENT]          cookies.[/INDENT]
 
I have searched my settings. My default is to accept all cookies. I have specifically said to accept all cookies from this domain. Nothing works.
 
But if I go to a Mac or XP box and use Firefox, no error is reported.
 
Any ideas?  I realize this isn't an Ubuntu issue, but it is apparently limited to Linux flavors of browsers.
 
Thanks for any help.You can remedy this by installing a simple Firefox extension called User Agent Switcher, effectively allowing you to switch your user agent string within the browser, allowing you to view sites that are IE only, etc.

After you get it installed, restart Firefox, and then modify your User Agent string via Tools > User Agent Switcher.  Then choose Internet Explorer 6 (Windows XP).  Then view the site you were trying to view before.  Bingo!



Here's the link: [https://addons.mozilla.org/firefox/59/](https://addons.mozilla.org/firefox/59/)

---

### Post by ciscosurfer on 2007-03-07
> **markitect said:**
> I tried the site you mention from a readhat 9 system at work with firefox 2.0.0.2 and had the same problem, you should head over to bugzilla.mozilla.org and see if its been reported and if not report it.It's not a bug.  Read my first post.

---

### Post by jlhughes on 2007-03-07
User Agent Switcher "fixed" the trouble. Thanks

---

### Post by ciscosurfer on 2007-03-07
> **jlhughes said:**
> User Agent Switcher "fixed" the trouble. ThanksGood deal!

---

