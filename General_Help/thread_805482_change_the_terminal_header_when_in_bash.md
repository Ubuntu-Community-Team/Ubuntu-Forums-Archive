---
title: "change the terminal header when in bash"
date: 2008-05-24
forum: General Help
---

### Post by Sava on 2008-05-24
hello,

I've been looking for a way to change the terminal's header when switching into bash. For example, at my school, **after type bash, the header shows bash-2.05b$ instead of the path**

> 
[alpha] [/winhome/q/q_ng] > dir
Crimson        
EditPlus       
IE             
Jbuilder2006   
Mozilla        
My\ Documents  
**[alpha] [/winhome/q/q_ng] > bash**
**bash-2.05b**$ lpq -P nib
nib is ready
no entries
bash-2.05b$ 


> 
**[alpha] [/winhome/q/q_ng] > bash**

changes to this:

> 
**bash-2.05b**

Does anybody know which file should I look into? I'm running Gutsy Gibbon.

Thanks in advance,


PS: I have this customization ( [http://ubuntuforums.org/showthread.php?t=674446](http://ubuntuforums.org/showthread.php?t=674446) ) applied, but it looks like .bashrc is not the file I need to look at.

---

### Post by angry_johnnie on 2008-05-24
Editing .bashrc, maybe?

It would be /home/you/.bashrc

Find PS1=something-something-something

and change it.

Here's an example of a color prompt:

PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

Mine, for instance, doesn't show \u@\h\ (user @ host).
It just says something rather silly :-), and then prints \w\$ (working-directory$)

---

### Post by mali2297 on 2008-05-24
In the hidden file **.bashrc** in your home directory, add the following line:
```

export PS1="\s-\v\$ "

```

You do realize that bash is started by default when you open a terminal in Ubuntu, don't you?

---

### Post by Sava on 2008-05-24
> **Sava said:**
> 
PS: I have this customization ( [http://ubuntuforums.org/showthread.php?t=674446](http://ubuntuforums.org/showthread.php?t=674446) ) applied, but it looks like .bashrc is not the file I need to look at.


:D thanks guys, but it seems nobody read this quote i wrote

in my ~/.bashrc, I do have this:

> 
PS1='\[\e[1;33m\]{\u}~>[\W]\[\e[m\] '

which results in displaying:

> [b]{sava}~>[~] gedit .bashrc

{sava}~>[Desktop] pwd
/home/sava/Desktop
{sava}~>[Desktop] cd Downloaded/
{sava}~>[Downloaded] 


which is great. But if I type in "bash", to be able to run command like this:

> while [ 1 ]; do clear; lpq -P chalk; sleep 15; done

and what not, it's still showing:

> 
{sava}~>[Downloaded] bash
**[COLOR="Red"]{sava}~>[Downloaded][/COLOR]** while [ 1 ]; ps -u sava | grep firefox; sleep 15; done 
bash: syntax error near unexpected token `done'
{sava}~>[Downloaded] while [ 1 ]; do clear; ps -u sava | grep firefox; sleep 15; done 


instead of 

> **[COLOR="Red"]bash-2.0.5b[/COLOR]** while [ 1 ]; ps -u sava | grep firefox; sleep 15; done 


:D sorry for my limited knowledge of Linux, hope it's clear now

help, anyone?

---

### Post by mali2297 on 2008-05-24
As I said, bash starts when you open a terminal window. There is no point in typing bash, just type in your command sequence directly.

---

### Post by Sava on 2008-05-24
ahh, ic. I guess it must 've been diff from me school, running Fedora 6.

thnx guys,

---

