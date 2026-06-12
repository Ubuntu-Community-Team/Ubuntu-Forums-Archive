---
title: "Very Small Application fonts in Fluxbox"
date: 2008-02-23
forum: General Help
---

### Post by Chris_666 on 2008-02-23
Hi, this is kinda my very first post, so bear in mind that I'm also quite new to linux.

The thing is, I have just installed fluxbox a couple of days ago, with the help from some friends and a lot of googling. Although after fixing everything, there is still one, rather big issue, thats bugging me. - My fonts of all applications (nearly) are very small, nearly too small to read even. For an instance, the drop-down menus in the upper bar of firefox (file, edit, view, history etc etc) are incredibly small, and the same goes for a lot of other stuff, mail box (thunderbird), IM (pidgin/gaim) etc. 

it is not my actual style thats something wrong with, in fact, the fonts there are just fine, using zimek_darkblue.  On other forums, I have been reading some stuff about it too, although without any luck. Modifying the xorg.conf, adding the dpi, didnt really help, i have no gtkrc-2.0.mine files or likely whatsoever, even though many recommend editing those files. I feel kinda lost after trying to figure out how to fix this problem for nearly 4 days straight. Please help

Thanks In advance

Chris

---

### Post by Chris_666 on 2008-02-23
Oh, I fixed the problem myself.

go make a file in your homedir

```
 

cd /home/<name</
sudo vim 

#In vim (or any other editor) write following:

Xft.dpi: 90 #you may wanna change the actual dpi, for which suits you the best(obviously) 

#save the file and call it .Xresources 


```

Now go restart your fluxbox and be happy :) - at least this worked for me.

---

### Post by RedSquirrel on 2008-02-23
No need to use sudo in your home directory.

```
vim .Xresources
```

is sufficient. ;)

---

### Post by kerry_s on 2008-02-23
or you could have just adjusted the font size.
[http://fluxbox.sourceforge.net/docs/en/faq-dev.php](http://fluxbox.sourceforge.net/docs/en/faq-dev.php)

create a .gtkrc-2.0

**gtk-font-name = "sans 12"**

change font name and size as needed.

also like RedSquirrel said, do not use root in your home folder, your going to corrupt it, and lock yourself out.

---

