---
title: "Something I'm not quite clear on"
date: 2007-03-13
forum: General Help
---

### Post by ascus4 on 2007-03-13
I'm not quite clear on this.  As we all know, Ubuntu by default installs with no root account.

Suppose I install Ubuntu and I  create account1 on install and create account2 after install.

If I log on to account1 am I now logged on as 'root' with all administrative privledges or will I have to enter my password each time I do a sudo?
Do I have access to files owned by account2?

If I log on as account2 and do a sudo will it ask me for a password?  Which password would I use, 
the one for account1 because that was the install account or would I use the password for account2 because that's the account I'm currently logged on to?

I almost want to create a root account because that's what I'm used to but I read that that's not recommended.  That indicates to me that this rootless system must work.

I hope I explained this properly.  Any help is appreciated.

Thanks.

---

### Post by alamba on 2007-03-13
Hey Buddy,
When you log into account1, u're not logged in as root, but you have permission to run sudo. When you run sudo command, it will ask you for a password which would be same as account1. Now, incase of account2, it will be a "normal" user and would not have previledges to use sudo unless you put it in the appropriate group.

I'd suggest a quick search on the topic on the forum. This question has been addressed a number of times and a bit of search would lead you to all your questions above.

A

---

### Post by Kateikyoushi on 2007-03-13
Yes you enter your password each time you sudo and if the last one already expired
Why do you need two accounts ?
It will ask for password even if you make another one and have to enter that users password.

It works for every ubuntu user it took me some time to get used to it as well but nothing special.

---

### Post by qamelian on 2007-03-13
> **ascus4 said:**
> I'm not quite clear on this.  As we all know, Ubuntu by default installs with no root account.

Suppose I install Ubuntu and I  create account1 on install and create account2 after install.

If I log on to account1 am I now logged on as 'root' with all administrative privledges or will I have to enter my password each time I do a sudo?
Do I have access to files owned by account2?

If I log on as account2 and do a sudo will it ask me for a password?  Which password would I use, 
the one for account1 because that was the install account or would I use the password for account2 because that's the account I'm currently logged on to?

I almost want to create a root account because that's what I'm used to but I read that that's not recommended.  That indicates to me that this rootless system must work.

I hope I explained this properly.  Any help is appreciated.

Thanks.

The account created during the installation (account1) is automatically added to the sudoers group and can temporarily game root/admin privileges by using the sudo command. Subsequent user accounts (account2) are not automatically added to sudoers and so have not access to root/admin privileges. You would need to add the second user to sudoers in order for them to gain admin access. 

Any user in the sudoers group can use the sudo command to gain privileges. Each user in this group always uses their own account password with sudo. So account1 always uses the account1 password and account2 always uses the account2 password.

---

### Post by alamba on 2007-03-13
> **Kateikyoushi said:**
> It will ask for password even if you make another one and have to enter that users password.

Don't think that's correct. Subsequent users are not in sudoers group AFAIK.

A

---

### Post by Kateikyoushi on 2007-03-13
Okay, I will confirm this by creating another user.

---

### Post by Sef on 2007-03-13
>  Originally Posted by Kateikyoushi  View Post
It will ask for password even if you make another one and have to enter that users password.

*Don't think that's correct. Subsequent users are not in sudoers group AFAIK.*


That is not what was being said.   There will be a password set up for the new account whether it has sudo priviledges or not.

---

### Post by Kateikyoushi on 2007-03-13
That's what I meant I do not know whether the user belongs to sudoers but will check it out.

---

### Post by ascus4 on 2007-03-13
Ok, thank you all for your responses and I understand now.  I did try a search but all I kept getting was discussions as weather or not to add a root account.  I don't need two accounts but I wasn't sure how it worked so I thought I'd need one.  I see now that I don't.

I do appreciate the responses.

Cheers,

---

