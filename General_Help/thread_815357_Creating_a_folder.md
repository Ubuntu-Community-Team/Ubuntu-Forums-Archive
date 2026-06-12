---
title: "Creating a folder"
date: 2008-06-01
forum: General Help
---

### Post by ministry on 2008-06-01
How do you create a folder in Linux, if I right click to add one the option is "greyed" out and I get the same result when I go to File and click on it .
I am trying to add a folder for screenlets  in the following path....usr/local/share/screenlets. 

Any help would be appreciated, thanks in advance :confused:

---

### Post by RATM_Owns on 2008-06-01
In terminal:
```
mkdir foldername
```

---

### Post by Ciego on 2008-06-01
Open up your terminal  ...

```
mkdir /usr/local/share/screenlets
```

---

### Post by OliverW on 2008-06-01
> **ministry said:**
> How do you create a folder in Linux, if I right click to add one the option is "greyed" out and I get the same result when I go to File and click on it .
I am trying to add a folder for screenlets  in the following path....usr/local/share/screenlets. 

Any help would be appreciated, thanks in advance :confused:

You get a greyed out option because you don't have permissions to write in /usr/local/share/* as the current user.
If you need the screenlets just for yourself, you can make a directory in your home directory called '.screenlets' (if it's not already there) and extract your screenlets specific stuff there.

If you need to be system wide available you can open the file manager via the terminal typing 'sudo nautilus'. This will start the file manager with admin rights, and then you should be able to create a directory in /usr/local/share.

---

### Post by sisco311 on 2008-06-01
```
sudo mkdir /usr/local/share/screenlets/**foldername**
```You need to create the folder as super user.
To copy files to the folder:
```
sudo /path/to/dir/* /usr/local/share/screenlets/[B]foldername
```

[/B]* - all the files from the directory

Or open the file browser as super user(root). Press Alt+F2 and type:
```
gksu nautilus
```

---

### Post by ministry on 2008-06-03
Thanks to everyone for the input will try them out

---

