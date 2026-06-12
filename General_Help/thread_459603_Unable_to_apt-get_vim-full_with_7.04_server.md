---
title: "Unable to apt-get vim-full with 7.04 server"
date: 2007-05-30
forum: General Help
---

### Post by Lambdaz on 2007-05-30
I'd like to install vim-full to enable syntax coloring with my fresh Ubuntu 7.04 server edition installation.

I searched the packages.ubuntu.com and found the the vim-full belong to 'universe'.
I opened the /etc/apt/sources.list file and found the 'universe' as well as 'multiverse' lines are uncommented.

I think I can install vim-full with no problem, but when I apt-cache search vim, I find vim-common and vim-tiny only. NO vim-full!

Indeed, when I try to install other 'universe' packages, I failed.
But I can find 'mulitiverse' packages such as 'sun-java6' with no problem!

It's so strange. Would you help me?

---

### Post by zvacet on 2007-05-31
You are saying that universe is open and still you can not download files from it.try this

```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by fanatik on 2007-05-31
i don't have vim-full and syntax highlighting works for me - do you have it configured correctly?

---

### Post by Lambdaz on 2007-06-01
> **zvacet said:**
> You are saying that universe is open and still you can not download files from it.try this

```
sudo aptitude update && sudo aptitude upgrade
```

Thanks a lot! It works. I need to know more about aptitude.

I can see vim-full with apt-cache search. But when I install vim-full, it says some packages needed is not installable. For example:
libatk
libgnome2-0
libgtk2.0-0
....

I'm running command line vim, why it needs gnome related packages?
Then I try install 'vim'. Finally I can see syntax coloring enabled with my Python code. 8)

It says 'a bug report against that package should bu filed '. But how to report it?

---

### Post by Lambdaz on 2007-06-01
> **fanatik said:**
> i don't have vim-full and syntax highlighting works for me - do you have it configured correctly?

Yes, I succeed. But I install vim instead of vim-full. Maybe there is a bug with vim-full.

Since we are talking about 7.04. The lines in /etc/apt/sources.list is not commented. There is no need to edit that file.

The first thing you need to do is install vim. With aptitude commands mentioned above, you can install it.
Second, you need to trigger on 'syntax on':
```
cd ~
cp /etc/vim/vimrc .vimrc
```

Then remove the " before syntax on in the .vimrc file.

Now, it should work.

---

