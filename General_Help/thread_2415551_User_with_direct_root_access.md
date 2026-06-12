---
title: "User with direct root access"
date: 2019-03-27
forum: General Help
---

### Post by ilaurens on 2019-03-27
Hi,

My problem is that I need to upload and replace a '/etc/nginx/nginx.conf' content with my own with sFtp. However it'll give me a permission error. Which is to be expected because the logged in user 'laurens' is not the owner of the file. 
I can chmod it to 777 which is not recommended or chown the file which is in general recommended. However I want to keep that file alone to whatever permission it is. 

I want to be able to replace any file I'd like. So I wanted to create a user with root and sudo permissions. I came that far but I want the user to be logged in directly as a 'root' like login. So that I don't need to 'sudo -i' or something familiar. SFTP does not support executing a command, so I cannot use it. 

Is it possible for a sudo/root user to be logged in directly as full root without executing any commands? I can enable ssh and enable root but I want to create a seperate account for my purpose.

---

### Post by jdeca57 on 2019-03-27
If I understand your question well, you're asking if one can activate the root account in Ubuntu (you can give another user root privileges) and the answer is yes, you can do that.[https://askubuntu.com/questions/44418/how-to-enable-root-login]("https://askubuntu.com/questions/44418/how-to-enable-root-login") gives that solution and it also says it's a bad idea because it compromises security.

---

### Post by ilaurens on 2019-03-27
> **jdeca57 said:**
> If I understand your question well, you're asking if one can activate the root account in Ubuntu (you can give another user root privileges) and the answer is yes, you can do that.[https://askubuntu.com/questions/44418/how-to-enable-root-login](https://askubuntu.com/questions/44418/how-to-enable-root-login) gives that solution and it also says it's a bad idea because it compromises security.
Hey, Thanks for the fast response. If I read that one correctly it's about unlocking the root account giving it a password. 

I want to use my own account 'laurens', to be able to do what a root account can without needing to run 'sudo -i' for instance. I don't want to touch the root account.

---

### Post by ilaurens on 2019-03-28
I did read about giving the user uid or gid not sure what is was called 0 in '/etc/passwd' however that locks me out and I cannot login to that account.

---

### Post by CatKiller on 2019-03-28
> **ilaurens said:**
> My problem is that I need to upload and replace a '/etc/nginx/nginx.conf' content with my own with sFtp. However it'll give me a permission error. Which is to be expected because the logged in user 'laurens' is not the owner of the file.  
Yes. 
> So I wanted to create a user with root and sudo permissions.
No. 
> I came that far but I want the user to be logged in directly as a 'root' like login.
Don't do this.

You are misunderstanding the purpose and mechanisms of the permissions system. User and group ownership are exactly how you accomplish what you want: giving appropriate users appropriate access.

You can temporarily assume the permissions of a different user - not just root - with su. Alternatively, making the user that you log in with a member of the group that can write to those specific locations is fine, too. 

Letting anyone on the Internet write anywhere, and run anything, on your computer is not fine. Not even close.

---

### Post by The Cog on 2019-03-28
You could perhaps look at setting up password-less public key access as root (using a public/private key pair). Then you can do something like ```
scp nginx.conf root@myserver.example.com:/etc/nginx
ssh root@myserver.example.com systemctl restart nginx.service
``` without ever actually getting a root command prompt. This would not require giving root a usable password. You should password protect the private key on your laptop/PC though, to stop it being stolen and used by other people though. You can google for password-less ssh configuration. There are loads of tutorials.

---

### Post by ilaurens on 2019-03-28
> **CatKiller said:**
> Yes. 
No. 
Don't do this.
You are misunderstanding the purpose and mechanisms of the permissions system. User and group ownership are exactly how you accomplish what you want: giving appropriate users appropriate access.
You can temporarily assume the permissions of a different user - not just root - with su. Alternatively, making the user that you log in with a member of the group that can write to those specific locations is fine, too. 
Letting anyone on the Internet write anywhere, and run anything, on your computer is not fine. Not even close.

It's just a example but when you install nginx it'll have '/etc/nginx' and the files within as root. I need to use 'sudo' to make add, edit things which is right. But with sftp I cannot use a command to get elevated permissions, unfortunately. I tried to add the current user to the 'root' group however that did not help either (probably a chmod issue there).
I can use chown to force me to get the rights, but I don't want that either because suddenly stealing the rights of files is not really what I want to do. Especially for things that might be running.

I came to 'root' because it can bypass those, which is exactly what I was aiming for, of course I'm not putting everything to root access. The proxy will, but the instances it'll call will be using another user. 

> **The Cog said:**
> You could perhaps look at setting up password-less public key access as root (using a public/private key pair). Then you can do something like ```
scp nginx.conf root@myserver.example.com:/etc/nginx
ssh root@myserver.example.com systemctl restart nginx.service
``` without ever actually getting a root command prompt. This would not require giving root a usable password. You should password protect the private key on your laptop/PC though, to stop it being stolen and used by other people though. You can google for password-less ssh configuration. There are loads of tutorials.
You are right, I can just use the root user for this purpose. But I want to keep 'root' out of it also not renaming it or something familiar. 

tried to use the root account, that worked fine that's why I'm asking this question, I don't want to use the 'root' account, I want to be able to use my own account. Thanks for the tip btw :) running it with a command prompt is not a issue, I can just use sudo fine there. But when using scp does not like it and cannot elevate permissions there.

---

### Post by The Cog on 2019-03-28
> I don't want to use the 'root' account, I want to be able to use my own account. 
So scp the file to your home folder, and then "sudo cp" it from your home folder to /etc/nginx/, perhaps. Actually, that's what I often do.

---

### Post by ilaurens on 2019-03-28
> **The Cog said:**
> So scp the file to your home folder, and then "sudo cp" it from your home folder to /etc/nginx/, perhaps. Actually, that's what I often do.

That is something, I have not thought about. Though it's not exactly ideal but it's a good workaround! will think about that one!

---

