---
title: "Changing name of computer, username, home folder name, permissions..."
date: 2008-04-23
forum: General Help
---

### Post by laeg_ on 2008-04-23
I have tried to do some of this before by changing my username in system > admin > users and groups. I then manually changed the name of /home/olduser to /home/newuser and when I tried to log in later on I go lots of error messages and had to reinstall.

I would like to change the name of the computer and my username so that everything looks and behaves just like I am olduser and I have olduser's files and settings etc.

I am only using linux a few days so please give it to me in layman's terms :)

---

### Post by ryanhaigh on 2008-04-23
The command ```
hostname
``` can be used to change the computers name, for more information on how to use it go to System>Help and support and search for man hostname.

As far as changing your username I don't think you can REALLY change it but you should be able to create a new user in System>Admin>Users and Groups (make sure you give the new user admin priviliges) you will then need to rename(mv means move but its the same thing) the home directory of that user
```
sudo mv /home/olduser /home/newuser
``` and then change the permissions of all files so that newuser owns them [sudo chown newuser:newuser -R /home/newuser]. Just to be safe you could use copy instead of move using cp -R instead of mv. Note that after you create the new user you should logout and use the terminal (ctrl+alt+f1) to do the rest. If you are not comfortable doing this there may be a way to do it via the gui but i am not sure it will work which is why I have given this method.

---

### Post by laeg_ on 2008-04-23
x

---

### Post by laeg_ on 2008-04-23
I tried to change the hostname from each of my user accounts with sudo hostname, and when that failed I also tried it as root but the change would never take immediate affect and be visible in the next command prompt. I have to relog into the console for it to display the new hostname, and even then it displayes the old hostname at the xwindows login screen and when I reboot it displays the old hostname in console and xwindows.

In regard to copying and taking ownership of the files I followed your instructions and I almost have what I'm looking for. Instead of cp -R /home/olduser /home/newuser making an exact copy of /olduser and replacing /newuser with it, it has in fact created a new dir /home/newuser/olduser.

Can I remedy this in the GUI by temporarily renaming and copying the new dir /home/newuser/olduser into /home, then deleting /home/newuser and changing the name of the copied dir back to /home/newuser?

---

### Post by ryanhaigh on 2008-04-23
That should work. The reason you had this problem is because the newuser directory already existed in /home.

Don't forget to change the permissions afterwards.

---

### Post by laeg_ on 2008-05-02
Sorry for delay in replying.

It seemed to work but then when I was opening the pictures dir from my places menu it was taking me to the wrong users dir. It seemed very messy and left me wondering what else wouldn't be perfect so I just did a clean install. Thanks for your help :)

---

