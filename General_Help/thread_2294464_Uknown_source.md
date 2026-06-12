---
title: "Uknown source"
date: 2015-09-11
forum: General Help
---

### Post by NaneK on 2015-09-11
Hi guys,

I wanted to install icon theme that I found here on forum, but I one thing is not clear to me.
Well the icon theme is called Xenlism Wildfire, and you can find more info about it here: [http://xenlism.github.io/wildfire/](http://xenlism.github.io/wildfire/)

The thing that bugs me is the installation of this icons theme.
It says that I have to do this:
```
sudo apt-key adv --keyserver keys.gnupg.net --recv-keys 90127F5B
```

And then:
```
echo "deb http://downloads.sourceforge.net/project/xenlism-wildfire/repo deb/" | sudo tee -a /etc/apt/sources.list
```


Well this is new to me. I know how to deal with PPA, but this key thing - never heard about it.
I do not want to install something that is untrusted, so I wanted to ask is this safe way to install something (safe as in would you install it)?

Thanks!

---

### Post by howefield on 2015-09-11
What's the issue ?

Your tolerance to risk is the deciding factor when installing from anywhere outside the official repositories and that includes a ppa (which also have keys). The above package appears to be genuine, I wouldn't have a problem trusting it, others might.

---

### Post by NaneK on 2015-09-11
Thanks for reply.
Well there is not issue, I just wanted to know what is that, since I never installed anything that way.

With PPA I do not enter any keys, so this is new to me. What is that key, and why is it needed?
And what is that sudo tee command? What does it do to that file?

I would just like to know more about this type of installing software.

Thanks!

---

### Post by qamelian on 2015-09-11
When you add a PPA, the keys get downloaded and imported automatically. The other command is adding the necessary repository to your Ubuntu system, so you can install the them that you want and have it update automatically, when the developer creates new versions.

---

### Post by NaneK on 2015-09-11
Thank you!

---

