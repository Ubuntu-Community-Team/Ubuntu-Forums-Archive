---
title: "How to run script as superuser for mounted iso?"
date: 2012-10-23
forum: General Help
---

### Post by rsq on 2012-10-23
I'm running 12.10 and relatively new to Linux.

I have some software in .iso format that I need to mount and install. I first mounted it using Furius ISO mount. I then went to the terminal and went to the directory with the install file (which we'll call 'install). 

Permissions are set by:
```

-r-xr-xr-x

```so it should be fine to run. Indeed, if I type: 
```

./install

```it executes fine, but the installer gives me an error "You may need to be logged in as root to continue". 

So I try
```

sudo ./install

```and it returns (after asking for password)
```

sudo ./install: command not found

```

---

### Post by Stonecold1995 on 2012-10-23
You probably typed something in incorrectly, it should run as root when you do that.

Did the script vanish or move somewhere when you first ran it?  Because this might happen if it deleted itself...

---

### Post by rsq on 2012-10-23
> **Stonecold1995 said:**
> You probably typed something in incorrectly, it should run as root when you do that.

I don't think so. It's a five character difference between 
```

./install

```which works. And 
```

sudo ./install

```which does not.

I may be clueless, but I don't see how I could have messed up those 5 characters in "sudo[space]".

---

### Post by Stonecold1995 on 2012-10-23
Maybe try this:
```
sudo -i
cd /path/to/installer
./install
```

Or try (if it's a bash script):
```
sudo bash install
```

---

### Post by rsq on 2012-10-23
> **Stonecold1995 said:**
> Maybe try this:
```
sudo -i
cd /path/to/installer
./install
```Or try (if it's a bash script):
```
sudo bash install
```

The second immediately gave me a "Permission denied". 

I tried the first, and after 
```

sudo -i

```this seemed to log me into username "root". However, I was unable to cd into the mounted directory (located at ~/mountediso). Permissions of the directory was literally: 
```

d?????????

```from using ```
ls -l
```

---

### Post by Stonecold1995 on 2012-10-23
```
chmod a+x install
```

---

### Post by rsq on 2012-10-23
> **Stonecold1995 said:**
> ```
chmod a+x install
```

Without sudo? 

```
chmod a+x install
```

returns 

```
chmod: changing permissions of 'install': Function not implemented
```

and using 
```
sudo chmod a+x install
```

first asks me for a password, then gives 
```
chmod: cannot access '/install': Permission denied
```

---

### Post by Stonecold1995 on 2012-10-24
Hmm.  I've never tried changing permissions for files in an ISO, so I'm really not too sure how to go about doing this.  Have you tried extracting the contents of the ISO to you hard drive and run the script from there?

---

