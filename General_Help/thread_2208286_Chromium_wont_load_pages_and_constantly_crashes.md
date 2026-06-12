---
title: "Chromium wont load pages and constantly crashes"
date: 2014-02-27
forum: General Help
---

### Post by danbuz on 2014-02-27
It takes forever to open simple pages, and once opened, they crash. I'm not able to change between pages or so. I completely removed chromium and it's folder, then reinstalled and the same happened.

When I open it the it alerts me this:

> [27967:27994:0227/201223:ERROR:nss_util.cc(776)] After loading Root Certs, loaded==false: NSS error code: -8018
ATTENTION: default value of option force_s3tc_enable overridden by environment.



Searched for similar problems and no success. Any suggestions ?

Thanks in advance!

---

### Post by Frogs Hair on 2014-02-27
How much ram do you have ? Chromium based browsers can be resource hungry .  Though Chrome is proprietary it might be worth installing to see if you experience the same behavior.

---

### Post by danbuz on 2014-02-27
4Gb of RAM. The problem started today, I've been using it for 2 months with no problem.

P.S. Chrome works fine, but i don't like the interface(different buttons, thinner tab). I would like to use chromium, but I guess it is not fixable?

---

### Post by danbuz on 2014-02-27
Anyone pls?

---

### Post by danbuz on 2014-02-28
Is this a bug or what? Should I consider could not use chromium from now on ?

---

### Post by Bucky Ball on 2014-02-28
You could consider holding your fire and bumping once every twenty four hours, please. Be aware that helpers are volunteers and we share many time zones. Please wait for awhile and you may get a response sooner than you expect. 

I can't imagine this is not fixable and no doubt there is someone lurking about that knows the fix and will get here eventually. In the meantime, research the problem, experiment, try some things out and report your results. 

Just out of curiosity, are you using Pepper Flash?

---

### Post by vasa1 on 2014-02-28
> **Bucky Ball said:**
>   ...
Just out of curiosity, are you using Pepper Flash?
OP says problems arise when opening "simple" pages. So there's an issue even without Flash of any kind.

---

### Post by sdowney717 on 2014-02-28
might be a hidden user config problem.

to test that, try making a new user, log in to new user

---

### Post by Bucky Ball on 2014-02-28
> **vasa1 said:**
> OP says problems arise when opening "simple" pages. So there's an issue even without Flash of any kind.

It will run in background 'in case' you hit a page where it is needed. If you look in Tools>Addons>Plugins you'll notice you have the option to 'Ask to Activate' as well as 'Always Activate'. When 'Always Activate' is set it will be on the look out for a flash situation and kick in automatically. I have mine set to 'Ask to Activate' which does nothing until you click the section of the page which is moaning about needing flash. Then you will get the option to 'Activate Now', which only activates it for this one instance, or 'Activate always for this page' (or something like that) which will set it to automatically activate for that page.

So, just wondering if some flash glitch might be an issue. Pepper flash with the regular flash also installed can sometimes be problematic also, regardless if flash is required.

---

### Post by raja.genupula on 2014-02-28
try to launch chrome from terminal. that can give us some debug information

---

### Post by danbuz on 2014-03-01
> **raja.genupula said:**
> try to launch chrome from terminal. that can give us some debug information


> [COLOR=#000000]*[27967:27994:0227/201223:ERROR:nss_util.cc(776)] After loading Root Certs, loaded==false: NSS error code: -8018*[/COLOR]
[COLOR=#000000]*ATTENTION: default value of option force_s3tc_enable overridden by environment.*[/COLOR]

This is what I got from terminal,  and no I do not use pepper flash. I could not load even simple text pages. New user do not help either! 
And I'm so sorry about the bumps, but I was terrified because I personalized chromium to such level, that I couldn't use any other browser.
I'm now with chrome, but when I logged in with my gmail account it does not sync my apps and history. I'm about to panic :)

---

