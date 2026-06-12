---
title: "Problem Password"
date: 2016-02-22
forum: General Help
---

### Post by andrea_libri on 2016-02-22
Hi, 


I took off my login password and now I try to set in back on and it doesn't work. It shows as if it worked but then when I go to the login screen it doesn't ask for a password. Can someone help me set it back?

---

### Post by Bucky Ball on 2016-02-22
You mean you set your machine to auto-login and when you switched off auto-login it is still auto-logging in? 

Which release and flavour of Ubuntu are you using, please?

---

### Post by andrea_libri on 2016-02-22
> **Bucky Ball said:**
> 

Which release and flavour of Ubuntu are you using, please?

How do I find out what version of software my Ubuntu is running?

---

### Post by andrea_libri on 2016-02-22
I restarted my computer and it works now! :o

---

### Post by andrea_libri on 2016-02-22
> **andrea_libri said:**
> How do I find out what version of software my Ubuntu is running?

I want to know this! :)

---

### Post by howefield on 2016-02-22
Open a terminal and type

```
cat /etc/lsb-release
```

or click on the Power symbol (cog wheel) in the top right corner of the top panel and select System Settings > Details..

Also

```
echo $XDG_CURRENT_DESKTOP
```

should tell you which desktop evironment you are running.

---

### Post by Bucky Ball on 2016-02-23
Also:

> lsb_release -a

... should get you the release. 

> uname -a

... will find kernel and other details.

Glad it's working even though we're not sure what the fix was. Please mark the thread as solved to help others (see first link in my signature for how).

Enjoy and good luck with it. :)

---

