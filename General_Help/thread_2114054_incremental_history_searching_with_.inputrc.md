---
title: "incremental history searching with .inputrc ?"
date: 2013-02-09
forum: General Help
---

### Post by coldraven on 2013-02-09
I have previously followed the advice here and it worked fine but I just tried it and now I get  errors. This is a new install of Kubuntu 12.04

[http://codeinthehole.com/writing/the-most-important-command-line-tip-incremental-history-searching-with-inputrc/](http://codeinthehole.com/writing/the-most-important-command-line-tip-incremental-history-searching-with-inputrc/)

I put the four lines into .bashrc then reloaded bash with the source command

```

"\e[A": history-search-backward
"\e[B": history-search-forward 
"\e[C": forward-char 
"\e[D": backward-char

```
```
coldraven@happy:~$ source ~/.bashrc
\e[A:: command not found
\e[B:: command not found
\e[C:: command not found
\e[D:: command not found

```Any ideas why it is not working?
Maybe it is too early in the morning to be doing this :)

---

### Post by suraj5989 on 2013-02-09
Looks like You need to add the entries to inputrc file not bashrc.
/etc/inputrc
or
~/.inputrc
inputrc contains the keyboard mapping config.
Not sure how to make it work by adding to bashrc file.
Hope this helps :)

---

### Post by zillah on 2013-02-09
Hi
Having similar issue

Regards

---

### Post by coldraven on 2013-02-09
> **suraj5989 said:**
> Looks like You need to add the entries to inputrc file not bashrc.
/etc/inputrc
or
~/.inputrc
inputrc contains the keyboard mapping config.
Not sure how to make it work by adding to bashrc file.
Hope this helps :)

I did try putting the lines into .inputrc . I had to create the file as it did not exist in my home directory before. That did not work.
I am fairly certain that I previously added the lines to .bashrc and it worked OK.
When it does work it is  really useful, you can find old commands in seconds.

---

### Post by suraj5989 on 2013-02-09
> I did try putting the lines into .inputrc . I had to create the file as  it did not exist in my home directory before. That did not work.

I tried this by copying the file present in /etc/inputrc to my home directory'.inputrc' and then adding the entries.
> # /etc/inputrc - global inputrc for libreadline
# See readline(3readline) and `info rluserman' for more information.

# Be 8 bit clean.
set input-meta on
set output-meta on

# To allow the use of 8bit-characters like the german umlauts, uncomment
# the line below. However this makes the meta key not work as a meta key,
# which is annoying to those which don't need to type in 8-bit characters.

# set convert-meta off

# try to enable the application keypad when it is called.  Some systems
# need this to enable the arrow keys.
# set enable-keypad on

# see /usr/share/doc/bash/inputrc.arrows for other codes of arrow keys

# do not bell on tab-completion
# set bell-style none
# set bell-style visible
#"\e[A": history-search-backward
#"\e[B": history-search-forward 
#"\e[C": forward-char 
#"\e[D": backward-char
[B]"\e[A": history-search-backward
"\e[B": history-search-forward
"\e[C": forward-char
"\e[D": backward-char[/B]
# some defaults / modifications for the emacs mode
$if mode=emacs

# allow the use of the Home/End keys
"\e[1~": beginning-of-line
"\e[4~": end-of-line

# allow the use of the Delete/Insert keys
"\e[3~": delete-char
"\e[2~": quoted-insert

# mappings for "page up" and "page down" to step to the beginning/end
# of the history
# "\e[5~": beginning-of-history
# "\e[6~": end-of-history

# alternate mappings for "page up" and "page down" to search the history
# "\e[5~": history-search-backward
# "\e[6~": history-search-forward

# mappings for Ctrl-left-arrow and Ctrl-right-arrow for word moving
"\e[1;5C": forward-word
"\e[1;5D": backward-word
"\e[5C": forward-word
"\e[5D": backward-word
"\e\e[C": forward-word
"\e\e[D": backward-word

$if term=rxvt
"\e[8~": end-of-line
"\eOc": forward-word
"\eOd": backward-word
$endif

# for non RH/Debian xterm, can't hurt for RH/Debian xterm
# "\eOH": beginning-of-line
# "\eOF": end-of-line

# for freebsd console
# "\e[H": beginning-of-line
# "\e[F": end-of-line

$endif

It worked for me.
Thank you for this example [coldraven]("http://ubuntuforums.org/member.php?u=993657").:)

---

### Post by coldraven on 2013-02-15
suraj5989, I'm glad it is working and thanks for reminding me where inputrc is located.
I have been very busy with other matters and now I want to do a fresh install on my machine so I will be using this method as soon as possible.
It is very useful, is it not?

---

### Post by Habitual on 2013-02-15
> **coldraven said:**
> I have previously followed the advice here and it worked fine but I just tried it and now I get  errors. This is a new install of Kubuntu 12.04

[http://codeinthehole.com/writing/the-most-important-command-line-tip-incremental-history-searching-with-inputrc/](http://codeinthehole.com/writing/the-most-important-command-line-tip-incremental-history-searching-with-inputrc/)

I put the four lines into .bashrc then reloaded bash with the source command

```

"\e[A": history-search-backward
"\e[B": history-search-forward 

I have done the same but my notes (.bashrc) has these 2 entries:
[CODE]bind '"\e[A": history-search-backward'
bind '"\e[B": history-search-forward'
```I don't know jack about .inputrc, but I do know that I don't see the 'bind' keyword in your history search entries.

and of course, ```
source ~/.bashrc 
```

---

### Post by stinkeye on 2013-02-16
I think all those ways should work if done properly.

If you don't mind the setting being system wide and binding to pageup/down keys,
the setting already exists in /etc/inputrc and just needs to be uncommented.

gksudo gedit /etc/inputrc
> # **alternate** mappings for "page up" and "page down" to search the history
"\e[5~": history-search-backward
"\e[6~": history-search-forward

---

### Post by sidney-harrell on 2014-02-07
Once you've added those lines to ~/.inputrc you need to close your terminals and reopen them. Then the change to ~/.inputrc will take effect.

---

