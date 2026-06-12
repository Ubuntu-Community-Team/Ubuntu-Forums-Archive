---
title: "ssh-piped symbolic links?"
date: 2012-12-06
forum: General Help
---

### Post by rybu on 2012-12-06
I have a collection of different computers that I would like to use as if they're all one computer, at least from the bash shell. 

What I would like to do is have something like a symbolic link on my laptop, so that if I ever requested access to that symbolic link, all access to that directory would be piped through an ssh tunnel to the remote computer.  

Ideally, I'd like to be able to do things like this, on my laptop:

rybu@rybu-laptop: cd 
rybu@rybu-laptop: cd office-comp
rybu@rybu-laptop: gcc blah.cpp
rybu@rybu-laptop: cp blah.cpp ..

The first command would move me to /home/rybu on my laptop. 

The 2nd command would trigger an ssh connection to my office computer, and set up a symbolic link so that the office-comp directory points to a specified directory on my office computer. 

The 3rd command would be executed on the office computer, not on the home computer.  

The 4th command would in effect be an scp command that would send a file from my office computer to my laptop. 

Is this easy to do?    I imagine this is the kind of thing people who administer many computers must do sometimes.

---

### Post by LewisTM on 2012-12-06
You can do everything except command #3 with [SSHFS]("https://help.ubuntu.com/community/SSHFS") i.e. mount a remote directory as a local one through ssh.

I don't think you can transparently switch to a remote shell by using cd. You will have to login separately, which is as simple as opening a new tab in the terminal and entering your ssh command.

Cheers!

---

### Post by rybu on 2012-12-06
If that's the best that can be done, so be it, I can work with that.  I imagined the smartypants Bash coders would have come up with something slicker than this by now.  Thanks.

---

### Post by The Cog on 2012-12-06
For number 3, I think:
```
ssh rybu@office-comp gcc blah.cpp
```
might do the trick.

---

