---
title: "Firefox 2.0.0.2 not loading some web pages, help!"
date: 2007-03-01
forum: General Help
---

### Post by ZeroXR on 2007-03-01
I updated to Firefox 2.0.0.2 and Swiftfox 2.0.0.2 this morning and I have come to an odd problem...

Before, I had 2.0.0.1 and was able to goto some forums, mininova and youtube with no problems, but after the upgrade to 2.0.0.2, it seems like they get stuck in an infinite loop of loading at about the 95% completion of page loading.

Is there a setting I'm not aware about? Is my browser incorrectly configured?

I did have Firestarter running when I had 2.0.0.1 and had no problems. With 2.0.0.2 however, both with and without Firestarter, I'm running into that same problem.

Anyone run into this? Can anyone help me fix this?

---

### Post by ZeroXR on 2007-03-01
Another thing... I tried using Konqueror to visit Mininova and it loaded perfectly. That would rule out mininova being down.

---

### Post by bigken on 2007-03-01
could be ipv6 in the address bar type about:config then in the filter bar type ipv6 just double click the result to change the value

---

### Post by ZeroXR on 2007-03-01
**bigken:** That did the trick! My thanks to making my crappy day loads better! :-D

---

### Post by ZeroXR on 2007-03-01
Welp, scratch that...

I just logged in to my machine and it's back to not loading again. :-(

Here's what my about:config looks like...

```
network.dns.disableIPv6 - false
Set by User
```

---

### Post by bigken on 2007-03-01
try changing it back to true if you search the forum for ipv6 im sure you will find many other things to try and get your answer sorry I cant be of more assistance  its late  and im off to bed be lucky :)

---

### Post by ZeroXR on 2007-03-01
Thanks for the help no less! I'll try searchingon ipv6!

---

### Post by STREETURCHINE on 2007-03-01
type 

```
about:config
```

into the address bar

then ipv6 in filter

then double click the ipv6 and make it true

---

### Post by ZeroXR on 2007-03-01
I have played with having it both set on True and False with the same result... Pages still aren't loading.

---

### Post by yabbadabbadont on 2007-03-01
Provide a link to a page that doesn't work for you so that others can test it.

---

### Post by imspecial on 2007-03-01
mininova and the mininova forum load completely fine for me as does the site of youtube (no idea where the forum is if it has one)

I am using swiftfox 2.0.0.2 and have network.dns.disableIPv6 set to true if that matters at all

---

### Post by ZeroXR on 2007-03-01
[http://www.mininova.org](http://www.mininova.org)

---

### Post by ZeroXR on 2007-03-01
**imspecial:** I have tried both setting the value for the ipv6 to true and false with no success.

---

### Post by yabbadabbadont on 2007-03-02
Try disabling all extensions, Java, and JavaScript.

It loads fine for me by the way.

---

### Post by ZeroXR on 2007-03-02
> **yabbadabbadont said:**
> Try disabling all extensions, Java, and JavaScript.

It loads fine for me by the way.

Now that is trippy... It loaded! What is up with that? Anyone know why the test site (Mininova) would load without a hitch when the Java and Javascript were off versus those being on and the test site not loading?

---

### Post by yabbadabbadont on 2007-03-02
Now enable the things you disabled, one at a time, until you find the one causing the problem.

---

### Post by ZeroXR on 2007-03-02
> **yabbadabbadont said:**
> Now enable the things you disabled, one at a time, until you find the one causing the problem.

Javascript seems to be the offending feature that locks up the loading process. Java has no effect.

---

### Post by yabbadabbadont on 2007-03-02
> **ZeroXR said:**
> Javascript seems to be the offending feature that locks up the loading process. Java has no effect.

They are probably using IE specific syntax or something equally stupid.  :roll:

---

### Post by ZeroXR on 2007-03-02
Do you know if Konqueror can read IE syntax? The pages loaded fine on Konqueror, but I know the pages used to load just fine on Firefox 2.0.0.1. The update to 2.0.0.2 killed that functionality.

---

