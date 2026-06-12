---
title: "Keyboard Configuration"
date: 2005-03-23
forum: General Help
---

### Post by andradelipe on 2005-03-23
Me again, 

My keyboard (brazilian ABNT2) don't work propertly, there is 2 keys changed, one of it, is the one that print this: "| \" , and the other, is from the number keypads, the "." doesn't exists anymore. 
There aren't problems in XFREE86.

anyone? :lol:

---

### Post by Paul Sinnett on 2005-03-23
[QUOTE=andradelipe]Me again, 

My keyboard (brazilian ABNT2) don't work propertly, there is 2 keys changed, one of it, is the one that print this: "| \" , and the other, is from the number keypads, the "." doesn't exists anymore. 
There aren't problems in XFREE86.

anyone? :lol:[/QUOTE]

 I found this link:

[https://bugs.freedesktop.org/show_bug.cgi?id=1257](https://bugs.freedesktop.org/show_bug.cgi?id=1257)

It seems to be a bug in X. It should be possible to fix it with a small edit.

---

### Post by andradelipe on 2005-03-29
I've reconfigured it with "dpkg-reconfigure xserver-xorg xorg" command. The key is in the right place now, but,  another weird thing happens now , my numeric keypad doesn't work anymore, it act like my mouse, just control the mouse pointer. Someone have an idea to solve it?

---

### Post by ola on 2005-03-29
It's not just that silly that you have forgot to push the num-lock key on the keyboard (if brazillian keyboards have those buttons (I always forgett mine ^_^))

---

### Post by andradelipe on 2005-03-29
Is not simple like that, Yes, it have a num lock, but nothing happens when it is pushed, except the little num lock light..
I've seen that this problem didin't apears when I move to text mode, just happens in my KDE 3.4  ](*,)

---

### Post by andradelipe on 2005-03-30
The Keyboard odissey!!!

Friends,

i've seen that my problem is not x.org, is in KDE 3.4 , I know that because on pure text mode, everything works so fine, and I've got the line "session imput" from another user who the keyboard works fine.. 
So, now the problem seems to be larger, anyone?

---

### Post by rigues on 2005-04-01
I've found a solution on a page about Xorg on Debian. Basically, it involves exchanging XFree86 for Xorg, and a small change on the /etc/x11/xorg.conf file. Solved the problem for me, hope this helps.

[http://www.ubuntuforums.org/showpost.php?p=111909&postcount=5](http://www.ubuntuforums.org/showpost.php?p=111909&postcount=5)

-- 
Rafael Rigues
[email]rigues@gmail.com[/email]

---

### Post by Musashi on 2005-04-18
[QUOTE=andradelipe]Me again, 

My keyboard (brazilian ABNT2) don't work propertly, there is 2 keys changed, one of it, is the one that print this: "| \" , and the other, is from the number keypads, the "." doesn't exists anymore. 
There aren't problems in XFREE86.

anyone? :lol:[/QUOTE]
 sudo gedit /usr/X11R6/lib/X11/xkb/keycodes/xfree86

Scroll to the very end of file
// For brazilian ABNT2 keyboard. by Ricardo Y. Igarashi(iga@that.com.br)
xkb_keycodes "abnt2" {
include "xfree86(basic)"
<BKSL> = 94;
<AC12> = 51;
<KPPT> = 134;
};

and include a option:

<AB11> = 211;

Will look like:
// For brazilian ABNT2 keyboard. by Ricardo Y. Igarashi(iga@that.com.br)
xkb_keycodes "abnt2" {
include "xfree86(basic)"
<BKSL> = 94;
<AB11> = 211;
<AC12> = 51;
<KPPT> = 134;
};

then 

$sudo dpkg-reconfigure console-data

Select from arch list
qwerty
brazilian
standart

reset the X
on gnome question about the keyboard layout choose x window configuration!

Then it's done!

---

