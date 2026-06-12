---
title: "issue with sudo command"
date: 2024-03-17
forum: General Help
---

### Post by thetaipan on 2024-03-17
Hello, 

I'm having some issues using the sudo command. 

dean@dean:~$ sudo apt install nmap
[sudo] password for dean: 
dean is not in the sudoers file.  This incident will be reported.
dean@dean:~$ 

Can anyone help with the above, I'm brand new to using Linux. 

I'm also using this on virtualbox 

thanks! :)

---

### Post by Bashing-om on 2024-03-17
Hello thetaipan - Welcome to the Forums :D

Sorry about the delay in responding - not much history/info provided and took a bit of time to think the best way forward.

so - let's get some info.
Execute terminal command:
```

groups

```
Are both dean and sudo in the output ?

If so then we may consider that "sudoers" is broken.
See now if this fix applies:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)
Re-itirate what psychocats advises - if this file requires editing then open this file with " sudo visudo " ! As this tool also does error checking.

an explanation of what this file is:
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

[INDENT]we can fix this - not a broken heart[/INDENT]

---

### Post by yancek on 2024-03-18
First question, did sudo ever work for you since the initial install?

It does not matter that Ubuntu was installed in Virtual Box.  When you installed, you were required to create a user before the install would complete.  That user would have root/sudo privileges so either 'dean' is NOT that user or your system is corrupted some way.  If you look at the file /etc/group, you should see a line beginning with sudo,  There will be a name listed on that line which will be the user (users) with sudo permissions.

On my system, when I run the 'groups' command both my primary user and sudo show in the output and sudo works exactly as it should.

---

### Post by thetaipan on 2024-03-19
Thanks, will take a look. 

This what comes up when trying to type sudo

dean@dean: $ audo apt install nmap
[sudo] password entered password
dean is not in the sudoers file. This incident will be reported. 
 
  thanks

---

### Post by thetaipan on 2024-03-19
and no, it never worked

---

### Post by yancek on 2024-03-19
Did you try the suggestions made above and just forget to respond?  It was suggested you open a terminal and type:  groups
If you did that, you should see sudo in the output as well as any user name for users you created.  Did you look at the /etc/group file for a line beginning with sudo.  Did you see any user names on that line?  If you are not going to follow instructions there isn't much point in use making them.

---

### Post by thetaipan on 2024-03-19
no need to be clown about it, idiot . I'm brand new to all this, and slowly making my way through things. You must feel amazing insulting people, way to go

---

### Post by thetaipan on 2024-03-19
thank you for the reply. I'm a beginner at all this, I can't say I understand everything you said, so will try slowly to work through it

---

### Post by coley9225 on 2024-03-19
thetaipan, welcome to wonderful, but sometimes confusing world of linux.

Maybe a visual will help with understanding what they would like to see.
first, try this
```
whoami
```

```
charles:$:whoami
charles
```

Then this, which is what they need to see.
```
charles:$:groups
charles adm cdrom **_sudo_** dip plugdev kvm lpadmin docker sambashare
charles:$:


 
```

The first command(whoami) will tell you who the computer thinks you are. The second one (groups) will tell you what groups that person is a member of. If first command does show you as dean,AND the second shows sudo(underlined and bold in my example), then there are other issues. Run those commands and post back the results, then everyone has a starting point.
Good luck.

---

