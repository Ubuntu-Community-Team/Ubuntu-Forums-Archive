---
title: "Using Windows shared printer without password"
date: 2007-12-27
forum: General Help
---

### Post by buttari on 2007-12-27
Hi,
I am trying to use a Windows shared printer through Samba. However, at the end of the printer configuration I always get asked a password like this:

[IMG]http://icl.cs.utk.edu/~buttari/stuff/screen.png[/IMG]

I assume that this is the password for user "buttari" on the linux box but it doesn't work. There is no need for a passwd to access the windows box (and in fact I can print without providing any passwd from a third windows box). I can also access the shared folders from my linux box without any problems (and passwd).
Can anybody help me with this?
Thanks

alfredo

---

### Post by zarqoon on 2007-12-27
Perhaps you have to provide the smbpassword which you may not have set yet.
Try to set it with
```
sudo smbpasswd buttari
```
and then try that password

---

### Post by buttari on 2007-12-27
> **zarqoon said:**
> Perhaps you have to provide the smbpassword which you may not have set yet.
Try to set it with
```
sudo smbpasswd buttari
```
and then try that password

Nope, didn't work. If I got it right, that should be the passwd used to access the linux box from a windows one, right?
Thanks

alfredo

---

### Post by zarqoon on 2007-12-27
It could also be the lp password that is needed to make changes in cups
you can set that with
```
sudo lppasswd -a buttari
```

---

### Post by buttari on 2007-12-27
> **zarqoon said:**
> It could also be the lp password that is needed to make changes in cups
you can set that with
```
sudo lppasswd -a buttari
```

Nope, not even this one worked.
Thanks

alfredo

---

### Post by zarqoon on 2007-12-27
you could try to manually add the printer to cups using the cups interface
type [http://localhost:631/](http://localhost:631/) into your browser to get to it.
I've never actually done this before so iam not sure how or if it works but the printer adress should be smb://ipOrHostname/printername

---

### Post by buttari on 2007-12-27
> **zarqoon said:**
> you could try to manually add the printer to cups using the cups interface
type [http://localhost:631/](http://localhost:631/) into your browser to get to it.
I've never actually done this before so iam not sure how or if it works but the printer adress should be smb://ipOrHostname/printername

Ok, I tried this. Now at the end of the configuration I get asked for a username and passwd like this:
[IMG]http://icl.cs.utk.edu/~buttari/stuff/screen2.png[/IMG]

Note that I set a passwd as suggested by zarqoon with
```
sudo lppasswd -a buttari
```

so I put "buttari" as username, the passwd I set but it doesn't work. This is frustrating.
Thanks

Alfredo

---

### Post by zarqoon on 2007-12-27
hmm i use gutsy and i didnt set any additional password but for me the user/pass of my usual account works fine in this context.
Is your user member of the group lpadmin?
Dont exactly know if its the right one but it looks right.
you can check it by typing id in the console.

---

### Post by buttari on 2007-12-27
> **zarqoon said:**
> hmm i use gutsy and i didnt set any additional password but for me the user/pass of my usual account works fine in this context.
Is your user member of the group lpadmin?
Dont exactly know if its the right one but it looks right.
you can check it by typing id in the console.

Zarqoon,
it worked. Actually the user wasn't in the lpadmin group. Adding it did the trick. 
Thanks a bunch

Alfredo

---

