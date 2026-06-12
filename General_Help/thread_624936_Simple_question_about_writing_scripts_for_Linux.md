---
title: "Simple question about writing scripts for Linux"
date: 2007-11-27
forum: General Help
---

### Post by warnec on 2007-11-27
Hello. I've wanted to change a bit a script that downloads andcompiles CF from git source. However, the script did download and compile x11 with xcb support, because it was required by CF from git. Now, I wanted to apply no-xcb patch. So i removed the lines, and it works like this:
```

echo -e "\033[1mWould you like to install Compiz Fusion?(y/n):\033[0m" ; read answer
			if [ $answer = y ] ; then
				echo -e "\033[1mWould you like to install latest Compiz Fusion revision from git or install version 0.5.2? If you choose git, compiz code will be patched so that it will not require libx11 with xcb support (which caused breaking of Java programs, such as OP2M)(git/stable):\033[0m" ; read answer
				if [ $answer = git ] ; then
					cd $downdir
					echo -e "\033[1mDownloading Compiz Fusion...\033[0m"
					git clone git://git.freedesktop.org/git/xorg/app/compiz
					cd $downdir/compiz
					echo -e "\033[Patching Compiz Fusion with noxcb patch...\033[0m"
  					patch -Np0 -i /home/maciek/no-xcb.patch
					echo -e "\033[1mInstalling Compiz Fusion...\033[0m"
					./autogen.sh --disable-$opdeskenv && make && sudo make install
				elif [ $answer = stable ] ; then
(later it is not what i'm talking about)

```
So after downloading it patches compiz with no-xcb patch, and then compiles&installs. I know that i shouldn't give specific directory (like home/maciek/no-xcb.patch) here, so my question is: how to change this part of script, so that it asks a user what is user's login, and then substitutes "maciek" for the login of the user (of course assuming that the patch is in their home directory)

Thanks!

---

### Post by kast on 2007-11-27
if you know that the patch is going to be in the users home directory then you could use $HOME

---

### Post by warnec on 2007-11-27
So 
```

patch -Np0 -i /&HOME/no-xcb.patch

```
?

---

### Post by kast on 2007-11-27
```
patch -Np0 -i /$HOME/no-xcb.patch
```

---

### Post by warnec on 2007-11-27
Thanks ;)

---

