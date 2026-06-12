---
title: "Help - third post no replies"
date: 2007-05-21
forum: General Help
---

### Post by squared on 2007-05-21
Somehow the term 'ns' is being interpreted as 'host'.  I get the same response from the terminal when I type either one.  Is there another way that Linux binds user defined terms with system defined commands...like alias, only another way?  I used to be very familiar with VMS and DOS both, but not with Linux.  There has to be a script file that is executing on login/startup that associates ns with host, but I have no clue where to look.  I can't get ns-2 to run because it's interpreting the executable name as something else.

---

### Post by mitch.c on 2007-05-21
ns is part of the ['host']("http://packages.ubuntu.com/edgy/net/host") package which is why you are seeing the behavior you describe, but I'm not entirely clear from your post what you are expecting when you type ns-2. Could you please clarify?

-- 
Mitch

---

### Post by squared on 2007-05-21
Mitch, thanks for replying.  I installed ns-2 (network simulation package), and I should be able to type 'ns' according to the wikki on ns-2 installation on UBUNTU.  here is what I see:

chris@chris-laptop:~/ns-allinone-2.31$ ns
Usage:      host [-v] [-a] [-t querytype] [options]  name  [server]
Listing:    host [-v] [-a] [-t querytype] [options]  -l zone  [server]
Hostcount:  host [-v] [options] -H [-D] [-E] [-G] zone
Check soa:  host [-v] [options] -C zone
Addrcheck:  host [-v] [options] -A host
Listing options: [-L level] [-S] [-A] [-p] [-P prefserver] [-N skipzone]
Common options:  [-d] [-f|-F file] [-I chars] [-i|-n] [-q] [-Q] [-T] [-Z]
Other options:   [-c class] [-e] [-m] [-o] [-r] [-R] [-s secs] [-u] [-w]
Special options: [-O srcaddr] [-j minport] [-J maxport]
Extended usage:  [-x [name ...]] [-X server [name ...]]

  ***************************************

  I get the same response when I type 'host' which has me confused.  The executable is called ns, and I'm not sure how to disassociated the term ns with host and get linux to run the executable.

---

### Post by justin whitaker on 2007-05-21
> **squared said:**
> Mitch, thanks for replying.  I installed ns-2 (network simulation package), and I should be able to type 'ns' according to the wikki on ns-2 installation on UBUNTU.  here is what I see:

chris@chris-laptop:~/ns-allinone-2.31$ ns
Usage:      host [-v] [-a] [-t querytype] [options]  name  [server]
Listing:    host [-v] [-a] [-t querytype] [options]  -l zone  [server]
Hostcount:  host [-v] [options] -H [-D] [-E] [-G] zone
Check soa:  host [-v] [options] -C zone
Addrcheck:  host [-v] [options] -A host
Listing options: [-L level] [-S] [-A] [-p] [-P prefserver] [-N skipzone]
Common options:  [-d] [-f|-F file] [-I chars] [-i|-n] [-q] [-Q] [-T] [-Z]
Other options:   [-c class] [-e] [-m] [-o] [-r] [-R] [-s secs] [-u] [-w]
Special options: [-O srcaddr] [-j minport] [-J maxport]
Extended usage:  [-x [name ...]] [-X server [name ...]]

  ***************************************

  I get the same response when I type 'host' which has me confused.  The executable is called ns, and I'm not sure how to disassociated the term ns with host and get linux to run the executable.

That listing there tells you how to use it. Each of those flags (-v, -H, etc.) are parameters that you can use when using ns (host name) (server name). 

Here is more info on ns and ns-2:

[http://www.isi.edu/nsnam/ns/](http://www.isi.edu/nsnam/ns/)

There is also a link to a tutorial there. Might be too basic for you, but maybe a command is missing....networking is not really my forte. ;)

---

### Post by mitch.c on 2007-05-21
> **justin whitaker said:**
>  

Here is more info on ns and ns-2:

[http://www.isi.edu/nsnam/ns/](http://www.isi.edu/nsnam/ns/)

I second this. Take a look at the link above. A quick look at the documentation will tell you how to use the package. The documentation is a bit confusing, but it does look like there *is* an ns command. 
One tidbit of information I caught in the [FAQ]("http://www.isi.edu/nsnam/ns/ns-faq.html") says...
> What do I do after I successfully build ns?
[LIST]
[*]Put the path to your ns executable into your PATH environment
[*]Put the path to your otcl into your LD_LIBRARY_PATH environment
[*]Put the path to your tcl library into your TCL_LIBRARY environment
[/LIST]
Since it appears you have another package installed with a like command name, you may have to symlink the ns command in the ns-2 package something like this (actual ns-2 directory name may be different):
```
$ sudo ln -s /ns-2/bin/ns /usr/bin/ns-2
```
Then the command ns-2 would call the binary /ns-2/bin/ns. I just don't know enough about the package to give you solid advice here.

---

### Post by fanatik on 2007-05-22
> **squared said:**
> Somehow the term 'ns' is being interpreted as 'host'.  I get the same response from the terminal when I type either one.  Is there another way that Linux binds user defined terms with system defined commands...like alias, only another way?  I used to be very familiar with VMS and DOS both, but not with Linux.  There has to be a script file that is executing on login/startup that associates ns with host, but I have no clue where to look.  I can't get ns-2 to run because it's interpreting the executable name as something else.

typing:
```
$ which ns
```

gives:
```
/usr/bin/ns
```

typing:
```
ls -l /usr/bin/ns
```

gives:
```
lrwxrwxrwx 1 root root 4 2006-10-06 19:05 /usr/bin/ns -> host
```

So ns is symbolically linked to the host command.

you can remove it if you want to use the ns name for something else. Or you can alias another command to ns. Aliases are searched before commands in $PATH. Or you just use the real executable name, ie ns-2.

---

### Post by squared on 2007-05-22
> **fanatik said:**
> typing:
```
$ which ns
```

gives:
```
/usr/bin/ns
```

typing:
```
ls -l /usr/bin/ns
```

gives:
```
lrwxrwxrwx 1 root root 4 2006-10-06 19:05 /usr/bin/ns -> host
```

So ns is symbolically linked to the host command.

you can remove it if you want to use the ns name for something else. Or you can alias another command to ns. Aliases are searched before commands in $PATH. Or you just use the real executable name, ie ns-2.



 Thanks for the help.  How do I remove the symbolic link?

---

### Post by DEMM on 2007-05-23
hi, looks like i kind'a fix the problem, i just copy the ns file form the directory of the ns allinone to the usr/bin directoy...now when i type ns, it apperars the %...but now this also happens when i type host ...LOL

command i used:
** sudo cp /home/demm/ns-allinone-2.31/bin/ns /usr/bin/ns**

---

### Post by fanatik on 2007-05-23
> **squared said:**
> Thanks for the help.  How do I remove the symbolic link?

```
sudo rm /usr/bin/ns
```

---

