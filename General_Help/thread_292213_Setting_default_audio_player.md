---
title: "Setting default audio player"
date: 2006-11-03
forum: General Help
---

### Post by Old Pink on 2006-11-03
Hi there,

When opening any audio file, amaroK loads and plays the file, perfect. When opening amaroK, I have a huge list of all my songs. amaroK is default for everything possible... amaroK is perfect. 

And yet, when I press the audio player button on my keyboard (set in keyboard shortcuts to take me to "Launch music player") it launches Rhythmbox.

Not a huge deal, but it'd be nice if this button took me to amaroK, how do I change the default music player to amarok? 

- Matt :D

---

### Post by Old Pink on 2006-11-03
... Bump. :(

---

### Post by knowbody on 2006-11-03
Right click an audio file, goto Properties > Open With, pick Amarok, click Close.  Now all of that file type should open w/ Amarok.

---

### Post by Old Pink on 2006-11-04
> **knowbody said:**
> Right click an audio file, goto Properties > Open With, pick Amarok, click Close.  Now all of that file type should open w/ Amarok.

> **Old Pink said:**
> Hi there,

When opening any audio file, amaroK loads and plays the file, perfect. When opening amaroK, I have a huge list of all my songs. amaroK is default for everything possible... amaroK is perfect. 

Read the original post **before** replying. [-(

It's just the keyboard button I have a problem with, it's default for everything else. :rolleyes:

---

### Post by eppoh on 2006-11-11
> **knowbody said:**
> Right click an audio file, goto Properties > Open With, pick Amarok, click Close.  Now all of that file type should open w/ Amarok.


I would like to use Amarok as the default player, but it doesn't default. I have to right click on a file and open with...amarok every time. Rythym box always tries to run it if i just click on it.

How can I get amarok to run all mp3's by default?

---

### Post by eXume on 2006-11-15
Yeh i would like to know as well.
When i click my 'media' key which is assigned to "Launch Music Player" (using Keyboard shortcuts) it tries to load RhythmBox.
I removed RhythmBox thinking this would fix the problem but it still tries to load it.
It would be great if someone could tell me how to set the "Launch Music Player" default to launch Amarok instead.

---

### Post by MorayJ on 2006-11-22
Hi,

The answer to this problem is here:

[https://launchpad.net/distros/ubuntu/+source/control-center/+bug/4265](https://launchpad.net/distros/ubuntu/+source/control-center/+bug/4265)

Apparently it is hardcoded and workarounds are required until the problem is fixed.

The one I have used is to add a symlink to my preferred audio player (amarok :)) in a directory that is in the path before rhythmbox

eg

This is the first part of my path which can be seen by typing **echo $PATH**:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin

My Rhytmbox command is in /usr/bin

This means that I can add my symlink  in any of the directories that precede it in the path (**/usr/local/sbin:/usr/local/bin:/usr/sbin**:/usr/bin). So I changed directory to /usr/local/bin, where I wanted it, and ran  

**sudo ln -s /usr/bin/amarok rhythmbox**

You can obviously put in whatever player you have in /usr/bin. My media key now works seamlessly, though the skip tracks etc are not. Let me know if someone gets that one sorted. This will presumably be fixed properly some time.

Cheers to you all
Moray

---

### Post by Troels on 2006-11-23
Thanks for the tip :-)

I have no problems with the other media buttons. I set them up in the global keyboard shortcuts in Amarok and it works great. (Except volume up and down - but they go to the central volume control so it is not that big a problem)

Cheers,
Troels

---

### Post by MorayJ on 2006-11-30
> **Troels said:**
> Thanks for the tip :-)

 I set them up in the global keyboard shortcuts in Amarok and it works great. 



D'oh. Oh yes, thanks for that! All set up here now

Cheers

---

### Post by nawzyah on 2007-01-11
Excellent work around, MorayJ!  Thanks for sharing it.

---

### Post by NoMo on 2007-01-25
hi, im completely new to linux ,i and i want to do exactly what is described in this thread,..amarok as default with keyboard links..

but i dont know what file to move..
can anyone discribe step by step what i have to do,,, 

thx !
have a nice day ...

---

### Post by rajan on 2007-02-11
> **MorayJ said:**
> 
My Rhytmbox command is in /usr/bin

This means that I can add my symlink  in any of the directories that precede it in the path (**/usr/local/sbin:/usr/local/bin:/usr/sbin**:/usr/bin). So I changed directory to /usr/local/bin, where I wanted it, and ran  

**sudo ln -s /usr/bin/amarok rhythmbox**

Cheers to you all
Moray

As Moray says, you need to create a symbolic link. first open a terminal and type 

```
which rhythmbox
```

read the output from the terminal (which should be "/usr/bin/rhythmbox")

the "which" command helps you figure out where a command is actually located. type "which" in front of any program that you are interested in knowing where in your filesystem it resides.... for example, here is the output from "which evolution":

```
rajan@paravati:~$ which evolution
/usr/bin/evolution
rajan@paravati:~$

```

this tells me that evolution (my email program) is located also in /usr/bin

now you need to change the directory that your terminal is at to the one where rhythmbox is located in because that's where you want to put your link.

```
 cd /usr/bin/ 
```

now in your terminal, create the symbolic link by typing

```
sudo ln -s /usr/bin/amarok rhythmbox
```

the "sudo" command gives you the administrator access that you need to be able to create such a link in that directory. the "ln" is the command for creating a link and the "-s" means to create it symbolically (like a desktop shortcut in windoze). now if you type in your terminal 
```
ls -l rhythmbox*
```

you should see a different colored entry with a "->" after it pointing to /usr/bin/amarok

if this doesn't work, it may be because you don't have amarok installed in /usr/bin/ and you can figure out where it is by typing 
```
which amarok
```


good luck

---

### Post by Envirotech on 2007-02-24
> **MorayJ said:**
> Hi,

The answer to this problem is here:

[https://launchpad.net/distros/ubuntu/+source/control-center/+bug/4265](https://launchpad.net/distros/ubuntu/+source/control-center/+bug/4265)

Apparently it is hardcoded and workarounds are required until the problem is fixed.

The one I have used is to add a symlink to my preferred audio player (amarok :)) in a directory that is in the path before rhythmbox

eg

This is the first part of my path which can be seen by typing **echo $PATH**:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin

My Rhytmbox command is in /usr/bin

This means that I can add my symlink  in any of the directories that precede it in the path (**/usr/local/sbin:/usr/local/bin:/usr/sbin**:/usr/bin). So I changed directory to /usr/local/bin, where I wanted it, and ran  

**sudo ln -s /usr/bin/amarok rhythmbox**

You can obviously put in whatever player you have in /usr/bin. My media key now works seamlessly, though the skip tracks etc are not. Let me know if someone gets that one sorted. This will presumably be fixed properly some time.

Cheers to you all
Moray

Thank you very much I trying to do this for some time.  It worked like a charm.:)

---

### Post by demonzrulaz on 2007-07-06
omg thank you so much. this really helped me alot! but for some reason not all my keyboard buttons are not working. i don't have a media keyboard exactly. what i want to do is map the e-mail button to forward to the next song. amarok recognizes the button but its not going to the next song. any suggestions?

---

### Post by rajan on 2007-07-07
the only thing i can think of is to go to system --> preferences --> keyboard shortcuts and then click on something that you never use like "toggle shaded state" or something. then when you click on it, it'll say "new accelerator" and it'll wait for you to type the new accelerator. hit the key that you want to know the identity of and hopefully it'll show up in the space that used to say "new accelerator." this isn't going to solve your problem, but at least you'll know what that key is known to your computer as. 

if you still can't figure out the problem, try combining that key with the windoze key or something like that. i know amarok uses those (i actually had to put mine back in). 

good luck.

---

