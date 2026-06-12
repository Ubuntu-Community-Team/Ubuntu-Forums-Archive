---
title: "Terminal/Bash Help"
date: 2007-12-21
forum: General Help
---

### Post by chrini on 2007-12-21
I'm not sure where the best place is to post this quesiton so I am posting it in general help...

I want to know how to change the font color of folders, files, etc in the Ubuntu terminal. Basically, I want to have different colors for the files and the folders so that they stand out just by glancing at it. Thanks.

---

### Post by andrewc6l on 2007-12-21
Take a look here:

[http://wiki.clug.org.za/wiki/Colour_on_the_command_line](http://wiki.clug.org.za/wiki/Colour_on_the_command_line)

---

### Post by chrini on 2007-12-21
I'm not sure I know which one will do what I want it to do.... they all sound like they have some special objective (as far as making something colorful in the terminal), but is there no way to do it in the preferences or anything???

Also, it seems like the first option on that page is probably the one I want, but what file do I edit and put the option in?

---

### Post by geirha on 2007-12-21
In ~/.bashrc you should find this line: ```
    eval "`dircolors -b`"
``` which will run the command "dircolors -b", and then run the output of that, which sets the LS_COLOR variable. (try running "dircolors -b" in a terminal).

Now, in a terminal run the following command which will dump the default configuration to a file called .dircolors in your home directory. ```
dircolors --print-database >~/.dircolors
```
Edit ~/.dircolors to your liking, then run ```
eval "`dircolors -b ~/.dircolors`"
``` and check the result with ls. If you're happy, change that line in ~/.bashrc to read 
```
    eval "`dircolors -b ~/.dircolors`"
```

---

