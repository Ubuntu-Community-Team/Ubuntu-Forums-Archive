---
title: "Chinese Input Method"
date: 2005-03-26
forum: General Help
---

### Post by Lost on 2005-03-26
HI anyone knows of any kinds of chinese input method available in Ubuntu?

---

### Post by wk1989 on 2005-03-26
[QUOTE=Lost]HI anyone knows of any kinds of chinese input method available in Ubuntu?[/QUOTE]
There's fcitx, the one I use,  another popular one is SCIM. And there's also Chinput and zhcon  for chinese in terminal.

---

### Post by mesocool on 2005-03-28
[QUOTE=wk1989]There's fcitx, the one I use,  another popular one is SCIM. And there's also Chinput and zhcon  for chinese in terminal.[/QUOTE]

When I was trying to insatll fcitx, I found that there is no make file in the folder..  ](*,)

---

### Post by garyng on 2005-03-28
apt-get install scim should work.

---

### Post by mesocool on 2005-03-28
[QUOTE=garyng]apt-get install scim should work.[/QUOTE]

So that is another software..

---

### Post by garyng on 2005-03-28
well if you like fcitx:

apt-get install fcitx

---

### Post by mesocool on 2005-03-28
So bascially no matter which one I pick, I just need to apt-get to install? \\:D/

---

### Post by garyng on 2005-03-28
and some changes to your environment setup to tell X to use it. There should be some basic documentation comes with the package telling you how.

---

### Post by mesocool on 2005-03-28
[QUOTE=garyng]and some changes to your environment setup to tell X to use it. There should be some basic documentation comes with the package telling you how.[/QUOTE]

if you don't mind, could you send me that software you are using to [email]mesocool@gmail.com[/email], Thanks..

---

### Post by mesocool on 2005-03-28
Am I on the right track if I got the following message?

Smart Common Input Method 0.9.1

Loading simple Config module ...
Creating backend ...
Loading Server module: rawcode ...
    Loading Server Factory 0 ... : OK
rawcode Server module is successfully loaded.
Loading Server module: socket ...
Failed to load socket Server module.
Loading Server module: table ...
Failed to load table Server module.
Loading socket FrontEnd module ...
Starting SCIM ...

But how to start using it...

---

### Post by garyng on 2005-03-28
XMODIFIERS

google on it and you would find detail instruction. This tells X that there is some additional helper tools(input engine in this case) that it can use.

I have no idea the keyword used for fcitx/scim, but you should be able to find it, either under /usr/share/doc/* or google.

I think it is activated using ctrl-space but you need to tell it first through XMODIFIERS.

---

### Post by stellit on 2005-04-16
if u cant apt-get install scim.
just edit the sources.list, and erase the # in front of 

deb [http://cn.archive.ubuntu.com/ubuntu](http://cn.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://cn.archive.ubuntu.com/ubuntu](http://cn.archive.ubuntu.com/ubuntu) hoary universe

it must be work

---

### Post by mellibra on 2006-05-25
I try to apt-get install fcitx, But it says it couldn't find fcitx. I think maybe it's the problem of sourcelist. When I install ubuntu, I choose English. So how to update sourcelist to fix this problem? Thanks.

---

### Post by mellibra on 2006-05-25
OK, I installed fcitx, but how to configure to use it. I mean how to configure to autostart when I startx

---

