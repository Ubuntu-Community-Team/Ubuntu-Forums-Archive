---
title: "Error when running &quot;apt-get update&quot;"
date: 2007-06-03
forum: General Help
---

### Post by Devsense on 2007-06-03
Hello, I have just performed a new installation of Ubuntu 7.04. After editing the /etc/apt/sources.list file and running "sudo apt-get update", I get the following error:

```
E: Method bzip2 has died unexpectedly!                                                                    
E: Method /usr/lib/apt/methods/bzip2 did not start correctly
```

I've tried searching google and these forums to no avail, any and all help would be appreciated :)!

---

### Post by figgles on 2007-06-03
What edit did you make? DId you back up the sources.list file? If you can restore the file -- do you have the same problem?

---

### Post by ukio on 2007-07-11
Exactly the same problem / error message here.

The problem appeared after I added the medibuntu repository and tried to install the w32codecs.

I followed the instructions on [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) to add the repository:
> sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

It did not change the original /etc/apt/sources.list I guess. Maybe it has something to do with the w32codecs..

Any ideas how to fix this issue?

regards,
ukio

P.S. 1: Uninstalling the w32codecs and reinstalling bzip2 did not help either
P.S. 2:  cp /bin/bzip2 /usr/lib/apt/methods/bzip2  makes apt-get update stall at the point where usually the error occurs

---

### Post by ukio on 2007-07-11
Solution: reinstalling the apt package did the trick!

I didn't dare to use to commandline to remove-install (afraid that i can't install when the apt package is removed), but using the adept package manager i could just select "request reinstall"

---

