---
title: "how do I add a new directory to the path?"
date: 2008-06-13
forum: General Help
---

### Post by joekidston on 2008-06-13
Hi, I'm new to Linux, so please excuse me if this is a stupid question (maybe should be in absolute beginner's talk?)

I am trying to run an atmospheric simulation model (the Portable University Model of the Atmosphere, PUMA, in case anyone knows it).  The model has it's own Model Starter graphical user interface to start it running.  When i click Save and Run, I get a message in the terminal that says

sh: puma/bld/most_puma_build: not found

So the program cannot find this executable.  I can see the executable when I cd into puma/bld, and my current directory is the parent of the puma directory.

Do I need to set the system-wide path so that it includes the parent of puma the puma directory?  I have tried that by adding the line 

PATH=${PATH}:/home/joe/Desktop/PUMA/Most15/

to ~/.bashrc

but it hasn't helped

Any ideas?

Thanks for any replies.

---

### Post by drs305 on 2008-06-13
> **joekidston said:**
> Hi, I'm new to Linux, so please excuse me if this is a stupid question (maybe should be in absolute beginner's talk?)

I am trying to run an atmospheric simulation model (the Portable University Model of the Atmosphere, PUMA, in case anyone knows it).  The model has it's own Model Starter graphical user interface to start it running.  When i click Save and Run, I get a message in the terminal that says

sh: **puma/bld/most_puma_build**: not found

So the program cannot find this executable.  I can see the executable when I cd into puma/bld, and my current directory is the parent of the puma directory.

Do I need to set the system-wide path so that it includes the parent of puma the puma directory?  I have tried that by adding the line 

PATH=${PATH}:**/home/joe/Desktop/PUMA/Most15/**

to ~/.bashrc

but it hasn't helped

Any ideas?

Thanks for any replies.

The paths don't seem to match. Case matters in ubuntu as well - *PUMA* does not equal *puma*. Is "most_puma_build" the app or script?

You can see what the current path is with:
```
echo $PATH
```

In ~/.basrc, try this. Resolve where the script or app really is, since the path you tried and the error message don't point to the same place. (You have a "Most15" folder included.) If "most_puma_build" is a folder, add that to the end. The following is the PATH statement if the app or script is in /home/joe/Desktop/puma/bld:
```
export PATH=$PATH:$HOME/Desktop/puma/bld/**:**
```
The colon separates path locations if you have others to add.

After making the changes, you must close the terminal or refresh it with "source ~/.bashrc" for them to take effect. Try the *echo $PATH* statement again to view your new PATH.

---

### Post by joekidston on 2008-06-13
Thanks for the reply.

I should have been more specific about the paths.

The executable that the programme is looking for is in 

/home/joe/Desktop/PUMA/Most15/puma/bld

and is called most_puma_build.

When I do echo $PATH, I see that 

:/home/joe/Desktop/PUMA/Most15/

is in the path.  To recap, the error message is 

sh: puma/bld/most_puma_build: not found

Do I need to add /home/joe/Desktop/PUMA/Most15/puma/bld to the path specifically, because the programme can't look to sub-directories of an existing directory?

Thanks again

---

### Post by joekidston on 2008-06-13
Well, I just added 

/home/joe/Desktop/PUMA/Most15/puma/bld

to the path, which is the directory where the executable sits, and that doesn't help either...

Hmmmm

---

### Post by ByteJuggler on 2008-06-13
> **joekidston said:**
> 
sh: puma/bld/most_puma_build: not found


The above indicates that the shell script is specifying the path to the most_puma_build executable when trying to run it (e.g. "puma/bld/") and then not finding the file where it's supposed to be, hence the error message.  

Note that when an application is run with a path specified, the system/search path is irrelevant and not used.  

So, to fix your problem, Either the shell script must be fixed to use the correct path explicitly (e.g. the "puma/bld/" part must be corrected so it resolves properly from the current directory, or you have to make it even more explicit by specifying it from root, e.g. something like /home/user/PUMA/puma/bld... or whatever, so the current directory becomes irrelevant), 

Or alternatively, the path must be removed from the line in the shell script attempting to run the executable completely (e.g. remove the "puma/bld/" bit from the line trying to run most_puma_build), so that then the shell will fall back on the search/system path to try and locate the most_puma_build executable that way, which it should find if you've added the path to your .bashrc/.bash_profile/ or /etc/profile file (which you seem to have done.)  You can check whether the system can find the file using the path by using the "which" or "whereis" command, e.g.

```

which most_puma_build

```

or

```

whereis most_puma_build

```

They both do more or less the same thing.  If you don't get any results, then your PATH is not set up right for the executable to be found.

---

### Post by drs305 on 2008-06-13
> **joekidston said:**
> Well, I just added 

/home/joe/Desktop/PUMA/Most15/puma/bld

to the path, which is the directory where the executable sits, and that doesn't help either...

Hmmmm
When you run echo $PATH, does it show something like:
```
 /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/home/joe/Dekstop/PUMA/Most15/puma/bld:
```


By the way, is the file executable?
```
chomod a+x /path.to.script.or.app/script.or.appname
```

---

### Post by joekidston on 2008-06-13
When I echo $PATH, I see

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/matlab/bin:/home/joe/Desktop/PUMA/Most15/:/home/joe/Desktop/PUMA/Most15/puma/bld


So the system can see everything, although I think it only needs to see the Most15 directory.

ls ~/Desktop/PUMA/Most15/puma/bld -l

returns 

-rwxr-xr-x 1 joe joe 257 2008-06-13 23:46 most_puma_build

so I guess it's executable?

Perhaps there is a setting on the graphical user interface for the model itself where I tell it what it's base directory should be (i.e. /home/joe/Desktop/PUMA/Most15/), but I can't see any way that I could do that...

Thanks again

---

### Post by joekidston on 2008-06-13
aha, apparently it was because I didn't have a c shell ThingAmaJig installed - i did

sudo apt-get install tcsh

and now I have a whole new load of errors!

Sorry for wasting your time

Thanks again

---

### Post by drs305 on 2008-06-13
> **joekidston said:**
> aha, apparently it was because I didn't have a c shell ThingAmaJig installed - i did

sudo apt-get install tcsh

and now I have a whole new load of errors!


Then it looks like it's time for a new thread! ](*,)

---

