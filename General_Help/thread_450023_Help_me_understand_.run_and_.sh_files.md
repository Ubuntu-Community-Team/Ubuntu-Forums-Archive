---
title: "Help me understand .run and .sh files"
date: 2007-05-20
forum: General Help
---

### Post by timzak on 2007-05-20
First, to start off, I am using Feisty and am a newbie of about 1 month.  I know just enough to get myself in trouble!

I've come across a couple of progams I want to install.  One is in.sh format and one in .run.  

The .sh program's installation instructions are to double-click the file to install it, or type "./moneydance_linux_x86.sh" to install.  Neither method works.  If I double-click, I get 

```
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.
```

If I type from the console, I get "Permission Denied".  If I prefix with sudo, I get "Command not found".  Why don't the instructions work and how do I get them to work?  In what situation WOULD the above instructions work?  Some other distro?

The .run program is Enemy Territory.  I finally figured out how to install ET using the following:

```
chmod +x et-linux-2.60.x86.run
sudo "./et-linux-2.60.x86.run"
```

after changing to the desktop directory where the install file is sitting.  The above was figured out by reading various threads here of people seeking help to install ET.  On a side note, why don't installation instructions ever say to use chmod to make something executable.  They seem to omit that important fact.  Do some distros not require chmod or something?  

The above works as long as I install to the default directory.  But if I try to install to my home directory, I get permission errors.  I found a few posts here detailing how to install to the home directory, but none of the methods worked:

```
tim@tim-desktop:~/Desktop$ sudo "./et-linux-2.60.x86.run"
```

```
tim@tim-desktop:~/Desktop$ sudo ./et-linux-2.60.x86.run
```

```
tim@tim-desktop:~/Desktop$ sudo sh et-linux-2.60.x86.run
```

I tried all of these without sudo too.  Every time, the installation starts, but when I change the install directory to my home folder, it gives me a permission error.  When asked for the directory, I type in "/home/tim/enemy-territory" for the game and "home/tim/bin" for the links as detailed in this post:

[http://ubuntuforums.org/showpost.php?p=538732&postcount=1](http://ubuntuforums.org/showpost.php?p=538732&postcount=1)

What's the secret to get this working?

Why are there so many methods?  Why isn't there only one right way?  Does it have to do with different distros using different console commands?  Help me understand.  I love Ubuntu but am really frustrated at the lack of cohesive installation instructions for various programs that you can't install through Synaptic or Add/Remove.

Thanks in advance!
Tim

---

### Post by mbradlcu on 2007-05-21
commentary first,, not having downloaded or copied files executable by default is a very (very) good thing, but I agree that mentioning that a chmod may be needed would be a big help.. in the /etc/login.defs there's a setting called umask,, umask sets the default permissions of copied or user created files,, adjust to suite.. Most distros set this to 022,, so the inverse perms are 755,,, apparently this doesn't apply to downloaded files or it would have been executable...

Check to make sure you don't already have a directory created in your home directory with the name of the intended destination directory for ET.  also do you have a directory in your home dir called "bin"? if not the installer may not be able to create the dir and that may be why it's failing.

I'm not sure why you're having a problem installing ET into your home as I've used that installer for many programs without this issue.

if you'd like to play around with a test,, create a directory in your home eg: Games and chmod the dir to 777 and try to install into it.

---

### Post by qix on 2007-05-21
Is the .sh file executable? Are you in the directory when you try to write the name of it?

The ./ prefix tells linux to look in the current dir for the file. Just so you know.

If you make it executable and doubleclick, or is in the right dir, and it's executable, it should launch.
An .sh file is a bash-script. That is a script that works in the console, doing various tasks depending on the system.

I don't know if you need to run it with sudo prefixed though. Sudo is the same as running is at root user.

---

### Post by jazzgossen on 2007-05-21
Abuot the program with the .sh file:

Since the file is called .sh, I'm guessing that it is a text file with shell script commands. Then, if it's not executable (though it should be for the instructions to work) you should be able to open it in gedit by double-clicking on it, and then gedit should display the contents of the file. If gedit says it can't read the file, then the file is probably corrupt.

Or, maybe the file is indeed a binary file, and not a text file (in that case it would be strange to call it .sh, but entirely possible). In that case, try changing the permissions (chmod +x, or right-click the file and choose properties->permissions...) and try running the file again. 

If you post a link to the file, we could have a look at it, and see what it is.

---

### Post by timzak on 2007-05-21
mbradlcu, qix, and jazzgossen,

Thanks for your replies.  The .sh file is a commercial financial program called Moneydance.  I've since read something on their forum that you must type "chmod 777 file_name" first.  What is the difference between chmod 777 and chmod +?

Thank you, qix, for explaining "./".  It's good to know what things mean, rather than blindly following directions.

Well, once I started to install Moneydance (after chmod 777), I was having graphical errors reading the installation menus, which were Beryl related.  So I disabled Beryl, restarted X, and installed Moneydance no problems.  Then for the heck of it, I tried Enemy Territory again.  Honestly, I don't know exactly how I got it working, but it worked the first try.  Could it have something to do with disabling Beryl?  I'm not exactly sure what I typed in the console, but it couldn't have been any different than I was trying before.  The only difference I can think of was Beryl not being loaded.  Weird, huh?

So how do I know if I have to make a file executable or not?  What are the different chmod commands and what do they mean?

BTW, qix, I was typing sudo in front of those commands thinking I needed to because of the permission errors I was getting when changing the installation path to my home directory.  It was just a guess on my part.  I don't think I typed sudo this last time that I successfully installed it.  I'm sure this will all make more sense as I gain more experience.

Thanks again.

---

### Post by rich.bradshaw on 2007-05-21
chmod +x means make eXecutable.

chmod 777 is the same but harder to remember!

---

### Post by mbradlcu on 2007-05-21
ahh good to hear you got it installed, yea beryl can do some funky things but you gotta love it!
chmod 777 and  chmod ugo=wrx do the same thing, I'm most comfortable with the first method.
As for when a file needs to be made executable I've found using 'sh some_file_to_exec' doesnt' always work, I"m guessing it's an env varilable issue but I just change the file to 770 and not bother figuring out why...
The classic response to your question would be 'man chmod' or 'info chmod' I often find the man pages obtuse unless I'm already pretty failure with the command. most times I'd google it,, eg: "chmod examples" which comes up with [http://catcode.com/teachmod/chmod_cmd2.html](http://catcode.com/teachmod/chmod_cmd2.html).. check out the google link, it should explain everything you need to know.
have fun!

---

### Post by qix on 2007-05-21
chmod 777 and chmod +x is two things for the same (almost). 7 is really 5+2+1 and (i don't remember which) one of the numbers (5,2,1) is the eXecutable bit. It would really help you to read up on linux and file permissions as it's used on every file, and you're getting across it all the time!
Find a Linux guide on the web, and find the part about file permissions. That would help you.

A quick google: [http://www.unix-tutorials.com/go.php?id=767](http://www.unix-tutorials.com/go.php?id=767)
I haven't read it myself, but it seems good. Maybe I should read it!

---

