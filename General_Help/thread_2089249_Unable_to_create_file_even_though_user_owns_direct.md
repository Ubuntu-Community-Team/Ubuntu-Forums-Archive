---
title: "Unable to create file even though user owns directory?"
date: 2012-11-28
forum: General Help
---

### Post by Axman84 on 2012-11-28
Hi all,

I cannot figure out this issue and I would really appreciate some help: I have created a user "MyUser" belonging to group "MyUser", and my problem is that MyUser gets permission denied error when attempting to create a file in its own directory.

I created the user like this:
```
sudo adduser --system --group --home /var/lib/MyUser MyUser
```

Now I did a 
```
sudo chown -R MyUser:MyUser /mnt/nas/Users/MyUser
``` 
and
```
ls -al /mnt/nas/Users/MyUser
``` tells me that MyUser user and group owns the dir and its subdirs:
```
drwxrwxr-- 2 MyUser MyUser 4096 Nov 28 21:58 MyDir
```

As you saw above, MyUser is created as a system user, and I think that is part of the problem perhaps? I attempt to create a file as MyUser and get an error:
```
sudo -u MyUser touch /mnt/nas/Users/MyUser/test
```
```
touch: cannot touch `/mnt/nas/Users/MyUser/test': Permission denied
```

Can anyone help me figure out what is going on here?

Thanks!

Im on Ubuntu x64 12.10.

---

### Post by papibe on 2012-11-28
Hi Axman84.

4th code snippet is not exactly the result of the 3rd.

Could you post the result of this command?
```
ls -ld /mnt/nas/Users/MyUser
```
Regards.

---

### Post by MythosLegend on 2012-11-28
> **Axman84 said:**
>  tells me that MyUser user and group owns the dir and its subdirs:
```
drwxrwxr-- 2 MyUser MyUser 4096 Nov 28 21:58 MyDir
```

As you saw above, MyUser is created as a system user, and I think that is part of the problem perhaps? I attempt to create a file as MyUser and get an error:
```
sudo -u MyUser touch /mnt/nas/Users/MyUser/test
```
```
touch: cannot touch `/mnt/nas/Users/MyUser/test': Permission denied
```


'/mnt/nas/Users/MyUser/' has read, write, and execute.

What about the permisions of directory 'mnt/nas/Users/MyUser/test'?

---

### Post by Axman84 on 2012-11-29
> **papibe said:**
> Hi Axman84.

4th code snippet is not exactly the result of the 3rd.

Could you post the result of this command?
```
ls -ld /mnt/nas/Users/MyUser
```
Regards.

No you're right, it was just an excerpt. Here is the output you request:

```
drwxrwxr-- 6 MyUser MyUser 4096 Nov 28 21:58 /mnt/nas/Users/MyUser/
```

---

### Post by Axman84 on 2012-11-29
> **MythosLegend said:**
> '/mnt/nas/Users/MyUser/' has read, write, and execute.

What about the permisions of directory 'mnt/nas/Users/MyUser/test'?

"test" is just the file I am trying to create. "MyUser" has rwx on all subdirs of the "MyUser" dir..

---

### Post by pkadeel on 2012-11-29
> **Axman84 said:**
> I created the user like this:
```
sudo adduser --system --group --home /var/lib/MyUser MyUser
```Now I did a 
```
sudo chown -R MyUser:MyUser /mnt/nas/Users/MyUser
```and
```
ls -al /mnt/nas/Users/MyUser
``` tells me that MyUser user and group owns the dir and its subdirs:
```
drwxrwxr-- 2 MyUser MyUser 4096 Nov 28 21:58 MyDir
```As you saw above, MyUser is created as a system user, and I think that is part of the problem perhaps? I attempt to create a file as MyUser and get an error:
```
sudo -u MyUser touch /mnt/nas/Users/MyUser/test
``````
touch: cannot touch `/mnt/nas/Users/MyUser/test': Permission denied
```Can anyone help me figure out what is going on here?

Thanks!

Im on Ubuntu x64 12.10.
man pages say about adduser
```
By default, system users are placed in the nogroup group.  To place the new system user in an already existing group, use
       the --gid or --ingroup options.  To place the new system user in a new group with the same ID, use the --group option.
