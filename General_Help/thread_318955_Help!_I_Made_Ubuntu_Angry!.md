---
title: "Help! I Made Ubuntu Angry!"
date: 2006-12-14
forum: General Help
---

### Post by DJ Lushious on 2006-12-14
Hello, all! I've been playing around with Ubuntu now for a few weeks and I'm loving it. Well, the other day I was reconfiguring a Samba install when I messed something up. What it amounts to is that I was setting access levels for my folders with the "chmod" command and now I get a peculiar error at login that I don't know how to remedy. This is what the error message has to say:

> User's $HOME/.dmrc file is being ignore. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory

I don't quite remember the directory path I had originally used chmod on to get this error, but I do know I set the access to 777. Would anyone here be willing to help a noob Ubuntu user, such as myself? Thanks in advance!

---

### Post by Shatrat on 2006-12-14
You can run ```
ls -l $HOME/.dmrc
``` to see the details on that file.
Double check the permissions and owner.

---

### Post by DJ Lushious on 2006-12-14
> **Shatrat said:**
> You can run ```
ls -l $HOME/.dmrc
``` to see the details on that file.
Double check the permissions and owner.
"-rw-------" So that's, what, a permission of 6?

---

### Post by gordyt on 2006-12-14
To change the ownership, just do:

chown your_user_name ~/.dmrc

Be sure and replace your_user_name with YOUR user name.  If you are not sure what to use for that, just type whoami.

Then to change the permissions to 644, just do:

chmod 644 ~/.dmrc

--gordy

---

### Post by DJ Lushious on 2006-12-14
> **gordyt said:**
> To change the ownership, just do:

chown your_user_name ~/.dmrc

Be sure and replace your_user_name with YOUR user name.  If you are not sure what to use for that, just type whoami.

Then to change the permissions to 644, just do:

chmod 644 ~/.dmrc

--gordy
Tried that, still got the same error. Maybe the problem is with my $HOME directory, and not solely .dmrc?
Here's the output of my ls -l $HOME:
[IMG]http://djlushious.home.comcast.net/pictures/ubu.gif[/IMG]

---

### Post by ButteBlues on 2006-12-14
```
chmod 644 -R ~
```

I had that issue a bit back.

---

### Post by DJ Lushious on 2006-12-14
> **a simple façade said:**
> ```
chmod 644 -R ~
```

I had that issue a bit back.
I get "Permission Denied" on that Terminal command. :-k

---

### Post by ButteBlues on 2006-12-14
Prefix that command with "sudo".

If that doesn't help, then the best way to circumvent the issue is to simply create another user and go from there.

---

### Post by Alex1770 on 2006-12-14
Just to check, can you type ```
ls -al ~
```?

---

### Post by DJ Lushious on 2006-12-14
Grr... Now I seemed to have locked myself out of my home directory. Whenever I start Terminal I get "Failed to change to directory '/home/lushamania' (Permission denied) I'd imagine the best way to deal with this now is to log in as root.

> Prefix that command with "sudo".

If that doesn't help, then the best way to circumvent the issue is to simply create another user and go from there.
I had also tried sudo. That seems to have gotten me where I am now. :(

EDIT - Yeah, I'm locked out of my user name. I rebooted and tried to log in and it game me an error message about how the session lasted for less than 10 seconds and then kicked me back out to the login screen. I'm now in as root, though.

---

### Post by ButteBlues on 2006-12-14
> **DJ Lushious said:**
> Grr... Now I seemed to have locked myself out of my home directory. Whenever I start Terminal I get "Failed to change to directory '/home/lushamania' (Permission denied) I'd imagine the best way to deal with this now is to log in as root.


I had also tried sudo. That seems to have gotten me where I am now. :(
You shouldn't have permission denied. >_>

Hit Ctrl+Alt+F1, and login at the terminal.

Try:
```
sudo chmod 755 /home/lushamania
```

---

### Post by DJ Lushious on 2006-12-14
> **a simple façade said:**
> You shouldn't have permission denied. >_>

Hit Ctrl+Alt+F1, and login at the terminal.

Try:
```
sudo chmod 755 /home/lushamania
```
Well, that fixed it! No error message at login, and I seem to be able to run everything! If I have any more problems I'll post 'em, but for now thanks for all of the help! You all have been a great help! I really appreciate everyone going out of their way to help me! :mrgreen:

---

### Post by ButteBlues on 2006-12-14
> **DJ Lushious said:**
> Well, that fixed it! No error message at login, and I seem to be able to run everything! If I have any more problems I'll post 'em, but for now thanks for all of the help! You all have been a great help! I really appreciate everyone going out of their way to help me! :mrgreen:
It's what we do. ;)

---

