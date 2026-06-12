---
title: "Files ending in &quot;~&quot; in home dir"
date: 2007-11-27
forum: General Help
---

### Post by HUNTtheHIPPO on 2007-11-27
I have a lot of files ending in a "~" after the extension in the home folder. What exactly are they? They appear to be files that auto-saved themselves. And is there a way to easily clean them all up?

---

### Post by niteshifter on 2007-11-27
That is exactly what they are: auto-save / backup copies of files. To clean them up - safely:

The instructions below assume you are in a Terminal, in your home directory - that is, the prompt ends with ~$.

First list them:
```
ls -l *~
```

If there's a large number of them use this:
```
ls -l *~ | less
```

(That's a lower-case L after the dash)

If you sure there's nothing in the list you wish to keep, let me repeat that: YOU ARE SURE (they will be gone for good after this, recovery is extremely difficult) then do this:

MAKE SURE YOU TYPE BOTH THE ASTERISK AND THE TILDE!
```
rm *~
```

Now if that last step makes you nervous you could do this before removing (rm) them:

```
mkdir to_be_deleted
mv *~ ~/to_be_deleted
```

Then, once you are satified that everything is ok, use the the command line way:
```
cd to_be_deleted
rm *~

```

Or use the GUI file browser (nautilus in GNOME, for example) and navigate to the to_be_deleted folder and whack them with the mouse (Ctrl+A will select all).

It's a very bad habit to get into of using rm without checking what rm is going to do! Always list 'em first, review, them rm !!!!

---

### Post by K.Mandla on 2007-11-27
And if I remember right, gedit is set by default to create those files whenever it saves. So you might check that and other programs to see if you can turn that off, if you don't like those files reappearing over time. (I know Bluefish does that too; I'm sure there are others with the same behavior -- some can be told not to do that. ;) )

---

### Post by LaRoza on 2007-11-27
Vim does it also.

---

### Post by mali2297 on 2007-11-27
.. as does Emacs. :-)

---

### Post by HUNTtheHIPPO on 2007-11-27
That helps, thanks.

---

### Post by Onyros on 2007-11-27
And Geany, too.

I hate that default behaviour.

---

