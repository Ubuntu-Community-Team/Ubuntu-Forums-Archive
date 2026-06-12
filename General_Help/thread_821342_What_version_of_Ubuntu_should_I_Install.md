---
title: "What version of Ubuntu should I Install?"
date: 2008-06-07
forum: General Help
---

### Post by Vigh on 2008-06-07
Hi if i'm running an Intel 64-bit computer, with 4GB of ram, what operating system should I install? Ubuntu AMD64bit? Is there an Ubuntu Intel64bit OS?

---

### Post by rraj.be on 2008-06-07
there is 64 bit os.

But not something specific for AMD or intell.

it can be used for any 64 bit os.

you can Get it here.

```
[https://shipit.ubuntu.com/]("https://shipit.ubuntu.com/")
```

You can download it from here

```
[www.ubuntu.com/GetUbuntu/download]("www.ubuntu.com/GetUbuntu/download")
```

I recomnend you to download using Bittorent as it provides lots of flexibilities

```
[http://releases.ubuntu.com/8.04/]("http://releases.ubuntu.com/8.04/")
```

---

### Post by Pjotr123 on 2008-06-07
Check this page:
[http://ubuntutip.googlepages.com/getubuntu](http://ubuntutip.googlepages.com/getubuntu)

---

### Post by Vivaldi Gloria on 2008-06-07
> **Vigh said:**
> Hi if i'm running an Intel 64-bit computer, with 4GB of ram, what operating system should I install? Ubuntu AMD64bit? Is there an Ubuntu Intel64bit OS?

I also have an Intel 64-bit computer, with 4GB of ram. 

What you call Intel64bit is actually called AMD64bit. That "AMD" at the front has nothing to do with processors. If I remember correctly, AMD first develped the 64 bit architecture so it is called AMD64bit even if you have an intel processor.

So if you want to download a desktop version of ubuntu you have two options.

1) PC (Intel x86) desktop CD

2) 64-bit PC (AMD64) desktop CD

Both will work perfectly well on your computer. 

Each has an advantage and disadvantage:

Intel x86 can use 3.5GB of RAM. For example in my computer the following command shows how much RAM I have:

```
hasan@narval:~$ cat /proc/meminfo
MemTotal:      3631012 kB
...
```

So the disadvantage of x86 is that you cannot use all of you RAM. But AMD86 also has an disadvantage. Almost all programs are 32 bit so there is no benefit it getting the AMD64 version for that. I know that some programs are harder to install on AMD64 version actually. So you may find yourself trying to install a hard-to-install program on AMD64.

So if you are a newbie go with x86 because things are a little easier. If you have used linux before give AMD64 a try so that you can use all of your 4GBs of RAM.

I personally have x86 and I am happy with 3.5GB of RAM.

---

### Post by jocko on 2008-06-07
> **Vivaldi Gloria said:**
> But AMD86 also has an disadvantage. Almost all programs are 32 bit so there is no benefit it getting the AMD64 version for that. I know that some programs are harder to install on AMD64 version actually. So you may find yourself trying to install a hard-to-install program on AMD64.

That's simply not true. *All* programs that are available for the 32 bit version of ubuntu are available for 64 bit ubuntu as well.
In some very rare cases (sun's java browser plugin and adobe's flash) there are no native 64 bit versions, but there are very simple workarounds (for flash there is a plugin wrapper available that allows firefox to run the 32 bit flash plugin, and there is a good alternative java plugin which works fine in 64 bit).
If you have a 64 bit processor and lots of memory, it's just a waste of a good computer if you don't install a 64 bit os.
The difference in performance is clearly noticable, as long as the amount of memory is not limiting (64 bit will use slightly more memory, which could be a bottleneck if you have too little ram).

---

### Post by housam on 2008-06-07
+ 1 for 64 bit version. Make use of what you've paid for .

---

### Post by Vivaldi Gloria on 2008-06-07
> **jocko said:**
>  there are very simple workarounds (for flash there is a plugin wrapper available that allows firefox to run the 32 bit flash plugin, and there is a good alternative java plugin which works fine in 64 bit).

You call potato, I call harder to install.

---

### Post by jocko on 2008-06-07
Harder? In which way is it harder to install the package flashplugin-nonfree in 64 bit compared to 32 bit?
The name of the package is the same, it's just that the 64 bit package brings a few extra dependencies and does some extra things during the installation. For the user, it will still be exactly the same procedure.
Setting up the java plugin is not harder, but you need to know the name of the package (icedtea-gcjwebplugin).
Just because it may be a little bit different doesn't mean it's any harder. Just different.

[SIZE=2]And of course: No matter which version you use and what the names of the actual packages are, the package ubuntu-restricted-extras will set up both flash and java automatically, as well as some other restricted licence programs (codecs, fonts, unrar)... So even if there are some few real differences between the 32 bit and 64 bit versions, everything can be done exactly the same way in both versions, if you just use the metapackages instead of searching for every individual package yourself.
[/SIZE]

---

### Post by Vivaldi Gloria on 2008-06-07
> **jocko said:**
> Harder? In which way is it harder to install the package flashplugin-nonfree in 64 bit compared to 32 bit?
The name of the package is the same, it's just that the 64 bit package brings a few extra dependencies and does some extra things during the installation. For the user, it will still be exactly the same procedure.
Setting up the java plugin is not harder, but you need to know the name of the package (icedtea-gcjwebplugin).
Just because it may be a little bit different doesn't mean it's any harder. Just different.

[SIZE=2]And of course: No matter which version you use and what the names of the actual packages are, the package ubuntu-restricted-extras will set up both flash and java automatically, as well as some other restricted licence programs (codecs, fonts, unrar)... So even if there are some few real differences between the 32 bit and 64 bit versions, everything can be done exactly the same way in both versions, if you just use the metapackages instead of searching for every individual package yourself.
[/SIZE]

OK. You convinced me. :-)

---

