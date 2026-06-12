---
title: "Ubuntu Not letting me log in (i Changed My Home's Permissions)"
date: 2008-03-12
forum: General Help
---

### Post by spidercat000111 on 2008-03-12
Hi. This is my first time posting here and i don't know if im in the rite thread. Anyway... I was trying to change the permissions of this file for virtual box. i had aleredy done it once. But i did not remember so i thought... Ok maybe if i change the permissions Of HOME Them i will be able to get into virtual box. Of course after this hole thing i remembered (go figure...) For some reason after i changed to permissions i rebooted the computer. Now it wont let me log in beacause of the permissions. I do have other users but when i go to change the Permissions of the other acount that wont work from this one the fields are all greyed out. I tried to type the command gksudo nautilus but it gaves me an error. So is there anyway i can reset the permissions of HOME or change them from recovery mode? Thanks!

---

### Post by .nedberg on 2008-03-12
Try
```
sudo chown -R <username>:<groupname> /home/<username>
```replace <username> and <groupname> with desired values.

Then:```
sudo chmod -R 755 /home/<username>
```

---

### Post by sisco311 on 2008-03-12
> **.nedberg said:**
> Try
```
sudo chown -R <username>:<groupname> /home/<username>
```replace <username> and <groupname> with desired values.

Then:```
sudo chmod -R 755 /home/<username>
```

and
```
chmod 644 ~/.dmrc
```

---

### Post by p_quarles on 2008-03-12
Thread moved to General Help. 

As sisco311 points out, the problem here is most likely with ~/.dmrc. Changing permissions recursively in your home folder will essentially break that file. If correcting the permissions on that file doesn't help, you can simply remove the file so that a new one is generated.

For future reference, you don't need to alter permissions on anything to use Virtualbox. Rather, you need to add the users that need access to it to the appropriate group:
```
sudo adduser *username* vboxusers
```

---

### Post by spidercat000111 on 2008-03-12
Thanks. Its Ok. I just made my other acount into a admin and used all my settings from the other account on this. And i got vbox running!

Thanks for the quick replies!

---

