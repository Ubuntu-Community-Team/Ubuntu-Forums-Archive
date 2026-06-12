---
title: "[SOLVED] streamtuner &amp;amp; sound recorder problem!"
date: 2008-07-04
forum: General Help
---

### Post by Dutch70 on 2008-07-04
I have searched the forums, but I guess noob that I am, couldn't find an answer that solved my problem.

anyway, when I use sound recorder with streamtuner and save the music, all I get for play back is a loud buzzing noise. not even a sign of music. I have also changed the setting to capture as I had read in another post but no help. 

Anyone have any ohter ideas?

---

### Post by spiderbatdad on 2008-07-04
there is another package in synaptic called streamripper. It works with streamtuner to record streams

You have to set it up in streamtuner preferences. There is a picture here, in the second post: [http://ubuntuforums.org/showthread.php?t=799754](http://ubuntuforums.org/showthread.php?t=799754)

If you want to use totem, you can also configure that in preferences.

---

### Post by Dutch70 on 2008-07-04
Ok, I actually thought that sound recorder was the same as streamripper, but I've got that figured out now, and it is configured to totem, just a different problem now. When I try to record something, I am getting this error.

```
[getting track name...]
error 36 [SR_ERROR_CANT_CREATE_FILE]
bye...
```

then the page disappears...

on a side note:
 It disappears so fast you cant read anything, then I got the idea to take a screenshot before it was gone...lol

---

### Post by spiderbatdad on 2008-07-04
```
x-terminal-emulator -e %q -d /mnt/Data01/Ripped -r -q
```

Check the syntax?

---

### Post by Dutch70 on 2008-07-04
> **spiderbatdad said:**
> ```
x-terminal-emulator -e %q -d /mnt/Data01/Ripped -r -q
```

Check the syntax?

when I run that in terminal it says 

```
there was an error creating the child process for this terminal.
```

not sure what you mean by "check the syntax" unless that is what I just done.:)

---

### Post by spiderbatdad on 2008-07-04
that isn't a terminal command. it is the configuration setting in streatuner in the preferences application menu:

---

### Post by Dutch70 on 2008-07-04
:lolflag: Oops! Edit: check the next post.

I have the same as yours, with this exception. where you have /Data01, I have /home. 
x-terminal-emulator -e %q -d /mnt/Home/Ripped -r -q

Would that be the problem?

Edit: No,I tried it. same result.

---

### Post by Dutch70 on 2008-07-04
wait! mine is different...

here it is...
```
x-terminal-emulator -e streamripper %q -d /mnt/Home/Ripped -r -q
```

well the only other difference was "streamripper" I tried taking that out and it still didn't work, then I started to put it back and it was already there.

Still getting the same error if anyone has any other suggestion it would be greatly appreciated.

---

### Post by Josey on 2008-07-07
you need to install streamripper in synaptic package manager.

---

### Post by mcduck on 2008-07-08
> **Dutch70 said:**
> :lolflag: Oops! Edit: check the next post.

I have the same as yours, with this exception. where you have /Data01, I have /home. 
x-terminal-emulator -e %q -d /mnt/Home/Ripped -r -q

Would that be the problem?

Edit: No,I tried it. same result.

You have to change the "/mnt/Home/Ripped" into some directory that actually exists on your machine, and where you have write permissions.

---

### Post by Dutch70 on 2008-07-08
Wow, I thought this thread was far gone and forgotten, but I really dont understand. Shouldn't they all exist on my my computer, or I really take it as the /home part that you mean, how could that not exist?

---

### Post by mcduck on 2008-07-08
Unless you have created it yourself, there definitely isn't any "/mnt/Home/Ripped" -directory in Ubuntu.

User's home directories are "/home/USERNAME", and you still need to create the "Ripped" directory or whatever you wan to name it.

Also remember that Linux is case sensitive, so "home" and "Home" would be two different things..

---

### Post by Dutch70 on 2008-07-12
I've tried ceating the "ripped" folders in caps and not, but I still keep getting this error...
```
[getting track name...]
error 36 [SR_ERROR_CANT_CREATE_FILE]
bye...
```
I dont understand what I am doing wrong!

---

### Post by mcduck on 2008-07-12
> **Dutch70 said:**
> I've tried ceating the "ripped" folders in caps and not, but I still keep getting this error...
```
[getting track name...]
error 36 [SR_ERROR_CANT_CREATE_FILE]
bye...
```
I dont understand what I am doing wrong!

Could you give the _exact_ command you are now using?

edit: also, check the paths you have configured in Grip for both ripped & encoded file destinations.. That erros message is telling you that the place where it's supposed to place ripped or encoded files either doesn't exist or you don't have write access there.

---

### Post by spiderbatdad on 2008-07-12
You should not have to create any file or do anything special in order for streamripper to create the file for you...
 try changing to this:

```
x-terminal-emulator -e streamripper %q -d ~/my_streams/Ripped -r -q
```

start a stream, and hit the record button...wait a minute.

Go to home folder and select View "hidden files" look in the folder "~"

there is also a streamripper config file in the folder ./config

---

### Post by Dutch70 on 2008-07-12
ok, I changed it to this, 
```
x-terminal-emulator -e streamripper %q -d ~/my_streams/Ripped -r -q
```

and it appears to be ripping the music, but I cant find it anywhere. even after going to /home and show hidden files. 

Edit: I found it...had to click on several folders. and figure out how to use it...lol

---

