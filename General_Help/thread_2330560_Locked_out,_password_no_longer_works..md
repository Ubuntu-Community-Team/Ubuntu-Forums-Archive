---
title: "Locked out, password no longer works."
date: 2016-07-12
forum: General Help
---

### Post by paul1945 on 2016-07-12
Hi, I have Ubuntu 14.04 and I made some symlinks for wine, which it kept deleting, thus stopping me being able to install programs.
So with my limited knowhow, I tried to change the attibutes for the symlinks, to stop them being deleted, which came up with an error.
One of the symlinks made my directory /home/paul/ into drive d:
After this the symlinks could no longer be accessed so I deleted them.
Now I can no longer get into Ubuntu, it comes up and asks me for a password, but refuses my password as incorrect, even though I have used this thousands of times under sudo.
Is the system screwed and requires a new install, or is this fixable? 
Thanks, Paul.

---

### Post by NM5TF on 2016-07-12
I have used this password recovery a couple of times now....:lolflag:

try this:   [https://linuxconfig.org/ubuntu-14-04-lost-password-recovery](https://linuxconfig.org/ubuntu-14-04-lost-password-recovery)

tommy

---

### Post by paul1945 on 2016-07-13
Hi, have had a look at the page, but it fails to tell one how to boot into the GRUB loader.
Have tried f4, f8, f10 on boot, but no luck.
So I am still nowhere.

---

### Post by deadflowr on 2016-07-13
> **paul1945 said:**
> Hi, have had a look at the page, but it fails to tell one how to boot into the GRUB loader.
Have tried f4, f8, f10 on boot, but no luck.
So I am still nowhere.

To access the grub menu you need to press the shift key when the initial bios screen disappears.
Alternatively, if using a newer machine, you might have UEFI set instead of Legacy BIOS, in which case you need to press the ESC key instead of the shift key.
(Or at least with UEFI, that is my understanding)

---

### Post by NM5TF on 2016-07-13
> **paul1945 said:**
> Hi, have had a look at the page, but it fails to tell one how to boot into the GRUB loader.
Have tried f4, f8, f10 on boot, but no luck.
So I am still nowhere.

if your machine is a Dell, use F12 at boot...you might have to press the F12 key
multiple times before you get the boot menu.....then proceed with the page
directions...they work....

---

### Post by paul1945 on 2016-07-13
Hi, thanks for that, both the shift key and the escape key work.
I have reset my password and managed to get into the Root, but when I reboot Ubuntu it again asks me for a password and does not recognise the one I have just done.
I still cannot get to the desktop.
So I presume it did not associate my username with the administrator or has not associated my username with my password.
How do I deal with that?
Thanks, Paul.

---

### Post by deadflowr on 2016-07-13
When you enter the password and hitting enter key, is it simply resetting the login page?
Or does it tell you the password is incorrect?

---

### Post by paul1945 on 2016-07-13
The screen disappears and goes black, then the login page re-appears and asks me to log in again.
So I presume it is just resetting the login screen. Paul.

---

### Post by deadflowr on 2016-07-13
Okay.
Try this:
when you get the login page press ctl+ alt + F1 (or F2-F6)
It'll change from the greeter to a terminal console shell.
enter your login name and your user's password.
When logged in here take a quick look at a single file with this
```
ls -la ~/.Xauthority 
```
the output shouold look like
```
-rw------- 1 your-username your-username  58 Jul 12 15:11 .Xauthority
```
if the username is something else, like root, then that is what the problem is and you will need to change it to your user's name.
To do so run
```
sudo chown your-username:your-username ~/.Xauthority
```
changing your-username with your user's name.
Hopefully that will fix it, if that is the problem.

Then all you need to do is restart the greeter.
To do that run:
```
sudo restart lightdm
```
alternatively, you can try
```
sudo service lightdm restart
```
but for 14.04 the first should work.

Hope it helps

---

### Post by paul1945 on 2016-07-13
Did not post this the first time, so trying again.
When I press ctrl-alt-F1, I get this:
No directory, logging in with HOME=/
The command prompt appears with paul$
when I type:
ls -la ~/.Xauthority
I get:
ls: cannot access //.Xauthority: no such file or directory
I also decided to navigate to my directory /home/paul/ and it exists and appears to be intact, although I cannot be sure the files and subdirectories are still all there.
When I try to cd to this directory it comes up with permission denied.

Just as an additional bit of information, I can get into the directory as a Root uses, but not as paul.
So this I guess explains why Ubuntu won't start.
I have tried:
sudo chown -R paul /home/paul
and
sudo chmod -R ugo+rw /home/paul
but without results.
It still states "permission denied"
If anyone knows whether this is fixable, and if so how, I would be grateful.

---

### Post by Impavidus on 2016-07-13
> **paul1945 said:**
> 
One of the symlinks made my directory /home/paul/ into drive d:
After this the symlinks could no longer be accessed so I deleted them.

What do you mean by that? Drive D is Windows-speak. Your home directory cannot be on a Windows partition, or you will be unable to login to the GUI (which you are).

Use ctrl-alt-F1 to get to the console and login. For some more diagnostics, use```
ls -l /home
mount | grep home
cat /etc/passwd | grep paul
```

---

### Post by paul1945 on 2016-07-14
Hi, thanks for that.
I managed to get into Ubuntu on boot-up with GRUB and found that I could not get into my /home/paul directory except from the root.
I guessed that Ubuntu cannot boot up for a user if the user directory is locked.
So I created a new "temp" directory under /home and copied all the files from the /home/paul directory into /home/temp.
Deleted the /home/paul directory while I had root privileges and renamed /home/temp to /home/paul.
Rebooted and lo and behold everything worked fine.
So my problem is fixed.
I have no doubt that I could have done something much simpler had I known what to do.
But I am hardly a Linux expert, so had to work with what I knew.
I now realise that making a symlink to the user directory was a bad idea. 
But I am still curious as to what happened, so I can avoid this or fix it with less headaches if this or something similar arises.
Appreciated all your help. Paul.

---

### Post by kurt18947 on 2016-07-15
Is this of any help? I've run into similar problems and reset my sudo password from a live session.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by paul1945 on 2016-07-16
Hello Kurt, The problems was not a password issue, but as Impavidus says above:
[COLOR=#000000]> What do you mean by that? Drive D is Windows-speak. Your home directory cannot be on a Windows partition, or you will be unable to login to the GUI (which you are).[/COLOR]
And that is exactly, what I in my inexpertise - and as a result of the far too vague advice by someone on the Wine Forum - had done.
I now also realise that I did not fix this from the Root, but as a Super User, as I had to log by means of "su" to deal with the matter. 
What I am now interested in is whether I could have "unlinked" this problem from the command line, rather than having to go through the convoluted procedure I used. 
Needless to say I will not do this again; but I would like to build my - obviously far too limited - knowledge.  Paul.

---

