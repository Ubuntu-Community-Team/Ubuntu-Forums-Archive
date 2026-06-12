---
title: "fix file permissions - git issue"
date: 2016-04-15
forum: General Help
---

### Post by evm78 on 2016-04-15
I created this problem myself, and i am aware of that :)

i had a problem with a driver update where i couldn't log in anymore. along the way i tried some of the recommendations here 
[http://askubuntu.com/questions/454576/cant-login-to-ubuntu-14-04-after-upgrade](http://askubuntu.com/questions/454576/cant-login-to-ubuntu-14-04-after-upgrade) and this screwed up some file properties

specifically i i did the 
sudo chmod -R ug+rwx /home/[username]
bit and the 
chown -R [user-name]:[user-name] /home/[user-name]
those actions didn't fix my problem at the time, but the effects are still here.

I made a few changes in a repository and 'git status' only showed the correct limited changes. I did add --all and commit without looking too closely, and EVERY SINGLE FILE in the repo got updated. Now Github won't preview any images. It seems to be because they are set to executable. 

I guess it's because of the chmod and chown i had done and forgotten about. 

Is there an ORGANIZED way to set all the file permissions back to something sane? i.e. folders behave normally, images behave normally? I can do a lot manually, but now i'm concerned that the changes could cause other problems i don't even know about.

Thanks in advance :)

---

### Post by bab1 on 2016-04-15
> **evm78 said:**
> I created this problem myself, and i am aware of that :)

i had a problem with a driver update where i couldn't log in anymore. along the way i tried some of the recommendations here 
[http://askubuntu.com/questions/454576/cant-login-to-ubuntu-14-04-after-upgrade](http://askubuntu.com/questions/454576/cant-login-to-ubuntu-14-04-after-upgrade) and this screwed up some file properties

specifically i i did the 
sudo chmod -R ug+rwx /home/[username]
bit and the 
chown -R [user-name]:[user-name] /home/[user-name]
those actions didn't fix my problem at the time, but the effects are still here.

I made a few changes in a repository and 'git status' only showed the correct limited changes. I did add --all and commit without looking too closely, and EVERY SINGLE FILE in the repo got updated. Now Github won't preview any images. It seems to be because they are set to executable. 

I guess it's because of the chmod and chown i had done and forgotten about. 

Is there an ORGANIZED way to set all the file permissions back to something sane? i.e. folders behave normally, images behave normally? I can do a lot manually, but now i'm concerned that the changes could cause other problems i don't even know about.

Thanks in advance :)
You should never just blindly follow instructions found on the Internet.  You should either test the command with test data or ask for advice.  The problem with the command is that a chmod x is not the same as chmod X.  The x makes all files and directories executable for the users (u,g,o or a).  Using an X leaves all files marked executable but does not add executable to those that are not already that way.  It should have been chmod ug=rwX.  But the damage is done and it is possible to fix it.

It's easier to use the command ***find*** for this action.  To set all the files at 664 (ug=rw,o=r) while leaving the directories at 775 (ug=rwx,o=rx) you can use this command```
find /home/[user-name] -type f | xargs -I {} chmod  664 "{}"
```...the command means this:  find files only starting at /home/[user-name] recursively and set the permissions to 664 (as they were by default).

If you want to test this make a directory in your home directory, add files and a subdirectory, then use the command (changing the start point (/home/[user-name]/<test-dir> and the chmod numbers (e.g 644 vs 664 or 660).  You will see the changes in the file permission but not the subdirectory permissions.

***Ask questions here first*** if don't understand.  I can give you specific test instructions if you need them.

---

### Post by evm78 on 2016-04-16
cool thanks. i found something very similar earlier and it worked. You're right about testing....but when a graphic driver stops me from logging in and i'm stuck in ctrl-alt-f1 console...i kinda lose perspective :)

---

### Post by bab1 on 2016-04-16
> **evm78 said:**
> cool thanks. i found something very similar earlier and it worked. You're right about testing....but when a graphic driver stops me from logging in and i'm stuck in ctrl-alt-f1 console...i kinda lose perspective :)
It helps to understand how to use BASH in a terminal.

---

