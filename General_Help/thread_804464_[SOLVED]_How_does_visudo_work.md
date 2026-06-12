---
title: "[SOLVED] How does visudo work?"
date: 2008-05-23
forum: General Help
---

### Post by angry_johnnie on 2008-05-23
I have edited /etc/sudoers in the past, using nano.
However, the first line in the file says it **must** be edited with visudo.
I would, but then, I don't really understand visudo.
I tried man visudo, but that didn't help much.
Even gvim is easier than that... at least it has buttons and menus! :-)

I would just like to know what visudo is using to edit /etc/sudoers.  It kinda feels like vi (and even the name suggests vi).

I'm no good with vi or vim either, but I do know files are edited with **:e**, and **:wq** is used to save and exit.

Is that how it works with visudo?

Or should I just stick to nano?

Does it even matter which editor I use?
After all, it says it MUST be edited with visudo...

---

### Post by kerry_s on 2008-05-23
visudo will use the editor you set as default, so for instance you can set yours to nano:

sudo dpkg-reconfigure --config editor

then when you> sudo visudo
it will open in nano

if you want to configure all your alternatives->
sudo dpkg-reconfigure --all

---

### Post by bingoUV on 2008-05-23
visudo is not exactly an editor. It spawns an editor, and checks the saved files for correctness. 

Justification : An incorrect sudoers file can be very painful, especially in Ubuntu, as you may not be able to edit it again. This is because you need to be root to edit it, and incorrect sudoers file will not let you gain root privileges. In most other distros, you can use root password(by default) to gain root privileges and repair your damaged sudoers file. It is tougher than that in Ubuntu.

You can change which editor visudo spawns.
```

export EDITOR=nano
sudo visudo

```

This will open nano editor with visudo.

---

### Post by ibuclaw on 2008-05-23
> **bingoUV said:**
> 
You can change which editor visudo spawns.
```

export EDITOR=nano
sudo visudo

```

This will open nano editor with visudo.

Wrong!

It's
```
sudo **-E** visudo
```

And personally, I keep the information stored in my .bashrc file
```

gedit ~/.bashrc

```
Then type at the bottom:
[PHP]
export EDITOR=nano
alias visudo='sudo -E visudo'
[/PHP]
And then just type in "visudo" to start it up.

Regards
Iain

---

### Post by bingoUV on 2008-05-23
Sorry, it could be some Ubuntu peculiarity. My RHEL 4 system's sudo does not even have -E option. And sudo visudo is working quite happily.

Can you tell what is different? What does Ubuntu's sudo's -E option do?

thanks

---

### Post by angry_johnnie on 2008-05-23
Thanks, all of you. :-)
I'll go set nano as default now (mine was, indeed, using vim).
I just downloaded a huge PDF about vim.  I hope I can make some sense of it.  I feel a lot more comfortable with nano, but it never hurts to know a little more.

Cheers!

---

### Post by ibuclaw on 2008-05-23
[QUOTE=bingoUV]What does Ubuntu's sudo's -E option do?[/QUOTE]
The -E option in Ubuntu keeps the users environment settings when the terminal switches to root.

---

