---
title: "Aterm/Eterm doesn't display “ or ” correctly"
date: 2006-12-06
forum: General Help
---

### Post by berserker on 2006-12-06
I recently installed aterm and eterm but notice that neither one displays &#8220; or &#8221; correctly.  The output is garbage.

Both display the "normal" quote:  " but not the "fancy" ones:  &#8220; &#8221;

Konsole displays them just fine.

I've tried changing fonts but nothing works.

Any ideas?

TIA!

UPDATE:  Couldn't figure it out so I installed urxvt (rxvt-unicode) which supports special characters.

---

### Post by soloslinger on 2007-03-04
I am having the same issue.  I am running a fairly fresh fluxbuntu install. The only terminal that displays the ' character correctly is xterm.  Aterm, Eterm and strangely putty from my windoze box all do not display the ' correctly.  I am wondering if perhaps it is the actual man page that causes this.  man aptitude has several examples of this.

soloslinger

---

### Post by carrellt on 2007-05-19
I just found the solution to this problem in an old post on the forum. Add the line
export LANG=en_US
to both your .bashrc and .profile. (Be sure to either re-start aterm/eterm, or 'source' both files to put the changes into effect

I wish that I understood exactly why this works, but I don't. I do know that it works when I do it on my system.

Good Luck.
Tom

---

### Post by berserker on 2007-05-19
> **carrellt said:**
> Add the line export LANG=en_US to both your .bashrc and .profile

Thanks for the tip.  That solved the special-character display problem in aterm but would generate the following error:

```
man passwd 
man: can't set the locale; make sure $LC_* and $LANG are correct 
Reformatting passwd(1), please wait...
```

So instead I put the following in ~/.bashrc and ~/.profile:

```
export LANG=C
```

The special characters are displayed correctly and I now get:

```
man passwd 
Reformatting passwd(1), please wait...
```

Don't know why it works. . .

---

### Post by carrellt on 2007-05-20
Huh. You're right. I only looked to see what my output of 'make' looked like (since that was where I saw the problem). But I had the same problem when trying to bring up a man page. I made the change that you suggested, and everything looks good. I'll have to look into this a little more to try and understand what we are doing. What I also wonder is why this issue hasn't really been addressed in the past. I have noticed this in the past few versions of Ubuntu (and also in Debian), but this is the first time I actually fixed it on my installation.

---

