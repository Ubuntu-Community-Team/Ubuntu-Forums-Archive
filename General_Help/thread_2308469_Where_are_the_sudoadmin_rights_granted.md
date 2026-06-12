---
title: "Where are the sudo/admin rights granted?"
date: 2016-01-03
forum: General Help
---

### Post by NotQuiteSU on 2016-01-03
I installed Ubuntu Server 14 LTS, with an admin account of 'bob'. I can sudo with no problem. But where are the rights given to bob? (I'm looking to create a new admin account to replace bob).

I checked the sudoers file and group memberships. Nothing lists 'bob'

---

### Post by brian-mccumber on 2016-01-03
To quote from this link - [http://askubuntu.com/questions/410244/a-command-to-list-all-users-and-how-to-add-delete-modify-users](http://askubuntu.com/questions/410244/a-command-to-list-all-users-and-how-to-add-delete-modify-users)

> 
[COLOR=#111111][FONT=Ubuntu]To list all users you can use:[/FONT][/COLOR]
cut -d: -f1 /etc/passwd
[COLOR=#111111][FONT=Ubuntu]To add a new user you can use:[/FONT][/COLOR]
sudo adduser *new_username*[COLOR=#111111][FONT=Ubuntu]or:[/FONT][/COLOR]
sudo useradd *new_username*[COLOR=#111111][FONT=Ubuntu]See also: [What is the difference between adduser and useradd?]("http://askubuntu.com/q/345974/147044")[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]To remove/delete a user, first you can use:[/FONT][/COLOR]
sudo userdel *username*[COLOR=#111111][FONT=Ubuntu]Then you may want to delete the home directory for the deleted user account :[/FONT][/COLOR]
sudo rm -r /home/*username*[COLOR=#111111][FONT=Ubuntu][SUP](Please use with caution the above command!)[/SUP][/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]To modify the username of a user:[/FONT][/COLOR]
usermod -l *new_username* *old_username*[COLOR=#111111][FONT=Ubuntu]To change the password for a user:[/FONT][/COLOR]
sudo passwd *username*[COLOR=#111111][FONT=Ubuntu]To change the shell for a user:[/FONT][/COLOR]
sudo chsh *username*[COLOR=#111111][FONT=Ubuntu]To change the details for a user (for example real name):[/FONT][/COLOR]
sudo chfn *username*[COLOR=#111111][FONT=Ubuntu]And, of course, see also: man adduser, man useradd, man userdel... and so on.[/FONT][/COLOR]


---

### Post by steeldriver on 2016-01-03
By default, the user created at installation is added to the group 'sudo'

```

getent group sudo

id -Gn bob

```

Then members of 'sudo' are granted rights as listed in /etc/sudoers

```

sudo grep '^%sudo' /etc/sudoers

```

---

### Post by brian-mccumber on 2016-01-03
With this you can check what permissions a specific user has for a specified directory by replacing username with the user name you wish to check permissions for that can be obtained using one of the commands from what I pasted earlier.
```

[FONT=monospace]ls -ld /home/username[/FONT]
```

To display all users that have accounts use - ```
[COLOR=#000000]cut -d: -f1 /etc/passwd[/COLOR]
```[COLOR=#000000]

You should find bob in that list. Then to check bob's permissions for a specific directory use the command I posted in the last post replacing home and username with the directory and user name you wish to check.[/COLOR]

You can also to to System Settings ---> User Accounts to see some data on the currently logged in user and you can change your user name and password here also.

---

### Post by NotQuiteSU on 2016-01-03
> **steeldriver said:**
> By default, the user created at installation is added to the group 'sudo'

```

getent group sudo

id -Gn bob

```

Then members of 'sudo' are granted rights as listed in /etc/sudoers

```

sudo grep '^%sudo' /etc/sudoers

```

```

getent group sudo
sudo:x:27:

```

```

sudo grep '^%sudo' /etc/sudoers
%sudo   ALL=(ALL:ALL) ALL

```

> **brian-mccumber said:**
> To display all users that have accounts use - ```
[COLOR=#000000]cut -d: -f1 /etc/passwd[/COLOR]
```[COLOR=#000000]

You should find bob in that list. Then to check bob's permissions for a specific directory use the command I posted in the last post replacing home and username with the directory and user name you wish to check.[/COLOR]
I didn't see bob in that list. I checked sudoers, etc. It's why I'm confused. Whenever I sudo, I am prompted for 'bob' password, but there is no trace I can find of having sudo access

---

### Post by steeldriver on 2016-01-03
What is the full output of

```

id -Gn bob

```

It's possible that 'bob' is in the 'admin' group instead - that is the old (deprecated) equivalent of 'sudo' and has been retained for historical reasons

---

### Post by NotQuiteSU on 2016-01-03
```

 id -Gn bob
bob htpc

```

---

### Post by steeldriver on 2016-01-03
In that case I'm pretty much stumped: does either 'bob' or 'htpc' appear anywhere in /etc/sudoers or possibly in a /etc/sudoers.d/xxx file?

```

sudo grep -r 'bob\|htpc' /etc/sudoers{,.d}

```

---

### Post by matt_symes on 2016-01-03
Hi

> **NotQuiteSU said:**
> ```

 id -Gn bob
bob htpc

```

According to what you have posted, bob is not a member of the sudo group and therefore is not an admin user.

> I didn't see bob in that list. I checked sudoers, etc. It's why I'm confused. Whenever I sudo, I am prompted for 'bob' password, but there is no trace I can find of having sudo access 

sudo will first try to verify you are you by asking for your password. After that it checks to see if you are valid sudo member.

In the example below jerry, a test account, is still asked for his password even though he's not an admin user.

```
media-server1:/mnt/storage_3/weechat/logs:5 % whoami             
jerry
media-server1:/mnt/storage_3/weechat/logs:5 % groups             
jerry
media-server1:/mnt/storage_3/weechat/logs:5 % sudo cat /etc/group > /dev/null 2>&1
[sudo] password for jerry: 
media-server1:/mnt/storage_3/weechat/logs:5 %
```

EDIT:

IO should point iout that i'm assuming you have not edited you sudoers config files as you are a new forum member.

Kind regards

---

### Post by steeldriver on 2016-01-03
Ah my mistake - I thought the OP was saying they *could *use sudo, but didn't know [I]how

[/I]That all makes more sense - thanks matt_symes

---

### Post by matt_symes on 2016-01-03
Hi

> **steeldriver said:**
> Ah my mistake - I thought the OP was saying they *could *use sudo, but didn't know [I]how

[/I]That all makes more sense - thanks matt_symes

I still may be wrong steel driver :D

I have just edited my post to point out that i have assumed that the OP has not edited the sudoers configuration files.

I assumed not as they are a recent member of the forums.

Kind regards

---

### Post by NotQuiteSU on 2016-01-03
It doesn't. I'm stumped as well. It's just the admin account i created when I first installed the OS.

---

### Post by matt_symes on 2016-01-03
Hi

> **NotQuiteSU said:**
> It doesn't. I'm stumped as well. It's just the admin account i created when I first installed the OS.

Have you edited your sudoers configuration files ? 

If no then bob is not an admin capable user unless you have done something funky.

Kind regards

---

### Post by NotQuiteSU on 2016-01-03
Nope, I just followed the installation. It asked for a login account, I said bob, gave it a password, that was it. I constantly do sudo, and it works with the password.

---

### Post by matt_symes on 2016-01-03
Hi

> **NotQuiteSU said:**
> Nope, I just followed the installation. It asked for a login account, I said bob, gave it a password, that was it. I constantly do sudo, and it works with the password.

Under bob's account ?

Please post the output of these commands. Copy and paste them into the terminal and copy and paste the output back here.

```
whoami && sudo grep bob /etc/sudoers{,.d/*}
```

Kind regards

---

### Post by HermanAB on 2016-01-03
the command 'groups' will list all groups that you are a member of.

---

### Post by NotQuiteSU on 2016-01-03
> **HermanAB said:**
> the command 'groups' will list all groups that you are a member of.

> **matt_symes said:**
> Hi



Under bob's account ?

Please post the output of these commands. Copy and paste them into the terminal and copy and paste the output back here.

```
whoami && sudo grep bob /etc/sudoers{,.d/*}
```

Kind regards

output was just 'bob'

---

### Post by matt_symes on 2016-01-03
Hi

> **NotQuiteSU said:**
> output was just 'bob'

That's not copying and pasting the output back here. Please copy and paste for context.

Is htpc in the sudoers file ? Does this return anything ?

```
sudo grep htpc /etc/sudoers{,.d/*}
```

Kind regards

---

### Post by Bashing-om on 2016-01-03
Mat; Hello -

> **matt_symes said:**
> Hi



Under bob's account ?

Please post the output of these commands. Copy and paste them into the terminal and copy and paste the output back here.

```
whoami && sudo grep bob /etc/sudoers{,.d/*}
```

Kind regards

The username would not be in the sudoers file(s) (??_
my results:
```

sysop@1404mini:~$ whoami && sudo grep sysop /etc/sudoers{,.d/*}
sysop
[sudo] password for sysop: 

sysop@1404mini:~$ ls -al /etc/sudoers{,.d/*}
-r--r----- 1 root root 769 Jul 18  2014 /etc/sudoers
-r--r----- 1 root root 958 Feb 28  2013 /etc/sudoers.d/README
sysop@1404mini:~$ ls -al /etc/sudoers
-r--r----- 1 root root 769 Jul 18  2014 /etc/sudoers
sysop@1404mini

```

[INDENT][INDENT]a bit to try and help
[/INDENT][/INDENT]

---

### Post by matt_symes on 2016-01-03
Hi

> **Bashing-om said:**
> Mat; Hello -

The username would not be in the sudoers file(s) (??_
my results:
```

sysop@1404mini:~$ whoami && sudo grep sysop /etc/sudoers{,.d/*}
sysop
[sudo] password for sysop: 

sysop@1404mini:~$ ls -al /etc/sudoers{,.d/*}
-r--r----- 1 root root 769 Jul 18  2014 /etc/sudoers
-r--r----- 1 root root 958 Feb 28  2013 /etc/sudoers.d/README
sysop@1404mini:~$ ls -al /etc/sudoers
-r--r----- 1 root root 769 Jul 18  2014 /etc/sudoers
sysop@1404mini

```

[INDENT][INDENT]a bit to try and help
[/INDENT][/INDENT]

Happy new year :D

If you're a member of the sudo group then you have admin privileges in a default configuration but you can add individual users to the sudo's configuration files and grant them rights to specific commands and even to specific computers. 

sudo is a lot more powerful than many people realise.

For the gory details (and no doubt a headache at the end)

```
man 5 sudoers
```

Kind regards

---

### Post by Bashing-om on 2016-01-03
matt_symes; Ho Kay ...

I have read the man page ... recon it time to go back and read it again .

That will teach me to tell grampa how to suck an egg . Just thought that you were going deeper down a rabbit hole.

[INDENT][INDENT]back to my lurking mode
[/INDENT][/INDENT]

---

### Post by NotQuiteSU on 2016-01-04
> **matt_symes said:**
> Hi



That's not copying and pasting the output back here. Please copy and paste for context.

Is htpc in the sudoers file ? Does this return anything ?

```
sudo grep htpc /etc/sudoers{,.d/*}
```

Kind regards

```

$ whoami && sudo grep bob /etc/sudoers{,.d/*}
bob

``` 

I ran the command 3 times, first time only prompted for password. no output any time
```

sudo grep htpc /etc/sudoers{,.d/*}
[sudo] password for bob:
$ sudo grep htpc /etc/sudoers{,.d/*}
$ sudo grep htpc /etc/sudoers{,.d/*}

```

Since I've done nothing but install the OS, I may just reinstall, choosing a better name this time around

---

### Post by matt_symes on 2016-01-04
Hi

Well that is odd ! No idea what is happening to your system there without some deep forensics.

It's definitely not what i first thought it may be though.

As you've just installed it, a reinstall may be the quickest fix.

Did you follow any online guides ? If so then could you post the links to them, if you still have them. I'd love to know what you may have tried, if anything.

Kind regards

---

### Post by HermanAB on 2016-01-04
I don't see anything wrong with your system.  It seems to work exactly as intended, so re-installing won't make any difference.  You will end up with exactly the same thing.  That is the beauty of Linux.  It is predictable.

---

