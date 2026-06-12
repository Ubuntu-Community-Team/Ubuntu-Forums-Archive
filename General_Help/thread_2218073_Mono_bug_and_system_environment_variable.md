---
title: "Mono bug and system environment variable"
date: 2014-04-19
forum: General Help
---

### Post by China Diapers on 2014-04-19
[FONT=arial]Hi, 

There's a known bug in Mono when porting Windows application to Linux to with back/fwd slashes and upper/lower case. There is an explanation on the Mono site here: [http://mono-project.com/IOMap](http://mono-project.com/IOMap), and it gives the solution as:

You have to type this, or include this in your script that launches your application:[/FONT]
    $ [COLOR=#7a0874]**export**[/COLOR] [COLOR=#007800]MONO_IOMAP[/COLOR]=all
    $ mono myapp.exe

[FONT=arial]So I understand if you are compiling via the command line, but what if I am compling from within the Mono IDE? 
Somebody suggested I may need to update the system environment variable on my system, I have googed this and read a few
pages but still no idea how I would go about it.[/FONT]

[FONT=arial]Anybody resolved this issue themselves, or have any idea how I go about resolving it?[/FONT]

---

### Post by coldcritter64 on 2014-04-19
> **China Diapers said:**
> [FONT=arial]...[/FONT][FONT=arial]Somebody suggested I may need to update the system environment variable on my system...[/FONT]

To do that open the file ~/.profile in your home directory, in a text editor, and add the line in the next code box to a new line at the end of the file. 
Use "ctrl + h" key combination in your home folder to show hidden files if you can't find ~/.profile (note, ~ is just an environment variable to represent your users home folder /home/<your-username>). 

```
export MONO_IOMAP=all
``` 
You will then need to log out of your desktop and log back in to activate the additional export command in ~/.profile.

After logging back into the desktop, open a terminal and run the next code to check,
```
echo $MONO_IOMAP
```
If set correctly the terminal will respond with "all" and then return to the prompt. 

Then you should be able to compile within the mono IDE and have it use that environment variable as well. 
Good luck with the bug squashing, coldcritter64. :)

---

