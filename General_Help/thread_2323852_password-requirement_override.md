---
title: "password-requirement override"
date: 2016-05-08
forum: General Help
---

### Post by geomcd1949 on 2016-05-08
I used 14.04 and could (and did) set any password I pleased.

16.04 requires a long password.

Is there a way to override the long-password requirement and set the password I choose?

I'm not worried about anyone getting into the computer.

Thanks.

~George

---

### Post by mc4man on 2016-05-08
The orig. install user can still use anything, can be 1 character. Any additional users are forced into some Gnome dev nonsense...
Anyway the password of any user can be changed to anything, any length with - 
 ```
sudo passwd [COLOR="#0000CD"]username[/COLOR]
```
where blue is the usename whose password you want to reset. After running above you'll get a prompt to set password, ect.

---

### Post by geomcd1949 on 2016-05-08
No joy, mc4man

I am the only user of this 16.04 only computer. My  username is "George." When I type sudo passwd George into the terminal  and hit ENTER, I get: passwd: user 'George' does not exist.

What am I doing wrong???

---

### Post by geomcd1949 on 2016-05-08
When I type "passwd" into the terminal and hit ENTER, I get

Changing password for owner.
(current) UNIX pasword:  

I type my current password.

I get: Enter new UNIX password:

I type my new preferred password.

I get: Retype new UNIX password.

I type again my new preferred password.

I get: You must choose a longer password

---

### Post by mc4man on 2016-05-08
Works fine here (16.04 Ubuntu)  - ex. changed my 1 char. pass to a 2 char. pass & then back to orig. 1 char. pass, no mention of length
> doug@doug-Lenovo-IdeaPad-Y510P:~$ sudo passwd doug
[sudo] password for doug: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
doug@doug-Lenovo-IdeaPad-Y510P:~$ sudo passwd doug
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
doug@doug-Lenovo-IdeaPad-Y510P:~$ 

---

### Post by geomcd1949 on 2016-05-08
Also tried: sudo passwd

Got: [sudo] password for owner:

Entered my old password

Got: Enter new UNIX password:

So I did

Got: Retype new UNIX password:

So I did again

Got: passwd: password updated successfully

However, whern I try to use the new password for a terminal "sudo" operation, it tells me "Sorry, try again.

And, the OLD password is accepted.

---

### Post by geomcd1949 on 2016-05-08
mc4man - I notice that the text in your terminal is

doug@doug-Lenovo-IdeaPad-Y510P:~$

Mine is 

owner@User:~$

So I tried 

sudo passwd owner

then followed your directions, and was able to change my password.

Thank you very much!

---

### Post by mc4man on 2016-05-08
> **geomcd1949 said:**
> mc4man - I notice that the text in your terminal is

doug@doug-Lenovo-IdeaPad-Y510P:~$

Mine is 

owner@User:~$

So I tried 

sudo passwd owner

then followed your directions, and was able to change my password.

Thank you very much!
Then your username is " owner "

---

### Post by geomcd1949 on 2016-05-09
Truedat! But I'm wondering where "George" came from? 

In the screen for signing in, there are "George" and "Guest." Nothing for "owner."

Anyway, thanks again!

~Geo.

---

### Post by Impavidus on 2016-05-09
> **geomcd1949 said:**
> When I type "passwd" into the terminal and hit ENTER, I get

Changing password for owner.
(current) UNIX pasword:  
...
I get: You must choose a longer passwordThis is the user setting his own password. It appears that there is a minimum password length.

> **mc4man said:**
> doug@doug-Lenovo-IdeaPad-Y510P:~$ sudo passwd doug
[sudo] password for doug: 
Enter new UNIX password: First user "doug" uses his own password to get root permissions. Next the root user sets the password for user "doug". There is no minimum password length.

> **geomcd1949 said:**
> Also tried: sudo passwd

Got: [sudo] password for owner:

Entered my old password

Got: Enter new UNIX password:

So I did

Got: Retype new UNIX password:

So I did again

Got: passwd: password updated successfully

However, whern I try to use the new password for a terminal "sudo" operation, it tells me "Sorry, try again.

And, the OLD password is accepted.First the user "owner" uses his own password to get root permissions. Then the root user sets his own password. Your own password indeed didn't change, but you did set a root password, which by default doesn't exist. If you wish (and it's more secure, but with an insecure password for a sudo user it doesn't matter much), you can disable the root login again using```
sudo passwd -d root
```Authenticate using your own password.

> **geomcd1949 said:**
> Truedat! But I'm wondering where "George" came from? 

In the screen for signing in, there are "George" and "Guest." Nothing for "owner."

Anyway, thanks again!

~Geo.
"George" is your full name, "owner" your username.You must have set it up like that when you installed. If you look at the file /etc/passwd (you can open it in a text editor), you can see a list of users of your system. Most of these will be non-login users, created to run various services in a secure way. It should contain a line with your username and your full name, along with some other details.

---

### Post by geomcd1949 on 2016-05-09
Thanks very much, Impavidus. A complete  explanation.

~George

---

