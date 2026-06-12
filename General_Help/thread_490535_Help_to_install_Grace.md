---
title: "Help to install Grace"
date: 2007-07-02
forum: General Help
---

### Post by eledu on 2007-07-02
Hi all!

I'm new here and also using Ubuntu. I need it to my studies and I need to install a program called "Grace". It's a XY plot program for graphics and so on. Firstly, i tried to install it directly from its webpage, downloading it. But when I wrote ./configure the following message appeared: 

checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

How is it possible? I have already used gcc to compile other programs in C and it has worked. No idea.

But I have found the utility "Add/Remove programs" in the menu of Ubuntu. I have typed Grace and it has appeared, wow. I have selected it to install and it has started to downloads packages but at the end it has said that this program can't be installed in a computer as mine "i386". I can't believe it, the most of computers are "i386".

Please if anyone knows how to install it, i would really appreciate his/her help because I really need it for my studies.

Thanks!!

---

### Post by r0ck80y on 2007-07-02
See if you have the following installed, then try grace again :
**build-essential, fontconfig, lesstif.**
Then after installation, run the software from terminal:```

xmgrace
```
Its possible that grace does not come up in the menu .

---

### Post by eledu on 2007-07-02
How can i know if i have these packets installed?

I have already installed Grace but in Fedora 4 in the university but, here in my laptop, I have Ubuntu. I wouldnt want to change it :(

I followed these simple steps in Fedora within grace unzipped folder:
./configure
./make
./make install

Then i could call the program either by an icon or by shell as you say: xmgrace. But to call xmgrace with the shell first i need to have it installed, i think.

Anyway, thanks for your reply.

---

### Post by r0ck80y on 2007-07-02
look for the packages i mentioned in ** Add Remove Programs**. If you see a tick mark against it, that means its installed.
---------or---------------

Open terminal and type the following:```

sudo aptitude update
sudo aptitude install build-essential lesstif fontconfig

```

Then install grace. Hope you've got it :)

---

### Post by eledu on 2007-07-02
Thank you very much.

Finally i have Grace installed, puff. I don't know why but from source code from its web hasn't worked well. But i have tried with "Add/Remove programs" one and it has worked properly. A little bit work to find out the executable because i was trying with "xmgrace" in the shell and didn't work, then i have searched it where it has supposed to be in /usr/local/grace/bin but there were all files unless "xmgrace". And after searching, i have found it at end in /usr/bin. It results that it is called "xmgrace6" and not only "xmgrace" :o

Well, the important thing is that i have it working now. Thanks again!!

---

