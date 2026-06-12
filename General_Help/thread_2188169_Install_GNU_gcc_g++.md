---
title: "Install GNU gcc g++"
date: 2013-11-15
forum: General Help
---

### Post by Xinghao_Chen on 2013-11-15
About a year ago I installed a GNU C/C++ compiler on my 32-bit 11.10 with the following command line (thanks to the advice on this forum):

 sudo apt-get install gcc g++ build-essential

Early this week I installed a 64-bit 12.04 on a USB stick memory. 

Does the same command line mentioned above still hold for this 64-bit 12.04 platform and get a correct 64-bit GNU C/C++ compiler installed?

Thank you.

---

### Post by steeldriver on 2013-11-15
Yes - although the 'gcc' and 'g++' parts are redundant since the build-essential meta package includes them in its dependencies

```

$ apt-cache depends build-essential
build-essential
 |Depends: libc6-dev
  Depends: <libc-dev>
    libc6-dev
  Depends: gcc
  Depends: g++
  Depends: make
  Depends: dpkg-dev

```

---

### Post by Xinghao_Chen on 2013-11-15
I am not sure understanding completely. I have no idea what are the diferences between apt-get install and apt-cache depends.

As to the redundancy, do you mean:

%sudo apt-get install gcc build-essential

and

%sudo apt-get install g++ build-essential

will do the same and install GNU C/C++ compiler?

I am still a newbie with Ubuntu and C/C++ and it would be very helpful to me by explaining your code lines line-by-line. 

Do I type every words of your code in command line? The "build-essential" appeared twice together and I am not sure why this is necessary as a command. Or, is the section starting from the second appearence of "build-essential" the output text?

---

### Post by steeldriver on 2013-11-15
The command

```
apt-cache depends build-essential
```

just lists the components that will be installed as dependencies when you do

```
sudo apt-get install build-essential
```

---

### Post by Xinghao_Chen on 2013-11-15
I just tried. Here is what I got:

xinghao@CTC-Ubuntu-64:~$ apt-cache depends build-essential
build-essential
 |Depends: libc6-dev
  Depends: <libc-dev>
    libc6-dev
  Depends: gcc
  Depends: g++
  Depends: make
  Depends: dpkg-dev
  Conflicts: build-essential:i386
xinghao@CTC-Ubuntu-64:~$ 

I have two questions:

(1) Does the "conflicts" line says something of trouble?

(2) The following two lines from the outputs:

Depends: <libc-dev>
    libc6-dev

They seem to be in a different format then the rest of the "Depends" line. How do I read them?

---

### Post by Xinghao_Chen on 2013-11-17
I asked the latter question and got an explanation on the Development forum at:

[http://ubuntuforums.org/showthread.php?t=2188476](http://ubuntuforums.org/showthread.php?t=2188476)

---

