---
title: "cant create symbolic link to linux-source??????"
date: 2007-05-26
forum: General Help
---

### Post by ninjaprawn on 2007-05-26
hi,

im following intructions to get my nokia 7610 to sync with ubuntu feisty!

but im completly stuck at the part where i need to create a symbolic link!!!

i have to go to symantic, and dowload linux-source, and linux-headers, extract, and create the link.

so i went to symantic packge manager, selected both, and chose to just download both!

the tutorial says they will be in /usr/src/ but theyre not, i found the linux-headers in /usr/share/doc, but not the source!

help?

the tutorial is at;
[http://siddharthdawara.blogspot.com/2006/09/gnokii-dku-2-nokia-6230-linux.html](http://siddharthdawara.blogspot.com/2006/09/gnokii-dku-2-nokia-6230-linux.html)

---

### Post by pbw on 2007-05-26
It's because the tutorial is outdated.

Each time you see a reference to 2.6.15, just replace that with 2.6.20, also the wrong quotes are used.

eg.

sudo apt-get install linux-headers-`uname -r` linux-source-2.6.20


-- pbw

---

### Post by ninjaprawn on 2007-05-28
i was clever enough to change the kernal version, but still have the same problem. the problem isnt realy creating the symbolic link, because ive done it before for java, and other things. its downloading and finding the neccessary file once downloaded.

thanks for the pointer on the quotes tho! i wouldnt have noticed.

---

### Post by ninjaprawn on 2007-05-28
what im doing is going into system->administration->symantic package manager,

then locating my version of linux source which is  2.6.20-16-generic, and also the headers, selecting to install or re-install, then ticking the box to just download them, then going to  /usr/src/ as the tutorial says, but there is nothing there, so i go looking, and find linux-headers in /usr/share/doc but there is no sign of linux-source!

i need to either re download the source agian, but toa place where i can find them, or find the ones i have supposedly already downloaded!!
also, wouldnt sudo apt-get install linux-headers-`uname -r` linux-source-2.6.20 install the source code and headers, rather than just download it?? or do i just completly not understand the whole process??

any ideas?????

thanks

---

### Post by snakedr on 2007-05-28
The synaptic install will install a linux-2.6.20.tar.gz file in /usr/src. If you don't see this file there is something wrong. The easiest way to access and extract the file is to :

sudo nautilus

This will get you into the file manager as root. Go to the /usr/src directory and you should see a linux-2.6.20.tar.gz file. (The exact file name may slightly differ.) Right click on the file and select extract here. That should create a folder by that name containing the source code.

The easiest way to make a link is to right click on the folder that contains the source code. Select create link. That will create a linked folder, notice the arrow indicating a linked file. To change the name of the link right click and select rename. Type in the name for the link, probably, linux.

This is the easy way to do this. Of course you can do all of this using the command line.

---

### Post by pbw on 2007-05-28
You can just wget kernel source from kernel.org, though of course apt should be downloading it for you. 

If that's the only thing not installing via apt, no need to depend on it. I never use apt when compiling a kernel.

You could also download the kernel source deb manually and then use dpkg in terminal to install it, and see what errors (if any) come up. then we could troubleshoot for you from there. 

Take a peek in /var/cache/apt/archives/ to see if it's already been downloaded.

-- pbw

---

### Post by Bachstelze on 2007-05-28
```
sudo apt-get install linux-headers-$(uname -r) linux-source
cd /usr/src
ls
```

You should have your source tarball in there, just extract it with 

```
sudo tar xjvf linux-source-2.6.20.tar.bz2
```

And make your symlink with

```
sudo ln -s linux-source-2.6.20 linux
```

---

### Post by ninjaprawn on 2007-05-29
thanks for all that help!

ill give it a go this afternoon!

---

