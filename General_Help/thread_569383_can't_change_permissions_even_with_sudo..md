---
title: "can't change permissions even with sudo."
date: 2007-10-07
forum: General Help
---

### Post by kdizle on 2007-10-07
Here is the setup:
I am a teacher who asked my district to rack and install a moodle server.  The district IT person decided to use unbuntu which sounded good because I have heard so much.  I have previously used RH, drake  and suse.
The server has an outside ip that resolves but all the links point to an internal ip address.I figure go to config.php in the moodle directory.
My IT guy says the sudo pasword is $$$$$, but I have read that ubuntu password is my regular password.  when I try
```
chmod 777 config.php
```

I am told permission denied, so I try:
```
sudo chmod 777 config.php
```
and nothing happens!

questions:
1.  What can I do to vim this file?
2.  Since I have been given what he is calling the sudo password $$$$$ can I use this some way?
3.  What do I need to get from my IT guy I can do this?

Thank you for any help.

---

### Post by taurus on 2007-10-07
The second command, "sudo chmod 777 config.php", only change the permissions of file config.php so what do you expect to happen when you run that command?

If you look at the listing of that file, you would see that everybody has read/write/executable permissions.

```
ls -la config.php
```
I assume you know that vim is just a text editor.  So, if you want to edit config.php, run it with

```
sudo vim config.php
```

---

### Post by kdizle on 2007-10-07
I am sorry I should have made that clear.

When I type in: "sudo chmod 777 config.php" and nothing happens, I mean it shows the next shell prompt and doesn't say any errors or anything but the file reamins in 640 not the new 777 I wanted.

I have tried sudo vim config.php but the smae thing happens the editor does not open just another shell prompt.

---

### Post by taurus on 2007-10-07
What happen if you run

```
su -
```
and use the password that your IT told you to use?

---

### Post by kdizle on 2007-10-07
> **taurus said:**
> What happen if you run

```
su -
```
and use the password that your IT told you to use?

I get Authentication failed

I assume that is related to root being turned off?

---

### Post by bettlebrox on 2007-10-07
777 permissions on any file is bad as anyone could write or write the file. What are the current permissions on the file?

---

### Post by taurus on 2007-10-07
Do you belong to groups adm & admin?  What release are you using?

```
id
```

Looks like you may have to talk to your IT again to see exactly how you would change and edit system files.

---

### Post by kdizle on 2007-10-07
> **bettlebrox said:**
> 777 permissions on any file is bad as anyone could write or write the file. What are the current permissions on the file?

I just want to change it long enough to edit the file.

---

### Post by kdizle on 2007-10-07
> **taurus said:**
> Do you belong to groups adm & admin?  What release are you using?

```
id
```

Looks like you may have to talk to your IT again to see exactly how you would change and edit system files.

uid=1001(***) gid=1001(***) groups=1001(***)

Thanks for the help.

---

### Post by anaconda on 2007-10-07
Looks like you dont belong to the admin group.

---

