---
title: "SSH is weird"
date: 2006-08-26
forum: General Help
---

### Post by tonyr1988 on 2006-08-26
I don't like how SSH works in Ubuntu. Namely:

1) When I hit Backspace, it outputs ^?
2) When I hit Del, it outputs ^[[3~
3) When I hit Down, Up, Left, or Right, it outputs ^[[B^, ^[[A^, ^[[D^, and ^[[C^

It also does this when I'm in programs, like vi, within SSH.

I need SSH to do programming things for class. In Windows' SSH Client, there's not a problem.

Is there a better way to access SSH in Ubuntu, and/or is there a way to re-map keys (namely those above) to normal ones?

---

### Post by scxtt on 2006-08-26
i don't have that problem w/ Dapper (or any Ubuntu release) when using SSH - i made no changes ...

are you using SSH on your Ubuntu box to connect to some other SSH server?

---

### Post by kaamos on 2006-08-26
This is problem with your ssh-client not ubuntu (I assume you connect from a not ubuntu box to your ubuntu server?).

---

### Post by peabody on 2006-08-26
Aha, the infamous backspace problem.  What kind of machine are you logging into?

This is a fix that can work, but it actually needs to be done on the remote machine.  In the .bash_profile (if you use bash, you'll have to research the equivalent file if you use a different shell on that system) put the following into it:

```

stty erase ^?

```

Put that in literally, two characters '^' and '?'.

I'm assuming you're using ssh in a gnome-terminal to login via ssh to another machine.

---

### Post by Woei on 2006-08-26
> **tonyr1988 said:**
> 
1) When I hit Backspace, it outputs ^?

I need SSH to do programming things for class. In Windows' SSH Client, there's not a problem.

Windows doesn't come with an SSH client. Which one do you use, Putty ?

> Is there a better way to access SSH in Ubuntu, and/or is there a way to re-map keys (namely those above) to normal ones?

SSH has little to do with your keymappings, your shell and terminfo files do however. Attach the contents of the /etc/inputrc file of the machine you're connecting to here. If you're using zsh, then add something like the following to ~/.zshrc:
```

case $TERM in
    xterm)
    bindkey '\eOH' beginning-of-line
    bindkey '\eOF' end-of-line
    bindkey '\e[2~' overwrite-mode
    bindkey '\e[5~' beginning-of-buffer-or-history
    bindkey '\e[6~' end-of-buffer-or-history
    bindkey '\e[3~' delete-char
    ;;
    screen)
    bindkey '\e[1~' beginning-of-line
    bindkey '\e[4~' end-of-line
    bindkey '\e[2~' overwrite-mode
    bindkey '\e[3~' delete-char
    bindkey '\e[5~' beginning-of-buffer-or-history
    bindkey '\e[6~' end-of-buffer-or-history
    ;;
    screen.linux)
    bindkey '\e[1~' beginning-of-line
    bindkey '\e[4~' end-of-line
    bindkey '\e[2~' overwrite-mode
    bindkey '\e[3~' delete-char
    bindkey '\e[5~' beginning-of-buffer-or-history
    bindkey '\e[6~' end-of-buffer-or-history
    ;;    
    linux)
    bindkey '\e[1~' beginning-of-line
    bindkey '\e[4~' end-of-line
    bindkey '\e[2~' overwrite-mode
    bindkey '\e[3~' delete-char
    bindkey '\e[5~' beginning-of-buffer-or-history
    bindkey '\e[6~' end-of-buffer-or-history
esac

```

The changes in /etc/inputrc will be similar.

---

### Post by tonyr1988 on 2006-08-27
I'm connecting from my Ubuntu (Dapper) laptop onto a Solaris box at the school. Unfortunately, being at the school, it's hard for me to get ahold of / change those files.

The Windows SSH client I'm on is when I'm on on-campus labs. They have Putty, but I didn't use it. Methinks it is:

[http://compserv.uark.edu/internet/SSH/index.htm](http://compserv.uark.edu/internet/SSH/index.htm)

That one.

This is my first few experiences with SSH, so I could be doing things wrong. Is the Terminal the only way to login to SSH from Ubuntu?

Oh yeah, I'm using:

> ssh -l [username] comp.uark.edu

Is that right?

---

### Post by peabody on 2006-08-27
Did you try my fix?  The stty erase one?  I can about gaurantee you that will work.

---

### Post by tonyr1988 on 2006-08-27
Originally I overlooked it (I accidentally read "remote" as "host"...stupid me).

But when I just tried it, it's not fixing it. Did I do things right?

I did "gedit .bash_profile and added the stty erase line at the very end of the file (I copy/pasted your quote directly into it), saved, and closed gedit. I then closed Terminal, re-opened it, and tried it again.

Same problem. Did I mess up on something?

---

### Post by peabody on 2006-08-27
> **tonyr1988 said:**
> Originally I overlooked it (I accidentally read "remote" as "host"...stupid me).

But when I just tried it, it's not fixing it. Did I do things right?

I did "gedit .bash_profile and added the stty erase line at the very end of the file (I copy/pasted your quote directly into it), saved, and closed gedit. I then closed Terminal, re-opened it, and tried it again.

Same problem. Did I mess up on something?

You're not supposed to do it on your computer, your supposed to do it on the remote computer.

---

### Post by scxtt on 2006-08-27
have you tried holding shift when you use backspace? -- that works for me on boxes that i connect to using putty but haven't fixed the ^H problem on ...

---

### Post by tonyr1988 on 2006-08-27
That's what I originally thought. Then, I thought about it from the perspective of comp.uark.edu (the server I'm SSHing to). From that view. *I* would be the remote computer, and it would be the host. So I got confused, and went ahead and tried it. :)

I can't do anything to change config files over there. Only things on my end. Is it not possible to do? It seems strange that it works in some programs, but not my Terminal.

And Shift + Bksp doesn't work either. Should I try putty or something under Wine?

---

### Post by peabody on 2006-08-27
Dude, I'm pretty sure you can edit files in your home folder over there.  There should be a dotfile for the shell you're using.  For bash it's either .bash_profile or .profile.  For ksh I believe it's .profile.  I forget what the startup file is for the csh family of shells, but regardless, you should be able to do a "vi .profile" and edit it.  Do a "ls -a" in your home folder to see what's there.

---

### Post by steve.horsley on 2006-08-27
The default shell on solaris is sh, which normally doesn't accept backspace, and doesn't have up/down arrows for history. Try just etnering the command **bash** when you've logged in, and see if they have bash installed.

---

### Post by peabody on 2006-08-27
> **steve.horsley said:**
> The default shell on solaris is sh, which normally doesn't accept backspace, and doesn't have up/down arrows for history. Try just etnering the command **bash** when you've logged in, and see if they have bash installed.

I'd have thought about this too, but he said that it works within Putty.  And just because sh is default doesn't mean the sys admin hasn't changed it, most of the sys admins I know change the default shell to either bash, ksh or tcsh.

---

### Post by steve.horsley on 2006-08-27
> **peabody said:**
> I'd have thought about this too, but he said that it works within Putty. 
Putty sends DEL when the user types BS. This is configurable in putty IIRC. OTOH, most nix terminals just send what the user types. Bash accepts both BS and DEL.
> 
 And just because sh is default doesn't mean the sys admin hasn't changed it, most of the sys admins I know change the default shell to either bash, ksh or tcsh. The fact that the up and down arrows don't work suggest that bash has not been installed as the default shell.

---

### Post by DCM36 on 2006-08-27
While this doesn't fix your problem, I have been able to use PUTTY with wine. Doesn't fix your problem, but might be a workaround.

---

### Post by RAOF on 2006-08-27
If you're using gnome-terminal, check out the "compatibility" settings.
Edit->Current Profile->Compatibility.  That will give you options of what gnome-terminal sends when you hit "backspace".  One of the options should work for you :)

---

### Post by tonyr1988 on 2006-08-28
Yay! Success. Sorry for my newbiness (and the confusion that it caused), but this is what I did:

1) bash showed we have v3.00
2) I did "ls -a" and saw it was called .profile
3) I edited .profile and added that line at the end.
4) I closed, opened bash, and the backspace works.

However, do I have to open bash every single time? Is there a way to make it my default, or does that require admin rights?

---

### Post by scxtt on 2006-08-28
check out the command **chsh**, as in do a man on it ... i'm thinking **#:> chsh -s /bin/bash $USER** will work ...

---

### Post by Woei on 2006-08-29
> **tonyr1988 said:**
> Yay! Success. Sorry for my newbiness (and the confusion that it caused), but this is what I did:

1) bash showed we have v3.00
2) I did "ls -a" and saw it was called .profile
3) I edited .profile and added that line at the end.
4) I closed, opened bash, and the backspace works.

However, do I have to open bash every single time? Is there a way to make it my default, or does that require admin rights?

When skimming through this thread, I still can't figure out what OS the remote host is running. If it's a Solaris machine, it won't have the chsh utility to change your login shell. Use something like 'passwd -e' instead. The binary will have to be root setuid, and of course, it's entirely possible something like NIS+ is in use, bypassing the local /etc/passwd file. If that's the case, send a nice email to your friendly server operator, asking him to change the login shell for you. It's a reasonable request.

Alternatively, you can let ksh (which I'm guessing is your current shell) automatically launch bash at login, by putting something like 'exec bash --login' at the end of your ~/.profile. Note that this is *not* recommended, as this will only work for interactive shells. It should only be done when your system administrator is uncooperative, and if he or she is, he or she isn't doing a good job.

---

