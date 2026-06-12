---
title: "Still unable to get Firefox working with Pipelight"
date: 2016-04-06
forum: General Help
---

### Post by jdkcarlson on 2016-04-06
I am running Trusty Tahr and want to watch Netflix through Firefox. I've installed Pipelight according to the instructions here

[http://ubuntuforums.org/showthread.php?t=2284778](http://ubuntuforums.org/showthread.php?t=2284778)

and the Firefox plugins, as well as a Firefox add-on called User-Agent Switcher, but no matter what I choose, I get redirected to Netflix system requirements or asked to install something and restart. What can I do?

(I added this question to the end of the solved thread above thinking it was the least disruptive way to achieve further clarification, but this was incorrect.)

---

### Post by Habitual on 2016-04-07
Google Chrome can play netflix without plugins.
Not _Chromium_, ***Chrome***.

---

### Post by SeijiSensei on 2016-04-07
What did you enter for the User-Agent string?  It should look something like
```
Mozilla/5.0 (Windows NT 6.1; rv:45.0) Gecko/20131011 Firefox/45.0
```
Firefox 45.0.1 is the current version on Windows.  Sometimes Netflix will refuse to start if you send a UA string with an outdated version number.  My browser is currently sending 39.0 which does work, but you might as well update the UA to the current version.

---

### Post by deadflowr on 2016-04-07
^^^This.
Whatever user agent string you use, DO NOT use Internet Explorer 8.
(As you posted you tried in the now closed thread)
Netflix knows that browser is dead.

And if I remember right IE strings aren't very good in the first place.

---

### Post by jdkcarlson on 2016-04-08
I was able to get Netflix working on Chrome, but wanted to get it working in Firefox too on principal.

This code worked for me. I didn't realize that there was an option to select the user-agent string manually and had been selecting OS and browser at random hoping to pick the magic combination, without success.

The IE8 was one of the options on the first User Agent Switcher I downloaded, an add-on that looks like it dates back to 2011. I realized at the time that that wasn't very recent but had the wrong plug-in.

I'm marking this as solved. Thanks, all!

---

### Post by SeijiSensei on 2016-04-11
I use [UAControl]("https://addons.mozilla.org/en-us/firefox/addon/uacontrol/") myself.  It lets you specify the User-Agent by the target domain.

---

