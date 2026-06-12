---
title: "uninstall package that was installed from source"
date: 2006-11-01
forum: General Help
---

### Post by josh on 2006-11-01
hi guys!

im trying to learn to install from source. using that ./configure, make, make install. i do understand that some programmers write their program with an uninstall option in mind. but others dont. besides make uninstall, is there any other way to uninstall a program that was installed from source. without using dpkg, apt or any package manager? i want to do it manual so that i can learn. thanks!

---

### Post by matthewstory on 2006-11-02
you can just delete all the files that it installs, that's the quickest way to do it.  Though this requires you to find out where all the files are:

for the program, check /usr/local, and /usr/sbin it's config files will most likely be in /etc, and there might be some libraries in /usr/lib.

---

### Post by LenzM on 2006-11-02
> **josh said:**
> hi guys!

im trying to learn to install from source. using that ./configure, make, make install. i do understand that some programmers write their program with an uninstall option in mind. but others dont. besides make uninstall, is there any other way to uninstall a program that was installed from source. without using dpkg, apt or any package manager? i want to do it manual so that i can learn. thanks!

People have gone to a lot of effort to avoid doing this ever again, just giving you warning that it can be a very tedious process locating and removing every file that gets installed.  If you want to see all the files that a program has installed for an example, click on properties in synaptic for some package you have installed, then the installed files tab.  It will give you an idea of what's involved.

---

### Post by josh on 2006-11-02
wow! so its seems that if i install software on linux, its very hard to get rid of it. thanks for the info guys!

---

### Post by nalmeth on 2006-11-02
There should be an INSTALL file in the source package that details the locations, or something similar. Check there.
And in the future, use checkinstall rather than make install. Then it will be as easy as:
sudo apt-get install checkinstall
cd source-directory/
./configure
make 
sudo checkinstall
sudo dpkg -r program ( to remove )

---

### Post by chriscando on 2006-11-02
Sometimes from the source you can just sudo make uninstall.
ndiswrapper works this way, make -> sudo make install -> sudo make uninstall (to remove)

---

### Post by LenzM on 2006-11-03
> **josh said:**
> wow! so its seems that if i install software on linux, its very hard to get rid of it. thanks for the info guys!

No it's only very hard to uninstall if the programmers were lazy and it's not a deb package.  Almost all the software you install will be through deb packages in apt/synaptic, so you can VERY easily remove software by just removing the package.  If you compile from source and the programmer wasn't lazy then you should be able to `make uninstall` or there should be an uninstall script.

---

### Post by josh on 2006-11-03
yea. i noticed that some programs have make uninstall in the readme. it just sux that u cant uninstall programs "cleanly" in linux

---

### Post by ~LoKe on 2006-11-03
> **josh said:**
> yea. i noticed that some programs have make uninstall in the readme. it just sux that u cant uninstall programs "cleanly" in linux

make uninstall and dpkg -r... are both quite "clean" in comparison to Windows.

---

### Post by bsussman on 2006-11-03
> **~LoKe said:**
> make uninstall and dpkg -r... are both quite "clean" in comparison to Windows.

and if you use checkinstall as recommended for source builds, it will be just that clean as well, since checkinstall makes and adds it as a deb package.

---

### Post by ~LoKe on 2006-11-03
> **bsussman said:**
> and if you use checkinstall as recommended for source builds, it will be just that clean as well, since checkinstall makes and adds it as a deb package.

Hence the **dpkg -r** ;)

---

### Post by josh on 2006-11-04
well yea. think i got it. but my main question is "how to uninstall manually". not using any other program like synaptic, checkinstall, dpkg. but i guess that will do for now. thanks guys!

---

### Post by ~LoKe on 2006-11-04
> **josh said:**
> well yea. think i got it. but my main question is "how to uninstall manually". not using any other program like synaptic, checkinstall, dpkg. but i guess that will do for now. thanks guys!

"Synaptic" is the closest thing to Add/Remove Programs in Windows.  dpkg -r would be the command run by an uninstaller in Windows, AFAIK.

---

### Post by bsussman on 2006-11-04
> **josh said:**
> but my main question is "how to uninstall manually".

There is not a very happy answer.

0. As mentioned, some packages provide an uninstall target.  Congratulations!  skip all the following messy steps.

OTHERWISE

1.  Study [http://www.pathname.com/fhs/](http://www.pathname.com/fhs/) to find out where things are supposed to be placed.

2. study the make file for the targets you made when you installed, to see if it conforms to #1 and where it put everything else.  Step 1 is actually not mandatory but it will make this step a little easier.

3. using rm, carefully remove everything.

OR

3. using the install target, write an uninstall target to reverse the steps.  This is not as hard as it sounds and makes you a contributing member,  especially when you sent it to the original author along with a cranky note about how it should have been there to begin with.

Seriously,  somebody recommended using checkinstall to rebuild and reinstall, at which point you can use apt-get or one of the GUIs to remove it!  Sounds a little screwy but I think it is very clever!

---

