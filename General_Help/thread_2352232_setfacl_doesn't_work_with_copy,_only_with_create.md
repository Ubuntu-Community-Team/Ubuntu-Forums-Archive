---
title: "setfacl doesn't work with copy, only with create"
date: 2017-02-10
forum: General Help
---

### Post by opus1 on 2017-02-10
I've read dozens of forums and tutorials on setfacl for the last few days and still have this fundamental problem. It seems all the stuff I've read about setfacl deals with creating files/dirs and not with copying them.

The situation is: I want a share directory on my home network for the kids to drag and drop files in and out of. 
[LIST]
[*]I created a dir called "xfer" on a drive that is shared with the rest of the network with NFS
[*]All users on the network belong to the "allusers" group that I created
[*]All users on all computers have a umask of 0007
[*]I initiallly did a "sudo chmod 777 xfer"
[*]I set the setuid bit using this command: ```
sudo chmod g+ws xfer
```
[/LIST]
So, when I do a ls -l on the directory I get: ```
drwxrwsrwx   7 bob   allusers  4096 Feb 10 12:29 xfer
```
Then I set the facl like this:```
sudo setfacl -Rdm g:allusers:rwx xfer
```
and now ls -l shows  ```
drwxrwsrwx+   7 bob   allusers  4096 Feb 10 12:29 xfer
```
and getfacl shows:```
# file: xfer
# owner: bob
# group: allusers
# flags: -s-
user::rwx
group::rwx
other::rwx
default:user::rwx
default:group::rwx
default:group:allusers:rwx
default:mask::rwx
default:other::rwx

```
with this setup all my users can create files with permissions of rw-rw---- (660), as I would expect.  Here's the thing I don't understand.  If the user has a file in their home directory like this:
```
-rwx------  1 mark mark       0 Feb 10 13:50 ZMarksFile
```
and then copies it into the shared directory (xfer) using thunar, it shows up in the shared directory as:
```
-rwx------+ 1 mark allusers  0 Feb 10 14:08 ZMarksFile
```
Shouldn't it have been forced to have permissions of rw-rw---- (660)? If not, how do I make that happen?  The way it works now doesn't lend itself to being an effective shared directory! I'm really pulling my hair out and haven't found any solutions on the internet.

---

### Post by Keith_Helms on 2017-02-11
Copy maintains the file permissions unless you explicitly tell it not to with --no-preserve=mode.

I don't think you really have a problem.  If you do a 
```
getfacl ZMarksFile
```
it should show something like 
```
group:allusers:rwx            #effective:---
```
If you sign in with some other ID that is a member of allusers and then do a
```
rm ZMarksFile
```
you should see
```
rm: remove write-protected regular file 'ZMarksFile'?
```

So basically even though the regular permissions got copied as is, under the covers the ACL permissions are being applied to the file.

---

### Post by opus1 on 2017-02-11
Ah.. OK, so it is a "copy" thing and not an "ACL" thing. I moved a file from the "mark" account into the xfer directory using the --no-preserve=mode option and it achieved what I wanted.  Trouble is: how do I make that default?  My kids are all under 10 and they know how to drag and drop using Thunar, but I can't ask them to use the command line all the time. I suppose I could make a custom action in Thunar (something like "copy to share"), but I thought there might be a "built-in" way to achieve this.  Doesn't sound like it.

---

### Post by Keith_Helms on 2017-02-11
If your kids aren't doing anything to create files with permissions 700 or 600 then it should't be a problem.  Are they using some application that sets file permissions to something other than the umask default?

---

### Post by opus1 on 2017-02-17
You're right -- they aren't doing any thing that would create those permissions.  I set their umasks to 0007. I checked my son's homework downloads from his school website and they were coming down rw-------, so I set the defaults to g:mark:rw with setfacl, and that seems to have fixed that problem.

So, I'll set this as solved (since there isn't a "wasn't a problem in the first place" option). Thanks for your help!

---

### Post by opus1 on 2017-02-17
You're right -- they aren't doing any thing that would create those permissions.  I set their umasks to 0007. I checked my son's homework downloads from his school website and they were coming down rw-------, so I set the defaults to g:mark:rw with setfacl, and that seems to have fixed that problem.

So, I'll set this as solved (since there isn't a "wasn't a problem in the first place" option). Thanks for your help!

---

