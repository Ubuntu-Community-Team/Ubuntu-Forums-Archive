---
title: "[SOLVED] can't log in or boot ubuntu? plz help"
date: 2008-03-07
forum: General Help
---

### Post by robertchahine on 2008-03-07
i was trying to install the "aqua dreams theme". so in the instruction there was a part that tells to change the menu in the grub folder. when i changed it and reboot the pc.but :( when it reboot sUbuntu would run the start up logo but only to get STuck at 1/4 of the way then  it tells me this error"exec:7 /etc/init.d/rcS : permission denied" and that it's terminated with status 2 or something like.
every time i turn on my pc i have this msg.i checked the pc for errors with live cd, but no error found.
what should i do?
pls help

---

### Post by taurus on 2008-03-07
Can you boot your machine into recovery mode from GRUB menu?  If you can, post the outputs of these two commands.

```
ls -la /etc/init.d/rcS
cat /etc/init.d/rcS
```

---

### Post by robertchahine on 2008-03-07
ok, i boot my machine into recovery mode and put this code
what to do next taurus?

---

### Post by taurus on 2008-03-07
Can you post the outputs of these commands here?  I just want to know what kind of permissions you have for /etc/init.d/rcS since that seems to be the trouble point.

Does it look something like this?

```

-rwxr-xr-x   1 root root   117 2007-10-04 07:17 rcS

```

---

### Post by robertchahine on 2008-03-07
-r--r-----r root root 117 oct 4 14:17 /etc/init.d/rcS

---

### Post by taurus on 2008-03-07
That could be the problem.  Try changing permissions back to where it was.

```
chmod 755 /etc/init.d/rcS
ls -la /etc/init.d/rcS
```
And if it looks good, reboot and see if Ubuntu is happy now.

```
shutdown -r now
```

---

### Post by robertchahine on 2008-03-07
i didn't change, it tells me that changing permission " /etc/init.d/rcS"is read-only file system.

---

### Post by taurus on 2008-03-07
Do you know which partition / is on your harddrive?  _Assuming_ it's /dev/sda1, boot your machine with the liveCD.  Then, mount your / partition

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
```
and post the output of this command again.

```
ls -la /mnt/ubuntu/etc/init.d/rcS
```

---

### Post by robertchahine on 2008-03-07
then what to do taurus?

---

### Post by robertchahine on 2008-03-07
i did everything you said? what to do now? do i reboot the system?

---

### Post by taurus on 2008-03-07
What do you mean?  Have you mounted your harddrive and changed the permissions as in my previous post?

Can you post the output of this command to make sure the permissions stick before you reboot it?

```
ls -la /mnt/ubuntu/etc/init.d/rcS
```

---

### Post by robertchahine on 2008-03-07
yes
it tells me "-rwxr-xr-x   1 root root   117 2007-10-04 07:17 /etc/init.d/rcS"

---

### Post by robertchahine on 2008-03-07
so do i reboot the machine now?

---

### Post by taurus on 2008-03-07
Go for it.

---

### Post by robertchahine on 2008-03-07
when reboot it, it told the same error :(

---

### Post by robertchahine on 2008-03-07
thank you very much taurus.
do you think that the only way is to reinstall ubuntu?

---

### Post by taurus on 2008-03-07
Let's start from the beginning again.

I assume you are booting from the LiveCD right now.  Can up post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That is a lower case letter L, not number 1.

---

### Post by robertchahine on 2008-03-07
ok, one second

---

### Post by robertchahine on 2008-03-07
it gives me this msg into the terminal


Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29032902

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4678    37576003+  83  Linux
/dev/sda2            4679        4865     1502077+   5  Extended
/dev/sda5            4679        4865     1502046   82  Linux swap / Solaris

---

### Post by taurus on 2008-03-07
Now run

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
ls -la /mnt/ubuntu/etc/init.d/rcS
```
Post the output of the last command.

---

### Post by robertchahine on 2008-03-07
it tells me:

ls: /mnt/ubuntu/etc/init.d/rcS: Permission denied

---

### Post by taurus on 2008-03-07
```
sudo ls -la /mnt/ubuntu/etc/init.d/rcS
```
Did you by any change playing around with the permissions of / or /etc before?

---

### Post by robertchahine on 2008-03-07
once i change it to 777 but someone helped me and returned it to normail recovery mode to 0440

---

### Post by robertchahine on 2008-03-07
i tried again the code:
> sudo ls -la /mnt/ubuntu/etc/init.d/rcS

it tells me :
-r--r----- 1 root root 117 2007-10-04 11:17 /mnt/ubuntu/etc/init.d/rcS

---

### Post by taurus on 2008-03-07
> **robertchahine said:**
> once i change it to 777 but someone helped me and returned it to normail recovery mode to 0440

Which directory did you change it to 0440?  That could be your problem right there.  If /etc has the permissions of 440, then your /etc/init.d/rcS will be stuck with that permissions--read-only for owner and group.

---

### Post by robertchahine on 2008-03-07
yeah , it's the /etc directory.
so what to do now?

---

### Post by taurus on 2008-03-07
Try (assuming we are still booting from the LiveCD),

```
sudo chmod 755 /mnt/ubuntu/etc
sudo chmod -R 755 /mnt/ubuntu/etc/init.d
ls -la /mnt/ubuntu/etc/init.d/rcS
```
Post the output of the last command here again.

---

### Post by robertchahine on 2008-03-07
ok taurus my friend, i wrote the code in the terminal
it tells me 

-rwxr-xr-x 1 root root 117 2007-10-04 11:17 /mnt/ubuntu/etc/init.d/rcS

what to do know?

---

### Post by taurus on 2008-03-07
Reboot without the CD and see if it boots from your harddrive this time.

---

### Post by robertchahine on 2008-03-07
now, when it reboot sUbuntu would run the start up logo but only to get STuck at 3/4 of the way then it tells me starting hardware abstration layer hald after a lot of processese that are done and written "ok".
and the permission of /etc/pppip-down.d/0dns-down is denied.

---

### Post by robertchahine on 2008-03-07
but after a while, i get to the login screen

---

### Post by robertchahine on 2008-03-07
but i enter my username and password, i recieve an msg that its font it's to small that nobody can read it. but there's the word GNOME.after clicking ok on this msg i returns to the login screen.

---

### Post by taurus on 2008-03-07
Press <Ctrl><Alt>F2 and log in with your username and password.  Then, post the output of this command here.

```
df -h
```
Just want to make sure your didn't fill up your disk space.

Again, not sure why you decided to change permissions of /etc because things will not run smoothly as before.

---

### Post by robertchahine on 2008-03-07
when i press ctrl+alt+F2 and put my username and password, it tells
...
bash: /etc/profile: permission denied
bash: /etc/bash_competion : permission denied
I hace no name!@robert-desktop:~$

---

### Post by taurus on 2008-03-07
I hate to say this but if you don't have important files on your machine (otherwise, back them up), I would go for reinstall so you would have a clean system.  We can fix one problem and then the next will pop up and it's probably wasting more time then reinstalling the whole thing over again.

But if you still want to fix it, then we can proceed.

---

### Post by robertchahine on 2008-03-07
i have some pictures on the /home folder. can i put them on the usb or something like that before reinstalling ubuntu?

---

### Post by taurus on 2008-03-07
If you want to back up your pictures in ~/Pictures, you can do that from the LiveCD.  I assuming you have a USB thumbdrive handy because you will need to copy those pics from the harddrive over to your thumbdrive.

Boot your machine with the LiveCD and run

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
du -h /mnt/ubuntu/home/*username*/Pictures
```
Replace the *username* with your actual login name.  The last command will tell you how much space you need to store those pictures.

---

### Post by robertchahine on 2008-03-07
ok, i'm going to try that now

---

### Post by robertchahine on 2008-03-07
i did that but the terminal tells me :

du: cannot access 'mnt/ubuntu/home/robert/pictures':no such file or directory

---

### Post by taurus on 2008-03-07
Linux/Unix is case SenSiTive so pictures is not the same as Pictures.

```
du -h /mnt/ubuntu/home/robert/Pictures
```
Otherwise, post the output of this command then.

```
ls -la /mnt/ubuntu/home/robert
```

---

### Post by robertchahine on 2008-03-07
ok. when i wrote "du -h /mnt/ubuntu/home/robert/Pictures",
it tells the subfolders and for everything permission is denied :(

---

### Post by robertchahine on 2008-03-07
by the way, when i enter the filesystem, then /mnt/ubuntu/home/robert i can see all of my folders.if we change the permission ccan we copy the folder then reinsall ubuntu?

---

### Post by taurus on 2008-03-07
You can try something like

```
sudo chown -R robert:robert /mnt/ubuntu/home/robert
sudo chmod -R 755 /mnt/ubuntu/home/robert
du -h /mnt/ubuntu/home/robert/Pictures
```
The first line will change the ownership of your $HOME on the harddrive and the second command will change the permissions.

---

### Post by robertchahine on 2008-03-07
it works. now i can copy the folder "Pictures" manually (copy paste)

---

### Post by robertchahine on 2008-03-07
thank you so so so much taurus..
i think you're king of ubuntu.

---

### Post by robertchahine on 2008-03-07
i think that there's  little bit of quetions

---

### Post by robertchahine on 2008-03-07
now if i want to reinstall ubuntu, do i have to format the computer, or what to do?

---

### Post by taurus on 2008-03-07
I would reformat it to make sure you have a clean and healthy machine.  And be real careful with changing permissions of anything outside your $HOME directory.

---

