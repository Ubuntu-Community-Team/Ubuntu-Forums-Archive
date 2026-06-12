---
title: "How Do I Safely Downgrade From PHP 7.4 to PHP 7.2"
date: 2020-10-28
forum: General Help
---

### Post by aaronesteban on 2020-10-28
I'm trying to install Mautic, but Mautic keeps giving me an error message saying that their software can't process PHP 7.4 yet and that I needed to downgrade to 7.2.
What is the best way to do this?

Any support is greatly appreciated.

---

### Post by ActionParsnip on 2020-10-28
What is the output of
```

lsb_release -a; uname -a

```

Thanks

---

### Post by DuckHook on 2020-10-28
Please refrain from nonstandard fonts, sizes and formats because this causes problems for viewers who are on small devices or otherwise sight&#8209;impaired.

Thanks for raising awareness for Mautic. I was unaware of its existence until your post.

If I were you, I would pose this question to the Mautic community. Their support forum is: [https://forum.mautic.org/c/support/8](https://forum.mautic.org/c/support/8)

They would be more knowledgeable about the base conditions required for their software than a more general forum like ours.

By way of an educated guess, I suspect that the best solution would be to install an older OS on which to run Mautic. I assume that anything as overarching as Mautic will be running as the central (if not dedicated) app on that specific server, so an older version like Bionic is not a big deal. 18.04 still has three years of life left in it, so running it is perfectly fine.

It is ***NOT*** a good idea to downgrade PHP in you current install (which I assume is Focal). PHP is a foundational component in all Linux OSes. Therefore dickering around with it will likely break your system is all sorts of highly unpleasant ways. It's better to run a version in which the older PHP version is a cohesive part of the system. I don't know when 7.2 was still the go-to version, but the members of the Mautic support forum would likely know that.

---

### Post by dragonfly41 on 2020-10-28
Mautic looks interesting .. will experiment with it.
In return .. 
[https://ostechnix.com/how-to-switch-between-multiple-php-versions-in-ubuntu/](https://ostechnix.com/how-to-switch-between-multiple-php-versions-in-ubuntu/)

---

