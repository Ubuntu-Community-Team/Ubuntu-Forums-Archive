---
title: "Adding programmes to general start-up"
date: 2007-06-15
forum: General Help
---

### Post by Cilionelle on 2007-06-15
How do I add a programme (the 845patch for my Dell Inspiron) to the after-GRUB/before-X sequence?  I would like to run it so that the video RAM is ready to load a 1024x768 screen...

---

### Post by straps on 2007-06-15
Make a service for yourself

**sudo cp -a /etc/init.d/skeleton /etc/init.d/inspironpatch**

edit the new file **/etc/init.d/inspironpath**

put your code in the **do_start** function

put some dummy code in the **do_stop** and **do_reload** functions, **don't leave them blank** (ex: echo "inspiron stop called")

make it starts before gdm with:
**sudo update-rc.d inspironpatch defaults 10**

It shold work, Bye

---

### Post by Cilionelle on 2007-06-15
Um...

"With those words, Cilionelle found himself underwater, struggling to breathe as he floundered in those new concepts.  'What code?' he gargled, desperately. 'I don't understand!'  Then, the darkness enfolded him - "

No!  Will not succumb... **How** do I do this?  Can I have some more information, pls?

---

### Post by Cilionelle on 2007-06-15
Bump!

---

### Post by weblordpepe on 2007-06-15
OK from the looks of things you have to create a file from a template, edit it to put in the code you want, and then set it to load on startup correctly.

> sudo cp -a /etc/init.d/skeleton /etc/init.d/inspironpatch creates the file **inspironpatch** from the skeleton file (the template).

Then you edit it by putting your code in the right place:
> put your code in the do_start function

put some dummy code in the do_stop and do_reload functions, don't leave them blank (ex: echo "inspiron stop called")


And you save it, but want to have it loaded correctly on bootup with:
> sudo update-rc.d inspironpatch defaults 10

---

### Post by weblordpepe on 2007-06-15
I tried looking at that skeleton file and its horrendously complicated. I give up! :P

---

### Post by reclusivemonkey on 2007-06-15
Just add whatever line you use to start the program to /etc/rc.local, i.e.

```

/usr/local/bin/845patch

```

---

### Post by Cilionelle on 2007-06-15
That's better!  I knew there must be a simpler solution... now to test it.  The command would be "845patch 65536" in my case, do I just insert that above "exit 0"?  Makes sense to have it so simple.  I was expecting something like the autoexec.bat file of yesteryear!

---

### Post by reclusivemonkey on 2007-06-15
> **Cilionelle said:**
> That's better!  I knew there must be a simpler solution... now to test it.  The command would be "845patch 65536" in my case, do I just insert that above "exit 0"?  Makes sense to have it so simple.  I was expecting something like the autoexec.bat file of yesteryear!

That's right, but just put the full path of wherever you have 845patch. If its in somewhere obvious (like /usr/local/bin) it should be ok though.

---

### Post by InfernalEternal on 2007-06-15
Excellent, it works a treat. :)

---

