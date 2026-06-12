---
title: "Xserver fatal error"
date: 2007-10-03
forum: General Help
---

### Post by apkelley on 2007-10-03
I am very new to Ubuntu and I would greatly appreciate anyone's help with this problem.

I have been having trouble installing a package called 'xvidtune' using Synaptic.  It says that the package is broken and I keep trying to install it and it doesn't work.  When I restarted my system the xserver wouldn't start.  Here is the associate error message:

FATAL: Error running install command for nvidia
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module
(EE) NVIDIA(0): ***Aborting***
(EE) Screen(s) found, but none have a usable configuration

I tried reconfiguring the xserver-xorg by typing
sudo dpkg-reconfigure xserver-xorg

and I got the following message

dpkg-query: parse error, in file '/var/lib/dpkg/status' near line 7980 package 'xvidtune'
'Depends' field, syntax error after reference to package libc6
/usr/sbin/dpkg-reconfigure: xerver-xorg is not installed

Does anyone know how to fix this?  I would greatly appreciate any help.  Thanks!

---

### Post by PmDematagoda on 2007-10-03
Seems like Xserver is not installed properly, try uninstalling Xserver using:-

```
sudo aptitude remove xserver-xorg
```

in recovery mode, then re-install Xserver using:- 

"sudo aptitude install xserver-xorg"

then install the Nvidia drivers by downloading the Nvidia driver for Linux here:-

[http://www.nvidia.com/object/unix.htm](http://www.nvidia.com/object/unix.htm)

And install the driver as given by the Nvidia web site.

After installation, configure the Xserver with:-
```

sudo dpkg-reconfigure xserver-xorg
```

Post your results after trying the above.

---

### Post by PmDematagoda on 2007-10-03
Excuse me, but I think I made a mistake telling you to use aptitude to install and remove Xserver. I think that may be wrong, so the commands to remove and re-install Xserver are:-

```
sudo apt-get remove xserver-xorg

```
and

```
sudo apt-get install xserver-xorg
```

Sorry about the mix-up.

---

### Post by apkelley on 2007-10-03
Hello,

Thank you for your quick reply.  Unfortunately, I don't believe that it worked.  Here's what happened.  

I typed:
sudo apt-get remove xserver-xorg

and the response was

Reading package lists...Done
Building dependency tree
Reading state information...Done
You might want to run apt-get -f install to correct these:
xbase-clients: Depends: xvidtune but it is not going to be installed
xorg: Depends: xserver-xorg but it is not going to be installed
xserver-xorg-core: Try 'apt-get - f install' with no packages (or specify a solution).

When I tried to reinstall xserver-xorg it told me that I already had the newest version.  

Do you know why xvidtune is not installing itself correctly?  I tried removing it and reinstalling it, but I keep getting the error that I mentioned earlier regarding a parse error.

Thanks again for your help!

---

### Post by PmDematagoda on 2007-10-04
Ok, then try another command:-
```

sudo apt-get remove xserver-xorg-core

```
And re-install using this:-

```
sudo apt-get install xserver-xorg-core
```

Then follow the normal instructions.

---

### Post by apkelley on 2007-10-04
Thanks again for your help.  Unfortunately it is still not working.  I tried the command:

sudo apt-get remove xserver-xorg-core

It gave me a very long list of things that said basically

****: Depends:***** but it is not going to be installed

where **** was a lot of different stuff.  Then when I tried reinstalling xserver-xorg-core it told me that I already had the latest version.  I don't think that the remove command is working.  

I keep getting the error message that  xvidtune has a parse error after line 7980.  Do you know a way to fix that?  I think that is the source of all my problems (but then again I don't really know anything about ubuntu... so I certainly could be wrong).  

Thank you very much for your help!!!

---

### Post by PmDematagoda on 2007-10-04
Ok, do:-

```
sudo apt-get -f install xserver-xorg
```

From what I can see, Xserver is missing some files, try the command above and reconfigure X.

---

### Post by apkelley on 2007-10-04
That still didn't work.  It gave me another list which mentioned xvidtune and said a similar thing about "depends" and that it wasn't going to be installed.  Then it said that I had the latest version.  

Do you have any other suggestions?

Thank you very much for all of your help!

---

### Post by PmDematagoda on 2007-10-05
Ok, try removing xvidtune using:-

```
apt-get remove xvidtune
```

And then try:-

```
dpkg-reconfigure xserver-xorg
```

After configuring X :-
```

startx
```

---

### Post by Ub1476 on 2007-10-05
If it's broken and such, just a quick guess which has fixed things for me:

```
sudo apt-get autoremove
```

---

### Post by apkelley on 2007-10-07
When I try 
apt-get remove xvidtune

I get the following:

Package xvidtune is not installed so not removed
dpkg-query: parse error, in the file/rev/lib/dpkg/status new line 7980 package 'xvidtune' 'Depends' field, syntax error after reference to package 'libc6'.

 I also tried 

sudo apt-get autoremove

which did not work either.  It just mentioned xvidtune having a problem.  

Any other suggestions?  Thanks for all of the help!

---

