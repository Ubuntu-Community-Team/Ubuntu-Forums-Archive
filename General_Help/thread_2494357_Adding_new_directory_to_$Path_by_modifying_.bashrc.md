---
title: "Adding new directory to $Path by modifying .bashrc -1st time-"
date: 2024-01-13
forum: General Help
---

### Post by ozark_hillbilly on 2024-01-13
After installing "glances" app I decided to add the additional packages associated with it.

terminal command: pip3 install --user glances[all]

Installing collected packages: scandir, pySMART.smartx, pymdstat, py-cpuinfo, pbkdf2, nvidia-ml-py3, ifaddr, zipp, wifi, sparklines, bernhard, async-timeout, zeroconf, importlib-metadata, pygal
  WARNING: The script cpuinfo is installed in '/home/ed/.local/bin' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
  WARNING: The script sparklines is installed in '/home/ed/.local/bin' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
Successfully installed async-timeout-4.0.3 bernhard-0.2.6 ifaddr-0.2.0 importlib-metadata-7.0.1 nvidia-ml-py3-7.352.0 pbkdf2-1.3 py-cpuinfo-9.0.0 pySMART.smartx-0.3.10 pygal-3.0.4 pymdstat-0.4.3 scandir-1.10.0 sparklines-0.4.2 wifi-0.3.8 zeroconf-0.131.0 zipp-3.17.0

[notice] A new release of pip available: 22.3 -> 23.3.2
[notice] To update, run: python3 -m pip install --upgrade pip
ed@ed-G41MT-S2PT:~$ 

********************************************************************
 This is the path I wanted to include in the .bashrc file per the above recommendation:
  
  export PATH="/home/ed/.local/bin:$PATH"
 
What is perplexing is when I look at the file with text editor by right clicking on the file under Folders this is shown:
it does not show me the very end of the file with lines showing characters "fi" and "fi" twice.
Reference screenshot: .bashrc with text editor through Folders 

Using nano (which I am unfamiliar with) under terminal mode those last characters are displayed. 
Reference screenshot: .bashrc with nano through terminal mode

Using nautilus through termial mode renders the same result as using text editor through Folders.

So I attempted to modify the file and verifying the change with "echo $Path" showed no change in the path assignment:

ed@ed-G41MT-S2PT:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
ed@ed-G41MT-S2PT:~$ 

There is no "home/ed/.local/bin" at the end.

What is the correct way to edit the .bashrc file?
This is one in a row so be kind to this old fart....lol
P.S.
I am understanding that it is the .bashrc file I need to modify (not GLOBAL) since I am the only user of this Linux PC.
Ubuntu 20.04

---

### Post by Holger_Gehrke on 2024-01-14
The file ~/.bashrc is read by the shell **when it starts up**. So the changes you made will not show up in a shell which is already running when you make those changes. You could of course manually reread the changed .bashrc by using the builtin 'source'-command ('source ~/.bashrc'). Or you could just close the terminal and start a new one.

Holger

---

### Post by MAFoElffen on 2024-01-14
But if you did this
```

mafoelffen@Mikes-ThinkPad-T520:~$ grep . $HOME/.profile
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.
# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022
# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
fi
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/.local/bin" ] ; then
    PATH="$HOME/.local/bin:$PATH"
fi
# set PATH so it includes my private Scripts folder if it exists
if [ -d "$HOME/Scripts" ] ; then
    PATH="$HOME/Scripts:$PATH"
fi
# set PATH so it includes the GO folder if it exists
if [ -d "/usr/local/go/bin" ] ; then
    export PATH=$PATH:/usr/local/go/bin
fi

```
You would see that PATH statements for Users goes in your $HOME/.profile file... That is mine, as an example.

---

### Post by TheFu on 2024-01-14
The .bashrc is run 
[LIST]
[*]at login for the specific userid, if the user's shell (in the passwd DB is bash)
[*]at the beginning of every bash shell, but not for other programs
[/LIST]

Modifying the file and expecting it to be magically already known isn't realistic.  If you open a new bash terminal or logout and login again, then the changes will be seen.

A number of files/settings are only seen at login.  There are a few things that require a reboot to be seen, but that wasn't the question.

---

### Post by ozark_hillbilly on 2024-01-14
thank you for that clarification....

---

### Post by ozark_hillbilly on 2024-01-14
I appreciate everyone's input and I believe with what you all offered has me headed the right way now.

I still remain perplexed why GNU nano in terminal mode shows the complete .bashrc file in its entirety while
nautilus and text editor from Folders do not show the last two lines which are:
   fi
fi

I understand they are used to close conditional statements but why they are not displayed at the very end of the file
unless using GNU nano makes no sense.

Update-

Figured it out. If you use the F11 key the last two lines are then exposed. But just drawing the slidebar on the right
down does not. ????

---

### Post by Holger_Gehrke on 2024-01-14
Is this just a problem with the scrollbar or does the editor actually not have the last two lines ? Try jumping to the end of the file by the keyboard shortcut ctrl-end (works in all the editors I've tried, so it should work in your editor - probably gedit - too).

Holger

---

### Post by TheFu on 2024-01-15
> **ozark_hillbilly said:**
> thank you for that clarification....

There are lots of details like that in  .... [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php) and similar free books.

BTW, your thread title is misleading. It looked like a simple type to me, since "$Path" isn't the same as $PATH or $path.
Unix systems are case sensitive.

---

