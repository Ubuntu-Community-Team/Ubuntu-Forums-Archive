---
title: "ssh: program must continue running when I close terminal"
date: 2008-05-08
forum: General Help
---

### Post by seventyeights on 2008-05-08
I need to ssh in, start an app (eg motion), and then close the terminal. I need programs to keep running after I disconnect. Right now, apps seem to either break or just shut down.

Any way to do this? Thanks.

---

### Post by scxtt on 2008-05-08
ssh_shell_prompt:# nohup motion &

you'll get the PID of the motion process back and it'll keep running when you end your session.

---

### Post by inportb on 2008-05-08
Also try screen. It's an awesome little app... like a window manager for terminal sessions.

> **scxtt said:**
> ssh_shell_prompt:# motion &

Somehow, I'm not sure how well that works. My apps seem to be terminated when I get out.
Maybe: (and I haven't tried this yet)

# nohup motion &

---

### Post by seventyeights on 2008-05-08
I have never heard of this command before. Already works perfect.

I upped your tally:
[You have been thanked 13 times in 13 posts]

:)

---

### Post by Kokopelli on 2008-05-08
yes a shell program would terminate.  doing "motion &" just pushes it to the background. nohup should work though

There are a couple of possible solutions to this but my favorite is to use screen.

```
screen -Amd <command>
```

The benefit of this versus nohup is you can always reattach the screen in a new ssh session if you want to see how it is doing.

---

### Post by scxtt on 2008-05-08
> **seventyeights said:**
> I have never heard of this command before. Already works perfect.

I upped your tally:
[You have been thanked 13 times in 13 posts]

:)thanks :)

i did forget the **nohup** initially, and that's how inportb caught it in a quote (but i don't have an edit time on the post) ... i use nohup on a few occasions on older HP/Sun hosts that don't have screen installed ... but when screen is available, i'm all about it :)
> 15 Sockets in ~/.screen.
:-D

---

### Post by qpieus on 2008-05-08
+1 for screen - it's fantastic.

Install screen on remote machine. After you ssh in, type screen. You'll get a welcome message, then you'll be back at a prompt. From there type your command to start whatever app you want. Once it's running, press Ctrl-a (control and a at the same time), then press d. Those keystrokes does what's called detaching the screen session. After detaching, you'll be back at a prompt. From there you can logout. The app you started in the screen session keeps on running.

To re-attach to your screen session: ssh in, then at a terminal prompt type ```
screen -r
```

This was a really simple example of how to use screen. Screen can do way more, like have multiple apps running in multiple sessions. You can even tweak the .screenrc config file to do all links of crazy stuff like make tabs for your different apps running in multiple screens. Way cool. There's many good screen tutorials on the web.

---

### Post by FuturePilot on 2008-05-08
Yes screen is your friend with SSH :D

---

### Post by seventyeights on 2008-05-08
One day, I set up four headless cd rippers controlled from my desktop, which was also ripping. When I got up to about 100 cds, I found I had to change out a cdrom. After I let that machine use up its encoding cue, I then proceeded to do a sudo shutdown *in the wrong terminal*!  My main screens very obediently blanked and there was a sudden silence.

Yes, hours of maniacal disk swapping did not have to be lost in vain!

end of story

Anyway, thanks for all the help. SSH & friends just gets better as I learn more about it.

As far as Motion goes, I just found the command [daemon on] to put in the motion.conf and it does exactly what I wanted, it releases the terminal. I must have passed over it in the man 10 times and not realized what it was. I'm just mentioning it now for future users of ssh and motion.

btw, in the given example, you say "nohup motion &", what is the & for? It worked for me without it.

---

### Post by FuturePilot on 2008-05-08
When you put & at the end of a command all it does it background the process so that you can still use the terminal. Otherwise you won't get a prompt back until that command that you entered before terminates. But the command will still work without &.

---

