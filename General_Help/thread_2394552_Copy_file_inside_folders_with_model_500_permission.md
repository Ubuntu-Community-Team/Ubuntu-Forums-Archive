---
title: "Copy file inside folders with model 500 permissions between computers"
date: 2018-06-18
forum: General Help
---

### Post by sed_faster on 2018-06-18
Hello,

I have this structure folders:
```

/folder1/test.txt

user@192.168.1.1:/server/folder2/

```

Both folders has 500 permissions and I intend copy file test.txt from my computer to the other user's computer. how should I do? I am thinking use scp with this parameters "-rvp" but I tried execute this command but don't copy anythings. The scripts returns which I have not permissions to execute this command. That's why I tried execute this command wich root, but the result it is the same! What I do wrong?

Thanks

---

### Post by TheFu on 2018-06-18
500 ---->   r-x------ .... so you cannot write to it.  root can't write when there aren't any write permissions either.

Please post the EXACT command you want and the EXACT, full, permissions on both systems with the current userids.

---

### Post by sed_faster on 2018-06-19
Thanks to your reply.

On pc1 I have a folder with permissions 500. I have this permissions because I need guarantee which I don't delete any file accidentally. But I need do backup of this folder and related files inside. I want ensure which in pc2 this folder will stay a same type permissions (500). 

To solve, temporarily, the issue, I copied the folder inside the pc1 to another location inside pc2 and after I did command mv, as sudo, to folder inside pc2.

---

### Post by TheFu on 2018-06-19
Well, hard to get rsync working correctly with those permissions for maintaining a mirror, but if it works.
I don't have **any** directories with 500 permissions. IMHO, sorta defeats the purpose.  I'd use a read-only mount, if that was what I wanted.  It is fun to see hackers frustrated on a website because none of the files can be modified due to read-only mounts.

If solved, please mark the thread solved to help others.

---

### Post by sed_faster on 2018-06-20
I never heard about "read-only mount" I execute this command:
```

sudo mount -o ro /dev/sdb4 /home/user/folder/
or
sudo mount -r /dev/sdb4 /home/user/folder/

```
And I was testing the directory and this is awesome! :) I need read more about the program "mount".

Thanks

---

### Post by TheFu on 2018-06-20
Unix is a big world. Hard to know what we don't know.
Solved?

---

### Post by sed_faster on 2018-06-20
The big truth :)
Yes, solved, thanks

Edit: where can I close the thread?

---

### Post by slickymaster on 2018-06-20
> **Edgar_Oliveira said:**
> The big truth :)
Yes, solved, thanks

Edit: where can I close the thread?

Being so please scroll to the top of the thread and look for the Thread Tools menu item on the right of the toolbar, click it to produce a dropdown menu and select the "Mark this thread as solved" option.

---

### Post by sed_faster on 2018-06-20
Thanks everybody

---

