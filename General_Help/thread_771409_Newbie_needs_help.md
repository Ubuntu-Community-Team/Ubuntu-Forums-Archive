---
title: "Newbie needs help"
date: 2008-04-27
forum: General Help
---

### Post by gabrielshier on 2008-04-27
Hello,
Just recently moved to try and use linux. I am currently using an Ubuntu 8.4 on a Lenovo by Dell. The general things are quite easy to catch up to, even devices managment and use managment. But i can't seem to figure out how do i install new programs that are not on the Add/Remove list. 
There are three type of files i don't know how to install. The first one is quite a big .sh file. The Ubuntu does not know how to open it when i double click it and i dont know what to do. Another type of file is a tar.gz. In that specific file i just decompressed it and then opend the Install file. Only none of the three commands that were listed didn't work. they were:


```
./configure
make
make install
```

How do i install such a thing? Are there some parameters that i need to type or a certain location it needs to be copied to?

Waiting for an answer,

Thanks,
Gabriel

---

### Post by TeoBigusGeekus on 2008-04-27
1) An .sh file is a script file. Right click it and make it executable. Then double click it and Ubuntu will give you the option to execute it or display its contents. Alternatively, navigate to the script's folder 

```
cd /path/to/folder
```

and execute it with

```
sh script.sh
```

2) A .tar.gz file is a compressed archive. You decompress it, say on your Desktop, and you then navigate in it.

```
cd /home/yourusername/Desktop/decompressedfolder
```

Once inside, you type

```
./configure
```

so that the compiler can check for dependencies. If you get an error message after this command, don't worry: not all source packages have a configure script.

You then type

```
sudo make
```

and after you give your password the source code will be compiled.

Finally, you type

```
sudo make install
```

and your application will be installed. You should see an entry for it in the applications menu or you can launch it with a terminal command, refer to software's documentation for that.

---

### Post by smoker on 2008-04-27
>  But i can't seem to figure out how do i install new programs that are not on the Add/Remove list. 

just a suggestion, did you check if the applications were in the 'synaptic package manager?' if so, to install is just a tick in a box, and apply!

if the apps are not in the repositories of synaptic, see if there is a 'deb' package available in the download page of whichever app. .deb's should install easily with a double-click!

---

