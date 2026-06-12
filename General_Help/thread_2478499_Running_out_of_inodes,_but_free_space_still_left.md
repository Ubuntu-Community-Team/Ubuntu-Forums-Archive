---
title: "Running out of inodes, but free space still left"
date: 2022-08-28
forum: General Help
---

### Post by andy205 on 2022-08-28
I have server with Ubuntu 18.04 and 15GB HDD. I still have 4GB left, but my HDD run out of inodes. If I understand it correctly I have too many small files and my HDD can't store anymore files, although there is still space left on the disc.

It is a webserver with a Docker and nothing else. Could you help me identify what is causing this problem? If think it might be Docker itself doing something crazy or some of my Docker containers (eg. is filling up HDD with small session files?). But I can't seem to find the culprit.

In the past I have deleted some log files etc. but it filled up inodes back to 100% in 2 days... .

---

### Post by SeijiSensei on 2022-08-28
It looks like you can't increase the number of inodes without recreating the ext filesystem: [https://ma.ttias.be/how-to-increase-amount-of-disk-inodes-in-linux/](https://ma.ttias.be/how-to-increase-amount-of-disk-inodes-in-linux/)

You can use the "find" command to list all the files below a certain size:
```

cd /
sudo find . -size -1000b > /small-file-list

```
This creates a list of all files smaller than 1000 bytes and writes the list to a file called small-file-list in the top directory. You can peruse it and see if there are obvious candidates for deletion.

---

### Post by ajgreeny on 2022-08-28
Just out of interest, do you currently have more than the two suggested kernel versions in your system, along with the linux-header packages that I think always come with them.

Those linux-header packages contain a lot of small files and I believe can use up many inodes.  Removing unnecessary linux-header packages may free sufficient inodes to at least help out with your problem.  The packages are not needed anyway so why not give it a try if you have them still installed.

EDIT:
I have just checked on one of my systems and removed the header packages for the second kernel I have installed.  The removal did reduce inode percentage but by only 2% so I suspect that you can forget about them as the cause of your problem.
Of course, the small file numbers could be from many other sources so SeijiSensei's suggested command may help you find them.

---

### Post by HermanAB on 2022-08-29
Maybe your use case will work better with XFS.

---

### Post by oldfred on 2022-08-29
Does df -i tell you anything?

I have in my notes that this can find large files.
sudo find / -name '*' -size +1G    # files larger than 1GB
but in looking at man page find can use less than also.

> [FONT=monospace][COLOR=#000000]-size [/COLOR][COLOR=#000000]n[/COLOR][COLOR=#000000][cwbkMG] [/COLOR]
              File uses less than, more than or exactly [COLOR=#000000]n[/COLOR][COLOR=#000000] units of space, rounding up.  The following suffixes can [/COLOR]
              be used: [/FONT]

---

### Post by andy205 on 2022-09-11
> **SeijiSensei said:**
> It looks like you can't increase the number of inodes without recreating the ext filesystem: [https://ma.ttias.be/how-to-increase-amount-of-disk-inodes-in-linux/](https://ma.ttias.be/how-to-increase-amount-of-disk-inodes-in-linux/)

You can use the "find" command to list all the files below a certain size:
```

cd /
sudo find . -size -1000b > /small-file-list

```
This creates a list of all files smaller than 1000 bytes and writes the list to a file called small-file-list in the top directory. You can peruse it and see if there are obvious candidates for deletion.


I'm out of inodes, I can't create a new file.

---

### Post by andy205 on 2022-09-12
Ok,it seems I solved it. 

I found command that tells how much inodes folder takes  [COLOR=#D4D4D4][FONT=&quot]for i in /var/somefolder/*; do echo $i; find $i |wc -l; done[/FONT][/COLOR] and I found folder that had huge number of inodes. Belogning to Docker container running PHP. Cointainer is probably misconfigured and is filling up disc space. Deleting him and starting him up again solved the issue. Although it will fill up space again in the future. But now at least I know what's wrong.

I didn't figured it out before, because I was logged in as a user and didn't have permission to access Docker folders. That's why I didn't find out that the ofending folder is Docker folder. This time I logged in as a root.... .

---

### Post by ajgreeny on 2022-09-12
Great news!

I suppose you now need to investigate why the docker folder is becoming so hungry for those inodes.
However, if you are happy that the problem is now  solved please mark it SOLVED using the Thread Tools menu up top.

---

