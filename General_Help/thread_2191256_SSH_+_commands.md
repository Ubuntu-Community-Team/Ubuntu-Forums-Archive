---
title: "SSH + commands"
date: 2013-12-01
forum: General Help
---

### Post by chris137 on 2013-12-01
Hi,
I spent a lot of time trying to figure out how to solve my problem.
I want to connect to a remote computer without entering my password:
```
sshpass -p password ssh host
```
works
Then I want to add commands to it.
```
<<EOF
cd /opt/
echo -n "directory changed"
read taste
EOF
```
almost works.
These commands get sent but too early.
I am not connected yet when those commands are sent so I get this output:
```
Last login: Sun Dec  1 23:25:13 2013 from blabla
cd /opt/
echo -n "directory changed"
read taste
user@host:~$ cd /opt/
user@host:/opt$ echo -n "directory changed"
directory changeduser@host:/opt$ read taste
```
I tried to use sleep but I don't know where to put it.

It's just so frustrating to see how close I seem to be but my computer just works too fast.
Help please :/

~Chris~

---

### Post by papibe on 2013-12-01
Hi chris137.

I would recommend you to use passwordless keys instead of 'sshpass'. This is a good start for that: [SSH/OpenSSH/Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys").

Then ssh itself can receive a remote command. For instance:
```
ssh host 'cd /opt; ls -aCF; echo -n "directory changed"; read taste'
```
In this case, there's no need for time coordination because the command is suppose to execute afer login.

I hope it helps. Let us know how it goes. 
Regards.

---

### Post by chris137 on 2013-12-02
Alright, so what you suggested did not work.
I did get another approach though.
I added a key and can now login without sshpass or my password.
The following matches what I originally tried to do and works:
```
#! /bin/bash
ssh -t server 'cp -r /opt/directory/ /home/chris/directory; echo -n -e "data saved!\n"; read taste; exit; /bin/bash'

```
I also modified the command a little bit after I found out i did not need certain parts of the command.

Thanks for your help though.
It took me to the right direction!

I am also open for suggestions if you have other tips like the ssh key.

~Chris~

Edit:
So I used this on another command I do via ssh but here I got the problem that I have to run that command as sudo.
Thus there will be another password prompt.
Any way to bypass this one?

Aaand another edit: (Just for edit#1, first problem still solved)
My problem just got more complicated after I realized i forget I am using screen.
So I try to do the following:
```
ssh -t server 'screen -r 20353.svr; sudo start_process; /bin/bash'
```
Unfortunately this does not work with screen.
Using this line of code i would start a screen session and only after detaching it would run my process.
Suggestions?

---

### Post by papibe on 2013-12-02
You can remove the password requirement for a sudo command if you want to. I would recommend reading about sudo and root [here]("https://help.ubuntu.com/community/RootSudo") first (just so you have a bigger picture).

Then, take a look at this [tutorial]("http://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password") on how to set a passwordless sudo for an specific program, which is safest that disable the password for all.

As for the 'screen' part, I'd like to know what you are trying to accomplish before I could give you more specific pointers. 

It seems like the screen 'svr' is already running or are you trying to create one?
Is it running under a regular user or under sudo?
Is the 'sudo start_process' command supposedly run inside the screen?  
Are you trying to launch an interactive session after the commands are executed?

Regards.

---

### Post by chris137 on 2013-12-02
I will deal with passwordless sudo tomorrow and will first answer your last questions:
Screen is already running and is not planned to be stopped.
It is running under a regular user but could also run as sudo if helpful.
Yes, it is supposed to run inside.
Yes, I will have to be able to give input anytime. That's why i chose screen.

This time while writing I got another approach and it seems to work.
I run the following command now:
```
ssh -t asd 'screen -r 20353.svr; screen -S 20353.svr -X stuff $"'sudo process'"; exit; /bin/bash'
```
Since I never close the screen session it seems I will not have to enter the sudo password again.
I just have to click enter and the process starts.
Originally I tried to start it immediatly but \n did not work and I now think that it is better to start it manually.

---

### Post by papibe on 2013-12-02
Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1809501&highlight=screen+stuff"). In order to sent a command to a screen running an interactive shell, you need to emulate the enter.

As for creating an interactive shell after sending a command to an specific screen, I would also use screen as in this [thread]("http://ubuntuforums.org/showthread.php?t=2151593&highlight=ssh+screen").

Putting all together, I think something like this would help you:
```
ssh -t host 'screen -S svr -X stuff "your_process^M"; screen -S rsession'
```
That would:
[LIST]
[*]connect you to host.
[*]execute 'your_process' in the screen 'svr' without attaching the terminal to it.
[*]finally it generate a new interactive session under another screen (called rsession).
(when you logout out of that screen you would logout of host too).
[/LIST]
Does that help?
Regards.

---

