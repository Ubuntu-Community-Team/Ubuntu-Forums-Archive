---
title: "Running a program at start up with output to screen and SSH session"
date: 2023-06-14
forum: General Help
---

### Post by sergei9472 on 2023-06-14
[COLOR=#000000][FONT=&amp]I have Ubuntu Server 22.04.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]**Tasks:**[/FONT][/COLOR]

[LIST=1]
[*]To run console app on it, which will display some text information on the screen.
[*]Need to see app's output (messages) it on connected via HDMI monitor or TV and also see it remotely via SSH.
[*]OS and app started automatically after turning on power of the RPI. So no need to login, press anything etc.
[*]App started automatically and if it hangs or exit, it restarted automatically.
[/LIST]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]**Additional tasks:**[/FONT][/COLOR]

[LIST=1]
[*]To save all output and error messages of app to separate log file in app folder if possible, but not to systemd&#8217;s journal.
[*]Limit log file size.
[*]Need an opportunity to login locally with connected keyboard and via SSH to run updates and do some maintenance etc.
[/LIST]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]**That's what I managed to achieve:**[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]I guess the best way is to use method with Systemd Service.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]1. App is here /home/user/myapp[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]2. I created myapp.service:[/FONT][/COLOR]
```
[COLOR=#000000][FONT=&amp][Unit][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Description=My App[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]After=network.target[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][Service][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Type=simple[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]ExecStart=/home/user/myapp[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]StandardOutput=tty[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]StandardError=tty[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]TTYPath=/dev/tty1[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]User=user[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Restart=always[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]RestartSec=3[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][Install][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]WantedBy=multi-user.target[/FONT][/COLOR]

```

[COLOR=#000000][FONT=&amp]App running automatically and displays info at connected monitor without login. I can switch to new tty with Ctrl + Alt +F2 with attached keyboard and can login to OS for maintenance. Some of the tasks have been completed.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Is it correct method? May be there is some better way?[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]**When I connect via SSH I see pts0, so don&#8217;t see output of app :(**[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
I tried to use **screen command** but it works only after login if I start app manually (myapp.service stoped).[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]1. Creating new session and run app: screen -S tty1 /home/user/myapp. See output on local screen.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]2. Connecting with SSH (manuals recommend use -t parameter. It works without it for me).[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]3. Attaching to session: screen -x. See output via SSH and on local screen. Can detach and run command for maintenance. Is there some way to run screen -x on server side automatically after connecting via SSH?[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]It works, but it not when I try to run it with myapp.service:[/FONT][/COLOR]
```
[COLOR=#000000][FONT=&amp][Unit][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Description=My App[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]After=network.target[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][Service][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Type=simple[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]ExecStart=/usr/bin/screen -S tty1 -/home/user/myapp[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]ExecStop=/usr/bin/screen -X quit[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]StandardOutput=tty[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]StandardError=tty[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]TTYPath=/dev/tty1[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]User=user[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Restart=always[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]RestartSec=3[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][Install][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]WantedBy=multi-user.target[/FONT][/COLOR]

```[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Don&#8217;t works. Have error message on local screen «Must be connected to a terminal»[/FONT][/COLOR]

---

### Post by TheFu on 2023-06-14
It is possible to show custom text files pre-login for both ssh and consoles.  
Canonical uses this in recent releases as advertising space.  I remove it from my systems, but you could follow how they do it for your own messages. You can find the files in /etc/ somewhere. They are a mix for text and scripts to pull dynamic content.

ssh logins using key-based authentication should bypass those messages, however.  Then you may need to use the MOTD technique, but many people, including me, disable that by having a ~/.hushlogin file.

I don't use either screen nor tmux.  Just never got into the habit and have never needed it.  My workaround (if you want to call it that), is to send any output to a log file, then that file can be viewed from anywhere, if I like.  The main reason to use tmux/screen was for re-connections when a connection was dropped.  Maybe I'm just lucky, but that has never been a huge problem anywhere I worked.

BTW, this post reads like a homework assignment or test questions. Care to share?

---

### Post by sergei9472 on 2023-06-15
> **TheFu said:**
> It is possible to show custom text files pre-login for both ssh and consoles.  
Canonical uses this in recent releases as advertising space.  I remove it from my systems, but you could follow how they do it for your own messages. You can find the files in /etc/ somewhere. They are a mix for text and scripts to pull dynamic content.

ssh logins using key-based authentication should bypass those messages, however.  Then you may need to use the MOTD technique, but many people, including me, disable that by having a ~/.hushlogin file.

I don't use either screen nor tmux.  Just never got into the habit and have never needed it.  My workaround (if you want to call it that), is to send any output to a log file, then that file can be viewed from anywhere, if I like.  The main reason to use tmux/screen was for re-connections when a connection was dropped.  Maybe I'm just lucky, but that has never been a huge problem anywhere I worked.

I will try, thanks. Output of my app always scrolls, it looks similar to output of ping command but strings have more characters. The display will scroll endlessly while the program is running. I am not sure advertising space will be useful for it.

> BTW, this post reads like a homework assignment or test questions. Care to share?
Sorry, I don't understand your question. I guess my English not so good. Could you please explain it, please.

If you want to use my post (tasks) like a homework for students, I agree to share.

---

### Post by TheFu on 2023-06-15
> **sergei9472 said:**
> I will try, thanks. Output of my app always scrolls, it looks similar to output of ping command but strings have more characters. The display will scroll endlessly while the program is running. I am not sure advertising space will be useful for it.

Are you trying to have some dynamic area that is constantly updated above the login: prompt?  Something like htop or glances do?

If that's the situation and you are coding in python or C, you might check out **notcurses** libraries. [https://github.com/dankamongmen/notcurses](https://github.com/dankamongmen/notcurses) - check out a youtube video to see what is possible.  Unfortunately, isn't isn't a simple replacement for **ncurses**, but the capabilities for **not curses** are really impressive, if you are using a language that has bindings for the library.

The way the original question was worded seemed like it was a homework assignment for a college student. That's why I asked. These forums won't answer homework questions knowingly, but we will help with leads for the answer.

---

### Post by sergei9472 on 2023-06-20
> **TheFu said:**
> Are you trying to have some dynamic area that is constantly updated above the login: prompt? Something like htop or glances do?
No, output of program is similar to output of ping command: +1 new string with text data (statistic) each second.

> If that's the situation and you are coding in python or C, you might check out **notcurses** libraries. [https://github.com/dankamongmen/notcurses](https://github.com/dankamongmen/notcurses) - check out a youtube video to see what is possible. Unfortunately, isn't isn't a simple replacement for **ncurses**, but the capabilities for **not curses** are really impressive, if you are using a language that has bindings for the library.

I don't coding. Just using ready app.

> The way the original question was worded seemed like it was a homework assignment for a college student. That's why I asked. These forums won't answer homework questions knowingly, but we will help with leads for the answer.
It's not a homework of student. Just trying to find solution for work tasks O:)

---

### Post by ian-weisser on 2023-06-20
> **sergei9472 said:**
> I don't coding. Just using ready app.

Well, if you really want this, then you must learn some basic coding. There is no "ready app" for what you have described.

---

