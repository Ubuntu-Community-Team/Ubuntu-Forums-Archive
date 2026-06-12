---
title: "I recently upgraded to 14 and now I can not log in"
date: 2014-07-15
forum: General Help
---

### Post by the-paul-84 on 2014-07-15
Hi everyone.

I recently upgraded to Ubuntu 14 from 12. After the download and install finished, I did the restart as prompted. Now, I am unable to log in.

I am confident I'm putting in the password correctly. I tried restarting the computer but still no luck. 

Any ideas? Thanks in advance.

---

### Post by Bashing-om on 2014-07-15
the-paul-84; Hi !

Bad things can happen. Let's see if this is X related or something deeper. ( did you have proprietary drivers installed ??)
Can you log in textually ?
What results:
At the log in screen key combo ctl+alt+F1 for a console.
At this console enter you 'username' followed by your 'password' ( no output to the screen here).
Are you able to log in ?
What now results from attempting to start the GUI from the console with terminal command:
```

sudo service lightdm start

```


Maybe this, maybe, an authorization issue.

[INDENT][INDENT]all in the process of fault isolation
[/INDENT][/INDENT]

---

### Post by the-paul-84 on 2014-07-15
Thanks so much for responding.

I put 
"sudo service lightdm start"

into the prompt but all I get in return is asked to enter in my password. I tried putting it into there, and got
the warning "Login incorrect" and under it says "deathstar login:" (deathstar is the name of the computer). 

What makes it even more strange, is I can still see the files on the samba server on this machine from the 
laptop I'm on right now.

---

### Post by steeldriver on 2014-07-15
You need to enter your **username **at the [FONT=courier new]deathstar login:[/FONT] prompt

You will then be prompted to enter your password

---

### Post by the-paul-84 on 2014-07-15
Geez, I really should have realized that.

After running that command, I get the message "start: Job is already running: lightdm

Is that a good or bad sign?

---

### Post by steeldriver on 2014-07-15
TBH I think we knew that already, however by logging in at the Ctrl-Alt-F1 virtual terminal you have demonstrated that there is nothing fundamentally wrong with your account or login credentials

While you're there, it's worth checking the following:

```

ls -ld ~/{,.Xauthority}

cat ~/.dmrc

ls /usr/share/xsessions

```

You can also look at an xsession-errors to see if there are any obvious clues there:

```

tail ~/.xsession-errors

```

What exactly happens when you enter your login credentials at the GUI (you should be able to get back there using Ctrl-Alt-F7)?

---

### Post by the-paul-84 on 2014-07-16
So I treid running "
ls -ld ~/{,.Xauthority}" and got a response that 
ls: cannot access ~.Xauthority: No such file pr directory
dr-x------ 3 jpk jpk 4096 Apr 16 16:18  /home/jpk/


I ran cat ~/.dmrc and got this in response
and got this in response:

cat: home/jpk/dmrc: No such file or directory

when I ran
ls /usr/share/xsessions

I get this in response:
gnome.desktop

And when I run
tail ~/.xsession-errors

I get this in response:
cannot open '/home/jpk/.xsession-errors' for reading: No such file or directory

I'm getting a bit nervous, this does not seem good. Let me know and thanks again.

---

### Post by steeldriver on 2014-07-16
Well your home directory needs to be writeable by at least you (i.e. dr**w**x------, or octal mode 700), although the default permissions are drwxr-xr-x (mode 755) so I'd suggest

```

sudo chmod 755 /home/jpk

```

to start - let's see if that helps. When you try to log in at the GUI, can you select a session explicitly? if so, make sure you are trying to start a gnome session

---

### Post by the-paul-84 on 2014-07-16
I ran the chmod and still can not login.

When logging in, I do not see anywhere to select a session explicitly so I'm assuming it is going into gnome.

---

### Post by steeldriver on 2014-07-16
Did you have an encrypted home directory? does 

```

ls -Al ~/

```

from the Ctrl-Alt-F1 console list normal home files and directories (Documents, Pictures etc.) or just some ecryptfs stuff?

---

### Post by the-paul-84 on 2014-07-16
It lists the files and directories normally.

---

### Post by Bashing-om on 2014-07-16
the-paul-84; Welp,

> 
It lists the files and directories normally.

So can not be too bad.
In that listing do you see- similar-:
```

-rw-------  1 sysop sysop     209 Jul 16 14:29 .Xauthority
-rw-------  1 sysop sysop   14018 Jul 16 14:29 .ICEauthority

``` where 'sysop' is my username where yours is jpk .
Those files should exist and be created each time you start the session (note the time stamps on the files), with at least these minimum permissions.
If they do not exist, we will have to do some digging and find out why not !

@ steeldriver: 
If we can not start X, then those files will not exist, correct ?

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by steeldriver on 2014-07-16
... ~/.Xauthority would typically persist from the last successful session invocation (not sure if the same applies to ~/.ICEauthority), however I guess it's possible the update process cleans them up.

