---
title: "Specific name for Terminal Command"
date: 2016-06-21
forum: General Help
---

### Post by SnuKies on 2016-06-21
Hello,


I have a question : is it possible to set an alias for a specific command ? ( I really did not know how to search this on google ).

For example, when I want to forcily turn off my screen, I type "xset dpms force off". But would it be possible to instead, just type : "turn off screen " as an alias for that command and turn off my screen ?

I do not want a button to do this, just to type it in my Terminal.



I'm thankful for any help provided.
Thanks.

---

### Post by &amp;KyT$0P# on 2016-06-21
for bash/ksh, add a line like this in configuration:
```
alias turnoffscreen='xset dpms force off'
```

---

### Post by SnuKies on 2016-06-21
Wow! Thank you very much !!! 

And if I want to remove this alias ? :)

---

### Post by &amp;KyT$0P# on 2016-06-21
Just delete it from the configuration file and restart your shell

---

### Post by SnuKies on 2016-06-21
Thank you very much for your help, halogen2 !:)

---

### Post by &amp;KyT$0P# on 2016-06-21
You're welcome :KS

(If this is resolved to your satisfaction, please use Thread Tools > "Mark this thread as solved...")

---

### Post by SnuKies on 2016-08-16
Okey, I'm writting back after a long time ....
I forgot to reply then, but I'll reply now: after I restart my laptop, the alias does not work anymore. I have to retype it.
Anyone knows why?

---

### Post by howefield on 2016-08-16
> **SnuKies said:**
> ... after I restart my laptop, the alias does not work anymore. I have to retype it.

Did you add the line to your ~/.bashrc file ?

---

### Post by SnuKies on 2016-08-16
> **howefield said:**
> Did you add the line to your ~/.bashrc file ?

I only put that in the terminal. As a newbie when it comes to Linux, could you expand your answer?

---

### Post by howefield on 2016-08-16
> **SnuKies said:**
> I only put that in the terminal. As a newbie when it comes to Linux, could you expand your answer?

Sure, for your alias to persist between reboots, you'll need to add it to your ~/.bashrc file. Eg, one of my aliases is "*alias sens="sensors | grep "Fan" | cut -d ":" -f 2"*", - to add it to the ~/.bashrc file, simply load up Files (Nautilus) which should open at your /home folder, press Ctrl  + h keys to see hidden files (those which start with a period) and scroll down to the .bashrc file. Double clicking that file should bring it up in your default text editor.

Simply append the alias to a new line at the bottom of that file, save and close out. Restart any terminals you have open.

Or if you prefer the command line, something like..

```
echo alias sens="sensors | grep "Fan" | cut -d ":" -f 2" >> ~/.bashrc
```

would append the line to the bottom of the file.

---

### Post by SnuKies on 2016-08-16
> **howefield said:**
> Sure, for your alias to persist between reboots, you'll need to add it to your ~/.bashrc file. Eg, one of my aliases is "*alias sens="sensors | grep "Fan" | cut -d ":" -f 2"*", - to add it to the ~/.bashrc file, simply load up Files (Nautilus) which should open at your /home folder, press Ctrl  + h keys to see hidden files (those which start with a period) and scroll down to the .bashrc file. Double clicking that file should bring it up in your default text editor.

Simply append the alias to a new line at the bottom of that file, save and close out. Restart any terminals you have open.

Or if you prefer the command line, something like..

```
echo alias sens="sensors | grep "Fan" | cut -d ":" -f 2" >> ~/.bashrc
```

would append the line to the bottom of the file.

Many thanks! 
Unfortunately, I'm not able to do it right now (I'm currently at work) but I'll come back later, at night, with an answer (If it worked, or not).

OffTopic: What does your script do?

---

### Post by howefield on 2016-08-16
> **SnuKies said:**
> Many thanks! 
Unfortunately, I'm not able to do it right now (I'm currently at work) but I'll come back later, at night, with an answer (If it worked, or not).

OffTopic: What does your script do?

You are welcome.

Off topic : It runs an application called sensors, I am only interested in the fan speed, so the commands runs the application, looks for the line with the word Fan in it and outputs the fan speed to the screen. So.. instead of 

