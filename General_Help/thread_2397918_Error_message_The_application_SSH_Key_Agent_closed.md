---
title: "Error message: The application SSH Key Agent closed unexpectedly"
date: 2018-08-04
forum: General Help
---

### Post by sajia on 2018-08-04
Every time I start up Ubuntu, I get the error message "The application SSH Key Agent closed unexpectedly". I'm translating, but it's something like that. Maybe "closed without warning".
It's the same every time: I log into Ubuntu, and after about 5 seconds a window pops up saying an application wants to use the keyring and asking for a password. Then after about 30-60 seconds, I get the error message and the option to send an error report.

I searched around and couldn't find anyone having this problem. I don't know what program might be using the keyring on startup. I'm very much a newbie, so I haven't edited with configuration files or installed any advanced utilities.
I'm tempted to follow the directions on this page to disable the SSH Agent:
[https://www.scivision.co/disable-gnome-keyring-ssh-agent/](https://www.scivision.co/disable-gnome-keyring-ssh-agent/)

But I'd rather not mess with system defaults if that can be avoided.

Any ideas? 


Ubuntu 18.04.1 64-BIT
Gnome 3.28.2

---

### Post by welshmike on 2018-08-07
I've been having the same problem for months and believe that it may be due to having MIcrosoft (ugh) Skype starting up or perhaps Chrome browser.
Sorry that I'm not providing a solution. Let's hope out problems get some attention.

---

### Post by welshmike on 2018-08-07
I've uninstalled Skype and rebooted. Thus far the problem has not recurred.

---

### Post by sajia on 2018-08-07
Thanks for the reply and finding at least one solution. My system doesn't have Skype. 
I tried uninstalling Chromium and rebooting, but still got the same error message.

---

### Post by welshmike on 2018-08-07
I also have Chrome (not Chromium) installed and believe that it also caused the problem.

---

### Post by sajia on 2018-08-09
Obviously there's something else in my case. Is there any risk to system stability or security if I disable the SSH agent from loading on startup?

---

