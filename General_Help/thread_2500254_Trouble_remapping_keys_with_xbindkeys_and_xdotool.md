---
title: "Trouble remapping keys with xbindkeys and xdotool"
date: 2024-08-27
forum: General Help
---

### Post by Tom_ZeCat on 2024-08-27
Hello, everyone. I’m trying to set up some basic keybindings using xbindkeys and xdotool, but I’m hitting a wall. My goal is to remap several keystrokes eventually, but for now, I’m focusing on these two to see if I can get them working. If successful, I plan to add more. The keybindings I’m working on are:

> Ctrl+A to move one word to the left (same as Ctrl + [left arrow])
Ctrl+F to move one word to the right (same as Ctrl + [right arrow])

I’ve used these remappings for years in LibreOffice Writer through its built-in macros and the Tools ==> Customize ==> Keyboard menu. I’m now trying to configure these settings natively in Linux (Kubuntu 22.04). The reason for this is that I sometimes use other word processors (like SoftMaker TextMaker and Fade In) and basic text editors. It would be a significant improvement if I could get these navigation commands to work in these other applications as well.

Following online tutorials, I created a configuration file named .xbindkeysrc in my home directory with the command:

```
xbindkeys --defaults > ~/.xbindkeysrc
```

I then edited this file using my preferred IDE, Geany, and added the following keybindings:

```
# Default keybinding I uncommented
"xbindkeys_show" control+shift + q

Remap Ctrl+A to Ctrl+Left Arrow
"xdotool key --clearmodifiers ctrl+Left" control + a

Remap Ctrl+F to Ctrl+Right Arrow
"xdotool key --clearmodifiers ctrl+Right" control + f
```

After saving the file, I ran xbindkeys from the command line. However, when I tested the keybindings in Geany or other text editors and word processors like AbiWord, they didn’t work. Pressing Ctrl+A or Ctrl+F made Geany blink, but no action occurred. Interestingly, these keybindings also do not work in LibreOffice Writer, despite having functioned for years through LibreOffice's custom commands. All of the other of my custom navigation commands continue to work fine in LibreOffice Writer.

When I stop xbindkeys with:

```
pkill xbindkeys
```

the Ctrl+A and Ctrl+F commands return to their default behavior in LibreOffice Writer, and Geany's default commands for select all text and find start working again.

The documentation suggests that running xbindkeys should automatically load the .xbindkeysrc file from my home directory. To verify, I tried specifying the config file directly with:

```
xbindkeys -f .xbindkeysrc
```

but the result was the same. I also checked if the file might have been improperly saved by opening .xbindkeysrc with nano and re-saving it, but this didn’t resolve the issue. My xbindkeys version is:

```
xbindkeys 1.8.7 by Philippe Brochard
```

and my xdotool version is:

```
xdotool version 3.20160805.1
```

It seems that xbindkeys is running, but the key remaps are not being applied. I have swapped the left Ctrl key and Caps Lock via Kubuntu’s system settings, and I wondered if this might be affecting it. However, the Ctrl+A and Ctrl+F remappings don’t work with the right Ctrl key (which I did not change) either. I tried removing indentation from the commands in the config file for readability, but this did not solve the issue.

I also suspected a file permissions problem and used chmod to set various permissions (up to 777 for full access), but there was no change.

I’m unsure why it’s not working as expected. I followed the tutorial steps carefully. Any advice or insights would be greatly appreciated. Thanks!

---

### Post by Holger_Gehrke on 2024-08-27
'xbindkeys' and 'xdotool' both rely on X11 being your display server. If you're using Wayland they can't really work. Check whether that's the problem by running 
```

echo $XDG_SESSION_TYPE

```
There is a replacement for 'xdotool' for Wayland called ydotool, but I'm not sure it can do what you want it to do. Alternatively you can try running a X11-session by selecting it in your greeter (the program which asks for your user-name and password before starting a session).

Holger

---

### Post by Tom_ZeCat on 2024-08-27
Thanks.  My system info showed that my Kubuntu is X11 based, but just to be sure I've run that command: 

> echo $XDG_SESSION_TYPE
x11

Definitely X11.

---

### Post by Holger_Gehrke on 2024-08-28
From the manual of xdotool:
> 
If you are trying to send key input to a specific window, and it does not appear to be working, then it's likely your application is ignoring the events xdotool is generating.
This is fairly common.

So the first step would be to try and see whether the apps you're using are rejecting keypresses coming from the XTEST extension. Open a terminal and the program you want to test. Try something like 'xdotool selectwindow key --window %1 Right' in the terminal. The mouse cursor will change and xdotool will wait for you to select a window to send the keypresses to. If the cursor in the program moves to the right after clicking in its window then the program isn't blocking XTEST generated events.

