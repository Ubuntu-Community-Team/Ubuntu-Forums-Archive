---
title: "Help creating a new login/admin PW"
date: 2007-08-11
forum: General Help
---

### Post by Chappy7777 on 2007-08-11
I have a 4 letter password that is used for login and any time I need to do something in admin (unless it's only been a few minutes since I last typed it in).

Can you please tell me how to change my login/admin password as it has been made clear as I have searched thru these forums for a few hours now that I should have made it at least 9 digits long, not 4?  The logic behind this is clear enough. Since the likelyhood of someone physically attempting to get into this machine is ziltch, it's the hackers I need to keep out.

Make it as ez as possible as I am fairly new at this.

---

### Post by Chappy7777 on 2007-08-11
> **Chappy7777 said:**
> I have a 4 letter password that is used for login and any time I need to do something in admin (unless it's only been a few minutes since I last typed it in).

Can you please tell me how to change my login/admin password as it has been made clear as I have searched thru these forums for a few hours now that I should have made it at least 9 digits long, not 4?  The logic behind this is clear enough. Since the likelyhood of someone physically attempting to get into this machine is ziltch, it's the hackers I need to keep out.

Make it as ez as possible as I am fairly new at this.
==============================================
Please note that I spent quite a bit of time looking thru old threads that speak about passwords and other admin probs. Most in regard to creating a Root PW. I could not find what I needed or I would not have started another thread. If the answer is "out there", I didn't see it.

Sorry.

---

### Post by meierfra on 2007-08-11
Type

```
passwd
```

in the terminal.

Enter your current password. After that you need to enter your new password twice.

---

### Post by EXCiD3 on 2007-08-11
You see, anytime you need to "do something in admin" you are actually entering the Root password. If you follow those posts to change the root password that would change that part. Now for your login password, im not really sure, but you could create a new account and then login to that account and see if you can delete the old one...Surely there is some better way of doing that.

And seriously, i doubt someone would hack your computer since you are running linux. Windows users are the main targets as they are the ones prone to spyware/adware and can allow hackers to enter much easier than Linux users. Thank god for linux!

---

### Post by Chappy7777 on 2007-08-11
> **meierfra said:**
> Type

```
sudo passwd
```

in the terminal.

Enter your current password. After that you need to enter your new password twice.
================================
Meierfra, thnx for the tip. This looks very close to the same commands that are used to create a root PW, I assume as I do as you say, I'll see that I am changing my admin PW and not creating a root pw. Correct?

---

### Post by meierfra on 2007-08-11
> I assume as I do as you say, I'll see that I am changing my admin PW and not creating a root pw. Correct?

Yes 

Edit: Now that I did edit  my previous post, it   does not create a  root passwd.

---

### Post by meierfra on 2007-08-11
Also be aware that your admin password ( that is the password you use for sudo)  is the same as your login password.

---

### Post by meierfra on 2007-08-12
Maybe this is less confusing:

In the main menu go to:

System -> Administrator ->Users and Groups

Select your account.

Click on Properties.

Enter your new password under "user password" and under "confirmation"

Click "ok"

---

### Post by Chappy7777 on 2007-08-20
> **meierfra said:**
> Type

```
sudo passwd
```

in the terminal.

Enter your current password. After that you need to enter your new password twice.
===================================================
I tried the above and for some reason it did not work. (I know that when I type in a password here I will not see anything). 

I just tried the System/admin/users/  and changed my PW, confirmed it and hit OK. I haven't done anything yet that requires typing a PW, but when I do I'll let you know if it worked. In the users page it listed Root as a user and my username that I log in with. I assume I was to change the PW under my ID, not under Root. It's a little confusing since it has a much longer row of dots in the PW line than are needed for my ID. And under Root it has PW dots, but I have no Root PW. Kinda confusing.

---

### Post by meierfra on 2007-09-13
I  just  learned  in another thread why "sudo passwd" did not work. The correct command is "passwd" and not "sudo passwd". To make matters worse if you use "sudo passwd" it establishes a password for root. I know that you asked  me about that at the time,  but  I was absolutely convinced  that it changed the   user password.  (passwd changes  the password of the current user, but "sudo" causes "root" to be the current users.)

I'm very sorry about that and can only hope that it did no cause any harm. Please disable the  root password via

```
sudo passwd root -l
```
( the l is a lower case L)

---

### Post by Bothered on 2007-09-13
> **meierfra said:**
> but  I was absolutely convinced  that it changed the   user password.

You were thinking of "sudo passwd [user]", which can be used to change the password of any user.

---

### Post by meierfra on 2007-09-13
Kind of.  But I knew that if you leave out [user] it  change the  password of the current user. What I didn't  think about is that "sudo" changes the current user to "root".
Also I didn't realize that passwd works without sudo.


So maybe to be on the safe  side one  should always use "sudo passwd user_name"

---

