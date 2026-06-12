---
title: "General understanding about Users and Groups"
date: 2008-03-05
forum: General Help
---

### Post by _godbout_ on 2008-03-05
Hi there!

I'm quite new in using Linux and Ubuntu. I'm playing with it for one week and I like it a lot :D
I just have a question about the Users and the Groups.

I had to modify some files. If I open them with my current login, the files are in a read-only mode, so I login in root to be able to write them. 
As I did this a couple of times, I decided to change the group of my normal login to root. 
I expected that I wouldn't have to login as root anymore to change these files, but it's not the case. They are still in read-only mode.

So, I assume that I mix up a bit the things here.
Could someone explain me where is my understanding mistake?

It should be nice!

Thanks a lot in advance!

Guillaume

---

### Post by Oldsoldier2003 on 2008-03-05
> **_godbout_ said:**
> Hi there!

I'm quite new in using Linux and Ubuntu. I'm playing with it for one week and I like it a lot :D
I just have a question about the Users and the Groups.

I had to modify some files. If I open them with my current login, the files are in a read-only mode, so I login in root to be able to write them. 
As I did this a couple of times, I decided to change the group of my normal login to root. 
I expected that I wouldn't have to login as root anymore to change these files, but it's not the case. They are still in read-only mode.

So, I assume that I mix up a bit the things here.
Could someone explain me where is my understanding mistake?

It should be nice!

Thanks a lot in advance!

Guillaume
okay a quick explanation:

files permissions are shown in theis format hwen you ls -l:
  -rwxrwxrwx

the first position being a - means its a file not a dir
the next three permissions are the owner permissions (read,write execute)
the nest three are the group permissions (read write execute)
the final are the public permissions (read write execute)


ok if you are a member of root ** GROUP** , but not root you fall under the group permissions

so if the permissions were rwxr-xr-x you would be able to read and execute but not write. Most scripts are chmod to 755 and can only be edited by the owner of the script.

the best thing for daily usage is to use the sudo command if you need to edit a file that belongs to root. only members of the admin GROUP may sudo (**SU**peruser** DO**)

```
sudo nano <filename>
```
 -or-
```
gksudo gedit <filename>
```

gksudo is for graphical apps, sudo is for CLI apps. You dont need to use nano or gedit, you can use whatever application you are comfortable with to edit the files.

Hope this helps you understand, and welcome to Ubuntu.

---

### Post by bodhi.zazen on 2008-03-05
This is a nice link that reviews permissions :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by Oldsoldier2003 on 2008-03-05
> **bodhi.zazen said:**
> This is a nice link that reviews permissions :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)


Lol and there i went doing it the hard way :) kicks self for typing all that out *grins*

---

### Post by _godbout_ on 2008-03-05
Thanks a lot guys!

I really appreciate your quick and consistent answer! I completely forgot about this story of owner/group/public. Of course, I understand better now!

But, as you made my mind clear, I have another question! :D

When I use sudo, the system asks me for the password of my current session. Why it's not the password of the root? I assume that if I want to edit a file which the owner is root, I should fill his password, shouldn't I?

Ah, another small question: the group where I am is called "guillaume". But I can do a sudo. Does that mean that this group is like a copy of the admin group? Or is it just because I have the privileges of Administrate the System?

Small small last question :D
But it's not related to this part, it's just about the text editors. I used to work with vi, under CentOs. But I've found that the Ubuntu's one is not really the same. The shorcuts are different, and I really don't find it easy (the arrows write some **** in the insert mode instead of moving for instance).
Do you know where there is such a difference? People don't use vi under ubuntu? Or maybe I have a too old version?

Thanks a lot guys anyway, you helped me a lot already!

Guillaume

---

### Post by _godbout_ on 2008-03-05
For the Vi text editor, I found a place where the problem is described:

[https://answers.launchpad.net/ubuntu/+source/vim/+question/24182](https://answers.launchpad.net/ubuntu/+source/vim/+question/24182)

I installed it again and it works perfect now! So great :)

---

### Post by _godbout_ on 2008-03-09
> 
When I use sudo, the system asks me for the password of my current session. Why it's not the password of the root? I assume that if I want to edit a file which the owner is root, I should fill his password, shouldn't I?

Ah, another small question: the group where I am is called "guillaume". But I can do a sudo. Does that mean that this group is like a copy of the admin group? Or is it just because I have the privileges of Administrate the System?


Noone has a small answer?... :)

---

### Post by Oldsoldier2003 on 2008-03-09
> **_godbout_ said:**
> Noone has a small answer?... :)

sudo allows you to gain superuser permissions- yes its because you are in the administrators group. 
basically you act as root for that command, or command session if you use sudo -i

---

### Post by bodhi.zazen on 2008-03-10
> **_godbout_ said:**
> Noone has a small answer?... :)

If you prefer, you can set sudo to use root's password, but then you would need to set a root password and ...

Sudo uses a users password so that as an administrator you do not need to give the root password to allow root access. You can configure sudo to allow more limited access, thus sudo is not all or none (unlike su).

---

### Post by Oldsoldier2003 on 2008-03-10
> **bodhi.zazen said:**
> If you prefer, you can set sudo to use root's password, but then you would need to set a root password and ...

Sudo uses a users password so that as an administrator you do not need to give the root password to allow root access. You can configure sudo to allow more limited access, thus sudo is not all or none (unlike su).

another thing I like about sudo is that i can go in and edit roots shell to /bin/false thus making it even more secure for a ssh accessible server. When you toss in  jailkit, publickey authentication and denyyhosts I truly think the sudo implementation is more secure than using root even with an ungodly long password...

---

### Post by _godbout_ on 2008-03-11
Ok, thanks a lot for the answers!

---

