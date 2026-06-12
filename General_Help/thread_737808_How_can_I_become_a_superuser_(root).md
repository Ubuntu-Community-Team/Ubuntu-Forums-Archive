---
title: "How can I become a superuser (root)?"
date: 2008-03-27
forum: General Help
---

### Post by rectec794613 on 2008-03-27
Hi All! Well, I want to become a superuser on my machine so I can install some stuff into my root folders. This is becoming a problem. I own this computer and I'm very experienced with it already. It says that root owns my iPod! *MY* iPod!
I cant change anything. I cant delete anything in it, either.
So can you help me Become root on my computer or at least give me a command to put in the terminal in which to modify/delete folders?:confused:

Thanks In Advance!:)

---

### Post by dcstar on 2008-03-27
> **rectec794613 said:**
> Hi All! Well, I want to become a superuser on my machine so I can install some stuff into my root folders. This is becoming a problem. I own this computer and I'm very experienced with it already. It says that root owns my iPod! *MY* iPod!
I cant change anything. I cant delete anything in it, either.
So can you help me Become root on my computer or at least give me a command to put in the terminal in which to modify/delete folders?:confused:

Thanks In Advance!:)

```
sudo whatever
``` will allow you root privileges to do any terminal command.

---

### Post by Rocket2DMn on 2008-03-27
You can also enable the root login (dangerous!) by rebooting into recovery mode and running
```
passwd
```
since root is disabled in Ubuntu by default.  Give it a root password and it will be setup.  Your sudo password will still be your password, but this will also allow you to use
```
su
``` to get a root terminal without having to reboot.

---

### Post by tubasoldier on 2008-03-27
If you choose to do what Rocket2DMn says there is a non-rebooting option:

```
sudo bash
passwd
```

or you could just use sudo bash. I'm assuming that you need access to your iPod through a graphical environment? You could run that program with the gksu command:

```
ALT+F2
gksu ProgramYouWantToRun
```

Hope this helps

---

### Post by munwin on 2008-03-27
Or start a terminal and type "sudo su"

---

### Post by -grubby on 2008-03-27
You can use:

```
sudo -i
```

or 

```
sudo su
```

---

### Post by ibuclaw on 2008-03-28
```
 sudo -s 
```
Works good to...

Regards
Iain

---

### Post by rectec794613 on 2008-03-28
Thanks, guys! But I already know about the sudo su command.
If it enables me to do root commands (which it does), what command should I use to modify my iPod through the terminal? P.S. I dont want to do stuff as root through the terminal as opposed to doing that as a logged-in user. Many Thanks in Advance:)

---

### Post by Rocket2DMn on 2008-03-28
Yes, sudo is the best way to go (or gksudo if it's a graphical program) - see [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
That is the preferred way.  An alternate way is when you open a terminal, you can get a root shell using some of those other commands, without having to logout or anything.

---

### Post by p_quarles on 2008-03-28
First of all, the *only* recommended way of using "sudo" to gain a root shell is
```
sudo -i
```
The others have the potential to create shells that will break things.

To the OP's question, there are two ways of accomplishing this:
```
gksudo nautilus
```
Navigate to the iPod's directory, and change the "owner" to your user.

The second way is via the command line, and will require you to find out the name that Ubuntu has given the iPod. You can do this by running:
```
ls /media
```
Make a note of the device name, and run the following command (careful to get it exactly right):
```
sudo chown *username* /media/*devicename*
```
If all goes well, the iPod will be "yours" whenever it is plugged in. :)

---

### Post by hs.chauhan on 2008-03-29
I did this and it worked.

sudo passwd su

Enter the new password and its done.

---

### Post by p_quarles on 2008-03-29
> **hs.chauhan said:**
> I did this and it worked.

sudo passwd su

Enter the new password and its done.
The fact that something works doesn't make it the best practice. Ubuntu is designed to run without a root password enabled, and changing that is officially unsupported. The best way to run a command as root is:
```
sudo *somsecommand*
```
The best way to invoke a root shell is:
```
sudo -i
```
The best way to run a graphical application with root privileges is:
```
gksu *someapp*
```
or
```
kdesu *someapp*
```
While this is not true most other Linux distributions, these commands allow you to do just about everything, and to do it the Ubuntu way.

---

### Post by mvan83 on 2008-03-29
> **p_quarles said:**
> First of all, the *only* recommended way of using "sudo" to gain a root shell is
```
sudo -i
```
The others have the potential to create shells that will break things.


Not to sound like a wiseguy, but do you have a source on that? I've always used sudo -s and thought that was the "correct" way. Don't see anything in the man page regarding which one is "preferred." Thanks.

---

### Post by Lord Illidan on 2008-03-29
I think we lot are ignoring the real problem. You shouldn't have to use root/sudo permissions to access an Ipod. At least, I didn't have to with mine, and I don't have to do it when plugging in any external device.

So, what are you trying to do with your Ipod, and does it work with RhythmBox, Banshee, Amarok, gtkpod, etc?

---

### Post by p_quarles on 2008-03-29
> **mvan83 said:**
> Not to sound like a wiseguy, but do you have a source on that? I've always used sudo -s and thought that was the "correct" way. Don't see anything in the man page regarding which one is "preferred." Thanks.
Actually, both are officially unsupported by Ubuntu:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The issue with "sudo -s" is that it gives you root privileges in your current user's shell environment. While this will not cause problems most of the time, there is the likelihood that someone unsure of how certain operations work will wind up breaking their main user's permissions. This is less likely with "sudo -i" just because it uses root's shell environment, as root is supposed to in the first place.

---

### Post by rectec794613 on 2008-04-08
I watched a YouTube video on [B][COLOR="RoyalBlue"][URL="http://youtube.com/watch?v=x18kONexcYY"]
how to login as root[/URL][/COLOR][/B]
It worked perfectly ):P

---

