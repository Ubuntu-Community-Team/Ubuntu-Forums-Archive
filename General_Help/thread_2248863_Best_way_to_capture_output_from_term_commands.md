---
title: "Best way to capture output from term commands?"
date: 2014-10-17
forum: General Help
---

### Post by loren41 on 2014-10-17
What is the best way to cut and paste multi-page terminal command output for delivery to the Forum?  I am currently using xterm in ubuntu 14.04.  Better terminal suggestions are welcome.

---

### Post by Iowan on 2014-10-17
You can redirect the output and attach it as a file.
```
 less /etc/network/interfaces > output.txt
```
[ATTACH]257304[/ATTACH]

There's a better way mentioned around here somewhere that pastes the content of the file - we strongly urge the use of **code** tags.

---

### Post by matt_symes on 2014-10-17
Hi

> **loren41 said:**
> What is the best way to cut and paste multi-page terminal command output for delivery to the Forum?  I am currently using xterm in ubuntu 14.04.  Better terminal suggestions are welcome.

I've used gnome-terminal and xfce4-terminal recently and you can set the scrollback size with them.

You can use the script command.

```
man script
```

Pastebin for long commands and post the url only.

```
man pastebinit
```

You can also use screens scroll back mode and screen is great anyway.

```

sudo apt-get install screen
man screen
```

> 
C-a [
C-a C-[
C-a esc     (copy)        Enter copy/scrollback mode.
 

Along with Iowan's redirection suggestion, that should give you a number of options.

Kind regards

---

### Post by jamesisin on 2014-10-17
You can also use the bash redirections with either > or >> depending if you want to replace or append.

```
ls / >> ~/Desktop/file.txt
```

---

### Post by papibe on 2014-10-17
Hi loren41.
> **loren41 said:**
> Better terminal suggestions are welcome.
The default desktop terminals are much mouse and shortcut-keyboard friendly.

If you are using regular Ubuntu, I'd recommend gnome-terminal. If you got Xubuntu, xfce4-terminal should do the work. And so on.

All of them support:
[LIST]
[*]mouse selection, right-click menu for easy copy/paste.
[*]scroll back using the mouse wheel, or the page_up, and page_down keys, so you can select text that was printed and scroll out of the screen.
[*]Switching from fullscreen to regular window by pressing F11, thus allowing more text to be copied.
[/LIST]
If you are looking for a nice, cool, that works fairly the same in all desktops, I recommend taking a look at 'terminator'.

Just my thoughts. Hope it helps.
Regards.

---

### Post by loren41 on 2014-10-18
Thanks for all your suggestions.  Good, quick assistance.
Loren41

---

### Post by Habitual on 2014-10-18
terminator has a logging feature.

---

### Post by nerdtron on 2014-10-18
> **Habitual said:**
> terminator has a logging feature.

Does it logs everything? I can't find this on my terminator installed.

---

### Post by Habitual on 2014-10-18
> **nerdtron said:**
> Does it logs everything? I can't find this on my terminator installed.

Seems to. I have one running now and I'll leave open for a few days (what else is new?)

I'll update this Monday with the result.

Right Mouse click in any terminator pane and select "Start Logger" and name it and go.

```
terminator -v
```
terminator 0.97

---

### Post by nerdtron on 2014-10-18
Lower version on mine.
$ terminator -v
terminator 0.95


I guess it only records the commands on my local machine and not the commands on the remote machine I am ssh into?

---

### Post by Habitual on 2014-10-19
> **nerdtron said:**
> Lower version on mine.
$ terminator -v
terminator 0.95


I guess it only records the commands on my local machine and not the commands on the remote machine I am ssh into?

Seems to recording everything on the screen here, local and remote. I type it and terminator logs it.

---

### Post by Habitual on 2014-10-20
> **nerdtron said:**
> Lower version on mine.
$ terminator -v
terminator 0.95


I guess it only records the commands on my local machine and not the commands on the remote machine I am ssh into?

terminator 0.97 captures everything local and remote.
No escape sequences or anything. All text as seen on the terminal.

---

### Post by nerdtron on 2014-10-20
I'm stuck on 0.95 as I use it on a centos machine, can't update manually either since it 0.97 needs python2.7 which also isn't yet updated on my package list.
0.95 don't have any recording options, in the right-click menu or in the preferences :(

---

