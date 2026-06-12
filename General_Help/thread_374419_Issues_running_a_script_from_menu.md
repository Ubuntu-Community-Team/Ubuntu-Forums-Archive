---
title: "Issues running a script from menu"
date: 2007-03-02
forum: General Help
---

### Post by NegativeSpace on 2007-03-02
Hi,

I downloaded an application which launches itself through a script. If I run the script from a terminal it runs perfectly well.

For convenience, I tried adding a menu item to run the script, but this didn't seem to work.

After a bit of investigating I found out what the problem was: the script requires a variable to be set to an already existing environment variable:
```
IDEA_JDK=$JDK_HOME
```
However, *JDK_HOME* was nothing. This is confusing since I added the line
```
export JDK_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.08
```
to my .bashrc file. Even more confusing is that, as I said earlier, if I run this script from a terminal, *JDK_HOME* is indeed *...sun-1.5.0.08*, and it runs perfectly well.

I can set *JDK_HOME* inside the script manually, but I am confused as to why, when the script is called from the menu, it can't see *JDK_HOME*, whereas from the terminal, it can.

If anyone can suggest why this happens I'd appreciate it.

Regards.

---

### Post by DavidHuttlestonJr on 2007-03-02
Snipped from the bash manpage:
       ~/.bash_profile
              The personal initialization file, executed for login shells
       ~/.bashrc
              The individual per-interactive-shell startup file
 The .bashrc file is _only_ read when launching an interactive shell.  If you put your JDK_HOME definition in the .bash_profile, you'll be all good.

---

### Post by kerry_s on 2007-03-02
Have you tried just making a script for the script.
Example:
gedit .myscript

#!/bin/sh

command i use in terminal

make executable-> chmod +x .myscript


Command for launcher-> /home/you/.myscript

---

### Post by NegativeSpace on 2007-03-02
Hi,

Thanks for your replies.

DavidHuttlestonJr: I tried what you said and, unfortunately, nothing changes. I read *man bash* and tried adding the JDK_HOME line to *bash.bashrc* to no avail, but to be honest I didn't entirely understand the explanation so it was more a shot in the dark.

kerry_s: I don't actually have a problem running the script if I modify it to declare ```
JDK_HOME=<dir>
``` inside the script itself, rather than trying to access it by *$JDK_HOME*. But I shouldn't **have** to declare JDK_HOME inside the script. I suspect, as DavidHuttlestonJr intimated, I need to export JDK_HOME somewhere other than *bashrc*. Unfortunately I don't know **where** or **why**.

Regards.

---

### Post by kerry_s on 2007-03-02
No, you don't need to modify anything, if as you say it runs "perfectly from the terminal"
just put the command you use in the terminal in the #!/bin/sh script and it's just like as if you ran it from terminal. then point your menu command at the script you just made that launches it.

---

### Post by RedSquirrel on 2007-03-02
> **NegativeSpace said:**
> Hi,

I downloaded an application which launches itself through a script. If I run the script from a terminal it runs perfectly well.

For convenience, I tried adding a menu item to run the script, but this didn't seem to work.

After a bit of investigating I found out what the problem was: the script requires a variable to be set to an already existing environment variable:
```
IDEA_JDK=$JDK_HOME
```However, *JDK_HOME* was nothing. This is confusing since I added the line
```
export JDK_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.08
```to my .bashrc file. Even more confusing is that, as I said earlier, if I run this script from a terminal, *JDK_HOME* is indeed *...sun-1.5.0.08*, and it runs perfectly well.

I can set *JDK_HOME* inside the script manually, but I am confused as to why, when the script is called from the menu, it can't see *JDK_HOME*, whereas from the terminal, it can.

If anyone can suggest why this happens I'd appreciate it.

Regards.

Put your export line in /etc/profile. See if that works.

** EDIT:**

On second thought, that probably won't help.

The problem is somewhat complicated. The thing is, when you log in using gdm, it doesn't source your .bashrc nor .bash_profile. 

There are a few ways around this, but off the top of my head, you could put your export line in ~/.bash_profile and then add something like

```
source ~/.bash_profile
```to the programs you want to run at startup. (In XFCE it's in Applications -> Settings -> Autostarted Applications; where it is in GNOME I can't recall...).

You could even put the export line itself in that list of programs that run at startup or you could make a script with the export line in it and put that in the list.... so many options.

Do let us know if it works. I'd play around with it some more but I'm afraid it's getting late and it's been a long day... must sleep...

---

### Post by NegativeSpace on 2007-03-03
RedSquirrel,

I added the export to *bash_profile* like you said, but wasn't quite sure why I should add the source line to each startup program. Incidentally, I'm not sure what source does, exactly (I'm a Linux newbie, I'm afraid). Well, I tried adding source to the script which wasn't working, but that didn't help.

However, that doesn't really matter because your first suggestion **does** work. Thanks!

I still don't know why it matters where the export line is added -- in */etc/profile* opposed to any *bash...* file, but at least I know now that I don't have to hard-code JDK_HOME inside the script!

Thanks again.

---

### Post by RedSquirrel on 2007-03-03
> **NegativeSpace said:**
> RedSquirrel,

I added the export to *bash_profile* like you said, but wasn't quite sure why I should add the source line to each startup program. Incidentally, I'm not sure what source does, exactly (I'm a Linux newbie, I'm afraid). Well, I tried adding source to the script which wasn't working, but that didn't help.

Sorry, my wording for putting that line in the list of startup programs wasn't clear. What I meant was that you'd just need to add ONE entry with that source command; you don't have to add it to EVERY program in the list of startup programs.

You would just create an entry for that line, call it "set-JDK_HOME" or something and then in the field that says 'command:' you would put

```
 source ~/.bash_profile
```> 
However, that doesn't really matter because your first suggestion **does** work. Thanks!
Yeah, I sort of thought after I'd logged out and moved on to other things that /etc/profile would apply to the whole environment and would work after all. :)

> 
I still don't know why it matters where the export line is added -- in */etc/profile* opposed to any *bash...* file, but at least I know now that I don't have to hard-code JDK_HOME inside the script!
It's kind of confusing, actually. :(

When you login using gdm, it doesn't access .bashrc because that's only used if you open a terminal  such as gnome-terminal, xfce4-terminal, or xterm. And .bash_profile is used if you login to a virtual console. (try Ctrl-Alt-F2 to go to a console and then press Ctrl-Alt-F7 to get back to your graphical environment) .bash_profile is setup (usually) to load .bashrc as well.

It is possible to set things up to access .bashrc and/or .bash_profile when you login using gdm, but leaving it the way it is (your variable set in /etc/profile) is fine.

---

