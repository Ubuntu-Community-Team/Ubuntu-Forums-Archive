---
title: "Open Nautilus with SUDO abilities via script"
date: 2013-12-04
forum: General Help
---

### Post by adam17 on 2013-12-04
Hi,

I have been playing with a few scripts and want to make one to open nautilus as root when executed.

So far I have used the code:

echo mypassword | sudo | nautilus /

this opens nautilus in the specified directory but doesnt give sudo premissions. 

yet in the terminal sudo nautilus / and entering the password will allow permission.

I know it is not advisable to use this method however I would still like to know how it is done, if at all possible.

Adam

---

### Post by Lars Noodén on 2013-12-04
You probably would do something like this:

```

gksu /usr/bin/nautilus

```

But you might want to close it as soon as you are done so that you don't forget that it is running as root.  Otherwise, things can get messy.

---

### Post by adam17 on 2013-12-04
Hi, 

Thanks for the quick response.

This seems to still ask for the password.

I would like to be able to execute the .sh file and have it open Nautilus without requesting the root password.

Thanks.

---

### Post by Lars Noodén on 2013-12-04
Well to customize sudo, you have to edit [sudoers](http://manpages.ubuntu.com/manpages/saucy/en/man5/sudoers.5.html).

```

%adam17  ALL=(ALL:ALL) /usr/bin/nautilus

```

There's one more thing to change in that line but I'll leave you to figure that out.

---

### Post by Isamu715 on 2013-12-04
Remember to edit *sudoers* with visudo instead of a regular text editor, it will check for errors after you finish editing, preventing you from rendering *sudo* useless on your system. If you don't want to use vi, you can pass any editor to *visudo* via the EDITOR variable, for ex. to use *nano*:
```
EDITOR=nano visudo
```

---

### Post by Slim Odds on 2013-12-04
> **Isamu715 said:**
> Remember to edit *sudoers* with visudo instead of a regular text editor, it will check for errors after you finish editing, preventing you from rendering *sudo* useless on your system. If you don't want to use vi, you can pass any editor to *visudo* via the EDITOR variable, for ex. to use *nano*:
```
EDITOR=nano visudo
```
Don't put "visudo" in your EDITOR variable, just the name of the editor. visudo uses EDITOR to select your desired editor.

---

### Post by Lars Noodén on 2013-12-04
> **Slim Odds said:**
> Don't put "visudo" in your EDITOR variable, just the name of the editor. visudo uses EDITOR to select your desired editor.

That's what that line does.  When an environment variable precedes a program name, that variable is local to that program session.  So in the example above EDITOR is set to nano just that once only for that particular session with visudo.

Anyway, +1 to using visudo, it prevents syntax errors that could cause you to get locked out.  Just be careful with long lines in nano so they don't get wrapped.

---

### Post by Slim Odds on 2013-12-05
> **Lars Noodén said:**
> That's what that line does.  When an environment variable precedes a program name, that variable is local to that program session.  So in the example above EDITOR is set to nano just that once only for that particular session with visudo.

Anyway, +1 to using visudo, it prevents syntax errors that could cause you to get locked out.  Just be careful with long lines in nano so they don't get wrapped.
The EDITOR variable is used by many, many programs and they will all run: "nano visudo" + their arguments (usually another file name to edit) instead of just "nano" + their own arguments. You do NOT want visudo in the EDITOR variable.

Maybe you're thinking of: ```
EDITOR=nano**[SIZE=3];[/SIZE]** visudo
```

---

### Post by Lars Noodén on 2013-12-06
> **Slim Odds said:**
> You do NOT want visudo in the EDITOR variable.

Of course not, that's why EDITOR is prepended to the line launching visudo, not on a separate line or separated by a semicolon, so that EDITOR remains unchanged, except for that single instance of visudo.  I'm not finding a good web page explaining that, but it's widely used when compiling.  Try this:

```

EE=foo
echo ${EE}
EE=bar less ~/.profile
echo ${EE}
less ~/.profile
echo ${EE}

```

While in less both times check EE by entering ***!**echo ${EE}*.  You'll see that in the first instance, it is set to "bar" and for everything else, it remains "foo"

---

