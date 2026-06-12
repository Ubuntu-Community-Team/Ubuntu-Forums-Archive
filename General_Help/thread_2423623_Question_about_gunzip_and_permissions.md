---
title: "Question about gunzip and permissions"
date: 2019-07-26
forum: General Help
---

### Post by xWEkxhW on 2019-07-26
Hi community,

I gunzipped something today and I noticed that the permissions changed from root to my username, and the originally root-owned .gz file was also removed. And this all appeared to be done without elevation.

Here is an example of what I did:

```
jez@garrus:~/logs$ sudo cp /usr/local/sbin/minecraft/logs/2019-07-25-2.log.gz .
jez@garrus:~/logs$ ls -l
total 8
-rw-r--r-- 1 root root 5182 Jul 26 13:17 2019-07-25-2.log.gz
jez@garrus:~/logs$ gunzip 2019-07-25-2.log.gz
jez@garrus:~/logs$ ls -l
total 24
-rw-r--r-- 1 jez jez 21878 Jul 26 13:17 2019-07-25-2.log
jez@garrus:~/logs$
```

Notice the original .gz file is owned by root, and after running gunzip it is owned by jez, and the original root owned file is removed.

How is this possible? I didn't sudo to run the gunzip and as far as I'm aware there aren't any fancy permissions on the home dir.

Just wondering, not a trick question.

Thanks

---

### Post by SeijiSensei on 2019-07-26
What user created the .gz file? I'm guessing it was root. The compressed file will retain the same ownership and permissions as it had before compression. Gunzip always replaces the compressed file with its uncompressed version.

---

### Post by xWEkxhW on 2019-07-26
minecraft user created it, it's a minecraft server

It definitely wasn't jez

And if the file is owned by root, how does gunzip have the capability to do this? root is root :)

---

### Post by SeijiSensei on 2019-07-26
I know nothing about minecraft. Is it supporting multiple users? Are they trustworthy?

---

### Post by xWEkxhW on 2019-07-26
minecraft is just a user, could be anybody. Probably just a /home thing

---

### Post by spjackson on 2019-07-26
This behaviour is all normal.

gunzip creates a new file and removes the old one. This can be demonstrated by ls -li. You will see that the i-node number changes. When it creates the new file, the owner has to be jez because that is the user running the program and there's no sudo. In order to remove the old file, the required permission is that the containing folder is writable by the current user, which it would normally be since it is ~/logs. Ownership & permission on the file itself do not matter for file removal.

---

### Post by TheFu on 2019-07-26
This is expected.  The directory permissions control whether a file can be created, modified, deleted.  Since the file was copied to a directory owned by a non-root account and that account, presumably, was used to gzip the file, gzip followed the expected behavior by using the userid running the gzip command to create the new file and that account had the authority, via the directory permissions, to delete the original. 

Expected behavior.

Forget gzip. Do this.

```
# Create a play area
mkdir ~/TEST
cd ~/TEST

# Create a root-owned file in the play directory
sudo touch root-owned-file

# Verify the directory is not owned by root, but the file is:
ls -l root-owned-file .

# delete the file owned by root.
rm root-owned-file
```

No error. This is the expected behavior.

The best way that I know to learn Unix permissions is to make 3 userids.  Mix and match those new userid into different groups, then create some play directories under /tmp/ for each of the users and play with some directories and files in each.  Probably best to open 3 terminals, one for each userid.  Try every possible combination of octal permissions to see what each userid can and cannot do with files.  After about 45 minutes doing this, something should "click" in your mind and you'll never have permissions issues again.  Don't forget to play with the setuid, setgid and "sticky" bits in the first octal and learn how those work. Also, definitely see how scripts and compiled programs are different when a directory has r-x--x--x permissions.  That one should blow your mind.

---

