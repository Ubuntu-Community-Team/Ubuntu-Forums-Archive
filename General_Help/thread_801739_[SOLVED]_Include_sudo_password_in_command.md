---
title: "[SOLVED] Include sudo password in command"
date: 2008-05-20
forum: General Help
---

### Post by Ezetreal on 2008-05-20
Aloha Linux users and abusers...

I looked around the internet but couldn't find a solution, probably because the terms i used to search are too common (password root include command...)

Here's the deal, I have a XP installed as a VM using KVM, I am using a script to launch it (sudo ./kvm_xp.sh). 
I created a launcher on the desktop with that command and when i double click to launch, a terminal opens up asking for the password which makes sense since i sudoed.

Here's my question: in the terminal, is it possible to include the root password for sudo within the command before hitting enter so as to avoid it asking for it ? 
 I am thinking somehing along the lines: sudo (password) ./kvm_xp.sh 
 
Would there be anything like that ?

Thanks for the help.

---

### Post by sdennie on 2008-05-20
I don't think you can do that however, you could enable yourself to run that command with sudo without issuing a password by editing /etc/sudoers (you'll have to google for how to do that).  You will probably want to chmod 0700 the script if you go that route though.

Edit:

Rather than googling, this looks like a good tutorial: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by Anduu on 2008-05-21
Well there is a way without monkeying with the sudoers file however it is ***_[COLOR="Red"]not secure[/COLOR]_***.Anyone peeking at your script will see your password

```
echo yourpassword | sudo -S "command"
```

---

### Post by p_quarles on 2008-05-21
> **Anduu said:**
> Well there is a way without monkeying with the sudoers file however it is ***_[COLOR="Red"]not secure[/COLOR]_***.Anyone peeking at your script will see your password

```
echo yourpassword | sudo -S "command"
```
Definitely don't do that. That's not supported by Ubuntu, and is not generally ever a good idea. 

I don't have any experience with KVM, but if it really requires root privileges to run a VM, I would ditch it. No other VM application does that. I recommend Virtualbox.

---

### Post by Ezetreal on 2008-05-21
Thank you for your suggestions ! I will try and see which one suits my needs best !

---

### Post by danwood76 on 2008-05-21
You may also be able to use fakeroot to launch it depending on why it needs sudo.

---

### Post by ibuclaw on 2008-05-21
I recommend that you must definately set an option in the sudoers file to allow to run it without a password!

echoing your password is a security risk! **Don't Do It!**

Open up a terminal and type in this:
```

sudo cp kvm_xp.sh /usr/local/bin/kvm_xp.sh

```
So now the script is in your $PATH

Next, we'll edit the sudoers file
```

export EDITOR=nano
sudo -E visudo

```
Then under "**# User alias specification**"

Type in the following:
```

**yourname**  ALL=(%root) NOPASSWD: /usr/local/bin/kvm_xp.sh

```
Replace "yourname" with your username.
And you are all set!
```
sudo kvm_xp.sh
```
And it will run!

Regards
Iain

---

### Post by imbjr on 2008-05-21
I was reading this thread and it just occured to me: isn't it a bad idea to run a virtual machine, especially a Windows one, with root-like privlidges?

---

### Post by Ezetreal on 2008-05-21
Thank you Tinivole ! I was trying to do just that but got confused by the CMD_Alias and the ./ in the command that i usually use to run the kvm_xp.sh (./kvm_xp.sh)
I guess using things without understanding them just leads to headaches !

Thank you very much !

I don't know if what i am doing is giving root privileges to the vm (i don't know how that would affect the local machine anyway since it's a diffrent disk technically). But again I use things without quite understanding all that they imply.

---

### Post by sdennie on 2008-05-21
As p_quarles said, a virtualization solution that requires root access is probably not good.  It may be as simple as changing permissions on a file in /dev (for instance VirtualBox loads its driver with full permissions for the vboxusers group).

