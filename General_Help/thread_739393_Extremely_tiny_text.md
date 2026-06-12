---
title: "Extremely tiny text"
date: 2008-03-29
forum: General Help
---

### Post by beatme101 on 2008-03-29
Hello, I've just installed Ubuntu 7.10, am a new user (only used it a little on a virtual environment, where it didn't do very well (not that it's doing well on a real PC)), and am having a rather strange problem.

All of the text is very tiny. Take a look at this picture:
[http://beatme101.com/images/ss/ubuntu-tiny-text.jpg](http://beatme101.com/images/ss/ubuntu-tiny-text.jpg)
That picture sums up my problem pretty well. What do I do? I won't be able to log in, or choose any menu options that could potentially change it when it's like this.

---

### Post by pointone on 2008-03-29
Veryify the integrity of the CD you used to install with. When booting from the CD, a menu should appear with the option to "Check CD for defects".

---

### Post by ibuclaw on 2008-03-29
That is wicked!

:lolflag:

Okay, I think we are going to have to start off your ubuntu experience in CLI!!!
If you have a separate computer. Use it for internet access!

As you may need help in real-time.

OK.
When ubuntu enters login screen. Switch to a Virtual Terminal.
```
 ie: Hit "**Ctrl+Alt+F4**" 
```

Now we should see a lovely DOS type command line screen called BASH Prompt. It should have a readable sized font.

Enter your username and password here.
Logging on is instant.

Lets have a small play about to make sure everything is good!
Type in:
```

myname="Fred"
echo "Hello $myname"

```

If the word "Hello Fred" gets printed, congratulations, you've just used your first Linux Command!

Now, back on track, to perform the next task, we need to be **root**
So we enter in
```
 sudo -i 
```
Enter in the password for your account again. And we now have unlimited access to the whole system.

Next, we change to the directory we need to work in.
```
 cd /etc/X11/xinit 
```
Unlike Windows, Linux is CASE SENTITIVE. so enter in the above location correctly.

Now lets backup what I think may be the troublesome file
```
 cp xserverrc xserverrc.bak 
```
And now we'll edit the xserver file.
```
 nano xserverrc 
```
This opens a text editor in BASH that should look something like this:
```

#!/bin/sh

# $Id: xserverrc 189 2005-06-11 00:04:27Z branden $

exec /usr/bin/X11/X -nolisten tcp

```
Don't worry if it isn't exactly the same.
Now change the **whole** line
```
 exec /usr/bin/X11/X 
```
to
```
 **exec /usr/bin/X11/X -br -audit 0 -dpms -dpi 96** 
```
And we save the file by hitting **Ctrl+X**
We are asked if we want to save it. Hit **Y** followed by **Enter**.

Now exit root and BASH Prompt (type exit twice)
```

exit
exit

```

And change back to the X-Screen
```
 **Ctrl+Alt+F7** 
```
And reset X with
```
 **Ctrl+Alt+Backspace** 
```

If what I believe to be wrong is true, then all should be normal.

If you find that the font is too big, go back and follow the previous steps and change **-dpi 96** to **-dpi 75**

Regards

---

### Post by beatme101 on 2008-03-29
Hey, thanks for responding you two.

1. I have followed your instructions and the CD claims to have no faults.

2. I have followed your instructions (great instructions by the way, easy to follow) and it changed nothing. THe text in the gui is still extremely tiny (I didn't forget to reset with that ctrl+alt+backspace). This was the original line:
```
exec /usr/bin/X11/X -dpi 100 -nolisten tcp
```


EDIT: Yeah, I have two PCs here, side by side, one with Ubuntu and the other with a working Windows 2000 which I'm using to communicate. :)

---

### Post by beatme101 on 2008-03-29
Bump..

---

### Post by beatme101 on 2008-03-29
Bump.

---

### Post by ibuclaw on 2008-03-29
Sorry for the delay, I've been looking round quite a bit.
Ended up looking round the man pages.

Try this instead:

Same routine, enter virtual terminal and switch to root.
And open a file with the console text editor.
```

nano /etc/X11/xorg.conf

```
Now we are going to search for a string of text.
To do this we hit "**Ctrl+W**"
A search box will appear at the bottom. Type in:
```
 Section "Device" 
```
And the cursor point will jump to this text.

Something like this would be shown with it:
```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"

```
As everyone's hardware config is different, don't expect yours to be the same.
Now just add what is in **bold** to the "Option" block.
```
 Option "NoLogo" "True" **"DPI" "96x96"** 
```
Save the file and restart the X-Server.

Same way as I explained before. "**Ctrl+Alt+Backspace**"

If this does work, or at least brings some legibility to your font. Then Brilliant!
You may want to adjust it up as appropriately as you like in multiples of 8.

Regards

---

### Post by beatme101 on 2008-03-30
Thank you for your reply but I do not see an "Option" block. Here's what I've got there:

```
Section "Device"
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection
```

Should I add a new line above EndSection?

```
Option "DPI" "96x96"
```?

EDIT: Okay, after waiting so long (I'd say how long but there're no datestamps on posts on this forum -.-), I tried it, nothing happenned. Restarted, text is still extremely tiny.

EDIT 2: I managed to fix it. I logged in, and the font was fine beyond the login screens, so I updated, and then I enabled a display driver it was nagging me about. I'm not sure if it was by updating, or by using that "driver software that cannot be supported by Ubuntu", but one of those fixed it. Thanks everyone who tried to help. :)

---

