---
title: "Beagle Search Upgrade"
date: 2008-05-04
forum: General Help
---

### Post by dwitkin on 2008-05-04
Hello. I'm still fairly new to Ubuntu and Linux, so bear with me through this question.

I'm using Ubuntu Hardy and have Beagle 0.3.3. There is a newer version of Beagle out, version 0.3.7, that I would like to use. The Ubuntu update manager doesn't notify me that I can upgrade to the new version (is this because it is not supported by Hardy?).

The Beagle project page allows me to download a .tar file that appears to have the files for 0.3.7, but I don't know how to install it. The instructions on the Beagle project page discusses using the 'sudo apt-get install beagle' command, but I believe I did this and it installed the 0.3.3 version.

In short, I guess my question is: If there is no '.deb' file available, and the update manager doesn't notify me that an update is available, does that need I'd need to go through the whole 'makefile' process to build from the source in order to upgrade to 0.3.7? (I've never done that before and frankly it seems a little intimidating to an ex-Windows user.) If that's the case, are there any very easy to use instructions for the process? Preferably, something with screenshots.

Thanks for your help.

---

### Post by macaholic on 2008-05-04
If you are new to linux I wouldn't suggest installing it from the source, but if you would like to try, I would be happy to help. It is not in the Hardy repositories because the dev(s) that mainatin that particualr package haven't decided to upgrade it since it may require its dependencies to be upgraded and could cause issues.
EDIT: I have successfully installed the latest version of beagle from the source, so if you want my offer still stands.

---

### Post by dbera on 2008-05-05
[https://bugs.launchpad.net/ubuntu/+source/beagle/+bug/225746](https://bugs.launchpad.net/ubuntu/+source/beagle/+bug/225746)

Maybe wait for a few days ...

---

### Post by dwitkin on 2008-05-05
First, thanks to both of you for your replies.

Macaholic, I will probably take you up on your offer but based on Dbera's comment, I'll wait for a more stable release of Beagle to try it (i.e., her link shows that 0.3.7 has some stability issues).

That said, are there some specific instructions for performing the build that you can provide? I'm comfortable at the terminal, but still need very clearly written command line instructions.

Thanks again.

---

### Post by dbera on 2008-05-05
> **dwitkin said:**
> ...I'll wait for a more stable release of Beagle to try it (i.e., her link shows that 0.3.7 has some stability issues)

How did you get that impression from the launchpad bug link ? These bugs are formal ways packagers upgrade packages and they do not necessarily mean there is a bug in the package. Also I could not find anything there which suggests there is any stability problem.

---

### Post by dwitkin on 2008-05-05
> **dbera said:**
> How did you get that impression from the launchpad bug link ? These bugs are formal ways packagers upgrade packages and they do not necessarily mean there is a bug in the package. Also I could not find anything there which suggests there is any stability problem.

dbera - I may be misinterpreting the information, but when I used the link you provided, here was the text that I thought suggested that the 0.3.7 release was unstable: 
"beagle (0.3.7-1) unstable; urgency=low"

---

### Post by dbera on 2008-05-05
"beagle (0.3.7-1) unstable" means the beagle package in ubuntu is based on "debian unstable" branch (debian has three branches - stable, testing, unstable). You can go and read about them in details ... but if you are not interested, I suggest you to ignore everything on that bug page other than the fact the 0.3.7-2 has been uploaded to ubuntu repositories. The rest is all technical detail only relevant for the ubuntu developers :)

---

