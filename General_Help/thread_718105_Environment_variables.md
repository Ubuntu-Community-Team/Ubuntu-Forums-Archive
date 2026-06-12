---
title: "Environment variables"
date: 2008-03-07
forum: General Help
---

### Post by Worp8d on 2008-03-07
Hi,

I'm having a lot of trouble setting environment variables.  I know this question has been asked a million times before but I've been through every doc/post I can find and I can't seem to work out what's going on.

I have just installed TeXLive and it tells me I need to add directories to each of the MANPATH and INFOPATH environment variables.  If I edit /etc/environment to include the lines

MANPATH=$MANPATH:/etc/other_dir
INFOPATH=$INFOPATH:/etc/other_dir

then when I call printenv it indicates that MANPATH has been set to "$MANPATH:/etc/other_dir".  If I add a directory to the PATH variable in the same manner by just setting it at the terminal prompt then it does indeed just add the extra directory to the list of ones already there and printenv doesn't return the $PATH part of the command.  What is going on?  How do I just add the extra directories to the variables?

---

### Post by taurus on 2008-03-07
Would it be better to add these lines to your ~/.bashrc?

```

MANPATH=$MANPATH:/etc/other_dir
INFOPATH=$INFOPATH:/etc/other_dir
export MANPATH INFOPATH

```

---

### Post by x1a4 on 2008-03-07
Also, once you've made changes to your configuration, you have to tell your system about it.  Execute: ```
source ~/.bashrc
``` to do it.

---

### Post by Worp8d on 2008-03-07
The Ubuntu documentation says that adding such lines to ~/.bashrc can result in lower performance due the code being executed many times unnecessarily.  Is there a way get the /etc/environment code to add these paths?  I'll give the ~/.bashrc version a go anyway and see what happens.

Thanks for the help!

---

### Post by Worp8d on 2008-03-07
I think my problem may have been that MANPATH and INFOPATH weren't actually set previously.  I just added the lines MANPATH="/etc/some_directory", and similar for INFOPATH, to /etc/environment and everything seems to work fine, including the man command.  

I'm still getting used to linux but I must say I'm having fun with computers again after years of hating Windows.  :)

---

### Post by lloyd_b on 2008-03-07
It looks like the contents of "/etc/environment" are *not* processed via a shell, hence the "$..." entries are not replaced.

There are a couple of places where you can put these definitions, where they *will* be correctly interpreted.  If you definitely want this to be system wide, then I'd suggest adding them to "/etc/profile".  If, on the other hand, you want them local to a specific user, then try adding them to "~/.bash_profile".

(Unlike ".bashrc", ".bash_profile" is only read once per login).

Lloyd B.

Edit: Looks like you already found your answer...

---

