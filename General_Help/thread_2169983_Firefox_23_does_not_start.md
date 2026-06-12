---
title: "Firefox 23 does not start"
date: 2013-08-24
forum: General Help
---

### Post by ukbeast on 2013-08-24
I am on ubuntu 13.04 and I get "Your Firefox profile cannot be loaded. It maybe missing or inaccessible.


Terminal gives me :
(process:23272): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed
Error: Access was denied while trying to open files in your profile directory.

---

### Post by Frogs Hair on 2013-08-24
You can create a new profile . Open the home folder select Ctrl +H to display hidden folders and delete the .mozilla folder. When you start FF a new profile folder will be created. The down side to this is that you will loose settings, bookmarks, and add-ons  if installed.

---

### Post by ukbeast on 2013-08-24
[I]I do did that before and I get the same error
[/I]

---

### Post by Erik1984 on 2013-08-24
How are the permissions on that folder?

```
ls -al ~ | grep mozilla
```

here it's 
```
drwx------  5 name name
```

---

### Post by Bx_Gilman on 2013-08-31
I have the same problem what i got after 
[COLOR=#000000][FONT=Ubuntu Mono]
ls -al ~ | grep mozilla 

is:
[/FONT][/COLOR]
drwx------  4 root root  4096 Aug 29 19:40 .mozilla

But how do you solve the problem. Btw where do you create a new profile with Ctrl+H in Firefox? but I cant open it.

Thanks for any help

---

### Post by Erik1984 on 2013-08-31
That is a bit weird, the owner should be you, not root on that folder.

This line should change it back to normal:
```
sudo chown -R yourname:yourname /home/yourname/.mozilla
```
of course substitute "yourname" with your username (the part before @ in the terminal).

Did you run Firefox as root sometime? If so then don't do that again :P

---

### Post by Bx_Gilman on 2013-08-31
Magic,

I typed in the line you gave me works. so thank you is in order. 

To the question "did I run Firefox as root"?- I have no idea if I did or not, but I'll be happy to learn how to check it out.  

I'm about to add a signature to my profile "Left the comfort world of Windows to the mystic world of Linux weird codes just so I can keep my old brain solving problems delaying the onset of Alzheimer" :-)

---

