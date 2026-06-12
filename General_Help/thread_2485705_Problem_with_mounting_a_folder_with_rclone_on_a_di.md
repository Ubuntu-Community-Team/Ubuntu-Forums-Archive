---
title: "Problem with mounting a folder with rclone on a different PC"
date: 2023-04-06
forum: General Help
---

### Post by johndid on 2023-04-06
Hi,
I installed Rclone on a linux machine (let's call it PC A), then I  uploaded a folder using the Rclone's encryption features to google  drive. I can list and mount the folder on google drive to a local folder  on the same pc (A) when I want to restore some files via the command:

```
rclone mount crypt: /home/tom/point/
```
Everything works fine and I'm happy with that.

Now, I'm trying to restore/recover my encrypted files on Google Drive on  another linux machine (Ubuntu server 20.04 lts, let's call it PC B), in  order to test if I still can get acccess to my files, in case  everything goes wrong with the other machine (A). So, I first installed  rclone on the new machine (PC B), then I copied the orginal  rclone.conf file into /home/john/.config/rclone.
It seems to be working since I can list the files stored on the cloud if I run via a putty ssh session:

```
rclone ls crypt:googlecry
```

But, if I try to mount it on a local folder of PC B:

```
rclone mount crypt: /home/john/googledrive/
```

nothing seems to be happening. By running a new root terminal from the web GUI (PC B is a ubuntu headless server) 
I got this:

```
ls: cannot access 'googledrive': Permission denied
```

I then stop the mount via  ctl+c and see this error message:

```
^C2023/04/06 17:59:05 ERROR : /home/john/googledrive/: Unmounted rclone mount
```

I am missing something here probably. Could help figure it out please?
Thanks

---

### Post by johndid on 2023-04-07
I did it on another linux pc with GUI and it worked. I can see and mount the encrypted folder I have on google drive and copy any file
on a local folder. So, there still must be something I can't figure out about how to manage and mount folder like this on a headless linux machine.

UPDATE:
OK! I figure it out! Sorry

---

