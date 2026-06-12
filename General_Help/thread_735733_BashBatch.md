---
title: "Bash/Batch"
date: 2008-03-25
forum: General Help
---

### Post by Jookia on 2008-03-25
How would I put this batch code

```
@echo off
del /s *.dso
del /s *.db
del console.log
```

into a bash format?

Also, if you don't mind, could you explain what does what? I'm eager to learn.

---

### Post by ibuclaw on 2008-03-26
First, Let's introduce you to BASH using the famous "Hello World" example:
```

#!/bin/bash
echo "Hello World!"

```

I will explain most things in the next code example.

I am presuming what some of the commands are here.
But here goes, a step by step run through of your script

```

**#!/bin/bash**
# First, we initiate the BASH shell using "_#!/bin/bash_"
**#** Hashes are _comments_ after we use this.

# *@echo off*
# This speaks for itself, in BASH we use _stty_ instead of @ to set console options,
# the other difference being that we don't use words such as on or off.
# We use _-_ to turn off the feature and _+_ or just the _name_ to turn it on.

**stty -echo**

*# del /s *.dso*
*# del /s *.db*
*# del console.log*
# I am presuming that del is "_delete_" and /s is "_recursive_".
# BASH uses the command _rm_ to remove files
# and _-r_ to make the removal recursive
# now "rm -r" on it's own my provoke unwanted behaviour in a batch script,
# such as being asked if you are sure that you want to remove the file.
# So we tend to enable the _-f_ or force option.
# Though think about what you are doing first before you execute the script.

**rm -rf *.dso**
**rm -rf *.db**
**rm console.log**

# and lastly. _stty_ isn't temporary, so before the script ends, we turn echo back on.
# else you may find that you can't see anything you type in the terminal thereafter

**stty echo**

# no exit code is needed. The script comes to a natural end.
# But before we can execute the script, we must first make it executable.
# This is done using the command _chmod_ in the terminal 
# along with _+x_ to add the executable _permission_ to it.
# **chmod +x scriptname**
# Then to execute it, we use _./_
# **./scriptname**
# and Voila! One ready made bash script.


```

Hope this explains all to you in a fine detail

And as a tip on the cake, here is a rundown of the script without the comments:
```

**#!/bin/bash**

**stty -echo**
**rm -rf *.dso**
**rm -rf *.db**
**rm console.log**
**stty echo**

```

Regards
Iain

---

### Post by Jookia on 2008-03-26
Thanks, I'd thank you, but I can't find it, if you get thanked for your post then it's cause I could find it.

---

### Post by ghostdog74 on 2008-03-26
you can shorten it
```

rm -rf *.dso  *.db console.log

```

---

### Post by danwood76 on 2008-03-26
> **Jookia said:**
> Thanks, I'd thank you, but I can't find it, if you get thanked for your post then it's cause I could find it.

Its the little medal symbol by the reply/quote buttons!

---

