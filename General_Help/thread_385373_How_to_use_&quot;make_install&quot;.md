---
title: "How to use &quot;make install&quot;?"
date: 2007-03-15
forum: General Help
---

### Post by AnthonyJK@gmail.com on 2007-03-15
[http://ubuntuforums.org/showthread.php?t=215801](http://ubuntuforums.org/showthread.php?t=215801)

from this post how exactly do I go about installing his program

he says:

now install my program
1) unpacking tar
2) make sure you have installed a libgtk2.0-dev and libvte-dev
packages
3) enter into a src directory
4) execute - sudo make install
Now you have a macbook-backlight-control program into /usr/bin/
I suggest to add it to startup-application in a system-preferences-sessions menu.


what does "enter into a src directory" mean and how do I "execute - sudo make install"

I tried just entering sudo make install into terminal but it returns with an error:

make: *** No rule to make target `install'.  Stop.

Thanks in advance!

---

### Post by zvacet on 2007-03-15
It means 
```
cd /program_folder/src
```
```
- sudo make install
```

---

### Post by peabody on 2007-03-15
By src folder he probably meant the folder the tarball extracted to.  This is typically (though not always) the name of the tar file minus the .tar.gz extension.  For example, I would use the following commands from the command line to extract a tar.gz file and change directory into the newly created folder

tar zxvf my-software-1.2.3.tar.gz
cd my-software-1.2.3

Once that's done make install should work correctly.

---

### Post by Ephemeral on 2007-03-15
For most installations :

cd my/directory/with/file/to/install
./configure
If everything is ok :
make
sudo make install

---

### Post by AnthonyJK@gmail.com on 2007-03-15
Ok I tried it and heres what happend


```
anthonyjk@AnthonyJK:~$ cd /home/anthonyjk/Desktop/macbook-backlight-control
anthonyjk@AnthonyJK:~/Desktop/macbook-backlight-control$ ./configure
bash: ./configure: No such file or directory
anthonyjk@AnthonyJK:~/Desktop/macbook-backlight-control$ make
make: *** No targets specified and no makefile found.  Stop.
anthonyjk@AnthonyJK:~/Desktop/macbook-backlight-control$ sudo make install
make: *** No rule to make target `install'.  Stop.
anthonyjk@AnthonyJK:~/Desktop/macbook-backlight-control$ 
```

It says theres no make file found but if I open the folder there is a makefile ????

---

### Post by tagra123 on 2007-03-15
Rather than using   _sudo make install_

**_Give apt and synaptic control of the program once installed by doing it this way._**

You can untar using the command above or by opening it with archive manager in nautilus.

```
./configure
make
sudo checkinstall
```

---

### Post by peabody on 2007-03-15
> **AnthonyJK@gmail.com said:**
> 
It says theres no make file found but if I open the folder there is a makefile ????

Can you post the output of the ls command?

And for everyone else here recommending a ./configure, that step is only typical to software that needs to be configured to compile on different platforms.  What he's trying to install sounds linux specific, so it would not at all be uncommon for there to simply be only a Makefile with no configure step.

---

### Post by SishGupta on 2007-03-15
ive had problems with CheckInstall in the past...

has it improved?

---

### Post by AnthonyJK@gmail.com on 2007-03-15
anthonyjk@AnthonyJK:~$ cd /home/anthonyjk/Desktop/macbook-backlight-control
anthonyjk@AnthonyJK:~/Desktop/macbook-backlight-control$ ./configure
bash: ./configure: No such file or directory
anthonyjk@AnthonyJK:~/Desktop/macbook-backlight-control$ make
make: *** No targets specified and no makefile found.  Stop.
anthonyjk@AnthonyJK:~/Desktop/macbook-backlight-control$ sudo checkinstall
sudo: checkinstall: command not found
anthonyjk@AnthonyJK:~/Desktop/macbook-backlight-control$ 


still no luck im not sure what im missing here :\

---

### Post by peabody on 2007-03-15
I would ignore the advice on checkinstall


could you type "ls" then enter while in the folder and post the output here.

---

### Post by jocko on 2007-03-15
> **AnthonyJK@gmail.com said:**
> anthonyjk@AnthonyJK:~$ cd /home/anthonyjk/Desktop/macbook-backlight-control
anthonyjk@AnthonyJK:~/Desktop/macbook-backlight-control$ ./configure
bash: ./configure: No such file or directory
anthonyjk@AnthonyJK:~/Desktop/macbook-backlight-control$ make
make: *** No targets specified and no makefile found.  Stop.
anthonyjk@AnthonyJK:~/Desktop/macbook-backlight-control$ sudo checkinstall
sudo: checkinstall: command not found
anthonyjk@AnthonyJK:~/Desktop/macbook-backlight-control$ 


still no luck im not sure what im missing here :\

What files do you have in the Desktop/macbook-backlight-control directory?
cd to that directory and type "ls" (without the quotes). Post the output here and maybe someone may point you in the right direction.

---

### Post by AnthonyJK@gmail.com on 2007-03-15
anthonyjk@AnthonyJK:~/Desktop/macbook-backlight-control$ ls
src

I have the following in the directory


/home/anthonyjk/Desktop/macbook-backlight-control/src
/home/anthonyjk/Desktop/macbook-backlight-control/src/eggaccelerators.c
/home/anthonyjk/Desktop/macbook-backlight-control/src/eggaccelerators.h
/home/anthonyjk/Desktop/macbook-backlight-control/src/macbook-backlight-control.c
/home/anthonyjk/Desktop/macbook-backlight-control/src/Makefile
/home/anthonyjk/Desktop/macbook-backlight-control/src/tomboykeybinger.c
/home/anthonyjk/Desktop/macbook-backlight-control/tomboykeybinder.h


Thanks again for the help peabody and others

---

### Post by peabody on 2007-03-15
It looks like you'll want to do

cd src
sudo make install

Let me know if that doesn't work.

---

### Post by zvacet on 2007-03-15
O.K.You entered folder.Why don´t you type second command and see what happend.

---

### Post by AnthonyJK@gmail.com on 2007-03-15
thanks peabody that worked:)

---

### Post by tagra123 on 2007-03-15
I haven't had any trouble with it recently. In the past it gave me a few headaches or just acted plain dumb.

I've installed the following in the last month using it without problems

**DvdStyler**
recent **ffmpeg**
**gcompris**
most recent **k3b**
**conky**

-----------------

As noted earlier sometimes configure is not necessary

All of the above used :

archive manage to untar 

and then
```

apt-get build-dep programImInstalling 
```
(build-dep has worked for me some, but not every time)
Most reliable method has been to google for the error to find out what lib is needed.
   
```
./configure
make
sudo checkinstall

```

If you don't like checkinstall then

```
./configure
make
sudo install

```

I personally prefer checkinstall simply because it makes the program easy to uninstall using the gui.  Freedom to use the tools you prefer is what makes linux great.

Checkinstall link:

[http://www.ubuntuforums.org/archive/index.php/t-2356.html](http://www.ubuntuforums.org/archive/index.php/t-2356.html)

---

