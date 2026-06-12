---
title: "Password Protect Folders/Files"
date: 2007-05-20
forum: General Help
---

### Post by BlkMagik07 on 2007-05-20
Hey everyone.

I was just wondering if there was a way (preferably an easy way) of password protecting files and folders in Ubuntu.  I have very sensitive/important files on my PC that need to be protected since I let my younger siblings use my PC all the time.  

Thanx.

---

### Post by Bachstelze on 2007-05-20
Just chmod them to 000, it will then require root access to view them.

---

### Post by joe.turion64x2 on 2007-05-20
> **BlkMagik07 said:**
> Hey everyone.

I was just wondering if there was a way (preferably an easy way) of password protecting files and folders in Ubuntu.  I have very sensitive/important files on my PC that need to be protected since I let my younger siblings use my PC all the time.  

Thanx.
Give them their own user account. Unless they get  the root password they won't be able to see your files.

Joe.

P.D. Make sure you make your home folder private.

---

### Post by mbradlcu on 2007-05-20
here's a little script that encrypts files,, note the meat of the script is
```
openssl enc -aes-256-cbc -salt -in $1 -out $1.enc
```
replace the $1 with the file name if you don't want to use the scripts.

magic_encoder_ring:
```
#!/bin/bash

## secret squirrel approved

openssl enc -aes-256-cbc -salt -in $1 -out $1.enc

echo "Secret Squirrl asks: Do you want to remove the source document? (y/n)"
read ANSWER

if [ "$ANSWER" = "y" ]
then
    rm -iv $1
    echo "****Removing  File****"
else
    echo "File was not deleted"
fi

if [ -e $1 ]
then
    echo "!!!files still exists!!!"
fi

```

now here's the script to decode the file for reading: again if you want to do it manually use:
```
openssl enc -d -aes-256-cbc -in $1 -out $1.txt
``` 

magic_decoder_ring:
```
#!/bin/bash

## secret squirrel approved

openssl enc -d -aes-256-cbc -in $1 -out $1.txt
less $1.txt
echo "do you want to remove this file? (y/n)"
read ANSWER
if [ "$ANSWER" != "n" ]; then
echo "****Removing Decripted File****"
rm $1.enc.txt
fi
if [ -e $1.enc.txt ]
then
    echo "!!! something's wrong,, files still exists!!!"
fi

```

if anyone has a way to do this without writing the the output to a temp file please let know!
thanks!

---

### Post by Ufo on 2007-05-26
One way to hide information from unauthorized access is to use encfs.
From its man page:

encfs creates a virtual encrypted filesystem which stores encrypted 
data in the rootdir directory and makes the unencrypted data visible at the mountPoint directory.  The user must supply a password which is used to (indirectly) encrypt both filenames and file contents.

---

### Post by timzak on 2007-05-30
> **HymnToLife said:**
> Just chmod them to 000, it will then require root access to view them.

Is there a way to do this and have it ask for the password?  I just did a chmod 000 to a folder I'd like to keep secure and all it does is tell me > You do not have the permissions necessary to view the contents of.  I would like the password box to pop up so I just type my root password and pop into the folder.

Can this be done?

Thanks.

---

### Post by nikhilk on 2007-05-30
Where is this particular folder you are trying to secure? Is it in your "home" directory or somewhere else? You got the permission error while doing a chmod or after it?

---

### Post by timzak on 2007-05-30
> **nikhilk said:**
> Where is this particular folder you are trying to secure? Is it in your "home" directory or somewhere else? You got the permission error while doing a chmod or after it?

Sorry for not being clear.  The folder is a sub-folder of a desktop folder.  Ie, residing on my desktop is a folder called Documents.  Within that folder are standard documents as well as another folder called Secure Documents.  From the terminal, I cd'd to inside the Documents folder then typed "chmod 000 Secure Documents".  There was no error message here.  In fact, it appeared to work because when I tried to open the Secure Documents folder, I received the message: > You do not have the permissions necessary to view the contents of Secure Documents

What I'd like is for the password box to pop up, allowing me to type my password and enter the folder

Hopefully that's more clear.

Thanks.

---

### Post by timzak on 2007-05-30
[http://ubuntuforums.org/showthread.php?t=410513&highlight=password+protect](http://ubuntuforums.org/showthread.php?t=410513&highlight=password+protect)

Here's another thread on this topic that pretty much sums it all up.  Thanks for everyone's help here for myself as well as the topic starter.

---

