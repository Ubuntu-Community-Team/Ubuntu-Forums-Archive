---
title: "Files not copying to external HD; bye bye music"
date: 2008-06-22
forum: General Help
---

### Post by c0rd3l1a on 2008-06-22
I just upgraded to Heron (from Drake) and went to throw all my backed up data from my external hd back onto my computer. At least half, possibly much more, of my files are not on my external hd. This happened to me once before a couple of years ago, with a different external hd. 

Basically, all of my folders copied, but very little of the actual files within the folders copied. It looks like most but not all things that were 2 folders deep copied and almost nothing that is 3 or more folders deep copied. It looks like it is mostly my music files that were affected, possibly because they got moved in larger bunches or because there are more subfolders?

Because I have tried the external hd with 3 different computers with different OSes I know that the problem is that these files actually don't exist and not that they just aren't being recognized.

I had initially just copied and pasted all the files onto the external hd using the file manager. 
My questions:

1. What happened?
2. Is this common? A flaw with Drake?
3. Is there a better way to back up data?
4. Does anyone want to come over to my house and re-rip 300 cds for me?

---

### Post by billgoldberg on 2008-06-22
> **c0rd3l1a said:**
> I just upgraded to Heron (from Drake) and went to throw all my backed up data from my external hd back onto my computer. At least half, possibly much more, of my files are not on my external hd. This happened to me once before a couple of years ago, with a different external hd. 

Basically, all of my folders copied, but very little of the actual files within the folders copied. It looks like most but not all things that were 2 folders deep copied and almost nothing that is 3 or more folders deep copied. It looks like it is mostly my music files that were affected, possibly because they got moved in larger bunches or because there are more subfolders?

Because I have tried the external hd with 3 different computers with different OSes I know that the problem is that these files actually don't exist and not that they just aren't being recognized.

I had initially just copied and pasted all the files onto the external hd using the file manager. 
My questions:

1. What happened?
2. Is this common? A flaw with Drake?
3. Is there a better way to back up data?
4. Does anyone want to come over to my house and re-rip 300 cds for me?

The most likely thing is you didn't remove your external hd properly.

(most people don't do this, and every now and things do go wrong)

If that's not the case, then I don't know.

You could put everything in 1 big container (.tar) when backing up.

---

### Post by c0rd3l1a on 2008-06-22
This external hd was always properly unmounted. So was the one previous when this happened a couple of years ago. 

I'll try the .tar next time. Thanks.

Also, the miscopied files/folders from the last one were not transferred onto this one because there was yet another external hd inbetween these two that met with an untimely death with the cement floor of my loft. So I know that this specific instance of miscopied files happened this calendar year (since I started using the new external hd).

I used the search feature and couldn't find any other reported instances of this.

---

### Post by ginjabunny on 2008-06-22
A bit late this tip - I always check the source and destination after copying, compare total size, no of files and folders, if there is a discrepancy then something didn't copy.

Also remember that different file systems have different rules on file names and sizes (e.g. FAT32 limits files to 2GB).

---

### Post by c0rd3l1a on 2008-06-22
How should I format my external hd? Is there a file system that is preferable that might prevent this from happening again? It is currently FAT32.

---

### Post by c0rd3l1a on 2008-06-22
Some more information:

It looks like there are some folders that didn't copy as well.

Files that were moved in smaller batches later on all seem to be intact and present.

---

### Post by ginjabunny on 2008-06-25
I also tend to use FAT32 for external drives because up until recently it was the only file system which was supported by Linux, Windows and MacOSX which allowed me to transfer files between them.
If you are just doing a backup and restore then maybe it would be better to use the same filesystem as the one you are backing up from.
I also tend to use my network server which is also Linux usinf NFS so I don't get the problem.

You could try rsync to copy and make it verbose so you can see what is happening, if you have a lot of files then maybe pipe the output into a text file them you can scan it for errors.

---

