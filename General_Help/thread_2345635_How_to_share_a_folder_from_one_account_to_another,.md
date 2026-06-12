---
title: "How to share a folder from one account to another, same pc?"
date: 2016-12-06
forum: General Help
---

### Post by javierdl on 2016-12-06
I want my wife to have access to my Pictures folder. How do I get this done?

Thanks guys :)

---

### Post by Jeroen_Mathon on 2016-12-06
Hey Javierdl,

You can achieve this by using groups in Linux.
You simply change the ownership of your pictures folder to your new group.

Lets say we have 2 users.
User1 = john
and user2 = bob

John owns the ./Pictures folder but wants bob to be able to look but not modify any data in that folder.
This can be achieved by using the chmod and chown tools.

Simply run ```
chmod -R 750 ./Pictures
``` to set the permissions of that folder so that the group that owns that folder can only look and the owner has full rights.

Then you can create a group using groupadd, lets call it pictures ```
groupadd pictures
``` we now add bob and john to pictures using ```
for i in bob john ; do gpasswd -a $i ; done
``` Now all we need to do is change the owner of the pictures folder recursively. we can do this using ```
chown -R john:pictures ./Pictures
```

John is your user and bob is your wife.

Now if you want your wife yo have full access you'd need to use the permission 770 instead of 750.

I hope that this can get you started.

---

### Post by TheFu on 2016-12-06
Do you want read-write or read-only access?

---

### Post by Morbius1 on 2016-12-06
> **TheFu said:**
> Do you want read-write or read-only access?
I have a follow up to that important question: Is your home directory encrypted?

The reason for asking is that your wife should already have read access to your Pictures folder.

---

### Post by TheFu on 2016-12-06
I usually put shared directories outside /home/ just to ensure that if a user leaves the company and someone decides to wipe their directory, an important shared directory isn't included in the wipe.  But that's just me.

Good question about the encryption, @Morbius1.  Another reason to move shared directories outside an individual's HOME.

Also, after setting up the directory, forcing the setgid bit on all subdirectories will ensure the shared group is maintained for newly created files, not the default group(s) of each individual.  That's a **chmod g+s**. Don't just do that recursively - do it only for directories, not files.

---

### Post by javierdl on 2016-12-06
This is great! Thanks a bunch guys :)
Namely JM for the step-by-step instructions :)
I'll give it a try tonight.


JDL

---

### Post by SeijiSensei on 2016-12-07
One convenience you might provide your wife is a "symbolic link" to your Pictures folder in her home directory.

```

cd /home/wife
sudo ln -s /home/javier/Pictures "Javier's Pictures"

```

Use "cd /home/wife/Pictures" if she'd prefer to have the link in her Pictures directory.  Do this after your fixed the permissions and whatnot following the advice above.

---

### Post by javierdl on 2016-12-25
Thank you for this SS, very convenient indeed.
Sorry I took so long to reply,

JDL

---

### Post by javierdl on 2017-01-02
JM,

Just to gain a better understanding of the second command line...
I didn't see the name of the group in this command line: "```
[COLOR=#000000][FONT=&amp]for i in bob john ; do gpasswd -a $i ; done[/FONT][/COLOR]
```"
Does this mean that it is implied that we are inside that new group when we execute this command line?

Other than that, I looked into what "i" is for, but I only found this: 
[COLOR=#111111][FONT=Ubuntu]"*sudo -s runs a shell with root privileges. **sudo -i **does this as well, but also acquires the root user's environment.*" But it might not be quite the same.
Could you explain how "i" is used here then?

Thanks,

JDL[/FONT][/COLOR]

---

### Post by TheFu on 2017-01-02
'i' is assigned from bob and john, one at a time. This is a loop. Basic programming. This assumed your shell is bash. This is a bash script construct.
To access the value held inside 'i', the $i is used.  For compactness, he wrote it as a 1 line script, but normally, it would be seen like this:
```

for i in bob john 
do
  gpasswd -a $i
done
```

I would have written it this way:
```
gpasswd -a bob
gpasswd -a john
```which results in exactly the same results.

To understand the gpasswd command, probably best to look at the man page - **man gpasswd**.  You can look at the manpage for almost any command - bash, ssh, sudo.  Many config files also have manpages - sudoers.  Options don't often mean what we assume they do across different commands. It is best to check what they mean using the manpage for each command to be certain.

For example, **sudo -i** has specific behaviors (gets root's env) which may or may not be desirable.  **sudo -s** has slightly different behavior (keeps YOUR userid's env) which is sometimes more what we want, but not always.  Sometimes we want **sudo -H**, which sets the HOME for root, not your userid.  And where can you learn what each of these options does?

---

### Post by Keith_Helms on 2017-01-02
> **javierdl said:**
> JM,

Just to gain a better understanding of the second command line...
I didn't see the name of the group in this command line: "```
[COLOR=#000000][FONT=&amp]for i in bob john ; do gpasswd -a $i ; done[/FONT][/COLOR]
```"
Does this mean that it is implied that we are inside that new group when we execute this command line?

Other than that, I looked into what "i" is for, but I only found this: 
[COLOR=#111111][FONT=Ubuntu]"*sudo -s runs a shell with root privileges. **sudo -i **does this as well, but also acquires the root user's environment.*" But it might not be quite the same.
Could you explain how "i" is used here then?

Thanks,

JDL[/FONT][/COLOR]

I believe the missing group name was a typo and the command should have been
```
[COLOR=#000000][FONT=&amp]for i in bob john ; do gpasswd -a $i **pictures**[/FONT][/COLOR][COLOR=#000000][FONT=&amp]; done[/FONT][/COLOR]
```

---

### Post by TheFu on 2017-01-03
Yep. I didn't check the **gpasswd** manpage either. Clearly.  I've never used that command.  Find it easier to edit the /etc/group.gshadow file(s) directly (or modify the groups in LDAP).

---

