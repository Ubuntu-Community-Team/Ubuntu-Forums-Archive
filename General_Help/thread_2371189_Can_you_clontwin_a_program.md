---
title: "Can you clon/twin a program?"
date: 2017-09-12
forum: General Help
---

### Post by zemega on 2017-09-12
Hi. I have a Ubuntu 16.04. I installed Mendeley Desktop and its working fine. After a while I'm working with two separate projects requiring separate documents and references. I find that the free limit is just not enough. What I would like to do is make a clone/twin/double installation of Mendeley Desktop. Kind of like the twin app feature in some of the newer phones, where you can have two Whatsapp, registered to two different numbers, running separately together. So I can have two Mendeley Desktop running side by side under one account. I can easily use one Mendeley account for one user and ssh -X into another account, but I will run into problems of registering documents across accounts. There's also the problem with permissions between users, even if I own both of the accounts.

If someone could help me with the terms that I can google with, that would be great. I'm actually lost on what term to google with.

---

### Post by TheFu on 2017-09-12
So .... what you are asking here is how to violate the free level ToS of Mendeley without paying for the paid version?

Correct?

---

### Post by HermanAB on 2017-09-12
Yes, you can run multiple copies of the same program and there are multiple ways to do it.
:)

---

### Post by zemega on 2017-09-12
> **HermanAB said:**
> Yes, you can run multiple copies of the same program and there are multiple ways to do it.
:smile:
Can you hekp me out? Give me some pointer for me to look for the solution?

> **TheFu said:**
> So .... what you are asking here is how to violate  the free level ToS of Mendeley without paying for the paid version?

Correct?
Nope. There's no problem or violation in having multiple accounts of Mendeley for your use. I just want to run multiple of the Mendeley Desktop program under one Ubuntu 16.04 account.

---

### Post by TheFu on 2017-09-13
Most programs will allow you do run multiple instances.  A few, where the devs specifically thought it was a bad idea, prevent it.  Try running 2 instances of thunderbird, for example.  It won't allow it.  

How does it know that another instance is running?  There are a few ways.
* Check the process table for that specific userid running thunderbird. If another process ID exists, under the same userid, running a program with the same inode location, don't allow it.
* Check for a "lock" file.  It is very common for programs to create a lock file at startup to prevent data file corruption when multiple processes try to modify the same data files.  This can be really bad or not bad at all.  It is better to be lucky than good.

So what does that mean?  It depends.
? Is the lock file based on some other variable?  Is it based off the HOME variable or something else?
? Is making another install directory location enough to allow multiple instances running?  Using dpkg, it is possible to install any package to a user-specified location. This will ensure that the inode is different for the 2 different installs.  Or if they release a tgz installer version of the software, there is almost always a way to tell it where to install that isn't the default location.  You'll have to try it to see.
? If the program checks the process table, things are harder.  Short of using a different userid or a different machine to run the program, then we are out of luck without the source code being modified.

I would start, if I cared, by making a few backups. Corrupt data is very, very, possible. If you have things you can't loose, make 3 backups - 2 need to be off the machine and you should verify that restoring the data is actually a fix.

I would next look at the installer. See where it allows the install directory to be set.  Install it in 2 different locations, if possible.  Sometimes they have a startup script that sets up the environment for each run, just prior to calling the compiled program.  That's how firefox works.

Or there is the easy way.  Just create another userid and run the program in there.
If you want to try harder, you could try running the program in a container. This isn't for beginners.  You can try by running inside a **firejail** environment.

All of these methods take extra effort, but having a script that uses a different HOME isn't really all that hard.  Just make certain the directory exists and has the same permissions, ownership, group, as your normal HOME does.

There you have it. Would be interesting to hear which you try and how they work or don't.

---

### Post by dragonfly41 on 2017-09-13
I am not sure if this idea will work for you.
But you could try syncing mendeley with zotero standalone.

