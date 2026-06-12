---
title: "Password not working after resetting it"
date: 2014-05-16
forum: General Help
---

### Post by Safeeq on 2014-05-16
I resetted the password for my ubuntu 1204 LTS installed on Windows 7. I'd forget the password and had to reset it by following the below steps.

boot ubuntu on recovery mode
> select drop to root shell prompt
mount -o remount,rw /
chmod 640 /etc/shadow
sudo passwd

The password was updated successfully and when I reboot the system to login on normal mode. It takes password without throwing an exception but switchs back to the same login page again.


Please let me know how to fix this.

---

### Post by Impavidus on 2014-05-16
The correct procedure to reset the password is described here: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
In other words, no need for the chmod (although it shouldn't harm, as you reset the permissions of the shadow file to their default value), no need for the sudo in the passwd command as you are root already, but you do need the user name after the passwd command, or it will change the password of root, which is not what you want. Or at least shouldn't be what you want.

You issue now is a different one, as your password is accepted, but your graphical session crashes as soon as it starts. The usual suspect is a file named .Xauthority, sitting in your home directory. Try switching to the console with ctrl+alt+F2 and logging in there. Run```
ls -l .Xauthority
```If it doesn't show you as the owner of the file, fix it with```
sudo chown yourusername:yourusername .Xauthority
```You can switch back to the GUI with ctrl+alt+F7. You can also do this from the recovery console, but in that case remember to remount the file system read-write or mount the /home partition if you have one and drop the sudo from the last command. Try again logging in. If this doesn't work we'll have to dig deeper.

This problem typically appears when you run GUI apps with sudo.

---

### Post by deadflowr on 2014-05-16
When you ran the sudo passwd command, was it like that, or did you put your username after it?
If you ran it as is, "sudo passwd", then you just changed the root password.

When you inputted the new password, was it different from the old password, or did you use the same one?
Me = confused. 

+1 to checking .Xauthority.
That tends to be the usual suspect with the login-loop problem.

---

### Post by Safeeq on 2014-05-16
Thanks for your replies - I tried the both commands from terminal and it throws back an exception saying that there is no such file or directory.   Also, I changed both the root and user password ( sudo passwd and passwd aditi ), by giving a new password.

---

### Post by Safeeq on 2014-05-16
Thanks for your replies - I tried the both commands from terminal and it throws back an exception saying that there is no such file or directory.   ls -l .Xauthority  udo chown yourusername:yourusername .Xauthority  Also, I changed both the root and user password ( sudo passwd and passwd aditi ), by giving a new password.

---

### Post by deadflowr on 2014-05-16
Recovery mode puts you in the root directory, aka root's home folder.
You need to move into your home folder.
```
cd /home/username
```
then run the ls -l .Xauthority command.
Change username to your username.

---

### Post by Safeeq on 2014-05-16
I logged onto recovery mode and used the cd /home/safeeq command to move to the home directory. Run the command ls -l .Xauthority - the results are same, its says no such file or directory.

I tried with normal mode and pressed ctrl+atl+f2 , logged as normal use (safeeq) and run the ls -l .Xauthority - got the same error. not sure if I am missing anything.

---

### Post by Impavidus on 2014-05-16
So it seems that .Xauthority doesn't exist. That is peculiar, but shouldn't cause a problem, as it should be recreated when you start a graphical session. We'll have to dig deeper.

What does **ls -dl /home/safeeq** give you? To check whether you have permission to recreate that file. And can you login as guest?

---

### Post by Safeeq on 2014-05-16
ls -dl /home/safeeq gives the output like

dr-X------ 3 safeeq safeeq 4096 Jun 20 2013 /home/safeeq

And, Yes I'd be able to login as guest.

---

### Post by Impavidus on 2014-05-17
That's wrong. You don't have write permission in your own home directory. Try running```
chmod u+w /home/safeeq
```

---

### Post by Safeeq on 2014-05-20
chmod u+w /home/safeeq command prints the below

chmod: changing permissions of '/home/safeeq': Read-only file system

And, running the ls -dl /home/safeeq prints the same message as earlier.

---

### Post by Impavidus on 2014-05-20
If you do this from recovery mode you have to remount the file system read-write first:```
mount -o rw,remount /
chmod u+w /home/safeeq
```But the chmod command should work directly from the console where you get with ctrl+alt+f2.

---

