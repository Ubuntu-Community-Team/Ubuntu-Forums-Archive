---
title: "Cron and screen"
date: 2013-06-08
forum: General Help
---

### Post by ras123 on 2013-06-08
```

# m h  dom mon dow   command 
00 **04** * * * screen -d -m rtorrent 
00 **16** * * * screen -r -X quit

```

Hi,
The above is a cron job with a screen, is it possible to detach and attach the screen with a session name in the above code? I need to start and quit multiple screens.
Thanking You,
Ras

---

### Post by Lars Noodén on 2013-06-08
You'll probably need to send an enter key stroke, too.  So maybe something like this would work.

```

00 16 * * * screen -r -X eval 'stuff quit\015'

```

If you use -S you can also name a session and target the named session.

---

### Post by ras123 on 2013-06-09
My code is working, but I would like to know how to detach and attach using a session name, I tried with -S option, but failed. So please let me know how to use -S option with some example.
Thanks
Ras

---

### Post by Lars Noodén on 2013-06-09
The **-S** can be used in conjunction with other options, all it does is label a session with a name so you can then reference that particular session by name.

Say in one terminal you start a screen session, just to confuse things, and do something like 'ls'.

```

screen
ls -l

```

Then in another terminal you start another session by name using **-S**

```

screen -S foobar

```

Then you can attach to the session you labelled 'foobar' above, using **-S** combined with **-x**

```

screen -S foobar -x

```

It's just a label.  It comes in handy when (if) you have more than one screen session.

---

### Post by Lars Noodén on 2013-06-09
You can also combine it with **-d** and **-RR** to attach to a session (and detach it if it is already attached) and create one if it does not exist.

```

screen -dRR

```

Or

```

screen -S someothername -dRR

```

For the full list of options peruse the manual page for [screen](http://manpages.ubuntu.com/manpages/raring/en/man1/screen.1.html).  There is too much there to take in at once but each time you skim through it, more becomes apparent.

---

