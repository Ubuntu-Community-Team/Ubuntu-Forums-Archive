---
title: "xbindkeys mouse to multi click with single click?"
date: 2013-02-16
forum: General Help
---

### Post by Jeff2013 on 2013-02-16
Can anyone provide me a simple way have a single mouse left click trigger multiple automatic left clicks ( between 3 and 9) using an xbindkeys script? It would be even better if I can link it to a particular application but that part isn't absolutely necessary if I can turn the script on and off.

(I know it must be possible and some genius coder can probably tell me in seconds how to do this.:))

Thanks in advance,
Jeff

---

### Post by stinkeye on 2013-02-16
Don't really understand how you are going to use your mouse normally when
left mouse is bound to multiple clicks but xdotool can perform multiple clicks.
eg this command will perform 3 clicks using the left mouse (button [COLOR="Red"]1[/COLOR])
```
xdotool click --repeat 3 [COLOR="red"]1[/COLOR]
```

You could use easystroke to bind a long press of the middle mouse button
to initiate the xdotool command or use a modifier key+left mouse(eg ctrl+Lmouse).

---

### Post by Jeff2013 on 2013-02-16
> **stinkeye said:**
> Don't really understand how you are going to use your mouse normally when
left mouse is bound to multiple clicks but xdotool can perform multiple clicks.
eg this command will perform 3 clicks using the left mouse (button [COLOR="Red"]1[/COLOR])
```
xdotool click --repeat 3 [COLOR="red"]1[/COLOR]
```

You could use easystroke to bind a long press of the middle mouse button
to initiate the xdotool command or use a modifier key+left mouse(eg ctrl+Lmouse).
Thanks for the reply. It's not for my primary OS/window manager, I'm running multiple window managers and one is very minimal (openbox) that I've been using to run one particular program almost exclusively. If I can make it program specific that would be great but since that window manager is kind of a specialty desktop it's ok to make the mouse always click that way or to be able to just turn that "script on and off". I'll give your recommendation a try. 

Thanks,
Jeff

---

### Post by Jeff2013 on 2013-02-16
> **Jeff2013 said:**
> Thanks for the reply. It's not for my primary OS/window manager, I'm running multiple window managers and one is very minimal (openbox) that I've been using to run one particular program almost exclusively. If I can make it program specific that would be great but since that window manager is kind of a specialty desktop it's ok to make the mouse always click that way or to be able to just turn that "script on and off". I'll give your recommendation a try. 

Thanks,
Jeff
I am assuming I can I just use xdotool to change the settings and then change it back the same way?

Jeff

---

### Post by stinkeye on 2013-02-16
Have a look at easystroke then.
It has an application specific setting and exceptions.
Clicking on add application brings up a cross hair to click on the application
window you want to add.

---

### Post by Jeff2013 on 2013-02-16
> **stinkeye said:**
> Have a look at easystroke then.
It has an application specific setting and exceptions.
Clicking on add application brings up a cross hair to click on the application
window you want to add.

 Thanks a bunch for the help Stinkeye. I'll give it a shot. I was just reveiewing the documentation on easystroke. Looks like one of the two should do the job. Hopefully easystroke but if not I'll just manually change the click settings with xdotool and change it back to 1 to 1 when I exit the program.    IMPORTANT: if I do need to use xdotool, what is the command to return to 1 to 1 from 1 to 3?  Thanks,   Jeff

---

### Post by stinkeye on 2013-02-16
> **Jeff2013 said:**
> Thanks a bunch for the help Stinkeye. I'll give it a shot. I was just reveiewing the documentation on easystroke. Looks like one of the two should do the job. Hopefully easystroke but if not I'll just manually change the click settings with xdotool and change it back to 1 to 1 when I exit the program.    IMPORTANT: if I do need to use xdotool, what is the command to return to 1 to 1 from 1 to 3?  Thanks,   Jeff
Xdotool just simulates keyboard or mouse activity.
The command
```
xdotool click --repeat 3 1
```
just simulates 3 clicks of button 1 each time it's run.

Doesn't bind anything.

---

### Post by Jeff2013 on 2013-02-16
So it will just reset once I log out or restart or???

---

### Post by stinkeye on 2013-02-17
> **Jeff2013 said:**
> So it will just reset once I log out or restart or???
No it's a once only command then exits.
Doesn't change any settings.

eg test in terminal.
Open a terminal and copy and paste in this command(dont press enter yet)...
```
sleep 3 && xdotool click --repeat 3 1
```
The sleep command is just to delay the running of the command for three seconds
so you can see it happening.
Manually click three times on the command you just pasted in the terminal
and you will notice it highlights the line.
Click again once so it is not highlighted then press enter while keeping the mouse hovered over the command line.
After 3 secs the line should now be highlighted again due to the 3 simulated mouse clicks
 and the terminal returns to the command prompt.
The command prompt is what you first see when opening a new terminal.
eg for me it is...
> glen@Quantal:~$

I have been playing around with easystroke and have been able to set
the xdotool command to be initiated when button one is released only in
a specific window.
You could also use a script to toggle easystroke on/off.
button1 is only changed to three clicks when easystroke is running.

Not sure how easystroke works in the desktop enviroment your using.
Give easystroke a test and if what I've explained is what you want I can help you set it up.

