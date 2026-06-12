---
title: "Is there any deb source for GVIM 7.1?"
date: 2007-08-22
forum: General Help
---

### Post by whjiang on 2007-08-22
My vim configuration requires vim 7.1 to run. However, in ubuntu 7.04, the vim is 7.0. Is there any deb source (unofficial) to allow me to upgrade my vim to 7.1?

Thanks

---

### Post by heimo on 2007-08-22
> **whjiang said:**
> My vim configuration requires vim 7.1 to run. However, in ubuntu 7.04, the vim is 7.0. Is there any deb source (unofficial) to allow me to upgrade my vim to 7.1?

Thanks

I don't know if it's safe to use, or brakes Feisty, but Gutsy seems to have 7.1.

---

### Post by igor54 on 2007-08-22
> **whjiang said:**
> My vim configuration requires vim 7.1 to run. However, in ubuntu 7.04, the vim is 7.0. Is there any deb source (unofficial) to allow me to upgrade my vim to 7.1?

Thanks

Go get this:
[http://rapidshare.com/files/37367886/vim_7.1-1_i386.deb](http://rapidshare.com/files/37367886/vim_7.1-1_i386.deb)

Works for me :)

---

### Post by horrendo on 2007-09-14
I tried to install that package but here's what I got ...

stbaldwin@au-stb-mobile:~/Desktop$ sudo dpkg -i vim_7.1-1_i386.deb 
Password:
dpkg: regarding vim_7.1-1_i386.deb containing vim:
 vim-runtime conflicts with vim (<< 1:6.4-001+3)
  vim (version 7.1-1) is to be installed.
dpkg: error processing vim_7.1-1_i386.deb (--install):
 conflicting packages - not installing vim
Errors were encountered while processing:
 vim_7.1-1_i386.deb

What did I do wrong?

Thanks,

Steve

---

