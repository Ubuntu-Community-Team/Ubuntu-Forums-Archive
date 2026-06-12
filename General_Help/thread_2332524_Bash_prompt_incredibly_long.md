---
title: "Bash prompt incredibly long"
date: 2016-08-01
forum: General Help
---

### Post by verymadpip on 2016-08-01
Hi everybody.
This morning I did a fresh install of 16.04.1 64 bit on my rig.
when I open a terminal my bash prompt is HUUUUUUUUUUUUUGE.
Something along the lines of:
pip@pip-system-product-name-with-more-stuff-about-16-characters-shortened-to-11-to-fix

This is not exactly accurate as I'm not at home at the moment, but you get the idea.
My question is, how do I shorten that, or is it going to be easier to just do another clean install?

It doesn't appear to be causing an issue, it's just REALLY annoying me :-)

---

### Post by 1clue on 2016-08-01
You want to mess with the PS1 environment variable.  Mine is this:

```

if [ "`id -u`" = "0" ]; then
        PS1='\[\033[01;05m\]\u\[\033[00m\]\[\033[01;31m\]@\h\[\033[01;34m\] $PWD
\$\[\033[00m\] '
elif [ "$LOGNAME" = "$USER" ]; then
        PS1='\[\033[01;32m\]\u\[\033[01;31m\]@\h\[\033[01;34m\] $PWD
\$\[\033[00m\] '
else
        PS1='\[\033[01;35m\]\u\[\033[01;31m\]@\h\[\033[01;34m\] $PWD
%\[\033[00m\] '
fi

```

It shows you how to put it on more than one line.  If you can't read code it has different prompts based on whether you're root, or logged in normally or as sudo user.  The primary difference between them is the color.  The escaped brackets and numbers are color codes.

It shows up as 
```

user@hostname/current/working/directory
$ 

```

---

### Post by 1clue on 2016-08-01
When you type the command, you're typing after the $.  So it doesn't matter how long the stuff on the top is.

---

### Post by banceu_sergiu_ione on 2016-08-01
Hi

You may want to have a look at your device name under system settings / details. The start line it goes with 'user name'@'device name':~$

---

### Post by verymadpip on 2016-08-01
Hi everybody.
Thanks for the info.

I might mess with the PS1 variable later.
It isn't doing any harm, just irritating me.

I'm gonna mark this as solved.
Thanks for the help guys.

---

### Post by 1clue on 2016-08-01
Just as a hint, play with PS1 on the command line not in your .bashrc. That way if you mess it up (you will) you can just close the terminal and open it again, and it's your last good place.

If you mess it up in the file, then you can't open another terminal until you fix it.

By messing it up, I mean making code that does not run.  Like a misplaced quote, or something like that.

---

### Post by verymadpip on 2016-08-01
1clue - 
Thanks for the tip.
I fully expect to mess this up when/if I try it.

---

### Post by btindie on 2016-08-01
If you type "cat /etc/hostname" does it show the same string?

As if so, it's because it's using the hostname in the bash prompt and during the installation process it came up with a really long default hostname.

See [http://www.cyberciti.biz/faq/ubuntu-change-hostname-command/](http://www.cyberciti.biz/faq/ubuntu-change-hostname-command/) for how to change it.

---

