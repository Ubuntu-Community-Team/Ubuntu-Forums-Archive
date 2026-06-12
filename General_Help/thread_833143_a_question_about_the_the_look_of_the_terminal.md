---
title: "a question about the the look of the terminal"
date: 2008-06-18
forum: General Help
---

### Post by netwalkman on 2008-06-18
Is there a way to make the words just before '$' in gnome-terminal highlighted or slanted or something else, so that it become easier to locate the boundaries of the output.

---

### Post by beckols on 2008-06-18
in your terminal click edit -> current profile, and it will give you many options to customize your terminal.  There is a way to do it by command-line, but it is pretty complicated, and I can't find a bunch of good examples that I saw one time

EDIT: not the one I originally found, but this is an in-depth guide on Bash Prompt customization:
[http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/index.html]("http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/index.html")

---

### Post by drs305 on 2008-06-18
Using the command line can be as easy or difficult as you want to make it. For example, to change the prompt in your current profile, you can type:
```
 PS1="**prompt: **"
```
This will result in " prompt: " as your prompt. You can put anything you want within the quotes. For a more complicated entry:
```
PS1="${debian_chroot:+($debian_chroot)}\t \u@\h:\w\$ "
```
This results in: 11:55:14 username@hostname:~$

You get the idea. Doing the above will last only as long as you have that terminal open. To make it permanent, you have to edit your /etc/bashrc file.

For examples and instructions, here is a good site:
[http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html]("http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html")

---

