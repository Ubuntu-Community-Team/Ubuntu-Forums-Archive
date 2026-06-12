---
title: "Graphical sudo"
date: 2013-04-26
forum: General Help
---

### Post by jsvidyad on 2013-04-26
Hello,

   Isn't there supposed to be some other command other than sudo which should be used when launching graphical commands with admin privileges? Which one is that? Please give me the ones for both ubuntu and kubuntu. Why should we use those commands rather than sudo for graphical applications?

---

### Post by haqking on 2013-04-26
> **jsvidyad said:**
> Hello,

   Isn't there supposed to be some other command other than sudo which should be used when launching graphical commands with admin privileges? Which one is that? Please give me the ones for both ubuntu and kubuntu. Why should we use those commands rather than sudo for graphical applications?

gksudo

and kdesudo

[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

---

### Post by slickymaster on 2013-04-26
gksu and gksudo are not installed as part of a default raring install,though they are in the repositories. In 12.04 at least gksudo was just a symbolic link to gksu.
gksu can be installed on 13.04 with and it will work.
```
sudo apt-get install gksu
```
Apparently its use is not recommended any more and it may be removed entirely from future issues of Ubuntu. In the long term **pkexec** is preferred, it allows an authorized user to execute program as another user. If the username is not specified, then the program will be executed as the administrative super user, root.
See the man page man pkexec for more information.

---

### Post by Warren Hill on 2013-04-26
For Ubuntu prior to 13.04 use **gksu** for 13.04 you can install **gksu** or follow the instructions here

[http://askubuntu.com/questions/284306/why-is-gksu-no-longer-installed-by-default-in-raring-13-04/284717#284717](http://askubuntu.com/questions/284306/why-is-gksu-no-longer-installed-by-default-in-raring-13-04/284717#284717)

There may be an issue with 64-bit raring that your password does not work and you have to  run **gksu-properties **once to change the mode from **su** to **sudo**.

However, that was in at least one on the beta releases and may have been fixed in the final release.

---

### Post by 3rdalbum on 2013-04-26
> **jsvidyad said:**
> Why should we use those commands rather than sudo for graphical applications?

For KDE, the command used to be "kdesu" - it might still be.

The reason to use those instead of sudo for graphical applications is all down to the effect on the .Xauthority file. If you use 'sudo' for graphical programs, there's a risk of it modifying the permissions or ownership of the .Xauthority file and causing you to be unable to log in next time (until you fix the permissions).

---

### Post by Warren Hill on 2013-04-27
When you use **sudo** you have elevated privileges but $PATH and $HOME are yours
When you use **gksu** you have elevated privileges and $PATH and $HOME are those of** root**

Normally it does not matter which you use but it can mean config files get written in the wrong place or owned by the wrong person.  This can cause problems.

The advice has always been use **gksu  **or gksudo (,**kdesu** on kde) with graphical programs because it's always OK.  It's easier than trying to explain which programs need gksu and which can use either.

This web page explains it better : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

With raring you can use **gksu** but it's not installed by default, because the developers would rather we used policy-kit to set things up but its not easy to use yet.

To install gksu

```
sudo apt-get gksu
```

then possibly -- once only

```
gksu-properties
```

make sure authentication is set to sudo.  You wont need to run **gksu-properties** again.

This was necessary on 64-bit Ubuntu in the beta2 release but not 32-bit.  Haven't tested the final release yet so it may or may not be neccesary 


The other way is to open a terminal and enter

```
sudo -i
```

Inside that terminal you are root so you can run the programs as root without problem: by typing the name of the program in that terminal.  Do not close the terminal until you are finished however as it will kill the program you want to run.

---

### Post by sudodus on 2013-04-27
> **slickymaster said:**
> gksu and gksudo are not installed as part of a default raring install,though they are in the repositories. In 12.04 at least gksudo was just a symbolic link to gksu.
gksu can be installed on 13.04 with and it will work.
```
sudo apt-get install gksu
```
Apparently its use is not recommended any more and it may be removed entirely from future issues of Ubuntu. In the long term **pkexec** is preferred, it allows an authorized user to execute program as another user. If the username is not specified, then the program will be executed as the administrative super user, root.
See the man page man pkexec for more information.

So **pkexec **will replace gksu(do). Just like that, or are there any implications for a regular user other than a new name?

---

### Post by coffeecat on 2013-04-27
> **Warren Hill said:**
> To install gksu

```
sudo apt-get gksu
```

then possibly -- once only

```
gksu-policy
```

make sure authentication is set to sudo.  You wont need to run **gksu-policy** again.

This was necessary on 64-bit Ubuntu in the beta2 release but not 32-bit.  Haven't tested the final release yet so it may or may not be neccesary 


I think you mean "gksu-properties", not "gksu-policy" to set sudo mode.

I've found something interesting in my 24-hour old shiny new 64-bit Raring installation. I have gksu installed although I didn't deliberately install it myself. [s]I think it was installed as a recommends of synaptic which is always the first thing I install after an apt-get update in a fresh Ubuntu installation. I must admit I wasn't paying much attention to the terminal feedback when installing synaptic - I tend to be on autopilot at this point, shame on me![/s] Whichever - I had to run gksu-properties to change from su mode to sudo mode.

**EDIT - for the record:** Checking on a fresh newer installation - it was hplip-gui that brought in gksu as a dependency.

---

### Post by Warren Hill on 2013-04-27
> **coffeecat said:**
> I think you mean "gksu-properties", not "gksu-policy" to set sudo mode.

I've found something interesting in my 24-hour old shiny new 64-bit Raring installation. I have gksu installed although I didn't deliberately install it myself. I think it was installed as a recommends of synaptic which is always the first thing I install after an apt-get update in a fresh Ubuntu installation. I must admit I wasn't paying much attention to the terminal feedback when installing synaptic - I tend to be on autopilot at this point, shame on me! Whichever - I had to run gksu-properties to change from su mode to sudo mode.

Thanks for the correction.  Yes I did mean **gksu-properties**.

---

### Post by Warren Hill on 2013-04-27
> **sudodus said:**
> So **pkexec **will replace gksu(do). Just like that, or are there any implications for a regular user other than a new name?

**pkexec** is not just a new name For example 

```
gksu nautilus
```

runs the file manager as root while 


```
pkexec nautilus
```

Doesn't work.

**pkexec** is a front end to policy-kit which aims at being a more fine grained tool for controlling rights and privileges than **sudo** and **gksu**.  More needs to be set-up and it's not all in place yet to be an easy tool the casual user.

For now I recommend you either install gksu (setting the Authentication mode to sudo if required) or type ```
sudo -i
``` in a terminal and run GUI applications that you want to run as root from inside that terminal.

---

### Post by sudodus on 2013-04-27
Thanks for the explanation :-)
So I'll stay with sudo and gksu

---

### Post by jsvidyad on 2013-04-29
So, 

  Should I use [gksu and kdesu] or [gksudo and ksesudo] ? I am asking about the graphical versions of sudo for ubuntu and kubuntu.

---

### Post by sudodus on 2013-04-29
It does not matter, because the -do versions are symbolic links to those with shorter name

```
 lrwxrwxrwx 1 root root 4 nov  9  2011 /usr/bin/gksudo -> gksu
```

---

### Post by bogan on 2013-04-29
Hi!. **All,**

I just tried: 'pkexec' with Raring 13.04 v. 3.8.0-19-generic #29 x86_64 and this is what I got```
: :~$ pkexec gedit /etc/modprobe.d/blacklist.conf
No protocol specified

** (gedit:2799): WARNING **: Could not open X display
Cannot open display: 
Run '/usr/bin/gedit --help' to see a full list of available command line options.
:~$ gksudo gedit /etc/modprobe.d/blacklist.conf
:~$ 
```This was with Ubuntu unity running correctly from a second Administration acount.

I did not need to set Authentication mode in gksu-properties, as it was already set to sudo.

'gksudo gedit ran OK, but still with the unwanted: "Utitled Document 1", as well as the correct file.

Is this what **warren hill **meant by: "Doesn't work"?

Chao!,** bogan**.

---

### Post by Warren Hill on 2013-04-30
> **bogan said:**
> Hi!. **All,**

Is this what **warren hill **meant by: "Doesn't work"?

Chao!,** bogan**.

Pretty much.

I'm sure it will get easier but pkexec needs to be configured see the [man page]("http://manpages.ubuntu.com/manpages/raring/en/man1/pkexec.1.html")

**gksu **still works in 13.04 it's just not part of the default install.

Lets hope that by the time Saucy comes someone has made it clear how to do this.

---

### Post by MestreLion on 2013-05-02
> **sudodus said:**
> It does not matter, because the -do versions are symbolic links to those with shorter name

```
 lrwxrwxrwx 1 root root 4 nov  9  2011 /usr/bin/gksudo -> gksu
```

Being a symlink does ***not*** mean it doesn't matter: many software *behave differently depening on what name was used to invocate them*. For example, ```
bash
``` turns on POSIX strict mode when invoked as ```
sh
```

---

### Post by sudodus on 2013-05-02
> **MestreLion said:**
> Being a symlink does ***not*** mean it doesn't matter: many software *behave differently depening on what name was used to invocate them*. For example, ```
bash
``` turns on POSIX strict mode when invoked as ```
sh
```
I think that gksu and gksudo behave in the same way, at least it looks like that for me, for example
```
gksu gparted
``` and ```
gksudo gparted
```
but the manual says they are invoking different modes, su mode and sudo mode.

Your comment is correct is principle, but sh and bash are actually running different binaries, at least in 12.04.2

```
sudodus@ssd-grund ~ $ which sh
/bin/sh
sududus@ssd-grund ~ $ l /bin/sh
lrwxrwxrwx 1 root root 4 mar 29  2012 /bin/sh -> dash
sudodus@ssd-grund ~ $ which bash
/bin/bash
sududus@ssd-grund ~ $ l /bin/bash
-rwxr-xr-x 1 root root 920788 mar 28 18:37 /bin/bash
sudodus@ssd-grund ~ $ which dash
/bin/dash
sudodus@ssd-grund ~ $ l /bin/dash
-rwxr-xr-x 1 root root 100284 mar 29  2012 /bin/dash

```
vim and vi are using the same binary as ex, view, gvim, gview, evim, eview, rvim ...
```
-rwxr-xr-x 1 root root 1903360 maj  4  2012 /usr/bin/vim.basic
```
**[FONT=courier new]man vim[/FONT]**:
```
       Vim behaves differently, depending on the name of the command (the executable may still be  the
       same file).

       vim       The "normal" way, everything is default.

       ex        Start  in  Ex mode.  Go to Normal mode with the ":vi" command.  Can also be done with
                 the "-e" argument.

       view      Start in read-only mode.  You will be protected from writing the files.  Can also  be
                 done with the "-R" argument.

       gvim gview
                 The GUI version.  Starts a new window.  Can also be done with the "-g" argument.

       evim eview
                 The  GUI  version in easy mode.  Starts a new window.  Can also be done with the "-y"
                 argument.

       rvim rview rgvim rgview
                 Like the above, but with restrictions.  It will not be possible to start  shell  com&#8208;
                 mands, or suspend Vim.  Can also be done with the "-Z" argument.

```

---

