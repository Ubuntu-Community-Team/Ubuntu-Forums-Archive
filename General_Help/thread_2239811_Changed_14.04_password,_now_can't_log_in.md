---
title: "Changed 14.04 password, now can't log in"
date: 2014-08-15
forum: General Help
---

### Post by RangerK on 2014-08-15
I really hoping this is a silly beginner error.  I have a new Ubuntu laptop running 14.04.  After getting it from the store, I would have to log in.  There were two option -- Log in as me, or as Guest.

I changed the password for me using "passwd".  Now I get stuck on the login screen.  If I type the old password, it get the text saying 'invalid password'.  When I type the new one, the screen sort of resets.  It goes dark for moment, then I see the default Ubuntu 14.04 background, then I see the background graphic I added, but I get the same stupid log in screen with the options me, and guest.

Can anyone help me figure out what happened and how to fix it?

---

### Post by mike225 on 2014-08-16
You can try Alt F4 to get to login but pretty sure they blocked the backdoor. new install may be needed; [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by lisati on 2014-08-16
I doubt that a full re-install is necessary.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) provides a method to reset passwords. Having said that, it sounds like something else got messed up somewhere.

---

### Post by deadflowr on 2014-08-16
> **lisati said:**
> I doubt that a full re-install is necessary.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) provides a method to reset passwords. Having said that, **it sounds like something else got messed up somewhere**.

Sounds like a login loop.
Possibly something off with the .Xauthority file.
To the op, perhaps let's take a look at said file
```
ls -la .Xauthority
```

If you press ctrl+alt+F2 you should get a login prompt for a full screen console.
Login through it and run the command.

the .Xauthority file is hidden in you users home folder, each user has it's own file personally for itself.
the command above will list the permissions and ownership of said file.

It may also be possible to simply move the file and let the system generate a fresh clean new one.
For that you can try
```
mv .Xauthority .Xauthority.bak
```
then the system should make one anew.
If that doesn't help, you can always move, or copy, the bak file by reversing the command 
```
mv .Xauthority.bak .Xauthority
```

Don't know if this will help, but a large number of login loops like this are because of that file being corrupted, so that's my thoughts on it at least.

---

### Post by RangerK on 2014-08-16
Thank you for your feedback, gentlement.  KNowing that I could get a terminal without logging in by clicking Ctrl+Alt+F2 was especially useful. (I didn't know that.)

Moving .Xauthority didn't work, and Alt-F4 didn't seem to do anything, though I wasn't sure when I was supposed to press it.

It turns out this was a problem with ecryptfs.  If I understand correctly, the same old password was used for both logging in and mounting my private directory.  When I changed my log in password, the directory couldn't mount and it would kick me back to the log-in screen.  Does this seem plausible????  

I knew that mounting my private directory was still using the old password, because I used it after
> Ctrl+Alt+F2
> Logging in with the new password
> ecryptfs-mount-private -- and them being promted to "Enter login passphrase"

I got the idea that my log in password needs to be the same as the password used by ecryptfs.

First I tried changing the log in password back to the old password using 'sudo passwd', but for some reason it wouldn't stick.  When I reset my machine, it revered to the same problem.

Next, I tried setting the ecryptfs password to the new password.  It worked.  I followed the directions in one of the answers given here: [http://askubuntu.com/questions/281491/cant-log-in-after-password-change-ecryptfs](http://askubuntu.com/questions/281491/cant-log-in-after-password-change-ecryptfs)

>  *based on grayfox May 17 at 19:28* - [http://unixtitan.net/main/2010/11/16/annoyance-changing-password-with-ecryptfs/](http://unixtitan.net/main/2010/11/16/annoyance-changing-password-with-ecryptfs/) *(i dont have enough reputation to comment his answer)*
  I had the exact same problem. Changed my password using 'passwd',  messed things up because of encrypted home directory. The above link  contains a solution:
  login to terminal
  $ ecryptfs-mount-private
  You need to know your old password to mount.
[INDENT]   This will unlock and mount your /home/$USER. At this point, we can   access /home/$USER. So just cd back into it and run&#8230;
 [/INDENT]
$ ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphrase[INDENT]   It&#8217;ll prompt you for your old password, and you can enter a new one afterwards.   You will need to change the password for your keyring as well.   From your menu bar &#8211; [Applications] => [Accessories] => [Passwords and Encryption Keys]   Under Passwords tab &#8211; right click &#8220;Passwords: login&#8221; and &#8220;Change Password&#8221;

 [/INDENT]
credits to [http://unixtitan.net](http://unixtitan.net) !

     


The only thing I didn't do was change the password to my keyring.  Right now I'm thrilled to have my work environment back because I have a ton of work to do.  

If anyone can shed further light on this issue, or correct anything I've misunderstood, I'd appreciate it.  Links to further reading are also welcome.

---

