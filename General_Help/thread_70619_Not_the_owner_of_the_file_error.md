---
title: "Not the owner of the file error?"
date: 2005-09-30
forum: General Help
---

### Post by 68Firebird on 2005-09-30
I reinstalled Ubuntu being I had problems getting things to install. So I thought I would start all over.
With the brand newinstall. I am trying to move my book marks and some setting into the Firefox profile folder but when I try I get a error "I am not the owner of the file". I am seeing this same error on other folders also.

As far as I know I only created 1 login. Did I do something wrong in the installation process? How can I become the owner of all these files I cannot at this point modify?

---

### Post by aysiu on 2005-09-30
Where are you moving them *from*? You may, in fact, not be the owner of the file if it's not in your /home/username folder already.

One quick way around this is to run the command *gksudo nautilus* and then temporarily assume root privileges.

Otherwise you can use the command *chown* to change ownership

---

### Post by 68Firebird on 2005-09-30
[QUOTE=aysiu]Where are you moving them *from*? You may, in fact, not be the owner of the file if it's not in your /home/username folder already.
One quick way around this is to run the command *gksudo nautilus* and then temporarily assume root privileges.
Otherwise you can use the command *chown* to change ownership[/QUOTE]

I am trying to eddit my firefox profile. Is this where it is? /etc/mozilla-firefox/profile

That is the file I am getting the "not the owner" error. I would like to add some of the key setting from my windows firefox profile to the one in Ubuntu.

---

### Post by 68Firebird on 2005-09-30
Brain fart, I was trying to eddit the wrong file. I found my firefox profile when I selected "show hidden files". Got it sorted out now.

---

