---
title: "how to install a script"
date: 2013-11-23
forum: General Help
---

### Post by Buntu Bunny on 2013-11-23
I need to add [this script]("http://wiki.scribus.net/canvas/Hebrew_Flipped_Text") to Scribus, however, I have never worked with scripts before. It seems as though it ought to be a simple matter of copying, pasting, and saving to /usr/share/scribus/scripts, but I notice all the files there are .py or .pyc files. I shouldn't think I would need a full blown course in Python to add someone else's script, but before I do something stupid, would someone please tell me how to do this?

---

### Post by Frogs Hair on 2013-11-23
I'm not familiar with Scribus , but the scripts I have used required making the text file executable from the the text file's proprieties. Right Click > Properties > Permissions > Execute.

---

### Post by Buntu Bunny on 2013-11-23
> **Frogs Hair said:**
> I'm not familiar with Scribus , but the scripts I have used required making the text file executable from the the text file's proprieties. Right Click > Properties > Permissions > Execute.

Thanks Frogs Hair. Putting your reply into my own words, I copy and paste the script to a text file (and save as a ? file), then make the file executable. I'll see what happens

UPDATE: I can't save it to /usr/share/scribus/scripts. I get 

```
Can't open file to write.
```

Nor is there an option to execute in permissions.  :?

---

### Post by Frogs Hair on 2013-11-23
Use gedit to create the text file.

---

### Post by grier-devon on 2013-11-23
You can also make it executable in the terminal by 
```
chmod u+x scriptname
```

As I am a big fan of GUI tools  since more of them become available with each release of Ubuntu and other Linux distro's I also believe learning things through the command line are equally important especially when dealing with scripting. With the chmod command that is basically how you set something to executable, but maybe through your time of scripting especially if you ever are the admin of something you will have to set the permission for the user, group and other as well which will require some knowledge of using the terminal

Information about User groups and permissions with information on using chmod:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Tutorial for using chmod:
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

Have fun

---

### Post by Buntu Bunny on 2013-11-23
Frogs Hair, that was a step forward, but apparently I have to do this as root because I don't have permission to write the file to  /usr/share/scribus/scripts. 

> **grier-devon said:**
> You can also make it executable in the terminal by 
```
chmod u+x scriptname
```

As I am a big fan of GUI tools  since more of them become available with each release of Ubuntu and other Linux distro's I also believe learning things through the command line are equally important especially when dealing with scripting. With the chmod command that is basically how you set something to executable, but maybe through your time of scripting especially if you ever are the admin of something you will have to set the permission for the user, group and other as well which will require some knowledge of using the terminal

Information about User groups and permissions with information on using chmod:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Tutorial for using chmod:
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

Have fun

grier-devon, a huge +1 to learning the command line. Even making it executable, I'll still have to get it to the correct directory, which brings me back to root. 

I can see that I have my learning work cut out for me.

---

### Post by grier-devon on 2013-11-23
> **Buntu Bunny said:**
> Frogs Hair, that was a step forward, but apparently I have to do this as root because I don't have permission to write the file to  /usr/share/scribus/scripts. 



grier-devon, a huge +1 to learning the command line. Even making it executable, I'll still have to get it to the correct directory, which brings me back to root. 

I can see that I have my learning work cut out for me.

Are you using "cp" to copy? Yet again if the system is requiring root privileges using the command line has it's added benefits. I am sure there is a way to have admin privileges in the GUI but that is something I am unsure of, here is the man page for using "cp". If you try "cp" and it says you do not have the privileges throw a "sudo" infront of the command to be prompted for your password to give yourself privileges. If you are having a hard time with cp let us know and we will help you.

---

### Post by Frogs Hair on 2013-11-23
As with everything in the file system have elevated privileges are required  to make changes. The chmod commands are useful as well if you want to use the terminal and if not use the following
  ```
gksudo nautilus
```

---

### Post by Buntu Bunny on 2013-11-23
> **grier-devon said:**
> ... <snip> ... If you are having a hard time with cp let us know and we will help you.

I will do that. I have to get to work now, but will come back to this later. 

> **Frogs Hair said:**
> As with everything in the file system have elevated privileges are required  to make changes. The chmod commands are useful as well if you want to use the terminal and if not use the following
  ```
gksudo nautilus
```

Rather, for me, thunar(?)

---

### Post by Buntu Bunny on 2014-03-18
Follow-up: I finally got this conquered. For anyone else looking for similar information, Scribus has a scripter - Script > show console. It was a simple matter of pasting the script into the console and saving the script in the correct directory, usr/share/scribus/scripts. 

This is in Scribus 1.4, however, I will need to prepare the manuscript in 1.5 because I need its PDF/X-1 capabilities to submit to the printer. I still need to find out if 1.5 will recognize the corrected text, or if I'll need to do the whole thing all over again!!! But that's a whole 'nother ballgame. 

If it isn't chickens, it's feathers. :)

Update: Scribus 1.5 does indeed acknowledge the script changes. That's a relief.

---

### Post by Buntu Bunny on 2014-03-25
One more update, I hope, the last. Apparently the script didn't save in usr/share/scribus/scripts. At least it wasn't there when I went to use it again. Nor could I get it to save there (permissions?). Anyway, I did a little more research and found instructions for installing scripts in Scribus [here]("http://booki.flossmanuals.net/scribus-2/_draft/_v/1.0/scripter-and-scripts/"). Nutshell version - copy and paste to a text editor, save as a .py file wherever desired. In Scribus, Script menu > execute script, then browse to it. After that it shows up under script > recent scripts. 

One thing I have to say about Ubuntu is that there's always something to learn. :)

---

