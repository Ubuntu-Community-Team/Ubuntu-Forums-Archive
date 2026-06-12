---
title: "After updating to the Xenial HWE stack, some terminal commands have disappeared"
date: 2016-11-07
forum: General Help
---

### Post by yadec on 2016-11-07
Hi, I've just installed the latest HWE stack (for 14.04 LTS) after the notification kept pestering me for the past few months. It mentioned security, so I thought I probably should sooner or later. After looking into what the installation does, I thought that the update would only update the kernel and allow for newer drivers. I'm still kind of new to Linux, so I'm not exactly sure what the kernel affects, but it has clearly changed more than I'm comfortable with.

After I restarted the computer and I started to go though my workflow again, I noticed that some command line tools that I had installed were missing. For example, I use Python in Anaconda on a daily basis. I tried this:

```
$ source activate some-conda-env
bash: activate: No such file or directory
$ conda --version
conda: command not found
```

Do I have to reinstall all of my tools now, or is there just some switch that I can flip back? Unfortunately, I didn't have the foresight to keep regular backups, nor did I keep a list of all the things I installed. In any case, I sincerely appreciate any help. Thanks.

---

### Post by mc4man on 2016-11-07
"would only update the kernel and **allow** for newer drivers"
Not really, it **replaced** a number of xorg & mesa packages with ...-lts-xenial ones
Did you notice anything related to your anaconda,  ect. being removed?

---

### Post by yadec on 2016-11-07
Hm, okay, thanks. When I pressed "install" on the pop-up, I saw a flurry of packages being downloaded, most of which were too fast to read. The only download that I can remember specifically was my graphics driver (nvidia-370), only because it was a longer download. Then it began to install various things that it had downloaded, at which point I think I stopped watching the window and went to do some other work. After a few minutes, it prompted me to restart my computer, which I did. Unless I missed it, I didn't see anything about packages being removed.

Another thing to note was that as far as I can tell, everything I installed with a PPA or apt-get still works, and even apps I installed with a .deb, but Anaconda in particular was a .sh install. The other thing I can remember was Nvidia's CUDA Toolkit, which I installed with a .run, I think (it might've been a .deb). In both cases the files are still there in my home directory but I can't use them from the terminal.

---

### Post by yadec on 2016-11-10
Any more ideas? (sorry for the bump)

---

