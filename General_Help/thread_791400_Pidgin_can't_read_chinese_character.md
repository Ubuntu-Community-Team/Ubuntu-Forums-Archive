---
title: "Pidgin can't read chinese character"
date: 2008-05-12
forum: General Help
---

### Post by dzaia-bs on 2008-05-12
Hi,
is anybody know how to solve this problem?
[IMG]http://blog.dzaia-bs.com/pictures/pidgin_bugs.png[/IMG]

I have installed chinese language pack for gnome and kde.
do I need to install any other library?

Thanks.

---

### Post by Brucevdk on 2008-05-18
I tried setting a message myself and it worked like a charm. But as soon as I uninstalled the package/font *ttf-arphic-uming* the whole system (including Pidgin) was unable to display certain Chinese symbols (apparently because of [font substitution](http://en.wikipedia.org/wiki/Font_substitution)). I did have to restart Pidgin first though.

I'm just wondering, what font are you using? I am using Bitstream Vera Sans (System -> Administration -> Appearance -> Fonts). I'm asking because of the following bug report in the Pidgin issue tracker, [#3535](http://developer.pidgin.im/ticket/3535#comment:1). In it rekkanoryo states:
> We have supported Unicode for years. You are using a font which does not contain the proper glyphs for the symbols you are typing.
Also see [the Fonts section of the Wikipedia Unicode article](http://en.wikipedia.org/wiki/Unicode#Fonts).

---

### Post by dzaia-bs on 2008-05-23
I've tried almost all fonts that are listed in fonts option (System -> Administration -> Appearance -> Fonts), but the pidgin still cannot read the status (in Chinese) properly.

It was not mine, it was my friend's MSN status.

By the way, it's not only happened in Linux environment, but also in Windows.

---

### Post by Brucevdk on 2008-05-23
> **dzaia-bs said:**
> I've tried almost all fonts that are listed in fonts option (System -> Administration -> Appearance -> Fonts), but the pidgin still cannot read the status (in Chinese) properly.

Afaik this wouldn't really matter since most of those fonts don't actually have any Chinese glyhps, try installing all of the Chinese fonts (it should magically work through font substitution, even when for example using Bitstream Vera Sans as your actual font). Here's the command:
```
sudo apt-get install ttf-arphic-bkai00mp ttf-arphic-bsmi00lp ttf-arphic-gbsn00lp ttf-arphic-gkai00mp ttf-arphic-ukai ttf-arphic-umin
```

> **dzaia-bs said:**
> It was not mine, it was my friend's MSN status.
All I did was try and reproduce the behavior, in which I somewhat succeeded (I have myself on my buddy list so it's close enough to what you describe).

---

