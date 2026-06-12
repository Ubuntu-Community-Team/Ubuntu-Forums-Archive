---
title: "Execution of .bashrc"
date: 2006-10-18
forum: General Help
---

### Post by Jonathan Métillon on 2006-10-18
Hi,

I use a .bashrc file in my home directory to tune my bash and define some aliases.

Also, as I use multiple Debian/Ubuntu machines, I wanted to centralize my profile. So I created a svn repositories where all my personnal config files are stored.

Then I remove my original home directory and check out in place a new one from repository.

Now I log in and my .bashrc seems not to be executed anymore. My prompt is not displayed like I specified and my aliases are not avaiable. But if I manually execute it, it works:

```
exec bash -$-
```

The file permissions look like that:

```
-rw-r--r--  1 john john 2.2K Oct 18 12:05 .bashrc
```

So why is .bashrc not executed anymore when I log in?

Thank you for your time.

Jonathan

---

### Post by taurus on 2006-10-18
```
source ~/.bashrc
```

---

### Post by anthro398 on 2006-10-18
This isn't really an answer to your question, but it is related.  I uncomment the .bashrc section telling bash to load aliases from the .bash_aliases file.

```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```

And, then I keep all my aliases in the .bash_aliases file and copy that file to new machines.  It looks like so: 

```
alias msie=~/.cxoffice/win98/desktopdata/cxmenu/Desktop/Internet+Explorer
alias msword=~/.cxoffice/win2000-office/desktopdata/cxmenu/StartMenu/Programs/Microsoft+Office/Microsoft+Office+Word+2003
alias msaccess='"/opt/cxoffice/bin/wine" --check --bottle dotwine --cx-app "C:////Program Files////Microsoft Office////Office10////MSACCESS.EXE"'
alias msexcel=~/.cxoffice/win2000-office/desktopdata/cxmenu/StartMenu/Programs/Microsoft+Office/Microsoft+Office+Excel+2003
alias msppt=~/.cxoffice/win2000-office/desktopdata/cxmenu/StartMenu/Programs/Microsoft+Office/Microsoft+Office+PowerPoint+2003
alias mstools=~/.cxoffice/win2000-office/desktopdata/cxmenu/StartMenu/Programs/Microsoft+Office/Microsoft+Office+Tools
alias msplay=~/.cxoffice/win98/desktopdata/cxmenu/Desktop/Windows+Media+Player
alias ocal='~/.apps/OracleCalendar/bin/ocal'
alias quicktime=~/.cxoffice/win98/desktopdata/cxmenu/StartMenu/Programs/QuickTime/QuickTime+Player
alias itunes=~/.cxoffice/win2000/desktopdata/cxmenu/StartMenu/Programs/iTunes/iTunes
alias oxygen=~/.apps/oxygen2/oxygen.sh
alias bottlesetup=~/.cxoffice/bin/bottlesetup
alias cxinstallwizard=~/.cxoffice/bin/cxinstallwizard
alias limewire=/opt/Limewire/runLime.sh
alias wink=~/.apps/wink/wink
#alias winfox=wine "C:\Program Files\Mozilla Firefox\firefox.exe"


```

---

### Post by Jonathan Métillon on 2006-10-18
> **anthro398 said:**
> This isn't really an answer to your question

Thank you anthro398. Indeed this is not really an answer to my question :-) Your technique is interesting, but the point of using a svn repository is to avoid this kind of "file copies". I have not only a .bashrc file, but a lot of config files. So I can check out all of them in one time, and keep them up to date easily accross multiple machines.

> **taurus said:**
> ```
source ~/.bashrc
```

Thanks taurus, that looks like an easier way to manually execute .bashrc than my *exec bash -$-*. But still I need to issue a command when I log in. I don't want that. I want .bashrc to be executed automatically when I log in, as it should. Any clue?

---

### Post by taurus on 2006-10-18
Okay, here is what I have in my ~/.bash_profile.  Make sure you have it so that it will execute your ~/.bashrc each time you log in or everytime you open a terminal...

```

# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

```

---

### Post by Jonathan Métillon on 2006-10-18
taurus,

I Just added these lines at the top of my .bashrc file. Not better.

If my .bashrc is not loaded, what it the point to add a command in it to load itself?

---

### Post by taurus on 2006-10-18
You are not supposed to add those lines to your ~/.bashrc!  You suppose to create a file called ~/.bash_profile and add those lines in there...  See what the first line in my code says!

```

# ~/.bash_profile: executed by bash(1) for login shells.

```

---

### Post by Jonathan Métillon on 2006-10-18
Oh ok taurus!

That's why I ****** up my system :-)

After I added this to my .bashrc, I created a .bash_profile file and added *source .bashrc *in it.

So the .bashrc is now properly loaded but it is loading itself: infinite loop!

How can I log in the system without .bash_profile being loaded?

---

### Post by taurus on 2006-10-18
Okay, I am going to repeat it one more time.  Please DO NOT add those lines that I included from above in your ~/.bashrc.  Instead, add them to ~/.bash_profile.  From a terminal, type

```
nano ~/.bash_profile
```
Now, cut 'n paste these lines below to your ~/.bash_profile...

```

# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

```
Save it.  Then log out and back in again...

---

### Post by Jonathan Métillon on 2006-10-18
Yes I understood that taurus :D

But it was too late. I've already done this and now the système goes out of memory when I log in, and kicks me out.

---

### Post by taurus on 2006-10-18
If you just follow what I told you at the beginning, this wouldn't happen.  Now, you need to boot your Ubuntu into a recovery mode from GRUB.  Now, you are in as root so I assume your user account is called john!  You need to edit /home/john/.bashrc and remove those lines that should go in /home/john/.bash_profile.  Then, add those lines to /home/john/.bash_profile.  Reboot and see if you can log into john again...

```

nano /home/john/.bashrc
nano /home/john/.bash_profile

```
p.s.  Just forget about the "source ~/.bashrc" thing for now, okay!!!  The only time you run "source ~/.bashrc" from the prompt is when you edit your ~/.bashrc and you want it to read in the new changes...  However, log out and back in would do the same job.

---

### Post by Jonathan Métillon on 2006-10-18
Yes taurus thank you. This is the point, I read .bashrc in your first message where I should have read .bash_profile. All these bash things, it confused me. ](*,)

I can't reboot and and use safe mode, this is a remote server. I can't access it physically.

---

### Post by Jonathan Métillon on 2006-10-19
That's ok, I've been able to use *su -c *using a basic user account to move the broken file:

```
$ su -c 'mv /home/john/.bashrc /home/john/.bashrc.bak'
```And now I can log in. Thank you for your help! :-D

---

