---
title: "Simplest solution to Capslock delay problem"
date: 2015-11-17
forum: General Help
---

### Post by paul204 on 2015-11-17
[SIZE=3][SIZE=2]Firstly I am so disappointed that the brand new 15.10 still have this problem... This is a problem that people discuss about since 2010, but still not fixed. So by default you will have THis KInd OF THing...
It is really hard for me to change the habit of typing actually. I tried to use shift instead of capslock, but it is just impossible for me to type like that.

There are some solutions to it already, like this: [http://ubuntuforums.org/showthread.php?t=1462333&page=3&p=12328951#post12328951](http://ubuntuforums.org/showthread.php?t=1462333&page=3&p=12328951#post12328951)
However the last step is always not working for me (run automatically when startup), so I tried for months and finally get a solution.

The steps at the beginning is the same as previous answers:

```
[COLOR=#000000][FONT=Ubuntu Mono]xkbcomp -xkb $DISPLAY /home/username/myxkbmap[/FONT][/COLOR]
```

Then open this file, modify the <CAPS> entry like this:

```
[COLOR=#000000][FONT=Ubuntu Mono]key <CAPS> {     repeat=no,     type[group1]="ALPHABETIC",     symbols[group1]=[ Caps_Lock, Caps_Lock ],     actions[group1]=[ LockMods(modifiers=Lock), Private(type=3,data[0]=1,data[1]=3,data[2]=3) ]   }[/FONT][/COLOR]
```

After that run the following code

```
[COLOR=#000000][FONT=Ubuntu Mono]xkbcomp /home/username/myxkbmap $DISPLAY[/FONT][/COLOR]
```

[SIZE=4]Now you should find that the problem is fixed, but just temporarily. Here comes the tricky part:[/SIZE]
Instead of executing it at startup, I would add it to the Shortcut. 

Go to Settings -> Keyboard -> Shortcut -> Custom Shortcuts, add a new shortcut with any name, the command to run is exactly 

```
[COLOR=#000000][FONT=Ubuntu Mono]xkbcomp /home/username/myxkbmap $DISPLAY[/FONT][/COLOR]
```

Then, click "disabled" and press "Capslock", and the problem will be fixed forever.

This method will be extremely useful, especially for user like me who need to switch between Chinese and English (The problem comes out again whenever you change input method). With my method, the code is not run only once during startup, but each time you press Capslock.
Hope this will help some people out[/SIZE]
[/SIZE]
[SIZE=5][SIZE=3]
[/SIZE]
[/SIZE]

---

