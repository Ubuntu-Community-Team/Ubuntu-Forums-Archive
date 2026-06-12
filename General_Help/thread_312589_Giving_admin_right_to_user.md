---
title: "Giving admin right to user"
date: 2006-12-04
forum: General Help
---

### Post by turshija on 2006-12-04
Hi there
I have screwed my main user that i have created in installation by changing something in "Users and Groups" from /users/home or something to /root and I haven't been able to log in... then I somehow managed to create new account from terminal named "boris" and used "sudo passwd root" to set root password.... 
Now here goes my problem ... New user named boris doesn't have any admin privileges and I don't know how to give them to it ... I know the root password and the main username named Turshija (on what i cannot login anymore because i screwed it) and I was wandering if there is some terminal command or something to set user "boris" same privilege as Turshija was...

Btw sorry about my English im not a native speaker and I am total Linux n00b thats why I managed to broke it up... :D

---

### Post by bapoumba on 2006-12-04
Boot in recovery mode (second line from top in grub menu). Be careful, you will be root !!

Then :
```
adduser Turshija admin
reboot
```

You should be able to login with Turshija. Please read [RootSudo]("https://help.ubuntu.com/community/RootSudo") regarding root priviledge.
Ubuntu favored not to activate the classical Linux root account. Once everything is okay for your user, you can disable the root account if you wish ;)

---

### Post by steve.horsley on 2006-12-04
If you know the root password, you can use **su** to get a root prompt (otherwise, use recovery mode). Then use **addgroup boris admin** to add boris to the admin group. Now boris should be able to use sudo, so he should be able to use the GUI users and groups admin tool. Maybe deleting and recreating your original user might be the easiest way to fix it.

---

### Post by turshija on 2006-12-05
> **bapoumba said:**
> Boot in recovery mode (second line from top in grub menu). Be careful, you will be root !!

Then :
```
adduser Turshija admin
reboot
```

You should be able to login with Turshija. Please read [RootSudo]("https://help.ubuntu.com/community/RootSudo") regarding root priviledge.
Ubuntu favored not to activate the classical Linux root account. Once everything is okay for your user, you can disable the root account if you wish ;)

Did it ... AND IT WORKS .. :D i logged in with boris and changed what I screwed on Turshija and it all works ... thank you guys ... :D

---

### Post by hypnotic_frog on 2006-12-05
Wow! Cool instuctions!
Need to do it on my work PC. ;)

---