While playing around with this and xbindkeys I noticed that it tended to work better if I was more specific with the modifiers - e.g. Control_R or Control_L instead of just Control in the xdotool-line. Even then it only worked about two times out of three.

Might be worth it to think about redefining keys in your applications directly. I'm certain that Geany has redefinable keyboard shortcuts and I wouldn't be surprised if the other do, too. Even bash has a way to redefine it's behaviour when editing commands (libreadline, there's lots of information about this in 'man bash'). The advantage of this approach is that you don't break the keyboard shortcuts of other application, but of course it's a lot more work.

Holger

---

### Post by Tom_ZeCat on 2024-08-28
> **Holger_Gehrke said:**
> From the manual of xdotool:

So the first step would be to try and see whether the apps you're using are rejecting keypresses coming from the XTEST extension. Open a terminal and the program you want to test. Try something like 'xdotool selectwindow key --window %1 Right' in the terminal. The mouse cursor will change and xdotool will wait for you to select a window to send the keypresses to. If the cursor in the program moves to the right after clicking in its window then the program isn't blocking XTEST generated events.

While playing around with this and xbindkeys I noticed that it tended to work better if I was more specific with the modifiers - e.g. Control_R or Control_L instead of just Control in the xdotool-line. Even then it only worked about two times out of three.

Might be worth it to think about redefining keys in your applications directly. I'm certain that Geany has redefinable keyboard shortcuts and I wouldn't be surprised if the other do, too. Even bash has a way to redefine it's behaviour when editing commands (libreadline, there's lots of information about this in 'man bash'). The advantage of this approach is that you don't break the keyboard shortcuts of other application, but of course it's a lot more work.

Holger

Okay, thanks for the info.  I've tried your "xdotool selectwindow key --window %1 Right" command.  Here are the results.  You'll see various keys like "Ctrl+A" listed.  I've written these letters in caps by convention, but they're really lower case, as in Ctrl+[lowercase a].  

