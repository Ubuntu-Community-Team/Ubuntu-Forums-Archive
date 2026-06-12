---
title: "Free space leaks after shift-deletes"
date: 2008-02-19
forum: General Help
---

### Post by Littleweseth on 2008-02-19
Hi, all;

I've been happily deleting files in Konqueror using shift-delete, which in theory should send files directly to oblivion (do NOT pass go, do NOT collect $200) and give me back some free space. However, it has not. I have a 3gb disparity between what df says i am using and how much free space i have.

According to some googling, this is a problem that happens when files are deleted, but programs are still using them - the files are marked as gone, but the space is not made available for reallocation to new files until the programs using the files are closed.

It therefore turned out that my decision to hard-kick my unresponsive X session via ctrl-alt-bkspc was ill-advised - the programs that were using the 3gb of files i had just deleted never got a chance to say 'hey, I'm done! mark the space as free now!' Now i have 2-3gb of what should be free space, but isn't.

--

The partition in question is /dev/sda3 mounted as /home (i have /home/ mounted on a separate partition, as opposed to part of the partition mounted at /.) I have tried fsck (with various options, including -D) with no success in reclaiming my disk space (though i'm sure my directory trees are happy.)

Following are the pertinent outputs from du -sm /home/* | sort -n and df -h.

root@pelleas:/home/lws# du -sm /home/* | sort -n
1       /home/lost+found
18650   /home/lws
19403   /home/shared

Those with desktop calculators will note that the above numbers sum to 38,054MB.



root@pelleas:/home/lws# df -h /home
Filesystem            Size Used Avail Use% Mounted on
/dev/sda3              41G   38G  652M  99% /home

or :
root@pelleas:/home/lws# df -m /home
Filesystem           1M-blocks Used Available Use% Mounted on
/dev/sda3                40961     38228       652  99% /home


Note especially that 40961-38228 = 2733, or 2.67gb of unused space, but there are only 652mb free.

I don't think software versions are particularly pertinent to the problem, but i'm running Ubuntu 7.10 with proc/version : Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007

--

Any help in getting mah disk-ette spacez backs would be appreciated. (Wierd fsck options? goat sacrifices under the full moon? tai chi?)

--

Edit 1 : before anyone asks pointed questions : yes, i have done 'locate Trash' as root and rm'ed all findings without prejudice. That freed up a couple hundred mb that i needed, but there's still 2gb on the run.

- lws

---

### Post by mozetti on 2008-02-19
I can't help you get your free space back, but I did enjoy reading that. :)

---

### Post by Littleweseth on 2008-02-19
I read a lot of David Eddings and Raymond Feist during my formative years as a writer of the English language. Does the quirkiness show? :p

-lws

---

### Post by Littleweseth on 2008-02-20
bump.

---

### Post by peedeeramone on 2008-02-20
wow that blows...

ive never heard of that, so i have no idea, but good luck

---

