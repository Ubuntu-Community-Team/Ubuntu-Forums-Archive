---
title: "gutsy wont recognize password. Recovery not an option."
date: 2008-04-22
forum: General Help
---

### Post by jakupl on 2008-04-22
Suddenly yesterday Ubuntu kept saying, that my password was wrong. 
I am on an ASUS A6rP. which needs 'hpet=disable' on the boot parameters to work.
When I try to boot in recovery mode, it won't work. even when I add 'hpet=disable'.

This password problem has happened before. But back then, I had no problems booting in recovery mode, but it didn't work. Even when I changed my password to '1234' ubuntu kept saying the password was wrong at login. So I reinstalled and the problem vanished. Until yesterday.

What could the problem be? I really don't want to reinstall again.
BTW. I'm running Gutsy gibbon and i'm currently running the live cd.
EDIT; I've ordered the hardy cd. so I'm going to wait probably 10 weeks for it to arrive. Hardy installation is not an option yet either.

---

### Post by ibuclaw on 2008-04-22
You could use your Current Gutsy LiveCD.

When you boot up into it.
Mount your Linux Filesystem to /media/ubuntu folder.
```
mount /dev/**sda1** /media/ubuntu
```
If you have a separate Partition for your Home Directories, mount that inside your /media/ubuntu folder.
```
mount /dev/**sda2** /media/ubuntu/home
```

Then change the root filesystem from the LiveCD to your Ubuntu System.
```
chroot /media/ubuntu
```
You are now inside your Ubuntu Filesystem as root.
Almost all users and applications from within your filesystem can be ran/edited.
You can even do an "apt-get upgrade" and your system will be upgraded!

But back to the problem at hand...
Switch to your user (no password needed)
```
su **username**
```
then type in:
```
passwd
```
And if all goes well.
You should go through it like this:
> Changing password for **username**.
(current) UNIX password: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully

Don't pick a password like 1234, the passwd manager will tell you that it is too simple.

When done, exit the terminal, reboot and remove the LiveCD.
And try out your fresh new password in gdm.

Regards
Iain

---

### Post by jakupl on 2008-04-22
Thanks for the reply, but when I try the first thing you said, I get,

```
ubuntu@ubuntu:~$ mount /dev/sda1 /media/ubuntu
mount: only root can do that
```

:confused:

---

### Post by dperfors on 2008-04-22
use:
```
sudo mount ...
```:)

---

### Post by jakupl on 2008-04-22
I checked with GParted, and it calls it '/dev/hda1' not sda1.
but I still get the same result.

```
ubuntu@ubuntu:~$ mount /dev/hda1 /media/ubuntu
mount: only root can do that
```

And I checked the cd for integrity, it's all good.

---

### Post by jakupl on 2008-04-22
oh... hehehe

---

### Post by jakupl on 2008-04-22
It wont work... what does it mean.

i don't suppose it should be '/home/ubuntu' huh


```
ubuntu@ubuntu:~$ sudo mount /dev/hda1 /media/ubuntu
mount: mount point /media/ubuntu does not exist
```

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/ubuntu
mount: mount point /media/ubuntu does not exist
```

---

### Post by ibuclaw on 2008-04-22
I used that as an example.

but if you want to follow it to the book.

use
```
sudo mkdir -p /media/ubuntu
```
And then continue with the how to :)

[EDIT]
And on the word with sudo (sorry for that)
It'll be "**sudo chroot /media/ubuntu**" too.

Then you'll become root within the "/media/ubuntu" filesystem.

Regards
Iain

---

### Post by jakupl on 2008-04-22
ok great. but now when I do the step nr. 2.
i get
```

ubuntu@ubuntu:~$ sudo chroot /media/ubuntu
chroot: cannot run command `/bin/bash': No such file or directory
```

---

### Post by jakupl on 2008-04-22
.... wait

---

### Post by jakupl on 2008-04-22
it worked, but I still get the same problem. it wont recognize the password

```
jakup@ubuntu:/$ passwd
Changing password for jakup.
(current) UNIX password: 
passwd: Authentication failure
passwd: password unchanged
```

---

### Post by ibuclaw on 2008-04-22
Hmm...

Probably best to back up your home folder.
Then remove and re-add your account,

```

jakup@ubuntu:/$ sudo cp /home/jakup /home/jakup.bak
jakup@ubuntu:/$ exit
root@ubuntu:/$ deluser --backup-to /home jakup
root@ubuntu:/$ adduser jakup

```
That should give you two copies of your home folder, one in a tarball.

One done, just copy or extract the files back into your home folder when you log back in.

Regards
Iain

---

### Post by jakupl on 2008-04-22
thankyou very much... where did the thank button go?? is that feature removed?? what a pity.

---

### Post by jakupl on 2008-04-22
oh no! but now when I try to do something witch requires super user, i get:

```
jakup@bobby:~$ sudo mv stardict-freedict-dan-eng-2.4.2 /usr/share/stardict/dic
[sudo] password for jakup:
jakup is not in the sudoers file.  This incident will be reported.
.
```

---

### Post by ibuclaw on 2008-04-22
Site is going through some updates atm.

It should all be back in a day or two.

As for your password disappearing...
It seems awfully strange for that to happen.

Ironically enough, I've just found a simpler way to fix it (darn it, how did I miss that in the passwd manual...:lolflag:)

Alternatively, while booted in the LiveCD and chroot'd to your Ubuntu Install, you could've done:
```

root@ubuntu:~# passwd -d jakup
Password changed.
root@fredbuntu:~# passwd jakup
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully

```

Ah well... I've learnt something new today.

Regards
Iain

---

### Post by jakupl on 2008-04-22
no. the last time this happened, before I reinstalled some time ago, i tried this in recovery mode, but it didn't work. It said that the password was updated successfully, but it still wouldn't allow me to login

---

### Post by ibuclaw on 2008-04-22
Oops...
I know where it went wrong though!
You're not part of the group "admin" anymore...
You'll have to go back to LiveCD (sorry)
Follow the steps up to chroot.
Then type in:
```
 useradd -g admin jakup
```

Again, sorry.

Iain

---

### Post by jakupl on 2008-04-22
thanks :) but it gives me this:

```
root@ubuntu:/# useradd -g admin jakup
useradd: user jakup exists
```

and the problem is still there.

---

### Post by jakupl on 2008-04-22
I solved this myself. This is what i did, if anyone encounters the same problem.

First I did a backup of the "group" file

```
sudo cp /etc/group /etc/group.bak
```

then I opened it.

```
nano /etc/group
```

and put my username at the end of the line that says "admin" like this:

```
admin:x:110:jakup
```

but I don't like it... because it feels like i'm running as root... maybe I am??

---

### Post by ibuclaw on 2008-04-22
It's all good.

If you read the sudoers file, you'll find this line:
> 
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

As it so rightfully says, only members of the admin group may gain root privileges.

So what you've done is right.

Regards
Iain

---

### Post by jakupl on 2008-04-22
yeah it feels good now :) thankyou very much for all your help.

---