> Left Ctrl+A = Blinks, puts no info in terminal
Left Ctrl+F = Blinks, puts no info in terminal
Left Ctrl+S = Does not blink, puts no info into terminal, message in a brown menu above terminal says: "Output has been suspended by pressing Ctrl+S.  Press Ctrl+Q to resume".  When I hit Ctrl+Q (in terminal), it quits.
Left Ctrl+D = Does not blink, puts no info into terminal.  
Left Ctrl+X = Outputs to terminal: ^X
[Left Arrow]  = Outputs to terminal: ^[[D
[Right Arrow] = Outputs to terminal: ^[[C
Left Ctrl+[Left Arrow] = Outputs to terminal: ^[[1;5D
Left Ctrl+[Right Arrow] = Outputs to terminal: ^[[1;5C
Right Ctrl+A = Blinks, puts no info in terminal
Right Ctrl+F = Blinks, puts no info in terminal

I have done everything successfully that I want to do in LibreOffice Writer via its macros and key customization system, except for using Ctrl+QS for going to the beginning of a line and Ctrl+QD for going to the end of a line.  LibreOffice doesn't allow the use of Ctrl+[two letters] as hotkeys.  However, I was able to use Ctrl+Alt+[ and Ctrl+Alt+] respectively for those.  So I'm good with LO Writer.  However, my other word processors, SoftMaker TextMaker and Fade In, have no similar macro system (at least not in their Linux versions).  For basic text editors, I have used Geany's snippets plug-in, which is quite nice for auto-typing a bunch of repetitive text, though I haven't searched for a macros and hot key system like LibreOffice has.  

I'm starting to wonder if what I'm attempting cannot be done.  I've also tried this with the GUI-based Linux apps, AutoKey and Input Remapper, but am not having much luck.  

One more thing: I tested both the left and right Ctrl button because my left Ctrl is actually the caps lock button.  I used Kubuntu's System Settings to swap the Ctrl and the Caps Lock.  So far, once I've done that, that Caps Lock key just to the left of the A key has always worked exactly like Ctrl.  My thought was: if I had to swap those back in Kubuntu's System Settings and then re-swap them via xbindkey to get this to work, I could do that.

---

### Post by dragonfly41 on 2024-08-28
You could experiment with Actiona. A UI emulator. You can build a library of procedures to call. I use it frequently for workflow automation. In fact as I write this.

P.S. Another workflow tool is Albert. But you have to write your custom extension in Python. There is a standard library supplied. You hit say Ctrl+Space to see the query field then design your own commands.

---

### Post by Tom_ZeCat on 2024-08-28
> **dragonfly41 said:**
> You could experiment with Actiona. A UI emulator. You can build a library of procedures to call. I use it frequently for workflow automation. In fact as I write this.

P.S. Another workflow tool is Albert. But you have to write your custom extension in Python. There is a standard library supplied. You hit say Ctrl+Space to see the query field then design your own commands.

Thanks. I will look into that.  I don't know Python very well at present, but I've invested in some good Python books and plan to learn it.  I worked hard learning Visual BASIC 6 (classic, not .net), but Microsoft orphaned it.  Thanks a lot, MS.  I then moved on to REALbasic (now renamed as Xojo), but that language is expensive, you have to keep paying on subscription.  It's good, but, no thanks.  Numerous people in the Linux community keep recommending Python, so I'm going with that one.  VB didn't support Linux or Mac anyone (though REALbasic did).

---

### Post by dragonfly41 on 2024-08-29
When you install Albert in my case the trigger is [Ctr+Space] but I have to hit it twice.

Then to get started simply type **py**     .. see Settings > Handlers > py* Settings icon in top bar.

More learning on multiple sites.
w3schools.com is one learning site. But there are many more.

Also note that Python can be embedded in Actiona and also CherryTree notes editor (Codebox).

Anaconda is a Python framework. Then again HaXe. Truly countless options. Rock solid.
After thought. You have Win 7 & Win 2K. They will only recognise the older Python 2, not Python 3 and so bear this in mind.

---

### Post by Holger_Gehrke on 2024-08-29
The point of the whole 'xdotool selectwindow ...' thing is not to try out the various keys, it's meant for checking whether the program(s) you want to control through xdotool and xbindkeys block XTEST generated events.

I've taken a short look at TextMaker, and whether or not you can change keyboard shortcuts depends on whether you're using the full commercial version or not. The manual of the free version explicitly says that that's a feature reserved for the full version. The free version does have the ability to dump it's complete configuration to a file and re-import that configuration, so it might still be do-able by editing the exported configuration and reimporting it.

If you started out on Visual Basic then [Gambas]("https://gambas.sourceforge.net/en/main.html") might be of some interest. Another alternative if you have experience using BlitzBasic (back from the times of the Amiga and Atari ST) would be [BlitzMax]("https://blitzmax.org") and [BlitzMaxNG]("https://github.com/bmx-ng/bmx-ng"). Python - of course - is in many ways the successor to Basic, it's as ubiquitous as Basic ever was or even more so.

Holger

PS: the more I look at it, the more your configuration starts to look like the Wordstar diamond of keys ...

---

### Post by Tom_ZeCat on 2024-08-29
> **dragonfly41 said:**
> When you install Albert in my case the trigger is [Ctr+Space] but I have to hit it twice.

Then to get started simply type **py**     .. see Settings > Handlers > py* Settings icon in top bar.

More learning on multiple sites.
w3schools.com is one learning site. But there are many more.

Also note that Python can be embedded in Actiona and also CherryTree notes editor (Codebox).

Anaconda is a Python framework. Then again HaXe. Truly countless options. Rock solid.
After thought. You have Win 7 & Win 2K. They will only recognise the older Python 2, not Python 3 and so bear this in mind.

Gonna check that out.  Thanks.  That w3schools.com thing sounds really cool.  Thanks for the heads up about Python and my old Windows versions that I use under VirtualBox.  I'll probably add Win 10 to the mix soon in that case.  I'll probably set it to be blocked from Internet access and to never try to update.  I can always temporarily allow it access if I actually need an update.  It drives me nuts if I have a secondary OS that I don't use much, and then I got to use it and it has a zillion updates to do.  I do have an old PC with Win 10 on it as well (which I do let update), but that one is basically just my Plex server for multimedia stuff.  


> **Holger_Gehrke said:**
> The point of the whole 'xdotool selectwindow ...' thing is not to try out the various keys, it's meant for checking whether the program(s) you want to control through xdotool and xbindkeys block XTEST generated events.

I've taken a short look at TextMaker, and whether or not you can change keyboard shortcuts depends on whether you're using the full commercial version or not. The manual of the free version explicitly says that that's a feature reserved for the full version. The free version does have the ability to dump it's complete configuration to a file and re-import that configuration, so it might still be do-able by editing the exported configuration and reimporting it.

If you started out on Visual Basic then [Gambas]("https://gambas.sourceforge.net/en/main.html") might be of some interest. Another alternative if you have experience using BlitzBasic (back from the times of the Amiga and Atari ST) would be [BlitzMax]("https://blitzmax.org") and [BlitzMaxNG]("https://github.com/bmx-ng/bmx-ng"). Python - of course - is in many ways the successor to Basic, it's as ubiquitous as Basic ever was or even more so.

Holger

PS: the more I look at it, the more your configuration starts to look like the Wordstar diamond of keys ...

TextMaker has two different paid versions, 2024 and NX.  I have 2024.  The NX version requires a monthly subscription, and I'm not doing that.  It's the same reason I won't use any Adobe product.  I prefer GNU Open Source software, if possible.  If I do use something proprietary, I'll only do so if you can pay for it and the use that version indefinitely as long as your OS can run it.  I have checked out Gambas and like that it's very VB-like.  However, Python is so widely used in the Linux community that there's an incredible amount of online resources for it.  I'm still getting used to having to code my GUIs, but I'll get the knack of it.  I think I like QT for GUIs rather than tkinter.  I might check out BlitzBasic.  Any idea if it's widely used in the Linux community?  

Yes, the commands I'm trying to put in are the WordStar cursor diamond commands.  I started on WordStar under CP/M, and I always miss the cursor diamond commands if I have to work without them.  I've been able to put them into LO Writer, and it makes a big difference for me.  TextMaker does have a macro system, but only for the Windows and Mac versions.  I only use it for writing in German because it has features for that language that no other word processor has.  Back in the 90s, Germany, and the other German-speaking countries, had a spelling reform, and that occurred after I learned German.  TextMaker will put a red squiggly line under a misspelled German word, but it will put a blue one under a word that's correct according to the old spelling standards, but no longer the current standard.  Plus, it will spell check using the official Duden dictionaries and provide definitions from it.  It's not an epic disaster if I can't somehow program the WordStar cursor diamond, but I'd like to do it, if possible.  Same thing with Fade In.  Writing a screenplay or stage play in Fade In is way easier than it is in a standard word processor because it automatically does the standard screenplay or stage play formats.  Plus, it has a system where you only have to type the first letter of a character's name and it fills in the rest.  I tried a screenplay template for LO Writer, but it wasn't anywhere near as good as Fade In or Final Draft.  Final Draft is excellent as well, but they only have Windows and Mac versions of that.  I give Fade In huge props for coming out with a Linux version, and it's much, much better than any of the free screenwriting word processors.

---

### Post by dragonfly41 on 2024-08-29
Now that we know what you are up to we can perhaps take stock. I admit I have no knowledge of Wordstar Diamond. I set off on a random walkabout to learn more out of curiosity. But since you mention QT then remember that the opening suggestion Actiona uses Qt widgets..


[https://benhoyt.com/writings/wordstar-diamond/](https://benhoyt.com/writings/wordstar-diamond/)


"I use the WordStar keys in my text editor (Sublime Text), my IDE (Intellij), my browser (including inside Google Docs), and even my terminal. One diamond to rule them all&#8230;"


[https://news.ycombinator.com/item?id=40804675](https://news.ycombinator.com/item?id=40804675)


[https://kawriting.co.uk/services/editing/](https://kawriting.co.uk/services/editing/)
[https://scrivener.app/](https://scrivener.app/)


[https://hn.algolia.com/?q=wordstar](https://hn.algolia.com/?q=wordstar)


[https://hn.algolia.com/?dateRange=all&page=0&prefix=true&query=wordstar%20python&sort=byPopularity&type=story](https://hn.algolia.com/?dateRange=all&page=0&prefix=true&query=wordstar%20python&sort=byPopularity&type=story)


[https://hn.algolia.com/?dateRange=all&page=0&prefix=true&query=sublime%20wordstar&sort=byPopularity&type=story](https://hn.algolia.com/?dateRange=all&page=0&prefix=true&query=sublime%20wordstar&sort=byPopularity&type=story)

---

### Post by Holger_Gehrke on 2024-08-29
Changing keyboard shortcuts doesn't have anything to do with macros per se. Textmaker 2024 should have that option - according to the PDF-manual that comes with the free version. There should be a button labeled 'Shortcut keys' available in the dialog that appears when selecting 'Tools'->'Customize'. And being German myself, I'm all too aware of the Rechtschreibreform. But with the transitional period long over, I would think that all word processors / spellcheckers would (and should) by now treat old spellings as mistakes unless you're quoting from text that was written before the reform.

Unless you really want to, there's no need to code your GUIs manually unless you're doing something very *very* ***very*** unusual. For GTK there's Glade, for QT there's QT Designer. For both there are ways to use a GUI created with these tools in Python.

BlitzBasic/BlitzMax/BlitzMaxNG is niche; not only on Linux but in general. When it was originally created - in the 90's I think - it was firmly aimed at the - by that time already dying - market of bedroom coders writing games. I mainly play around with it since there's a very nice clone of Geometry Wars written in BlitzMax that I've tried now and again to optimize to run with just a few more frames per second once there's a ton of enemies on screen.

Holger

---