[http://libguides.mit.edu/ld.php?content_id=8960881](http://libguides.mit.edu/ld.php?content_id=8960881)

[http://libanswers.wustl.edu/faq/5331](http://libanswers.wustl.edu/faq/5331)

So you have project1 on mendeley, project2 on zotero, and sync.

With such experiments, backup your data, particularly with syncs.

There is also SpideroakONE for sharing databases, shared between project1 and project2.

---

### Post by zemega on 2017-09-14
The provided installer for Ubuntu is in deb form. So that itself cannot be installed per user. The provided binary for general linux will call upon the installed mendeley desktop itself, not the binary one. 

I tried with su. Gotten error of 
```
mendeleydesktop 

(gconftool-2:20767): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did  not receive a reply. Possible causes include: the remote application  did not send a reply, the message bus security policy blocked the reply,  the reply timeout expired, or the network connection was broken.
Error setting value: No D-BUS daemon running


(gconftool-2:20768): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did  not receive a reply. Possible causes include: the remote application  did not send a reply, the message bus security policy blocked the reply,  the reply timeout expired, or the network connection was broken.
Error setting value: No D-BUS daemon running

No protocol specified
QXcbConnection: Could not connect to display :0
```

It seems to be working fine by using ssh -X. But if I'm removed from network, I cannot use ssh. Unless perhaps if I make a dummy ethernet interface or something. At least I believe I can do something about it. I think I will stick with this solution for now.

---

### Post by TheFu on 2017-09-14
$ dpkg -x app.deb /path/to/target/dir/

Also, trying to run any GUI program as root is asking for trouble. It is almost always a terrible, terrible, terrible, idea.

---

### Post by zemega on 2017-09-15
> **TheFu said:**
> $ dpkg -x app.deb /path/to/target/dir/

Also, trying to run any GUI program as root is asking for trouble. It is almost always a terrible, terrible, terrible, idea.

I tried dpkg -x and running the python script inside bin folder, it redirects to the installed mendeleydesktop. I haven't tried on a fresh Ubuntu install without any mendeley desktop installed yet.
su is switch user right? I tried to switch user inside terminal and run mendeley desktop and it gives me the error from before

```

x1@x:~/Downloads$ su x2
Password: 
x2@x:/home/x1/Downloads$ mendeleydesktop 
 

(gconftool-2:20767): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did  not receive a reply. Possible causes include: the remote application  did not send a reply, the message bus security policy blocked the reply,  the reply timeout expired, or the network connection was broken.
Error setting value: No D-BUS daemon running


(gconftool-2:20768): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did  not receive a reply. Possible causes include: the remote application  did not send a reply, the message bus security policy blocked the reply,  the reply timeout expired, or the network connection was broken.
Error setting value: No D-BUS daemon running

No protocol specified
QXcbConnection: Could not connect to display :0

```

Although I found another solution using su and xhost.
```

x1@x:~/Downloads$ xhost + x2@xxx.xxx.xxx.xxx
x1@x:~/Downloads$ xhost +
x1@x:~/Downloads$ su x2
Password: 
x2@x:/home/x1/Downloads$ mendeleydesktop
libGL error: failed to open drm device: Permission denied
libGL error: failed to load driver: nouveau
QSslSocket: cannot resolve SSLv2_client_method
QSslSocket: cannot resolve SSLv2_server_method
QLayout: Attempting to add QLayout "" to ToolBarActionWidget "", which already has a layout
QLayout: Attempting to add QLayout "" to ToolBarActionWidget "", which already has a layout
Qt WebEngine Plugins directory not found. Trying fallback directory... Plugins as for example video codecs MAY NOT work.
Using old PDFNet version - Recommend 5.2.0 or later

```
It still gives error and warning but it works. All the functions that I need works through su and xhost. And it also works offline.

I would consider this solved, especially if there's no error or warning given, but I'm still open to suggestion

---

### Post by TheFu on 2017-09-15
If you are going to use a different, non-root, userid, then you need to **su - x2**. That will get the environment from the x2 userid.  Without the -, your current userid environment is retained. THAT is likely an issue.

xhost + lets any system with network access to that machine have access to your X/Server.  That is a huge, huge, huge, security hole.  The **xhost + {IP}** method is fine.  This command is providing remote access to the X/Server, but only from the {IP} you list.  1000x better than xhost + which allows any IP access.

You are pretty close, just the little details were missing.  Good job!

---

### Post by zemega on 2017-09-17
> **TheFu said:**
> If you are going to use a different, non-root, userid, then you need to **su - x2**. That will get the environment from the x2 userid.  Without the -, your current userid environment is retained. THAT is likely an issue.

xhost + lets any system with network access to that machine have access to your X/Server.  That is a huge, huge, huge, security hole.  The **xhost + {IP}** method is fine.  This command is providing remote access to the X/Server, but only from the {IP} you list.  1000x better than xhost + which allows any IP access.

You are pretty close, just the little details were missing.  Good job!

I think this is the correct way. Don't use just 'xhost +'. That's a no no. Use 'xhost +SI:localuser:username'. Then use 'su - username'. This way it works offline as well. What else should I know?

```

x1@x:~/Downloads$ xhost +SI:localuser:x2
x1@x:~/Downloads$ su - x2
Password: 
x2@PCNAME:~$ mendeleydesktop
libGL error: failed to open drm device: Permission denied
libGL error: failed to load driver: nouveau
QSslSocket: cannot resolve SSLv2_client_method
QSslSocket: cannot resolve SSLv2_server_method
QLayout: Attempting to add QLayout "" to ToolBarActionWidget "", which already has a layout
QLayout: Attempting to add QLayout "" to ToolBarActionWidget "", which already has a layout
Qt WebEngine Plugins directory not found. Trying fallback directory... Plugins as for example video codecs MAY NOT work.
Using old PDFNet version - Recommend 5.2.0 or later
```

---

### Post by TheFu on 2017-09-18
> **zemega said:**
> I think this is the correct way. Don't use just 'xhost +'. That's a no no. Use 'xhost +SI:localuser:username'. Then use 'su - username'. This way it works offline as well. What else should I know?


Thousands of things, but you probably aren't interested or have the time to learn them all today, now, immediately. 

I've never used xhost +{IP} with a username.  That must be new. I haven't used xhost+ in about 15 yrs, so any new options are beyond my personal experience.  
An example:
```
$ xhost +172.22.31.7

```
The IP would be for the X/Windows client machine ... over the network.  If you are running it on the same machine, the 
```
$ xhost +localhost

``` should work fine.

---

### Post by zemega on 2017-09-20
> **TheFu said:**
> Thousands of things, but you probably aren't interested or have the time to learn them all today, now, immediately.

I have to learn them when X11 is out of the way in the future. I don't know whether xhost will still be used in Wayland or not. At that time, probably there will protocol based Wayland instead of X11.

---

### Post by TheFu on 2017-09-20
> **zemega said:**
> I have to learn them when X11 is out of the way in the future. I don't know whether xhost will still be used in Wayland or not. At that time, probably there will protocol based Wayland instead of X11.

X11 took 40 yrs to get to the level of sophistication is has.  I have doubts that any replacement will deal with those details in less than 10 yrs.

But mostly what you need to know has NOTHING to do with X/Windows.

---

