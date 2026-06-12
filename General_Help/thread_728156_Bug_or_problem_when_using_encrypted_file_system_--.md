---
title: "Bug or problem when using encrypted file system --error at time of updates"
date: 2008-03-18
forum: General Help
---

### Post by MountainX on 2008-03-18
Should I report this as a bug?

I set up a new clean install of Kubuntu Gutsy i386 using the excellent steps found here:
[http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)

I had a non-encrypted /boot partition and then I had root, /home and swap in the LVM group in the encrypted partition as per the instructions above.

As soon as the install completed I applied the updates. The updates gave an error. When I rebooted, I got error 15: file not found. I went through a bunch of trouble shooting steps, including booting to live CD, starting grub and trying to fix the problem. But in the end things were really screwed up and I could not salvage the installation. I suspect that the updates gave me a new kernel and that it could not be installed properly due to my partition configuration -- but that's just a guess.

UPDATE:
I just tried again with the same result. I did the text-based installer for Kubuntu Gutsy i386. I used the same steps to created an encrypted file system at the link above. After installation, I booted into Kubuntu and the first thing I did was use Adept Updater to update my system. I found 160 packages to upgrade and downloaded 246 MB. 60% through the installation (screen says preparing to configure libqt3-mt..) I got an error:
Could not commit changes - Adept Updater:
There was an error committing changes. Possibly there was a problem downloading some packages or the commit would break some packages.

Last time this happened I could not recover and I had to completely reinstall. What should I try this time?

---

### Post by MountainX on 2008-03-18
Thanks to the following post, I got past that error:
[http://ubuntuforums.org/showpost.php?p=4539588&postcount=12](http://ubuntuforums.org/showpost.php?p=4539588&postcount=12)

```
sudo dpkg --configure -a
```

I never had any problems like this in Ubuntu previously. Is this a Kubuntu issue? Am I doing something wrong? Thanks

---

