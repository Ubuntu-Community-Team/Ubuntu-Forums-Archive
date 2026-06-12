---
title: "How do you use terminal in this situation ?"
date: 2008-07-10
forum: General Help
---

### Post by myromance123 on 2008-07-10
"Open a terminal to the directory where you downloaded the file."

  That is what I must do to install this program I downloaded. The programs called Alice.  Im wondering how to do the above, everything else I should be okay with.

  These are the full instructions on that website for installing :

> Linux-only instructions (Thanks, Charles!):

Alice needs 250MB of free space.
Please have opengl drivers and a Java Runtime Environment([http://www.java.com/en/](http://www.java.com/en/)).

Download the file Alice-2.0.0.tar.gz.
Open a terminal to the directory where you downloaded the file.
Run the command: tar xvfz Alice-2.0.0.tar.gz then run: cd Alice/Required then run: ./run-alice


  Thanks for any help ~

---

### Post by chalewa on 2008-07-10
ok so say you downloaded the file to 

/home/your_username/alice

then at the terminal you would do:

```
cd /home/your_username/alice
```

or if the file is a subdirectory of your home folder, you can just do 

```
~/alice
```

---

### Post by Gunman1982 on 2008-07-10
Click on "Applications->System->Console" thats your "terminal/console" it starts in your home folder, now cd to the folder where you saved the Alice...tar.gz file. In example if you have it on the desktop execute 'cd Desktop' <- keep in mind that linux is case sensitive.

---

