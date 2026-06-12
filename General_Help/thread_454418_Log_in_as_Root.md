---
title: "Log in as Root"
date: 2007-05-25
forum: General Help
---

### Post by wh33t on 2007-05-25
I want to log in as root. How can I achieve this?

I am so tired of not being able to write to different drives and having to sudo everything. I find that Ubuntu is starting to work against me now instead of with me.

---

### Post by wh33t on 2007-05-25
Also... how can I turn on SSH server?

---

### Post by NeoLithium on 2007-05-25
Well, it's VERY not recommended to run as a root user, you can enable the login. 
System -> Administration -> Login Window 
go to the security tab and check the 'Allow local system administrator login'

---

### Post by Error1312 on 2007-05-25
You'll first need to set a password for the root account.
Just log in as a regular user, open a terminal and enter the following:

sudo passwd root

and enter the password you want to use for the root account. 
When that is done, on login, just enter 'root' for the username and use the password you chose to login.

---

### Post by lahook on 2007-05-29
> **Error1312 said:**
> You'll first need to set a password for the root account.
Just log in as a regular user, open a terminal and enter the following:

sudo passwd root

and enter the password you want to use for the root account. 
When that is done, on login, just enter 'root' for the username and use the password you chose to login.


can you change your root password and keep root login disabled?
for example I'm logged in as my main user, instead of sudo /program   pswd (main user password) can i   sudo /program  pswd (different than main user)
and keep it so if i type "root" in user login on boot access is denied?

---

### Post by ramjet_1953 on 2007-05-29
Where I think you are missing the point here, is that the very reason you need to access root privileges using sudo is to protect the system, not only from external sources, like the Internet, but from yourself!

Linux is very secure because of this feature. 

The reason why Windows is so insecure, is because it doesn't operate this way, unless it is set-up with log-in accounts.

This seems to be a situation where a little bit of knowledge can be dangerous. Please take the time to read-up and understand about how security works in Linux and you will realise the dangers of what you are asking.

Regards,
Roger :cool:

---

### Post by wh33t on 2007-05-29
Yea.. windows is insecure. I get it...

No offense but I can't handle my OS getting in the way. I've used windows for many years and while I used to mess it up all the time as I was learning, its very rare that ever happens now. I will treat linux the same way. The same principle applies to any computer running any os in any environment, if there is something you must 'have' on your computer, then back it up. And I always have back ups of everything. So not to worry.

---

### Post by wh33t on 2007-05-29
Oh and thank you for telling me how to login in as root.

---

### Post by ramjet_1953 on 2007-05-30
I just hope that you are not running your system as root, while you are on the Internet.

Regards,
Roger

---

### Post by wh33t on 2007-05-31
Yes I am...

---

