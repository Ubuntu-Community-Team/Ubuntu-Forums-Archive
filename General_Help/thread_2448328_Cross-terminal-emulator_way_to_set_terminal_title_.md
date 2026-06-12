---
title: "Cross-terminal-emulator way to set terminal title in bash/ksh script?"
date: 2020-08-05
forum: General Help
---

### Post by &amp;KyT$0P# on 2020-08-05
This code works in Konsole -
```
echo -e -n "\033]30;Custom Title\007"
```
But it doesn't work in xfce4-terminal, or any other terminal emulator that I've tried?  And I can't find a code that does?

How to have a bash/ksh script set terminal window title in a way that works across different terminal emulators?

---

### Post by kneutron on 2020-08-06
[https://unix.stackexchange.com/questions/358981/change-the-current-terminal-tab-title-inside-a-shell-script](https://unix.stackexchange.com/questions/358981/change-the-current-terminal-tab-title-inside-a-shell-script)

echo -e '\033]2;SomeTitle\007'


--Works in OSX High Sierra with builtin Terminal for me.  Doesn't work on Ubuntu 20.04 with gnome-terminal.  xfce4-terminal has a "set title" menu option/hotkey but that escape-code line doesn't work there either.


--You might try installing the ' wmctrl ' package and look at the man page, search for ' title '

--TBH (this might be outside the box for you) I never worry about my terminal title, I use GNU ' screen ' and put my stuff in the .screenrc init file.  That actually could be a more portable solution for you.

$ cat .screenrc
> 
hardstatus alwayslastline
hardstatus string '%{= kG}[ %{G}%H %{g}][%= %{=kw}%?%-Lw%?%{r}(%{W}%n*%f %t%?(%u)%?%{r})%{w}%?%+Lw%?%?%= %{g}][%{c}%Y-%m-%d %{W}%c %{g}]'
# cyan for non-root date = readability xxx 2020.0605
# color ref: [https://www.gnu.org/software/screen/manual/screen.html#String-Escapes](https://www.gnu.org/software/screen/manual/screen.html#String-Escapes)
# Default screens

screen -t shell1	0	/bin/bash
screen -t shell2	1	/bin/bash
screen -t shell3	2	/bin/bash


# switch back to 1st window
select 0


---

### Post by kneutron on 2020-08-07
--And also, don't forget you can always spawn another ' xterm -name blah & ' and **disown** on the original terminal, if you don't really need to change it on the fly.

---

### Post by &amp;KyT$0P# on 2020-08-07
> **kneutron said:**
> --You might try installing the ' wmctrl ' package and look at the man page, search for ' title '

Thanks kneutron, that *almost* solves this problem.  I can make it work if I run the script using a .desktop file with [FONT=Courier New]Terminal=true[/FONT], which is what I need now.  But there are two issues:

1) When I first open terminal then run the script from terminal, I haven't been able to get it to work, because I'm finding the terminal window ID based on looking for [FONT=Courier New]$PPID[/FONT] in [FONT=Courier New]wmctrl -l -p[/FONT] output.  I don't know how to get the parent PID of the parent PID, recursing until hitting a PID in the wmctrl list.  Is this a reasonable approach?  If so, how to "walk up the PID tree" to get the desired PID?

2) If I have multiple terminal windows open from the same terminal process, how to pick out only the terminal window running my script, to avoid changing title on unrelated terminal windows?

---

### Post by kneutron on 2020-08-07
> [COLOR=#000000]I don't know how to get the parent PID of the parent PID, recursing until hitting a PID in the wmctrl list. Is this a reasonable approach? If so, how to "walk up the PID tree" to get the desired PID?

--Try ' pstree ', you might have to awk the output

 > [/COLOR][COLOR=#000000]2) If I have multiple terminal windows open from the same terminal process, how to pick out only the terminal window running my script, to avoid changing title on unrelated terminal windows?

--Remember my ' xterm -name ' suggestion, you could launch the script with xterm -e and not have to worry about changing the title on the fly[/COLOR]

---

### Post by &amp;KyT$0P# on 2020-08-07
Thanks for your help kneutron!  I now got something good enough for me.

To sum up:

1) Take advantage of [FONT=Courier New]KONSOLE_VERSION[/FONT] environment variable to detect Konsole.  If using Konsole, just use the code in the OP.  Simple, straightforward, and nice.

2) Some terminal emulators (e.g. xfce4-terminal, mate-terminal, xterm, and also Konsole) set an environment variable [FONT=Courier New]WINDOWID[/FONT] , this can be converted to hex and used with [FONT=Courier New]wmctrl[/FONT].  Note that if [FONT=Courier New]wmctrl -l[/FONT] lists leading zeros for a window ID, it seems to need those passed back in when selecting a window by ID.

3) For terminal emulators that make a mess of [FONT=Courier New]WINDOWID[/FONT] (like QTerminal which always sets it to 0) or don't do [FONT=Courier New]WINDOWID[/FONT] at all, I'm stuck hoping there's one terminal window per terminal process and fall back to using
```
pstree -p -T -s "$PPID"
```
and
```
wmctrl -l -p
```
to make best guess of the window ID.


Note that (2) and (3) won't work if done too early, you might need to add some [FONT=Courier New]sleep[/FONT] in your code or otherwise find a way to wait for the terminal to be fully open.

Unfortunately with gnome-terminal none of these methods work reliably enough with gnome-terminal, but I primarily use Konsole and secondarily xfce4-terminal so this is fine for me for now.

---

### Post by HermanAB on 2020-08-07
Note that there are various ways to prettify scripts.  I prefer Zenity:
[https://www.aeronetworks.ca/2015/09/zenity-progress-dialogue.html](https://www.aeronetworks.ca/2015/09/zenity-progress-dialogue.html)

---

### Post by &amp;KyT$0P# on 2020-08-07
> **HermanAB said:**
> Note that there are various ways to prettify scripts.  I prefer Zenity:

Zenity is great for giving a script some GUI, I have some convenience scripts that use it similar to how that blog link describes.  But in this case adding GUI elements would not do the job.

---

### Post by &amp;KyT$0P# on 2020-08-08
> **halogen2 said:**
> But it doesn't work in xfce4-terminal, or any other terminal emulator that I've tried?  And I can't find a code that does?

Turns out I was at least in part blocked by my [FONT=Courier New].bashrc[/FONT] being a modification of standard Ubuntu bashrc, which contains this code -
```
# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac
```

The following code **does** momentarily change the terminal title in xfce4-terminal and mate-terminal -
```
echo -e -n '\033]0;Custom Title\007';sleep 5
```

I like the effect of the bashrc code, so I will still stick with the [FONT=Courier New]wmctrl[/FONT]-based solution.

---

