---
title: "launcher"
date: 2004-11-17
forum: General Help
---

### Post by viorel on 2004-11-17
I've got some programs that run perfectly from the terminal. I just don't find it that handy to start the terminal and launch my program form there everytime. I created a launcher on my desktop that should start a program (in this case matlab) in the terminal. The command is: 
```
gnome-terminal -e matlab
``` 
The launcher opens the terminal and the matlab spash appears. After matlab is done loading, the terminal closes and so does matlab. I'm guessing I have to keep the terminal open after launching. So my question is: how do I do that? Or how can i launch a program (like matlab) from a desktop-launcher?

---

### Post by viorel on 2004-11-17
I understand it might be a kinda stupid question, but could somebody take the time to answer it? Thanks!

---

### Post by piedamaro on 2004-11-17
It should work, I don't have matlab installed tho. (I've tried with top and it works).

---

### Post by viorel on 2004-11-17
[QUOTE=piedamaro]It should work, I don't have matlab installed tho. (I've tried with top and it works).[/QUOTE]
 Did you do it in the same way I did?

---

### Post by dataw0lf on 2004-11-17
Try a
 ```
nohup metlab &
``` 
The 'nohup' stands for 'No Hang Up'; when a terminal is closed it sends any processes spawned from that terminal a HUP signal.  This allows you to close the terminal without it doing so.  The & is used to put a process in the background (ie, not display on the current terminal).
dataw0lf

---

### Post by viorel on 2004-11-17
Thanks dataw0lf, works fine now!

---

### Post by WW on 2004-11-17
I have a very similar question. I've been trying to add matlab to my Applications menu.  First I created a Math menu entry in the main menu, and then added matlab to the submenu.  I was having the same problem that viorel described: I couldn't find the right invocation of matlab that would stay running.

With dataw0lf's tip, I can now get it to work (thanks dataw0lf!), but with just one nuisance.  The command that I put in the launcher is

    nohup matlab &

