---
title: "Attempting to activate my fingerprint sensor in 12.10"
date: 2013-04-08
forum: General Help
---

### Post by meijin3 on 2013-04-08
I've been trying this guide: [http://www.tuxtrix.com/2012/05/how-to-activate-validity-fingerprint.html](http://www.tuxtrix.com/2012/05/how-to-activate-validity-fingerprint.html) but things fall apart when I get to step 2 with ```
sudo dpkg -i libfprint0_0.4.0+git20120202-0ppa1~precise2_amd64.deb
```.

I get this:
```
dpkg: error processing libfprint0_0.4.0+git20120202-0ppa1~precise2_amd64.deb (--install): cannot access archive: No such file or directory
Errors were encountered while processing:
 libfprint0_0.4.0+git20120202-0ppa1~precise2_amd64.deb

```

Now, I'm using Quantal which may be the problem but I don't know how to fix it. Thanks once again, Ubuntu Forum-goers!

---

### Post by zero2xiii on 2013-04-09
> No such file or directory

There is your problem.

First, check the file name. It should be the exact same as the one you downloaded (don't just copy paste from the website!).
Start typing the name and press the TAB key to complete the name.

Second, check the path:
> sudo dpkg -i libfprint0_0.4.0+git20120202-0ppa1~precise2_amd64.deb
will assume the file is in the current working directory.

To check your current working directory:
```
echo $(pwd)
```

Or to check that the file is in the current location:
```
ls
```
and make sure the file name exist in the current directory. If not, use the ChangeDirectory "cd" command to change to the correct directory:
```
cd /correct/path/to/FOLDER_containing_file
```

Cheers

---

