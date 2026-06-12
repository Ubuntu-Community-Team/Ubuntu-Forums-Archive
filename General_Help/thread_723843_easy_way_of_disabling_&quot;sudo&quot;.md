---
title: "easy way of disabling &quot;sudo&quot; ?"
date: 2008-03-13
forum: General Help
---

### Post by alsac on 2008-03-13
I much prefer using the su or su - commands as opposed to "sudo". Is there a way to disable sudo altogether?

---

### Post by Joeb454 on 2008-03-13
Probably yes, but I would recommend against disabling it completely.

If you prefer to use su or su - commands then just stop using sudo :)

---

### Post by sumguy231 on 2008-03-13
You can allow yourself to become root directly by setting a root password, like so:
```
sudo passwd root
```
When you've done that and you're sure you can properly log in as root, you can disable sudo by running this command as root:
```
visudo
```
Hit insert, place a # at the front of the line that says "%admin ALL=(ALL) ALL". Press escape, type :wq, and press enter.*

*Disclaimer: I haven't done this before, it might screw something up. You get to find out for yourself.

---

### Post by alsac on 2008-03-13
Perhaps I should clarify.

I don't want to simply log in and use ubuntu as root - never do that! I always use any distro as a user, create the appropriate accounts, etc.. , but when in a shell, I prefer to use su or su - instead of sudo. So in ubuntu, am I forced to use sudo in a shell to perform a command as root, or can I somehow disable this whole concept and just use the good ol' su or su - commands when required?

Thanks for the replies.

---

### Post by rustybronco on 2008-03-13
mod's remove this post if possible please/thank you.

---

### Post by bodhi.zazen on 2008-03-13
Perhaps you want something like :

```
sudo -i
```

If you want to use su, you need to first set a root password. Then you can just remove your user from the admin group or disable root access to the admin group with visudo.

From there I suppose you could remove sudo from the system, I have not tried that on Ubuntu.

---

### Post by s.jesudasan on 2008-03-13
go to system>administration>users n groups
select root then select properties
then in the last two boxes down the bottom type some password
then close it now open a teminal and type su
give the password 
now u r the root

---

### Post by sumguy231 on 2008-03-14
> **alsac said:**
> Perhaps I should clarify.

I don't want to simply log in and use ubuntu as root - never do that! I always use any distro as a user, create the appropriate accounts, etc.. , but when in a shell, I prefer to use su or su - instead of sudo. So in ubuntu, am I forced to use sudo in a shell to perform a command as root, or can I somehow disable this whole concept and just use the good ol' su or su - commands when required?

Thanks for the replies.

My instructions will allow you to do just that. I agree, you should only log in as root when necessary. The instructions I posted simply enable the root account (necessary to use su) and disable the use of sudo.

I would instead just recommend using sudo -i, which will give you a root prompt without enabling the root account.

---

