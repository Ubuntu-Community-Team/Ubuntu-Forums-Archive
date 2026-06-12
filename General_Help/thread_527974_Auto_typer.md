---
title: "Auto typer"
date: 2007-08-17
forum: General Help
---

### Post by The Wisedude on 2007-08-17
Is there any auto typer for linux? I really cannot find one..

---

### Post by praet on 2007-08-17
I think what you are looking for could be done in a bash script that calls a program to send keys like this:

```
xvkbd -text "string to type"
```

see:
[http://homepage3.nifty.com/tsato/xvkbd/#option](http://homepage3.nifty.com/tsato/xvkbd/#option)

You could also send individual keys/ combinations like this:
```
xsendkeys "a"
xsendkeys "Shift_L+a"
```
The first line sends the letter "a" while the second sends a capital "A".
From: [http://linux.die.net/man/8/xsendkeys](http://linux.die.net/man/8/xsendkeys)

---

### Post by The Wisedude on 2007-08-17
> **praet said:**
> I think what you are looking for could be done in a bash script that calls a program to send keys like this:

```
xvkbd -text "string to type"
```

see:
[http://homepage3.nifty.com/tsato/xvkbd/#option](http://homepage3.nifty.com/tsato/xvkbd/#option)

You could also send individual keys/ combinations like this:
```
xsendkeys "a"
xsendkeys "Shift_L+a"
```
The first line sends the letter "a" while the second sends a capital "A".
From: [http://linux.die.net/man/8/xsendkeys](http://linux.die.net/man/8/xsendkeys)


Im not to good with this stuff, im looking for a program.

---

### Post by The Wisedude on 2007-08-17
bump

---

### Post by The Wisedude on 2007-08-17
bump

---

### Post by PhilipGanchev on 2007-08-17
What is an auto typer?  What does it do?

---

### Post by praet on 2007-08-20
Basically the above program will send keys as if they were keyboard presses.

So install the xvkbd program, (in a terminal, type:)
```
sudo apt-get install xvkbd
```

Then test it by running it with some string text:
```
xvkbd -text "string to type out"
```
and the keyboard presses will be simulated.

Heres an example with a delay of three seconds.  
```
sleep 3s; xvkbd -text "string to type out"
```
So you can call the command, then move to an input field, and three seconds later that input field will receive the keypresses that type out that text.

What i meant by script is that for more complicated actions, like waiting between commands, you should save what you want to do in a bash script.
file "autotype.sh"
```
#!/bin/sh
sleep 3s
xvkbd -text "this "
sleep 1s
xvkbd -text "is "
sleep 1s
xvkbd -text "sent "
sleep 1s
xvkbd -text "from "
sleep 1s
xvkbd -text "a script. "

```

Make sure the script is executable: ```
chmod +x autotype.sh
```
then run the script: ./autotype.sh

Hope this helps.

---

### Post by praet on 2007-08-21
As per your pm request here is how to send alternate keys:
```
     \r - Return
     \t - Tab
     \b - Backspace
     \e - Escape
     \d - Delete
     \S - Shift (modify the next character)
     \C - Control (modify the next character)
     \A - Alt (modify the next character)
     \M - Meta (modify the next character)
     \[keysym] - the keysym keysym 
```

So to send the enter key you could use \r :
```
xvkbd -text "\r"
```

Something like Ctrl+alt+del is sent like this:
```
xvkbd -text "\C\A\d"
```

see [http://homepage3.nifty.com/tsato/xvkbd/](http://homepage3.nifty.com/tsato/xvkbd/) for more tips.

---

### Post by LOBONCA on 2008-02-07
Is there an app that is less criptic to install and has a user interface?

I am looking for something to replace the Windows AutoHokey. In my work I need the ability to use various key combinations to send large strings of text to via email and a notepad.

---

### Post by kaspin on 2008-02-08
I'm also hoping to find a replacement for Autohotkey, and will try Auto typer, although it looks a bit complicated for a newbie like me. Could it be used to show mouse coordinates? This would be most useful for helping visually impaired people. For example, to reply to a Skype call you have to press the green button. With a macro written in Authotkey it is possible to simulate a mouse click anywhere you chose on the screen (or in a window within the screen) to cope with this

---

### Post by peabody on 2008-02-18
I've managed to implement a program that has the hotstring functionality of autohotkey.  The link is in my signature (autokey).  Give it a shot and let me know if it works for you.

---

