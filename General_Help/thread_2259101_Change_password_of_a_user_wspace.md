---
title: "Change password of a user w/space"
date: 2015-01-02
forum: General Help
---

### Post by mczacierka on 2015-01-02
I have a problem with changing a password of my one user. Ive been through root and tried to change it in recovery mode, but i had no luck. The main problem i am having is that my username has a space in it and i cannot change the password due to it. when i type in root: "passwd Insurgency Server". I get the error saying cannot find the user "Insurgency" (My username is Insurgency Server btw). What could i substitute the space with? I've tried a forward slash inbetween and that did not work.
Any help?
Thanks,
      Mike.

User: Insurgency Server
password: Unknown?????

---

### Post by TheFu on 2015-01-02
Welcome to the forums!

I doubt that is really the userid.  Linux/UNIX systems make it hard to enter a userid with a space.  Also, all userids are lowercase.  This isn't Windows.

First - check what the real userid is - look inside the /etc/passwd file - I bet "iserver" is the real userid and "Insurgency Server" is the *user's full name*.  That is used just for display, not anywhere else and not for logins.
You can also run ** env |grep USER**, which should return the name (but strange environment setups _could_ change that.

Assuming that you somehow got 2 words into the userid field (wow!), the best, long-term, answer is to change the userid into a 1 word userid, all lowercase, and between 2 and 50 characters long.  The 50 characters is my crazy guess at length, I don't know if there is a length limit or not off the top of my head.

The passwd manpage (section 5) specifies what each field in the /etc/passwd contains.

---

### Post by Hadaka on 2015-01-02
Here ya go..
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

try an underscore instead of a space as in....new_name

---

### Post by Impavidus on 2015-01-02
+1 to the above.

In general, if you want to pass an argument containing a space to some command, you have to escape the space using a backslash or quote the argument in either single or double quotation marks. There is a difference between them, which will not be of importance until you start bash scripting.```
hello\ world
"hello world"
'hello world'
```

---

