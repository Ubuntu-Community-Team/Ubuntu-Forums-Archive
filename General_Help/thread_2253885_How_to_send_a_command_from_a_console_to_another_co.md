---
title: "How to send a command from a console to another console"
date: 2014-11-23
forum: General Help
---

### Post by Kalinco on 2014-11-23
Dear all,
I have installed Ubuntu onto an old computer of mine and it gave me the idea of using it to run a few scripts to do some mundane tasks. And obviously, as it is a very old computer, I thought that I would remove the GUI and use it with a 'pure' console (pressing ctrl, alt + f1) and having two 'pure' consoles running, one for sending the commands and one for initialising them. My question is, how would I send that command into the other console without user input?

Thanks in advance

Kalinco

---

### Post by sudodus on 2014-11-23
Do you want to run commands from one computer into another computer? - ***ssh*** - see ```
man ssh
``` and this link to install an ssh server into one of the computers

Do you want to use it for a simple chat? - ***write*** - see ```
man write
``` (you can use ssh for the communication, you should be logged into the same server)

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

### Post by Kalinco on 2014-11-23
No, two consoles on the same computer - one accessed by ctrl, alt + f1 and the other by ctrl, alt + f2

---

### Post by nerdtron on 2014-11-23
> one for sending the commands and one for initialising them. My question  is, how would I send that command into the other console without user  input?

I'm curios though. What application would require this? when you input the command, it will run and initialize right there on your screen, why need it to be in the other console?

Maybe when we can understand you situation we can offer an accurate/more fitting answer.

---

### Post by Kalinco on 2014-11-23
I am intending to use it as a basic and private minecraft server, one console would start the server, the other would run it. This way I can stop the server safely pre computer shut-down by sending the stop command into the other console.

---

### Post by Lars Noodén on 2014-11-23
You can send *output* from one program in one tty to show in another tty.  For example, if you are in tty1, you could send output to tty2 like this:

```

date > /dev/tty2

```

That will show the output of the program "date" in tty2, but it will only show it, you won't be able to re-use it that I know of.  

If you are working with the console or via ssh, you will find a terminal multiplexer very, very useful.  [tmux](http://manpages.ubuntu.com/manpages/trusty/en/man1/tmux.1.html) is pre-installed on the server distro and can be added easily to any former desktop.  So if I have one instance of tmux running with 4 panes, I can run "ls" in the 4th pane from one of the others like this:

```

 tmux send-keys -t 4 ls C-m

```

(the -t 4 says target the 4th pane, the C-m tells tmux to generate a return character for you after entering "ls".)
It's also possible to copy and paste text between panes.  

See one of the numerous tmux tutorials to get started or ask questions here.

---

### Post by nerdtron on 2014-11-23
Still unsure of what the difference between start and run as I don't use minecraft.
But if you need multiple consoles or virtual console screens and doesn't want to leave you current terminal you might want to look at screen. I see so many post about minecraft starting applications and then they want it to keep running on the background, close the terminal, open a new the terminal and be able to get back to the running process.

It's all about using screen:
[http://www.tecmint.com/screen-command-examples-to-manage-linux-terminals/](http://www.tecmint.com/screen-command-examples-to-manage-linux-terminals/)

If you are a video guy:
[http://www.youtube.com/watch?v=tIQE4VXkh_I](http://www.youtube.com/watch?v=tIQE4VXkh_I)

---

### Post by Lars Noodén on 2014-11-23
> **Kalinco said:**
> I am intending to use it as a basic and private minecraft server, one console would start the server, the other would run it. This way I can stop the server safely pre computer shut-down by sending the stop command into the other console.

You definitely want tmux (or screen) for this.  If you launch tmux and then run minecraft or minetest within tmux, then your server stays available in one pane.  Then you can disconnect or log out and the game will stay running.  Then you can log in and view that pane whenever you want to check status or issue game server commands, and then log out again without disrupting the minecraft or minetest server.

---

### Post by Kalinco on 2014-11-23
Thanks for your help guys - I will take a look at tmux and screen

---

