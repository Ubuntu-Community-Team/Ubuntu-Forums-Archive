---
title: "username is not in the sudoers file. This incident will be reported."
date: 2022-06-11
forum: General Help
---

### Post by chat-4432 on 2022-06-11
i can't apt install
i try 
sudo adduser username sudo
it show 
> username is not in the sudoers file. This incident will be reported.
i also try 
Open sudoers file using command 
sudo nano /etc/sudoers
still got the same error.
what should i do ??

---

### Post by guiverc on 2022-06-11
Is your username in the sudoers file?

When did you last change the sudoers file?  and did you use a correct method (such as `visudo`) which checks for errors before exiting the editor (Note: *`visudo` isn't connected with `vi` but uses whatever editor you've set as default*).  The importance of this is any error detected in the reading of that file is treated as a *END-of-FILE* marker, meaning subsequent lines are ignored (*don't exist during that sessio*n).

Your issue reads like you're 
- not in the sudoers file, either not mentioned at all, or
- if you are mentioned in that file, it's after the EOF (*end-of-file*) marker which includes any error-in-that file.

Myself; I'd use a *live* system to explore what's in that file (*you didn't provide OS/release details*) if you cannot read it because of Permission denied issues etc, ie. check you're in there, and if you are - what if any errors are present in the file & fix them.

---

### Post by chat-4432 on 2022-06-11
> **guiverc said:**
> Is your username in the sudoers file?
i think no

> When did you last change the sudoers file?  and did you use a correct method (such as `visudo`) which checks for errors before exiting the editor (Note: *`visudo` isn't connected with `vi` but uses whatever editor you've set as default*).  The importance of this is any error detected in the reading of that file is treated as a *END-of-FILE* marker, meaning subsequent lines are ignored (*don't exist during that sessio*n).
i can't use visudo same error 

> Your issue reads like you're 
- in the sudoers file, either not mentioned at all, or
- if you are mentioned in that file, it's after the EOF (*end-of-file*) marker which includes any error-in-that file.
i dont understand can you explain this ??

> Myself; I'd use a *live* system to explore what's in that file (*you didn't provide OS/release details*) if you cannot read it because of Permission denied issues etc, ie. check you're in there, and if you are - what if any errors are present in the file & fix them.
i use ubuntu 22.04 wsl (a lot of bug)

---

### Post by chat-4432 on 2022-06-12
when i install 22.04 wsl 
it was boot as root 
i want to disible it.
do you know how to do this ??

---

### Post by guiverc on 2022-06-12
I missed a rather key "NOT" in one of my sentences which is what confused you. Sorry.

 If your username isn't in the `sudoers` file, your user account isn't allowed to use `sudo` to elevate your privileges. This is your issue.

Normally I'd fix this by

- changing user (`su`; which can be understood as *switch-user* or *super-user*) though a default Ubuntu install has the 'root' account disabled, thus it needs to be setup before it can be used to fix these issues (as `sudo` is the intended way for Ubuntu),

or

- booting *live* media and make changes from there bypassing your existing security (as the only security operating will be that from the *live* media which is usually minimal). You can use this approach to just change files on the disk; regardless of OS that is there, ie. the *live* media can be another OS to the one you're changing, ie. make changes to installed windows, Ubuntu or any other OS as you're just changing data on the disk itself.  It's just booting an OS & using the "Try Ubuntu" type option without installation.

You hadn't mentioned **WSL** ; and I have *almost* no experience with WSL thus I'm incapable of giving advice with regards WSL (I'm using a windows machine <10 minutes per week).

As **WSL** is involved, what I provided may apply, or there are other things at play that I'm not aware of. I don't support WSL & thus don't keep up with what it provides/allows for, where it differs etc.  I only know WSL does have limitations.

---

### Post by yancek on 2022-06-12
> # Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL 

If you look at the ./etc/sudoers file, you should see the lines above.  Problem is you can't view that file without sudo privileges.  You can look at /etc/grouup and you should see a line beginning with sudo and if your user name is not listed, you cannot use sudo.  You cannot add a user to the sudo group without sudo privileges.

Also, WSL is windows software and it is not the same as a standard Ubuntu install.  Try the microsoft support forum or a windows forum for information.  The link below is to the microsoft site and includes information on WSL.  I'd suggest you read that.

[https://docs.microsoft.com/en-us/windows/wsl/about](https://docs.microsoft.com/en-us/windows/wsl/about)

I have one user on my Ubuntu install and that user is not listed in the sudoers file but is listed in /etc/group under sudo.

---

### Post by MAFoElffen on 2022-06-12
One note...

The OP (original Poster) in their post #4: Mentioned "Ubuntu 22.04 WSL", and boots as "Root"...

Tell me if I interpret that wrong, but... I read that as Ubuntu 22.04 running on "Windows Subsystem for Linux" (WSL).

Next, when Ubuntu installs, the first user created is an Administrator Account. If that Windows app created (preconfigured) that User as 'root', that is the first Admin account. If the OP created another account, it looks as if it is just a normal user, without Admin rights and privileges, which is not in the Sudoers file, nor part of thesudo (wheel) group. Trying to do something that needs elevated previldges, as a User that does not have those previledges would cause the error that the OP is getting.

The correct way to correct this would be to be logged in as that Administrator account (root or what that may be) and do:
```

*sudo *usermod* -aG sudo &#8220;username&#8221;*

```
...where 'username" is changed to the username of the User you want to make an Admin.

---

