---
title: "Trouble Logging into Remote Desktop Server"
date: 2013-01-25
forum: General Help
---

### Post by TheMightyPuck on 2013-01-25
I am running a remote desktop server on my Ubuntu 12.04 box, and am attempting to remote desktop into it from a Windows 7 PC; however, when I attempt to do so the remote desktop on my windows machine doesn't recognize my username.  I suspect this is because the username on the server has a space in it.  (IE. John Smith)Is this indeed the issue and if so, is there a way to get it to recognize this? 

Thanks!

---

### Post by tokyo08 on 2013-01-25
maybe in the place of the space, you put a "_"

---

### Post by TheMightyPuck on 2013-01-25
I have tried both "John Smith" and John_Smith, but the xrdp login doesn't like either of those.

---

### Post by Trip4004 on 2013-02-16
You have to use your unix username and password.
If you don't know it 
Open a terminal or use ctrl+alt and type the following command

```
finger
```
if you don't have the package installed
```
sudo apt-get install finger
``` 


```
wago@something:~$ finger
Login     Name          Tty      Idle  Login Time   Office     Office Phone
wago      Wago Louage   pts/0       3  Feb 16 12:44 (:10.0)

```

And use the login this should do the trick

---

### Post by HermanAB on 2013-02-16
Hmm, never use funny characters in user names, host names or domain names.  If you do, then you will run into inexplicable issues.

---

### Post by dcstar on 2013-02-17
> **TheMightyPuck said:**
> I have tried both "John Smith" and John_Smith, but the xrdp login doesn't like either of those.

Linux usernames should not have spaces. I am surprised the system allowed you to create an account - my system refuses to add in accounts with spaces in the login name.

---