---

### Post by Jeff2013 on 2013-02-17
> **stinkeye said:**
> No it's a once only command then exits.
Doesn't change any settings.

eg test in terminal.
Open a terminal and copy and paste in this command(dont press enter yet)...
```
sleep 3 && xdotool click --repeat 3 1
```The sleep command is just to delay the running of the command for three seconds
so you can see it happening.
Manually click three times on the command you just pasted in the terminal
and you will notice it highlights the line.
Click again once so it is not highlighted then press enter while keeping the mouse hovered over the command line.
After 3 secs the line should now be highlighted again due to the 3 simulated mouse clicks
 and the terminal returns to the command prompt.
The command prompt is what you first see when opening a new terminal.
eg for me it is...


I have been playing around with easystroke and have been able to set
the xdotool command to be initiated when button one is released only in
a specific window.
You could also use a script to toggle easystroke on/off.
button1 is only changed to three clicks when easystroke is running.

Not sure how easystroke works in the desktop enviroment your using.
Give easystroke a test and if what I've explained is what you want I can help you set it up.

   I'll give it a try over the next couple days and let you know if I need some help.  Thanks for taking time to help me.   Jeff

---

### Post by stinkeye on 2013-02-18
Ok, no problem.
The important setting in the easystroke preferences tab
is to change the **timeout profile** to "timeout off" so the
xdotool command is only initiated on button release.
Goodluck.

---

### Post by Jeff2013 on 2013-03-10
> **stinkeye said:**
> No it's a once only command then exits.
Doesn't change any settings.

eg test in terminal.
Open a terminal and copy and paste in this command(dont press enter yet)...
```
sleep 3 && xdotool click --repeat 3 1
```
The sleep command is just to delay the running of the command for three seconds
so you can see it happening.
Manually click three times on the command you just pasted in the terminal
and you will notice it highlights the line.
Click again once so it is not highlighted then press enter while keeping the mouse hovered over the command line.
After 3 secs the line should now be highlighted again due to the 3 simulated mouse clicks
 and the terminal returns to the command prompt.
The command prompt is what you first see when opening a new terminal.
eg for me it is...


I have been playing around with easystroke and have been able to set
the xdotool command to be initiated when button one is released only in
a specific window.
You could also use a script to toggle easystroke on/off.
button1 is only changed to three clicks when easystroke is running.

Not sure how easystroke works in the desktop enviroment your using.
Give easystroke a test and if what I've explained is what you want I can help you set it up.

Hi Stinkeye,
     I'm finally have time to play around with this again and I think I want to try to do two different things that may be easier(?)

First, what if I want to bind the multiple left clicks (at least 3 and as many as 9) to one of my Logitech 518's extra buttons? Say one of the two side buttons? Would that be easier and how would I do that? Can I just edit the mouse config file or something? (and where would that be?)

Second, I would like to use the other of the 518's two side buttons to bring up the context menu so that I can launch the context menu while I'm in another application window. 

If I can do either or even better both without messing with the left click it would be great!

Thanks in advance!

Jeff

---

### Post by stinkeye on 2013-03-10
Use easystrtoke to bind a command or keyboard shortcuts to a button.
_[http://ubuntuforums.org/showthread.php?t=1694352&p=10495426#post10495426]("http://ubuntuforums.org/showthread.php?t=1694352&p=10495426#post10495426")_

---

### Post by Jeff2013 on 2013-03-11
> **stinkeye said:**
> Use easystrtoke to bind a command or keyboard shortcuts to a button.
_[http://ubuntuforums.org/showthread.php?t=1694352&p=10495426#post10495426](http://ubuntuforums.org/showthread.php?t=1694352&p=10495426#post10495426)_

Hi Stinkeye,

Other than easystroke (which doesn't seem like its exactly what I'm looking for) is it possible for me to edit the mouse config file directly and at least get those two thumb buttons doing something other than just forward and back in a browser window?

Even adding general context menu items would be better than nothing though not as helpful as automatic multi clicks.

Thanks in advance.

jeff

---

### Post by stinkeye on 2013-03-11
I'm sure there's a way but I have never looked into it 
because easystroke suits my needs.
May have to do some research into xbindkeys and autokey.

Not sure what your goal is but this may help...
[**_[COLOR="#B22222"]AutoKey : Linux Utility for Text Substitution , Hotkeys and Desktop Automation[/COLOR]_**]("http://saravananthirumuruganathan.wordpress.com/2010/04/14/autokey-linux-utility-for-text-substitution-hotkeys-and-desktop-automation/")

---

### Post by Jeff2013 on 2013-03-16
> **stinkeye said:**
> I'm sure there's a way but I have never looked into it  because easystroke suits my needs. May have to do some research into xbindkeys and autokey.  Not sure what your goal is but this may help... [**_[COLOR="#B22222"]AutoKey : Linux Utility for Text Substitution , Hotkeys and Desktop Automation[/COLOR]_**]("http://saravananthirumuruganathan.wordpress.com/2010/04/14/autokey-linux-utility-for-text-substitution-hotkeys-and-desktop-automation/")  Can anyone tell me what the exact command structure I would use to launch the application menu?  I've got the mouse binding part down but don't know the command to launch the menu.  Thanks in advance,  Jeff

---

