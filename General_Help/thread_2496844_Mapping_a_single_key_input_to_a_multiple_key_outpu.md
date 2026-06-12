---
title: "Mapping a single key input to a multiple key output"
date: 2024-04-14
forum: General Help
---

### Post by justsomeguyinslc on 2024-04-14
Hi folks.

I am trying to figure out how to map one key to Output multiple keys. For example:

If I press 5

I would like it to Output

1234567


Does anyone have any idea how I might do this? I tried using input remapper but so far no luck

Thank you all.

---

### Post by dragonfly41 on 2024-04-14
I use Actiona (in repo) for such UI tricks. But there is also xdotool and Autokey.

---

### Post by justsomeguyinslc on 2024-04-15
Autokey works perfectly for me.

Thanks for suggestion.

Take Care.

---

### Post by TheFu on 2024-04-15
Some other options:
xdotool ydotool dotool cnee xnee .... plus 50 others.

Also, many window managers can do this in the config files.

I would caution against having just 1 simple, commonly used, key to start entering anything.  5 ---> "123456" is probably a bad idea.  Perhaps alt-5 or cntl-5 would be safer choices?  Or if you make a script, 5.  Then it would be "5<enter>" in a terminal or other launcher. That would be pretty safe, but you'd likely need to move the cursor to the text-entry location in that script.  With cntl-5, you could just type the longer text you'd like to have.

I use xdotool (with X11), to move the mouse to a specific window and location inside that window, select everything, move to another window, paste it, then move to a 3rd window to wait as the first window running a test script updates.  Then the move-select, move-paste, move-wait happens again.  This is all needed because the refresh inside the first window can be instantaneous or take up to 20 seconds.  For a while, I did all of this manually, but since there were about 100 times this needed to happen, I decided to automate it down to <enter> to begin the cycle.  I'd love to have a way to have the first window's contents appended to a file over and over, but that isn't possible due to the application.
**my-select-paste** bash script follows:
```
#!/bin/bash

# move to the window to copy data
/usr/bin/xdotool mousemove --sync 300 750
sleep .1s

# cntl-a to place all text into the X-buffer
/usr/bin/xdotool key --clearmodifiers "Control_R+0x61"
sleep .1s

# Move to paste window
/usr/bin/xdotool mousemove --sync 300 1070

# Paste copied data from the X-buffer
/usr/bin/xdotool click 2 
sleep .1s

# Add  a newline
/usr/bin/xdotool key --clearmodifiers Return
sleep .1s
# Move to the my-select-paste terminal and rerun it.  cntl-c to cancel to loop.
/usr/bin/xdotool mousemove --sync 1500 1070
read -p "Enter to continue..."
my-select-paste
```

The location of the windows involved matters. I have a script that launches 2 xterms to specific locations and moves a browser window then resizes it.  Also, my window focus is set to follow the mouse. I suppose other people would click at the location with button 1, rather than just move the mouse.  I've use focus-follows-mouse for almost 30 yrs, so I won't be changing.  There's a tool that will report any input key/mouse action.  There are tools that will record all of them, but there's little need to have hundreds of mouse-move events replayed.  Just go to the last location, as I've shown.  Initially, I automated everything by using cnee to record it, them playback the recording, but any tiny change to the website broke those actions.  Button locations had to be extremely exact and when new buttons were added by the website, everything after that point broke. I ended up analyzing the web page and creating a script that created a selenium script that has been 100% perfect for nearly a year, regardless of website changes.

Anyway, seeing a full automation script can make things clearer. Hope it helps.  The select-move-paste-move happens extremely fast, instigated with just the <enter> on a keyboard.  If I wanted, it could type all of Shakespeare's works with that <enter>.

I don't know if the delay is needed, but figured moving the mouse and getting the focus to recognize the next window as active wouldn't be immediate on a loaded computer, working hard, so why not have a tiny, tiny, delay to avoid a possible issue?

The nice thing about ActionA is there's a little recording GUI that many people find easier to work inside.  Definitely worth a look.

---

### Post by justsomeguyinslc on 2024-04-15
I actually ended up using the sequence of numbers to output my desired string. Seems to be working fine so far. Autokey has an option where you can tell it do not do the translation if the shortcut string is part of other text. However, I appreciate your code there and I'm going to save it future use. One of these days I will actually hone my talents to the point where I can design scripts myself. Maybe, heh. Thanks.

---

### Post by dragonfly41 on 2024-04-15
Clearly OP has AutoKey working. But for the record since @TheFu mentioned Selenium in his contribution, I throw in [SikuliX]("http://sikulix.com/") to experiment with. And I must not forget [Albert]("https://albertlauncher.github.io/"). In Albert a single trigger key can launch Python extensions.

---

### Post by him610 on 2024-04-15
> If I press 5

I would like it to Output

1234567
What do you do when you just want 5 to be 5?

---

