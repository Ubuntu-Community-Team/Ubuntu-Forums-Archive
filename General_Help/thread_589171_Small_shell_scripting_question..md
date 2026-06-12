---
title: "Small shell scripting question."
date: 2007-10-23
forum: General Help
---

### Post by Chris Lappe on 2007-10-23
I am teaching myself to write some simple shell scripts, to automate routine commands, but am running into a small quirk.

Say I write a script and save it as "test.sh", make it executable and everything is fine until I try to run it by typing "test".

Nothing happens and the command prompt returns to normal.

If I type "test.sh", then the script works fine.

Am I supposed to have to type the ".sh" to run a shell script????

---

### Post by aysiu on 2007-10-23
You can just rename the script to not have the .sh extension.

---

### Post by Prospero2006 on 2007-10-24
If it's executable, type:
```

./scriptname

```

Or you could copy it to a directory in the system path like /usr/local/bin.

Then you could just type:
```

scriptname

```

Pros
(All those years using Slack finally paid off!

---

### Post by Chris Lappe on 2007-10-24
> **aysiu said:**
> You can just rename the script to not have the .sh extension.

Tried that, it won't run that way.

---

### Post by Chris Lappe on 2007-10-24
> **Prospero2006 said:**
> If it's executable, type:
```

./scriptname

```

Or you could copy it to a directory in the system path like /usr/local/bin.

Then you could just type:
```

scriptname

```

Pros
(All those years using Slack finally paid off!

Neither of those worked either, I still have to type the full "test.sh" or it won't work.

---

### Post by aysiu on 2007-10-24
> **Chris Lappe said:**
> Tried that, it won't run that way.
Sure it will. I've done it many times before.

Copy your script to /usr/local/bin: ```
cd /path/to/current/location/of/script
sudo cp test.sh /usr/local/bin
``` Rename it to not be .sh ```
cd /usr/local/bin
sudo mv test.sh test
``` Make it executable ```
sudo chmod +x test
``` Run it ```
test
```

---

### Post by Chris Lappe on 2007-10-25
> **aysiu said:**
> Sure it will. I've done it many times before.

Copy your script to /usr/local/bin: ```
cd /path/to/current/location/of/script
sudo cp test.sh /usr/local/bin
``` Rename it to not be .sh ```
cd /usr/local/bin
sudo mv test.sh test
``` Make it executable ```
sudo chmod +x test
``` Run it ```
test
```


Didn't work, it no longer shows the ".sh" on the file, but the script only runs in you type "test.sh", just typing "test" gets nothing.

Is there a difference between the command you used "sudo chmod +X" and what I had used before "sudo chmod 755"?

---

### Post by mahousaru on 2007-10-25
What is the exact error when you try just test?

Can you do

```

whereis test

```

To make sure you don't have another test file in your search paths please.

---

### Post by Chris Lappe on 2007-10-26
> **mahousaru said:**
> What is the exact error when you try just test?

No error, the command prompt just returns.

---

### Post by mahousaru on 2007-10-26
Oh I just realised why... 

test is an existing command or bash function!

---

### Post by Chris Lappe on 2007-10-27
> **mahousaru said:**
> Oh I just realised why... 

test is an existing command or bash function!

Renamed the file, still doesn't work.

:confused::confused::confused::confused:

---

### Post by cwaldbieser on 2007-10-27
> **Chris Lappe said:**
> Renamed the file, still doesn't work.

:confused::confused::confused::confused:

1) Create your script with a name that is not already an command in your command path.  For example, if you think "frotz" would be a good name, check to see if it alread exists:
```

$ type frotz
bash: type: frotz: not found

```
So you know this name is not used.
```

$ mv <scriptname> frotz

```

2) Make sure the script is executable.
```

$ chmod u+x frotz

```

3) Try to run the script from the directory it is in.
```

$ ls frotz
frotz
$ ./frotz

```

If that works, the last step is to move it into your command path (/usr/loca/bin or ~/bin are good places).

---

### Post by Old *ix Geek on 2007-10-27
What did you rename the file?  Please post the following:

. the exact name of the file
. its permissions
. its location
. your location when you're trying to run it
. exactly what you're typing when tying to run the file
. the result of typing **echo $?** after it's run without doing anything

---

### Post by Chris Lappe on 2007-10-28
> **cwaldbieser said:**
> 1) 

If that works, the last step is to move it into your command path (/usr/loca/bin or ~/bin are good places).

I followed your instructions, and things are working better, I just noticed one more thing that may or may not be "normal".

As I write scripts, I save them to a directory under my home folder. "/home/chris/bin/" after I make them executable, I move them to "/usr/local/bin/".  

They are now running fine, as long as I leave the copy in "/home/chris/bin/".  If I delete that copy and leave only the one in "/usr/local/bin/", I get:

"bash: /home/chris/bin/<scriptname>: No such file or directory"

Just a note if it helps, here is the result of my "echo $PATH":

/home/chris/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by cwaldbieser on 2007-10-29
> **Chris Lappe said:**
> I followed your instructions, and things are working better, I just noticed one more thing that may or may not be "normal".

As I write scripts, I save them to a directory under my home folder. "/home/chris/bin/" after I make them executable, I move them to "/usr/local/bin/".  

They are now running fine, as long as I leave the copy in "/home/chris/bin/".  If I delete that copy and leave only the one in "/usr/local/bin/", I get:

"bash: /home/chris/bin/<scriptname>: No such file or directory"

Just a note if it helps, here is the result of my "echo $PATH":

/home/chris/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

It sounds like you are trying to run the script in /home/chris/bin rather than the one in /usr/local/bin.  Are you typing in the full path to the command to run it?

In your script, you could add something like:
```

#!/bin/bash

PROGRAM="$0"
echo "Program is [$PROGRAM]."
FULLPATH=$(readlink -f "$PROGRAM")
echo "Full path to program is [$FULLPATH]."
...

```

That would tell you the path that you entered to run the script as well as the full path to the script that is being run.

Also, you might want to put /home/chris/bin, /usr/local/bin, and /usr/local/sbin at the end of your PATH rather than the beginning.  Normally, if a command exists on the system, you want to use the system command rather than one you made up.  If you want to run your own version of a program, you can always name it something else or alias it, or even type in the full or relative path to it.

---

