---
title: "Just installed Ubuntu and don't have Admin - Please HELP?"
date: 2007-08-18
forum: General Help
---

### Post by Joesplace on 2007-08-18
I am completely new to Linux and loaded Ubuntu 7.04 and have a problem. I don't have administrative privileges on the only login name it setup. How do I get admin privileges turned on? 

Whenever I attempt to login as root I get this error: "The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator."

Can someone please assist with details so I can access my other drives, external HD, and networks?

---

### Post by steveneddy on 2007-08-18
By default, you can't log in as root. 

What are you trying to do so we can help you?

There are ways to get admin privilages by using the 

```
sudo
```

command.

You should be able to do what you need without logging in as root.

---

### Post by Joesplace on 2007-08-18
I have three partitions setup on my 80 gig HD and one has all my data and the other has XP. I can't mount any volume and get this error when I try: "Error org.freedesktop.Hal.Device.PermissionDeniedByPolicy."

I saw an error that said my login does not have admin privileges and I thought that might be the answer. Any ideas? :(

---

### Post by Sef on 2007-08-18
Applications > Accessories > Terminal

type

sudo apt-get update  [enter]

then

password  (log in password)  [enter]

If it updates, you have admin privileges.

---

### Post by Joesplace on 2007-08-18
This is what I get, doesn't do much just back to prompt:

joe@joe-laptop:~$ sudo apt-get update
Password:
joe@joe-laptop:~$

---

### Post by HermanAB on 2007-08-18
If you don't want to type sudo all the time:
$ sudo -s
Password: supersecret
#

La voila!

Herman

---

### Post by Joesplace on 2007-08-18
ok, I did that but I still can't access any volume. So does this mean I have admin privileges or how do I turn that on?

---

### Post by Joesplace on 2007-08-19
trying to mount another volume, error says"hal-storage-fixed-mount refused uid 1000"

---

### Post by steveneddy on 2007-08-19
[Try reading this]("http://www.psychocats.net/ubuntu/mountwindows").

---

### Post by HermanAB on 2007-08-19
If you have a # prompt, then you are root.  Anyhoo, you can see what is going on using the user manager clicketyclick thingy, or you can display your group membership with:
$ groups

You should be a member of the admin group.

Cheers,

Herman

---

### Post by strabes on 2007-08-19
These two pages will teach you a bit about root/sudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Joesplace on 2007-08-19
ok- just found out what happened. My son said he unchecked the admin box in the only login account. How do I get that back?

---

### Post by Joesplace on 2007-08-19
ok- just found out what happened. My son said he unchecked the admin box in the only login account. How do I get that back?

---

### Post by Joesplace on 2007-08-19
Thanks Guys - figured it out. Reboot into recovery mode, login then type "addgroup {username} admin" - after rebooting, admin privileges are restored . . . .

---

