---
title: "Can't find the .torsmorc file"
date: 2005-05-09
forum: General Help
---

### Post by ArtemisL on 2005-05-09
I installed Torsmo via the synaptic package manager, but I cannot seem to find the .torsmorc file. From all the sites I've read, it's supposed to be in my home directory but it's not there. I've tried whereis and locate and cannot even find the torsmo folder. It's a nice program but I want to move if from the bottom left of the screen to the top left instead.

Can someone please point me in the right direction?

Thanks,
Artemis

---

### Post by lt_kije on 2005-05-09
[QUOTE=ArtemisL]I installed Torsmo via the synaptic package manager, but I cannot seem to find the .torsmorc file. From all the sites I've read, it's supposed to be in my home directory but it's not there. I've tried whereis and locate and cannot even find the torsmo folder. It's a nice program but I want to move if from the bottom left of the screen to the top left instead.[/QUOTE]

Torsmo's a great app -- unfortunately, the default install doesn't copy the file to your home directory. It is in your system, though: try using `find` to search for it:

(on the command line)
$ find / -name "*torsmo*rc*" 2>/dev/null

That command will search everything on your hard drive (from the root directory upwards) for files that match the pattern "*torsmo*rc*" (that is, that have `torsmo` and `rc` in their file names). It will also redirect error messages to /dev/null, which leaves the good output. The redirection at the end is optional, but I've found that searching the whole computer often produces errors (regarding permissions) that can be safely and efficiently ignored.

If the above doesn't work, search as well for "*torsmo*sample*".

And lastly, if you have no luck at all finding the file included in the package you installed, check this out (found via google): [http://www.suseroot.com/suse-linux-tweaks/torsmorc.sample](http://www.suseroot.com/suse-linux-tweaks/torsmorc.sample).

Good luck!

lt_kije

---

### Post by ArtemisL on 2005-05-11
It_kije,

Thank you SO much!! The find command worked like a charm *writes that down for future reference*. Before I had gotten your reply, I tried creating the file in my home dir, then pasted from a sample torsmo.rc file I found online, and then saved the file. It worked (much to my surprise lol). I haven't been using Linux for long, but some of the basic commands are starting to come back to me from when I used Unix sooooo long ago. Thank you for being so patient, giving me those commands, and being thoughtful enough to help me!
 

In case anyone else has this problem, the file was located in /usr/share/doc/torsmo/examples/torsmorc.sample.gz
sudo -s to login as root, then gzip -d torsmorc.sample.gz 


Artemis

---

### Post by lt_kije on 2005-05-11
[QUOTE=ArtemisL]It_kije,

Thank you SO much!! The find command worked like a charm *writes that down for future reference*. Before I had gotten your reply, I tried creating the file in my home dir, then pasted from a sample torsmo.rc file I found online, and then saved the file. It worked (much to my surprise lol). I haven't been using Linux for long, but some of the basic commands are starting to come back to me from when I used Unix sooooo long ago. Thank you for being so patient, giving me those commands, and being thoughtful enough to help me!
 

In case anyone else has this problem, the file was located in /usr/share/doc/torsmo/examples/torsmorc.sample.gz
sudo -s to login as root, then gzip -d torsmorc.sample.gz 


Artemis[/QUOTE]
 No problem; glad you got it working. And just a quick note: since it's generally a good idea to avoid using root/super-user privileges when possible, you can just use an editor like vi/vim/emacs to open the file:
```

$ vim /usr/share/doc/torsmo/examples/torsmorc.sample.gz
```

You don't need to be super-user to read the file (it's intended to be read by all the system's users) and Vim is smart enough to decompress the file.

lt_kije

---

