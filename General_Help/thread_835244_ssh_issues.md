---
title: "ssh issues"
date: 2008-06-20
forum: General Help
---

### Post by adam35413 on 2008-06-20
I have been experience a weird issue with ssh.  I have a ubuntu 7.10 server that I am trying to ssh to.  I can ssh fine from my windows machine at work (behind a proxy) and at home to the same network the server is on using Putty.  However, when I try ssh with the command line tool on my Ubuntu 8.04 laptop, it does not work.  I have tried it both from behind the proxy at work and from home on the same network as the 7.10 server.  Whenever I attempt to ssh, it gets to the password phase fine.  After I have entered a correct password it just hangs.  

Any thoughts?

---

### Post by beckols on 2008-06-20
What is the exact command you are using?  Just `ssh IP` or do you add any options?

---

### Post by adam35413 on 2008-06-20
The exact command is "ssh IP".  I have also done "ssh IP -l username" to try something different, but no dice.

---

### Post by beckols on 2008-06-20
This happened to me when I ssh'ed remotely into one computer, then tried to ssh from that computer to another one on the same internal network. It just hung and didn't do anything... I don't see how these situations would be similar though.

---

### Post by unutbu on 2008-06-20
Try 
```

ssh -vvv username@IP
```
Post the last 10 lines of output before the terminal hangs.

---

### Post by beckols on 2008-06-20
I've been doing a little research and I've found quite a few other cases with your problem, but of course no one can find a solution... except for one guy who had a vague response along the lines of his PAM settings were messed up, but thats out of my knowledge-range

---

### Post by adam35413 on 2008-06-20
I just got home and got the verbose output.  Here are the last couple lines:

debug3: Ignored env COLORTERM
debug3: Ignored env XAUTHORITY
debug3: Ignored env _
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768

At this point the ssh session hangs.

Any ideas?  I just installed Putty and I am able to connect to my server fine.....

---

### Post by adam35413 on 2008-06-20
Bump.  I am completely mystified.

---

### Post by unutbu on 2008-06-20
Please post the entire output of ssh -vvv if it isn't too long. Or if it is, just the stuff after you type the password.

Please include the ssh command you use.

---

### Post by adam35413 on 2008-06-21
My command is "ssh -vvv siteaddress.com".  I am not specifying a user because it is the same as what I am coming from.  However I have tried specifying a user too and that didn't help.  

Here is the full output after the password is entered and the computer hangs:
```
debug3: packet_send2: adding 48 (len 66 padlen 14 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 0
debug3: tty_make_modes: ospeed 38400
debug3: tty_make_modes: ispeed 38400
debug3: tty_make_modes: 1 3
debug3: tty_make_modes: 2 28
debug3: tty_make_modes: 3 127
debug3: tty_make_modes: 4 21
debug3: tty_make_modes: 5 4
debug3: tty_make_modes: 6 255
debug3: tty_make_modes: 7 255
debug3: tty_make_modes: 8 17
debug3: tty_make_modes: 9 19
debug3: tty_make_modes: 10 26
debug3: tty_make_modes: 12 18
debug3: tty_make_modes: 13 23
debug3: tty_make_modes: 14 22
debug3: tty_make_modes: 18 15
debug3: tty_make_modes: 30 0
debug3: tty_make_modes: 31 0
debug3: tty_make_modes: 32 0
debug3: tty_make_modes: 33 0
debug3: tty_make_modes: 34 0
debug3: tty_make_modes: 35 0
debug3: tty_make_modes: 36 1
debug3: tty_make_modes: 37 0
debug3: tty_make_modes: 38 1
debug3: tty_make_modes: 39 1
debug3: tty_make_modes: 40 0
debug3: tty_make_modes: 41 1
debug3: tty_make_modes: 50 1
debug3: tty_make_modes: 51 1
debug3: tty_make_modes: 52 0
debug3: tty_make_modes: 53 1
debug3: tty_make_modes: 54 1
debug3: tty_make_modes: 55 1
debug3: tty_make_modes: 56 0
debug3: tty_make_modes: 57 0
debug3: tty_make_modes: 58 0
debug3: tty_make_modes: 59 1
debug3: tty_make_modes: 60 1
debug3: tty_make_modes: 61 1
debug3: tty_make_modes: 62 0
debug3: tty_make_modes: 70 1
debug3: tty_make_modes: 71 0
debug3: tty_make_modes: 72 1
debug3: tty_make_modes: 73 0
debug3: tty_make_modes: 74 0
debug3: tty_make_modes: 75 0
debug3: tty_make_modes: 90 1
debug3: tty_make_modes: 91 1
debug3: tty_make_modes: 92 0
debug3: tty_make_modes: 93 0
debug1: Sending environment.
debug3: Ignored env GPG_AGENT_INFO
debug3: Ignored env SHELL
debug3: Ignored env DESKTOP_STARTUP_ID
debug3: Ignored env TERM
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env GTK_RC_FILES
debug3: Ignored env WINDOWID
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env GNOME_KEYRING_SOCKET
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env USERNAME
debug3: Ignored env PATH
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env GDM_XSERVER_LOCATION
debug3: Ignored env PWD
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env GNOME_KEYRING_PID
debug3: Ignored env GDM_LANG
debug3: Ignored env GDMSESSION
debug3: Ignored env HISTCONTROL
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env WINDOWPATH
debug3: Ignored env DISPLAY
debug3: Ignored env LESSCLOSE
debug3: Ignored env COLORTERM
debug3: Ignored env XAUTHORITY
debug3: Ignored env _
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768

```

