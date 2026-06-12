---
title: "My brief encouter with Ubuntu"
date: 2008-03-12
forum: General Help
---

### Post by pebblehead on 2008-03-12
I miss the good ol' XP but there is no WAY i'm using vi-****-sta. After a few minutes it became apparent to me i need to go back to my anger management classes:
[http://img507.imageshack.us/my.php?image=screenshot1xz0.png](http://img507.imageshack.us/my.php?image=screenshot1xz0.png)

Current BP: 180/140.

Please help before I get a stroke

---

### Post by zxscooby on 2008-03-12
no problem just follow this guide 
[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?highlight=%2864%29%7C%28flash%29%7C%28bit%29](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?highlight=%2864%29%7C%28flash%29%7C%28bit%29)

or use konqueror.

---

### Post by sloggerkhan on 2008-03-12
well, to begin with,

cd /home/<username>
cd ~
would have been valid to get you to your home folder.
cd home only works if you're in a directory that has a home subdirectory.
you could do cd $home, though.

---

### Post by pebblehead on 2008-03-12
yes i know i sound like a mentally challenged 5 year old.....but how do i find firefox? The search bar apparently doesn't function. I looked in lib, usr, etc... but i still can't find it.

---

### Post by zxscooby on 2008-03-12
lol all i saw was the unsupported architecture part.

maby you should check out the community documentation on using the terminal
i think you have to be SU to use the F#&@ing dumbSh#@& command.

---

### Post by zxscooby on 2008-03-12
the article i linked too had a link to download the 32bit version of firefox 
it should be saved to your home folder./ home/(your username)

---

### Post by pebblehead on 2008-03-12
Allright, thanks man. I think i'll do it tomorrow though, it's 5am here lol.

---

### Post by Arthur Archnix on 2008-03-12
Try asking questions instead of posting pictures of you throwing a tantrum. And remove that pic; you seem to know you can't type that here, but posting a pic of you typing it is hardly better.

Everything you're trying to do is case sensitive. In Ubuntu, Desktop means one thing, and desktop means something completely different. 

The forums are often good at providing quick answers, but if you need immediate help, or feel like "talking" about it, head over to #ubuntu on irc:

Fire up pidgin, add an irc account, choose a name, then when the freenode screen pops up saying you're connected type
```
/join #ubuntu
```Lastly, it looks like, among other things, you're trying to install adobe flash player for an x86-64 bit system. Try this: Open a terminal (>menu >accessories >terminal) and copy and paste this in there:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by sloggerkhan on 2008-03-12
ps: you open programs either from the applications menu or by typing their name. You install them from synaptic package manager in the system > admin dialog.

---

