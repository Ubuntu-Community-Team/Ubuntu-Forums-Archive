---
title: "Window matching in Metacity"
date: 2006-12-15
forum: General Help
---

### Post by kobewan on 2006-12-15
I recently came across devilspie and found out about window matching. devilspie is a good utility, but it doesn't do quite what I want. I'm trying to find a tool that will run any command that I tell it to after finding a matching window. Something like that would be very useful in scripting so I figured a few applications like that must already exist, but I have been completely unable to find anything for window matching besides devilspie and wmctrl. Basically, I need a way to do something like this:-

(if ((application name = Firefox) and (focused = true)) then (run ~/script) else (run ~/other script))

Another possible way to do it, I suppose, is to use an devilspie's debug mode or an equivelant program (which would output the name of any opening application), filter through outputted list using something like grep and pass the result on to a script. If grep returns a value showing that the program exists, the script will then carry out the command. Unfortunately, I have nowhere near the knowledge of bash and scripting to be able to carry something as complex as that out. 

Can somebody give me the name of an program that could fulfill my requirements? If nobody can do that, can somebody least tell me if what I outlined above could work and point me in the right direction? Thanks.

---

### Post by tweedledee on 2007-01-30
> **kobewan said:**
> Can somebody give me the name of an program that could fulfill my requirements? If nobody can do that, can somebody least tell me if what I outlined above could work and point me in the right direction? Thanks.

I have (finally) figured out how to start answering your question.  To determine which window has focus, use this nasty construct:
```
xwininfo -id `xprop -root | nawk '/_NET_ACTIVE_WINDOW/ {print $5; exit;}'` | nawk -F \" '/xwininfo:/ {print $2; exit;}'
```
Basically, this does the following:

