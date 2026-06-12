---
title: "chmod command doesn't like .gvfs folder"
date: 2013-09-29
forum: General Help
---

### Post by ozark_hillbilly on 2013-09-29
When executing the chmod command:

chmod -R a+rwX,o-w


this is the error message under terminal mode:

root@ed-Desktop:/home/ed# chmod -R a+rwX,o-w /home/ed
chmod: cannot access `/home/ed/.gvfs': Permission denied
root@ed-Desktop:/home/ed# 


.gvfs is an empty folder; i get this trying to list it in terminal:

root@ed-Desktop:/home/ed# ls -l .gvfs
ls: cannot access .gvfs: Permission denied


attached is a screenshot of the user directory and folder

I installed an app into my /home/ed.....  area and the install assigned root ownership to all the files related to the app. I wanted to reassign w/ my user permissions to these new files. File permissions/ownership is an ongoing challenge for me unfortunately.

Any help is appreciated,

Ed

---

### Post by steeldriver on 2013-09-29
That's likely nothing to do with your recent app install - the .gvfs directory is not really a 'folder', it's a mountpoint for user-mounted filesystems and for that reason its default ownership / permissions are *drwx------ user user*. Leave it alone.

---

### Post by Impavidus on 2013-09-30
To repair the root-owned files in your directory, just run```
sudo chown -R ed:ed /home/ed
```That should change all file ownerships back to yourself. If you've set up some special groups for some files threat them separately. If you don't know what I'm talking about, this is not the case for you.

---

### Post by ozark_hillbilly on 2013-09-30
Received the following when trying to do the chmod:

root@ed-Desktop:/home/ed# sudo chmod -R ed:ed /home/ed

chmod: invalid mode: `ed:ed'

---

### Post by Vaphell on 2013-09-30
he meant chown, either way i don't think chowning/chmodding filesystems mounted in user session is a good idea, like steeldriver said. You have fstab for that.

---

### Post by Habitual on 2013-09-30
> **steeldriver said:**
> Leave it alone.

+1

---

### Post by Impavidus on 2013-09-30
Indeed, I meant chown.

Yes, leave .gvfs alone. Nothing was mounted there, but my earlier statement refered to> I installed an app into my /home/ed.....  area and the install assigned  root ownership to all the files related to the app. I wanted to reassign  w/ my user permissions to these new files. File permissions/ownership  is an ongoing challenge for me unfortunately.Anyway, using a root shell to manipulate files in your home directory is asking for trouble in the form of root-owned files. It's better not to use a root shell and use sudo to fix things in your home directory. If properly done, you should never need it again. Actually, it's always better to use sudo than to use a root shell. See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for some additional info.

---

### Post by ozark_hillbilly on 2013-09-30
Thanks for the tip and I will stay out of the root shell from now on. I did manage to get the permissions changed BTW!

Appreciate the help from you guys.

---

