---
title: "Project: Telnet output to webpage"
date: 2017-04-13
forum: General Help
---

### Post by vesil400 on 2017-04-13
Hello all, need help with this if even possible.
I want to output text from a  telnet session straight to a webpage, preferrably without going through a log file first just because it will eventually fill up the drive. Unless it is frequently deleted.
So I can telnet into a host that is constantly outputting lines, about 5 lines per second without clearing the previous lines. I just want the last line to appear updated maybe 1fps on a webpage. Telnet and the webserver for this will be run on the same ubuntu machine. Cant find anything specific for this scenario on the internet. 
Can telnet output be piped to something that is usable in html or php or anything else?
If anyone has any idea how to do this I can shape everything around that!

So far I have managed to pipe telnet to a logfile, then separate the last line of that logfile to a separate log file with watch and tail and try to use that but it is not ideal and doesnt really work like I want. 
It would be better if somehow could get the output straight to html or something...? Maybe an alternative telnet client of some sort? I have only CLI so cant use putty.

Ideas welcome!

Thanks, Christian

---

### Post by TheFu on 2017-04-13
Welcome to the forums.

a) open a console/terminal if you are on the same machine without a GUI. Normally, there are 8 real ttys on a Linux system and support for hundreds of pttys.
b) don't use telnet.  pretty much NEVER use telnet.
c) use ssh for remote connections. Sounds like you aren't doing remote.
d) there are terminal capture programs. They write to a file that you specify. Look up 'script' and 'script-replay' [http://www.tecmint.com/record-and-replay-linux-terminal-session-commands-using-script/](http://www.tecmint.com/record-and-replay-linux-terminal-session-commands-using-script/)

If you want to show the last 5 lines (and output), just use **tail -n 5** and redirect it where you want. A tiny script will wrap that in HTML if you like and a little javascript can force a refresh.

Or am I missing the point completely?

If you want to work with others in real-time, usually people use **screen** or **tmux** to share a terminal.

---

