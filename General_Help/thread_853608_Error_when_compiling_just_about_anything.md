---
title: "Error when compiling just about anything"
date: 2008-07-08
forum: General Help
---

### Post by Ataris on 2008-07-08
I've downloaded several things from source (I can't use the Internet on my PC, so I can't use the terminal for that kind of thing), such as Quanta. It gives me an archive, and I extract it. I then cd to the folder where all the files are, and type in ```
./configure
``` A bunch of code goes flying past, and then I type in ```
make
``` Then it tells me something like "no target ****." Regardless, it seems I can't compile ANYTHING. It's the same thing every time, I configure it, something happens, I type in make or make install, and then nothing happens. Is there something I need to download or what?

---

### Post by sdennie on 2008-07-08
You probably need to install, at the very least, build-essential:

```

sudo apt-get install build-essential

```

Even then, you will probably be missing many things to build almost any source package.  I really recommend staying away from source packages unless you have no other recourse.  Almost any kind of software you'd ever want can be found in Applications->Add/Remove or System->Administration->Synaptic Package manager.  Using those two sources makes installation and maintenance much easier.

---

### Post by Ataris on 2008-07-08
As I said in my first post, I don't have access to the Internet on my PC. I have to use public computers to download the software's source (if I can't find a deb package, and I can't often times). Is there a way I can get build essential without the terminal?

---

### Post by ibuclaw on 2008-07-08
If configure didn't create a makefile, then you don't have the right -dev packages installed on your system to compile the source.

What is the complete output of the ./configure command?

HINT:
If the output is too big, try
```
./configure >> configure_output.txt
```
Then open up the file
```
gedit configure_output.txt
```
and paste it up in your next post.

Regards
Iain

---

### Post by Ataris on 2008-07-08
I'd have to go home and find out, I suppose I should have known. I figured it was because I needed libraries I didn't have and such. I'll return with the output later.

---

### Post by lamego on 2008-07-08
Build from source requires a lot of development packages, you will not succeed without an internet connection.

Also please note that quanta is available from the repositories, which is far more easy to install.

---

### Post by sdennie on 2008-07-08
If you don't have any way to get the Ubuntu machine onto the network, you'll probably need to download or order an Ubuntu DVD that can be used as a repo.  Googling for "ubuntu repo dvd" brings up several hits that might help you.

---

