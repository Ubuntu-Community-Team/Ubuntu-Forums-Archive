---
title: "[SOLVED] I POD help"
date: 2008-01-03
forum: General Help
---

### Post by ChrisC098 on 2008-01-03
I am using Gutsy Gibbon and have an I Pod Classic 80GB today I installed gtkpod and was planning on using it to manage my files. I dragged and dropped some music files into the i pod and then ejected it and to my horror my i pod contained no files on it. However if I look in gtkpod all the files are still there. Does anyone know how to get those files back onto my I Pod?

---

### Post by shadyedsan on 2008-01-03
sounds like you haven't saved the session. when using gtkpod, make sure your ipod is mounted and set up properly (usually in /mount/whateveryouripodiscalled/) and that you have selected the proper model from the list. When you add files to the ipod, make sure that when you are done click save changes, which is located next to the load ipod button on the top left. this should save all changes to the files on your ipod for normal usage.

if you are unsure about how to add files to the ipod, here's how:

1. make sure your ipod is selected on the left and that is is connected properly (i.e. you can see all the current files on the ipod)
2. if it's just a single file you want to add, click the files button on the top and select the file from a directory and click ok (or add)
3 if it's a whole folder of files, repeat the last step but click the dirs button instead.
4. when you are finished, remember to click the save changes button located next to the load ipod button.

that should do it

:)

---

### Post by Sukarn on 2008-01-03
The version of gtkpod and libgpod in the ubuntu repositories are too old. They do not work with iPod Classic (Yes, its iPod, not I Pod).
Go to [http://www.gtkpod.org/about.html](http://www.gtkpod.org/about.html) and get the latest gtkpod and libgpod and compile them. If you need help with compiling then look around, there are a few howto's dealing with compiling gtkpod and libgpod on the forums. Search for them.
If you still have problem, then ask here.

- Sukarn, a happy user of iPod Classic 80gb (Black)

---

### Post by ChrisC098 on 2008-01-04
Ok so I' m having some trouble compiling libgpod but also now when I plug in the iPod i get "Plugin Error Unable to activate plugin portable players- iPod" and I can't even get gtkpod to open anymore. That didn't happen before so I think I might have messed something up. Edit:I uninstalled and reinstalled gtkpod, version 0.99.10-2, with synaptic and also libgpod and that is verion 0.5.2-2. Then when I try to run gtkpod i get this:
chris@chris-laptop:~$ gtkpod
gtkpod: error while loading shared libraries: libgpod.so.2: cannot open shared object file: No such file or directory

---

### Post by Sukarn on 2008-01-05
That looks about right. You have to remove libgpod1, use checkinstall for installing libgpod with the package name libgpod2, and then link libgpod.so.2 to libgpod.so.3

All this is explained in [this guide](http://ubuntuforums.org/showthread.php?t=619615).

If you don't want to use amarok, then don't follow the guide from when the guy tells you to install amarok. Follow the guide up to that point only.

The problem here is that libgpod 0.5.2 does not have the hash checking and other stuff needed for iPod Classic. All that is present in 0.6 though, and 0.6 is not in the Ubuntu repos, so you have to compile it.

Personally, I installed a lot of packages related to this (python-gpod and a lot of dependencies) from debian unstable repos (manually downloaded and installed from the website) to get my iPod working with gPodder (an audio podcast client).

---

### Post by click170 on 2008-03-05
I'm having a problem getting GTKpod to work properly.  I installed both GTKPod and Libgpod from the website, the latest versions, they seemed to install fine, I made sure to use checkinstall to install them too.  
When I try to open Gtkpod from the Applications menu it doesn't open, and when I try from the command line it says this;
"gtkpod: error while loading shared libraries: libgpod.so.3: cannot open shared object file: No such file or directory"

I've looked around, and am certain that libgpod.so.3 is in /usr/local/lib.  I have created links to it in /usr/lib, and a couple other places in an attempt to get this to work but nothing has so far.  I noticed that /usr/local/lib wasn't in the path, so I used the /etc/environment file to add it and tried again but still to no avail.

Does anybody else have this problem, or any ideas as to how to solve it?
Thanks.

---

### Post by Sukarn on 2008-03-07
> **click170 said:**
> I'm having a problem getting GTKpod to work properly.  I installed both GTKPod and Libgpod from the website, the latest versions, they seemed to install fine, I made sure to use checkinstall to install them too.  
When I try to open Gtkpod from the Applications menu it doesn't open, and when I try from the command line it says this;
"gtkpod: error while loading shared libraries: libgpod.so.3: cannot open shared object file: No such file or directory"

I've looked around, and am certain that libgpod.so.3 is in /usr/local/lib.  I have created links to it in /usr/lib, and a couple other places in an attempt to get this to work but nothing has so far.  I noticed that /usr/local/lib wasn't in the path, so I used the /etc/environment file to add it and tried again but still to no avail.

Does anybody else have this problem, or any ideas as to how to solve it?
Thanks.

These are the four places where I have libgpod3 present -
```

$ mlocate libgpod.so.3
/usr/lib/libgpod.so.3
/usr/lib/libgpod.so.3.0.0
/usr/local/lib/libgpod.so.3
/usr/local/lib/libgpod.so.3.0.0

```

---

### Post by click170 on 2008-03-07
Thanks, of all the things that have gone wrong so far today, this is the only one thats gone right.  It was the very first one in the list you sent, I created a soft link to it in that location and it started without problem.

Thanks again.

---

### Post by pythonusr on 2008-04-01
Or you can install them into /usr with:

```
./configure prefix=/usr
make
sudo make install
```

---

