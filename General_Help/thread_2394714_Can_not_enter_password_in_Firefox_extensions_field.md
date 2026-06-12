---
title: "Can not enter password in Firefox extensions fields"
date: 2018-06-20
forum: General Help
---

### Post by gost. on 2018-06-20
Hi everyone,

I installed Ubuntu 18.04 recently, and I want to use some extensions for Firefox  that requires registration, such as *Hoxx VPN Proxy*. When I click on the field *Your Password*, the extension display exit. I also tried to access the field by pressing the *Tab* button, with the same result. I do not find any solution for my problem, any idea ? 

I have the same problem with all the extensions I tried that requires a password.
I tried to disable all others extensions, and reset configuration.

Thanks

My config:
Ubuntu 18.04 , minimal installation, without Canonical partners packages
Firefox Quantum 60.0.2

---

### Post by PaulW2U on 2018-06-20
> **gost. said:**
> I do not find any solution for my problem, any idea ? 
Take a look at bug report: [Ubuntu 18.04's ibus package breaks password fields in Firefox (by lowering & raising window whenever they're focused)]("https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1765304").

Does that describe what you're seeing? There is a workaround or temporary solution posted in comment 23. No-one has yet confirmed that it works or that it doesn't in the Launchpad  bug report although they have in the linked Mozilla report.

As the fix seems to involve patching a system package you might not want to risk installing the fix at this time.

---

### Post by gost. on 2018-06-20
Yes it is the same issue, I will try and let you know.

Edit:

It works perfectly, thanks !
 Here is the solution:

>                         On Ubuntu 18.04 the problem is solved if you installed the available package by clicking the link below
[https://bugzilla.mozilla.org/attachment.cgi?id=8974077](https://bugzilla.mozilla.org/attachment.cgi?id=8974077)
Here is the origin of the .deb
[https://bugzilla.mozilla.org/show_bug.cgi?id=1405634](https://bugzilla.mozilla.org/show_bug.cgi?id=1405634)


              
[TABLE]
[TR]
[TD][calvin (jcalvin)]("https://launchpad.net/~jcalvin")             wrote             on 2018-06-12:                          [/TD]
                       [TD="class: bug-comment-index"]           [ #23]("https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1765304/comments/23")           [/TD]
         [/TR]
            [/TABLE]


---

### Post by PaulW2U on 2018-06-20
Excellent, I'm glad the fix worked.

Hopefully the bug will soon be fixed in Ubuntu.

---

