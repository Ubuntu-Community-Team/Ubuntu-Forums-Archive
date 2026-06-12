---
title: "Best Korean font and other Korean questions"
date: 2005-10-24
forum: General Help
---

### Post by madtinkerer on 2005-10-24
Hi.

What's the best Korean font, in everyone's humble opinion?  I've tried a few but they all appear blurry and disproportional.  Also, how do a I set the universal Korean font in Gnome?  I have all the applications and menus in English, but when I type in Korean it looks terrible.

I've been reading all the CJK things I can find on the forums, but any other hints people have for integrating Korean input on my desktop would be great.  One more thing, is there any way to get NateOn messanger support on my computer?  A plugin for gaim perhaps?

Thanks

---

### Post by Marc Higgins on 2005-11-15
Our experiance with Korean setup so far;

We are having some issues with Korean web sites; we live & work in Seoul so Korean is fairly important to us & many korean sights don't work properly (in my view) because they are made with only MS java in mind & it's a bastardised java.

To be fair I have come across a number of US sights that are the same.

In terms of input methods the alternatives we tried are scim & nabi.

Have got scim running on Hoary but doesn't seem to do korean properly, some 3 charicter letters can't be typed.

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

