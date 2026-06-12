---
title: "Ubuntu taking up twice as much space after copying from another partition"
date: 2007-03-24
forum: General Help
---

### Post by monaleilani on 2007-03-24
I moved a partition containing Ubuntu to a partition to the front of the disk, making it hda1.. On hda2, where Ubuntu used to be, it took up 7.5gb out of 11.5. Now on the first partition, it takes up 16 / 23 gb. And I've not made any installations or big changes or anything. I asked in an IRC channel and the only good response given to me was that sometimes you have files with big chunks of zero data that don't take up space until you copy them. I used the command dd to do the copy.
Does anyone have any ideas on what happened or how to fix it? I've lost alot of space on a small hdd..

:confused:

---

### Post by bogoliubov on 2007-03-24
Hmm, I don't know what could have caused this. But perhaps you can see if the files you've copied have changed, it there are multiples etc.

For instance, you can do 'ls -l -R' > filelist' for both flesystems and compare.

---

### Post by monaleilani on 2007-03-24
Well, this is rather odd.. But it seems to have fixed itself. I restarted soon after posting this thread and had some problems with grub... So I spent a while working with that and when I finally got Ubuntu back up the space taken up on the 1st partition was 4 gb. I must have been incorrect about how much space it took up when it was on the 2nd partition - 4gb is definitely not 7.5 gb.
Thanks for the help! :)

---

### Post by nasov on 2008-01-26
actually mu ubuntu is taking up 7.5gb and im just wondering if there is a way of "cleaning" the drive out of unnecessary files other than apt-get clean or autoclean?

any clues?

---

