---
title: "Problem with logging in"
date: 2014-11-27
forum: General Help
---

### Post by brianbuck3 on 2014-11-27
I have a Dell D400 laptop which I use as a spare and which I have recently had converted from Windows XP to Ubuntu 14.4

The conversion seems to have worked ok but the laptop will now only allow me to log in as a guest. If I try to log in using my own name, I am asked for a password even though I have never installed a password, and none of the passwords I use or have previously used, are accepted. I have tried logging in as a guest and then attempting to create a new user but the laptop won't allow me to do this either and nor will it allow me to log in to safe mode.

Can anyone help me by suggesting a way to resolve this?

Many thanks
Brian Buck

---

### Post by flaymond on 2014-11-27
try type this


Username - Ubuntu
Password -            (blank)



This is the most safeway to log in if you got locked out (but not always worked).

---

### Post by brianbuck3 on 2014-11-27
Thank you very much for the suggestion but I'm afraid it doesn't work. The screen opens with my user name already displayed but won't accept any kind of password and won't log in without one except as a guest.

Thank's for trying though.

---

### Post by flaymond on 2014-11-27
So, you mean..you can access terminal using guest account (Ohh, I think you locked out and cannot access your Ubuntu and dont have any accounts)



You can try Grub method. Check this site -

[http://itsfoss.com/how-to-hack-ubuntu-password/](http://itsfoss.com/how-to-hack-ubuntu-password/)


Update your post if its worked, if not..we will figure out together. :)

---

### Post by Elfy on 2014-11-27
>  If I try to log in using my own name, I am asked for a password even though I have never installed a password, 

Yes you did.

When you installed it asked you for 

> username
password
confirm password

use password to login
whatever you used then - that IS your password.

---

### Post by Elfy on 2014-11-27
> **InterProg said:**
> try type this


Username - Ubuntu
Password -            (blank)



This is the most safeway to log in if you got locked out (but not always worked).

How is that ever going to get someone in to their account?

---

### Post by flaymond on 2014-11-27
I think 'he' locked in live session. That's why I prefer that method. or arrow up for null.

---

### Post by nknwn on 2014-11-27
There's this: [http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/](http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/)
but it is not the only method out there.

Pretty sure I've used this method in the past:
[http://www.slashgeek.net/2012/06/12/reset-linux-root-password-in-under-5-minutes/](http://www.slashgeek.net/2012/06/12/reset-linux-root-password-in-under-5-minutes/)

---

### Post by flaymond on 2014-11-27
There's a lot of method you can try to resetting root password. It's your choice and suitable with steps.*** But, every method had the risk that you need to take***.

---

### Post by nknwn on 2014-11-27
Recent: [http://ubuntuforums.org/showthread.php?t=2226219&p=13033419#post13033419](http://ubuntuforums.org/showthread.php?t=2226219&p=13033419#post13033419)

Note: "In the newer versions of Ubuntu, the filesystem state has been defaulted to **read-only**. This means that ....

---

### Post by AkeB on 2014-11-30
I have run into a similar login problem like brianbuck3. I have a PC with dual boot Windows 7 Home Premium & Ubuntu 14.04 LTS. I set up up this PC earlier on this autumn and have logged in to Ubuntu many times before. However, for various reasons I have mainly used Windows for the last couple of weeks and now when trying to boot Ubuntu again and tried to login with the password I **thought** I had set it didn't work, I just get the "wrong password message". After having tried a number of possible other passwords without success I eventually searched the net for help. After some search I run into a similar guide like InterProg linked above ([http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)). I followed those instructions, but noted in the process that when issuing

ls /home


I **did not **get a list of available user accounts. Despite this the "passwd" command accepted resetting the password for the account "ake" (my root login looked like this: "root@ake-alina-aspire").

However after exiting the root account and resuming the boot process when getting to the login prompt and tried to use the new password to login I simply get nowhere. No error message, the login prompt just pops up again and again.

Just to make sure I hadn't misunderstood any of the commands in resetting the password I went through the same process again with the same result. This time I also tried to change the password for the account "ake-alina-aspire" but then I got the error message that no such account exists. After exiting and resuming the boot process I am still stuck with the login prompt.

What can have happened? Does the fact that the command "ls /home" doesn't return any information mean that there does no longer exist any **user** account on my Ubuntu installation and the account "ake" actually (and inadvertedly) has turned into my **root** account?

Any help to sort out this mess would be appreciated. It would of course be possible to solve the problem by simply reinstalling Ubuntu, but I would prefer to solve the problem by other means if that can be done.

Just in case it is of any interest in the situation, it is still possible to login to a **guest** account, so the login process as such has apparently not crashed. I should perhaps also add that I use Mate 1.8 on top of Ubuntu as I prefer a Gnome-lookalike to Unity (my first Ubuntu version in use was 9.04 - though not on this PC which I bought earlier this autumn).

---

### Post by AkeB on 2014-11-30
After having studied some postings on Ask Ubuntu and the Ubuntu I've got some answers but am still confused. The reason for "ls /home" not returning any account names is apparently that I've used a separate partition for my /home folder and thus it wasn't mounted. "mount --all" took care of that problem, so now I know that my user account wasn't deleted after all. Then I changed the password for this account and to make sure to be able login I also created a new account and gave that sudo privileges 

(as described here How can I add a new user as sudoer using the command line?

[http://askubuntu.com/questions/7477/how-can-i-add-a-new-user-as-sudoer-using-the-command-line](http://askubuntu.com/questions/7477/how-can-i-add-a-new-user-as-sudoer-using-the-command-line)

&#8220;ls&#8221; is not listing any user's under /home directory in Ubuntu

[http://askubuntu.com/questions/412437/ls-is-not-listing-any-users-under-home-directory-in-ubuntu](http://askubuntu.com/questions/412437/ls-is-not-listing-any-users-under-home-directory-in-ubuntu))

The net result is somewhat confusing. I'm **still** not able to login in to my original account "ake" even after changing the password once more (tries to login only results in being prompted for password) but the new account "arawn" works fine! Now that I know the old account was there after all this makes the matter more confusing. Can my account "ake" have been corrupted in some way that it isn't possible to change the password despite the "passwd" command seemingly doing what it should?

There is also another matter that I've being thinking of. In the installation process I was asked at some stage if I wanted to do an encryption. As I read somewhere on the net that this was advisable to do, I answered yes to that question. Does that mean that passwords would be encrypted as well and then not possible to change? If so that would explain why I can't change the password to the "ake" account.

---

