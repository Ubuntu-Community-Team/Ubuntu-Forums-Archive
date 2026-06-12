---
title: "Museek install help"
date: 2008-05-22
forum: General Help
---

### Post by Jeztastic on 2008-05-22
Hi,

I have installed Museek from the repositories, but when I start up Musetup-GTK I get this error: 

```
Config failed, reading from template
No such file or directory: '/home/jez/.museekd/config.xml
```

Why has the config file not been created? What can I do about this?

Thanks!

Jez

---

### Post by Jeztastic on 2008-05-25
Bump!!!

---

### Post by caiooiac on 2008-07-16
I think by now you have already a solution, or just gave up museek, but anyway, I found on museek site, in FAQ:

Step 1: mkdir ~/.museekd
Step 2: touch ~/.museekd/config.xml
Step 3: museekd
.... wait a few seconds ....
Step 4: ctrl-c
Step 5: musetup

After step 3 you will have some errors. Just continue the steps.

Hope I helped...

Caio

---

### Post by Jeztastic on 2008-07-27
You're right, I had given up, but thanks for the advice. I will try this later!

---

