---
title: "Hellp with ssh session and the display on the server"
date: 2021-12-20
forum: General Help
---

### Post by julio213180 on 2021-12-20
Hi Guys, can you please give some advise on a little problem that I'm facing, and maybe some confusion to?
I have a file/web server that I use to play with it, and it does not have a graphical desk top, after it boots it stays on a terminal mode waiting for commands.
i use ssh (putty) to login on the server from my desktop PC. 
What i wanted to ask, is it possible to have all the commands that I'm typing on the ssh appear on the monitor that is connect on the server?
I searched to web trying to find something about that, but was unsuccessful, can you please give me some ideas?
i found a option to forward a session by using the option -X on ssh, but to use that would i have to have the x server installed on my server?   
and if I do install it, would it make the server have a graphical desktop? I don't want to have the server to be graphical, I like it in terminal mode.
thank you.

---

### Post by TheFu on 2021-12-20
ssh -X requires an X/server on the machine you sit behind - probably Windows since you are using Putty.  It is how people run programs on remote systems, but have the display of that window locally displayed. I use this daily, constantly, always.  But I don't use MS-Windows in that way since around 2002. Back then we'd buy a commercial X/Server for $150/seat. It was a pain to get working correctly. Of course, with a Linux GUI/Desktop workstation, all this local and remote X/Windows stuff using ssh "just works."  I've posted example commands here (in UF) many times. Since 2002, I either used Linux as dual boot or in a virtual machine, since the built-in X/Server is really great.  

I don't understand the point of typing in Windows and expecting things to show up on some other system display.  You can type on Windows and keep an interactive copy of the session in a file. There are lots of tools for that.  Most probably require using Linux, not Windows.  **asciinema** and **script** are the common tools.
[Https://github.com/asciinema/asciinema-player#self-hosting-quick-start](Https://github.com/asciinema/asciinema-player#self-hosting-quick-start)
I use:
```
$ asciinema rec mystuff.ae
$ asciinema play mystuff.ae
```
But that could be completely wrong for what you need.

If you want to use 1 keyboard and mouse to control 2 different systems, then there's something called **synergy**. It use to be commercial. I've never used it. It probably requires a GUI session to work, so it won't work on a non-GUI "server". [https://symless.com/synergy](https://symless.com/synergy) But it may work without a GUI. IDK.

---

### Post by julio213180 on 2021-12-21
thank you for the clarification. I appreciated.

---

### Post by Holger_Gehrke on 2021-12-21
You could use 'screen'. It's normally used as a kind of text-based windowing system in a terminal and as a way to run processes that take a long time without staying logged in the whole time (you basically detach the session from your terminal, log out and disconnect and later reconnect and reattach the session to a new instance of screen), but it has the ability to have one session in multiple terminal at the same time. Connect by ssh and log in, start screen, log in on the servers console and run 'screen -x'.
More details in the man page for screen.

Holger

---

### Post by TheFu on 2021-12-21
> **Holger_Gehrke said:**
> You could use 'screen'. It's normally used as a kind of text-based windowing system in a terminal and as a way to run processes that take a long time without staying logged in the whole time (you basically detach the session from your terminal, log out and disconnect and later reconnect and reattach the session to a new instance of screen), but it has the ability to have one session in multiple terminal at the same time. Connect by ssh and log in, start screen, log in on the servers console and run 'screen -x'.
More details in the man page for screen.

Holger

I'd forgotten about this with **screen**.  Bet **tmux** does it too. If I were younger, didn't have solid networking to my systems, and didn't already make a habit of using **tee** for all long running processes (or using a batch manager with logging), then I'd spend the effort to learn screen or tmux ASAP.  For admins, 1 of those two solutions is on the same level as using ssh, so very, very, worthwhile in learning and using daily, constantly, always.

---

