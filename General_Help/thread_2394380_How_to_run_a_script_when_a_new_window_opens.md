---
title: "How to run a script when a new window opens"
date: 2018-06-15
forum: General Help
---

### Post by cedardoc on 2018-06-15
How would I automatically run a script when a new window opens?

Thanks,
Dave

---

### Post by TheFu on 2018-06-16
I'd call the script and have it open the new terminal.  If you want **any** possible window opening to cause this, that would need to be tied into the window manager and different window managers would have different methods for hooks.

---

### Post by cedardoc on 2018-06-16
How about just using the vanilla Ubuntu 18.04?  I don't even know how to begin to search for that.

---

### Post by TheFu on 2018-06-17
> **cedardoc said:**
> How about just using the vanilla Ubuntu 18.04?  I don't even know how to begin to search for that.

Sorry, 18.04 is too new for me and I don't use any DE.  I'm a WM-only user but programmed X/Windows applications for about 5 yrs.

Do you want to run 1 script, 1 time?
OR
Do you want to run 1 script, every time a specific window opens?
OR
Do you want to run 1 script, every time **any** window opens?

---

### Post by Claus7 on 2018-06-17
Hello,

> **cedardoc said:**
> How would I automatically run a script when a new window opens?

Thanks,
Dave

> **TheFu said:**
> 
OR
Do you want to run 1 script, every time **any** window opens?

If it is that last option you are after, then the following script would suffice:

```
while :
do
wmctrl -l > tmp_wmctrl1.txt
sleep 2
wmctrl -l > tmp_wmctrl2.txt
tmp1=$(wc -l < tmp_wmctrl1.txt)
tmp2=$(wc -l < tmp_wmctrl2.txt)

if [ $tmp2 -gt $tmp1 ]
   then
   echo ":-)"
fi

rm tmp_wmctrl1.txt tmp_wmctrl2.txt

done
```

What it does is that: there is an infinite loop, and inside that loop the command 'wmctrl -l' runs twice, and which lists the open windows each time. Then it compares the output of the command in these two different instances by checking the number of lines each output has. If the 2nd instance has a greater value than the first (which means that a new window has opened) then the argument of the if statement is fulfilled, and it prints to the screen the happy face: there you can substitute whichever other action you want to take place.

In order to exit from the infinite loop Ctrl+c would end the script.

Regards!

---

### Post by TheFu on 2018-06-17
Does wmctrl work on Wayland?   Wayland is a relatively new display manager that replaces X11. Wayland was the default for 17.10, but enough other programs weren't ready that 18.04 dropped by to X11 as the default.

A simple count of windows might be fine or it might not. For very little effort, using diff, it would be much better to see if any window processes had changed. 
```
$ diff tmp_wmctrl*
8a9
> 0x0340000f  0 cb35 xterm
```
shows that another xterm was started --- the '>' says "new window added" ... a '<' would say one or more was closed.

So if we grep on '^>' then we'd know that at least 1 new window had showed up. ```
$ diff tmp_wmctrl* | egrep -c '^>'
``` and if the result is larger than zero, a new, additional, window showed up in the last 2 seconds.

There are dead spots with this method.  Hooking into the new-window event would solve that.  Which is why I'd tie into the window manager and placement hooks that most have. I know mvm, fvwm, and openbox support it, so any compliant WM should do it.  What gnome3 (the default DE for stock Ubuntu 18.04) does is a mystery to me, mainly because I've never looked.  Gnome3 doesn't work great on low-end systems with minimal GPUs or inside virtual machines, so I won't be using it.

[http://openbox.org/wiki/Help:Applications#Example_of_per-app_settings](http://openbox.org/wiki/Help:Applications#Example_of_per-app_settings) shows how to control extra stuff for specific applications under openbox. Every WM should have a similar capability. Don't expect any GUI to do this. It will be either config files or dconf or whatever gnome is forcing these days.   Binary config files should be outlawed, imho, and are definitely against the core Unix philosophy.  Heck, XML is terrible, but at least we can edit settings with a text editor.

[https://wiki.gnome.org/Projects/GnomeShell/Extensions](https://wiki.gnome.org/Projects/GnomeShell/Extensions) might be helpful.  IDK.
Ubuntu under Unity had an extension capability using XML files. 

I bet someone else can add a little of their knowledge to what Claus7 and I have already and make this even better. None of us is as smart as all of us. ;)

---

### Post by cedardoc on 2018-06-17
Thank you both! Yes, Claus7 is right - that's what I'm after.  I'll try both and see what works better :)

---

### Post by cedardoc on 2018-06-20
Here's what ended up working for me (I wanted to force any new windows to raise)

> while :
do
wmctrl -l > /tmp/tmp_wmctrl1.txt
sleep 2
wmctrl -l > /tmp/tmp_wmctrl2.txt
tmp1=$(wc -l < /tmp/tmp_wmctrl1.txt)
tmp2=$(wc -l < /tmp/tmp_wmctrl2.txt)


if [ $tmp2 -gt $tmp1 ]
   then
   mywin=$(wmctrl -l| wmctrl -l | awk '{ print $1}' | sed '$!d')
   echo $mywin
   wmctrl -i -a "${mywin}"
fi


rm /tmp/tmp_wmctrl1.txt /tmp/tmp_wmctrl2.txt


done


Just wondering, in the case of a program like Pidgin, this method still doesn't work if there's a new message but the window is already existing - is there any way you know of to detect when a panel icon is flashing?  When I get a new message on pidgin the icon in the panel flashes (even though the window doesn't raise).  There must be some way to detect that and cause the window to raise similar to how this is done above...

Thanks, 
Dave

---

### Post by TheFu on 2018-06-20
A quick google found this gnome3 addon: 
[https://askubuntu.com/questions/80969/gnome-shell-move-windows-to-front-on-launch-no-more-is-ready-to-use-noti](https://askubuntu.com/questions/80969/gnome-shell-move-windows-to-front-on-launch-no-more-is-ready-to-use-noti)

Is that the end-goal you were trying to achieve?

---

### Post by cedardoc on 2018-06-21
Actually, that would solve my first question (although I still like being able to do the same thing with a bash script like above)

However that does not solve my second problem:  When a Pidgin conversation window is open, but then you bring something to the foreground, then step away from your computer, and while you're away the other person sends another message that window stays in the background (because its not a "new window" its just an "updated window").  Yes, the icon in the panel for Pidgin may change color or even subtly flash a bit, but I want that new posting to raise the window again so I actually see that new post.

So my thought is that if the windows manager (I assume that's what's receiving the "notification" message) is smart enough to flash the little window list icon, there must be a way to detect that change with a script and have the script raise the window.  In my case I'm using Tint2, but I've seen that flashing behaviour in other window lists (like cairo dock or docky etc)

Thanks

---

### Post by TheFu on 2018-06-21
The flashing request is coming from the app, not the window manager - they might be doing it by changing the window title, I don't know. Just a guess.  Never heard of tint2.  googling .... that's just a panel, not a WM, assuming I found the right thing.  I'm not a dock/panel user either.

I haven't used pidgin in years.  Switched to a BNC, so I never miss any messages, even when I'm not connected.

---

