---
title: "Can't login to ubuntu after username, hostname and password change"
date: 2013-06-29
forum: General Help
---

### Post by LinuxWillWin on 2013-06-29
Hello friends,

I have a serious problem. I changed my username, hostname and my userpassword in the files ```
/etc/hosts/
/etc/hostname/
/etc/passwd/
```. Now when I try to login on my username it appears the login tone and it switches back again to the login screen, so I am not able to login to Ubuntu. When I press CTRL+alt+F1 I can login to my account through the command line and navigate through my folders, etc. When I try to start the gui with ```
startx
``` I have just a black screen and nothing happens. I also have activated the root account login on the login screen and set a root password a longer time ago. On this account I can normally login to my Desktop. 
I hope someone can help me with this, thank you so much.

---

### Post by steeldriver on 2013-06-29
The X server needs to write to your home directory when it starts up - did you rename your home directory as well? what about the numeric UID / GID? if so did you make sure the 'new' username owns its home directory?

Just fyi there's no need to edit /etc/passwd directly - there are tools (like usermod) for that

I'm not sure what you mean by "activated the root account login on the login screen' but if you mean you use the username 'root' (instead of a user to which you have given sudo privileges) that's a bad idea

---

### Post by LinuxWillWin on 2013-06-29
(Sorry for my bad english, I'm from Germany ;) 
That could be the point. Yes I think I renamed the home directory. Probably I didnt make the new username owning the home directory, but how do I ? (Yes, I knew that a account with the name root is bad and dangerous, but I just wanted to test it.)
So,... what shall I do next?

---

### Post by steeldriver on 2013-06-29
Don't worry, your english is just fine (a million times better than my deutsche)

So when you are logged in with your new username at the Ctrl-Alt-F1 console, what do

```

ls -ld ~

ls -ld ~/.Xauthority

```

say? do you see your new name in the user column? or the old name? or just a number (like 1002)?

---

### Post by LinuxWillWin on 2013-06-30
SOLVED! :)
I forgot to change my old username to my new one in the file ```
/etc/passwd
``` in line 39. 
Thanks for your help!

---

