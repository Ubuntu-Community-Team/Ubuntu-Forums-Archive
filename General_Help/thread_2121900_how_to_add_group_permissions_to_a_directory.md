---
title: "how to add group permissions to a directory"
date: 2013-03-03
forum: General Help
---

### Post by andrewjs18 on 2013-03-03
I had thought it was this command: sudo chmod g+a -R directory path 

but it's not, apparently.

any help would be appreciated

---

### Post by steeldriver on 2013-03-03
what permissions do you want to add?

```

chmod g+r mydir # add read permission to members of primary group

chmod g+w mydir # add write permission to members of primary group

```

fyi 'a' is a synonym for 'all' e.g.

```
chmod a+w # add write permission for owner, group and others
```

---

### Post by andrewjs18 on 2013-03-03
> **steeldriver said:**
> what permissions do you want to add?

```

chmod g+r mydir # add read permission to members of primary group

chmod g+w mydir # add write permission to members of primary group

```

fyi 'a' is a synonym for 'all' e.g.

```
chmod a+w # add write permission for owner, group and others
```

777 would probably be best.

so if I'm reading your above code right, the last one would work best for me?

---

### Post by steeldriver on 2013-03-03
That depends... what are you trying to achieve exactly?

There's nothing stopping you from using octal permissions directly with chmod i.e. chmod -R 777 dir however it's rarely a good idea imho to recursively make all files executable to everyone; if you want to make all files and directories in dir *readable* and *writeable* to everyone then you could use

```
chmod -R a=rwX *dir*
```

[note that's a CAPITAL X] which will make all the directories rwx for owner (u) group (g) and others (o) but only give execute permission to regular files if they already have the execute bit set

Hope this helps

---

### Post by Impavidus on 2013-03-03
So you know about octal notation for permissions? Then you can simply use```
chmod 777 mydir
```
But judging from your first post you want full rights for the group applied recursively. Assuming you only want execute permissions for directories and files where someone allready has execute permission, use```
chmod -R g+rwX mydir
```
You can also set the group permissions to be identical to the owner permissions:```
chmod g=u mydir
```
Else read the manual page for chmod:```
man chmod
```

---

