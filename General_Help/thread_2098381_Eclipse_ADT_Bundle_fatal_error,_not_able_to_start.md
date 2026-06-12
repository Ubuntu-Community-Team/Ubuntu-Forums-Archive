---
title: "Eclipse ADT Bundle: fatal error, not able to start"
date: 2012-12-26
forum: General Help
---

### Post by mich30 on 2012-12-26
I have downloaded the ADT Bundle for Linux ([http://developer.android.com/sdk/index.html](http://developer.android.com/sdk/index.html)) that includes android sdk + eclipse with ADT plugin.

After extracting the .ZIP file, double click on eclipse... I choose the default workspace and the application crashes... one log gets created (the one you see attached to this post)

My Java version:

```

~$ java -version
java version "1.6.0_37"
Java(TM) SE Runtime Environment (build 1.6.0_37-b06)
Java HotSpot(TM) 64-Bit Server VM (build 20.12-b01, mixed mode)

~$ javac -version
javac 1.6.0_37

```

I've also tryied to reinstall the libgobject, without success:
```
sudo apt-get install libglib2.0-dev

```

---

### Post by mich30 on 2012-12-27
Well, I solved! I was trying to open an existing eclipse-workspace directory, with some old projects in it (created with an old version of Eclipse). If I select a new workspace directory... the program starts fine!

---

