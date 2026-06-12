---
title: "First 'return' entered in terminal logs me out. AND other issues"
date: 2013-05-15
forum: General Help
---

### Post by dustinr on 2013-05-15
Hello all.

As my title suggests, when I first hit 'return' (enter key) inside of a terminal after the OS has booted, it will log me out of the session. I then can log back in and the next command entered works okay.
I was suspecting my vnc servers that I run, but I even disabled it and this still occurs. I do have auto login enabled.
This happens almost every time it boots up but, once in a blue moon it will work correctly.

I can open applications like chrome or settings. It seems like it is only the first terminal command, regardless what it is,
    will log me off. I can even type gibberish 'asdfasdf' and it will still happen.

Interesting NOTE: while it is in the state that it boots and auto logs IN, BUT before I run a command. 
    I can NOT do the combo of 'Ctrl + Alt + F1' that normally would bring you to the frist console.
    Not only the frist console, but any of them. Instead it does not respond to any of that and stays at the desktop. default console 7
    After I do the issue of first 'return' in the terminal, it auto logs me out, I log in. I can then switch consoles.

A couple other things that will happen ( might or might not be related to this issue ):

Sometimes it boots to a black screen with mouse cursor and blinking cursor in top left. 
    I can move the mouse, and if i hit a key I see some non-human readable text in the top left.
    When I hit 'enter' it will bring me to the log-in screen. the below issue ( slow log in screen) had occured during this situation. 
    When i get logged back in, the terminal 'return' issue does not occur.
    
Sometimes when I am logged off automatically, the log in screen is extremely slow to respond. 
    The cursor does not even blink. I type the password and hit enter, after a couple mins it will log me into the screen.

Has anyone experienced this or something similar? Any help would greatly be appreciated.

I have Ubuntu 12.04 with kernel 3.6.0-030600-generic

---

### Post by matt_symes on 2013-05-15
Hi

> As my title suggests, when I first hit 'return' (enter key) inside of a  terminal after the OS has booted, it will log me out of the session. I  then can log back in and the next command entered works okay.
I was suspecting my vnc servers that I run, but I even disabled it and this still occurs. I do have auto login enabled.

That sounds really odd ! Never come across that before.

Just so we can be sure what is happening on your system, i have a couple of questions.

When you say terminal, you are talking about a terminal emulator like gnome-terminal or xterm and not a console (ctrl + alt + F1-7) ?

If this is so, have you tried logging into a console ? If so, do you get the same/similar problem logging into a console ? I.e does it log you out and back to getty ?

If it's a terminal emulator, what emulator is it ? Have you tried a different one ?

When did this start happening ? Can you pin-point anything you did or the system did, such as an update, just before it happened ?

Kind regards

---

### Post by dustinr on 2013-05-15
Yes terminal meaning the gui window that can be ran after the graphical log in. not the ctrl+alt+F*

