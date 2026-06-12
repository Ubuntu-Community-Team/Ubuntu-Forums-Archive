---
title: "Help me....install things."
date: 2006-12-23
forum: General Help
---

### Post by badgaz1 on 2006-12-23
I'm new to Ubuntu and I am having a n00bie problem. I really don't have a clue what I am doing for starters...

For example I want to get all the buttons on my mouse (Logitech G5) working fully (I want autoscroll when I press the scroll wheel in and my "back" button to function)  so I was looking around on Google and found this:

[http://lomoco.linux-gamers.net/](http://lomoco.linux-gamers.net/)

I downloaded and extracted it but I really don't have a clue how to install it. On the website it says:

> Installation

./autogen.sh
./configure --prefix=/usr
make
make install


but that really doesn't mean anything to me. I tried typing './autogen.sh' into the terminal but I just get "No such file or directory".

:(

---

### Post by konst88 on 2006-12-23
You should enter to the directory using the cd command. example:
```
cd dirName
```

---

### Post by evaristegalois on 2006-12-23
go to the directory to which you downloaded the files

type

sh ./autogen.sh

(the command sh executes all the lines in the file)

then type the command 

./configure

then type the command 

make

and, if everything goes well (you'll see), type

sudo make install

---

### Post by evaristegalois on 2006-12-23
oh, and before I forget, one should always look for a debian package before installing manually like this. Just google debian and the name of the program. debian packages are installed by typing

sudo dpkg -i program-name.deb

alternatively, if you are online and have the right repositories in your etc/apt/sources.list,you can type

sudo apt-get install program-name

---

