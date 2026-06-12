---
title: "compiling applications"
date: 2008-02-05
forum: General Help
---

### Post by Cew27 on 2008-02-05
hi there 
i think i know how to compile software but i am just wondering how to get rid of it once it is compiled??
to compile 
cd Desktop/<name> (this is where i put my source) 
./config
make
sudo make install 
is that all there is to it? 
also how do i remove the files i understand i do sudo apt uninstall or something along those lines but where to i navigate to to run this code? 
im just wondering as i was looking at gentoo and it states that most software is source
what makes installing from source better than a package ?
many thanks

---

### Post by Cew27 on 2008-02-05
bumpedy bump

---

### Post by diaa on 2008-02-05
> **Cew27 said:**
> hi there 
i think i know how to compile software but i am just wondering how to get rid of it once it is compiled??
to compile 
cd Desktop/<name> (this is where i put my source) 
./config
make
sudo make install 
is that all there is to it?


probably you mean ./configure not ./config
Yes, this is the standard compilation procedure as far as I know.

> **Cew27 said:**
> 
also how do i remove the files i understand i do sudo apt uninstall or something along those lines but where to i navigate to to run this code?


Apps/libraries installed using the method above cannot be removed using *apt-get*, to remove them you should execute
```
sudo make uninstall
```

> **Cew27 said:**
> 
im just wondering as i was looking at gentoo and it states that most software is source
what makes installing from source better than a package ?
many thanks

Usually because you can get the most recent versions and because when compiling it you can optimize it for your machine(so it runs faster only on your machine)
but IMHO always use Ubuntu repositories when possible, yes you may not find the latest version there but it saves you a lot of headache, it's tested and it's easier to install and remove.

---

### Post by odiseo77 on 2008-02-05
Also, if you're installing a package from source, you probably want to install checkinstall (it's on ubuntu's repos), and try with ***sudo checkinstall -D***, instead of "sudo make install". This way checkinstall will generate a .deb package that you can easily and cleanly uninstall later via apt-get/dpkg/synaptic.

---

### Post by Cew27 on 2008-02-05
brilliant! thanks 
to dia 
where is "Apps/libraries " can you give the full location 
thanks

---

### Post by odiseo77 on 2008-02-05
I think what diaa meant with "App/libraries" is that, when you install something from source (either an application or a library), you can't uninstall it with apt-get (or dpkg, or synaptic), but with "sudo make uninstall" (inside the root of the source directory). But if you want to know the location of the program you installed, it may vary depending on which program is it. If you want to keep track of where the program is installed, you can execute the following command inside the source directory: ***make -n install***. This way, "make" will pretend it's installing the program and will tell you where it goes (however, if you want to uninstall it, I wouldn't advice you to manually delete the files, since you can break important stuff in your system; it's better to use checkinstall as I suggested in my previous post).

Greetings.

---

### Post by bodhi.zazen on 2008-02-05
I advise you look at checkinstall. 

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)
	[http://www.howtoforge.com/howto_linux_debian_deb_checkinstall](http://www.howtoforge.com/howto_linux_debian_deb_checkinstall)


Checkinstall will make a .deb from your source, and the deb is easier to manage.

dkpg -i *.deb
dpkg -r *.deb

Checkinstall sometimes fails though.

```
./configure
make
sudo checkinstall
```

Also, if you compile keep the source code. I keep it in ~/src/package_name.

Sometimes the developer does NOT write an uninstall script in the make file. In that case you need to manually remove the package.

```
sudo updatedb
locate <package_name>
```

Remove those files manually ```
sudo rm bla bla bla
```

Why compile for source ? In general, try to stay with the packages in the repositories. If you like to play though, go for it.

The most common reason to compile would be if a package is not in the repos or if there is a newer version that has some feature or bug fix that you can not live without.

---

### Post by Cew27 on 2008-02-06
ok so what is the correct command sudo checkinstall or sudo checkinstall -D ?
also how can i find out where a program is installed? for example awn i compiled that and cant find the make file?

---

### Post by bodhi.zazen on 2008-02-06
either will work

-D specifies a debian package (.deb)

After running checkinstall you will have a .deb in the directory ...

In your case, awn.deb (or whatever name you gave it).

---

### Post by Cew27 on 2008-02-06
just tried this with g15 stats for my keyboard and it didnt work :( it just kept saying command not found

---

### Post by bodhi.zazen on 2008-02-06
did you install it ?

```
sudo apt-get install checkinstall
```

---

### Post by Cew27 on 2008-02-06
i have now :)

---

