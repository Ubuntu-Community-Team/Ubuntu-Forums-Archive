---
title: "Can't log in to main account (&quot;will&quot;) desktop session"
date: 2013-11-05
forum: General Help
---

### Post by W-Unit on 2013-11-05
Hi there.

I recently upgraded to Saucy and things were going fine. I needed to do a full restart so I did so (from a KDE Plasma desktop).

After restarting I am unable to log in to a desktop session on my main account (will).
Doesn't seem to matter what type of session I select - Kubuntu, Plasma, Xubuntu, Ubuntu (Default) - none of them work.
In all cases, after typing my password and pressing Enter, the screen goes black momentarily, and then I am back at the login screen. There are no error messages or anything.
I am still able to do stuff requiring superuser privileges via the console (CTRL+ALT+F1).

The "guest session" option works fine.

Thanks :)

---

### Post by Bashing-om on 2013-11-05
W-Unit; Hi !

Did the authentication change on your /home directory ?? - very often the case.
check:
At the GUI login ctl+alt+f1 -> terminal;
```

ls -la ~/.Xauthority
ls -la ~/.ICEauthority
ls -la /var/lib/lightdm/

```
If you are not the current owner, will have to "chown" them back to "you".

[INDENT][INDENT]we will see what is
[/INDENT][/INDENT]

---

### Post by newb85 on 2013-11-05
@Bashing-om, are you sure about that third line?  On my system, everything in /var/lib/lightdm is owned by lightdm.

---

### Post by Bashing-om on 2013-11-05
@newb85; Thanks for checking ! // I do not have lightdm installed so I can not check, but, so long as lightdm is not owned by root, we should be good in that department. Hey, that is my thinking (??)

[INDENT][INDENT]two heads are better than 1
[/INDENT][/INDENT]

---

### Post by W-Unit on 2013-11-06
Ah, I think I figured it out... I'm able to get logged in again normally, at least, but need to fix something so that I don't have to go through these steps every time...

I think things got messed up because I tried to change my login password by using the passwd command.

So for discussion purposes we have Password1 (old password that I had since installing Ubuntu) and Password2 (new password that I set using the passwd command).

So I press CTRL+ALT+F1 and log in successfully using Password2. I do an ls command and notice that there appear to be only two files in my home directory: One of them is a ".desktop" file with a name that metions something about accessing private data, the other is a README.txt. So I open README.txt with Vim and it tells me to use the command ecryptfs-mount-private.
After running with this command, I am prompted for my password. I try entering Password2 but am told that it is incorrect. Then I try Password1 and am successful; everything goes back to normal and I'm able to log in and access the files in my home directory.

So in summary, I can log in again, but at the moment it looks like I have two different passwords: one to log in (the new one), and one to actually access my home directory (the old one). How do I change them both to the same password?

Thanks again guys! :)

---

### Post by Bashing-om on 2013-11-06
W-Unit; Oh my.

Good deal you have it figured out.
Seems you have encrypted your /home directory. I have absolutely no experience in this realm and do not want to go there.

With no knowledge/experience I do not have the ability to advise further. we will have to depend on others' advise now in this matter.

[INDENT][INDENT]my best regards
[/INDENT][/INDENT]

---

### Post by newb85 on 2013-11-06
> **Bashing-om said:**
> 
N
[INDENT][INDENT]two heads are better than 1
[/INDENT][/INDENT]

Agreed, though I'm this case I think my machine was worth meet than my head...

---

