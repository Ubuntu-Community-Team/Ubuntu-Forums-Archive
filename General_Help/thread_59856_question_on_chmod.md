---
title: "question on chmod"
date: 2005-08-25
forum: General Help
---

### Post by cymoril on 2005-08-25
hello there,

i posted earlier in a another thread about my inability to sudo ( sudo: must be setuid root )

thankfully, that problem has been solved.

i think it was the command chmod -R 777 /usr/sbin which caused this problem.

is there any way i can reverse the chmod i did? does it matter?

thanks,
cymoril.

---

### Post by Juergen on 2005-08-25
I don't know another way than to get a list and manually re-apply the original permissions file-by-file. 

Most files in /usr/sbin are 755, but some need to be executed in another user/group context than that of the calling user - these won't work correctly anymore.

And maybe even worse: you removed the security settings for this directory with **s**ystem-**bin**aries in it. 
Anybody with access to your box now can write to these files and maybe replace them with cracked versions, e.g. 'rootkits' (your permissions are similar to running always as root - like in windows...).

The 'brute force' way to get the permissions back would be a reinstall - if you can make a backup of your $HOME (or better, it is on its own partition) , that might be the way to go for you.

---

### Post by cymoril on 2005-08-25
Thanks Juergen.

I guess I really messed up.

You said that:

 "some need to be executed in another user/group context than that of the calling user - these won't work correctly anymore." 

I don't understand. I am the sole user of this machine. Is there a chance of files/apps not working at some point in the future?

About the backup, are the settings for my programs kept in /home? The only thing I see when I do ls from /home/user is Desktop. And there are just links on my Desktop.

I am curious to know where the settings for programs like Opera and Thunderbird are stored. If they are in Home, I don't know how to view them or I'm doing so incorrectly.

Thanks,
Cymoril

---

### Post by Irony on 2005-08-25
There's a bunch of *.folders* and *.files* in *home/user* - they are visible if you push *Ctrl+H* to reveal hidden files.

I'm new to this but for example the *.B.blend* file in my *home/user* file holds the settings I have saved for the default look for my Blender files.

---

### Post by cymoril on 2005-08-25
ah, that works. thank you.

---

### Post by Juergen on 2005-08-26
> I don't understand. I am the sole user of this machine. Is there a chance of files/apps not working at some point in the future?No, you aren't 'the sole user'.

Look at /etc/passwd. These users are defined on your system (and some are really used ;-)).
Open an xterm and type 'ps aux'. The first column is the user that runs a process - you'll probably see several others than your own account.

By running them under their own user-account you can restrict the rights of (server)processes, so if they have a security-hole that is exploited the badboy still won't have access to the whole system.

Take sudo as example: after setting the 'suid' bit in its permissions it is no longer run under the user-account calling it, but under the user it belongs to - root. 
This way sudo can execute stuff for you with root-rights. If you take the suid-flag away, sudo doesn't work anymore...

---

