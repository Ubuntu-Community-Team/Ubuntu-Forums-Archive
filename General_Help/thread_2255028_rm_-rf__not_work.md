---
title: "rm -rf ? not work"
date: 2014-12-01
forum: General Help
---

### Post by daemoncesar on 2014-12-01
ls -la

```

root@myserver:/home/james/.cache/mozilla/firefox/n44420h6l.default/cache2/trash745485373# ls -la
ls: can not access 7004B63B88AB89BDFFA9D412F7E1720CECA6AEA2FA: File or directory not found
ls: can not access 305D92DFFFDCD08CB0229S246A0302724E9BBD492B2: File or directory not found
total 1136
drwxrwxrwx 2 1010 1010 1155072 Dez  1 11:12 .
drwxrwxrwx 3 1010 1010    4096 Dez  1 11:54 ..
-????????? ? ?    ?          ?            ? 7004B63B88AB89BDFFA9D412F7E1720CECA6AEA2FA
-????????? ? ?    ?          ?            ? 305D92DFFFDCD08CB0229S246A0302724E9BBD492B2?EA2FA

```

rm -rf not work !

---

### Post by ajgreeny on 2014-12-01
```
-????????? ? ?    ?          ?            ? 7004B63B88AB89BDFFA9D412F7E1720CECA6AEA2FA
-????????? ? ?    ?          ?            ? 305D92DFFFDCD08CB0229S246A0302724E9BBD492B2?EA2FA

```
That seems a very strange ls output for those two files.

Do they show if you look for them in the file-manager?  Can you right click on them and delete them that way.

---

### Post by llamabr on 2014-12-01
Question: these two files are buries way inside a hidden directory.  What did you break, or alternatively, why do you want to bother deleting them?

---

### Post by daemoncesar on 2014-12-01
I would like to create a user with the same name , and this file does not have the delete. I believe that is a problem with the partition.

Should I use fsck...I am using raid0 software...

I can not delete with no parameters .

---

### Post by ajgreeny on 2014-12-02
> **daemoncesar said:**
> I would like to create a user with the same name , and this file does not have the delete. I believe that is a problem with the partition.

Should I use fsck...I am using raid0 software...

I can not delete with no parameters .
You can't make another user with the same name as one already in existence unless you delete the existing one, and even then I am not sure if it will be possible.
However, why do you want to make another user with the same name; I can not see the point of doing this.

By all means use a live system (DVD or USB) to run fsck on the partition that contains those files using command ```
sudo e2fsck /dev/sdx#
```where sdx# is the partition, eg sda2.  You can find your partitions device names with ```
sudo fdisk -l
```from the live system.  Even if it does not solve your problem, it will do no harm.

---

### Post by daemoncesar on 2014-12-02
Always All The Servers work delete hum directory as root ....

It can only be a physical error. I'll try to fsck to see if that resolves the problem.

---

### Post by ajgreeny on 2014-12-02
> **daemoncesar said:**
> [COLOR=#ff0000]Always All The Servers work delete hum directory as root ....[/COLOR]

It can only be a physical error. I'll try to fsck to see if that resolves the problem.
What on earth do you mean by the part I show above in red?
Are you wanting to remove that folder or those files using root?  It should not be necessary as they are in your /home.  However they do not seem to have any permissions showing in your **ls -la** command, which I have never seen before, so that may be why you can not remove them as a user; root may be able to.

---

### Post by Impavidus on 2014-12-02
ls -la shows that the directory with these strange files (and it parent directory) are owned by user 1010. ls -la should show user names, not numeric user IDs, suggesting this user doesn't exist on the system. Maybe this directory was copied from a different system, preserving user ID?

---

### Post by mcduck on 2014-12-02
My bet would be filesystem error, the files aren't there any more but orphaned inodes still exist (based on *ls* giving an error that it can't find the files, even when ran as root, and all permission, ownership etc. information missing) . fsck should be able to fix that.

(good point about non-default user ID and the suer missing from the system, though, the non-standard full permissions on the parent folder also seem like they aren't from default Ubuntu setup)

---

