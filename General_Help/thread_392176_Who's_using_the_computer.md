---
title: "Who's using the computer?"
date: 2007-03-24
forum: General Help
---

### Post by bogoliubov on 2007-03-24
Hello. Me and some friends have accounts on each others computers (all ubuntu and dynmic dns service) so we can share files easily. 

I can see if someone is logged in, but how can I see if someone has connected with sftp or sshfs? These don't show up if you do 'who', nor in auth.log if I understand things correctly.

---

### Post by bapoumba on 2007-03-24
> **bogoliubov said:**
> Hello. Me and some friends have accounts on each others computers (all ubuntu and dynmic dns service) so we can share files easily. 

I can see if someone is logged in, but how can I see if someone has connected with sftp or sshfs? These don't show up if you do 'who', nor in auth.log if I understand things correctly.
Hi,
what about **users** and **last** ?

---

### Post by bogoliubov on 2007-03-24
No, it's the same stuff basically, only the ones that log in...

But thanks anyway; I didn't know about those commands...

---

### Post by bapoumba on 2007-03-24
Okay. grep in /var/log/messages the ssh or ftp accesses ? (cannot test commands here, so cannot help you much on that, sorry).

---

### Post by bogoliubov on 2007-03-24
Nope, can't find anything. One of my friends was using sftp yesterday, so I know what to look for.

Is there any setting for ssh-server or anything that I can try to change?



Just to make things clear. I can see people who log in (like myself) and people who try to log in but fail, but nothing for sftp stuff

---

### Post by bogoliubov on 2007-03-27
Bump

---

### Post by Tulsapoke on 2007-04-20
Did you ever figure this out?  I am interested in setting this up also with some friends.  So did you just create a guest user account?  What did you lock down?  Do you make everything read only?  Are they confined to the Guest /home directory and just the media files directories? Do you use user groups?  Any basic info on how you set this up would be great.

I am able to get into my account and have free reign to do anything with seemingly all files when I am logged onto SSHFS though my main user account.  I would not want to allow friends this much freedom, nor would I want that on their Ubuntu boxes.

---

### Post by aktiwers on 2007-04-20
With ```
netstat
``` you should be able to see what IP's and stuff that are connected.

---

### Post by bogoliubov on 2007-04-23
Thanks for the help; I'll try netstat!

Tulsapoke:

I set up port-forwarding for ssh (port 22 I think) on my router , then opened up the same port in ubuntus firewall. 
Then I created the accounts for the users, added quotas to each. There should be an howto somewhere on this site that describes how its done.

Basically I only share with read permission. So all files that I share are on one partition, and I am the owner of all the files. 
Then I have created a group for this purpose, I call it "multimedia". I add each of the users to this group.
All group members have read access to the files, and no one else.

Perhaps there is a better way of doing this. If so, please let me know!

---

### Post by FluffyElmo on 2007-04-23
I think sftp logins are logged the same as ssh ones since sftp runs over ssh. Try logging in from another machine while watching the logs for ssh logins and I think you'll see that they match...

---