If /usr/share/xsessions contains only gnome.desktop, then that suggests only the gnome-desktop package is installed (not - for example - ubuntu-desktop). I *think* that lightdm looks in /var/lib/AccountsService/users/*username* for the user's last session - but I don't know what it does if that session is no longer available. However

```

cat /var/lib/AccountsService/users/jpk

```

might let us know if we're on the right track.

---

### Post by the-paul-84 on 2014-07-16
So, both of those files did exist. After running 
cat /var/lib/AccountsService/users/jpk

I get this result:
[User]
XSessions=ubuntu
XKeyboardLayouts=
Background=/usr/share/backgrounds/warty-final-ubuntu.png


As you can assume, I do not know what I am looking at.

---

### Post by steeldriver on 2014-07-16
So the issue *may* be that it's trying to start an ubuntu-session, and the desktop file no longer exists - however I'm kind of surprised that

    A. it's not smart enough to fall back to an available session

and

    B. you don't have the option to manually select gnome-session from the login screen (12.04 has a 'button' shaped like the Ubuntu logo next to the username)

I guess next steps would depend which session you want to use - if you intend to use the ubuntu desktop session, then I guess (re)installing the ubuntu-desktop metapackage would be the obvious thing to try. OTOH if you intend to stick with gnome-session, then we could see what happens if you remove/rename the AccountService file (and possibly the default session from /etc/lightdm/lightdm.conf, if *that* also still refers to ubuntu-session)

**EDIT: **just read your previous post again - do you mean you found ~/.Xauthority and/or ~/.ICEauthority? if so can we see their ownership and permissions please (using 'ls -l')

---

### Post by the-paul-84 on 2014-07-16
The Xauthority line is
-rw------- 1 jpk jpk 157 Jul 15 16:30 .Xauthority

The line for[COLOR=#000000] [/COLOR]~/.ICEauthority is
[LEFT][COLOR=#000000][FONT=Ubuntubeta] -rw------- 1 jpk jpk 4950 Jul 15 16:30 [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta].ICEauthority[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta][/FONT][/COLOR][/LEFT]

I just looked again, and I can still not see an option to manually select gnome-session on the UI login page.

I mostly use this computer as a Samba server for hosting files for the other computers around the house. The strange thing is all of those files can still be accessed. From time to time, I'll watch Netflix on it, but that is about it.

I'm nervous if I do a reinstall I will lose all of the files on the computer. It makes no difference if I stick with gnome or not.

---

### Post by Bashing-om on 2014-07-17
the-paul-84; Hey ;

Looks as if it is a Desktop environmental issue ...
What returns from terminal command:
```

echo $DESKTOP_SESSION

```

And we need to know that the package manager is in a consistent state. What returns form terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```
So we can see what to do about the desktop.

steeldriver's advise still rules:
> 
I guess next steps would depend which session you want to use - if you intend to use the ubuntu desktop session, then I guess (re)installing the ubuntu-desktop metapackage would be the obvious thing to try. OTOH if you intend to stick with gnome-session, then we could see what happens if you remove/rename the AccountService file (and possibly the default session from /etc/lightdm/lightdm.conf, if that also still refers to ubuntu-session)

I'll bet 'tween all of us
[INDENT][INDENT][INDENT]we will get this fingered out
[/INDENT][/INDENT][/INDENT]

---

### Post by the-paul-84 on 2014-07-17
Running echo $DESKTOP_SESSION returns a completely empty line.

sudo apt-get update ran, but the last line had the following error
E: Unable to change to (unreachable)// - chdir - (2: No such file or directory)

sudo apt-get upgrade ran, but told me a bunch of packages have unmet dependencies and suggested I run apt-get -f install

sudo apt-get -f install ran successfully 


I feel a bit foolish for not running these originally. I really can not thank you guys enough to help me with this.

---

### Post by Bashing-om on 2014-07-17
the-paul-84; Humm

> 
Running echo $DESKTOP_SESSION returns a completely empty line.

Completely unexpected outcome, I presently do not know where to go from here -> except (re-)install a desktop.
With that in mind, what was the original install ?

Wont hurt to try
[INDENT][INDENT][INDENT]see what happens
[/INDENT][/INDENT][/INDENT]

---

### Post by the-paul-84 on 2014-07-17
I guess I'll try the reinstall, but I'm really worried about losing the files that are currently on it. If I do a reinstall from a burnt DVD, will I have an option to keep the files?

I do have access to the files on the samba server, but downloading all of them would be a major time commitment as it's close to a terabyte.

---

### Post by steeldriver on 2014-07-17
Actually I wouldn't expect DESKTOP_SESSION to be set within a CLI virtual terminal - I don't see anything suspicious there

@the-paul-84 can you confirm whether you are back in business? your last post is a bit ambiguous

If not I would suggest

```

sudo apt-get install --reinstall gnome-desktop

```

---

### Post by Bashing-om on 2014-07-17
Yepper,

Recon that is why you, steeldriver, get the big bucks .
> 
Actually I wouldn't expect DESKTOP_SESSION to be set within a CLI virtual terminal - I don't see anything suspicious there

True, it is not set -- hey I just checked for my own edification - as always, thanks steeldriver

@the-paul-84; We are not talking about (RE-)installing the operating system - no worry there- but re-installing a desktop environment, 
carry on as steeldriver has advised for the ' gnome-desktop'.

[INDENT][INDENT]bet it turns out well
[/INDENT][/INDENT]

---

### Post by the-paul-84 on 2014-07-17
Wow, I just decided to try using the standard login screen (I wanted to do one last try before I ran sudo apt-get install --reinstall gnome-desktopand it worked, but I am getting some odd issues when logging in.

There is a pop up that says "Sorry, Ubuntu 14.04 has experienced an internal error". There is also an error warning on the top right hand side that says "System program problem detected. Do you want to report the problem now?" I tried restarting the computer and got the same thing happened. 

I tried to open the terminal, but nothing happens.

---

### Post by the-paul-84 on 2014-07-17
Well, I'm not sure what happened, but I can log in and open all of the  programs. The warning messages still come up, but all the programs  including the terminal and wine seem to open without an issue.

---

### Post by Bashing-om on 2014-07-18
the-paul-84; Morning ;

The good news;
> 
 but I can log in and open all of the programs.


So now tell us the bad news, what exactly is "The warning messages still come up" ?// What happens and where does it happen, what did you expect to happen, what actually happened, and what if any errors do you see generated where ??

Are we now in the 
[INDENT][INDENT][INDENT]mopping up stage
[/INDENT][/INDENT][/INDENT]

---

### Post by the-paul-84 on 2014-07-18
It is really nice to see the end in sight!

The warnings only comer up when I first start the machine. There are 4 of them, stacked on on top of the other in the top right hand side. I seperated them and took a screen shot to show what it looks like.

If I click Cancel, they go away and do not appear to come back after that, but if possible, I'd like to stop them from coming up at all.

[ATTACH=CONFIG]254819[/ATTACH]

---

### Post by sedawk on 2014-07-18
When I did an upgrade a few weeks/months back I was missing package unity after the upgrade.
Here is a nice description on how to solve that issue: [http://itsfoss.com/fix-unity-freezes-after-login-ubuntu-14-04/](http://itsfoss.com/fix-unity-freezes-after-login-ubuntu-14-04/)

In case something is wrong with your old configuration files, you can try to create a new user account with 
command line tool "useradd" and then check if a fresh user account works. (You might have to set a password. If
you called the new user "mrfresh", you might have to do "sudo su - root" and then "passwd mrfresh" and finally "exit" to get back to your account)

---

### Post by Bashing-om on 2014-07-18
@the-paul-84; Hey;

OK seems I had my wires crossed - back on track now.

@ sedawk; Appreciate that input, will for sure be of consideration; 1st things 1st.

Paul, Let's take a shot in the dusk here, and once more see what results when 'lightdm' ( because that is 1 of the MANY dependencies of ubuntu-desktop, but the one that has been "removed") is once more re-installed .. looking to see if there are errors reported .
4 instances of "System program problem detected" , are we looking at 4 different issues ? OR just 4 reports from a single issue ?
```

sudo apt-get install --reinstall lightdm

```

reboot and let's see if/what changes.

[INDENT][INDENT]as we proceed merrily on our way
[/INDENT][/INDENT]

---

### Post by the-paul-84 on 2014-07-18
I ran 
sudo apt-get install --reinstall lightdm

and it reinstalled without any issues. I restarted the machine, but the same thing. 4 error messages.

The first error comes up right after I put in my password. The next 2  show up after the desktop loads. Then, the final comes up after it has  been on for about 2 min.

---

### Post by steeldriver on 2014-07-18
Do the dialogs give any indication about what application/process is generating the messages? If not, do

```

tail ~/.xsession-errors

ls /var/crash

```

give any clues?

---

### Post by the-paul-84 on 2014-07-18
Running tail ~/.xsession-errors gives me this

```
jpk@deathstar:~$ tail ~/.xsession-errors
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.

```

```
jpk@deathstar:~$ ls /var/crash
_usr_lib_i386-linux-gnu_libgtk-3-0_gtk-update-icon-cache-3.0.0.crash
_usr_sbin_cupsd.0.crash
_usr_sbin_unity-greeter.104.crash
_usr_sbin_unity-greeter.104.upload
_usr_sbin_unity-greeter.104.uploaded

```

What is strange, whgen I clicked cancel on the warnings, I get this
```
jpk@deathstar:~$ tail ~/.xsession-errors
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: update-notifier-crash (/var/crash/_usr_sbin_cupsd.0.crash) main process (2100) terminated with status 1
init: update-notifier-crash (/var/crash/_usr_sbin_unity-greeter.104.crash) main process (2105) terminated with status 1
init: update-notifier-crash (/var/crash/_usr_lib_i386-linux-gnu_libgtk-3-0_gtk-update-icon-cache-3.0.0.crash) main process (2097) terminated with status 1

```

but running ls /var/crash gives the eaact same result

---

