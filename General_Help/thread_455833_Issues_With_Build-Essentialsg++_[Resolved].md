---
title: "Issues With Build-Essentials/g++ [Resolved]"
date: 2007-05-27
forum: General Help
---

### Post by TriJump on 2007-05-27
Okay I am trying to install build-essentials so that I can try to get Wine up and running on Feisty.  I am stuck with an internet connection so I am relegated to downloading packages from the repositories on another computer, putting those on my thumb drive and transferring them over.  

So anyway, I download the build-essential package, get it into Ubuntu, double click to try and install and I get a dependency issue - it says it requires g++.  So I download g++, try to install and it says I need g++-3.3.  So I download that one, try to install, and it says I need libstdc++5-3.3-dev.  So again, I download that and try to install it and I get a dependency issue that says g++-3.3 needed.  So now I feel I am stuck in a loop, libstd needs g++-3.3 to work, and g++-3.3 needs libstd to work.

 I've searched through the forums trying to find an answer and couldn’t.  So am I stuck in a loop or did I miss something that the beginning with the build-essential pack?  Any help would be greatly appreciated.  Thanks.

---

### Post by taurus on 2007-05-27
The package build-essential and all it dependencies are on the CD so insert the CD that you installed with into a drive and run

Applications -> Accessories -> Terminal
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by TriJump on 2007-05-27
Thanks for the quick reply, I'm going to give this a shot and see what happens.

---

### Post by TriJump on 2007-05-27
Excellent, it worked perfectly thank you for the help.

---

