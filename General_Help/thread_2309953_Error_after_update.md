---
title: "Error after update"
date: 2016-01-14
forum: General Help
---

### Post by Otto-C on 2016-01-14
Up to date 12.04 system.
Tuesday (1-12-16) evening did system update powered down. Wednesday evening opened a New file. Upon
entering text type info and saved same. The icon changed from usual text file to a film strip. Upon trying to
open went to the movie player screen, and showed "error occured GstDecodeBin2:This appears to be a text
file" with an "OK"
How to recover from this?

tia
otto-c

---

### Post by Bucky Ball on 2016-01-14
You opened a new file? Using what software? What kind of file? You saved it as what?

Please provide more detailed information, thanks. To recover that file you would need to change the .mov or .mp4 or whatever to that of the filetype you are intending. Sounds like a text document, but there are lots of filetypes for them. Try .odt

---

### Post by Otto-C on 2016-01-15
Here are the steps I have used for a very long time.

Home
MyStuff
Create New Document
Create Empty Document
   Rename to New1
  Open New1
  Enter new stuff to file such as the following:
GAS09.DAT,GAS09.RPT,HIST09.DAT,HIST09.RPT
GAS10.DAT,GAS10.RPT,HIST10.DAT,HIST10.RPT
GAS11.DAT,GAS11.RPT,HIST11.DAT,HIST11.RPT
GAS12.DAT,GAS12.RPT,HIST12.DAT,HIST12.RPT
GAS13.DAT,GAS13.RPT,HIST13.DAT,HIST13.RPT
GAS14.DAT,GAS14.RPT,HIST14.DAT,HIST14.RPT
GAS15.DAT,GAS15.RPT,HIST15.DAT,HIST15.RPT

  Clicked Save
  Exited to MyStuff
Icon now changes to film strip.
As above the file can no longer be opened by clicking on it.

hth
otto-c

---

### Post by Otto-C on 2016-01-20
Bump

---

### Post by Vladlenin5000 on 2016-01-20
What's the exact name of your new file?

---

### Post by sandyd on 2016-01-20
Hi, can you post the output of
```

file *path/to/file*
```

---

### Post by Otto-C on 2016-01-23
New1

---

### Post by Otto-C on 2016-01-23
I'm sorry do not know how to do your 'file' thing.
Please give me an example. I'm 'otto', going to dir 'MyStuff', the file is 'New1'

---

### Post by oldos2er on 2016-01-23
Try ```
file MyStuff/New1
```

---

### Post by Bucky Ball on 2016-01-23
> **Otto-C said:**
> I'm sorry do not know how to do your 'file' thing.


You mean code tags? See the link in my signature. You use [noparse]```
put_terminal_output_here
```[/noparse]. You get:

You get:

```
put terminal output here
```

---

### Post by Otto-C on 2016-01-23
$ file MyStuff/New1
```

MyStuff/New1: ASCII text

```

---

### Post by Vladlenin5000 on 2016-01-23
Typically those files are correctly recognized and handled in Linux and should open with the default text editor - gedit in standard Ubuntu -. They aren't recognized by Windows as such unless you append the .txt extension to the name but that isn't relevant for your case. The reason I asked for the exact file name was in the hope to identify something that might have 'fooled' the system but I was wrong.

The only thing I can suggest at the moment is to right-click it, choose "open with..." and then select the proper application. Needless to say this doesn't solved the underlining issue.

---

