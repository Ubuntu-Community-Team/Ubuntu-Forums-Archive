---
title: "how to type korean"
date: 2005-05-01
forum: General Help
---

### Post by pdk001 on 2005-05-01
hello
i just want to type korean on notepad or something else
korean is work as well on the browser but i cant typing any korean it cant switch to put shift+space bar at a same time)
i dont want full korean in ubuntu i only typing korean
help me out please
thanks in advance

---

### Post by mrbass on 2005-05-03
this has finally been solved....I'll update my Japanese, Chinese input guide to include korean.  A week ago scim-hangul wasn't in the repositories and now it is.
but here's a quick way to install Korean input in the meantime
make sure universe is enabled in /etc/apt/sources.list
```
sudo gedit /etc/apt/sources.list
```
double check if the universe and multiverse lines are uncommented (remove # in the front of the lines)

```
sudo apt-get update
sudo apt-get install scim uim scim-uim scim-gtk2-immodule scim-hangul scim-tables-ko
```

Do the following in a terminal one line at a time (copy and paste)
```
sudo touch /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 646 /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XMODIFIERS="@im=SCIM"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export GTK_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XIM_PROGRAM="scim -d"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export QT_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 644 /etc/X11/Xsession.d/74custom-scim_startup
```
Then reboot and press CTRL-space to start inputting with Korean.

If I were you I'd go to System | Preferences | SCIM Input Method Setup and under IM Engines uncheck everything except Korean.  Then figure out which korean input methods you don't use and uncheck those too.

---

### Post by pdk001 on 2005-05-04
oh thanks you so much its work fine
that's why im here with my poor english. you guys never disappoint me
thanks you once again

park dong kyu

---

### Post by mrbass on 2005-05-04
someone mentioned nabi input method.....let me know if you ever get a chance to try that one out and report back which method you prefer.
[http://www.ubuntu.or.kr/wiki.php/InstallingInputMethods](http://www.ubuntu.or.kr/wiki.php/InstallingInputMethods)

---

### Post by pdk001 on 2005-05-04
i tried serveral times in korean site(exactly there [www.kldp.org](www.kldp.org)) there never any help for me so far like i above said that's why im here at english site with my poor english?
 there are almost newbies of linux users or they aint smarter than you guys
you guys always give me advices & imformations everthings i wanted

and this machine doesnt work korean typing at all( this machine didnt install korean during the installing linux)

---

### Post by mrbass on 2005-05-08
Yeah hopefully next ubuntu release (I have no idea though) will include outta the box CJK support as well as the other languages.  We don't want all Chinese, Japanese and Korean users to migrate to [http://www.asianux.com/](http://www.asianux.com/) now do we...hehe.

---

### Post by moon2js on 2005-05-08
I'm wondering if everyone else has encountered a problem with SCIM in Korean. Overall, it works generally very good without me having to do anything. But sometimes when I have gaim open and I want to switch to Korean mode, pressing [ctrl]+[space] completely closes the program without any warning or reason. I have to restart it and hope my friend is still there.

And I think this has happened to me at least once in Firefox. It seems to happen whenever I press [ctrl]+[space] to activate the Korean SCIM to type in &#54620;&#44544;.

Anyone else encounter this or have any ideas what might be causing it?

I've used nabi in the past, but imho SCIM is much nicer and more feature rich, much like the way Windoze handles input methods.

---

### Post by mrbass on 2005-05-10
[http://sourceforge.net/mailarchive/forum.php?forum_id=42962&max_rows=25&style=nested&viewmonth=200505](http://sourceforge.net/mailarchive/forum.php?forum_id=42962&max_rows=25&style=nested&viewmonth=200505)

see for utf on that page...seems to be many issue with UTF-8 encoding and GAIM.

---

