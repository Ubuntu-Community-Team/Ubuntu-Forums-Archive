---
title: "How do I setup my account so that I can access files owned by www-data?"
date: 2007-10-06
forum: General Help
---

### Post by initialxy on 2007-10-06
Hello everyone!

I have apache server and PHP running on my computer and I wrote a simple PHP upload script for file sharing purpose. The files uploaded by my PHP script is owned by the user www-data and my default user account was not able to access them. The last i can do is change the permission of these uploaded files but i find that kind of annoying. Is it possible to set up my default account so that it can access files owned by www-data?

Thanks!

---

### Post by DagMan on 2007-10-07
Perhaps theres an option to add yourself to the same group if it exists as one.
I would say to just add the group ownerships of the folder so you can access it but I don't know if that would work out with files being uploaded from elsewhere.

---

### Post by initialxy on 2007-10-07
Thanks for you reply.
unfortunately that didn't work. I was able to change the folder that contains the uploads to the same user group as my default account. but newly uploaded files are still www-data user group. So I'm still unable to access uploaded files normally.

---

### Post by DagMan on 2007-10-07
Is there by chance a group that is web or www-data or apache that you aren't a part of?  I'm just brainstorming btw.  I've never had a reason to run apache.

---

### Post by initialxy on 2007-10-07
I checked all the existing users and user groups. I can't find www-data anywhwere. I also added myself to all the existing user groups but still no luck.

---

### Post by X-626 on 2007-10-07
You will have to add yourself to the www-data group through the terminal.  I'm not sure why it doesn't show up in the groups listing.  The command for this is:
```
sudo adduser username www-data
```Substitute "username" for your own user name.
Within the PHP file itself, you could also use the function "chmod" to change the file permissions of the uploaded file to whatever you want.

---

### Post by initialxy on 2007-10-08
> sudo addusr username www-data 
didn't work out for me, i don't know why. it seemed to be perfecty reasonable..
but i used exec(); in my php script to change the permission of the uploaded file to 777. and that worked out perfectly.

Thanks!

---

