---
title: "Not able to access directory of home folder"
date: 2008-02-06
forum: General Help
---

### Post by bargi on 2008-02-06
Hi,

I am trap in a strange problem........

Today when I log in to my PC I was not able to access my home folder directory .

My home folder is :
```

/home/bargi

```

When I run command :
```

cd /home/bargi

```

It show me :
```

bargi@bargi-desktop:~$ cd /home/bargi
bargi@bargi-desktop:~$ 

```

when I run ls command it show me my home folder content........

when I try to switch to directory :

```

cd /home/bargi/Test

```

It give me error :
```

bash: cd: Test: No such file or directory

```

This occurs only when I cd Test....rest of directory are easily accessible.

Last night I have created a C++ project in Test folder.

Also when I run command :

```

sudo -s

``` 

And login as root and run ls command ,it is showing the content of /home/bargi folder.....

Why this is happening ????

Is this is due to that I have created that C++ project ?????

Please help me  :(

Thanks

---

### Post by kesman on 2008-02-06
```
bargi@bargi-desktop:~$
```

The "~" at the end of that line means that you are in your home folder. To see a list of directories in the folder, type ls. If you see a directory named "Test" in there, you can access it with
```

cd Test

```
and if it's not in the list, it's not in your home -directory at all. Remember that linux directories are Case-Sensitive, which means that Test and test would be different directories.

---

### Post by bargi on 2008-02-06
Thanks for reply !

But I have take all the steps u have suggested earlier......

but still I am not able to access folder Test ......

---

### Post by kesman on 2008-02-06
post the output of
```

ls

```
run in your home-dir

---

### Post by bargi on 2008-02-06
Here is the output :
```

    Desktop    file:     nautilus-debug-log.txt  Pictures     Templates   Public    Settings  **Test **  

```

The bolded folder Test is not Accessible but  rest are .............

---

### Post by kesman on 2008-02-06
Whoops. nevermind. Try sudo cd Test

---

### Post by kesman on 2008-02-06
are you sure that Test is a directory? Maybe it's a file.

---

### Post by bargi on 2008-02-06
I run the command and output is following:

```

bargi@bargi-desktop:~$ sudo  cd Test
sudo: cd: command not found

```

Test is a directory.

```

drwxr-xr-x 4 bargi bargi   4096 2008-02-05 21:31 Test

```

Thanks

---

### Post by IcemanV9 on 2008-02-06
Try this ...
```
file Test
```
If it is a directory, then make sure you own the directory to be able to access ...
```
ls -l
```
If the directory is not owned by you, then type ...
```
sudo chown bargi:bargi Test
```

---

### Post by bargi on 2008-02-06
I am the owner of that folder as it clear from my previous post.............

Thanks

---

### Post by IcemanV9 on 2008-02-06
Yes. I can see that as we post our responses at the same time. Anyway, your $PATH might be the problem ...
```
cd: command not found
```
The basic $PATH should be like this ...
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
```
If there are some missing in your $PATH, then type ...
```
export PATH=$PATH:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
```

---

### Post by bargi on 2008-02-06
Hey I solve the problem........

The problem was due to the space ......... Actually I have given a single space after naming 

"Test(Space) ".......When I remove this space it runs.............

But I am confused that in linux it should show me Test folder like this :

```

cd Test\ /

```

If there is space in name. ............????????

Thanks IcemanV9 for your Time :)

---

### Post by IcemanV9 on 2008-02-06
Space?! Man. It really does give you a wild goose chase to resolve the problem! :)

Anyway, you can rename it to Test[without space!].
```
mv Test\  Test
```

---

