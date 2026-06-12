---
title: "Locked out of the house"
date: 2008-06-06
forum: General Help
---

### Post by gopher38 on 2008-06-06
Hi.  Problem with users and passwords.

Background:  I have an old notebook, that was just suffering under XP (more than 10 minute to boot).  Decided to try Ubuntu on dual boot.  Extremely pleased, because my boot time went down to under 2 minutes, and everything (such as moving or renaming files) moves much faster.  Using Gutsy, since the Heron LiveCD wouldn’t work for me.  

Problem:  I got the PC set up like I wanted for me, with direct login for my account (wireless password stored in WICD), but I wanted to create an extra account for my parents, so I created an account “parents” with password “parents”.  However, when I tried to change to that user account (by clicking the account name in upper right corner), I would get a message at login saying “authorization failed” (I’m on a French machine, so the actual message is “l’autorisation a echoue”). I couldn’t select any options either; the computer was just blocked on “authorization failed” (if I clicked OK, it would just come straight back up and eventually I’d have to turn the power off).  I thought that the problem might be because I had direct login on my main account, so I removed all direct login, hoping that ubuntu would prompt me for the account information at login.  Unfortunately, what happens is that I get the “authorization failed” message right at the start and can’t select any account: neither mine nor my parents.   So in effect I’m totally blocked out.

I still have the LiveCD, so I imagine that I can boot with that and edit the system files on my notebook, but I don’t know which files or variable I have to change.  What I want to do is either have the login screen prompt me for an account or login directly to my principal account, like I had it before.  Any help would be greatly appreciated.

P.S.: the reason I mention WICD above is that the wireless password is stored there and I suppose it could be THAT authorization that is failing, but I don’t think so, since I’m still at the login screen, but I wanted to be complete in my problem description.  Thanks.

---

### Post by danwood76 on 2008-06-06
Can you log out and then login to your parents user?
It may just be user switching giving you this issue.

---

### Post by Trail on 2008-06-06
Maybe you can try booting into recovery mode (at grub stage)? If you do, you can change a user's password with the 'passwd' command.

If it can't work, there's a grub hack to load the kernel as root without asking you for a password, but try more normal methods first.

---

### Post by kpkeerthi on 2008-06-06
Boot into **recovery mode** from GRUB. At the command prompt, enter
```
password <login-id>
```
to change the password.

To delete a password
```
password -d <login-id>
```

---

### Post by kpkeerthi on 2008-06-06
And if your GUI locks up, press Ctrl + Alt + Backspace to retart X. It should take you back to Login screen.

---

### Post by rraj.be on 2008-06-06
> **Trail said:**
> 
If it can't work, there's a grub hack to load the kernel as root without asking you for a password.

Isn't this a security risk.

Is it legal.

Could you give some more info.

---

### Post by danwood76 on 2008-06-06
You say grub hack.
Its just telling the kernel to enter single user mode as recovery mode does.

Of course its legal though, and letting anyone use your computer is a security risk, heck even turning it on is.

---

### Post by kpkeerthi on 2008-06-06
> **rraj.be said:**
> Isn't this a security risk.

Is it legal.

Could you give some more info.

The grub hack is to enable single user mode. You may want to read about [run levels]("http://www.debian-administration.org/articles/212") in linux.

If you see recovery mode in your Ubuntu's GRUB, then single user mode is already enabled.

And yes, it is a security risk (if your laptop is stolen). You may password-protect your GRUB if you are paranoid. See [http://www.debiantutorials.org/content/view/40/227/](http://www.debiantutorials.org/content/view/40/227/)

A nifty tool that may help you is **startup manager**. Install it using synaptic.

---

### Post by gopher38 on 2008-06-06
Hello and thanks for the responses (had to run out and do my grocery shopping).  I'm going to try your suggestions now, but I don't think changing the password will help, since I already know what the passwords are.  Perhaps I didn't explain it well, but the login screen never allows me to enter a password (or a user account for that matter).  It comes up directly with the "authorization failed" message, and if I click "OK", it pops right back up with "authorization failed" and so on and so forth.  But I'll feel better if I can at least enter the recovery mode, then I'll try deleting all the passwords (is a password required for an account?  I don't even know that).  Then I'll try the CNTL-ALT-BACK thing, which sounds interesting. And I'll report back, hopefully in Ubuntu - if not, in XP  :(

---

### Post by gopher38 on 2008-06-06
Well, I learned some things. The recovery mode works and puts me into a command line interface.  I deleted both of the passwords, but I still have the same problem.  I tried the CNTL-ALT-BCK trick, and the screen go black, display some text, and then try to start up again, and I receive the same error message.  I did learn something from it though.  I said before that I didn't think that this was related to WICD, but now I'm not so sure.  When I do Cntl-Alt-Bck, between the screens, I could see the message, starting WICD daemon, so apparently that application is already going, so maybe the error message is coming from it and not from the login screen.  Unfortunately, I'm a newbie to Linux, so I don't know how to stop it from loading.  In my low-tech way, I tried moving /opt/wicd to /opt/bckwicd but that didn't fix it.  

Seems I've heard something about rc.local or init.d.  Does anyone know where I'd go to stop the WICD from loading?

Thanks.

---

### Post by gopher38 on 2008-06-06
Good news and bad news.  I still don't know why it locked me out, but I used the recovery mode login (thanks for telling me about that) and the tar backup technique and was able to restore to a recent state, so I didn't have to restart from zero.  My recommendation to any new users like myself, do a search on backups using tar and do that right away once you get to a semi stable state on your computer.  Works very well; much faster than Acronis Image.  I'll now at least be able to experiment a bit with the login problem knowing that I can get back to my starting point.

---

### Post by _DD_ on 2008-06-06
Glad you've got it fixed.

If you're still having some problems then could you post the contents of the following files (open them by running the commands below)...

```
sudo gedit /etc/hosts
```
```
sudo gedit /etc/hostname
```
```
sudo gedit /etc/pam.d/common-auth
```

(I don't know why I said to use sudo - make sure you don't make any accidental changes!)

And does it work if you actually log out, rather than trying to switch users?

---

### Post by aysiu on 2008-06-06
I don't know what the fix is, but these two links seem to indicate it has something to do with pam and autologins:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/203755](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/203755)
[http://ubuntuforums.org/showthread.php?t=562238](http://ubuntuforums.org/showthread.php?t=562238)

Incidentally, both were from Gutsy.

---

### Post by gopher38 on 2008-06-07
Thanks for those links.  They seemed to indicate that it had something to do with PAM keyring.  I had actually made some changes to that when I first installed Ubuntu, when I was trying to eliminate the password request every time for wireless login.  I never did get it to work, so I switched to WICD, but apparently the changes I made caused this problem.  I edited out this line:

@include common-pamkeyring

In the file:

/etc/pam.d/gdm

And now the problem is gone.  Thanks.

---

### Post by danwood76 on 2008-06-07
The way to stop PAM asking for a keyring password is to delete the keyring file and just set your wifi password with an empty keyring password.
It asks if your sure you wasnt to store it insecurely, just click yes ;)

---