imbjr: Unless you tell the guest VM how to access the host machine and give it full write access, installing Windows in a VM is probably the least lethal way to beta test a defunct operating system.

---

### Post by ibuclaw on 2008-05-21
> **Ezetreal said:**
> 
I don't know if what i am doing is giving root privileges to the vm (i don't know how that would affect the local machine anyway since it's a diffrent disk technically). But again I use things without quite understanding all that they imply.

[LIST]
[*]**sudo cp kvm_xp.sh /usr/local/bin/kvm_xp.sh**
This copies the script to the $PATH of all users. the PATH is where the shell looks for all executable files to be run without specifying the location of the executable every single time,
ie: The below line would just be a nuisance,,,

**/usr/bin/sudo -E /usr/sbin/visudo**

Type in "echo $PATH" in the console and you'll see what I mean.
[/LIST]
[LIST]
[*]**export EDITOR=nano; sudo -E visudo**
visudo has switched the default editor from nano to vim.
Since many users (including myself) are likely to be confused by the way vim works as a text editor (all I understand myself is the ":wq" command to quit if I accidently open in it!)
[/LIST]
[LIST]
[*]**yourname  ALL=(%root) NOPASSWD: /usr/local/bin/kvm_xp.sh**
 - yourname = only that user can use the sudo command with the script.
 - ALL(%root) = that user executes the script as root.
 - NOPASSWD: = the user needs no password verification to run the script.
 - /path/to/path = the list of programs the user has access to run as root, separated by commas.

[/LIST]

On thoughts about the VM, it will be ran as root. But if the VM does not have access to your filesystem, then you should be perfectly safe.

Regards
Iain

---

### Post by Ezetreal on 2008-05-21
Thanks for the clarification Tinivole !

There is one thing I found out about vim,  :wq saves and exits, that might not be the best thing to use to close it if accidentally opened :), :q  might be a better option !
Hope this helps :)

I've marked this as solved.

Thank you again. I have nothing but respect for linux users and their willingness to help.

---

### Post by ibuclaw on 2008-05-21
> **Ezetreal said:**
> Thanks for the clarification Tinivole !

There is one thing I found out about vim,  :wq saves and exits, that might not be the best thing to use to close it if accidentally opened :), :q  might be a better option !
Hope this helps :)

I've marked this as solved.

Thank you again. I have nothing but respect for linux users and their willingness to help.

Yes, thanks for pointing that out. I will remember that in the future.

Although, to be honest, I never really bump into vim unless I'm editing the sudoers file! So even if I do make a change, the visudo app will make and exclamation at me for a malfunctioned line.
At which point I press "**x**" to "**e(x)it without saving changes to sudoers file**"

Regards
Iain

---

### Post by Ezetreal on 2008-05-21
Type in the following:
```

**yourname**  ALL=(%root) NOPASSWD: /usr/local/bin/kvm_xp.sh

```
Replace "yourname" with your username.
Replace "<SHELL>" with the shell that you use in your script. ie: /bin/bash, /bin/sh, or /bin/ksh for example.

And you are all set!
```
sudo kvm_xp.sh
```
And it will run!


Tinivole, I actually spoke too soon, it isn't working yet, it is still requiring a password from me (It didn't ask for it previously simply because i had already put the password in not too long before).
In the above quote, you say replace "<SHELL>" but I can't find what you are refering to, I just noticed this. I am hoping that is the only problem.

Thanks again

---

### Post by ibuclaw on 2008-05-21
Sorry, I was refering to having the shell put in with the script. ("NOPASSWD: /bin/sh,/usr/local/bin/kvm_xp.sh")
It was a way of doing it that I later resolved (It was also a bit of a security risk).

I've managed to get it working with this simple script:
```

#!/bin/bash
#Name of script: who_am_i
echo "You are $LOGNAME"

```
Here is a working sudoers file.
You should only copy the "bits" you need.
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification
Defaults:ALL timestamp_timeout=0
Defaults:ALL tty_tickets
# User alias specification
studio ALL=(%root) NOPASSWD: /usr/local/bin/kvm_xp.sh
# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

