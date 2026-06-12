---
title: "Superuser account. Did I mess up?"
date: 2023-12-27
forum: General Help
---

### Post by ckrles on 2023-12-27
Hi. I had some trouble when sharing files from my laptop to my ubuntu pc. When I moved files in LAN from phone to ubuntu, ubuntu displayed a padlock which prevented me from manually deleting them (I could with administrative priviledges). I realized it was an issue of the owner. So I set a samba user and password. Everything works fine. NO padlock, but when I start my ubuntu pc I get the message: "Authentification is needed to run /bin/sh" as superuser. My user name is on top of the dialog box. In order to add a new samba user I used the command    	 	 	 	   udo useradd username -s /sbin/nologin

I set it yesterday. Did I do something wrong? I don't think I'm being hacked or something. I just found out this morning when I started the pc again.

I guess I have given my ubuntu user (samba user) supereuser priviledges. Should I remove them? (I guess). How could I remove them. I don't think I need any account with superuser priviledges.

Thanks.

---

### Post by ckrles on 2023-12-27
Any ideas?

---

### Post by Tadaen_Sylvermane on 2023-12-27
Forgive me,  your description is a bit muddy. Looks like you wanted to add a dedicated user for samba access? In this case you did it correctly but you can't login to that user directly. You need to give that user a samba password via ```
sudo smbpasswd -a "$USER"
``` where "$USER" is the samba user. Once this is done restart smbd ```
sudo systemctl restart smbd
``` After this you can mount your samba share from a Windows machine with the created username + password. This all assumes you've already correctly set up the share in the first place.

If you wanted to give a samba password to your existing user then you would need to do that ```
sudo smbpasswd -a "$EXISTINGUSER"
``` along with restarting smbd. First you will need to load a live image and chroot into the system to remove your user from the nologin group though. The group name is self explanatory why this is happening.

---

### Post by ckrles on 2023-12-27
I did give the samba user (same as main pc user) a password by using the command you indicate. What makes me feel concerned is that it asks for superuser password when booting. I didn't use any 'su' command. I only used sudo commands. 
The samba user in the pc can access the files pasted by my phone. No padlock on the files anymore.
I would like to know if I could have possibly messed up something in terms of system security, like giving too many permissions or leaving and open backdoor. And if so, how to undo it. How could I check if superuser is enabled and how do I stop the pop up message requesting the password?


How do I chroot into the system to remove my user from the nologin group?
Thanks.

---

### Post by Tadaen_Sylvermane on 2023-12-27
Load a live linux distro. Then mount the root partition of your machine to /mnt and run ```
sudo chroot /mnt
``` or whatever the path is. Then you can use ```
usermod --shell /bin/bash "$USERNAME"
``` Afterwards reboot from the hard drive instead of the live image and if I'm understanding what you explained it should work fine after this.

You can also manually edit the line in /etc/passwd but make sure you know exactly what you are doing else you can make things worse not better. The last field right now should show ```
/sbin/nologin
``` according to your requestr for help. So change that to /bin/bash

---

### Post by TheFu on 2023-12-28
I can't tell what you did or didn't do without actually looking at a 100% accurate list of commands for each userid.

The smbd daemon runs as root, so it doesn't need extra permissions to access storage. This is why samba/CIFS shares can self-manage access for remote systems.  It is a negative for security.

If it were me and I didn't know what I'd done, I'd wipe the OS and do a fresh install, taking careful notes. Additionally, I'd learn AND understand Unix file permissions.  As an Admin, this is not optional, it is mandatory, so spend the 30-90 minutes learning them until you are CONFIDENT that you know them. They are clear, simplistic and elegant.  Do this before you do anything thing else - practice with every possible combination of permissions with 3 different users and 2 different groups in a play directory system under /tmp/ .... 
Start with 000 permissions and work up to 777.  When you are all done, you'll understand when to use 751 and 755 and 644 and 640 and why you might want to do this: 
```
drw-rw-r-- 2 tf jellyfin  4096 Oct 27  2021 flac/
drwxrwxr-x 2 tf jellyfin  4096 Oct 27  2021 vorbis-q6/

```
for those directories.  Trust me, there are reasons.

Forget the "superusers".  On many Linuxen, we use **sudo** instead.  To do almost anything administrative, sudo is used to temporarily elevate privilege for 1 command at a time.  Further, each run of sudo gets logged, so there's no wondering which commands were run with what options.

---

### Post by ckrles on 2023-12-28
> **Tadaen_Sylvermane said:**
> Load a live linux distro. Then mount the root partition of your machine to /mnt and run ```
sudo chroot /mnt
``` or whatever the path is. Then you can use ```
usermod --shell /bin/bash "$USERNAME"
``` Afterwards reboot from the hard drive instead of the live image and if I'm understanding what you explained it should work fine after this.

You can also manually edit the line in /etc/passwd but make sure you know exactly what you are doing else you can make things worse not better. The last field right now should show ```
/sbin/nologin
``` according to your requestr for help. So change that to /bin/bash

I really don't know how to mount the root partition.

---

### Post by ckrles on 2023-12-28
> **TheFu said:**
> I can't tell what you did or didn't do without actually looking at a 100% accurate list of commands for each userid.

The smbd daemon runs as root, so it doesn't need extra permissions to access storage. This is why samba/CIFS shares can self-manage access for remote systems.  It is a negative for security.

If it were me and I didn't know what I'd done, I'd wipe the OS and do a fresh install, taking careful notes. Additionally, I'd learn AND understand Unix file permissions.  As an Admin, this is not optional, it is mandatory, so spend the 30-90 minutes learning them until you are CONFIDENT that you know them. They are clear, simplistic and elegant.  Do this before you do anything thing else - practice with every possible combination of permissions with 3 different users and 2 different groups in a play directory system under /tmp/ .... 
Start with 000 permissions and work up to 777.  When you are all done, you'll understand when to use 751 and 755 and 644 and 640 and why you might want to do this: 
```
drw-rw-r-- 2 tf jellyfin  4096 Oct 27  2021 flac/
drwxrwxr-x 2 tf jellyfin  4096 Oct 27  2021 vorbis-q6/

```
for those directories.  Trust me, there are reasons.

Forget the "superusers".  On many Linuxen, we use **sudo** instead.  To do almost anything administrative, sudo is used to temporarily elevate privilege for 1 command at a time.  Further, each run of sudo gets logged, so there's no wondering which commands were run with what options.
I had thought of that. I'll probably wipe the OS and make a fresh install, specially since I'm running ubuntu 20.04 Lts. I'll move to ubuntu 22.04 Lts.
What would be the safe and correct way to add a user to samba?

---

### Post by TheFu on 2023-12-28
smbpasswd

---

