---
title: "Script for a AD domain user"
date: 2008-07-08
forum: General Help
---

### Post by ic3000 on 2008-07-08
Hello to all,

I'm using Ubuntu connected to a Windows 2003 server AD domain with Winbind!

Until now everything is working ok and i can do everything the windows users do on my network.

I can manualy connect to my network shares as my documents and department folders.

Some colleagues are asking to put on there workstation fedora and i'm trying to write a script to help them connect to the network sahres.

My problem is that if on the script i use $USERNAME to get the users username i finish with DOMAIN\username.

Is there a way that i can use on a script to make a variable only with the username leaving the DOMAIN\ behind?

Thanks in advance!

---

### Post by justleen on 2008-07-08
im not sure if i get this correctly.. you use the variable $USERNAME, which gives you back "domain\username" and you only need the username?

you can use "who" and "whoami" to get the usernames as well.

to strip the domain bit, i'd use sed..
```

usern=`echo $USERNAME|sed 's|DOMAIN\||'`
echo $usern

```

---

### Post by ic3000 on 2008-07-08
Thanks justleen!

When i try you sugestion i get the following error:

> sed: -e expression #1, char 12: unterminated `s' command

Do you know what could be the problem?

Thanks once more for your reply!

---

### Post by justleen on 2008-07-08
ohw, duh

\ is a special char that need to be escaped
[code]
usern=`echo $USERNAME|sed 's|DOMAIN\\||'`
usern=`echo $USERNAME|sed 's#DOMAIN\\##'`
usern=`echo $USERNAME|sed 's/DOMAIN\\//'`

[code]

the last lines just as an example to sed's substitute. You may use any char for it
sed 's/searchstring/replacestring/'
i preffer pipes.. (unless there are pipes in what ever i search/replace..)
sed 's|searchstring|replacestring|'



sorry.. getting carried away..

---

### Post by ic3000 on 2008-07-08
Thanks again justleen!

I tried the 3 examples you gave but still got the same error on the 3!

I really dont have a clue on what could be wrong...

Thanks once more!

---

### Post by ic3000 on 2008-07-08
I found that i have to use one more \ for it to woks!

Once againt Thank you alot justleen!!

---

### Post by ic3000 on 2008-07-11
Here i am boring you guys again!

Im trying to put this script to work on the users login and i was able to do it puting a Default file on /etc/gdm/ ...but sometimes using this i really dont know why the system dont let the users login... sometimes i does sometimes it wont... its very strange for me... but if i remove the file i can always login to the domain or to localhost.

I was researching and before i use it on fedora that this could be acomplish also by puting the sript i need on /etc/init.d...

I tried this with ubuntu and it wont work... on fedora it does but on Ubuntu it wont...

Is there a diferent way to do thid on ubuntu?

Where do i have to put a script that i need to run on users login?

Thanks once more!

---

### Post by Dougie187 on 2008-07-11
Hello,
as far as i know,
/etc/init.d scripts shouldn't be mapped to login, even on fedora. Those should be mapped to start up. If you want to do login scripts, you should put them in
/etc/profile or /etc/profile.d

Also, here is another post about login script in ubuntu.

[http://ubuntuforums.org/showthread.php?t=439354](http://ubuntuforums.org/showthread.php?t=439354)

Hope that helps!

---

### Post by ic3000 on 2008-07-11
duh!!

You are right... that was it... it was my mistaque and was driving me crazy about it...

It works ok using profile.d directory to put my scripts!

Thanks alot Dougie187!!!

A bit off topic but still on bash scripting... The script  is using mount.cifs to access a share on a w2k3 server, and it works but i still have a problem here!

When using mount.cifs on ubuntu i get in some sirectory and files a codification error for special characters like ~, ç etc...

If i use smb://servername/sharename to access the share on the w2k3 server i can see all the files and folders with proper charset encoding but when i tried to use mount.cifs i finish with the enconding problem for special characters...

Is this a problem or limitation with mount.cifs on Ubuntu?

I tried to use iocharset=utf8 and iso8859-a but the result is the same...

The same script using sbin/mount.cifs on fedora i get the right enconding...

the command i use is mount.cifs //servername/sharename /localdirectorytomountshare

Any clue on what could be wrong here?

Thanks again!

---

### Post by Dougie187 on 2008-07-11
im not sure about that one. You might make a seperate post just about this. you might get more traffic that way.

---

