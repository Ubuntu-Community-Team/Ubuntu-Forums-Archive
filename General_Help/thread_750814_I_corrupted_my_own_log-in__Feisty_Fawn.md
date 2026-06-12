---
title: "I corrupted my own log-in / Feisty Fawn"
date: 2008-04-09
forum: General Help
---

### Post by IggySaffron on 2008-04-09
I installed 7.04 last night.  I used 'ubuntumark' as my log-in.  After I had restarted a number of times, I realized it was too long, so I went to the users section and shortened it to 'mark'.  I also edited one other file from 'ubuntumark' to 'mark'.  There was another file or directory which I could not edit.

Now when I rebooted, the new user name shows me errors, like:

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the fail safe sessions to see if you can fix this problem."

I am a novice, so I would need clear steps to follow, if you are willing to help.

Thanks

---

### Post by warp99 on 2008-04-10
Well you changed you name, but didn't change the name of your home directory. So boot up normally as you would then at the login screen press crtl+alt+F2, login then issue the following:

```
cd /home/ && ls -l
```

You should have a directory name 'ubuntumark', but no directory named 'mark' so move the  directory:

```
sudo mv ubuntumark mark
```

type exit, then press crtl+alt+F7 to get back to a login screen and login as normal.

---

### Post by IggySaffron on 2008-04-10
Thanks for helping.  I get the message:
mv: cannot stat 'ubuntumark': no such file or directory.

I must have messed up big.  Is there anything further that I can try?

Thanks, Mark

---

### Post by warp99 on 2008-04-10
Without looking at what you did it going to difficult to fix the problem, so your best bet is to boot into recovery mode then make a completely new user with admin rights. He's how you would do this:

Boot up the computer and when the "Grub Loading" line appears quickly press 'escape' then choose recovery mode to boot into a command prompt, then the following:

```
adduser <name_of_new_user>
```

then

```
usermod -G adm,dialout,cdrom,floppy,audio,dip,video,plugdev,lpadmin,scanner,admin,fuse <name_of_new_user> 
```

If one of the groups is not available just omit that group since it hasn't been created. Quick little trick is to press the up arrow and the command string will reappear so you can edit out offending group and press enter. Don't worry if you run out of screen just keep typing, the command string will wrap around. 

After that just enter 'reboot' and you can login to your new account with the same privileges as your old user name. Once you know that your new user name is working properly with 'sudo' you can delete your old user name and old user directories. Hope this helps.

---

### Post by IggySaffron on 2008-04-10
WARP99, you rock.  Many thanks!!
Mark, formerly ubuntumark

:)

---

