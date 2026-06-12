---
title: "my home moved"
date: 2007-12-29
forum: General Help
---

### Post by roschell on 2007-12-29
I was just trying to share photos between users on my pc in bash, when my home directory gone... 
Then I found it in other user's Desktop folder, how can I get it back? 

/home/rick possibly moved to /home/iris/Desktop, as it is there but without access

thanks guys

---

### Post by Aseld on 2007-12-29
Who has root access on this computer? Which commands did you run? Did you use "sudo mv [anything]"?

---

### Post by roschell on 2007-12-30
I have the root access and that is the directory which was moved, and you are right I did use also a command sudo mv ...  as I tried to transfer link to photos onto other user, cant exactly recall the full command. I believe it is somewhere in script but now have no access to it...

---

### Post by p_quarles on 2007-12-30
First, if you want to transfer files from your home directory without removing them, you should use the "cp" command rather than the "mv" command. 

Second, you can browse through the entire hard drive by running this:
```
gksudo nautilus
```
This gives you root access to the entire hard drive, so be careful what you do here.

---

### Post by roschell on 2007-12-30
This was just a link I attempt to transfer, and I do not understand how it resulted in user's folder move. How can I move it back? 

the command is asking for password which is not the same as the root password, it does not work;

thanks for help, I am user, not programmer

---

### Post by p_quarles on 2007-12-30
Use your own password, not root's.

---

### Post by roschell on 2007-12-30
I tried both but get 'failed to run nautilus as a user root', now I am logged in as a different user not as a admin; admin was the account which was moved and I can not get into it.

---

### Post by roschell on 2007-12-30
I did not find a way how to transfer my admin's account back to /home within ubuntu, however my try to so through SLED worked very well. With root's permission I could transfer my ubuntu's admin account back where it belongs. 

This may be a good idea to keep two different versions of linux on a pc...

---

### Post by ~LoKe on 2007-12-30
> **roschell said:**
> I did not find a way how to transfer my admin's account back to /home within ubuntu, however my try to so through SLED worked very well. With root's permission I could transfer my ubuntu's admin account back where it belongs. 

This may be a good idea to keep two different versions of linux on a pc...

It may be a good idea not to do things of which their outcome is unpredictable or unknown to you.

---

### Post by roschell on 2007-12-31
> **~LoKe said:**
> It may be a good idea not to do things of which their outcome is unpredictable or unknown to you.

Is installed linux system predictable? why then there would be so many threads in forums such as this one; why systems have bugs? In my case I ran basic command on transfer of a folder, and faced unpredictable consequences, you are right, then why the system acted as it did; Is it because your critics outbalances the helping and programming site, cos you did not certainly replied on solving this issue in the first place. But I wish you happy new year anyway.

---

### Post by ~LoKe on 2007-12-31
> **roschell said:**
> cos you did not certainly replied on solving this issue in the first place.
Because your problem was solved by the time I got here.  I was simply giving you a suggestion for future situations.  Syntax errors could cause serious problems, so I was advising you to be careful what you type into the terminal.  Just a friendly suggestion; sorry you took it the wrong way.

---

### Post by dlegend on 2007-12-31
As an additional tip for the future, if you happen to type a command that you've forgotten and need help reversing it, you can find a list of recently typed commands by typing **history** in the terminal. You can also search your history commands by typing **history | grep "search term here"**. That way you can simply find the commands you've recently typed and post them with the help request thread so people know exactly what you've done.

---

### Post by roschell on 2007-12-31
I appreciate the suggestion, thanks. Just tried that to see why the system behaved different way and got me into trouble. But listen what..., the command is not there, doesnt this list only commands which went OK? if it is the case then we know why..., is there a place I can locate exactly what happened and possibly report the bug?

---

