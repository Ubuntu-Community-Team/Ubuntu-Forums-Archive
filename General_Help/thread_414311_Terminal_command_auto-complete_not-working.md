---
title: "Terminal command auto-complete not-working"
date: 2007-04-19
forum: General Help
---

### Post by theseeker on 2007-04-19
My problem is rather straightforward, but I don't know a solution for it!

I installed Feisty, and noticed that when using terminal commands as a superuser, I can't use TAB key to auto-complete the command, i.e. sudo apti[TAB] doesn't result in sudo aptitude. I don't know if I'm the only one that has this problem, as in Edgy it was working normally! 

I hope I don't have to type the whole command from now on!!!

HEEEELP!!!!

---

### Post by darklemming54 on 2007-04-19
what shell are you using

---

### Post by theseeker on 2007-04-19
Bash, it is. 

Any suggestions?

---

### Post by darklemming54 on 2007-04-19
edit: nevermind, I don't know why it wont work

---

### Post by theseeker on 2007-04-19
No luck, i'm afraid

---

### Post by theseeker on 2007-04-19
Any other suggestions? It is REALLY annoying... :(

---

### Post by avb on 2007-04-19
> **theseeker said:**
> Any other suggestions? It is REALLY annoying... :(


please post the output of the command 'set'. And btw, what terminal are u using?

---

### Post by theseeker on 2007-04-19
I'm using gnome-terminal. Set goes:

```

giorgos@steppenwolf:~$ set
BASH=/bin/bash
BASH_ARGC=()
BASH_ARGV=()
BASH_LINENO=()
BASH_SOURCE=()
BASH_VERSINFO=([0]="3" [1]="2" [2]="13" [3]="1" [4]="release" [5]="i486-pc-linux-gnu")
BASH_VERSION='3.2.13(1)-release'
COLORTERM=gnome-terminal
COLUMNS=80
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-uVH5BL9ATx,guid=b0400c7be38fc69b3a5abc004628038d
DESKTOP_SESSION=default
DIRSTACK=()
DISPLAY=:0.0
EUID=1000
GDMSESSION=default
GDM_XSERVER_LOCATION=local
GNOME_DESKTOP_SESSION_ID=Default
GNOME_KEYRING_SOCKET=/tmp/keyring-cq1tX6/socket
GROUPS=()
GTK_RC_FILES=/etc/gtk/gtkrc:/home/giorgos/.gtkrc-1.2-gnome2
HISTFILE=/home/giorgos/.bash_history
HISTFILESIZE=500
HISTSIZE=500
HOME=/home/giorgos
HOSTNAME=steppenwolf
HOSTTYPE=i486
IFS=$' \t\n'
LANG=en_US.UTF-8
LINES=24
LOGNAME=giorgos
MACHTYPE=i486-pc-linux-gnu
MAILCHECK=60
OPTERR=1
OPTIND=1
OSTYPE=linux-gnu
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PIPESTATUS=([0]="0")
PPID=7231
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
PS2='> '
PS4='+ '
PWD=/home/giorgos
SESSION_MANAGER=local/steppenwolf:/tmp/.ICE-unix/5341
SHELL=/bin/bash
SHELLOPTS=braceexpand:emacs:hashall:histexpand:history:interactive-comments:monitor
SHLVL=1
SSH_AGENT_PID=5379
SSH_AUTH_SOCK=/tmp/ssh-dLEVQe5341/agent.5341
TERM=xterm
UID=1000
USER=giorgos
USERNAME=giorgos
WINDOWID=46137422
XAUTHORITY=/home/giorgos/.Xauthority
_=']'
command_not_found_handle () 
{ 
    /usr/bin/command-not-found $1;
    return $?
}

```

Thanx for any help!

---

### Post by theseeker on 2007-04-20
Hey, people! Anyone with the faintest idea of what's wrong here??! I can't be alone on this...

Please HELP!!!

---

### Post by theseeker on 2007-04-20
Ok, found it!

For future reference, you have to uncomment the following inside the /etc/bash.bashrc file:

```

# enable bash completion in interactive shells
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

```

Credits here: [http://ubuntuforums.org/showthread.php?t=331266](http://ubuntuforums.org/showthread.php?t=331266) ;)

---

### Post by spockrock on 2007-06-09
thanks you are a life saver!!

---

### Post by bhavi on 2008-03-24
> **theseeker said:**
> Ok, found it!

For future reference, you have to uncomment the following inside the /etc/bash.bashrc file:

```

# enable bash completion in interactive shells
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

```

Credits here: [http://ubuntuforums.org/showthread.php?t=331266](http://ubuntuforums.org/showthread.php?t=331266) ;)

Thanks mate.. worked great...

---

