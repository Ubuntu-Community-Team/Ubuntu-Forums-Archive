---
title: "Gnome Terminal Starts in /opt/... Instead of ~"
date: 2008-07-02
forum: General Help
---

### Post by GenuineXP on 2008-07-02
I don't know how I managed this, but whenever I start a terminal it opens in the /opt/sauerbraten directory and not my home directory. I've searched for the string "sauer" in ~/.bashrc, ~/.profile, and /etc/.bash.bashrc, and none of those files contain that string (i.e., none of them appear to set the initial directory to /opt/sauerbraten).

I tried searching for a .Xdefaults file and there isn't one on my system (I read it may be in there... possibly).

Any idea how this happened or how to fix it? I'm planning on removing that directory since packages are available for the latest Sauerbraten now. I dunno what'll happen if it's gone and I start a terminal!

Thanks.

---

### Post by iaculallad on 2008-07-02
On your terminal: What does the command below displays?

```
env|grep HOME
```

---

### Post by GenuineXP on 2008-07-02
Whoops, forgot to mention that I tried that already too. It gives me HOME=/home/sean, as it should. That was one of the first things I thought got screwed up (environment variables, I mean).

Weird...

---

### Post by iaculallad on 2008-07-02
Can you see your home directory when using the command below on your terminal:

```
grep sean /etc/passwd
```

---

### Post by GenuineXP on 2008-07-02
Yep, I did that too. :-P

It's /home/sean, as it should be.

---

### Post by iaculallad on 2008-07-02
Huh... I can't even see an option on how to change it to default to point to user's Home directory in the **gconf-editor** tool.

---

### Post by GenuineXP on 2008-07-02
I should mention that using nautilus-terminal to open the terminal from my desktop (i.e., right-click on my desktop and select "Open Terminal") the terminal opens in my home directory like it should.

---

### Post by GenuineXP on 2008-07-03
This is strange and annoying. Bump.

---

### Post by GenuineXP on 2008-07-03
Stranger still... it's not happening anymore! I don't get it...

As long as it doesn't happen again, I guess there's no problem.

---

