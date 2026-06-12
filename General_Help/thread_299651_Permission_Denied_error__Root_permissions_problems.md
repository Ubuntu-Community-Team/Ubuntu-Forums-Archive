---
title: "Permission Denied error / Root permissions problems"
date: 2006-11-14
forum: General Help
---

### Post by tedrogers on 2006-11-14
Hi,

I'm specifically referring to a set of commands from page 4 on the following thread:

[http://ubuntuforums.org/showthread.php?t=202834&page=4](http://ubuntuforums.org/showthread.php?t=202834&page=4)

This thread is all about setting up wireless broadcom cards with Edgy and has been very very helpful overall.

However, I am now trying to get my wireless up and running at the terminal (before X windows is loaded) using the following commands:

```
sudo echo 'ifdown wlan0' >/etc/init.d/WlanDown
sudo ln -s ../init.d/WlanDown /etc/rcS.d/S40WlanDown
```

When I run the first one of these commands in the terminal I get the following error:

```
bash: /etc/init.d/WlanDown: Permission denied
```

It has been suggested by another user that I have a problem with my root permissions.

Can anyone advise here?

Normally my sudo commands works fine, for example, when running something like:

```
sudo gedit /etc/X11/xorg.conf
```

I have also checked my user permissions as instructed on this help guide:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

And specifically, this section here:

```
To add a new user to sudo, open the Users and Groups tool from System --> Administration menu. Then click on the user and then on properties. Choose the User Privileges tab. In the tab, find Executing system administration tasks and check that.

In the terminal this would be: sudo adduser $user admin, where you replace $user with the name of the user.
```

This doesn't seem to make a difference, either using the Users & Groups in the Administration Menu or by running the command (where $user is replaced with my username):

```
sudo adduser $user admin
```

Has anyone got any suggestions here??

Thanks in advance all.

---

### Post by bmillsap on 2006-11-14
I had this same problem trying to set IP forwarding this way.  I speculated that the problem is because of the output redirection, it's treated like two different commands, 1) "echo" and 2) a command to write to a file.  The "sudo" status only applies to the first command and doesn't stick for the second command.  It will work (did for me anyway) if you sudo -i to get a root terminal, then type the command, then exit the root terminal.  It will also work in a startup script that's running as root.  But I'm not sure how to sudo commands like this at a regular user prompt.

---

### Post by tedrogers on 2006-11-14
Champion...thanks for that! Gotta love ubuntuforum.org!

I ran root terminal using:

```
sudo -i
```

And then ran each command separately without the sudo prefix:

```
echo 'ifdown wlan0' >/etc/init.d/WlanDown
ln -s ../init.d/WlanDown /etc/rcS.d/S40WlanDown
```

Worked like a charm....well at least the commands weren't rejected...so I would assume it worked like a charm!

Thanks for your prompt response.

---

### Post by dbott67 on 2006-11-14
Can you post the output of:
```
ls -all /etc/init.d/WlanDown
```
and
```
ls -all /etc/rcS.d/S40WlanDown
```

Nevermind... see what happens when you type slow?  It's funny, though, I was thinking of suggesting that you use "sudo su", rather than just sudo (I didn't know the reason why... nice answer, bmillsap!)

-Dave

---

### Post by mabelrxu on 2007-04-22
you could've also used "sudo bash" ... that would've made the entire terminal into under the sudo user ... just remember to type "exit" to get back to the regular user

---

### Post by mabelrxu on 2007-04-22
actually, here's the difference:

sudo bash: makes it a super-user terminal, default directory is /home/root/, aka ~ since you're acting as the root user anyways

sudo -i: you're logging in as the root user, so it's like you're logged in as yourself on the desktop, then you're logging in again, so there's two layers of logging in, default directory is /home/root/

sudo su: makes it a super-user terimal (just like sudo bash), except default directory is /home/userName/, where userName is your own username ... useful for not having to type sudo before everything, yet still having the home directory in the "right" place

---

