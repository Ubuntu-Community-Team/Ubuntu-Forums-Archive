---
title: "help with setting perminant alias commands"
date: 2008-05-06
forum: General Help
---

### Post by bendoggy on 2008-05-06
I've tried adding to my .bashrc, .profile, and even tried making a .bash_aliases program. I relatively new to linux. A week or so fresh and am using the new Hardy Heron.

Every time, I add something to the .bashrc and reboot. I doesn't set it. It reads, bash: *alias*: command not found

Any suggestions?:confused:
Any help would be appreciated. :)

---

### Post by kerry_s on 2008-05-06
what are you putting exactly?

they go in ~/.bashrc

you don't have to reboot. they take effect immediately.

here's what mine looks like.

---

### Post by jerrallan on 2008-05-18
Ben Doggy is right.  The alias disappears after reboot. Ubuntu here.

---

### Post by jerrallan on 2008-05-18
Ben Doggy is right.  The alias disappears after reboot. Ubuntu here.

```
$ alias bak='cp file1 file2'
```

---

### Post by p_quarles on 2008-05-18
> **jerrallan said:**
> Ben Doggy is right.  The alias disappears after reboot. Ubuntu here.

```
$ alias bak='cp file1 file2'
```
Running "alias" from the shell will only set an alias for the current session. To make it permanent, you need to set it in the shell's rc file. So, you would edit ~/.bashrc and add a line that reads just like the example command in your post. That way it will be set whenever you load the shell.

---

### Post by jerrallan on 2008-05-26
> **p_quarles said:**
> Running "alias" from the shell will only set an alias for the current session. To make it permanent, you need to set it in the shell's rc file. So, you would edit ~/.bashrc and add a line that reads just like the example command in your post. That way it will be set whenever you load the shell.

You are correct!. Just discovered that.  And if they are put in ~/.bashrc, they should "stick"

---

### Post by cdtech on 2008-05-26
My bash aliases are in my ~/.bash_aliases file

I had to comment out:
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

within the .bashrc file. This makes it much easier to manage long list of aliases

---

