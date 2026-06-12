---
title: "Bash Scripting (CLI)...Please Help"
date: 2021-08-23
forum: General Help
---

### Post by wyattwhiteeagle on 2021-08-23
I didn't know which forum to post this in or how to make it "easy on the eyes"

The section below isn't exactly a "step by step" easy to follow guide.
It's a section at the Bash Scripting link in my signature.

I will be using this post as a guide for posting my questions.
> [B]
Scripting[/B]

[COLOR=#333333][FONT=Ubuntu]**NOTE**: The commands given in the scripting section are to be put into the text editor and not in the terminal unless instructed otherwise.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Bash is primarily a scripting language, so it would be a crime not to talk about scripting. Let's dive straight in with a bash script. More precisely the infamous "Hello World" script. You can create a bash script by opening your favorite [text editor]("https://help.ubuntu.com/community/gedit") to edit your script and then saving it (typically the .sh file extension is used for your reference, but is not necessary. In our examples, we will be using the .sh extension).[/FONT][/COLOR]

 #!/bin/bash         

echo "Hello, World"[COLOR=#333333][FONT=Ubuntu]The first line of the script just defines which interpreter to use. NOTE: There is no leading whitespace before #!/bin/bash. That's it, simple as that. To run a bash script you first have to have the correct file permissions. We do this with [chmod]("https://help.ubuntu.com/community/FilePermissions") command in terminal (change mode) as follows:[/FONT][/COLOR]
chmod a+x /where/i/saved/it/hello_world.sh   #Gives everyone execute permissions
# OR
chmod 700 /where/i/saved/it/hello_world.sh   #Gives read,write,execute permissions to the Owner[COLOR=#333333][FONT=Ubuntu]This will give the file the appropriate permissions so that it can be executed. **Now open a terminal and run the script like this**:[/FONT][/COLOR]
/where/i/saved/it/hello_world.sh[COLOR=#333333][FONT=Ubuntu]Hopefully you should have seen it print Hello, World onto your screen. If so well done! That is your first Bash script.

[/FONT][/COLOR]

---

### Post by wyattwhiteeagle on 2021-08-23
The way I understood it, I open gedit, pasted the below making sure there was no "white space", clicked to save, named it "hello_world.sh" and saved it.
It saved to /home/wyatt.
When I ran /home/wyatt/hello_world.sh it said, "bash: /home/wyatt/hello_world.sh: Permission denied"

No where in the Guide does it say what to do if it doesn't "print on the screen"

The guide said that chmod will give permissions.

What did I do wrong?
How should it look?
How should I have ran it?

> #!/bin/bash         


echo "Hello, World"
chmod a+x /where/i/saved/it/hello_world.sh   #Gives everyone execute permissions
# OR
chmod 700 /where/i/saved/it/hello_world.sh   #Gives read,write,execute permissions to the Owner



> wyatt@wyatt-Aspire-E1-532:~$ /home/wyatt/hello_world.sh
bash: /home/wyatt/hello_world.sh: Permission denied
wyatt@wyatt-Aspire-E1-532:~$ 


---

### Post by deadflowr on 2021-08-23
Those are two separate things.
The first is the script
```
#!/bin/bash

echo "Hello, World"
```
which you copy into a file and name that file something like hello-world.sh

The second is setting the required permissions for the file in order to run it.
```
chmod a+x /where/i/saved/it/hello_world.sh #Gives everyone execute permissions
# OR
chmod 700 /where/i/saved/it/hello_world.sh #Gives read,write,execute permissions to the Owner
```
The important part of this section are the parts before the # symbols as those parts are not read by the system.
They are typically used for comments about the commands like they do here.
So the actual commands would look this this
```
chmod a+x /where/i/saved/it/hello_world.sh 
```
or 
```
chmod 700 /where/i/saved/it/hello_world.sh 
```

You only need to run one of those chmod commands.

---

### Post by wyattwhiteeagle on 2021-08-23
I changed it to...
```
#!/bin/bash         

echo "Hello, World"
chmod a+x /where/i/saved/it/hello_world.sh
```

Ran this in terminal
```
/home/wyatt/hello_world.sh
```

Terminal still says "Permission denied"

---

### Post by deadflowr on 2021-08-23
No.
The sections I posted are as they should be, don't combine things that aren't already combined.

The first part
```
#!/bin/bash

echo "Hello, World"
```
is to be saved as is to a file.
That's it.
That's the script.

The second part
```
chmod a+x /where/i/saved/it/hello_world.sh
```
is to be run inside a terminal.
This command is what sets to required settings in order to run the script.

Perhaps I should have clarified the point of running the chmod command in a terminal.
But I thought the wiki already explained that.

---

### Post by wyattwhiteeagle on 2021-08-23
> **deadflowr said:**
> 
Perhaps I should have clarified the point of running the chmod command in a terminal.
But I thought the wiki already explained that.

Thank you.
I will try that.

The Wiki says the below and so when I ran that, the terminal said "No such file or directory"

> [COLOR=#333333][FONT=Ubuntu]**Now open a terminal and run the script like this**:[/FONT][/COLOR]
```
/where/i/saved/it/hello_world.sh
```[COLOR=#333333][FONT=Ubuntu]Hopefully you should have seen it print Hello, World onto your screen. If so well done! That is your first Bash script.[/FONT][/COLOR]


---

### Post by deadflowr on 2021-08-23
The* /where/i/saved/it/hello_world.sh* is only an example name.
Unless you created it there is no such location as /where/i/saved/it.

What name did you save the file as?
And do you know where you saved the file?

---

### Post by wyattwhiteeagle on 2021-08-23
> **deadflowr said:**
> What name did you save the file as?
And do you know where you saved the file?

I must be either missing something or doing something wrong.

I named the file as hello_world.sh and saved it in /home/wyatt

I changed it to this...
> #!/bin/bash


echo "Hello, World"


Changed to this and entered into the terminal...
> chmod a+x /home/wyatt/hello_world.sh

And Terminal says...
> wyatt@wyatt-Aspire-E1-532:~$ chmod a+x /home/wyatt/hello_world.sh
wyatt@wyatt-Aspire-E1-532:~$ 

That's all...terminal said nothing else and nothing else seems to have happened

Then I changed the a+x to 700...same thing...nothing from terminal and nothing happened

---

### Post by The Cog on 2021-08-23
This is all just basic stuff that a beginner has to get through. Don't worry, once you know what's going wrong it will all quickly make sense.
Two things I was told very early on when I started:
1- Linux generally says nothing if there's no problem. There's no "Yes I did that OK" message. 
2 - Linux is case sensitive - this catches windows users out a lot. hello_world.sh and Hello_world.sh are different files, and both could exist next to each other.
So the face that this command didn't complain means it was successful, and execute permission has now been applied to that script file.
```
wyatt@wyatt-Aspire-E1-532:~$ chmod a+x /home/wyatt/hello_world.sh
wyatt@wyatt-Aspire-E1-532:~$
```
You should now be able to run the script with this command:
```
wyatt@wyatt-Aspire-E1-532:~$ **/home/wyatt/hello_world.sh**
```

---

### Post by wyattwhiteeagle on 2021-08-23
> **The Cog said:**
> This is all just basic stuff that a beginner has to get through. Don't worry, once you know what's going wrong it will all quickly make sense.
Two things I was told very early on when I started:
1- Linux generally says nothing if there's no problem. There's no "Yes I did that OK" message. 
2 - Linux is case sensitive - this catches windows users out a lot. hello_world.sh and Hello_world.sh are different files, and both could exist next to each other.
So the face that this command didn't complain means it was successful, and execute permission has now been applied to that script file.
```
wyatt@wyatt-Aspire-E1-532:~$ chmod a+x /home/wyatt/hello_world.sh
wyatt@wyatt-Aspire-E1-532:~$
```
You should now be able to run the script with this command:
```
wyatt@wyatt-Aspire-E1-532:~$ **/home/wyatt/hello_world.sh**
```

And we have success

Thank you so much for that info, it's enlightening :)


So...a recap...is this pretty much how it goes?

> "Hello World" Basic Scripting

The Rules

In a text editor
```
1. #!/bin/bash must be the very first thing done in a text editor.
2. Must skip a line before typing a command
3. Command line must start with a command such as the word echo
```

In the terminal
```
1. chmod is a terminal command as though it's like someone's name inside the terminal
2. a+x is asking that person to do something specific
3. 700 (same as a+x and asks the same thing done)
4. a+x must be followed by the file location and filename ( /home/wyatt/file.sh )
5. The person, request, path, and filename must be on the same line
```

Instructions
The Script

In a prefered text editor. (Your choice. Doesn't matter which one...gedit; LibreOffice Writer)
```
1. Immediately type #!/bin/bash
2. Press enter twice
3. Type whatever command needed. (In this case, the command echo)
4. Hit the spacebar once
5. Type "Hello World" (be sure to include the quotation marks)
6. Click to save the file
7. Name the file including the extension as part of the filename, like this .sh (note the entire filename...in this case...file.sh)
8. Choose whare you want to save the file (note the location)
9. Save the file

```

Now in terminal
Activating The Script

```
1. type chmod a+x /home/wyatt/file.sh (where the file is saved and the entire filename)
2. Hit enter
3. Type /home/wyatt/file.sh (the path and filename)
4. Hit enter

```

The Terminal should say Hello World

---

### Post by TheFu on 2021-08-23
Another important thing is that file extensions don't matter to Linux/Unix.  Those are for humans and we often lie.  A few GUI programs may filter a file selection list by extensions, but that would be it.  .sh isn't needed and it is just as common so see shell scripts without any extension.

[https://tldp.org/LDP/abs/html/index.html](https://tldp.org/LDP/abs/html/index.html) is a good resource for bash. It starts with extremely beginning-level knowledge. Google "ABSG bash" to find it easily.  

Bash is just one shell.  sh, dash, and almost any scripted language can also be used. Some examples are python, perl, awk, ruby, go, r, .... there must be 150 options.  

> 1. #!/bin/bash must be the very first thing done in a text editor.
Not exactly.  The program to interpret the following commands (or a way to find the correct interpreter) needs to be on this line after a "#!" Some example:
```
#!/bin/bash
#!/usr/bin/perl
#!/usr/bin/env python3
```
Only one of those lines would be in any script file.

> 2. Must skip a line before typing a command
Nope.  But whitespace is nice.  Any script commands cannot be on the same line as 1. above, but there doesn't need to be an extra empty line. That is a programming style question.  For example:

```
#!/bin/bash

LOG=/tmp/sys-info-$$
```
or
```
#!/bin/bash
LOG=/tmp/sys-info-$$
```
are both valid.

> 3. Command line must start with a command such as the word echo
Leading whitespace on a line is fine.
```
#!/bin/bash
     LOG=/tmp/sys-info-$$
```
or
```
#!/bin/bash
LOG=/tmp/sys-info-$$
```
are fine.  bash, is not indentation sensitive.  Indentation is a programming style question, except for python, where indentation must be correct.

Comment lines have the first non-whitespace character as a '#', so 
```
# this is a comment
      # this is also a comment
date    # this is a comment on the same line as a command.
```
All valid.

It is true that any editor can be used, but the the file output must be text and it must have non-Windows end-of-line characters.  Don't use Notepad on Windows, then transfer the file over to Linux, chmod +x it and expect that to work.  Windows puts CR+LF at the end of every text line.  OSX and all Unix-like OSes just have a LF (or is that the CR?).  Also, using a word processor will probably save the file in a non-ASCII format by default, so these really shouldn't be used.  An editor is a very personal choice and anyone who has programmed more than a few months will have strong opinions about the best editor.  Obviously, there is only one editor.  Editor wars are a long-time holy war on Unix systems.  So, it is probably best to just set your EDITOR environment variable in a startup config file ~/.bashrc and never worry about it again.

I'm not thrilled with "Activating The Script" as a description.  "Make the script executable" is technically correct.  There are ways to run a script without changing the permissions, provide the userid can read it.  All scripts must be readable by any userid that wants to run them. They don't necessarily have to have execute permissions, but that does make it easier to run them.  I posted about this in another thread today that I think you were in.

---

### Post by wyattwhiteeagle on 2021-08-25
> **TheFu said:**
> Another important thing is that file extensions don't matter to Linux/Unix. Those are for humans and we often lie. A few GUI programs may filter a file selection list by extensions, but that would be it. .sh isn't needed and it is just as common so see shell scripts without any extension.


[https://tldp.org/LDP/abs/html/index.html](https://tldp.org/LDP/abs/html/index.html) is a good resource for bash. It starts with extremely beginning-level knowledge. Google "ABSG bash" to find it easily.


...
...
...


So, it is probably best to just set your EDITOR environment variable in a startup config file ~/.bashrc and never worry about it again.


I'm not thrilled with "Activating The Script" as a description. "Make the script executable" is technically correct...I posted about this in another thread today that I think you were in.


Without ignoring what I edited out of the quote (for easier posting)...


Thank you. I'm certain the info and advice will come in handy :)


Yes, I responded in the thread where the person is or was trying to run through Wine an *.sh file for a game.
I went to the Wine forum to ask something that all other searching left me either more confused about Wine or not really helping me with a the information I was seeking. When I seen the thread, I noticed that the thread starter was trying to run it in Wine.


In my most "untechnical" thinking, sh files don't work in Wine.
I may be wrong about that.


The guidance at the Wiki that my signiature links to seems a little confusing to me.
I needed help in understanding it and to help me correct what I was doing wrong.


When I entered the chmod line into the terminal and got no response...I actually thought I broke something.


Now I laugh because I didn't break anything, I just didn't realize I did it right.


About the "Activating The Script"...I chose that to help me with my thinking. I don't think in technical terms a whole lot.


I'm just an "All-American Southerner" who has a hard time with technical thinking, though it might help me in some scenario's.

---

### Post by TheFu on 2021-08-25
I live near Squidbilly-Land, in southern America too.  Ref: [https://en.wikipedia.org/wiki/Squidbillies](https://en.wikipedia.org/wiki/Squidbillies) Lived in the south most of my life, but not all of it.  Ya'll.

This can help with many things related to Unix: [https://en.wikipedia.org/wiki/Unix_philosophy](https://en.wikipedia.org/wiki/Unix_philosophy)
When a command does what you ask, no output should be expected ... unless the command is supposed to output something.
When a command fails or doesn't understand the request, it should complain loudly.

---

### Post by wyattwhiteeagle on 2021-08-28
> **TheFu said:**
> I live near Squidbilly-Land, in southern America too.  Ref: [https://en.wikipedia.org/wiki/Squidbillies](https://en.wikipedia.org/wiki/Squidbillies) Lived in the south most of my life, but not all of it.  Ya'll.

This can help with many things related to Unix: [https://en.wikipedia.org/wiki/Unix_philosophy](https://en.wikipedia.org/wiki/Unix_philosophy)
When a command does what you ask, no output should be expected ... unless the command is supposed to output something.
When a command fails or doesn't understand the request, it should complain loudly.

Thank you

If I add text next to the Hello World in the script, do I need to run the chmod command to refresh the executable file?

Like...instead of echoing "Hello World", have the terminal echo "Hello, World. How ya'll doin?" Does it need to be "refreshed" as an executable file?

---

### Post by TheFu on 2021-08-28
Permissions are tied to the file metadata. They shouldn't change unless someone/some process goes out of the way to change it. Further, if you copy the file with execute permissions, those should be retained if copied to any POSIX compliant file system.

Rather than asking this question, why not try it and check the permissions?  **ls -al** is how to see the permissions for all files in the current directory. The permissions will be displayed in that output along with the owner and group for the file.  For now, that's probably enough.  When you are ready, there are tutorials for permissions.  Any Unix tutorial is fine. Permissions on all Unix-like OSes are the same - so they work the same on BSD, Linux, MacOS, Android, iOS, and most appliances like NAS, video player sticks, etc.  

Of all the popular OSes, only 1 that I know doesn't use Unix-style permissions, though it has other types of permissions by using file extensions and file attributes. Actually, on NTFS, there are permissions that appear to be similar to Unix permissions, but they don't really work the same way.

Also, there are many different terminal programs, so it is a generic term most of the time. A terminal is where we have an interactive "shell" that works using a "CLI" interface.  You'll see terming, cli, shell used interchangeably when we mean "command line program".  There are CLI, TUI, GUI programs.  CLI and TUI run inside a terminal using a text-only interface.  A GUI program uses a Graphical User Interface.

---

### Post by wyattwhiteeagle on 2021-08-28
> **TheFu said:**
> Permissions are tied to the file metadata. They shouldn't change unless someone/some process goes out of the way to change it. Further, if you copy the file with execute permissions, those should be retained if copied to any POSIX compliant file system.

Rather than asking this question, why not try it and check the permissions?  **ls -al** is how to see the permissions for all files in the current directory. The permissions will be displayed in that output along with the owner and group for the file.

In the script, I edited only what the terminal is to echo, saved it and ran it.

And Terminal say's...

> wyatt@wyatt-Aspire-E1-532:~$ /home/wyatt/hello_world.sh
Hello, World. How ya'll doin'?


```
wyatt@wyatt-Aspire-E1-532:~$ ls -al
total 156816
-rwx------  1 wyatt wyatt       51 Aug 28 01:29 hello_world.sh
wyatt@wyatt-Aspire-E1-532:~$ 

```
There were others in the output list.
I edited to keep the focus.
The only things I'm not quite understanding what they are or what they represent...

the "-rwx------" at the beginning of the line.
the "1" before my name.
the "51" before the date

---

### Post by Impavidus on 2021-08-28
> **wyattwhiteeagle said:**
> 
The only things I'm not quite understanding what they are or what they represent...

the "-rwx------" at the beginning of the line.
the "1" before my name.
the "51" before the date

The -rwx------is about type and permissions. The first - means it's a regular file. Symlinks get l, directories d, etc. Then rwx means that the owner has Read, Write and eXecute permission, the ------ means that the group and others have no permissions.

The 1 means that there's 1 hardlink pointing to this file. That is, there's 1 path/filename pointing to this file. Directories have more, but using multiple hardlinks to the same ordinary file can be useful.

The 51 is the filesize: 51 bytes.

The manual page for ls will tell you more:```
man ls
```

---

### Post by monkeybrain20122 on 2021-08-28
Instead of chmod +x you can just right click your script and from properties check "allow to execute". Same thing but perhaps less cryptic for new users, and you can also view permissions and ownership from properties. I know this is not how the purist would do thing, but since you are not running a server and you do have a gui, why not use it? Devs put a lot of time is creating a DE for convenience so that not just command line gurus can use Linux.

---

### Post by wyattwhiteeagle on 2021-08-28
> **monkeybrain20122 said:**
> Instead of chmod +x you can just right click your script and from properties check "allow to execute". Same thing but perhaps less cryptic for new users, and you can also view permissions and ownership from properties. I know this is not how the purist would do thing, but since you are not running a server and you do have a gui, why not use it? Devs put a lot of time is creating a DE for convenience so that not just command line gurus can use Linux.

I fully understand.

I want to learn this, not to become a "command line guru", but to learn how to create a script that cleans, removes, installs what I personally want, Uninstalls what I don't use or need, update, full-upgrade, etc...all in 1 script.

Some might suggest things like Rsync, I've tried it. It wasn't what I was looking for.

I don't want someone to create this script for me, I want to learn how to create it and how to make it do it's work...thus the chmod, etc command lines.

However, I more than likely need help in area's such as editing the script so as to not have the system starting another job before finishing a job, or trying to do it all at once. 

A "dummy" script (actually just a basic text file that isn't an executable file but shows what such a script would look like) to use as an example to go by would be a great help.

If I were to backup my system right now, the backup won't be sufficient because that backup will include the current error's.

To me, a backup and backing up is a correcting measure. I understand it as backing up to a state with less error's and doing better from that point.

---

### Post by TheFu on 2021-08-28
Google "TLCL" for basic Linux knowledge - like permissions. That will take you to a free, no-hassle, PDF book to download. The book is also available from book stores, if you want dead trees.  To learn permissions, it required an active effort by the student.  Reading examples isn't the same. Actually work through the commands. Type them in. Do not copy/paste.  Type everything (*command completion* is fine).  You'll need 2-3 users + 2 groups and at least 3 terminal windows to learn how different userids are impacted by the permissions.  I'd say to create 3 new users (u1, u2, u3) and 2 groups (g1, g2) for these exercises. Don't use your normal user.  Setup a play area under /tmp/ somewhere.  Create some files by each user, assign different groups, and start playing with the permissions.  Which users can access the files? Which cannot?  Working through every possible combination of permissions will teach a great deal.  Start with 000 --- 777 with 001, 002, 003, 100, 200, 500, 755, 711, 644, 640 being very useful to learn.  Don't miss 055 and 705!  Those can be fun!

Google "ABSG bash" for Bash Scripting. It covers every technique that bash supports and the different data types available. Variables, arrays, hashes, arrays of arrays, etc. If I need more than variables and arrays, I switch to a better scripting language. Bash becomes quite cumbersome with non-trivial data types.  Also, if a bash script becomes longer than 1 page, I'll almost always change to a better language.  Bash has math capabilities, but they aren't anywhere nearly as good as other scripting languages.  And writing functions that don't depend on global variables (every professional programmer knows to avoid global variables), isn't really possible.

Learning which external-to-bash commands to use takes time, experience and asking the right question. When asking, begin by saying the end goal, not the tiny issue, since people new to Unix/Linux often will come up with elaborate methods to do stuff in scripts that have already been solved by a tool they don't know exists.

For example, I think fully automating system patching is foolish. I've been burned a few times.  I do use a script, but it has to be manually run and it logs everything. It doesn't automatically answer questions. A human needs to pay attention.  What my update script does is bring consistency to my weekly patching. I don't forget a system. On systems that have extra stuff to be done, those extra commands get run too.

Your system has hundreds of bash scripts on it already.  They make the system run.  Lots of examples.  Github has - I'm guessing - millions of scripts. All there to learn from as you like.  Lots of people before you have written an update script. I bet at least 100 will be on github and easily found. The scripting is 10% of the knowledge. The other 90% is "what" and "why."  My blog articles try to spend less about the "what to type" and more about the "why" stuff.

An example script: [https://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](https://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt) - must click the link to see it. Since I wrote that script, I've learned a few more techniques that would allow selective deletions in a fairly easy way.

What I consider scripting "best practices": [https://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](https://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting)

---

### Post by wyattwhiteeagle on 2021-08-28
> **TheFu said:**
> For a restore, start with a minimal Ubuntu install, then put everything back in reverse order ... data, settings, then install the packages from the manually installed list. 

Thank you for the example script and other info in your post here.

I was just reading your posts at the above quoted thread, what I quoted from that post is pretty much what I believe would be best for me. To start with a minimal install and work in reverse order just as you explained there.

I may be wrong, it may be easier for me to use normal install and remove what I don't need or use.

Honestly, I'm not sure which approach is best for me...Daily, Automatic, Versioned, minimal or normal install, etc.

Am I trying to overload myself with certain knowledge before I'm ready for that knowledge?

There are some concerns though.

With me having only 4gb Ram, 6.1gb swap area, less than 128gb usable space to work with, and smaller usb drive's that are used to store things like windows apps, songs, photo's, jpg, png, scripts, backups, etc...seems like that less than 128gb is gonna get filled up real quick if I don't pay attention to what I install.

I recall something about my FAT or something being less than the standard. For my 128gb, should that be a concern?

How do I remove those things which aren't removed or reset by just uninstalling a pachage or app?

Would this be the proper order of doing things...

> Minimal install
Data
Settings
Ubuntu-restricted-extras (instead of just running the mscorefonts-installer)
(Apps that I use which are removed with minimal install)
PlayOnLinux
Wine (it has been suggested to use POL to install multiple versions and branches of Wine...thus the disk space concern)
Winetricks
Apps requiring POL, Wine, and/or Winetricks
Scripts and Backups

---

### Post by TheFu on 2021-08-28
128G is huge!   Even the bloated Ubuntu desktop would use less than 35G.  If you are slightly careful, it is easy run only use 25GB total - including swap space by using Lubuntu/Xubuntu instead.

You control the bloat.  

I think more than 4.1G of swap is a waste on Linux.  Systems with less RAM, will use the swap as needed. Systems with more RAM will probably use it a little, because it is there, but not really needed.  I've run Ubuntu on systems with 2G, 3G, 4G, 6G, 8G, 16G, and 32G.  For all of those that are "desktops", my swap is 4.1G.  There is a long thread here from June 2020 about swap that is worth a read.

My main desktop has 40G of storage.
My laptop has a 500G SSD, but only about 100G is allocated for use and only about 50G is actually used.

On the network, there is lots and lots of storage. 40TB+, but that isn't copied to each computer. It is accessed like a local disk from any system.

---

### Post by monkeybrain20122 on 2021-08-28
You can install a lot of things and still costs less than 20G. Typically installed programs go to system file system and I have used 20G max 

It of course depends on what you install, I am talking about basic stuffs. Ubuntu 21.04 fresh install was about 9 G after trimming unsued localities, so much for "bloated". Now if you install games that might cost you a few Gs because of the game data, or VM images will cost quite a bit since they are standalone OSes in a way.

What typically takes up space are things in your $HOME, data like documents,  music and video files and pictures etc and yes, in your case probably Windows programs in your wineprefixes (multiple versions of wine don't take up much space, it is what you install with it that does)  

Also, if you use Linux programs packaged as appimages, flatpaks and snaps then they take up more space since they are bundled with their dependencies. 

But then for modern desktops and laptops (by that I mean 7-8 year old machines) specs llike yours are rare. Others might disagree but I think nowadays with plenty of rams and storage the issue of "bloat" is mostly a thing of the past, even cheap second hand machines have enough ram and storage for the most extravagant Linux desktop. Those who still worry about "bloat" are either running very old hardware or out of habit, like people talking about "burning a live CD" in the forum.

I would rather have a bit of "bloat" and run a modern, pleasant looking desktop with all the cool bells and whistles (since I spend a ot of time on  it) than to save a few GBs and put up with a crappy DE that looks and functions like recycled Windows 98 or beaten up Windows XP. Some hardcore people only need a  terminal so any GUI is "bloat" for such people. But I am a desktop user, not a system admin.

---

