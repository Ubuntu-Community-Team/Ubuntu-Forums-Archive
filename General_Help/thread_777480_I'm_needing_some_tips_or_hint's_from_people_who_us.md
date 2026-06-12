---
title: "I'm needing some tips or hint's from people who use the terminal daily....."
date: 2008-05-01
forum: General Help
---

### Post by amyfan on 2008-05-01
hi i have been looking everywhere on the net and in the forums on some cool or fun things to do in the terminal in ubuntu.
also looking for a list of things like lspci and others like lsusb and any other little cool commands like that mainly with out sudo and if with sudo nothing that i have to mess with certain files.
thank you to who all reply to this....

---

### Post by amyfan on 2008-05-01
also if it matters any im on ubuntu gnome hardy.

---

### Post by Ramses de Norre on 2008-05-01
If you want practice, don't use a GUI file manager and text editor anymore.

---

### Post by kerry_s on 2008-05-01
while your at it, you might want to try some of the terminal filemanagers. mc, clex, vfu, etc...
try and replace the not so used programs with term equivalents.

i use a custom install, so i don't have much in the first place. on this install, im using clex for the file manager, vim for editor, rxvt for terminal, apt-get instead of gui, etc...

---

### Post by amyfan on 2008-05-01
kerry_s, cool but that looks like it is going over my head..

---

### Post by NullHead on 2008-05-01
you could always play with espeak. 

Example: ```
espeak my\ computer\ can\ talk\ to\ me!
```

---

### Post by -Zeus- on 2008-05-01
> **kerry_s said:**
> while your at it, you might want to try some of the terminal filemanagers. mc, clex, vfu, etc...
try and replace the not so used programs with term equivalents.

i use a custom install, so i don't have much in the first place. on this install, im using clex for the file manager, vim for editor, rxvt for terminal, apt-get instead of gui, etc...

Even something like mc is sort of cheating a little lol... if you want real hardcore you use mv, cp, cd, ls, that sort of stuff.  Not a graphical file manager packaged in a terminal.

RE the thread starter, you might want to try nano instead of vi if you haven't already.

---

### Post by retrow on 2008-05-01
```
sudo apt-get install htop
```
Then type 'htop'
That gives you a listing of processes and how much CPU/memory they are using in real time. "q' to quit.

To check which processes you are running
```
ps x
```
... and to search for a specific running process
```
ps x | grep process_name
for example:
ps x | grep firefox

```This gives you the process number on the right. That way whenever any program/process freezes your machine you can check the process number of that application and then run
```
kill process#
For example if you see that nautilus has frozen whose process number is 8980, run
kill 8980
```
Then there is always,```
fortune
```when you are totally and absolutely bored.

---

### Post by amyfan on 2008-05-01
thanks retrow and -Zeus- and kerry_s for those replies if there are any more please feel free to im me or simply post here..

---

### Post by y-lee on 2008-05-01
[A day without X]("http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/") :)

---

### Post by bodhi.zazen on 2008-05-01
1. Tab completion. Start typing a command or file name, hit the tab key. If there is more then one option, hit tab twice.

2. Command history. Type Control-R, start typing a recent command, hit enter to execute, Ctrl-R again to cycle through additional matches.

3. Set your own aliases , or short cuts for commands.

4. Add a function to .bashrc to extract archives.

> # Extract files from any archive
# Usage: ex <archive_name>

ex () {
     if [ -f $1 ] ; then
        case $1 in
                *.tar.bz2)   tar xjf $1        ;;
                *.tar.gz)    tar xzf $1     ;;
                *.bz2)       bunzip2 $1       ;;
                *.rar)       rar x $1     ;;
                *.gz)        gunzip $1     ;;
                *.tar)       tar xf $1        ;;
                *.tbz2)      tar xjf $1      ;;
                *.tgz)       tar xzf $1       ;;
                *.zip)       unzip $1     ;;
                *.Z)         uncompress $1  ;;
                *.7z)        7z x $1    ;;
                *)           echo "'$1' cannot be extracted via extract()" ;;
        esac
     else
        echo "'$1' is not a valid file"
     fi
}

# Thanks to rezza at Arch LinuxNow extract an archive with the command :

ex <archive>

Additional ideas :

[http://ubuntuforums.org/showthread.php?p=1698783](http://ubuntuforums.org/showthread.php?p=1698783)

[http://ubuntuforums.org/showthread.php?t=679762](http://ubuntuforums.org/showthread.php?t=679762)

Try a new shell. zsh :


[[IMG]http://www.cafelinux.org/OptickleArt/albums/userpics/thumb_xterm.png[/IMG]]("http://www.cafelinux.org/OptickleArt/albums/userpics/xterm.png")

Click on picture to see a screen shot of my login screen.

ZSH :

[http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/](http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/)
    [http://www.ibm.com/developerworks/linux/library/l-z.html?dwzone=linux](http://www.ibm.com/developerworks/linux/library/l-z.html?dwzone=linux)

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

---

### Post by amyfan on 2008-05-02
thanks everyone who replied those are some sweet things to mess around with.

---

### Post by amyfan on 2008-05-03
bump

---

### Post by upthelum on 2008-05-03
> **kerry_s said:**
> while your at it, you might want to try some of the terminal filemanagers. mc, clex, vfu, etc...
try and replace the not so used programs with term equivalents.

i use a custom install, so i don't have much in the first place. on this install, im using clex for the file manager, vim for editor, rxvt for terminal, apt-get instead of gui, etc...

How did you make Terminal text different colours?

---

### Post by kerry_s on 2008-05-03
> **upthelum said:**
> How did you make Terminal text different colours?

that's vim syntax. the default install is vim-tiny, it doesn't have syntax highlighting. you can install the regular vim(sudo apt-get install vim) or if you want everything, like the gui(gvim), grab vim-full. i don't use all that, so just regular vim is fine for me.

then create a .vimrc file with " syntax on ".
if you need to learn vim/vi it comes with a tutor. open a terminal and type-> vimtutor
good for if you need to learn or if you are just rusty, like i was. :)

my vimrc is simple.->

---

### Post by upthelum on 2008-05-03
> **kerry_s said:**
> that's vim syntax. the default install is vim-tiny, it doesn't have syntax highlighting. you can install the regular vim(sudo apt-get install vim) or if you want everything, like the gui(gvim), grab vim-full. i don't use all that, so just regular vim is fine for me.

then create a .vimrc file with " syntax on ".
if you need to learn vim/vi it comes with a tutor. open a terminal and type-> vimtutor
good for if you need to learn or if you are just rusty, like i was. :)

my vimrc is simple.->

I recently had to use vi so will learn more about vim, nice touch ta much....

---

### Post by kerry_s on 2008-05-03
> **upthelum said:**
> I recently had to use vi so will learn more about vim, nice touch ta much....

thanks, i added a few more options. i'm still reading the manual slowly. :) haven't used vi in at least 2 years, figured it was time for a refresh.

```
  1 syntax on
  2 set background=dark
  3 set viminfo=""
  4 set number
  5 set ignorecase
  6 set hlsearch
  7 set laststatus=2
  8 set ttyfast
  9 set statusline=%5(%)%F%m%r%h%w\ %5(%)Lines=%l\ of\ %L\ %5(%)Type=%Y\ %=%p%%

```

pic->

---

