---
title: "Separating OS and user &quot;stuff&quot;"
date: 2021-06-06
forum: General Help
---

### Post by anneranch on 2021-06-06
Separating OS and user "stuff"  -** link to discussion wanted. **
( i really di not know what to put in "search " ) 
There was / is a thread discussing how to physically separate OS files from user stuff AFTER  it was initially "associated  / downloaded  ". 
For example - if I install  application XYZ  in /home/app XYZ  can it be moved to /media/MYStuff   without destroying  the OS "packages" . ?

---

### Post by ajgreeny on 2021-06-06
I'm not at all sure what you are asking here but you can certainly have a separate /home partition in which all your "stuff" will go, separate from the OS itself.

However a lot will depend on what you mean by "stuff", for example, you can probably not install application XYZ in /home/app/XYZ as all applications and packages are installed in the OS and not in your home.

There are a few exceptions to this but as a new user I suspect doing things this way will be more confusing to you than useful, so would advise against doing so.
In theory you could download the archived version of firefox direct from Mozilla to your home Download folder, and after extracting the folder from the archive it is possible to run firefox direct from the executable in the extracted folder.  But why bother? It does not make life any easier for you but complicates things.

---

### Post by grahammechanical on 2021-06-06
How about searching the internet for "Linux file structure explained?" We get this

[https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/](https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/)

[https://www.linux.com/training-tutorials/linux-filesystem-explained/](https://www.linux.com/training-tutorials/linux-filesystem-explained/)

Keep in mind that when we download an application is has been packaged into a compressed/archive  file. We then use a package manager to uncompress the package into its many libraries and scripts which are then distributed into the many directories/folders in the OS part and the User part  of the operating system.

It is possible to extract the contents of a application package archive into the folder it is in but that would not be the same as installing the application. Applications in Windows come with a Setup.exe or Install.exe file that does the installing. I do not think Linux applications come with an install executable file like that. They most probably have an install script or text file that the package manager makes use of.

I do have a little knowledge of the windows file structure from Windows DOS to Windows 98 days. I know nothing about the file structure used by Apple Corp for its computer operating systems.

Regards

---

### Post by oldfred on 2021-06-06
You can have all the data, Documents, Videos, Music, etc folders that are normally in /home in a data partition and link those folders back into /home, so it still looks like standard, but data is actually in another partition, either same or different drive. I also move some hidden folders in /home like Firefox & Thunderbird profiles, so only the user configuration files are still in /home, so it is tiny. And then I keep it in same partition as / .

[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

