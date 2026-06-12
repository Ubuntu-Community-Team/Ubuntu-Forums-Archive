---
title: "Use of sudo"
date: 2012-10-24
forum: General Help
---

### Post by otetiani on 2012-10-24
I was reading up on the use of sudo and have 2 questions:

1) I read that sudo should NEVER be used for launching graphical applications like gedit and that gksudo should be used.  So does this mean when I launch, relaunch lightdm I should:
```
gksudo start lightdm
```

2) Is there a way to shorten the timeout for sudo from 15 min to say 1 minute?

Thanks

---

### Post by MG&amp;TL on 2012-10-24
> I was reading up on the use of sudo and have 2 questions:

1) I read that sudo should NEVER be used for launching graphical applications like gedit and that gksudo should be used.  So does this mean when I launch, relaunch lightdm I should:
```
gksudo start lightdm
```LightDM isn't technically graphical, as it's just a daemon that launches graphical things. So no. However, things like firefox, yeah. :)

> 2) Is there a way to shorten the timeout for sudo from 15 min to say 1 minute?

Thanks
[http://philipwyett.wordpress.com/2009/02/17/ubuntu-remove-5-minute-sudo-timeout/](http://philipwyett.wordpress.com/2009/02/17/ubuntu-remove-5-minute-sudo-timeout/)

...is, I believe, what you're looking for. That guide's for disabling it entirely. Just swap 0 for 1 where appropriate.

---

### Post by otetiani on 2012-10-24
Thanks MG&TL, that was what I was searching for, and thanks for the clarification!

---

