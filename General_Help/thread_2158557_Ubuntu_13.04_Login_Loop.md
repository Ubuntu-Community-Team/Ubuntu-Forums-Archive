---
title: "Ubuntu 13.04 Login Loop"
date: 2013-06-29
forum: General Help
---

### Post by FotisGR on 2013-06-29
I have a problem with Ubuntu 13.04.


I cannot log in to my account. I put the right password but there is an endless loop. (if i put wrong pass, it says "Invalid password..."). Also, it doesnt show the small drop down menu with choices "Gnome fallback, Default, etc.."

If i login as guest, the desktop is clear, no bars, no menus, anything. Just right clicks works only.

I have already try this solution ```
chown username:username .Xauthority
``` but there is no "Xauthority" at ubuntu 13.04. (?)

Is the problem about lightdm? Also, i tried ```
sudo dpkg-reconfigure lightdm
``` but it soesn't work.

I use the recovery mode (root command shell or something like this) in order to try the above commands.


Has anyone a solution?


Thank you.

edit: Now, guest session works fine.

---

### Post by deadflowr on 2013-06-29
.Xauthority is a user file, not a system file.
Try running this
```
mv /home/yourusername/.Xauthority /home/yourusername/.Xauthority.bak
```
then try a reboot.

And replace the yourusername with your actual username.

---

### Post by FotisGR on 2013-06-29
> **deadflowr said:**
> .Xauthority is a user file, not a system file.
Try running this
```
mv /home/yourusername/.Xauthority /home/yourusername/.Xauthority.bak
```
then try a reboot.

And replace the yourusername with your actual username.

It doesn't work.

Also about [this solution]("http://askubuntu.com/questions/223501/ubuntu-12-10-gets-stuck-in-a-login-loop/223634#223634")

[IMG]http://img713.imageshack.us/img713/319/3ror.jpg[/IMG]

---

### Post by deadflowr on 2013-06-29
It's because your running as root.
The file is in the users home directory.
Root has it's own home directory.

You need to change into the users home folder to change the file.
try
```
cd /home/yourusername
```
Again, change yourusername to your actual user name
If unsure about what your username is, 
```
cd /home
```
and then run ls command, which will list the folders in the home directory. Those folders are the users folder, and as such will be named for the owners/users.
Then run the ls -lah command and see that it lists a different output then the one you tried before.

---

### Post by FotisGR on 2013-06-29
Yes, you have right.

I found a .bak file but i cannot use mv command because there is no an original file!

[IMG]http://imageshack.us/a/img837/6862/q4c7.jpg[/IMG]

[IMG]http://img195.imageshack.us/img195/9537/aglm.jpg[/IMG]

What do you sugget? rename? make a new xAuthority file? etc..

Thank you.

---

### Post by deadflowr on 2013-06-29
You only changed into the home directory, now change into the users home folder.
```
cd /home/username
```
then run ls -lah
and the Xauthority file should be listed.

---

### Post by FotisGR on 2013-06-29
There isn't .Xauthority file. Only some .xAuthorityXXXXX files. (most recent - 27 June)

[IMG]http://img833.imageshack.us/img833/8885/mi5a.jpg[/IMG]

:sad:

---

### Post by deadflowr on 2013-06-29
Since I'm not totally keen on what your actual problem is, I only noticed you're logging in through the recovery mode, hence all the root/user issues.
You can try this method.
Reboot and boot as normal, to the login screen.
You can try and login, or press the keyboard keys ctrl+alt+F1, or F2, or F3, or F4, or F5, or F6.
ctrl+alt+F1-6 will switch you to a terminal prompt/window.
Enter your name and password, then try removing the .Xauthoirty file.
Simply
```
rm ~/.Xauthority
```
Then run
```
sudo service lightdm restart
```
If the loop still happens, you could also try and remove the .ICEauthority file
using the same method as before.
Then try to restart lightdm.

Again, not totally keen on what the real problem is.
If after restarting lightdm, and it still loops try a reboot.
Both files should(are suppose to) regenerate, so deleting them should not be a major problem.

Since it's in your folders(which you own), there is no need to run the rm(remove) with sudo.

---

### Post by FotisGR on 2013-06-30
I tried everything. (delete xauthority and ICEauthority files, restart lightm, reconfigure lightdm..). Nothing works.

May I will make a new fresh install..

---

