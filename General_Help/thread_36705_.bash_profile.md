---
title: ".bash_profile"
date: 2005-05-24
forum: General Help
---

### Post by SychoSly on 2005-05-24
Can someone please tell me what is in the .bash_profile in the bottom of it, in the if loop. 

I forgot to back it up, and my teacher was messing around with it, and now I get errors in it. 

Please help. Thanks.

---

### Post by dataw0lf on 2005-05-24
The two standard if flow control statements in Ubuntu's .bash_profile are :

```


# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

```

---

### Post by JonahRowley on 2005-05-24
There's also a copy of this file in **/etc/skel**.

---