```
According to this, your user is a system user with name MyUser group MyUser but is not added to any other group. Then you are using sudo which fails because your new user is not a member of "sudo" group. for that you need another command before doing sudo on behalf of MyUser
```
sudo adduser MyUser sudo
```

---

### Post by Axman84 on 2012-11-29
> **pkadeel said:**
> man pages say about adduser
```
By default, system users are placed in the nogroup group.  To place the new system user in an already existing group, use
       the --gid or --ingroup options.  To place the new system user in a new group with the same ID, use the --group option.
```
According to this, your user is a system user with name MyUser group MyUser but is not added to any other group. Then you are using sudo which fails because your new user is not a member of "sudo" group. for that you need another command before doing sudo on behalf of MyUser
```
sudo adduser MyUser sudo
```

Oh ok, I see. But I do not want MyUser to be in the sudo group. The program that the MyUser is dedicated to gets write permission errors in the /mnt/nas/MyUser dir, that is why I am debugging this.

How can I try to create a file as MyUser without it being in the sudo group?

---

### Post by pkadeel on 2012-11-29
> **Axman84 said:**
> Oh ok, I see. But I do not want MyUser to be in the sudo group. The program that the MyUser is dedicated to gets write permission errors in the /mnt/nas/MyUser dir, that is why I am debugging this.

How can I try to create a file as MyUser without it being in the sudo group?
By logging in as MyUser.
because you can not create a file in his home dir being a normal user and if you use your own sudo then the file will be created as a root user so if you do not want MyUser to be a member of sudo group then the two options are

[LIST=1]
[*]to login as MyUser.
[*]create a file as your own sudo then chown that file to MyUser (but I don.t think this is what you want so you only have one option)
[/LIST]

---

### Post by Axman84 on 2012-11-29
> **pkadeel said:**
> By logging in as MyUser.
because you can not create a file in his home dir being a normal user and if you use your own sudo then the file will be created as a root user so if you do not want MyUser to be a member of sudo group then the two options are

[LIST=1]
[*]to login as MyUser.
[*]create a file as your own sudo then chown that file to MyUser (but I don.t think this is what you want so you only have one option)
[/LIST]

I can't log in as MyUser because its a system user account dedicated to a program, thats the point.

So I have no options?

---

### Post by pkadeel on 2012-11-29
> **Axman84 said:**
> I can't log in as MyUser because its a system user account dedicated to a program, thats the point.

So I have no options?
After my post I got a second thought and found that even if you make your new user a member of sudo and then use his sudo permission to create a file, that file will again not be owned by the MyUser but it will be owned by root which you will need to chown back to MyUser so why not use your own sudo create a file then chown it back to MyUser. That will be as good as logining in as MyUser and then creating a file.

Or Else trust```
drwxrwxr-- 2 MyUser MyUser 4096 Nov 28 21:58 MyDir
``` and proceed to next step.

---

### Post by Axman84 on 2012-11-29
> **pkadeel said:**
> After my post I got a second thought and found that even if you make your new user a member of sudo and then use his sudo permission to create a file, that file will again not be owned by the MyUser but it will be owned by root which you will need to chown back to MyUser so why not use your own sudo create a file then chown it back to MyUser. That will be as good as logining in as MyUser and then creating a file.

Thanks, I'll try it.

---

### Post by Axman84 on 2012-11-29
> **pkadeel said:**
> After my post I got a second thought and found that even if you make your new user a member of sudo and then use his sudo permission to create a file, that file will again not be owned by the MyUser but it will be owned by root which you will need to chown back to MyUser so why not use your own sudo create a file then chown it back to MyUser. That will be as good as logining in as MyUser and then creating a file.

Or Else trust```
drwxrwxr-- 2 MyUser MyUser 4096 Nov 28 21:58 MyDir
``` and proceed to next step.

I was able to create a file as sudo, sudo chown it to MyUser:MyUser, and move it into the MyUser owned dir, but I don't really see how that helps me here.. Still stuck.

Does anyone have anything else I can try?

---

### Post by pkadeel on 2012-11-30
> **Axman84 said:**
> I was able to create a file as sudo, sudo chown it to MyUser:MyUser, and move it into the MyUser owned dir, but I don't really see how that helps me here.. Still stuck.

Does anyone have anything else I can try?

[LIST=1]
[*] Ok re-analyse the whole scenario.
[*]You have a user MyUser
[*]You have a program which is run by MyUser
[*]You have a folder owned by MyUser and the program wants to write a file in that folder
[*]The folder permissions are set 0775 yet you get permission denied error.
[/LIST]
Question1: what is the whole path in which this folder resides?
Question2: Are the folder permissions on all the parent folders in the path have 0755?

---

