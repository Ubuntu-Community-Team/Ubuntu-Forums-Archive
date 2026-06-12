---
title: "HOWTO: My Top 5 Bash Aliases"
date: 2013-02-21
forum: General Help
---

### Post by strid3r on 2013-02-21
When I first started using Ubuntu, one thing that got on my nerves was having to type out long commands into the terminal.
Some of them were hard to memorize and others were just a waste of time.

Then I discovered aliases and the terminal has become my best friend. :p

Aliases allow you to shorten commands, for example I have an alias setup for "sudo apt-get update". When ever I want to run this command, I just type "u" and hit enter.

Here's how I set it up:

```
alias u='sudo apt-get update'
```

You can even take it one step further and update your whole system and clear the apt-cache with one single character:

```
alias u='sudo apt-get update && sudo apt-get upgrade && sudo apt-get -y dist-upgrade && sudo apt-get -y autoremove && sudo apt-get -y autoclean'
```

There are so many uses for aliases, but here are my top 5 that I use the most. Feel free to post your own faves!


Take ownership of any file. Type "takeown filename"
```
alias takeown='sudo chown -R $USER'

```

Open a file in gedit as root. Type "sedit filename"
```
alias sedit='sudo gedit'
```

Search for a process that is currently running. Type "psx process name"
```
alias psx='ps aux| grep'
```

Add a ppa to your sources. Type "ppa ppa:name/of/ppa"
```
alias ppa='sudo apt-add -y repository
```

Install a program (be careful with this one). Type "inst program name"
```
alias inst='sudo apt-get install -y'
```

Try these out by pasting the "alias ..." into your terminal and then use the alias as you would a normal command.

If you want to make them permanent, just copy the "alias ..." command to your .bash_aliases file in your home folder.

---

### Post by ajgreeny on 2013-02-21
Ones I use a lot are:-
Simply to exit terminal quickly
```
alias q='exit'
``` To quickly view the grub menu of my five OS machine
```
alias menu='grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100'
```To view all recently installed packages
```
alias install='grep -iw install /var/log/dpkg.log.1 && grep -iw install /var/log/dpkg.log'
```To view all recently removed packages
```
alias remove='grep -iw remove /var/log/dpkg.log.1 && grep -iw remove /var/log/dpkg.log'
```To see all recently upgraded packages.
```
alias upgrade='grep -iw upgrade /var/log/dpkg.log.1 && grep -iw upgrade /var/log/dpkg.log'
```

I also have openssh-server installed but to stop it opening on bootup as I need it only occasionally, I comment out the line
```
# start on filesystem
```in /etc/init/ssh.conf which stops the server before it even starts. I then use aliases
```
alias ssh+='sudo service ssh start'
alias ssh-='sudo service ssh stop'
```to start and stop ssh server when I need to, just for my system's added security..

---

### Post by strid3r on 2013-02-21
> **ajgreeny said:**
> Ones I use a lot are:-
Simply to exit terminal quickly
```
alias q='exit'
``` To quickly view the grub menu of my five OS machine
```
alias menu='grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100'
```To view all recently installed packages
```
alias install='grep -iw install /var/log/dpkg.log.1 && grep -iw install /var/log/dpkg.log'
```To view all recently removed packages
```
alias remove='grep -iw remove /var/log/dpkg.log.1 && grep -iw remove /var/log/dpkg.log'
```To see all recently upgraded packages.
```
alias upgrade='grep -iw upgrade /var/log/dpkg.log.1 && grep -iw upgrade /var/log/dpkg.log'
```

I also have openssh-server installed but to stop it opening on bootup as I need it only occasionally, I comment out the line
```
# start on filesystem
```in /etc/init/ssh.conf which stops the server before it even starts. I then use aliases
```
alias ssh+='sudo service ssh start'
alias ssh-='sudo service ssh stop'
```to start and stop ssh server when I need to, just for my system's added security..



Cheers mate!

There's some I never thought to use. Gave me some cool ideas. ;)

---

