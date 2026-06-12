---
title: "Ubuntu on Chromebook stopped working"
date: 2015-05-14
forum: General Help
---

### Post by cwblanch on 2015-05-14
Hey,

Not really sure where to post this so decided to put it in general.

I've been trying to get Ubuntu on the Chromebook I never use, maybe it will get more use that way.
I tried Chrubuntu, but that didn't go well. It just wouldn't boot.
 Now I've tried Crouton, and I got it working well. While I was updating and installing packages I'll probably need, I got a prompt to update to 14.04, and wanting to be on the latest LTS I updated. The problem is it's now not starting from the ChromeOS at all after the update. Does Crouton not support 14.04?

I also don't seem to be getting any major errors. I'm getting a lot of Initializing, then system information and then:

```
/user/bin/xinit: connection to X server lost

waiting for X server to shut down Hangup

Unmounting /usr/local/chroots/precise...
```

Am I going to have to reinstall Crouton?

Thanks!

---

### Post by wildmanne39 on 2015-05-15
Looks like it is working here.
[https://github.com/dnschneid/crouton/issues/779](https://github.com/dnschneid/crouton/issues/779)

---

### Post by cwblanch on 2015-05-16
I think I narrowed down that 14.04 just doesn't work on Crouton on my particular Chromebook, so I just have to keep it on the previous LTS.
Thanks!

---

