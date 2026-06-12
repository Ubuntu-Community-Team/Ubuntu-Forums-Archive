---
title: "bash completion question"
date: 2006-12-17
forum: General Help
---

### Post by reckless2k2 on 2006-12-17
I understand the <TAB> bash completion process but how do I set it up that as I'm typing in bash it fills in the line with commands from my history? 
Thanks.

---

### Post by maxamillion on 2006-12-17
Hit the up arrow key to scroll through the history buffer.

---

### Post by ayoli on 2006-12-17
another way to search history is to use CTRL+R

---

### Post by reckless2k2 on 2006-12-17
Thanks for the input guys but I am aware of these options. What I'm talking about is completely different and works like the "fill-in" feature in Firefox. I would start typing and it would fill in, accordingly to similar in the history, the completion of the commands. I know this is available but I don't know how to add the feature. At my workplace, they are using some shell that has this feature.

---

### Post by maxamillion on 2006-12-17
That is probably going to be a feature or plugin specific to the terminal emulator you are using because I highly doubt something as simple as xterm wouldn't be able to sport such a feature.

Of course I could be completely wrong and find out that it is in fact something that can be added to the personal bash config

---

### Post by medeski on 2006-12-17
Do you mean that the shell should autocomplete what you type without you having to press any extra keys, or that it should autocomplete commands when you hit TAB once?

If it's the former I have no clue, though ctrl-R kind of does that.  If the latter, you can create a file called .inputrc in your home directory with the following lines:
set show-all-if-ambiguous on
set show-all-if-unmodified on
set completion-ignore-case on  # if you don't want case-sensitivity

.inputrc will get read whenever you start a new bash process.

---

### Post by ayoli on 2006-12-17
i think i've found the trick. put in your ~/.inputrc file:
```
M- /: dynamic-complete-history
```
then when you type for ex ap in your shell, ALT+/ will complete ap with the command starting with ap that are in your history.
[http://www.gnu.org/software/bash/manual/bashref.html#SEC108](http://www.gnu.org/software/bash/manual/bashref.html#SEC108)

---

### Post by reckless2k2 on 2006-12-17
medeski - Your first explaination is exactly the functionality I was talking about. It will autocomplete based on bash history of commands typed as I'm typing similar to a fill-in feature in web browsers. As I'm typing, if the lines "fills" with what I want to do, then all I would do is hit enter.

I've seen this feature in action and it does not require more than typing and hitting enter if the string matches what you want to do. For instance:

I typed the following in a previous terminal session:

sudo nano /etc/apt/sources.list

When I open a new session and begin typing:

sudo nano 

It starts to fill with .........

as I continue typing so if I type /etc it'll fill in /apt/sources.list from my last session to that path. If this time I type /etc/ssh/...... it'll start filling that.

---

### Post by bodhi.zazen on 2006-12-17
I like this idea but it is not working.

current .inputrc:> set show-all-if-ambiguous on
set show-all-if-unmodified on
set completion-ignore-case on # if you don't want case-sensitivity
M- /: dynamic-complete-history

But I do not get any type of completion from my history.

Example: vim /etc/fstab:
> 
bodhi@Arch:~$vim /etc/fstab

[color=blue]This opens vim /etc/fstab. Close vim...[/color]

bodhi@Arch:~$vim [color=blue]<hits tab key>[/color]
vim       vimdiff   vimtutor

[color=blue]Alt / , Ctrl /, Alt tab, and Ctrl - tab all do nothing[/color]

Same results restarting the bash shell (terminal)

> bodhi@Arch:~$source .inputrc
bash: M-: command not found

So what gives ?

---

### Post by ayoli on 2006-12-17
actually after a little check i had to change a bit my inputrc, here it is:
```

#tab complete without needing to get the case right
set completion-ignore-case On 
#show list on first tab, no need to hit tab again
set show-all-if-ambiguous On 
# not sure what this one does...
set visible-stats On 
"\eh": dynamic-complete-history
```

restart your shell

then if i type in vim /etc/fstab that's open vim, i close it, then type in 
```
$ vim /etc/f[ALT+h]
/etc/firefox/firefoxrc  /etc/fstab
```
yeah, ive also edited firefoxrc before :)

---

### Post by bodhi.zazen on 2006-12-17
ayoli: Thank you :p

I do not have time right now, gotta ski :D

I'll try it later ...

---

### Post by bodhi.zazen on 2006-12-17
ayoli: Thanks, but that did not work. No error messages, but Alt-h acts the same as tab completion :(

---

### Post by ayoli on 2006-12-18
> **bodhi.zazen said:**
> ayoli: Thanks, but that did not work. No error messages, but Alt-h acts the same as tab completion :(
weird, here another exemple:
```
[18:52:55@ayoli.zone]:~ >$ sudo ap[alt+h]
apache     apt-cache  apt-get    aptitude   
[18:52:55@ayoli.zone]:~ >$ sudo ap[TAB]
apache2                  apmd                     apt                      aptitude
apache2ctl               apmsleep                 apt-cache                apt-key
apache2-ssl-certificate  appletviewer             apt-cdrom                apt-mark
aplay                    apport-retrace           apt-config               apt-sortpkgs
aplaymidi                apport-unpack            apt-extracttemplates     
apm                      appres                   apt-ftparchive           
apm_available            apropos                  apt-get  
```

---

### Post by medeski on 2006-12-18
reckless2k2,

I googled some yesterday for the answer to your question and didn't get too far.  If you find out what they use where you work, it would be cool if you could post it here.  It sounds like nice functionality  :)

If you have access on your work account to poke around  in directories like /etc, are there any relevant config files there?

---

### Post by reckless2k2 on 2006-12-18
I'm going to get on it and see what I can find out.

---

### Post by bodhi.zazen on 2006-12-18
> **ayoli said:**
> weird, here another exemple:

Hey, weird is my middle name:

bodhi.weird.zazen :p

At any rate, I started from scratch and it appears to be working, it is just, well a little weird to be honest.

I think I prefer Ctrl-R , type a partial command, Ctrl-R to search backwards, hit enter when I like what I see 8)

I will try this Alt-H and see how it goes.

Thanks for the tips :D

---

### Post by ayoli on 2006-12-19
> **bodhi.zazen said:**
> Hey, weird is my middle name:

bodhi.weird.zazen :p

At any rate, I started from scratch and it appears to be working, it is just, well a little weird to be honest.

I think I prefer Ctrl-R , type a partial command, Ctrl-R to search backwards, hit enter when I like what I see 8)

I will try this Alt-H and see how it goes.

Thanks for the tips :D

honnestly i think also i prefer ctrl+R to do history search, i tried to seaarch what the op was searchin and found that :p

---

