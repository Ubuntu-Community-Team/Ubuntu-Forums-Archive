---
title: "Cannot log in to GNOME - libresmgr/csound/xsession problem?"
date: 2007-02-23
forum: General Help
---

### Post by euchrid on 2007-02-23
I really hope someone can help me with this - it's killing me!

I've got my system set up to log in automatically. When I try to start up my system, I get an error message stating that my session lasted 10 seconds. When I look at the detailed information, I get the following output, preceded by a bunch of stuff that seems to just be my login details:
```
stdin: is not a tty
/etc/X11/Xsession.d/40guidance-displayconfig_restore: line 11: /usr/bin/displayconfig-restore: No such file or directory
/usr/bin/gnome-session: error while loading shared libraries: libresmgr.so.0.9.8: cannot open shared object file: No such file or directory
```

Hmm. I then have to try log in - which inevitably fails. I can, luckily, open things like Firefox and Synaptic through the terminal, and I have searched all day looking for an answer. There are several posts relating to similar problems, but the advice has so far failed.

Before this disaster occurred, I was trying to set up csound5. It's not in the repository, so I was installing it from a .deb file and a couple of .tar files (instead of Synaptic - I know, naughty, naughty). It looked simple enough. It even had an installer. However, it installed several kinds of 'lib' file, and I cannot find out where it put them. Some of them were named the same as ones I already had on my system. I have spent several hours re-installing every kind of 'lib' file, but the error remains.

On top of that, so far, I have tried:
- To locate and install libresmgr.so.0.9.8 or any similar variant. I got nothing, except that the file only seems to exist in rpm packages, which I have not used or opened.
- Re-installing ubuntu-desktop and all gnome and gnomelib and libgnome packages.
- Deleting the .ICEauthority file, as well as chmodding it to 600 and doing 'chown'.
- Deleting gnome-session and 40guidance-displayconfig_restore. Made a mess and didn't help.
- Installing anything with 'resmgr' in it and anything that looked like 'libresmgr', and when that didn't work, uninstalling it.
- Looking for, as per a similar post, a file called 'ia32-libs-sdl' - but I couldn't find anything.

I am pretty positive that it was the installation of csound that caused the problem, but I did also try to remove Update Manager and the Nautilus CD/DVD burner before that. (I know I sound like a right muppet, but there was a reason at the time). The problem was not noticed until I turned my system on again this morning.

I have put everything back to how it was before I started tinkering around last night (i.e Update Manager and Nautilus Burner are back); the only thing different is that everything that looks relevant has been re-installed. The error has not changed one jot. (By the way, I have also now successfully installed XFCE/Xubuntu, so that I can see what I'm doing on the system, as my terminal skills are not so great).

I'm sure there is a simple answer, and I think I need to find out why the gnome-session is looking for libresmgr.so.0.9.8 - but I have no idea of how I would get that information or what I could then do with it.

It's probably obvious to most people that I have absolutely no idea of what I'm doing - but this is how we learn (I hope). One day I will be clever and answer other people's problems, but for now - HELP! - and thank you.

---

### Post by Stemp on 2007-02-23
Do you have a libresmgr.so.1.0 in the /lib directory ? 
Maybe you could try to create a link between this lib and the 0.9.8 wanted by gnome ? 

```
sudo ln /lib/libresmgr.so.1.0 /lib/libresmgr.so.0.9.8
```

It will not solve your problem but may help you to get in the session ;)

---

### Post by euchrid on 2007-02-23
You, sir, are a genius and a gentleman. 

Unless you are female, in which case, you are a lifesaver and a lady. (or something).

In any case, thank you!

What did that actually do? I have seen symbolic links mentioned a lot, but never really understood what they are or how they work.

Also, what else do I need to do to sort this out on an even deeper level? I take it this was a temporary fix?

Thanks once again.

---

### Post by Stemp on 2007-02-23
> What did that actually do? I have seen symbolic links mentioned a lot, but never really understood what they are or how they work.

It's just a filename linked to the real file.

> Also, what else do I need to do to sort this out on an even deeper level? I take it this was a temporary fix?

I really don't know. You'll have to wait for a true genius ;)

---

### Post by euchrid on 2007-02-23
For some reason, I assumed symbolic links were a lot more complicated. Thanks for clearing that up.

I'm interested to see if anyone else had similar troubles with csound5 (is it only me that tried to make it work on Ubuntu?).

I'll check back here after work this time tomorrow - so don't be offended if I don't get back straight away!

Thanks.

---

### Post by euchrid on 2007-03-01
I ended up sorting this out by going back and deleting all the files and libraries that csound had installed. Now there are no problems. 

Has anyone else got this issue or similar with csound5?

---

### Post by jwmislan on 2007-12-18
**Yes** I had the same problem with the new csound packages.

  I wanted to install csound, I got 5.06 to install then I noticed that qjackctl wouldn't start anymore.
In a terminal,  qjackctl - gave the error ' error while loading shared libraries: libresmgr.so.0.9.8: cannot open shared object file: No such file or directory' .
After Googling on libresmgr.so.0.9.8, I found this post.

I suspected the csound install all along, but wanted more info .

Those files in,
 /usr/local/lib
/usr/local/bin
were basically, making qjackctl think that it needed libresmgr.so.0.9.8 .
Deleting them all, is what fixed it for me.

csound is not offered in gutsy amd64 because it is too unstable,
see - 'view the change log'  at - [http://packages.ubuntu.com/gutsy/sound/csound](http://packages.ubuntu.com/gutsy/sound/csound)
   -   for more info.
and see 'other versions of csound' (same page) if you want the feisty amd64 version.
It installs, and works fine on gutsy amd64. 

Anyway I ended up installing the feisty amd64 version
just to play around with a few ideas - build/configure a virtual-midi keyboard, and some other ideas.
 
Cheers
JWM

---

