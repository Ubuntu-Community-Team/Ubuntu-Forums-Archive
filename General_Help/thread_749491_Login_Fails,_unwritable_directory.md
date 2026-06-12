---
title: "Login Fails, unwritable directory?"
date: 2008-04-08
forum: General Help
---

### Post by N_nykrog on 2008-04-08
Hi Everyone!

I'm not that experienced with Ubuntu, I've used FF a few months. Yesterday I tried making my OOo compatible with docx, unsuccesfully. Today I am unable to login, and my computer gives me the error:

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME diretory must be owned by user and not writable by other users.

And follows up with another:

The GNOME session manager was unable to lock the file '/home/niels/.ICEautority'. Please report this as a GNOME bug. Sometimes this error may occur if the file's directory is unwritable, you could try to login in via the failsafe session and ensuring that it is.

I am, however, able to start the xserver with startx.

I've had other problems, such as being unable to upgrade, 

[http://ubuntuforums.org/showthread.php?t=666319](http://ubuntuforums.org/showthread.php?t=666319)

but I've ignored them, as my Ubuntu has worked functionally.

I will be very happy if anyone is able to help me with precise orders of what to do, at least to save my files.

---

### Post by redbob on 2008-04-08
Hi!

I suffered for this kind of problem some days ago. I was 'opening' some folders by the command chmod and I accidentally chmoded from the / !! So my machine turned impossible to fix. Since Hardy Heron is comming soon, you could wait 'til final release may arrive, then you boot with a Live CD, backup your files, and make a fresh install. You just gain with it, because we are catching experience with ubuntu installing. 
;)

---

### Post by nkassi on 2008-04-08
To fix your home directory you can do the following
from a teminal (ctrl-alt-f1)

type the following 

```
sudo chown -R your_username /home/your_username
```

type in your password when it ask

of course don't forget to replace your_username with your current username 

Nic

---

### Post by ibuclaw on 2008-04-08
1) Boot into Recovery Mode
 It should be option 2 in the GRUB Menu.

2) You'll be brought to a lovely console screen.
 Type in the following:
```

cd /home
chown **username**:**username** **username** -R
cd **username**
chmod 755 * -R
chmod 644 .dmrc
chmod 644 .ICEauthority
exit

```
Upon typing in exit, gdm will continue to load.

3) Login as usual.
That should bring you back to some normality

Regards
Iain

---

### Post by N_nykrog on 2008-04-08
Well thanks everyone, I simply did what nkassi told me to, and it worked!

---

