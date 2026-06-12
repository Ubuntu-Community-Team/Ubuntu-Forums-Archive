---
title: "Can't access my ubuntu account....."
date: 2014-05-27
forum: General Help
---

### Post by Harsh_Parikh on 2014-05-27
Hey,I can't access my ubuntu account.....everytime when i write my username and password,it will take me back to the username prompt.....i tried hundred of times but everytime it takes me back to the username prompt and never says "Incorrect Password".....i also tried to change password from recovery mode....still i can't access.....Please help.....

---

### Post by nknwn on 2014-05-27
When you tried to "change your password from recovery mode" did you make your system files writeable?
Check step 3 here:
[http://ubuntuforums.org/showthread.php?t=2226219&p=13033419#post13033419](http://ubuntuforums.org/showthread.php?t=2226219&p=13033419#post13033419)

---

### Post by Impavidus on 2014-05-27
Your graphical session crashes as soon as it starts, taking you back to the login screen. There is no problem with the password. The usual suspect would be the file **.Xauthority** in your home directory, which, through incorrect usage of sudo, may have become root-owned. **.ICEauthority** sometimes causes the same problem. Both must be owned by you and have permissions -rw------- (octal 0600). If you login in the console (ctrl-alt-F2) or from a root shell (recovery mode), you can check and fix if needed.

---

### Post by Harsh_Parikh on 2014-05-27
> **Impavidus said:**
> Your graphical session crashes as soon as it starts, taking you back to the login screen. There is no problem with the password. The usual suspect would be the file **.Xauthority** in your home directory, which, through incorrect usage of sudo, may have become root-owned. **.ICEauthority** sometimes causes the same problem. Both must be owned by you and have permissions -rw------- (octal 0600). If you login in the console (ctrl-alt-F2) or from a root shell (recovery mode), you can check and fix if needed.

How can i fix it..??Please tell quickly......

---

### Post by Harsh_Parikh on 2014-05-27
> **nknwn said:**
> When you tried to "change your password from recovery mode" did you make your system files writeable?
Check step 3 here:
[http://ubuntuforums.org/showthread.php?t=2226219&p=13033419#post13033419](http://ubuntuforums.org/showthread.php?t=2226219&p=13033419#post13033419)

Yes,I did it....but tell me about .Xauthority file if you know anything about it.....

---

### Post by NM5TF on 2014-05-27
I had the same problem a while ago....you might need to do this from a terminal using ALT+TAB+F1...

```
sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo service lightdm restart
```

of course you will need to use your password when asked for it

the entire thread is here:

[http://ubuntuforums.org/showthread.php?t=2224708](http://ubuntuforums.org/showthread.php?t=2224708)

tommy

---

### Post by Impavidus on 2014-05-27
> **Harsh_Parikh said:**
> Yes,I did it....but tell me about .Xauthority file if you know anything about it.....
please Quick....I am online now....

Obviously you were online when you posted that, but I wasn't.

Good link by NM5TF. Read post #3 in particular.

---

