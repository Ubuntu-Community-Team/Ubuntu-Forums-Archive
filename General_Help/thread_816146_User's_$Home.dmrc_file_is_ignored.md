---
title: "User's $Home/.dmrc file is ignored"
date: 2008-06-02
forum: General Help
---

### Post by momo07 on 2008-06-02
Hello,
I recently installed ubuntu ver 8.05 (Hardy Heron) on my machine and was instantly amazed.  I am new to the Linux OS and I don't think I will be going back to windows thanks to ubuntu.  However I need some help please.  Whenever I try to log in to my machine I get the following message:

User's $Home/.dmrc file is ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $Home directory must be owned by user and not writable by other users.

I also have another problem when I click on the update icon.  I can see the updates but the package manager just hangs after I click on update. I don't know if these are related.  

Please let me know how to rectify this in more detail as I'm new to ubuntu.

Thanks in advance

---

### Post by drs305 on 2008-06-02
Try running this to reset the home folder and .dmrc permissions:
```
chmod 750 ~/ && chmod 644 ~/.dmrc
```

You may need to log out and back in to clear things up (switch users). The 750 setting will not allow others outside your group to view your home folder. If you want them to be able to see and execute items in your home folder, change 750 to 755.

---

### Post by Znort_Ubern00b on 2008-06-02
do as above...damn he's quick...lol

---

### Post by drs305 on 2008-06-02
> **momo07 said:**
> I also have another problem when I click on the update icon.  I can see the updates but the package manager just hangs after I click on update. I don't know if these are related.  

It could be a server problem. To check this, open synaptic > Settings > Repositories > Ubuntu Software > Download from > Other > Select Best Server.

This will pick a good server for your area and if it was a server issue this should solve it.

---

### Post by momo07 on 2008-06-02
Thanks drs305,

That worked like a charm. Also thanks for your effort Znort_Ubern00b.  This is the best I appreciate your responses.

Thank you

---

### Post by krlhc8 on 2008-06-03
Holy friggin' crap you're awesome!  I've been trying to figure this out for weeks!  I kept trying chmod 644 ~/.dmrc, but it didn't work and made me want to cry.  Thanks.

---

### Post by BigT0 on 2008-06-13
WOW! Thanks allot.
i had the same problem after installing hardy over an existing hardy. the installation replaced system files but not the /home. I named the new user the same name as my previous one and i think thats why it gave me the above error on login.
I went through a few posts but this one hit bulls eye!

---

### Post by Liv3dN8as on 2008-08-18
I too have this problem and I have tried a few solutions with none solving the problem. I'm out of ideas besides reinstalling and I really don't want to do that.
Here is my permissions for my .dmrc file:
srw-r--r-- 1 god god 0 2008-08-01 08:31 /home/god/.dmrc

Let me know if there is anything else you need to help me out.
Thanks in advance.

todd

---

