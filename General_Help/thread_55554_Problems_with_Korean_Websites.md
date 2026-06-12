---
title: "Problems with Korean Websites"
date: 2005-08-09
forum: General Help
---

### Post by gobfrey on 2005-08-09
Hi

  I'm runing Ubuntu Hoary, and using firefox for my browsing, and very happy with the whole experience I am too.

  My wife, however is having a lot of problems with the Korean websites she browses.  A lot of the functionality seems to be IE specific.  She has different problems on numerous sites.  I tried running Konqueror, and still no joy.

  I do have wine running, but the korean fonts are not installed and I don't know how to sort out the text input system.

Can anyone help me with this?

I really don't want to go back to dual boot.....

Adam

---

### Post by Marc Higgins on 2005-11-11
Hi Adam,

We are having some of the same issues here; we live & work in Seoul so Korean is fairly important to us & many korean sights don't work properly (in my view) because they are made with only MS java in mind & it's a bastardised java.

To be fair I have come across a number of US sights that are the same.

In terms of input methods the alternatives I know of are scim & nabi.

Have got scim running but Hoary doesn't seem to do korean properly, some 3 charicter letters can't be typed.

Have nabi working on a FC4 machine with gnome & it works a treat (apart from being a redhat machine). The only reason it's not an ubuntu machine is I haven't worked out Nabi on Breezy

Have had a few shots at getting nabi runing but i just end up with the input box & no thing to select for korean inut. My challenge is want to be able to do this not only in gnome but also xfce4 (xubuntu) & KDE

This is what i have installed.

Installed the following packages:Hi Adam,

We are having some of the same issues here; we live & work in Seoul so Korean is fairly important to us & many korean sights don't work properly (in my view) because they are made with only MS java in mind & it's a bastardised java.

To be fair I have come across a number of US sights that are the same.

In terms of input methods the alternatives I know of are scim & nabi.

Have got scim running but Hoary doesn't seem to do korean properly, some 3 charicter letters can't be typed.

Have nabi working on a FC4 machine with gnome & it works a treat (apart from being a redhat machine). The only reason it's not an ubuntu machine is I haven't worked out Nabi on Breezy

Have had a few shots at getting nabi runing but i just end up with the input box & no thing to select for korean inut. My challenge is want to be able to do this not only in gnome but also xfce4 (xubuntu) & KDE

This is what i have installed.
imhangul (0.9.11-1)
language-pack-gnome-ko (20051011)
language-pack-gnome-ko-base (20051011)
language-pack-ko (20051011)
language-pack-ko-base (20051011)
language-support-ko (20051010)
libnspr4 (2:1.7.12-1ubuntu1)
mozilla-browser (2:1.7.12-1ubuntu1)
mozilla-firefox-locale-ko (1.0-1ubuntu1)
mozilla-locale-ko (1.7-1)
nabi (0.15-1)
openoffice.org2-help-ko (1.9.129-0.1ubuntu5)
openoffice.org2-l10n-ko (1.9.129-0.1ubuntu3)
ttf-alee (4.7ubuntu1)
ttf-unfonts (1.0.1-2ubuntu1)
xfonts-baekmuk (2.2-1ubuntu1)


Then I have  

#sudo dpkg-reconfigure locales

decided i didn't really need 50 differnet kinds of english but i did need Korean, so  i selected the following; 

en_US.UTF-8 UTF-8
ko_KR.UTF-8 UTF-8
ko_KR.EUC-KR EUC-KR

the quick way to achivev the same this is sudo nano /etc/locale.gen  edit it to look like this & save it

en_US.UTF-8 UTF-8
ko_KR.UTF-8 UTF-8
ko_KR.EUC-KR EUC-KR

then run 

 sudo locale-gen

But when i run nabi for the term i see;

Nabi: Can't load config file
Nabi: xim server started

It starts but there are no fonts

---

### Post by reedlaw on 2005-11-11
I have the same problem with Chinese sites.  We just have to encourage everyone to use standards.  In the meantime, I am also wondering if it is possible to use SCIM within Wine.  I can run many apps in Wine without a problem but Chinese input is impossible.  Has anyone had any success with this?

---

