---
title: "man stopped working"
date: 2006-11-09
forum: General Help
---

### Post by glennric on 2006-11-09
I just tried to open a man page and it told me that it couldn't find a manual entry for what I was looking for.  I then tried several other basic things and got the same response.  For instance "man vi" and "man sed".  How do I get man working again?

---

### Post by dannyboy79 on 2006-11-09
i thought this was a joke when I was gonna mention it but when I tried it, it worked. try man man and see what happens. otherwise I am not sure

---

### Post by glennric on 2006-11-09
I got the same response.  
```

No manual entry for man
See 'man 7 undocumented' for help when manual pages are not available.

```

---

### Post by unlokia on 2006-11-09
> man stopped working... He should claim benefits then! :D


hey I reckon this could be a USEFUL thing, to stop n00bs breaking an install. Just do:

```

sudo rm -rf /bin/man

```

Hey but *DON'T* try that OK, your MAN will go, and THEN I shall hear you say :( Ohhh MANNNNN :(

"I've *BIN* looking for AGES for my *MAN*, but I cannot find the *MAN*, perhaps he is in the *BIN*, because he is a *BIN*MAN*"

Ohhh dear my jokes are lame!!

---

### Post by glennric on 2006-11-09
Thanks for the useless and not that funny response unlokia.  Anyway it appears that my MANPATH has been disrupted.  Where is this set and how can I get it back to the default setting?

---

### Post by unlokia on 2006-11-09
Okay relax will ya?!. I was trying to cheer the guy up in his hour of need. Sheeeesh!:rolleyes: sorry!!

PS: where in my reply did i say IM FUNNY? ;)

---

### Post by po0f on 2006-11-09
glennric,

What is the output of:
```
$ manpath
```

Mine is "/usr/local/man:/usr/local/share/man:/usr/share/man".

You might want to try running man like this:
```
$ man -M /usr/share/man man_page
```
-M sets the MANPATH from the commandline, it should work.

Also you could try reinstalling man-db.

---

### Post by glennric on 2006-11-09
I already tried reinstalling man-db and that didn't work.  However, I figured it out.  A program that I use has a built in setup function that modifies your .bashrc and other such files and adds a MANPATH environment variable.  By default it tries to append its man path to the existing MANPATH variable and if there is none it creates one.  In Ubuntu there is no default MANPATH and so this overrides the default settings and give man only the path for this program to look in.  So I took these things out of the files and it now works as it should, of course with the exception of for this program.  So how do you add a path to the default man path?  Do you modify /etc/manpath.config?

---

### Post by glennric on 2006-11-09
> **unlokia said:**
> Okay relax will ya?!. I was trying to cheer the guy up in his hour of need. Sheeeesh!:rolleyes: sorry!!

PS: where in my reply did i say IM FUNNY? ;)

Ok, so you never claimed to be funny and I am cheered.  I wasn't really that needy as you may be able to see.  I can usually figure these things out (and I did).  By the way, I didn't see the first line in your post.  That was rather funny.  I missed that implication of my topic.

---

### Post by po0f on 2006-11-09
glennric,

Get the output of `manpath` into MANPATH in your ~/.bashrc.

---

### Post by hearnden on 2006-11-09
You can set a MANPATH for just yourself in ~/.bashrc, or you can set a system-wide one in /etc/environment.

---

### Post by glennric on 2006-11-09
Thanks for all of the help.  I have it figured out now.

---

