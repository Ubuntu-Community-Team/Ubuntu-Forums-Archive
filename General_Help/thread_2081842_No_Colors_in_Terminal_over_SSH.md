---
title: "No Colors in Terminal over SSH"
date: 2012-11-07
forum: General Help
---

### Post by jlacroix on 2012-11-07
This is strange. When I SSH into my file server and type the "ls" commands, I get color in the terminal (for example, directories are colored blue). But when I SSH into my other Kubuntu machine, I don't get any colors at all. If I'm physically sitting at that machine, I have colors in the terminal, but not when I SSH into it.

I tried restoring the .bashrc file from /etc/skel but that didn't help. This is a silly problem but maybe someone else has run into it before?

---

### Post by Slim Odds on 2012-11-07
> **jlacroix said:**
> This is strange. When I SSH into my file server and type the "ls" commands, I get color in the terminal (for example, directories are colored blue). But when I SSH into my other Kubuntu machine, I don't get any colors at all. If I'm physically sitting at that machine, I have colors in the terminal, but not when I SSH into it.

I tried restoring the .bashrc file from /etc/skel but that didn't help. This is a silly problem but maybe someone else has run into it before?
Check your bash startup files. ls is an alias for 'ls --color=auto". Without the '--color=auto' you will get no color over a remote link like that.

---

### Post by jlacroix on 2012-11-07
> **Slim Odds said:**
> Check your bash startup files. ls is an alias for 'ls --color=auto". Without the '--color=auto' you will get no color over a remote link like that.
You're right, when I execute "ls --color=auto" I get the output I expect. Why would that be different in SSH versus when I am actually at the machine?

---

### Post by rnerwein on 2012-11-08
> **jlacroix said:**
> You're right, when I execute "ls --color=auto" I get the output I expect. Why would that be different in SSH versus when I am actually at the machine?

hi
try: echo $TERM and have a look what kind of terminal is set if you login via ssh.

---

### Post by jlacroix on 2012-11-08
> **rnerwein said:**
> hi
try: echo $TERM and have a look what kind of terminal is set if you login via ssh.
It says it's giving me xterm. That doesn't sound right, or is it?

---

### Post by rnerwein on 2012-11-08
> **jlacroix said:**
> It says it's giving me xterm. That doesn't sound right, or is it?

hi
yeah "xterm" must be ok
have a look at the .profile and .bashrc on the other system
look for: 
xterm-color) color_prompt=yes;;
#force_color_prompt=yes
......

---

### Post by pqwoerituytrueiwoq on 2012-11-08
restore the .profile file, that fixed it for me on xubuntu

---

### Post by jlacroix on 2012-11-08
> **pqwoerituytrueiwoq said:**
> restore the .profile file, that fixed it for me on xubuntu
Bingo! Thank you :)

---

### Post by Slim Odds on 2012-11-08
> **jlacroix said:**
> Bingo! Thank you :)
Yep, check those startup files.... good work.:)

---

