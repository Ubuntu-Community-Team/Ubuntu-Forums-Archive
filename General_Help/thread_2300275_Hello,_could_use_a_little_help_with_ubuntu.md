---
title: "Hello, could use a little help with ubuntu"
date: 2015-10-24
forum: General Help
---

### Post by renny4 on 2015-10-24
How can I get into the root dir. I try sudo It asked for my pass word. I typed in my password and it will not let me use root.
In kali I am in root all the time. Can this be done in ubuntu?
thank you
renny:D

---

### Post by sudodus on 2015-10-24
Welcome to the Ubuntu Forums :-)

Using sudo should be enough. It is safer than to log in as root. This is why Ubuntu is set to use sudo.

Type in your password at the prompt, the same password as you use to log in to your user (the first user, that is created when you install the system). There will be no echo (no dots), but 'sudo will listen' and press the Enter key after you have entered the whole password.

Examples:

A command line program:

```
$ [COLOR="#0000FF"]sudo lsblk[/COLOR]
[sudo] password for renny: [enter your password and press the Enter key]
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 298,1G  0 disk 
&#9500;&#9472;sda1   8:1    0    80G  0 part 
&#9500;&#9472;sda2   8:2    0    64G  0 part 
&#9500;&#9472;sda4   8:4    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0     8G  0 part [SWAP]
&#9500;&#9472;sda6   8:6    0    32G  0 part 
&#9500;&#9472;sda7   8:7    0    14G  0 part 
&#9492;&#9472;sda8   8:8    0 100,1G  0 part 
sdb      8:16   0  55,9G  0 disk 
&#9500;&#9472;sdb1   8:17   0   3,7G  0 part 
&#9500;&#9472;sdb2   8:18   0   320M  0 part 
&#9500;&#9472;sdb4   8:20   0     1K  0 part 
&#9492;&#9472;sdb5   8:21   0  51,9G  0 part /
sdc      8:32   0 931,5G  0 disk 
&#9500;&#9472;sdc1   8:33   0    50G  0 part 
&#9500;&#9472;sdc2   8:34   0     1K  0 part 
&#9500;&#9472;sdc5   8:37   0    20G  0 part 
&#9500;&#9472;sdc6   8:38   0     8G  0 part 
&#9492;&#9472;sdc7   8:39   0 853,5G  0 part /media/multimed-2
sr0     11:0    1  1024M  0 rom  
$ 
```

A GUI program:

```
[COLOR="#0000FF"]gksudo gedit[/COLOR]
```

---

### Post by oldos2er on 2015-10-24
> **renny4 said:**
> How can I get into the root dir. 

Do you mean / or /root ? ```
sudo -i
``` should allow you to "cd" into /root

> **renny4 said:**
> I try sudo It asked for my pass word. I typed in my password and it will not let me use root.
In kali I am in root all the time. 

The root *account* is locked by design in Ubuntu; see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Andrew_Welham on 2015-10-25
try

cd /

---

### Post by Kpenguin on 2015-10-25
You could also try
```
gksudo nautilus
```

---

### Post by renny4 on 2015-10-25
thank all your help worked, I like sudo, now that I got my password to work Thanks big time
renny

---

