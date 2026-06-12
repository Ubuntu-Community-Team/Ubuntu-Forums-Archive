---
title: "minimizing (terminal) window from command line"
date: 2014-03-31
forum: General Help
---

### Post by g999b on 2014-03-31
Hello,

Geek question be prepared...

I use Ubuntu and sometimes OSX. I took a stupid geek habit with OSX, I wrote a little command line script to be able to minimize my Terminal window with a command. I can do that fairly easily with OSX because I can invoke an AppleScript code directly from the command line with the command *osascript*. In real terms what does it mean? I dont need the mouse to minimize my term window, I type the name of my script and "swoosh" the term minimizes.

Sorry for the long intro, here comes my question: can I do the same with Ubuntu?

What I mean is, let's assume I am logged in, Gnome is launched, etc. I have an open Terminal window (inside Gnome), can I write a script that will actually minimize the terminal window (not close nor kill the window -> only minimize it)?

I am actually clueless bc. obviously I cannot use Apple script...

I dont even know what language I can use for the script (?), Bash will not be able to act on a window insode Gnome (maybe I am wrong, please correct me), I know a bit of Perl... but it does not seems like a Perl job at all...

Please let me know your perspective on this geek question, and if you have a hack -> that'd be great

Thanks

---

### Post by sudodus on 2014-03-31
Browsing the internet with the search string ***bash minimize window*** I found

```
xdotool windowminimize $(xdotool getactivewindow)
```

according to the tip in this link

[http://askubuntu.com/questions/318062/what-is-the-command-to-minimize-a-terminal](http://askubuntu.com/questions/318062/what-is-the-command-to-minimize-a-terminal)

You can make an alias of it, for example

```
alias min='xdotool windowminimize $(xdotool getactivewindow)'
```

that you enter into your **~/.bashrc** file and after that it will be enough to type

```
min
```

to minimize the window.

---

### Post by g999b on 2014-03-31
Absolutely brilliant ! worked like a charm, thank you Sudodus!

---

### Post by steeldriver on 2014-03-31
fyi I think you can actually chain the 2 xdotool commands in one (instead of running xdotool twice)

```
xdotool getactivewindow windowminimize
```

---

