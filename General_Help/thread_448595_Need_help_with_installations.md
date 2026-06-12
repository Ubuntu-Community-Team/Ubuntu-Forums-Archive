---
title: "Need help with installations"
date: 2007-05-19
forum: General Help
---

### Post by toylas on 2007-05-19
hi all,

I am new to ubuntu. I want to install some packages from scratch by compiling them instead of using synaptic package manager (I want to make individual installations in the opt directory). When I try to configure fluxbox I get the following error:

checking for X... no
configure: error: Fluxbox requires the X Window System libraries and headers.

I can not locate the X include files anywhere. I do not see an option to install include files (or I don't recognize one :( ). 

Similar thing happens when I try to compile GNU Data Language. It does can not find readline package. I can locate only libreadline.so. That's it. And I can't find/recognize the option to install include packages for readline. 

Could you please tell me if I'm being stupid or I have to do something more? I do not want to compile X, readline from source as I do not want to take the risk of corrupting the existng installation. 

Thanks,
Tulasi

---

### Post by Cene on 2007-05-19
I think the problem is that you don't have the *xserver-xorg-dev* package. Try installing it from repos.

---

### Post by RedSquirrel on 2007-05-19
xorg-dev is the metapackage. I recommend that.

For Fluxbox, I would also recommend you do:

```
sudo apt-get build-dep fluxbox
```to install anything else that might be required.

For readline, there is libreadline5-dev.

---

### Post by toylas on 2007-05-19
Thanks guys! It works fine now.

Thanks

---

### Post by RedSquirrel on 2007-05-19
> **toylas said:**
> Thanks guys! It works fine now.

Thanks

You're welcome. Just out of curiosity, which version of Fluxbox did you install? The latest subversion version? :)

---

