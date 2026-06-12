---
title: "shutdown without password"
date: 2006-11-19
forum: General Help
---

### Post by wiz561 on 2006-11-19
Hi,

   I'm trying to get my dapper box to shutdown without a password, but can't do it.  I've added the following to the /etc/sudoers line (the shutdown command, that is)...


# User privilege specification
root    ALL=(ALL) ALL
ALL     ALL=NOPASSWD:/sbin/shutdown

  But when I try to shutdown, I still get an error.

<me>@chorizo:~$ sudo /sbin/shutdown -r now
Password:
<me>@chorizo:~$ 
@chorizo:~$ /sbin/shutdown -r now
shutdown: you must be root to do that!


   Argh!  What am I doing wrong?  Any help is appreciated.


Thanks in advance.

---

### Post by ajgreeny on 2006-11-19
If you want to do it in terminal try *sudo shutdown -r now,*  ie get rid of the sbin bit of your command, it certainly works for me if ever I need to use it eg when I have to reboot because the xserver has gone toes up.

---

### Post by wiz561 on 2006-11-19
damn...  i tried it and it still asks for a password!

---

### Post by DaveBorealis on 2006-11-19
> **wiz561 said:**
> damn...  i tried it and it still asks for a password!

It's asking for the password because of the 'sudo'.  Try it without:
```
/sbin/shutdown -r now
```

Dave

---

### Post by ajgreeny on 2006-11-20
Oh yes. Of course it does!
Sorry I was not thinking fast enough, and I have to admit I thought root was the only way to shutdown in terminal mode, though when you consider that you need no password to shutdown using the desktop icons, it makes sense that users can do it as well.  I'll now get my brain trained to think before I reply to questions that I believe I know the answer to.

I've now just tried the /sbin/shutdown/ -r now and it tells me that this is only possible for root, so still no further forward.

---

### Post by wiz561 on 2006-11-20
Yup, if I do sudo it asks for a password; if I just do /sbin/shutdown -r now, it says that I must be root...but yet I added the stuff to the sudoers file.

Any other ideas?

Thanks!

---

### Post by dbott67 on 2006-11-20
Just throwing out ideas here:

**_[COLOR="Red"][SIZE="6"]WARNING: POTENTIAL SYSTEM HOSING AHEAD[/SIZE][/COLOR]_**

What if you chown the **/sbin/shutdown** command to your user account?

-Dave

---

