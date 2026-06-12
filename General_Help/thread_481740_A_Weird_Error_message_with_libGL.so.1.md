---
title: "A Weird Error message with libGL.so.1"
date: 2007-06-22
forum: General Help
---

### Post by foldor on 2007-06-22
I keep getting an error message that states, this "./googleearth-bin: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory"

Replace the ./googleearth-bin: with a bunch of different programs I try to use and this is it. It happens when I try to install or run google earth, The ATI proprietary drivers, and other programs I can't remember right now.

Any ideas?

---

### Post by trinaryouroboros on 2007-06-22
Sure thing, I would refer here foremost:

[http://ubuntuforums.org/showthread.php?t=199589](http://ubuntuforums.org/showthread.php?t=199589)

If the errors described and fixes thereof do not fit the bill, you could also double check to see if the libGL.so.1 is -actually- missing from /usr/lib

If so, use getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Once you got it, use it by typing:

cd /usr/lib
getlibs libGL.so.1

---

### Post by foldor on 2007-06-23
Ok, thanks for the help, but it didn't work. It seemed prmising because the getlibs was able to fetch the required library and create the symbolic link. However I still get the same error message.

---

### Post by trinaryouroboros on 2007-06-23
Strange, and nothing on the other thread helped?

---

### Post by foldor on 2007-06-23
No, it was for Nvidia cards, and I use an ATI. I tried its steps anyways and they didn't work either.

---

### Post by trinaryouroboros on 2007-06-24
Lost am I, never troubleshooted ATI stuff, but, I would start there.

---

### Post by Cappy on 2007-06-24
You have to do "getlibs -32 libGL.so.1" or "getlibs -64 libGL.so.1"
If you don't use the "-32" or "-64" switch getlibs thinks you are pointing it at a binary. That works better btw since it can determine all the libraries you are missing and if they are 32-bit or 64-bit.

I made a small update to the script so install the new version:
```

cd /tmp
wget -q http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs
chmod +x getlibs
sudo mv getlibs /usr/bin
cd ~

```

And then do this:
```
getlibs -32 libGL.so.1
```

If you're running 64-bit you should also run:
```
getlibs -64 libGL.so.1
```
just to make sure.

---

