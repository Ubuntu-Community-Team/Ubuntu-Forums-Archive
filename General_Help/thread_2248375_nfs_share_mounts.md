---
title: "nfs share mounts"
date: 2014-10-14
forum: General Help
---

### Post by zcgokce on 2014-10-14
I have a synology system. I can see the shares if I use nautilus and use the desktop.  But  I would like to mount them to /mnt/Media.  In the past with onther NAS system I have used cifs and was able to mount it.  

I have used the following on the fstab
```

10.10.2.46:/volume1/New  /home/zeki/mnt/Media nfs soft,intr,rsize=8192,wsize=8192

```when I do ```
sudo mount -a

```

I get no error but when try to to cd to the mnt/Media folder 

I get the following error 

[B]-bash: cd: Media: Permission denied
[/B]

When I try to access the same folder from the Nautilus gui I get a permission error and it looks like I am not the owner and only root can have access to it.  When I su to Nautilus I have access to the folder.  I have tried chancing the owner of the folder with chown but it did not help. 

What am I missing here.  

Thanks for the help.

---

### Post by TheFu on 2014-10-14
/Media is very different from /home/zeki/mnt/Media.

I suspect you really mean for /mnt/Media to be in the fstab, then you'd need to go to /mnt/Media (case sensitive).

---

### Post by zcgokce on 2014-10-14
Thanks for the quick response.  When the folder that I am trying to cd to is /mnt/Media.  that is where I am getting the error at.

---

### Post by TheFu on 2014-10-14
Look at your fstab above - that's all I had to go on. It clearly says you want to mount that storage to
/home/zeki/mnt/Media.  That directory must pre-exist before the mount command will work, BTW.

**df**  should show the mounts. Does it show the mount you expect?

---

### Post by zcgokce on 2014-10-14
I already have the mnt/Media folder.  df show the following. 

10.10.2.46:/volume1/New 8707393240 5386245560 3321045280  62% /home/zeki/mnt/Media

It seems to me that it is mounted I just have the permission issue.

**-bash: cd: Media: Permission denied**

---

### Post by TheFu on 2014-10-14
ls -al /home/zeki/mnt/Media
??

Have you tried to chmod or chown it?

BTW - the posts above are double confusing to me because the directory mentioned seems to change locations even inside the same post. Please be exact, specific, and accurate to get better help.

---

### Post by zcgokce on 2014-10-14
[COLOR=#000000]ls -al /home/zeki/mnt/Media returned 

[/COLOR]ls: cannot open directory /home/zeki/mnt/Media: Permission denied


I have tried chown but it did not work.  

I went back to the original post and re read it and and corrected the discrepancies.  Thanks for the help.

---

### Post by TheFu on 2014-10-14
I really think you want to do what I suggested in post #2 above. THAT is the best location of all the choices. Mounting storage under a personal HOME is a terrible idea 99.999999% of the time.

/mnt/Media is the best choice of all the stuff said above. 
[B]sudo mkdir /mnt/Media 
[/B]fix the /etc/fstab for that location[B]
sudo mount -a
sudo chown -R your-id:your-id /mnt/Media[/B]

Be happy.

---

### Post by zcgokce on 2014-10-14
I solved the problem.  It was a setting with the synology nfs.  When setting up the nfs permissions Squash needs to be set to map all users to admin. 

But mounting outside of the home makes perfect sense now you mentioned it.  So I have fixed the fstab as well.  Thanks for your help and good feedback

Cheers

---