```
hugh@xenial:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +59.5°C  (crit = +102.0°C)

radeon-pci-0100
Adapter: PCI adapter
temp1:        +68.5°C  (crit = +120.0°C, hyst = +90.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +60.0°C  (high = +95.0°C, crit = +105.0°C)
Core 2:       +57.0°C  (high = +95.0°C, crit = +105.0°C)

dell_smm-virtual-0
Adapter: Virtual device
Processor Fan: 2880 RPM
CPU:            +59.0°C  
GPU:            +63.0°C  
Other:          +70.0°C  

hugh@xenial:~$ 
```

I get..

```
hugh@xenial:~$ sens
 2920 RPM
hugh@xenial:~$
```

---

### Post by vasa1 on 2016-08-16
Just to supplement howefield's response ...

You can alternatively store aliases you create in *~/.bash_aliases*. As the "." indicates, this file, like *.bashrc* is a hidden file and you'd need to enable viewing hidden files in your file manager to see it. It may not be present by default, unlike *~/.bashrc* which is.

The syntax is the same as what you'd use in *~/.bashrc* and so your *~/.bash_aliases* file will just be a list of aliases you've created.

Part of my *~/.bash_aliases* looks like this:```
alias pg='ping -c3 www.google.com'
alias mysoft='dpkg --get-selections | grep -v deinstall > ~/Desktop/installed-software'
alias ppp='ps -o pid,ppid,stime,time,command -u $USER'
# or the one below with -H if you want a "tree"
#alias ppp='ps -o pid,ppid,stime,time,command -H -u vasa1'

alias de='cd ~/Desktop'
alias zzz='cd ~/a-ztemp/zzz'

# MF
alias axismf='qpdf --password=.......... --decrypt temp.pdf axis.pdf'

alias p2t='pdftotext -nopgbrk -layout axis.pdf axis.txt'
alias sc1='/usr/share/pyshared/scour.py --remove-metadata --set-precision=3 -i in.svg -o out.svg'
alias rmtn='rm -rf /home/vasa1/.thumbnails'
alias myxprop='xprop | grep -E "_OB_APP"'
```As you can see, the order isn't important, you can have comments and blank lines.

There are some useful commands relating to aliases for when you're in a terminal.

**alias** lists aliases alphabetically and excludes comments and blank lines. You'll see the aliases present in *~/.bashrc* and those in *~/.bash_aliases*.

**alias myxprop** reproduces the line corresponding to that particular alias.

**type myxprop** will tell me that "myxprop" is an alias and what it stands for. This is useful *before* assigning an alias to a command.

---

### Post by howefield on 2016-08-16
Cool, thanks vasa1.

Nice read.

---

### Post by SnuKies on 2016-08-16
So I used the command and got the following error.

```
bash: alias: dpms: not foundbash: alias: force: not found
bash: alias: off: not found
bash: alias: dpms: not found
bash: alias: force: not found
bash: alias: off: not found
alex@alexPC:~$ echo alias turnoffscreen="xset dpms force off" >> ~/.bashrc
```

But if I try something like ```
alias turnoffscreen='xset dpms force off'
``` it works. Also, I opened my Home folder, pressed Ctrl + H and I see no .bashrc file. ( I just upgraded to 16.04 from 14.04. Could this be a problem? :\)

---

### Post by &amp;KyT$0P# on 2016-08-16
> **SnuKies said:**
> So I used the command 
Which command?  This?
```
echo alias turnoffscreen="xset dpms force off" >> ~/.bashrc
```

If that one, I think that will make a mess of your bashrc as the shell will remove the quotation marks.  Should be this:
```
echo 'alias turnoffscreen="xset dpms force off"' >> ~/.bashrc
```

So run in a Terminal,
```
gedit ~/.bashrc
```
(replacing gedit with your preferred text editor, if different)
and from there manually cleanup the offending line.

> and got the following error.
When are you seeing those errors, on bash startup or trying to use the alias?

---

### Post by SnuKies on 2016-08-28
I'm sorry for the very late reply, but we've started renovating :D And it's little time that I have left...

OnTopic: Done. Thank you all, guys.

---

