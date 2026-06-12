---
title: "[SOLVED] Three questions about the terminal (tty1...6)"
date: 2008-02-11
forum: General Help
---

### Post by b0rka7a on 2008-02-11
I have three questions about the terminal (tty1...6)
1. How to set a smaller font size (and maybe different font) ?
2. How to start my counter-strike server ( ./hlds ) automatically in tty1 when my Kubuntu starts ?
3. How can I minimize the server so I can use the terminal and then go back to the server ?

---

### Post by b0rka7a on 2008-02-11
Oh, and also how to scroll up :D 10x in advance!

---

### Post by PinkFloyd102489 on 2008-02-11
2. Add the server command to /etc/rc.local to make it start on boot.
3. Add a & to the end to send the process to the background and give you control over the terminal again.

No idea about #1. Try the ~/.bashrc file.

---

### Post by b0rka7a on 2008-02-11
10x for the fast reply! Im not on my pc right now. Well... okay, when I add & in the end of the command, it starts in the background, but how do I return to the server again ? And also, I want to control it via ssh too :) How ? (I have the ssh server runing and I can connect to it). Ill write tomorrow because Im writing from my phone now. Good night ;)

---

### Post by Zwack on 2008-02-11
To start a process in the background you can use <command> &
It might crap out when you log out though (assuming you want it to stay running) so you could try 

nohup command &

If you don't mind pausing it between times you can switch a process from the foreground to the background using Control-Z.

Command

Control-Z

Command Stopped, prompt returns

bg

Command is running in the background....

fg

Command is running in the foreground again.

However I suspect that you might be a bit more interested in the screen command...  You can detach a screen session and leave it running, then you can attach to it later... either from a shell, or from a terminal window in X or... 

Z.

---

### Post by b0rka7a on 2008-02-12
When I start the server with "<command> &" it runs in the background. When I type "fg" the server continues working in the foreground.
When I press Ctrl+Z, then type "bg" the server stops and then continues working in the background.
When I start the server with "nohup <command> &" the server starts in the background, but when I type "fg" I can't go back to the server.

=-=-=-=-=

I start the server:
```
boris@kubuntu:/home/hlds$ **./hlds_run -game cstrike +ip 192.168.1.2 +sv_lan 1 -nomaster +maxplayers 18 +map de_dust**
Auto detecting CPU
Using Pentium II Optimised binary.
Auto-restarting the server on crash

Console initialized.
[b]...
   <<[bla bla bla]>>
...[/b]
Type 'amx_help' in the console to see available commands
Time Left: 59:43 min. Next Map: de_airstrip
```
=-=-=-=-=

I start the server with "<command> &":
```
boris@kubuntu:/home/hlds$ **./hlds_run -game cstrike +ip 192.168.1.2 +sv_lan 1 -nomaster +maxplayers 18 +map de_dust &**
[1] 8053
boris@kubuntu:/home/hlds$ Auto detecting CPU
Using Pentium II Optimised binary.
Auto-restarting the server on crash

Console initialized.
[b]...
   <<[bla bla bla]>>
...[/b]
Type 'amx_help' in the console to see available commands
Time Left: 59:43 min. Next Map: de_airstrip
   **<<[I press Enter here]>>**
boris@kubuntu:/home/hlds$
```
=-=-=-=-=

I stop the server:
```
boris@kubuntu:/home/hlds$ **fg**
./hlds_run -game cstrike +ip 192.168.1.2 +sv_lan 1 -nomaster +maxplayers 18 +map de_dust
**exit**
exit
Tue Feb 12 19:05:59 GMT 2008: Server Quit

boris@kubuntu:/home/hlds$
```
=-=-=-=-=

I start the server with "nohup <command> &":
```
boris@kubuntu:/home/hlds$ **nohup ./hlds_run -game cstrike +ip 192.168.1.2 +sv_lan 1 -nomaster +maxplayers 18 +map de_dust &**
[1] 8174
boris@kubuntu:/home/hlds$ nohup: appending output to `nohup.out'
   **<<I press Enter here>>**
boris@kubuntu:/home/hlds$ **fg**
nohup ./hlds_run -game cstrike +ip 192.168.1.2 +sv_lan 1 -nomaster +maxplayers 18 +map de_dust
[b]exit
   <<THE SERVER IS NOT RESPONDING!!>>[/b]
```
I type "fg" then stop it with Ctrl+C and "sudo killall -9 hlds_i686" (If I don't kill that process I can't start the server again, because the port that the game is using is busy)

---

### Post by b0rka7a on 2008-02-12
Also when I start the server in tty1 with "<command> &", then type "fg" in tty2, I get:
```
bash: fg: current: no such job
```
I want to work in it from other PCs with ssh ? How ?

---

### Post by Zwack on 2008-02-12
If you want to move it from tty to tty then you definitely need to use screen.  fg/bg only work in the current shell.  tty2 is not the same as tty1 is not the same as pty1 is...

Search for that command I found a good tutorial on it the other day.  That way you can detach your screen session, logout, log back in and reattach it to do more.

screen is your friend.

Use screen.

As for scrolling up/down in the terminals Control-PageUp and Control-PageDown will do what you want.


I hope that this helps,

Z.

---

### Post by b0rka7a on 2008-02-12
Thank you :) I found that tutorial:
[http://news.softpedia.com/news/How-to-set-up-a-Counter-Strike-1-6-dedicated-server-under-Linux-35607.shtml](http://news.softpedia.com/news/How-to-set-up-a-Counter-Strike-1-6-dedicated-server-under-Linux-35607.shtml)
Now everything is working just perfect ! Thank you again !

Edit: And the scrolling is working with Shift + PageUp/Down

---

