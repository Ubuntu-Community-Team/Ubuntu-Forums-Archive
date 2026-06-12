---
title: "send running terminal to ssh"
date: 2013-04-19
forum: General Help
---

### Post by mErchamion on 2013-04-19
Hi everybody! I am wandering if it is possible to get a running terminal window be sent over ssh to a remote display. To visualize it, suppose You have something running at the office's box (eg compressing huge files) and you want to follow the outputs from your spot at a meeting, class, whatever. I can connect via ssh to the office, and I want to 'transfer' the window into my remote display. I dont know if this is even possible. I know I can do some stuff redirecting the outputs, but I guess that if windows can be transfered this way, the method can be applied to any running window. I know I could do it via remote desktop apps, but that is not what I am looking for.

Hope I have been clear enough. Thanks in advance for your help and patience!

---

### Post by zero2xiii on 2013-04-19
Hay,

Yes it is very possible.

Simply install and use "screen"

```
sudo apt-get install screen
```

man screen for more details. It is accessible over SSH aswell (in a LAN I know, I use it over a LAN almost daily)

Cheers

---

### Post by sandyd on 2013-04-19
send the output to a file 
i.e.
```

apt-get install nano  &>/tmp/log

```
Then on the second computer
```

tail -f /tmp/log
```

---

### Post by Lars Noodén on 2013-04-19
You can use screen or tmux to have two (or more) sessions looking at the same activity.  Be sure to read up on which ever one you choose.  screen in particular is enormously flexible and you might find something interesting in the writeups or manual pages if you are not overwhelmed by all the options. 

The quickstart for [screen](http://manpages.ubuntu.com/manpages/quantal/en/man1/screen.1.html) is easy:

1. On the first machine log in, start screen and then run your process.  Leave it running. 

2. Then on the second machine, ssh into the first machine (as the same user) and then run **screen -x** to attach to the existing screen session.   To leave that screen session without disrupting it on the first machine, use **ctrl-a d**.  All screen commands start with **ctrl-a**

Try it a few times with a dummy process, like the while loop below, to get familiar with attaching and leaving sessions.

```

while sleep 1; do date; done

```

You can do the same with [tmux](http://manpages.ubuntu.com/manpages/quantal/en/man1/tmux.1.html).

1. On the first machine log in, start tmux and then run your process.  Leave it running. 

2. Then on the second machine, ssh into the first machine (as the same user) and then run **tmux a** to attach to the existing tmux session.   To leave that tmux session without disrupting it on the first machine, use **ctrl-b d**.  All tmux commands start with **ctrl-b**

screen is more established and common but much more flexible and therefore very complex.  tmux is newer, thus not so common, and much simpler.

---

### Post by markbl on 2013-04-19
Tmux essentially supersedes screen. If you are learning something new you may as well start with tmux. I have used screen frequently for 20 years but I use tmux wherever I can nowadays.

---

### Post by Lars Noodén on 2013-04-21
> **markbl said:**
> Tmux essentially supersedes screen. If you are learning something new you may as well start with tmux. I have used screen frequently for 20 years but I use tmux wherever I can nowadays.

+1 for tmux

I've used screen on and off for a long while too but went over to tmux a few years ago.  It's about all I use now and I find it much more straight forward than screen.   I think there are quite a few things that you can do with screen than with tmux, but I also think they are quite uncommon.  About the only situation I've personally run across is when sharing a session between two or more different users and one of them should be read-only.   Basic [sharing between different accounts can be done with tmux](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Remote_Processes#tmux.281.29) but read-only is not really an option.

---

### Post by mErchamion on 2013-04-26
Hi everybody! thanks for your replays. tmux does the trick smoothly, though it requires to be launched before the task in question is launched (screen as well). Actually, tmux seems to be much more powerfull than what I am exploiting now, because it keeps running in the backgrund, so you can login via ssh, start update-upgrade , logout  , close the terminal and then check the progress via ssh. I wonder about security issues in this, but i think that it is ok for me.

Thank you all!

---

### Post by Lars Noodén on 2013-04-26
Cool isn't it?

> **mErchamion said:**
> ...I wonder about security issues in this...

If you are running only one script or program and want the session to exit after completion, you can launch it like this:

```

tmux new-session -n myscript "/some/path/to/script"

```

Then when the script ends, the session ends.

Or if you are running with escalated privileges inside tmux you can use sudo to launch the script.  Then after 15 minutes (if you haven't changed the default) the password will be needed again, unless you clear it with 'sudo -k' first.

---

