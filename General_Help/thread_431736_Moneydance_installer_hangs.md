---
title: "Moneydance installer hangs"
date: 2007-05-03
forum: General Help
---

### Post by 50words on 2007-05-03
I am trying to get Moneydance installed, but I'm not having any luck. I have tried both versions (w/ Java and w/o), and get the same results on both. I do have JRE installed.

I download the file, make it executable, navigate to the directory, and run the following in terminal:

```

./moneydance_linux_x86.sh

```

or, for the "with Java' version

```

./moneydance_linux_x86wj.sh

```

Then I get this:

```

Unpacking JRE ...
Preparing JRE ...
Starting Installer ...

```

A blank window opens (a menubar with greyed-out box), and it hangs right there.

I'm in Feisty with nothing fancy installed.

---

### Post by 50words on 2007-05-03
Bueller?

---

### Post by Chuckanut on 2007-05-08
I just had the same problem and found a solution in another thread.  Right click on the downloaded package and change all the permissions to Read and Write and check the Execute box.  It all worked fine after that.

Tom

---

