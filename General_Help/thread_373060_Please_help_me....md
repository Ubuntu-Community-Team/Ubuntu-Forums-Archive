---
title: "Please help me..."
date: 2007-02-28
forum: General Help
---

### Post by antimage on 2007-02-28
Hi..everybody...
First, I'm sorry for my bad english..I hope u understand..

I have to migrate (about  400 Computer) from XP to Linux..:popcorn: 
After several test on many distro (SuSE, Kubuntu, Fedora, Mandriva, PCLinuxOS,etc), I choose Kubuntu..

Now, I have a problem with sudo command, I have learned that the sudo password and the kdesu password (for example, Add/Remove Programs,System Setting,and other GUI asking for password) is the current User password, am I right?
So, thats a big problem because I don't want about 400 user with their own password, can change or using sudo command, changing many system setting...

What I want is: 
Installing Kubuntu with 2 username, one is for me (with administrator rights), and one is for user (if they want to change some setting, they must supply my password, not their user password)

--or--

Installing Kubuntu with just 1 username, and change the sudo password, for example:

Username=*newbie*
password=123456
sudo password=abcdef 

(the user *newbie* may only know his password '123456' and dunno the sudo password 'abcdef')

So, If *newbie* type the 'sudo' command, 'sudo' ask for 'abcdef' password, not '123456' password...

And the question is: 
How to change the sudo password? or...
How to make a different password between sudo and user? :confused: 

I'm very respect for every reply and solution, I hope u understand what I say, 
Thanks before, God bless u all...:KS

---

### Post by bettlebrox on 2007-03-01
If the user isn't listed in the /etc/sudoers then they cannot use sudo.

If you have to install Ubuntu on 400 systems you might want to look at installing over the network using PXE:

[https://help.ubuntu.com/community/Installation/Netboot?action=show&redirect=PXEInstall](https://help.ubuntu.com/community/Installation/Netboot?action=show&redirect=PXEInstall)

---

### Post by actuary286 on 2007-03-01
Only the first user created on a machine automatically has Administrative rights. Basically, the sudo password is set to the password of the first user on the machine, the one created during installation. As long as you create your account first any other users will start out with normal user rights and no sudo.

---

### Post by antimage on 2007-03-01
Thanks for the reply...

@bettlebrox...
Thanks bro...
I use visudo -f /etc/sudoers command and edit it, the %admin ALL = (ALL) ALL (or something like this) is completely give permission for every user with their own password, ...If i try to mark # in front of %admin...., every user have admin permission without asking for password...

@actuary286...
Thanks bro...
I create another new_user, locking current session, and start a new session with new_user I've created...
When I try to change some setting with GUI, the password box appears, and I use my new_user password, failed!, I use the first_user password, failed!, I use root password, failed! and then "Conversation with su failed!" or "su returned with error!" or something like that...
but, when I use konsole(shell), I type (for example) sudo cp something, I use my new_user password, Its work!!!

Why can this happen???

---

### Post by Stemp on 2007-03-01
[http://ubuntu-tutorials.com/2007/03/01/allowing-limited-sudo-access-with-visudo/](http://ubuntu-tutorials.com/2007/03/01/allowing-limited-sudo-access-with-visudo/) ?

---

### Post by antimage on 2007-03-01
Thank u Stemp...
I think its work...
:guitar:

---