---

### Post by adam35413 on 2008-06-21
Any thoughts?

---

### Post by unutbu on 2008-06-21
I'm sorry, I don't know what the problem is. All I can offer is a way to explore the problem.

Here are some weak suggestions:
1) Try to log in from the laptop to the server. After it hangs, log in to the server. Then type
```

cd /var/log
ls -lt | head -n10
```
This will show you the last 10 log files to have changed. If there is an error message related to sshd, it would be in one of those files.

2) You probably won't find anything by following suggestion #1 because sshd is not run in a very verbose mode by default. To change that, run
```

ps axuw | grep sshd
sudo /etc/init.d/ssh stop
sudo /usr/sbin/sshd -d

```
The first command is just to show you the current command which is used to run the ssh server (daemon), sshd. If your system is like mine, the command will be /usr/sbin/sshd. The second command stops sshd. The third command restarts sshd manually, but this time with the -d flag, which puts sshd in debug mode. The server will now write more verbose debug output to a system log. I'm not sure which file, but you'll be able to find it with suggestion #1.

So after restarting sshd with the -d flag, try ssh'ing from laptop to server again, and then check the /var/log files for error messages.

If you want even more debugging messages, you can redo suggestion #2 with the -dd flag, or even the -ddd flag. 

By the way, is it the terminal that is hanging, or is the whole computer hanging?

---

### Post by linuxtips.org on 2008-07-04
You can also start sshd process with debugging enabled on a different port while you're still continue to work with normal port 22 ssh server like that:

```

sudo /usr/sbin/sshd -ddd -p 5656

```

and connect with:

```

ssh -vvv -p 5656 user@hostname

```

You can also see article on [Linux-Tips.org]("http://www.linux-tips.org"): [Solving ssh problems]("http://linux-tips.org/article/61/solving-ssh-problems")

> **unutbu said:**
> 
2) You probably won't find anything by following suggestion #1 because sshd is not run in a very verbose mode by default. To change that, run
```

ps axuw | grep sshd
sudo /etc/init.d/ssh stop
sudo /usr/sbin/sshd -d

```


---

### Post by mexpolk on 2008-07-04
I confirm that is the driver of the Wireless (wl) that does not work! I've installed, the old, ndiswrapper and SSH works again. *Goodbye PuTTY!!!*

Also, another symptom is that I couldn't export Facebook photos from F-Spot. My guess is that, the wireless drivers, has something to do with some authentication systems.

If you need to install ndiswraper, **_[this]("http://ubuntuforums.org/showpost.php?p=5320732&postcount=18")_** is how I solved.

---

