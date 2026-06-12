---
title: "Since update I have .dmrc file error"
date: 2008-07-03
forum: General Help
---

### Post by Shadowmeph on 2008-07-03
I updated the other day but didn't reboot until this morning. After I rebooted I received an error user home dir must be owned by user. not writeable I can't remember all of it but it says something about a .dmrc file now I don't seem to have a desktop I cannot access anything at all ( its all black) the only thing that I can see is my wired network connection icon I had to dig out the ubuntu disk so I could access the net to find out how I can fix this problem

---

### Post by Shadowmeph on 2008-07-03
ok I remembered I had a simular problem before that I posted here [http://ubuntuforums.org/showthread.php?t=833257]("http://ubuntuforums.org/showthread.php?t=833257") which someone told me to go here[http://ubuntuforums.org/showthread.php?t=827028]("http://ubuntuforums.org/showthread.php?t=827028") which worked that time but this time I cannot access anything not even terminal to put in the command that might fix my problem

---

### Post by sisco311 on 2008-07-03
Boot your ubuntu installation.
Wait for the log in screen, then
press Ctrl+Alt+F2 and log in:
Run this commands:
```
sudo chown -R $USERNAME:$USERNAME $HOME
chmod 0755 $HOME
chmod 0644 ~/.dmrc
```
Press Ctrl+Alt+F7.

---

### Post by drs305 on 2008-07-03
Please refer to sisco311's post #5.

---

### Post by sisco311 on 2008-07-03
> **drs305 said:**
> If you can't boot to recovery or a normal desktop, can you  get to the liveCD desktop? If so:

First, open a terminal in liveCD.

Create a mount point:
```
sudo mkdir /temp
```You need to know your linux partition. If you don't know it, run "sudo fdisk -l" . Mount your linux partition. The XXX should be something like /dev/sda1 and probably has an '*' symbol in the 'boot' column:
```
sudo mount /dev/XXXX /temp
```Once you linux partition is mounted, run these commands:
```

cd /temp
sudo chmod 644 /home/*username*/.dmrc
sudo chown *username*: /home/*username*/.dmrc
sudo chmod 755 /home/*username*
sudo chown *username*: /home/*username*
sudo shutdown -r now

```

the chown command will fail with:[I]chown: invalid user: `username'

@OP [/I]You can try to boot in recovery mode(single user mode) and from the root shell issue:
```
chown -R username:username /home/homedir
chmod 0755 /home/homedir
chmod 0644 /home/homedir/.dmrc
```
replace username with your user name and homedir with your home directory(by default your user name)

---

### Post by drs305 on 2008-07-03
> **sisco311 said:**
> the chown command will fail with:[I]chown: invalid user: `username'


If you are talking about the single colon after username, no it won't. Or maybe I don't understand what you are saying. If you look at the documentation it is an acceptable substitute for *username:username*, which is what I always used to type. Try it, you'll be surprised...

---

### Post by sisco311 on 2008-07-03
> **drs305 said:**
> No it won't. If you look at the documentation it is an acceptable substitute for *username:username*, which is what I always used to type. Try it, you'll be surprised... ;-)
On the live cd *username* is not a valid user.
Maybe creating a new user with: *sudo useradd username *will work[I].
[/I]I know about username**: **and username**. **and username\:

---

### Post by drs305 on 2008-07-03
> **sisco311 said:**
> On the live cd *username* is not a valid user.
Maybe creating a new user with: *sudo useradd username *will work[I].
[/I]I know about username**: **and username**. **and username\:

Misunderstood what you were saying. Thanks. I'll go back and remove the incorrect information.


**Added:**
The OP stated he can't even access a terminal. Is there a way to *chown* his home from the liveCD?

---

