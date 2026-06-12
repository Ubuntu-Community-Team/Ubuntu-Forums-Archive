---
title: "[SOLVED] Screwed up file permissions. Superuser's access denied."
date: 2007-12-04
forum: General Help
---

### Post by Bheegerji on 2007-12-04
In messed up with my file permissions and when I tried to login the next  time, I can't access my account (which happens to be the superuser account)

After signing with my password I get this message:

"User's $HOME/.dmrs file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

After I click on the OK switch, I get another message:

"Your session lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem.

Details of error

Can't create dir/home/username/Desktop
Can't create dir/home/username/Desktop
Can't create dir/home/username/Template
Can't create dir/home/username/Public
Can't create dir/home/username/Document
Can't create dir/home/username/Music
Can't create dir/home/username/Picture
Can't create dir/home/username/Video"

I have another account on my system. I can see that the file permissions of the superuser account has been set to "List, create and delete, no access."

Please help to restore my account.

---

### Post by scxtt on 2007-12-04
boot into recovery mode (hit escape when grub prompts if you've never seen "recovery mode" as an option) - you'll be "root" and be able to restore the correct permissions.

---

### Post by Bheegerji on 2007-12-04
> boot into recovery mode (hit escape when grub prompts if you've never seen "recovery mode" as an option) - you'll be "root" and be able to restore the correct permissions.

I tried to login with my account and password in recovery mode but get the same error.

---

### Post by scxtt on 2007-12-04
recovery mode should automatically log you in as root, i've never seen it not (i.e. you're not prompted to log in, you're just given a root prompt).

---

### Post by Bheegerji on 2007-12-04
But its asking me to login. I'll try again and let you know.

---

### Post by scxtt on 2007-12-04
by the way, you DEFINITELY should not have a GUI - so if you're still getting one - you're not in recovery mode ...

also, you could use a LiveCD to fix this issue ...

---

### Post by Bheegerji on 2007-12-04
Yeah, the last time it asked to type the root password or control-D. I typed COntrol-d and was lead to the login screen.

This time I typed the root password and i'm shown the command prompt. What are the commands that I should give? I'm not well versed in linux commands.

---

### Post by Znort_Ubern00b on 2007-12-04
at the prompt type 
chown /home/yourusername yourusername

this should allow you to log in again

---

### Post by Bheegerji on 2007-12-04
After login, how do I change my file permissions?

---

### Post by Znort_Ubern00b on 2007-12-04
are you in admin group on system??
 if so you can change permissions by right clicking on folder and choosing properties then permissions tab...ensure you click the apply to folders within button.

---

### Post by scxtt on 2007-12-04
> **Znort_Ubern00b said:**
> at the prompt type 
chown /home/yourusername yourusername

this should allow you to log in againit would actually be:

chown $USER /home/$USER
ex. chown scxtt /home/scxtt

---

### Post by Bheegerji on 2007-12-04
> chown /home/yourusername yourusername

I'm getting this reply
bash: chown/home/alpha: No such file or directory


> are you in admin group on system??
if so you can change permissions by right clicking on folder and choosing properties then permissions tab...ensure you click the apply to folders within button.

The second user is not in the admin group.  Thats what I'm using now.

---

### Post by scxtt on 2007-12-04
> **Bheegerji said:**
> After login, how do I change my file permissions?hard to say w/ absolute certainty since we don't know what you did to put you in this position ...

what's the output of **ls -l /home** - you need to be sure your user owns his/her own directory and it's not writable by anyone else ...

---

### Post by Bheegerji on 2007-12-04
> what's the output of ls -l /home

total 8
drw-rw-rw- 55 username username 4096 2007-12-03 20:21 username
drwx------ 34 secondaryusername   adm   4096 2007-12-04 16:46 secondaryusername

---

### Post by scxtt on 2007-12-04
well you'll have to do the following for "username":

chmod 755 /home/username

the rw- for "other" is what's preventing you from loggin in as "username".

---

### Post by Bheegerji on 2007-12-04
> chmod 755 /home/username

Thanks SCXTT. That worked. Loged in back to my account.


One more thing. Where do you guys learn all these commands from? I'd love to learn all these.:confused:

---

### Post by scxtt on 2007-12-04
over time you learn things like that - i've been messing w/ unix/linux since '98 - even went to school for/graduated w/ a degree in "computer science" and work w/ it daily ...

not that it has to be that way for everyone, but to get the most out of it you've got to put more than "a click here, a click there" into it ...

in time, you'll know lots of commands too :)

---

### Post by Bheegerji on 2007-12-04
> over time you learn things like that - i've been messing w/ unix/linux since '98 - even went to school for/graduated w/ a degree in "computer science" and work w/ it daily ...

not that it has to be that way for everyone, but to get the most out of it you've got to put more than "a click here, a click there" into it ...

in time, you'll know lots of commands too 

Thats a long time. 

I got my comp(with WinXP) only 2 years back, and have been usin Linux from last month. I'm sure with the support you guys give I can learn more.

anyways thank you for your support mate.
and thanks to Znort_Ubern00b too.

---

### Post by 303rdLogistics on 2008-02-18
I had the exact same problem, and fixed it by following SCXTT's instructions of entering "chmod 755 /home/username" in recovery mode.

I'm wondering what could be a possible cause of this so I can prevent this from happening again, thanks!

---

