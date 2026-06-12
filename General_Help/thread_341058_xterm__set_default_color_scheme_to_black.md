---
title: "xterm : set default color scheme to black"
date: 2007-01-18
forum: General Help
---

### Post by Littleweseth on 2007-01-18
G'day;

I use xterm for all my terminal needs, but recently I've been getting more and more irked that my xterm displays black-on-bright text. This is mainly annoying because when you go to do something like ls on a directory containing executables, the lime green is nearly indistinguishable from the background.

How do I change to the default, sane black-backgrounded xterm and make it stay that way? At the moment, the terminal colour seems to change as a function of my gnome theme. :|

---

### Post by po0f on 2007-01-18
Littleweseth,

Edit ~/.Xresources to contain the following (if it doesn't exist, create it):
```
[FONT="Courier New"]xterm*foreground: white
xterm*background: black[/FONT]
```

Then, Alt+F2 and run this command:
```
[FONT="Courier New"]xrdb ~/.Xresources[/FONT]
```

Open a new terminal.

---

### Post by kerry_s on 2007-01-18
Here's the .Xresource for xterm-> [http://www.xfce.org/various/Xresources.txt](http://www.xfce.org/various/Xresources.txt)

---

### Post by Littleweseth on 2007-01-18
po0f : worked perfectly :)

kerry_s : i dumped that text into my .Xresources and tried to start an xterm; I get this;

```
lws@daedalus:~$ xterm
Warning: Cannot convert string "/usr/share/pixmaps/gnome-gemvt.xbm" to type Pixmap
Warning: Cannot convert string "/usr/share/pixmaps/gnome-gemvt-mask.xbm" to type Pixmap
xterm:  unable to open font "", trying "fixed"....
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  70 (X_PolyFillRectangle)
  Resource id in failed request:  0x0
  Serial number of failed request:  80
  Current serial number in output stream:  84

```

I'm guessing that's actually a 'lbank template' and I'm supposed to go fill in the blanks? :p

While we're here... can I get gentoo-like terminal coloring? I.e. root prompt is red, user prompt is blue, that kind of niceness.

tyvm;
-lws

---

### Post by kerry_s on 2007-01-18
I just use the right click> save page as, then just rename it to .Xresources. Here's what mine looks like.->

---

### Post by po0f on 2007-01-18
Littleweseth,

In ~/.bashrc:
```
[FONT="Courier New"]PS1="**\[\033[1;34m\]**[\u@\h:\w]\$**\[\033[00m\]** "[/FONT]
```
for blue.
Switch the first bolded part to \[\033[1;31m\] to get a red prompt.  The second bolded part is needed to reset the terminal font coloring.

In my ~/.bashrc, I actually have colors defined as variables, it makes it easier to scan:
```
[FONT="Courier New"]BLUE="\[\033[1;34m\]"
GREEN="\[\033[1;32m\]"
RED="\[\033\[1;31m\]"
RESET="\[\033[00m\]"

PS1="${BLUE}[color="blue"]**[**[/color]${GREEN}[color="green"]**\u@\h:\w**[/color]${BLUE}[color="blue"]**]**[/color]${RED}[color="red"]**\$**[/color]${RESET} "
[/FONT]
```

(Added the colors so you could visually see what would be changed.)

Note: \u is for user, \h is for hostname, \w is for current working directory, and \$ is the prompt ("$" for a regular user, "#" for root).

Want more, just ask.  :)

[Reference](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html).

---

### Post by Littleweseth on 2007-01-19
Thanks, that reference was good reading :)

---

