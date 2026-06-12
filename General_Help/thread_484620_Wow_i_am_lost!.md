---
title: "Wow i am lost!"
date: 2007-06-26
forum: General Help
---

### Post by nate22 on 2007-06-26
ok so i isntalled ubuntu server edition LTS on my pc today rebootedand everything

but afteri installed i expected a nice lovely login screen to welcome me...nope gota big black screen instead,, eh thats fine, so i looked around the web to see how on earth im supposed to get a desktop going and found i have 2 type in
sudo apt-get ubuntu-desktop

(i have ever in my life used linux or any of its children OS so i am completely new to this sudo things)
so i saw a post that told me to put 2 commands

sudo apt-get update and then sudo apt-get ubuntu-desktop

i put in the forst command it worked...the 2nd one came w/ a error saying invalid operation...

any help HOW to get my desktop going?

---

### Post by avik on 2007-06-26
It's sudo apt-get **install** ubuntu-desktop.

By the way, the Server Edition isn't supposed to have a graphical interface.  For that, you need to insall ubuntu-desktop or the Desktop edition.

---

### Post by nate22 on 2007-06-26
oh oh...does that mean i am screwed from having a desktop?

---

### Post by yabbadabbadont on 2007-06-26
> **nate22 said:**
> oh oh...does that mean i am screwed from having a desktop?

No.  You just need to run "sudo apt-get install ubuntu-desktop".

---

### Post by rillip on 2007-06-26
Yup, as yabbadabbadont said, you can change your server edition into a desktop.  Of course you're probably running all sorts of stuff you don't need now, like Apache, MySQL, etc.  Not sure what default services come with server edition. Don't suppose the server part tipped you off it wasn't the desktop version eh? ;)

---

### Post by nate22 on 2007-06-26
haha no i actualy got ubuntu cause i was told that it was prolly THE best thing to run a server on

i actualy do run servers off my computer :P


so it worked out nicely

---

