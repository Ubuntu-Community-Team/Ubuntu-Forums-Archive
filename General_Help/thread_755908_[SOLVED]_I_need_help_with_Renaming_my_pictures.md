---
title: "[SOLVED] I need help with Renaming my pictures"
date: 2008-04-15
forum: General Help
---

### Post by linuks on 2008-04-15
Hello all,

After searching the net for about two days, I'm seeking help of linux wizards.

I have a pretty big collection of MP3's (50GB). I'm using Ampache to stream the music from home to work. I love the look of the ampache, especially art work display. Sometimes I have trouble with art being displayed. So, I set up ampache to search music folders for "folder.jpg" art work first (second option is Amazon db search). Now, almost none of my jpegs are named "folder.jpg".

task: What I'm trying to do is: Find all the jpgs (so easy to do) and then rename every jpg in each directory to "folder.jpg" (not so easy to do for me).

I'm still going to be searching for the solution before someone hopefully answers my question here. I don't give up that easily ;).

Thank you in advance guys,
Sani

---

### Post by ryanhaigh on 2008-04-15
```
#!/usr/bin/env python

import os
path='/path/to/music/collection/'
for root, dir, files in os.walk(path):
    for file in files:
        if file.endswith('.jpg') or file.endswith('.JPG'):
            os.rename(root+os.sep+file, root+os.sep+'folder.jpg')

```

This script will search for all files in the path recursively, files ending with jpg or JPG will be renamed to folder.jpg. Keep in mind that if multiple images exist in one location only one will remain.

---

### Post by ryanhaigh on 2008-04-15
```
#!/usr/bin/env python

import os
import shutil

path='/path/to/music/collection/'
for root, dir, files in os.walk(path):
    for file in files:
        if file != 'folder.jpg':
            
            if file.endswith('.jpg') or file.endswith('.JPG'):
                shutil.copyfile(root+os.sep+file, root+os.sep+'folder.jpg')
                #os.rename(root+os.sep+file, root+os.sep+'folder.jpg')

```
This is an alternative that will copy rather than rename, because trying to copy folder.jpg to folder.jpg will obviously not work the additional check is required.

One last version:

```

#!/usr/bin/env python

import os
import shutil
path='/path/to/music/collection/'
for root, dir, files in os.walk(path):
    for file in files:
        if file.endswith('.jpg') or file.endswith('.JPG'):
            if not os.access(root+os.sep+'folder.jpg', os.F_OK):
                print root+os.sep+file+' renamed to folder.jpg'
                shutil.copyfile(root+os.sep+file, root+os.sep+'folder.jpg')
                #os.rename(root+os.sep+file, root+os.sep+'folder.jpg')
            else:
                print root+os.sep+'folder.jpg exists'


```

This one checks whether folder.jpg exists already and if it does the copy is not carried out and a message is printed, if it is does not then the file is copied and you are told.

---

### Post by linuks on 2008-04-15
Ryan,

You are really THE Wizard. It didn't even take you a long time to provide me with the solution. The warning about having a few pics in a dir, was very nice. I was prepared for that and there was only one pic (front cover) in each dir. ;)

Thank you so much for your help.
Sani

---

### Post by ryanhaigh on 2008-04-15
No problem, there is also a great GUI tool called pyrenamer that is great for situations like this and just about any other renaming operation. You can mark this thread as solved using the threadtools menu on the top right so that people know it provides an answer to the issue that you (and possibly they) have.

---

### Post by linuks on 2008-04-15
Solved! Thanks for additional recommendations Ryan.

Be good.
Sani

---

### Post by jago25_98 on 2008-04-15
krename too

---

