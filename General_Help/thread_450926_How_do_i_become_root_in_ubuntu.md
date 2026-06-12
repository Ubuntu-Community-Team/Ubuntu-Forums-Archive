---
title: "How do i become root in ubuntu?"
date: 2007-05-21
forum: General Help
---

### Post by linuxmann on 2007-05-21
i am trying to update clamav by ClamTK. It is asking me to be root in order to update clam av. How do i become root?

---

### Post by RedSquirrel on 2007-05-21
I don't use clamav, but whenever you need root permissions, just use sudo for non-graphical applications and gksudo for graphical applications.

sudo <non-graphical app>
gksudo <graphical app>

See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aldenhg on 2007-05-21
```
sudo your command here
yourpassword
```
will work for most things, but occasionally you'll run into some permission problems for some heavy duty stuff.
For more intense stuff you can actually become root for a terminal session with the ```
su
yourpassword
[I]...
later, when you're done
...[/I]
exit
```
command. You really should do the exit thing at the end, otherwise you have a root session open and that is a bit of a security risk. Sure, chances are nothing will happen, but you might also forget that you're root and totally screw yourself over. Hardcore. You'd be surprised what a ```
rm -rf /
``` will do. Well, it wouldn't surprise you, but you'd be plenty pissed.

---

### Post by linuxmann on 2007-05-22
it says authentication falure sorry. This is when i do that su thing.

---

### Post by dmizer on 2007-05-22
to get a root prompt, simply type:
```
sudo su
```
be sure to type "exit" when you're done to return to your normal user prompt.

---

### Post by Bachstelze on 2007-05-22
You don't use *su* in Ubuntu. Use *sudo -i* instead.

---

### Post by dmizer on 2007-05-22
interesting.

but what is the downside of using 'sudo su' instead?  they both land you in a root prompt.  if there's a finer detail that i'm missing i'd like to know about it.

---

### Post by Bachstelze on 2007-05-22
sudo su is acceptable but su alone doesn't work. The main difference betweeen them is that sudo -i 
simulates an initial login. If makes no difference on a default setup but is more interesting when you begin to customize your login procedure. Also, it is more in the Ubuntu spirit of "no su".

---

### Post by anaconda on 2007-05-22
hmm..
I prefer the "sudo su", because it wont change the current directory. With "sudo -i" the current directory changes to /root 
I dont think they have any other difference.

---

### Post by ghell on 2007-05-22
A long time ago I used to use "sudo bash" :p This seems to stay in the current directory etc, it keeps the bashrc and ~ from the main user, etc. I don't know how bad an idea it is to use this.

I use su on fedora a lot but in ubuntu it seems far more stable to use sudo and sudo -i. You may be able to set some flag to get it to keep the current directory when using -i or something, I don't know. in su this is changed by using su - rather than su

Note that there is also a "Root Terminal" under system tools, disabled in the menu by default.

---

### Post by bung33 on 2007-05-22
After I initially installed 7.04, no password was setup for root, so I was unable to sudo any command. I would receive the same authentication failure message. However, after creating a password for root in the users and groups program, I was able to sudo everything. During the installation of 7.04, I wondered why I was never asked for a root password. Anyway, if you find you can't sudo anything, you might want to check the user settings for root. It could very well be that a password was never created to begin with...

---

### Post by Bachstelze on 2007-05-22
That was definitely not the problem. I never set a root password in my Feisty and sudo works perfectly well...

---

### Post by crane on 2007-05-22
> **bung33 said:**
> After I initially installed 7.04, no password was setup for root, so I was unable to sudo any command. I would receive the same authentication failure message. However, after creating a password for root in the users and groups program, I was able to sudo everything. During the installation of 7.04, I wondered why I was never asked for a root password. Anyway, if you find you can't sudo anything, you might want to check the user settings for root. It could very well be that a password was never created to begin with...

When you set up the system the first user you create should have sudo rights. When you use the sudo command and it asks for your password, just enter your password. I can't imagine it not working , especially if you have right s to edit/change users on the system.

---

### Post by bung33 on 2007-05-28
I was confused by the same thing. I've never had a problem sudoing something the first time before. However, I tried my user password probably ten times but to no avail. It wasn't until I created a password for the root account, which coincidentally was the same anyway, that it worked...

---

