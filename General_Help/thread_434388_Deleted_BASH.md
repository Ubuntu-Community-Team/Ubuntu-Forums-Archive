---
title: "Deleted BASH"
date: 2007-05-05
forum: General Help
---

### Post by Phlosten on 2007-05-05
Whoops!

I was having trouble with my system not being able to run shell scripts. I am not sure why but I was just getting
```
 /bin/bash: bad interpreter: Permission denied
```

when i tried to run my script with

```
./script.sh
```

So in my process of trying to work out what had gone wrong I stupidly rm'ed bash from the /bin folder.
Now I am in a pickle as I cant seem to remedy it by reinstalling bash as I think it needs bash to install.

```

andrew@silverthorn:/bin$ sudo apt-get install --reinstall bash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/790kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 128078 files and directories currently installed.)
Preparing to replace bash 3.1-5ubuntu3 (using .../bash_3.1-5ubuntu3_i386.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Exec format error
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new pre-removal script: Exec format error
dpkg: error processing /var/cache/apt/archives/bash_3.1-5ubuntu3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/bash_3.1-5ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How can I fix my system?

---

### Post by taurus on 2007-05-05
Well, you can boot your PC from the LiveCD, mount the partition where / is, and then just copy /bin/bash from the LiveCD to your harddrive.

Assuming / is located on /dev/hda1, do

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
sudo cp /bin/bash /mnt/ubuntu/bin
ls -la /mnt/ubuntu/bin/bash
```
If everything looks good, reboot and see what happens.

---

### Post by Phlosten on 2007-05-06
OK, I'll give that a go. Niow where did I put that Live CD...

---

### Post by Phlosten on 2007-05-06
Well that restored my bash. I only had a 6.06 Live CD and I run 6.10 and stick to installing with the alternate, but i copied the bash from 6.06 and then once rebooted back into my install i ran the 'sudo apt-get install --reinstall bash' to update everything.

However I still have an issue running my bash script.
I get an error as follows:

```

andrew@silverthorn:~$ ./mountsshshares.sh 
bash: ./mountsshshares.sh: /bin/bash: bad interpreter: Permission denied
andrew@silverthorn:~$ 

```

However if I run the script via the following

```
bash mountsshshares.sh
```

It works fine. What is broken that causes it to need the bash whatever.sh and not be able to use the ./script.sh way?

Can anyone shed any light on how to fix this issue?

---

### Post by taurus on 2007-05-06
```
chmod 755 mountsshshares.sh 
./mountsshshares.sh
```

---

### Post by Phlosten on 2007-05-06
Nope, that doesnt do it. Still the same problem.

---

### Post by jhjessup on 2007-05-08
try relinking /bin/sh:

```
sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh
```

---

### Post by hanzomon4 on 2007-05-08
do you have "!#/bin/bash" as the first line in your script?

---

### Post by psusi on 2007-05-08
It's #!/bin/bash, not !#.

---

### Post by hanzomon4 on 2007-05-08
> **psusi said:**
> It's #!/bin/bash, not !#.

:oops:

---

