---
title: "How extract a executable file in /usr/bin?"
date: 2014-09-24
forum: General Help
---

### Post by Chanath on 2014-09-24
How extract a executable file in /usr/bin to see how the code is written?

---

### Post by Lars Noodén on 2014-09-24
If it is a script, then it is enough to just view it with a pager like [less](http://manpages.ubuntu.com/manpages/trusty/en/man1/less.1.html)

```

less /usr/bin/shasum

```

However, if the file is a binary, then you will need to find which package it belongs to and then get the src package.  Here is how to do it for the program evince which also happens to be in a package of its own.  

```

$ dpkg -S /usr/bin/evince
**evince**: /usr/bin/evince
$ cd /tmp
$ apt-get source evince
$ ls
evince-3.10.3 
evince_3.10.3-0ubuntu10.1.debian.tar.gz 
evince_3.10.3-0ubuntu10.1.dsc
evince_3.10.3.orig.tar.xz  
$ cd evince-3.10.3
$ ls 
...

```

For that you will need the package dpkg-dev installed already.

---

### Post by Chanath on 2014-09-24
Thanks for the reply, Lars, but this > apt-get source didn't work as apt cannot find the source package in the repos. There is no ppa anymore, only a .deb package, which I had installed with > dpkg -i. I tried with another binfile, which was installed from the Ubuntu trusty repos, and that > apt-get source connected to the repos and downloaded the files as in your reply.

I have the .deb package, and when I extract it, I can get to the executable bin file. When I click on that file, wherever it is, it works. I don't have to keep it in the /usr/bin, I can just keep it in the Documents folder. I'd like to look into that executable bin file. Thanks again for the help.

---

### Post by Lars Noodén on 2014-09-24
Which package, may I ask?  And do you have the source repositories activated in the Software Center / System Settings -> Software and Updates -> Ubuntu Software -> Source code

or

```

grep deb-src /etc/apt/sources.list

```

---

### Post by Lars Noodén on 2014-09-24
> **Chanath said:**
> There is no ppa anymore, only a .deb package, which I had installed with .

.deb is only a binary, so unless the program is a script, you are out of luck.  

In that case, it will be necessary to find the project's archive at github, sourceforge or somewhere else.  If that is not around, then maybe an archive would have it.  But then it will be a bit of extra work to make it into an APT package.  Using the source repository gets you the extra files needed to easily make a new package.

---

### Post by Chanath on 2014-09-25
Thanks Lars, I believe I am out of luck as there is no repos for this deb package, which had been created for an old release of Ubuntu.
I leaarned something from your post, thanks again.:)

---

### Post by Lars Noodén on 2014-09-25
One small chance might remain, since you mention that the package is from an old ubuntu version.  If you have that version of Ubuntu in a VM, you could set the repository in sources.list to point to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) and then see if they've kept the old source packages.

---

### Post by Chanath on 2014-09-25
Thanks, Lars, I'd try that. If that works out, I'd come back here and let you know.
Best regards! :smile:
Chanath

---

