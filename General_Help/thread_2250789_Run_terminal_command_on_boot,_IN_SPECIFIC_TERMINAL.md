---
title: "Run terminal command on boot, IN SPECIFIC TERMINAL"
date: 2014-10-31
forum: General Help
---

### Post by matthew50 on 2014-10-31
Hey!

I know that the question "How do I run a command on startup" gets asked a lot, but I want to run multiple commands, each in one of my 6 ubuntu text terminals.

Is there a way to run a command for a terminal? Lets say I want to run "htop" in terminal 2, "sudo apt-get update" in terminal 3 and "sensors" in terminal 4, leaving terminal 1 free.

Many thanks!

---

### Post by CaptainMark on 2014-10-31
This may be useful for logging on to tty's automatically [https://stackoverflow.com/questions/14152026/how-can-i-automatically-login-on-a-tty-and-execute-a-script](https://stackoverflow.com/questions/14152026/how-can-i-automatically-login-on-a-tty-and-execute-a-script) it then reccommends using .bash_profile to start a script, you can use the command tty to check which tty is running, the only problem I foresee with this is that you would never be able to log on to tty 2-4 without running those commands. Just out of curiosity what is the reason you want to do this? If you just wanted to run a script but be able to view the output then using crontab with redirects would be a simpler option, or crontabs that start commands in screen which you can then recall from any terminal later.

---

### Post by matthew50 on 2014-10-31
> **CaptainMark said:**
> This may be useful for logging on to tty's automatically [https://stackoverflow.com/questions/14152026/how-can-i-automatically-login-on-a-tty-and-execute-a-script](https://stackoverflow.com/questions/14152026/how-can-i-automatically-login-on-a-tty-and-execute-a-script) it then reccommends using .bash_profile to start a script, you can use the command tty to check which tty is running, the only problem I foresee with this is that you would never be able to log on to tty 2-4 without running those commands. Just out of curiosity what is the reason you want to do this? If you just wanted to run a script but be able to view the output then using crontab with redirects would be a simpler option, or crontabs that start commands in screen which you can then recall from any terminal later.

The reason I wish to do this is that I'm making a web server, and I need it to automatically execute a command in more than one tty without me having to plug in a keyboard or monitor and do it manually.

I've already made each tty login automatically, so now I just need to execute a specific command in a specific terminal all at once, or with a short delay.

Thankyou very much in advance!

---

### Post by CaptainMark on 2014-10-31
Screen still sounds like a better idea to me, in case you aren't aware of it screen allows you to run commands in terminals that aren't attached to any TTY or terminal window, you can then attach dettach and reattach at will to the terminals, they can be easily started at boot time automatically and can be used locally or over SSH connections from another machine, if you already know all this then apologies for pushing the idea, its possible I'm misunderstanding your intentions. Any way glad the link was useful. [https://help.ubuntu.com/community/Screen](https://help.ubuntu.com/community/Screen)

---

### Post by nerdtron on 2014-10-31
```
sudo apt-get install screen
```

Then you can start using screen to multiply your consoles.
```
screen -S htop-screen
```
On this screen run htop, then press Ctrl+a,d to deattach and leave it running on the background

```
 screen -S apt-get-screen
```
On this screen run apt-get, then press Ctrl+a,d to deattach and leave it running on the background

```
 screen -S sensors-screen
```
On this screen run your sensors, then press Ctrl+a,d to deattach and leave it running on the background

Now you are back to your original terminal.
You can list all your created screen:
```
screen -ls
```

You can "go inside" on the screens that you have by using:
```
screen -dr [screen.number]
```

And if you want to automate running screen by just using single line commands, see the answer here : [http://superuser.com/questions/386059/how-can-i-start-multiple-screen-sessions-automatically](http://superuser.com/questions/386059/how-can-i-start-multiple-screen-sessions-automatically)

---

### Post by dragonfly41 on 2014-10-31
Can't you open multiple tabs inside a single terminal window?

---

