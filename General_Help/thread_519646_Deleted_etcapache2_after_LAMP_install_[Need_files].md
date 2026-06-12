---
title: "Deleted /etc/apache2 after LAMP install [Need files]"
date: 2007-08-07
forum: General Help
---

### Post by jrattner on 2007-08-07
Like an idiot, I accidentally deleted the contents of /etc/apache2/* after a fresh LAMP install.  Is there any way for my to get the contents of that directory back?  I just need the default folders and files and configurations that would be there right after a fresh install.

-justin

---

### Post by dreadlord_chris on 2007-08-07
reinstall Apache2
```

sudo apt-get install apache2

```

---

### Post by jrattner on 2007-08-07
But...If I already have customized files in that directory, will that over write them?

Ideally, I want my /etc/apache2 directory replaced with what would have initially been there after a fresh LAMP install.

At the same time, I do not want the contents of /var/www/ over written.

How do I accomplish this feat?

---

### Post by trak87 on 2007-08-07
In that case I believe you want to select "Mark For **Complete** Removal" in Synaptic instead of just "Mark For Removal". That should remove everything whether it's been modified or not.

You can temporarily make a backup copy just to be sure. I don't think the user contents of /var/www/ will be touched at all, but make a backup copy just to be sure:

```
cd
mkdir mywwwfiles
sudo cp -a /var/www ~/mywwwfiles
```

---

### Post by jrattner on 2007-08-07
Sounds good, I will give it a go.

---

### Post by trak87 on 2007-08-07
Oops. That code suggestion may not work when you use sudo. You might need to do this instead (replace the tilde character with the actual path of your home directory):


```
cd
mkdir mywwwfiles
sudo cp -a /var/www /home/yourlogin/mywwwfiles
```

---

### Post by dreadlord_chris on 2007-08-07
> **jrattner said:**
> But...If I already have customized files in that directory, will that over write them?

Ideally, I want my /etc/apache2 directory replaced with what would have initially been there after a fresh LAMP install.

At the same time, I do not want the contents of /var/www/ over written.

How do I accomplish this feat?

if you "accidently" deleted the files in that directory - then there's nothing there to overwrite, customized or not

the contents of /var/www won't get overwritten doing a reinstall...

---

