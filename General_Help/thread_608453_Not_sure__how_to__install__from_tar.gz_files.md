---
title: "Not sure  how to  install  from tar.gz files"
date: 2007-11-10
forum: General Help
---

### Post by groping_blindly on 2007-11-10
Hi  all.

This is a pretty general question,  so I'm not sure  which is  the appropriate thread.

Can anyone give  me  (or point me to)  a general  rundown on how tar.gz files work, and  how to install software  from them?

Specifically, I've downloaded Kompozer  in  a tar.gz but I  can find no instructions on what to do with it, where  to extract  it to, what to  do  to install the extracted files.  etc. etc.  I hoped it'd install  itself  when  I  ran  the archive, but  no.

Also, is Kompozer available  via Synaptic  Package Manager?  I ran  a search and came  up empty.   Is it out of date now?   All I want  is a Wysiwyg html editor.  I'm not particularly set on Kompozer, but  it seems to be  a widely  used editor.

No  prizes forguessing I'm new  to all this :)

Thanks,
D.

---

### Post by Maestro23 on 2007-11-10
Kompozer is in the Repositories. Make sure you have Universe & Multiverse enabled in your Software sources.

Installing Software in Ubuntu:
[http://www.psychocats.net/ubuntu/installingsoftware#source](http://www.psychocats.net/ubuntu/installingsoftware#source)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by weblordpepe on 2007-11-10
Hi groping_blindly.

tar.gz files are a real linux/unix thing, and date back to way way back when grandad used the first terminals.

You need to go to the command console, and run:
**tar -xzf foobar.tar.gz**
That'll extract it.

Usually programs come as tar.gz if they are coming as source code. You'll have a folder extracted, so **cd** to that folder, and then look for a README file.
Typically you gotta do things like
**./configure**
**make**
**make install**

But the instructions should be outlined in the file. Basically you need to compile the program using all the libraries on your system, and more often than not, you will be missing files needed to compile the program.

Its a right pain. You're best to stick to the repositories, or RPM/DEB files.

---

### Post by groping_blindly on 2007-11-19
Thanks guys. I'm still working on  this, but with no  luck  yet.   How do I get Kompozer  into the  list  of available applications in the add/remove application thingy?   I know that's where it's meant  to  be, I've seen it on the list on a  mate's system.  But not on mine.  I've installed all the    current updates, I've enable universe  and multiverse sources.  I've done everything I can think of and it's simply not there.  Any ideas people?

I had a go at installing from the tar.gz.   You're right.  It gets messy.

---

### Post by Shazaam on 2007-11-19
Have you looked at this?

[https://help.ubuntu.com/7.10/add-applications/C/index.html](https://help.ubuntu.com/7.10/add-applications/C/index.html)

---

### Post by juan@forum on 2007-11-19
before compiling and installing source packages you will need some tools

sudo apt-get install build-essential

---

### Post by bodhi.zazen on 2007-11-19
Actually it depends on what is in the tar.gz

tar.gz is akin to a "Zip" file and can contain anything from source code to python (or other) scripts to pre-packaged binaries.

Best read the documentation or look at the README file.

---

### Post by XerXeX on 2007-11-20
Hi everyone. I have the same problem. I'm trying to install Celtx, a scriptwriter ([http://www.celtx.com/download.html](http://www.celtx.com/download.html)), but Im stuck. I really need it for a project that is coming up and time is short. I dont want to boot XP and run Final Draft 7. 

When I type in these lines "sudo apt-get install build-essential" it requires me to insert the ubuntu CD (also some other programs requires me to do this) but when I do insert the cd it keeps asking for it although it is inserted and wont install anything. 

How do I move on? Im kind of new to linux so any help would be _really_ appreciated!

---

### Post by mercedcollege on 2007-11-20
> **XerXeX said:**
> Hi everyone. I have the same problem. I'm trying to install Celtx, a scriptwriter ([http://www.celtx.com/download.html](http://www.celtx.com/download.html)), but Im stuck. I really need it for a project that is coming up and time is short. I dont want to boot XP and run Final Draft 7. 

When I type in these lines "sudo apt-get install build-essential" it requires me to insert the ubuntu CD (also some other programs requires me to do this) but when I do insert the cd it keeps asking for it although it is inserted and wont install anything. 

How do I move on? Im kind of new to linux so any help would be _really_ appreciated!

it need to retrieve some files off from the Internet and cd

When it requirds the Cd 

it will say 
insert media /cdrom than press enter

---

### Post by XerXeX on 2007-11-20
> **mercedcollege said:**
> it need to retrieve some files off from the Internet and cd

When it requirds the Cd 

it will say 
insert media /cdrom than press enter

Yes, but like I said, eventhough I insert the CD it keeps asking for it although its mounted and nothing happens.

---

### Post by bodhi.zazen on 2007-11-20
> **XerXeX said:**
> Yes, but like I said, eventhough I insert the CD it keeps asking for it although its mounted and nothing happens.

Edit your sources and remove the CD form the list.

```
gksu gedit /etc/apt/sources.list
```

Put a # at the very front of the line referring to the CD.

Now, in a terminal :

```
sudo apt-get update
```

Then install what you will ....

---

### Post by mercedcollege on 2007-11-20
I am pretty new at this too :)

---

### Post by Screaming Monkey on 2007-11-20
XerXeX:  You shouldn't need a cd or anything for Celtx.  I have it installed and it works just fine.  The thing that helped me is to add a custom launcher to my panel, name it celtx, then, where it says command, locate the folder where you extracted it to and find the file simply called "celtx".  Set the icon to whatever you will.  Save the launcher, then click on the launcher.  Should work without having to build anything.

---

### Post by XerXeX on 2007-11-21
Screaming Monkey, I created a launcher, chose "Program", "Name" Celtx, "Command" /home/xerxex/Downloads/celtx/celtx. A launcher pops up on my desk, I double klick it, nothing happens. :(

I dont know if Im doing anything wrong. Plz advice!

---

### Post by Screaming Monkey on 2007-11-21
I can't tell what it is you're doing wrong.  I did the exact same thing and it works for me.  I do know though that you don't need to double click the icon, one click will do, but it does take a minute for the program to launch.  

What version of Ubuntu you using?

---

### Post by XerXeX on 2007-11-21
Im using 7.10 and Im on a AMD64 X2. Im going to try again now that I know that it takes a minute for it to launch, sounds way too long for such a program but better than nothing!

---

### Post by bodhi.zazen on 2007-11-21
Don't forget to make the script executable

chmod a+x /path_to_script

---

