---
title: "SSH closes my my apps when the session closes and I can't seem to run Telnetd"
date: 2013-12-08
forum: General Help
---

### Post by techrev on 2013-12-08
I'm really getting ready to go postal here.  I'm not finding answers to simple questions.  I can't do what I need to do with SSH, but, I can't run any other protocol - in spite of the fact that I am fully aware of the risks involved in running telnet and don't care.  So, tmux, screen, nohup and disown do NOT work anymore.  I cannot ssh over to my linux box, which is in the same room with me and on my local network and is firewalled from the internet, run an xwindows app displayed back through cygwin and then close the ssh session that spawned it leaving the window running on my windows box.  I've been able to do this for years, and it's how I do things.  I like it.  I don't want messy terminals cluttering up my taskbar.  So, some brilliant developers somewhere decided to change the way SSH functions for whatever reasons without thinking about all the ways that it may be used.  This isn't unusual, not everyone uses things in the same way, and not every developer realizes how their actions will effect how other people are using things.  Fine, but why can't I get telnetd to run?  I installed it, I installed inetd, and nothing.  It will not run.  It seems that something is preventing it from running entirely.  Probably SELINUX or something annoying like that.  So, I look for help on how to set this up, and everywhere I look all I see is people complaining about how you should use SSH and telnet isn't secure.  In spite of the fact that I don't care about security in this case at all.  So, can someone please give a reasonable answer to how this can be accomplished or if I have to tear the whole distribution apart or change to a different distribution all together if I want it to function as expected.  As it has for over 20 years that I can remember, anyway.

---

### Post by techrev on 2013-12-08
[COLOR=#000000][FONT=Consolas]ssh -X -f login@machine yourprogram 
or 
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]ssh -Y -f login@machine yourprogram   

Seem to have worked perfectly.  I found this on another site, but re-post here in case someone winds up here with the same problem.  I can create a batch file in windows, add that to my task bar, then click it to open a gnome-terminal or nautilus --no-desktop window or whatever I want without any problems this way.[/FONT][/COLOR]

---

### Post by SeijiSensei on 2013-12-08
Are you running the remote application with an "&" on the end to keep it running in the background?

```

client$ ssh -X server
server$ firefox &
server$ exit
client$

```

---

### Post by techrev on 2013-12-09
Of course, along with all those other things - tmux, nohup, screen, etc.  They all close when I exit the ssh session.  Running it like I said worked perfectly though.  I've been doing this for 20 years, though I haven't set this up over the past couple years.  I know how it's *supposed* to work, and it's not working like that anymore.  Ubuntu 12.04.

---

### Post by Lars Noodén on 2013-12-09
How are you exiting the SSH session?  tmux should stay running until you kill the tmux session itself.  What happens when you start a tmux session:

```

tmux

```

Then close the terminal window, open a new window, log back in with SSH, then reattach to that session?

```

tmux attach

```

It should still be running as you left it.  If you use ctrl-D or exit to leave the only/last remaining tmux window, tmux itself will close.  That is not what you want, usually.  

Alternately, instead of closing the terminal window you can leave the SSH session by entering ~. on a new line.

---

### Post by ian-weisser on 2013-12-09
Fundamentally, ssh hasn't changed. On stock 13.10 client and server, I can happily detach jobs and leave them running.
I think your idea that something on the server end is killing processes upon logout is on the right track.
Something new in the server account's .bash_logout perhaps?
Or a cron job that cleans out old connctions?
Or some too-clever power management policies?

---

### Post by techrev on 2013-12-10
Well, for me, I'm running stock Ubuntu 12.04.  When I disconnect my ssh session it goes to a blank line and doesn't return to my prompt.  Eventually I hit ctrl-c - because it's the only way out - and *poof* everything closes.  I tried tmux and I tried screen and everything else.  I thought it might have something to do with me running cygwin ssh client, but it's kind of server side behavior to close everything.  I've seen other people with the same problem.  Again, it's a clean stock install.

---

### Post by techrev on 2013-12-10
Basically, tmux and everything else started within the tmux session closes.  I didn't try running tmux on the server then attaching to it from my ssh session.  I have no idea if it would stay under those circumstances.  It's a bit much though for my purposes to set all that up.  I imagine that may work, but I would have to start a tmux session every time the server starts.  For me it's easier to use the ssh command line.  If I run tmux for the first time through in the ssh session it dies when the session collapses.

---

### Post by Lars Noodén on 2013-12-10
Rather than a cygwin client what about PuTTY or regular ssh?

---

