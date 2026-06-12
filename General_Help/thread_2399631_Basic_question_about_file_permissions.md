---
title: "Basic question about file permissions"
date: 2018-08-27
forum: General Help
---

### Post by southof40 on 2018-08-27
I should know this but ... it appears I don't.

```
drwx------  2 ubuntu golf  4096 Aug 28 00:45 permstesttemp
drwxrwxr-x  2 ubuntu golf  4096 Aug 28 00:46 permstesttempalt
```

... they are in ... 

```
/home/ubuntu
```

... In those directories are two files ...
```

~$ ls -l ./permstesttemp
-rw-rw-r-- 1 ubuntu ubuntu 0 Aug 28 00:45 pm.txt

~$ ls -l ./permstesttempalt/
-rw-rw-r-- 1 ubuntu golf 0 Aug 28 00:46 pm.txt

```

... I have a user romeo who is a member of the golf group ...

```

$ id romeo
uid=1001(romeo) gid=1001(romeo) groups=1001(romeo),27(sudo),1002(golf)

```

I have python program which is run by romeo and attempts to read those files but when that program tries to open them it reports a permission error for both files.

It seems to me that the while a permission error is understandable for the first one I don't understand why the second file (in permtesttempalt) isn't able to be read by user romeo

```

import os

COREDIR = '''/home/ubuntu'''

def main():
    filename = "pm.txt"
    filepath = os.path.join(COREDIR, 'permstesttemp', filename)
    filepathalt = os.path.join(COREDIR, 'permstesttempalt', filename)

    for fpath in [filepath, filepathalt]:
        print("About to read {0}".format(fpath))
        try:
            with open(filepath, 'r') as f:
                print(f.read)
        except PermissionError:
            print("Encountered PermissionError when trying to  read {0}".format(fpath))


if __name__ == "__main__":
    main()


```

I'm sure the reason is obvious ... would someone be kind enough to explain ?

---

### Post by HermanAB on 2018-08-28
Note that there are two layers of permissions that are not visible or usable with ls and chmod/chown: 
Access Control Lists and AppArmor.

---

### Post by southof40 on 2018-08-28
> **HermanAB said:**
> Note that there are two layers of permissions that are not visible or usable with ls and chmod/chown: 
Access Control Lists and AppArmor.

OK , good point, I hadn't thought about Access Control Lists however it does seem that's not significant here 

```
$ getfacl pm.txt
# file: pm.txt
# owner: ubuntu
# group: golf
user::rw-
group::rw-
other::r--

$ getfacl ./permstesttemp/pm.txt
# file: permstesttemp/pm.txt
# owner: ubuntu
# group: ubuntu
user::rw-
group::rw-
other::r--

$ getfacl ./permstesttempalt/pm.txt
# file: permstesttempalt/pm.txt
# owner: ubuntu
# group: golf
user::rw-
group::rw-
other::r--
```

As to AppArmor I'm not familiar with it . I presume to apply it to a python script it would actually have to be applied to python itself ? I looked in /etc/apparmor.d and what I can see doesn't seem to match either the shell or python so I don't think that's signficant here.

Thanks for your response, I appreciate it.

---

### Post by The Cog on 2018-08-28
Has the process that is running the script logged out and in again since being made a member of the group? You only pick up your changed group membership as you log in.

---

### Post by sisco311 on 2018-08-28
The user also needs execution access (+x) on /home and /home/ubuntu. ;)

---

### Post by southof40 on 2018-08-28
*Has the process that is running the script logged out and in again since  being made a member of the group? You only pick up your changed group  membership as you log in.*

Thanks I have now logged off and logged on but that, unfortunately, didn't fix it ! Thanks for your help.

(Edited to fix up the results of typing too fast).

---

### Post by southof40 on 2018-08-28
> **sisco311 said:**
> The user also needs execution access (+x) on /home and /home/ubuntu. ;)

Can I just check that we're on the same page ? The python script which I quoted in the original post is being run by romeo from /home/romeo/src/permstest . Given that's the situation does romeo still need execution access on /home and /home/ubuntu ?

Thanks for your response.

---

### Post by sisco311 on 2018-08-28
Yes. Because the file he wants to access is in /home/ubuntu. Right?

---

### Post by southof40 on 2018-08-28
> **sisco311 said:**
> Yes. Because the file he wants to access is in /home/ubuntu. Right?

Yes that's correct and I hadn't appreciated that without execution access on the directories all the from '/' a user can't get to the file. Thanks.

However this probably indicates that what I'm doing is just plain a bad idea because to allow user 'romeo' (who is a member of group 'golf') to read a file 

```
/home/ubuntu/permstesttempalt/pm.txt
```

It seems to me I have to either allow 'all' execution rights on /home and /home/ubuntu (doesn't sound like a great idea) or I have change the group associated with /home and /home/ubuntu to 'golf' and then tweak the group perms for /home and /home/ubuntu. Well changing the groups associated with those two directories is (I'm almost certain) a bad idea so I guess I should be moving the file to somewhere which is more commonly accessible ?

---

### Post by HermanAB on 2018-08-28
Execution access on a directory means something else - kindof 'cd and browse' access on the directory:
[https://unix.stackexchange.com/questions/150449/what-does-execute-permission-mean-on-a-folder](https://unix.stackexchange.com/questions/150449/what-does-execute-permission-mean-on-a-folder)

When applying permissions to directories on Linux, the permission bits have different meanings than on regular files:
    The read bit allows the affected user to list the files within the directory
    The write bit allows the affected user to create, rename, or delete files within the directory, and modify the directory's attributes
    The execute bit allows the affected user to enter the directory, and access files and directories inside
    The sticky bit states that files and directories within that directory may only be deleted or renamed by their owner (or root)

---

### Post by sisco311 on 2018-08-29
You are on the right track regarding file permissions. 

And, IMO, you have to rethink your concept about your project. 

&#8220;The miracle is this - the more we share, the more we have.&#8221; In other words we need more info... :)

---

### Post by southof40 on 2018-08-29
Very clear , thank you. It explains to me some behaviour I have noticed while moving around directories but never quite understood. Thanks again.

---

