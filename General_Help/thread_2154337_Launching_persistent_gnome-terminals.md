---
title: "Launching persistent gnome-terminals"
date: 2013-06-14
forum: General Help
---

### Post by Mahler122 on 2013-06-14
Hi,

I'm trying to launch a new gnome terminal which will execute a bash command and when that command exits, will return to the bash interactive command line as if I had typed that command myself. I then want to be able to press the up arrow and retrieve the command executed. essentially I have been trying gnome-terminal -e 'bash command' type commands to get gnome-terminal to launch a new terminal which executes the command like I mentioned. The bash commands I've been trying are

```
bash -c 'command'
```

would have been perfect, except that this launches a non-interactive terminal which exits as soon as the command finishes.

```
bash -s -c 'command'
```
or
```
bash -i -c 'command'
```

don't work either since it seems that the -c option overrides the -s and -i options.

I also tried piping the command to the command line like:

```
echo "command" | bash -i
```

But this doesn't quite work either, because bash automatically submits the command 'exit' after 'command' finishes.

Finally, I found the following stack overflow entries which look promising.

[http://stackoverflow.com/questions/7192575/run-bash-command-in-new-shell-and-stay-in-new-shell-after-this-command-executes](http://stackoverflow.com/questions/7192575/run-bash-command-in-new-shell-and-stay-in-new-shell-after-this-command-executes)
[http://stackoverflow.com/questions/8784657/make-bash-run-a-command-right-after-it-starts-and-then-stay-in-this-session](http://stackoverflow.com/questions/8784657/make-bash-run-a-command-right-after-it-starts-and-then-stay-in-this-session)

These suggestions actually work if you execute the bash command in the same terminal and aren't launching a new terminal with gnome-terminal! This behaviour is what I want, except somehow the string is getting mangled when I pass the command to gnome-terminal for execution.

For instance executing

```
bash --rcfile <(echo ". ~/.bashrc && command")
```

in a terminal gives the expected behaviour.

However

```
gnome-terminal -e 'bash --rcfile <(echo ". ~/.bashrc && command")'
```

fails because it's actually looking for a file instead of using the output of the echo command. I assume this is because of some bash string mangling which I can't figure out how to undo. Literally every combination of quotes and escapes of suspect characters I've tried seems to end in failure. For example:

```
gnome-terminal -e 'bash --rcfile <(echo ". ~/.bashrc && ls")'
```

gives:

```
bash: . ~/.bashrc && ls): No such file or directory
```

Can somebody explain how I can unmangle the string I'm passing to gnome-terminal, or tell me a better way I can do this? Thanks a lot for any help!

---

### Post by Mahler122 on 2013-06-25
bump, I still haven't found a solution to this.

---

### Post by HiImTye on 2013-06-25
why not do something like```
cp -f ~/.bashrc ~/.bashrc.tmp
echo "command -arg1 -arg2" >> ~/.bashrc.tmp
gnome-terminal -e 'bash --rcfile ~/.bashrc.tmp'
```
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by Mahler122 on 2013-06-26
Well, I've got something working, but at the cost of a special rc file for each command I want to launch.

The rcfile with the command at the end wasn't enough to get the desired functionality. I had to add a command 'history -s "command"' before launching the command in question so that if I close the running program with Ctrl-C or the program crashes, I can press 'up' to get that command back immediately. I then can fill a script with stuff like this:

gnome-terminal \
--tab -e "bash --rcfile /path/to/rcfile1" \
--tab -e "bash --rcfile /path/to/rcfile2" \
.
.
.
etc

where reach rcfile contains a specific command with a history command, after the usual .bashrc file.

I liked the method I started out with though because I don't have to deal with extra rc files or temporary files hanging around.

Thanks for the suggestion!

---

### Post by HiImTye on 2013-06-26
just make a bash script
```
#!/bin/bash
cp -f ~/.bashrc ~/.bashrc.tmp
echo "$*" >> ~/.bashrc.tmp
gnome-terminal -e 'bash --rcfile ~/.bashrc.tmp'
```
put the script somewhere in your path (I use ~/Launchers) and name it what you want to type to launch your command (it doesn't need the .sh extension). then just call it like```
scriptName command -arg1 -arg2 -arg3 -etc
```
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

