---
title: "can't create more then one script"
date: 2008-06-12
forum: General Help
---

### Post by guimenez on 2008-06-12
Hello

i can just create one script in ubuntu

i make a script in /home/bin and start like this:
#bin/sh

but if i make another one, it overwrite the older script.

why i can't make more then one script?????????????'

please help me

---

### Post by x1a4 on 2008-06-12
Hi,

The first line should be 
```
#**!**/bin/sh
```
or whatever shell you want to use for your script, eg: 
```
#!/bin/bash
```
or
```
#!/bin/zsh
```
or
```
#!/bin/tcsh
```
etc

/bin/sh is symlinked to /bin/dash (the Debian Almquist Shell)

The script should be in /home/<yourusername>/bin

NOT named /home/<yourusername>/bin but inside the ~/bin/ directory.  Each script should have its own file name:

/home/<yourusername>/bin/funkyscript1
/home/<yourusername>/bin/greatscript2
/home/<yourusername>/bin/amazingscript3
etc

---

### Post by p_quarles on 2008-06-12
Moved to General Help.

---

### Post by guimenez on 2008-06-13
thanks for the help

but it still the same problem, if i have a script with any name like video then create a new one called audio, after saving it change the first script(video) but i'm edting the script sound

i don't know what to do

---

### Post by ddales on 2008-06-13
What are you using to edit the scripts?

You have to create a script, save it, close it, then do the same for the next script.

For example:

vi /home/myuser/audio
#!/bin/bash
enter some function
enter another funtion

:w
:q

vi /home/myuser/video
#!/bin/bash
enter some function
enter another funtion

:w
:q

Hope that helps

---

### Post by guimenez on 2008-06-13
i'm using gedit like always.

even if try it with vim, after save the script, it change all scripts in my folder /home/username/bin

:(

---

### Post by KeyserSoze93 on 2008-06-13
Make sure ~/bin is a folder:
"file ~/bin"

See what's in there (if anything...):
"ls ~/bin"

Write them, by calling gedit from the command line with a new file:
"gedit ~/bin/blah"
"gedit ~/bin/test"

Make them executable:
"chmod +x ~/bin/*"

Run them (directly, not worrying yet about making sure ~/bin is in your path:
"~/bin/blah"
"~/bin/test"

What happens when you do that?

---

### Post by guimenez on 2008-06-13
finnaly

thanks ;)

the problem its that i've always made a copy of the script then change the script code and save to another file.

i need do make new any time i build a script

thanks

---

