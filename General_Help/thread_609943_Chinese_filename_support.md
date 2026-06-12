---
title: "Chinese filename support"
date: 2007-11-11
forum: General Help
---

### Post by jumbo_cards on 2007-11-11
Hey Guys,

I'm new to ubuntu~
I can currently view chinese sites fine with firefox.  However I can't view filenames on my hard disk with chinese in them.
they show up as ????

How do I solve this?  Any help would be appreciated!

---

### Post by jumbo_cards on 2007-11-11
anyone have any ideas?

---

### Post by scrooge_74 on 2007-11-11
You have to install locales for other languages, plus you can use scim yo write in chinese

you will need to install the chinese fonts also

sudo apt-get install scim scim-chinese scim-tables-zh scim-config-socket scim-frontend-socket scim-gtk2-immodule

sudo dpkg-reconfigure locales

---

### Post by jumbo_cards on 2007-11-12
I do have the Chinese locales installed...


sudo apt-get install scim scim-chinese scim-tables-zh scim-config-socket scim-frontend-socket scim-gtk2-immodule

tells me that everything is up-to-date and does nothing.

sudo dpkg-reconfigure locales

also says that my chinese fonts are up-to-date
  zh_CN.UTF-8... up-to-date
  zh_HK.UTF-8... up-to-date
  zh_SG.UTF-8... up-to-date
  zh_TW.UTF-8... up-to-date

I've tried to SCIM to input Chinese, but can't seem to get it working.  The shortcut mapping for the "next input" (ctrl-alt-up) does not work.  (ctrl-alt-right) which suppose to bring up the input menu only takes me to the next desktop >.>''

Plus I still can't view chinese characters in filenames and still shows ????.txt as an example.

I have no experience whatsoever with ubuntu nor scim.  Please bear with me, I do want to use ubuntu on my notebook... but if I can't fix this chinese support issue, I don't know whether ubuntu would be a good choice of OS for me =(

your help is appreciated...

---

### Post by scrooge_74 on 2007-11-12
Ok, for writting with scim it works with text editor (dont remember the name I use notepad), first from a terminal type scim -d then open the text editor, right click and then pick input method scim, worst case you have to pick which character set.  That should be it.

As for seeing the characters in a terminal or it is in gnome? If in Gnome you have to add the language support is under Admin>System>Language support (I think i am using Xfce4 so I dont quite remember all I did)

After adding the locales I can see chinese characters in a terminal so I am not sure what I missed telling you.

---

### Post by jumbo_cards on 2007-11-12
scim -d
and the output is:
```
Smart Common Input Method 1.4.7

Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
Failed to launch SCIM.

```

For the language support under admin, I do have chinese option checked...

---

### Post by scrooge_74 on 2007-11-12
I had the same problem the other day.  Do you have Scim open before you went into a terminal? Was the icon already in the  top bar?

You can also launch scim by just typing scim, if you close the terminal it shuts down

---

### Post by jumbo_cards on 2007-11-13
what icon am I suppose to see?

I don't see any icons what-so-ever regarding scim on any of the task bars.

---

### Post by scrooge_74 on 2007-11-13
When scim is working a little keyboard icon appears on the top bar on the right.

---

### Post by jumbo_cards on 2007-11-13
yes, I have that icon on the top right position

typing just "scim" gives me the same error

---

### Post by scrooge_74 on 2007-11-13
close the keyboard on top first

then type scim in a terminal

---