> [COLOR=#000000]If this is so, have you tried logging into a console ? If so, do you get the same/similar problem logging into a console ? I.e does it log you out and back to getty ?[/COLOR]

> [COLOR=#000000]Interesting NOTE: while it is in the state that it boots and auto logs IN, BUT before I run a command. [/COLOR]
[COLOR=#000000]I can NOT do the combo of 'Ctrl + Alt + F1' that normally would bring you to the frist console.[/COLOR]
[COLOR=#000000]Not only the frist console, but any of them. Instead it does not respond to any of that and stays at the desktop. default console 7[/COLOR]
[COLOR=#000000]After I do the issue of first 'return' in the terminal, it auto logs me out, I log in. I can then switch consoles.[/COLOR]

It is the Gnome Terminal V3.6.1

Sadly I can not pin point when this happened. and many changes had been made before I even noticed. I built the machine remotely.

---

### Post by matt_symes on 2013-05-15
Hi

That is very interesting about the consoles.

Reboot so you get to the same problem and instead of opening gnome terminal type 

```
xterm
```

instead. Do you still get the same problem - i half expect you to say yes :)

Kind regards

---

### Post by dustinr on 2013-05-15
lol only one problem, typing xterm will require me to execute that command via gnome... Il thrown it in a start up script.

Okay I just tried it and it yields the same result....

With that in mind, I tried hitting just enter with out bringing a terminal.... same thing, logs me out

---

### Post by hawthornso23 on 2013-05-15
Something strange in your .bashrc ?

---

### Post by dustinr on 2013-05-15
Possibly, I am exploring this thought right now.

---

### Post by matt_symes on 2013-05-15
Hi

Post them here is you want others to look at them.

Kind regards

---

### Post by dustinr on 2013-05-31
Sorry for the long delay.

I did a diff from a fresh install of Ubuntu 12.04's /home/user/.bashrc and the .bashrc in question and the only difference is what I added manually.

> 
export HISTTIMEFORMAT="%F %T: "
export PATH="$PATH:/core/bin:/usr/local/zend/bin"
export EDITOR=vi
export DISPLAY=:0
set -o vi




I am going to comment these out and see if it helps.

Thanks

...

I am editing my previous post.

I just tried what I said above and it had no effect. I will google more, but any advice would be appreciated.

---

### Post by dustinr on 2013-05-31
Here is an interesting note...

When I said earlier that I could not 'Ctrl Alt F1' , I now realize that I can not get into ANY of the F* sessions. Pressing F1 - F12 does not change the screen, or even make it 'blink'.

I wonder if X is starting faster than gnome can initialize. More google...

---

### Post by dustinr on 2013-05-31
This does not happen everytime I boot, but nearly. Here is the output of 'ps aux | grep tty' when I did not get logged off by 'enter' and I could switch tty's

> $ ps aux | grep ttyroot       921  0.0  0.0  19984   984 tty4     Ss+  14:09   0:00 /sbin/getty -8 38400 tty4
root       935  0.0  0.0  19984   972 tty5     Ss+  14:09   0:00 /sbin/getty -8 38400 tty5
root       958  0.0  0.0  19984   976 tty2     Ss+  14:09   0:00 /sbin/getty -8 38400 tty2
root       960  0.0  0.0  19984   984 tty3     Ss+  14:09   0:00 /sbin/getty -8 38400 tty3
root       967  0.0  0.0  19984   976 tty6     Ss+  14:09   0:00 /sbin/getty -8 38400 tty6
root      1289  2.6  0.4 114152 19244 tty7     Ss+  14:09   0:02 /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
root      2961  0.0  0.0  19984   976 tty1     Ss+  14:09   0:00 /sbin/getty -8 38400 tty1
kiosk     4032  0.0  0.0  13588   920 pts/15   S+   14:11   0:00 grep --color=auto tty

And here is the output of the same command, but this time when it booted, I could not switch tty's and when i hit 'enter' ( after I ran this command ) it did log me off

> $ ps aux | grep ttyroot       927  0.0  0.0  19984   980 tty4     Ss+  14:12   0:00 /sbin/getty -8 38400 tty4
root       933  0.0  0.0  19984   980 tty5     Ss+  14:12   0:00 /sbin/getty -8 38400 tty5
root       943  0.0  0.0  19984   980 tty2     Ss+  14:12   0:00 /sbin/getty -8 38400 tty2
root       946  0.0  0.0  19984   976 tty3     Ss+  14:12   0:00 /sbin/getty -8 38400 tty3
root       954  0.0  0.0  19984   976 tty6     Ss+  14:12   0:00 /sbin/getty -8 38400 tty6
root      1293  1.1  0.4 114200 19256 tty7     Ss+  14:12   0:03 /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
root      2905  0.0  0.0  19984   980 tty1     Ss+  14:12   0:00 /sbin/getty -8 38400 tty1
kiosk     5097  0.0  0.0  13588   916 pts/15   S+   14:16   0:00 grep --color=auto tty

I think it is interesting that the '19984' numbers of the other tty's are the same, and the '114152' and '114200' of the tty7 are different ... I am not sure what that number represents.

---

### Post by dustinr on 2013-05-31
Okay... I tried some suggestions from [http://ubuntuforums.org/showthread.php?t=1624602&page=2](http://ubuntuforums.org/showthread.php?t=1624602&page=2) post 16 with no luck.

So I think I got it working, but not in the way that I wanted to. At some point I had updated my kernel to 3.6 so I decided to try to boot using the previous kernel 3.2.0-38 and now the problem is gone.

This worries me because I bumped up the kernel version to 3.6.0-030600-generic to resolve GPU hangs that the IVY bridge was experiencing...

I guess I will see how well this will work, but please if anyone as an idea why this is happening, please help me out.

---

### Post by matt_symes on 2013-06-02
Hi

If you installed 3.6 to fix the GPU issues then you could try to install the raring or even quantal hardware enablement stack to bump up the kernel without using a main line kernel (the 3.6 kernel you have will be a mainline kernel).

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

This may fix your issue for you.

Kind regards

---

### Post by Habitual on 2013-06-04
for the return "error" try this:
```
bash --rcfile x
``` you don't need an actual x file
run it and press <enter> , same result?

Little hard to accomplish if you can hit enter. My bad. Sorry.

---

### Post by dustinr on 2013-06-24
Hello all, sorry for the long delay. I found a 'band aide' that resolves this issue. It seems the the SSD I am using is too fast and it does not let the system fully initialize before running lightdm. I edited the /etc/init/lightdm.conf file and added a 2 second sleep before the command that runs lightdm. 

After this was in place I have not seen the 'return' press to log out. All is well and I will mark this as solved, thank you all for the suggestions.

---

