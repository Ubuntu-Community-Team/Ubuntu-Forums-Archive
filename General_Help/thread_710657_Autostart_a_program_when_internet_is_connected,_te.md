---
title: "Autostart a program when internet is connected, terminate it when connection lost?"
date: 2008-02-28
forum: General Help
---

### Post by kybishop on 2008-02-28
I was hoping to autostart the folding@home program when I'm connected to the internet, and shut it off when I lose the connection.

If its of importance, im running kubuntu (with kde of course)

Any help would be apprieciated.
Thanks, Kybshop

---

### Post by JoeLinux117 on 2008-02-28
Maybe I can help a little.

Question: Do you connect to the Internet using DHCP (just in case, it's basically when your IP address and other information is provided automatically to your computer)?

If you're using DHCP, then you can place a script in **/etc/dhcp3/dhclient-exit-hooks.d/** (this directory contains scripts that are read by "dhclient" -- the program that handles DHCP in the background for you -- upon completion of DHCP tasks).  By comparison, the /etc/dhcp3/dhclient-enter-hooks.d/ directory contains scripts that are processed *before* the DHCP process actually begins.

The script would start the folding@home program (which seems really cool, I'm actually considering installing it now).  It may look something like this:

```
#!/bin/bash

folding@home &
```

I'm not sure what the program name is, so I just wrote "folding@home".  That means that you should replace that with whatever the program is actually named (if it's "folding", then that line would read "folding &").  You can name the script whatever you want, just make sure that it's executable (if you name the script "folding", for example, you can type "sudo chmod a+x folding" to give it the executable attribute).

That would ensure that the program starts when you receive an IP address (presumably that would mean that you have an Internet connection as well, unless your network setup is different that most of America).

Now, to close the program upon loss of Internet connection is a different story.  For this, maybe you can add a script to your crontab (the scheduler) to check for an Internet connection every 5 mins or so, and if it doesn't find one, then kill the program.

That one might look something like this:

```
#!/bin/bash

ping -c 2 google.com

if [ "$?" -ne "0" ];
  then pkill folding@home;
fi
```

Put that in your crontab by typing "crontab -e", and once you get to edit the crontab, insert a line that looks like this (assuming this script is called "folding_terminate":

```
*/5 * * * * folding_terminate
```

That will run it every 5 mins.  Once it sees that it can't reach google.com, it will attempt to terminate the program "folding@home" (again, if that's not the program name, change it).

Hope this helped!



--JoeLinux
[Learn About Linux - A World Without Windows]("http://www.learnaboutlinux.net")

---

### Post by kybishop on 2008-02-28
You're awesome joe!

---

### Post by kybishop on 2008-02-28
One of the folders in the pathway to fah6 (the name of the folding@home program) has spaces in it. would this be the proper format in the first script?
'/home/kyle/Settings and Miscellaneous/FoldingAtHome/fah6'

I was also going to put the terminate script in the FoldingAtHome folder, so would that also be the correct format to input into crontab, where you wrote folding_terminate, substituting fah6 for the name of the script?

one last question =D
To execute folding@home, I must navigate to the folder listed above, and then type ./fah6
I've tried typing out the whole directory, with a . at the beginning, but it doesn't seem to work. Will this change how I should enter it into the starting script?

PS thanks for your help thus far, glad to learn more about linux any day!

---

### Post by JoeLinux117 on 2008-02-29
> One of the folders in the pathway to fah6 (the name of the folding@home program) has spaces in it. would this be the proper format in the first script?
'/home/kyle/Settings and Miscellaneous/FoldingAtHome/fah6'
Yes.

> I was also going to put the terminate script in the FoldingAtHome folder, so would that also be the correct format to input into crontab, where you wrote folding_terminate, substituting fah6 for the name of the script?

> To execute folding@home, I must navigate to the folder listed above, and then type ./fah6
You could actually add this in to the script, if you *must* navigate to the folder beforehand.  Just add "cd /home/kyle/Settings and Miscellaneous/FoldingAtHome/" on a line somewhere above the actual command to run it.

> I've tried typing out the whole directory, with a . at the beginning, but it doesn't seem to work. Will this change how I should enter it into the starting script?
You should be able to run most executables one of three ways:

1)  Absolute path -- You type the full path to the executable (e.g., "/usr/bin/amarok")
2)  Relative path -- You type the path relative to your current directory (e.g., if you're in the directory "/usr/bin", you can just type "./amarok")
3)  Based on your PATH variable -- You just type the name of the executable, because the path is named for you in the PATH environment variable (e.g., just type "amarok", because "/usr/bin" is already named in your PATH variable... just type "echo $PATH" to see what's in your PATH variable, Windows also has this variable)

I guess the exception to specifying the whole path for the executable might be if "fah6" has some reference within it to the current directory, ".", which would only be valid if you're already in the directory that folding@home is expecting.  So if "fah6" has "cat ./beach.txt" (beach was the first thing I thought of, sorry, I'm a South Floridian), then that would only apply if "beach.txt" could be found in the current directory.  So if you're in "/home/kyle", there's no "beach.txt" found there, so "fah6" wouldn't run properly.  I could see that as a possibility, albeit a result of poor programming practices.  I hope I didn't just confuse you with that.

Let me know if this helped!


--JoeLinux

---

### Post by JoeLinux117 on 2008-02-29
> I was also going to put the terminate script in the FoldingAtHome folder, so would that also be the correct format to input into crontab, where you wrote folding_terminate, substituting fah6 for the name of the script?
I meant to say something after this quote in my last post.  Where I wrote "folding_terminate", that's just the name I gave to that script I wrote in the first post (the second script).  So if you copied:

```
#!/bin/bash

ping -c 2 google.com

if [ "$?" -ne "0" ];
  then pkill folding@home;
fi
```
into a file called "folding_kill", then that same crontab entry would look like this:

```
*/5 * * * * folding_kill
```
See what I mean?  Just substitute the "folding@home" *within* the script with the name of the program (which I would presume would be "fah6").

So it would then look like this:

```
#!/bin/bash

ping -c 2 google.com

if [ "$?" -ne "0" ];
  then pkill fah6;
fi
```
And I think that would be it.  Let me know if it works!

--JoeLinux

---