1. xprop -root provides information on the "root" X window - for our purposes, all that matters is that the "root" window contains the "_NET_ACTIVE_WINDOW" tag, which is the currently focused window.  (Caveat: this relies on the window manager to actually set this flag; Metacity seems to do okay, other WM I don't know.)

2. The first "| nawk " extracts that line from the (large) x-prop output, splits the line on the basis of white space, and extracts the part the region that contains the window ID.

3. The ID is then sent to xwinfino -id, which returns a bit of information on the window matching that ID.

4. The output from xwininfo is then piped to nawk again, which extracts the line containing the window name, splits that line on the basis of a double quote, and pulls the part of that line containing the name.  (Caveat: this would only extract the first part of a window title that contained double quotes; I haven't figured out how to work around that yet -- if I could, I'd just split on spaces and rebuild it.)

Anyway, this answers the basic question of "what window has focus?"  You can now test against that to handle your if statement (assuming you store the final output) and execute the appropriate script.

The unresolved part is how to actually run this kind of test in the background.  Assuming (from other threads) you are trying to use this to execute program-specific keyboard and/or mouse commands, I'd just make use of xbindkeys, since it's already running in the background: use xbindkeys to trap a shortcut/mouse action, and execute a script that looks something like (psuedo-code):
```
appname = xwininfo -id `xprop -root |nawk '/_NET_ACTIVE_WINDOW/ {print $5; exit;}'` | nawk -F \" '/xwininfo:/ {print $2; exit;}'
if (appname == App1) then (execute some command)
else if (appname == App2) then (execute alternative command)
else (execute standard command)
```

Ugly, but it may get the job done; I've not yet tried it out, but I intend to.

---

### Post by tweedledee on 2007-01-31
Here's a full solution, with a not-very-sophisticated example.  In this case, I'm assuming you want your middle-button to act as a middle-button in Firefox, but a double-click under all other circumstances.

Create a script (we'll call it middle-button.bash) and make it executable; I'll assume it is in ~.
```
#!/bin/bash
Program="Firefox-bin"

Class=`xprop -id \`xprop -root |nawk '/_NET_ACTIVE_WINDOW/ {print $5; exit;}'\` |nawk -F = '/WM_CLASS/ {print $2; exit;}'`
#Name=`xprop -id \`xprop -root |nawk '/_NET_ACTIVE_WINDOW/ {print $5; exit;}'\` |nawk -F = '/WM_ICON_NAME/ {print $2; exit;}'`
Found=`echo "$Class" | grep -c "$Program"`

if [ $Found != 0 ]
then
	/usr/bin/xte 'mouseclick 2' &
else
	/usr/bin/xte 'mouseclick 1' 'mouseclick 1' &
fi
exit 0
```
Note that this only uses xprop, not xwininfo, so is a little cleaner than the example above.  This also allows you to match on either the Class or Name (where Name is the stuff in the window's title bar, and class is (usually) the name of the actual executable, or at least something fairly uniquely identifying).  You can choose either, just adjust the "Found" line to use "$Name" instead if you choose to match that way.  To use it for a different program, just change the "Program=" line to the text you want to match.

To invoke this, we need an ~/.xbindkeysrc that looks like this:
```
"/home/user/middle-button.bash &"
b:2 + Release
```
Obviously for all this to work we need xte (xautomation) and xbindkeys installed; see this thread for those unfamiliar with how to work with those: [http://www.ubuntuforums.org/showthread.php?t=316441](http://www.ubuntuforums.org/showthread.php?t=316441).

To find out what the name & class of a program are, run xprop (no commands), and click on an open window; in the mess of output you are looking for the two lines that start with WM_CLASS and WM_ICON_NAME (usually near the bottom for me).  Of course, WM_ICON_NAME should just be the same as the displayed title of the program, so matching with that doesn't require you to play with xprop at all (but may also be more challenging to make sure you only match the programs you actually want).

Caveat on all this: the application-specific effect only occurs when the program actually has focus - clicking in the window when it is not focused will have the general behavior (or behavior specific to the currently focused program).

---

### Post by kobewan on 2007-02-09
Thanks for the excellent information, I *really* appreciate it. I've managed to actually use it to do the job that I had in mind for a long time.

Unfortunately, this does not work on full-screen applications. I don't know why this is, but I suspect its because Metacity doesn't correctly report which window is the "Active Window" when a program is in full screen. It may also be because the program itself doesn't report things correctly, but I tried it in full screen vidoes of VLC and Xine both, and the script is not able to detect that the video is what is focused (it works perfectly when they are not full screen). 

I don't really think that anything can be done about it, but I appreciate the help immensely anyways. I'm going to use this script for everything but videos, which is quite good.

---

### Post by tweedledee on 2007-02-09
You are correct that VLC at least does not work (I don't have Xine installed).  The reason is quite simple - the window that is created is missing nearly all attributes.  It does however work with fullscreen modes of the other three applications I tried, including Totem, so it is apparently limited to a small number number of programs that do an unusual sort of fullscreen.

Nonetheless, we are not beaten.  Although I can't find any unique information to identify VLC in full screen mode, there is a unique way to identify a fullscreen app.  Provided that you only intend to use those applications in full-screen, you can still grab them.  Use this in place of the NAME or Class identifier:
```
State=`xprop -id \`xprop -root |nawk '/_NET_ACTIVE_WINDOW/ {print $5; exit;}'\` |nawk -F = '/_NET_WM_STATE/ {print $2; exit;}'`
``` and this for Program:
```
Program="_NET_WM_STATE_FULLSCREEN"
```
Basically this just matches all fullscreen apps instead of a particular program.  If you want to tell xine and VLC apart, you are now asking the impossible (as near as I can tell), but you can at least sort of identify them.

---

### Post by kobewan on 2007-02-10
Actually, the main reason that I use xine-ui instead of Totem is that I can configure it so that it uses the same shortcut keys as VLC. That means that I don't need to tell them apart when they are in full screen, so if I can get this to work it would be perfect.

However, I still can't get it to work. I'm guessing that its because of the way that I am implementing this. Basically, my plan is to have a separate script for each mouse button, and xbindkeys will just run that script every time I press any mouse button. The script itself looks something like this:

```
#!/bin/bash
Program1="Firefox-bin"
Program2="xine Video Window"
Program3="_NET_WM_STATE_FULLSCREEN"

Class=`xprop -id \`xprop -root |nawk '/_NET_ACTIVE_WINDOW/ {print $5; exit;}'\` |nawk -F = '/WM_CLASS/ {print $2; exit;}'`

Name=`xprop -id \`xprop -root |nawk '/_NET_ACTIVE_WINDOW/ {print $5; exit;}'\` |nawk -F = '/WM_ICON_NAME/ {print $2; exit;}'`

State=`xprop -id \`xprop -root |nawk '/_NET_ACTIVE_WINDOW/ {print $5; exit;}'\` |nawk -F = '/_NET_ACTIVE_WINDOW/ {print $2; exit;}'`

firefox=`echo "$Class" | grep -c "$Program1"`
xine=`echo "$Class" | grep -c "$Program2"`
full=`echo "$State" | grep -c "$Program3"`

```

After that, there is a mess of 'if' loops that does something like this:

if window is <program1>, then do <something>.
if not, and if window is <program2>, then do <something>
if not, and if window is <A fullscreen program>, then do <something>
if not, then the window doesn't match anything that I want, so do <default>

The problem is that it still doesn't detect full screen program as anything. Have you tried it to see if it works, or is it something that I'm doing?

---

### Post by tweedledee on 2007-02-10
Your "State=" line in your posted example is wrong.  You have two "_NET_ACTIVE_WINDOW" phrases; the second should be "_NET_WM_STATE" instead.  All my tests work with the basic format you describe; that's the same approach I'm using for my applications.

Also, in the process of playing with this, I noticed the gxine actually behaves "properly" even in fullscreen, so can be uniquely identified.  Just a bit of information if you decide you do need to distinguish your two players, since gxine and xineui may be similar enough for your purposes.  I also noticed that VLC is really pretty poor at identification all the time, using "frame" as its class!  With a little luck, future versions will clear up the identification issues and make this process a little simpler.

---

### Post by kobewan on 2007-02-10
Argh, stupid me! I can't believe I did that....

Anyways, thanks a lot, that's done the trick. I know that VLC reports things incorrectly, that's actually why I uncommented the Name variable before. That's what made me assume that it might have been a problem with the program reporting it incorrectly, except that it didn't work with Xine either.  Anyways, basically the only flaw in this setup is that it won't differentiate between any fullscreen apps unless they are specifically listed, i.e. it will use the same key bindings for  VLC and a fullscreen image in GQView(or any other picture viewer).

Still, I've thought of a pretty simple workaround and am now finally able to have full applications specific mouse settings. Thank you!

---

### Post by tweedledee on 2007-02-10
> **kobewan said:**
> Argh, stupid me! I can't believe I did that....
Happens to all of us.  I only noticed it myself when I copied the text directly from your post and all of sudden nothing worked.

> Still, I've thought of a pretty simple workaround and am now finally able to have full applications specific mouse settings. Thank you!
Glad to help.  I'm making use of this myself for a few things, and I keep thinking of extra ones.  I love total control!

---

### Post by tweedledee on 2007-03-11
I've converted this into a how-to, with somewhat easier implementation, here: [http://www.ubuntuforums.org/showthread.php?t=380927](http://www.ubuntuforums.org/showthread.php?t=380927).

---

