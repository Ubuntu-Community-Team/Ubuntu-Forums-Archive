---
title: "some files can't be deleted through FTP"
date: 2006-10-05
forum: General Help
---

### Post by bastupungen on 2006-10-05
Hello!
I am running azureus and and FTP-server with my ubuntu system. So i can upload files both with the FTP clients and with azureus, its an easy and fast way to get a hold of files and then download then to the clients with FTP.

But I am having some unexplainable problem with permissions. I cannot delete the files downloaded by azureus through FTP. I can delete files created by my main user and files created in the FTP program. 

So! I checked which user/group that the files created by azureus are given too. Files created through azureus get the same permissions and files i create with my main user. And the files I create with my main user I can delete with FTP.

So I can delete some files and not delete some, even though the have the same group/user and permissions... WHAT GIVES!!!???

/Bastu

---

### Post by wkulecz on 2006-10-06
Post the result of "ls -la" in your ftp directory.

While the u+g may be r+w, the azureus user may by default be in a different group than the group the "owns" the ftp directory.

--wally.

---

### Post by bastupungen on 2006-10-06
drwxrwxr-x  5 bastu  bastu 4096 2006-09-22 08:49 .
drwxrwxrwx 16 mediau users 4096 2006-10-05 01:35 ..
drwxr-xr-x  2 bastu  bastu 4096 2006-09-21 19:11 Sigur_Ros-Agaetis_Byrjun-2CD-Limited_Edition-2000-NuHS
drwxr-xr-x 10 bastu  bastu 4096 2006-09-21 19:18 Slagsmalsklubben-Collection-8RLS-VIP
drwxr-xr-x  2 bastu  bastu 4096 2006-09-21 19:21 Sophie_Zelmani-A_Decade_of_Dreams-2005-SMiD
-rwxr-xr-x  1 bastu  bastu    0 2006-10-06 02:07 test

hmm... The test file that I had created with my user. It doesn't have the "d" in the beginning of the permissions-line. What does that mean?

Oh, it ment directory. So question still unanswered.

---

### Post by bastupungen on 2006-10-07
bump, please try to simulate this if you can. I cannot for my wildest dreams figure this one out...

---

### Post by taurus on 2006-10-07
The "d" in front means it's a directory, NOT a file!!!  So if you want to remove everything under it, including itself, then do

```
rm -rf Sophie_Zelmani-A_Decade_of_Dreams-2005-SMiD
```

---

### Post by bastupungen on 2006-10-07
Ok, I found the problem!

The directory was not set to group-write there for, for some reason, i could not change the files in it, exept if i created the file myself, eventhough i had made the file accessable to all.

---

