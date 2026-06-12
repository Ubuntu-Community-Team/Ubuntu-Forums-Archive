---
title: "BURN! cant install SUN EE JDK.bin"
date: 2008-04-09
forum: General Help
---

### Post by hurinth on 2008-04-09
[COLOR="Olive"][B]K this is how I got burn:

-Went to download java_ee_sdk-5_04-linux.bin and placed it in my desktop

-Gave it 777 permissions to that file

-Ran ./java_ee_sdk-5_04-linux.bin and got following message:

> ./java_ee_sdk-5_04-linux.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

What is wrong here?

Thanks[/B][/COLOR]

---

### Post by |{urse on 2008-04-09
try

sudo apt-get install libstdc++5

---

### Post by hurinth on 2008-04-09
[B][COLOR="Olive"]Great Bill, just wandering what those libraries are all about???
And also, I am behind a proxy so at the moment of connecting with the library server everything hangs: 
> 0% [Connecting to archive.ubuntu.com (91.189.88.46)] Is there a way to get those with Firefox and install them in a different way?[/COLOR][/B]

---

### Post by |{urse on 2008-04-09
thats the standard c++ libs my friend praise bob. Be sure to thank me if that worked =p

---

### Post by hurinth on 2008-04-09
**[COLOR="Olive"]K, but do you know a way to get those libs with firefox?? I updated previous post after your last reply[/COLOR]**

---

### Post by |{urse on 2008-04-09
do a 

sudo apt-get update

first, then try it again

if that doesnt work

cd /tmp/

wget -c [http://lug.mtu.edu/ubuntu/pool/main/g/gcc-3.3/libstdc++5_3.3.6-13ubuntu2_i386.deb](http://lug.mtu.edu/ubuntu/pool/main/g/gcc-3.3/libstdc++5_3.3.6-13ubuntu2_i386.deb)

dpkg -x libstdc++5_3.3.6-13ubuntu2_i386.deb libstdc++5

sudo cp libstdc++5/usr/lib/libstdc++.so.5.0.7 /usr/lib

cd /usr/lib

sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5

---

