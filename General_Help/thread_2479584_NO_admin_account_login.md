---
title: "NO admin account login"
date: 2022-09-29
forum: General Help
---

### Post by jacksonguitars on 2022-09-29
Dear sirs and ladies!
I moved my Ubuntu hard drive to a new computer. A more modern computer.
Now I cannot login to my admin account if I've already logged in to my reguar user account.

If i restart the computer. Then I may login to my admin account. But not otherwise.

any great ideas would be greatly appreciated.

---

### Post by grahammechanical on 2022-09-29
I am confused. In all the years I have used Ubuntu and I have installed it many times and I have never known Ubuntu to have an Admin account and a User account. I have known Debian and other distributions to require the setting up of both an Admin account and a User account.

On Ubuntu if we try to do something that requires administrator privileges the operating system will present a dialog box where we can put in our password. If we are using a command line terminal we preface the command with sudo and then enter our password when requested to do so. For a brief period we become the administrator and then revert to being a standard user.

I understand that distributions that require both an Admin account and a User account it is required to log out of one account in order to log in to the other account. 

Please explain.

Regards

---

### Post by HermanAB on 2022-09-30
With most Linux distributions , the first user account that you create is the admin account.  Most users leave  it at that  and only ever create a single account.  

If you create more accounts and you want to give admin privileges to them, then you need to edit  the sudoers file. This is best left till you know more about Linux in general - next year.

---

### Post by jacksonguitars on 2022-10-01
I cant login to my admin acoount after logging into my regular user account, after switching my ubuntu OS to a new computer with newer hardware. On my old hardware it worked fine

---

### Post by QIII on 2022-10-01
So ... Are you saying that previously you would create two users for yourself, an Admin and a regular user?

Is this important to you, given that when you install your OS the first user created is already an admin type and can gain near-root access using sudo without having to have a separate admin user?

An explanation of your use-case might be helpful here.  You certainly have a right to do as you please with your machine, but you are talking about a common misconception that is something most of us would never do.

---

### Post by The Cog on 2022-10-01
It would clarify things for us if you could, in each account, use the command **id** and post the results. 
Feel free to change the actual usernames if you want to keep them secret, but then use them consistently in subsequent posts.
This sounds very unusual, so we may have to do a lot of fishing to find out what's going on.

---

### Post by TheFu on 2022-10-01
> **jacksonguitars said:**
> I cant login to my admin acoount after logging into my regular user account, after switching my ubuntu OS to a new computer with newer hardware. On my old hardware it worked fine

Can you 'su - {other user}'?

---

