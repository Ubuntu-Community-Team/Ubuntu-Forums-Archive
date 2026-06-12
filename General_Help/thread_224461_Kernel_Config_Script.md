---
title: "Kernel Config Script"
date: 2006-07-28
forum: General Help
---

### Post by Brando569 on 2006-07-28
hey all, i couldnt remember where the coding section is so ill just throw this here :)

heres the script ive been working on to make compiling a kernel easier and quicker. i have pretty much everything how i want it except for 1 thing: 

1) i know how an if/else statement works in c++ and i found a huge bash tutorial but i was j/w if someone could give me a quick answer. what i want to have the statement do is if there is already a symbolic link for 'linux' then the script would remove it and create one for the current kernel your compiling, if there isnt one it would just create the link on go on like usual.

heres the script, feel free to use it :D

```
#make sure to edit this

cd /usr/src
sudo cp /home/bran/kernel/linux-2.6.17.tar.bz2 /usr/src
sudo cp /home/bran/kernel/bd-claim.patch /usr/src
sudo cp /home/bran/kernel/patch-2.6.17-beyond2.2.bz2 /usr/src
sudo tar -xvjf linux-2.6.17.tar.bz2
sudo ln -s /usr/src/linux-2.6.17 linux
cd linux
sudo cat ../bd-claim.patch | patch -p1
sudo bzcat ../patch-2.6.17-beyond2.2.bz2 | patch -p1
sudo cp /boot/config-2.6.17-ck1ck1 .config
sudo make xconfig
sudo make-kpkg clean
make-kpkg -initrd kernel_image kernel_headers modules_image
sudo dpkg -i *.deb
```

---

### Post by mlind on 2006-07-28
see bash manual, CONDITIONAL EXPRESSIONS (line 1951 and onwards)

For example, -h tests for symbolic link, -e tests that file exists

```

file="/usr/src/linux"
if [ ! -e $file ]; then
        echo "file doesn't exist.."
fi

```
or
```

test -h /usr/src/linux || echo "nope, symbolic link is missing"

```

---

### Post by Brando569 on 2006-07-28
> **mlind said:**
> see bash manual, CONDITIONAL EXPRESSIONS (line 1951 and onwards)

For example, -h tests for symbolic link, -e tests that file exists

```

file="/usr/src/linux"
if [ ! -e $file ]; then
        echo "file doesn't exist.."
fi

```
or
```

test -h /usr/src/linux || echo "nope, symbolic link is missing"

```



ehh it seems bash if-then statements are a lil mor e comoplexd then the ones in C++. ill t4ry nd figure it our=t tomorrow

---

