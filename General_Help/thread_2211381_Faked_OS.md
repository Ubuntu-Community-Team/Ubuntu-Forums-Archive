---
title: "Faked OS?"
date: 2014-03-15
forum: General Help
---

### Post by robin7 on 2014-03-15
I'm a college student who hopes to avoid having to "convert" back to Windows.  So far so good, but I am required to turn rough drafts into a particular web site for their constructive input.  When I go to sign in, I run into a message that my OS is not supported (Windows, Mac, Google Chrome are supported).  

I would hate to switch back to Windows!  I suppose maybe I could try it in a virtual environment, but is there something strictly legal that I can do in my browser or something to make the web site think I'm using an "acceptable" OS?  I'm sure that Windows in a VM on this old hardware would be maddeningly slow.

---

### Post by Old_Grey_Wolf on 2014-03-15
Try this Mozilla site for instructions [https://support.mozilla.org/en-US/questions/679978](https://support.mozilla.org/en-US/questions/679978)

Be sure to read the link on that page to this site [http://www.useragentstring.com/pages/Firefox/](http://www.useragentstring.com/pages/Firefox/)

---

### Post by bapoumba on 2014-03-15
Please look for browser useragents. There are plugins for all major browsers.

Edit : nija'd by an astonished OGW :)

---

### Post by monkeybrain20122 on 2014-03-15
[https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/)

BTW, which stupid site is that?

---

### Post by Old_Grey_Wolf on 2014-03-15
> **bapoumba said:**
> Please look for browser useragents. There are plugins for all major browsers.

Edit : nija'd by an astonished OGW :)

As bapoumba said, also you may also find more current information that way.

---

### Post by Old_Grey_Wolf on 2014-03-15
> **monkeybrain20122 said:**
> 
BTW, which stupid site is that?

I don't understand the question.

---

### Post by bapoumba on 2014-03-15
> **monkeybrain20122 said:**
> 

BTW, which stupid site is that?

> **Old_Grey_Wolf said:**
> I don't understand the question.

+1. Sorry I thought it was a sig..

---

### Post by robin7 on 2014-03-15
> **monkeybrain20122 said:**
> [https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/)

BTW, which stupid site is that?

Haha, thats smarthinking.com.  Kind of a tutoring site for college students.  

The add-ons I've looked at for Firefox require me know some "string" (?) ahead of time!  How do I know what string to use?  I'm running Xubuntu 12.04 with Firefox and the web site wants Windows, Mac, or Google Chrome for an OS.

---

### Post by coldraven on 2014-03-15
> **robin7 said:**
> Haha, thats smarthinking.com.  Kind of a tutoring site for college students.  

The add-ons I've looked at for Firefox require me know some "string" (?) ahead of time!  How do I know what string to use?  I'm running Xubuntu 12.04 with Firefox and the web site wants Windows, Mac, or Google Chrome for an OS.

You don't need to know a string, just select from the list of available user agents. Selecting IE8 would likely satisfy most web-sites.

---

### Post by Old_Grey_Wolf on 2014-03-15
> **robin7 said:**
> Haha, thats smarthinking.com.  Kind of a tutoring site for college students.  

The add-ons I've looked at for Firefox require me know some "string" (?) ahead of time!  How do I know what string to use?  I'm running Xubuntu 12.04 with Firefox and the web site wants Windows, Mac, or Google Chrome for an OS.

Look at the second link in my original post.

The most current Firefox version in that list of strings is for version 25.0. For Mozilla/5.0 (Windows NT 6.1; Win64; x64; rv:25.0) Gecko/20100101 Firefox/25.0. If you are running FF version 27 than change that number 25.0 to 27.0.

---

### Post by monkeybrain20122 on 2014-03-15
> **robin7 said:**
> Haha, thats smarthinking.com.  Kind of a tutoring site for college students.  

The add-ons I've looked at for Firefox require me know some "string" (?) ahead of time!  How do I know what string to use?  I'm running Xubuntu 12.04 with Firefox and the web site wants Windows, Mac, or Google Chrome for an OS.

You don't need to know any string, choose something like "Firefox 24/Windows" from the drop down and it will work.

Idiots, why do they want to limit their client base?

---

### Post by robin7 on 2014-03-15
I successfully loaded the new useragent (Firefox on Windows, listed among "acceptable" combinations), but it didn't fool the web site.  I deleted cookies and tried again - still no joy.  That's a smart web site - with a dumb policy.  Is there anything else I can try?

---

### Post by sammiev on 2014-03-15
Make sure useragent is turned on, it should be blue in color.

---

### Post by robin7 on 2014-03-15
Yes it's "turned on," and passes the test offered at the add-on's web site.  It just doesn't fool that particular web site I guess.

---

### Post by monkeybrain20122 on 2014-03-15
> **robin7 said:**
> I successfully loaded the new useragent (Firefox on Windows, listed among "acceptable" combinations), but it didn't fool the web site.  I deleted cookies and tried again - still no joy.  That's a smart web site - with a dumb policy.  Is there anything else I can try?

Find another service, they don't want your business.

---

### Post by robin7 on 2014-03-15
That would be nice if the school allowed it.  But I'll mark it SOLVED, since the browser, on a third attempt, apparently fooled the site using the standard "Firefox on Windows" useragent string.  Success!  It looks like I'll at least make it through this semester without having to switch OSes!

Thanks to everyone who responded.

---