and I check the "Run in terminal" option. (The ampersand at the end of the command doesn't seem to matter; it works the same with or without it.)

The nuisance is that a terminal is started, and then matlab opens up its own window.  The first terminal never goes away.  It has just one line of output:
```
nohup: appending output to `nohup.out'
```
I can close the terminal, and matlab continues to run.  It would be nice if this terminal went away automatically, but I couldn't find a combination of options that would get rid of the terminal while leaving matlab running.  Any chance this is possible?

I suspect the problem is a matlab quirk.  It appears to need a terminal to start up in, but then it opens up its own window anyway.

---

### Post by jwb on 2004-11-17
Maybe I'm missing something, but have you just tried right clicking on the Desktop and doing "Create Launcher"?

Fill in the name under "Name" and under command, just put the full path to the program...... like /usr/bin/programname or /etc/programname or whatever.

If you're not sure where the program resides, do

[INDENT]locate programname[/INDENT]

from the command line. If you don't find it, do

[INDENT]sudo updatedb[/INDENT]

This will update the db that locate searches through. Then try locate programname again.

You'll likely see quite a few hits, but what you are looking for is usually /some/path/programname with nothing after it. Likely will be in in /usr/bin.

---

### Post by WW on 2004-11-17
jwb: I should have explained that better.  When I said "The command that I put in the launcher is ...", I was talking about the "Launcher properties" window of a menu item.  This is the window that pops up when you right-click in a submenu of Applications and select Properties.

The executable command is "matlab", and it works fine from the command line.

---

### Post by jwb on 2004-11-17
[QUOTE=WW]jwb: I should have explained that better.  When I said "The command that I put in the launcher is ...", I was talking about the "Launcher properties" window of a menu item.  This is the window that pops up when you right-click in a submenu of Applications and select Properties.

The executable command is "matlab", and it works fine from the command line.[/QUOTE]

You lost me there, but I take it what I said wasn't the answer. :-)

Try shouting at the monitor or pounding the keyboard. Works for me. ;-)

---

### Post by dataw0lf on 2004-11-17
Ok, this should work for you then:
 
```
nohup metlab > /dev/null 2>&1 &
``` 

Cheers,
dataw0lf

---

### Post by piedamaro on 2004-11-17
[QUOTE=jwb]You lost me there, but I take it what I said wasn't the answer. :-)

Try shouting at the monitor or pounding the keyboard. Works for me. ;-)[/QUOTE]
Lol, it helps sometimes...

Maybe I'm getting this wrong, but it should be enough to run:

gnome-terminal -e "nohup matlab"

from your menu launcher. Does it work?

---

### Post by WW on 2004-11-17
dataw0lf, piedamaro: Thanks for the suggestions, but both still leave the terminal sitting there with the "nohup: appending..." message.  I think the problem lies in the matlab startup script. I tried looking at it, but it is a hairy shell script with lots of architecture-specific voodoo. I decided it's not worth my time trying to figure it out.  Since I can just kill the extraneous terminal after matlab starts, it is only a minor nuisance--I can live with it.

---

### Post by jwb on 2004-11-17
[QUOTE=WW]dataw0lf, piedamaro: Thanks for the suggestions, but both still leave the terminal sitting there with the "nohup: appending..." message.  I think the problem lies in the matlab startup script. I tried looking at it, but it is a hairy shell script with lots of architecture-specific voodoo. I decided it's not worth my time trying to figure it out.  Since I can just kill the extraneous terminal after matlab starts, it is only a minor nuisance--I can live with it.[/QUOTE]

I guess what I'm not getting is why you need the terminal window in the first place. Is it a GUI app?

---

### Post by dataw0lf on 2004-11-17
> I guess what I'm not getting is why you need the terminal window in the first place. Is it a GUI app? 
It has nothing to do with him 'needing' a terminal window, nohup (a CLI command) is returning 'appending to nohup.out' (ie outputting stdout and stderr to a created file) in a terminal.  I thought that routing it to /dev/null would stop this output; apparently not.
> I think the problem lies in the matlab startup script 

Nah, I really don't think so.  It's just nohup returning what it's supposed to.
dataw0lf

---

### Post by jwb on 2004-11-17
[QUOTE=dataw0lf]It has nothing to do with him 'needing' a terminal window, nohup (a CLI command) is returning 'appending to nohup.out' (ie outputting stdout and stderr to a created file) in a terminal.  I thought that routing it to /dev/null would stop this output; apparently not.
 

Nah, I really don't think so.  It's just nohup returning what it's supposed to.
dataw0lf[/QUOTE]

I'm still not tracking. All you want to do is launch a GUI app from a Desktop launcher or an applications menu launcher, right?

Why isn't just creating a launcher that calls directly to the program sufficient?

---

### Post by zenwhen on 2004-11-17
I too am slightly confused as to the need for a terminal command at all. You either directly call a GUI app or check where it says to launch the app it a terminal. It is pretty simple.

---

### Post by dataw0lf on 2004-11-17
[QUOTE=jwb]Why isn't just creating a launcher that calls directly to the program sufficient?[/QUOTE] 

[QUOTE=zenwhen]I too am slightly confused as to the need for a terminal command at all. You either directly call a GUI app or check where it says to launch the app it a terminal. It is pretty simple.[/QUOTE]

All he's doing is creating a visual shortcut in Gnome to start the program from the shell.  Thus, when it starts (and isn't nohupped), it will hang in a terminal unless a nohup and a & is issued.
dataw0lf

---

### Post by jwb on 2004-11-17
[QUOTE=dataw0lf]All he's doing is creating a visual shortcut in Gnome to start the program from the shell.  Thus, when it starts (and isn't nohupped), it will hang in a terminal unless a nohup and a & is issued.
dataw0lf[/QUOTE]

Yeah, I get that. I just don't see why the terminal needs to be called 
*at all.* 

He's doing a launcher with "gnome-terminal -e program" when all he needs is "program".

---

### Post by jdong on 2004-11-17
If you want the window to close, **nohup matlab &;exit**

---

### Post by WW on 2004-11-17
jdong: That does not work because it is not valid syntax for the shell.  Apparently you can't put a semicolon after &.

---

### Post by piedamaro on 2004-11-17
I must admit I didn't understand why you need the hangup, but I remember I had a problem running a gui for the R language from the gnome menu, because of a weird startup script.

Anyway
nohup matlab & exit

should work. (At least it works if I try it with random gtk programs).

---

### Post by viorel on 2004-11-18
[QUOTE=piedamaro]I must admit I didn't understand why you need the hangup, but I remember I had a problem running a gui for the R language from the gnome menu, because of a weird startup script.

Anyway
nohup matlab & exit

should work. (At least it works if I try it with random gtk programs).[/QUOTE]
 Still doesn't work... It launches Matlab, closes the terminal, but then the Matlab splash screen goes away and matlab isn't launched. I'm thinking of maybe closing the terminal after matlab is running (so exit with a delay???). Just have no idea how to do it...

---

