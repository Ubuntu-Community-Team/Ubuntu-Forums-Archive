---
title: "looking for terminal logger"
date: 2007-02-15
forum: General Help
---

### Post by blastradys on 2007-02-15
I've just started using linux and have just begun to get sexy and dirty with the terminal, so I'd like to keep my interactions with it logged and filed automatically so I can view them later, If there is a program available somewhere to do this, or if it can be enabled without anything else - I ask you.  

I understand history can be saved from within Konsole and Gnomes terminal emulator.   But that is not automatic.  

Also, I use Kuake and sometimes Konsole, so if there is a way to log each session from both emulators at a lower level, that'd be great. Thanks,

blastradys

---

### Post by tocleora on 2007-02-15
This would be a total workaround and not the smartest solution, but you could create a bash script that you call the bash script like:

script.sh [command]

where script.sh is the script and command is whatever you're wanting to call.  Then have the bash script log the command to a text file and then execute the command.  I don't know 100% this will work but if it's something you think would work for your situation I'll even go as far as to research the code for you if you need it.

---

### Post by ethan@xmlstandards.org on 2007-02-15
OK,

A bit of a newbie Linux user myself here, but I believe you can use a program called "script". It should be already installed upon a base installation and will allow you to recored your interactions with the terminal to a file (default is called "typescript"  think).

Have a look at the man pages (man script).

Hope that helps.

This is exactly what this program is intended for.

---

### Post by phork on 2007-02-15
An even better solution, install sudosh and fuggetaboudit.  If you use sudosh as your shell it will log your entire shell session, which you can play back EXACTLY as you saw it at a later date.  This replicates everything you saw (and you can change the playback speed).  So if you fired up nano and edited something, you will see nano in all of it's ncurses glory.  Not sure if ubuntu has a pre-made package for this these days, but it's a simple ./configure; make if not.

---

### Post by tocleora on 2007-02-16
Anyone else notice sudosh's screenshot says "Putty" at the top?  Isn't that a completely different program?

[http://sourceforge.net/projects/sudosh/](http://sourceforge.net/projects/sudosh/)

EDIT: nevermind. I see it's not a terminal app now.  Sorry. :)

---

