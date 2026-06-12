---
title: "Error while trying to run /home/andy/bin/python3 paste_snippets.py which is   linked"
date: 2018-07-18
forum: General Help
---

### Post by raleigh3 on 2018-07-18
I made a keyboard shortcut. But I get this message when I try to run it.
  ```
Error while trying to run /home/andy/bin/python3 paste_snippets.py which is  
linked to the key(<Primary>Alt>a) Primary is really the Ctrl key.

```  It works fine in 16.04 but not in 18.04.
  Am I doing something wrong?

---

### Post by TheFu on 2018-07-18
Is paste_snippets.py in a directory in the PATH and set to executable and what's the first line of the file?

---

### Post by raleigh3 on 2018-07-18
Yes. It's in my bin dir and in my path.

#!/usr/bin/env python3 is first line of python script.

---

### Post by TheFu on 2018-07-19
Can you tie the key to /full/path/to/bin/paste_snippets.py?

I assume the script works from /tmp and ~/ and /var and any other directory?

---

### Post by raleigh3 on 2018-07-19
I have tried that with no luck.

---

### Post by raleigh3 on 2018-07-19
I found the problem In the python script. 

```
#!/usr/bin/env python3

import os
import subprocess

home = os.environ["HOME"]
directory = home+"/.config/snippet_paste"
if not os.path.exists(directory):
    os.mkdir(directory)
# create file list with snippets
files = [
    directory+"/"+item for item in os.listdir(directory) \
         if not item.endswith("~") and not item.startswith(".")
    ]
# create string list
strings = []
for file in files:
    with open(file) as src:
        strings.append(src.read())
# create list to display in option menu
list_items = ["manage snippets"]+[
    (str(i+1)+". "+strings[i].replace("\n", " ").replace\
     ('"', "'")[:20]+"..") for i in range(len(strings))
    ]
# define (zenity) option menu
test= 'zenity --list '+'"'+('" "')\
      .join(list_items)+'"'\
      +' --column="text fragments" --title="Paste snippets Ctrl V"'
# process user input
try:
    choice = subprocess.check_output(["/bin/bash", "-c", test]).decode("utf-8")
    if "manage snippets" in choice:
        subprocess.call(["thunar", directory])
    else:
        i = int(choice[:choice.find(".")])
        # copy the content of corresponding snippet
        copy = "xclip -in -selection c "+"'"+files[i-1]+"'"
        subprocess.call(["/bin/bash", "-c", copy])
        # paste into open frontmost file
        paste = "xdotool key Control_L+v"
        subprocess.Popen(["/bin/bash", "-c", paste])
except Exception:
    pass

```


                                      I had to replace this line
     
```
subprocess.call(["nautilus", directory])
  
```
with
      
```
subprocess.call(["thunar", directory]) 
```
  
I do not have nautilus but use thunar as my file manager.

---

### Post by TheFu on 2018-07-19
I thought caja was the default for Mate desktops?

---

