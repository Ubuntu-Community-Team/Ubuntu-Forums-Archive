---
title: "Trying to make it so that a python script will startup"
date: 2024-01-17
forum: General Help
---

### Post by eraitico on 2024-01-17
I'm trying to startup this script [https://pastebin.com/tqE91NH2](https://pastebin.com/tqE91NH2) but nothing seems to work (ubuntu focal)
Also i would be fine with the script being an executable but it opens and closes immediately, any help is appreciated.

---

### Post by #&amp;thj^% on 2024-01-17
This link is 9 years old but still viable: [https://stackoverflow.com/questions/24518522/run-python-script-at-startup-in-ubuntu](https://stackoverflow.com/questions/24518522/run-python-script-at-startup-in-ubuntu)
Start where it reads "Instructions"

---

### Post by Holger_Gehrke on 2024-01-17
If you mean "automatically start the script at system start or after login" then the previous answer by 1fallen is exactly what you need. But if you mean "how do I start the script (or find out why it doesn't run)", then read on.

Try starting the script from the command line. Open a terminal, use the 'cd' command to make the directory where the script is stored your current working directory and call the script by entering 'python "rmb2key0.py"' (or whatever the script is called on your system). When I tried this it gave me an error, saying I didn't have "pynput" installed. I searched the packages in the repositories with 'apt search pynput' and found 'python3-pynput'. After running 'sudo apt install python3-pynput' I tried again and got another error telling me i needed 'pyautogui'. Searching with 'apt search autogui' showed nothing related to python, so I did a web search. It's a module available through pip (Python installer for packages). So running 'pip3 install --user pyautogui' installed the package (and a bucket full of dependencies ...). Afterwards the script worked ... kind of. It injects a keypress event every time the right mouse button is pressed but doesn't remove the button press from the event queue, so most of the time the context menu pops up and the keypress is evaluated by the handler for that menu (which isn't expecting a '0' key and just discards it). The one program where it worked almost as expected was emacs, because in emacs the rmb is used to set the 'mark' (a second, invisible cursor; it's used to set a 'region', basically the area of text between 'mark' and 'point' (the normal cursor)).

One big warning: this will **not** under any circumstances **work under Wayland** (pyautogui uses Xlib). For security reasons Wayland doesn't allow the insertion of artificial keypresses. So if you're using a recent Ubuntu of any flavour except Xubuntu (which hasn't yet made the jump to Wayland), this can't work unless you choose to use X11 at login.

Holger

---

### Post by MAFoElffen on 2024-01-17
...Or add the other form of the shabang from a Unix type as the first line...
```

#!/usr/bin/env python3

## The rest of the script...
import os
import time
import re
from pynput import mouse
import pyautogui

def on_click(x, y, button, pressed):
    if pressed:
     if button == mouse.Button.right:
        button = pyautogui.press('0')
    
with mouse.Listener(on_click=on_click) as listener:
        listener.join()


```
Made executable with chmod...

Just a note: Starting it via
```

/path/to/ScriptName
# Or if in the same folder already
./ScriptName

```
...That is if where it is stored is not in the $PATH. If it is in the $PATH, it just runs. If not, and if you don't preface it with the path to it, even if in the same folder, it will say not found.

^^^ Thinking back now... No one ever explained the why of that to me. I just "accepted that" as how it is and works for the last 33 years. LOL

EDIT: LOL. After 33 years, i looked it up. Most places skipped over that detail. But found the answer to that understanding between these two answers
> 
When an executable is not in the PATH , you need to specify the path explicitly. ./ is a "relative" path specifier: "starting from here (.) go "no further" (/). If you add the current directory to your PATH environment variable and issue rehash command, you will no longer need it.
###
When you run a command, the shell searches the PATH variable (or some hash table, depending on the shell#) where to find the executable. But usually the current working directory (.) isn't included. So, you need to tell the shell where to find your script by prepending ./ as explained by Floris.

The purpose of that default setting is, that you are saved from accidentally executing a script (in the current dir) which is named e.g. rm instead of the expected command in /bin. This is especially crucial for root, because the local script can behave completely different as you'll expect it!


---