#Test script
studio ALL=(%root) NOPASSWD: /usr/local/bin/who_am_i

```
replace "studio" with your username.

Give the test script a try.
First run "**who_am_i**" (Mark it executable and put it in it's designated place).
You should get the answer "**You are fred**", or whatever your name is.

Then run "**sudo who_am_i**" and it should work no probs (at least, for me it works).

Regards
Iain

---

### Post by imbjr on 2008-05-22
> **vor said:**
> 
imbjr: Unless you tell the guest VM how to access the host machine and give it full write access, installing Windows in a VM is probably the least lethal way to beta test a defunct operating system.

What I was thinking of was the virtualisation software itself not needing root access. No software should run with that power unless it cannot be avoided. 

Or how about this (unlikely?) scenario: Someone installs an MS OS using a virtualisation solution that requires root powers and then installs some piece of malwared s/w. The s/w detects its running in a virtual machine, which it then compromises and then has run of the host PC.

---

### Post by Ezetreal on 2008-05-22
At last ! Success !

I didn't know why it wouldn't work although I was doing everything right or at least I thought I was doing it right.
After a little hair-pulling I managed to get it to work by changing the owner of the file by  chown myname:myname (it didn't work with just chown myname:root)

Thank you very much for all your help Tinivole and everyone else,

I will finally mark this as solved and not look back :)

EDIT:  ARRRGH !!! STILL NOT WORKING ! TALKED TOO SOON AGAIN ! UNSOLVED !

---

### Post by ibuclaw on 2008-05-22
Hmmm...
This is becoming most curious.

OK, firstly, chowning the script shouldn't really do anything.
So undo the changes back to "root:root"

Secondly, add this to your sudoers file:
```

Defaults:ALL timestamp_timeout=0
Defaults:ALL tty_tickets

```
This will set the timestamp to 0. Meaning that it will prompt for a password every single time unless the "NOPASSWD:" option is envoked.
That way, you **WILL** know when it is finally working.

And secondly, to reply to your PM, no. The fact that you have modprobe and iptables and sysctl in your script means nothing.
If you envoke the script as root, you will remain root throughout the whole script.

Oh, by the way, did you get my test script working alright?
That's what I'm most interested in at the moment.
With the results of that I could perhaps somewhat narrow down where the problem might be.

Regards
Iain

---

### Post by Ezetreal on 2008-05-22
I just tried your script with no success.

Maybe I should have done this from the start, here is my sudoers file:
> 
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset
Defaults:ALL timestamp_timeout=0
Defaults:ALL tty_tickets


# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

ezetreal ALL=(%root) NOPASSWD: /usr/local/bin/who_am_i

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
~                                

I just replaced kvm_xp.sh by who_am_i and still no luck.

I hope that the solution is not a simple thing that i forgot to do. Although it would be great to have it fixed, I'd feel like an A**.

Thanks Tinivole

---

### Post by ibuclaw on 2008-05-22
Woops!

Actually, I have to apoligise too!
It **really is** something small!

Cut out the line and put it at the bottom!
```

# Cmnd alias specification

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
ezetreal ALL=(%root) NOPASSWD: /usr/local/bin/kvm_xp.sh

```
Sorry, that is partly my ignorance too. As my box is setup with the "**%admin**" line removed.

Basically, the problem is that the bottom line currently overrides the "**NOPASSWD**" line!

So putting the "**kvm_xp.sh**" command at the bottom fixes this! (finally):lolflag:

Regards
Iain

---

### Post by Ezetreal on 2008-05-23
YIPPIIIIIIIII

This is an excellent message to wake up to !!


Thank you ! Thank you !

I should've sent that sudoers file way earlier ! 

Tinivole you're a genius !

*bow down*

---

