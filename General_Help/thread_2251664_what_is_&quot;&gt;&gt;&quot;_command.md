---
title: "what is &quot;&gt;&gt;&quot; command?"
date: 2014-11-05
forum: General Help
---

### Post by shahin on 2014-11-05
Good Evening 
I got this somwhere online; the procedure for adding md5 checksum to a tar file. But I now think it is incorrect. When I check the MD5, it gives me an error. What is ">>" command? What should I be doing instead? 
```
sansari@ubuntu:&#8254;/stock3$ md5sum -t N900PVPUCNC5_N900PSPTCNC5_N900PVPUCNC5_HOME.tar >> N900PVPUCNC5_N900PSPTCNC5_N900PVPUCNC5_HOME.tar
sansari@ubuntu:&#8254;/stock3$ md5sum -c N900PVPUCNC5_N900PSPTCNC5_N900PVPUCNC5_HOME.tar
md5sum: N900PVPUCNC5_N900PSPTCNC5_N900PVPUCNC5_HOME.tar: no properly formatted MD5 checksum lines found
sansari@ubuntu:&#8254;/stock3$ 

```

---

### Post by papibe on 2014-11-05
Hi shahin.

'>>' is like '>' but it does not destroy the destination. Instead it adds the content to the end of the file.

I don't think that would work either.

We may come with more suggestion if you explain a little bit more what you are trying to do.

Regards.

---

### Post by shahin on 2014-11-06
Hi Papibe,
I just want to create MD5 authenticated file of the tar file. I'll try 

```
md5sum -t N900PVPUCNC5_N900PSPTCNC5_N900PVPUCNC5_HOME.tar > N900PVPUCNC5_N900PSPTCNC5_N900PVPUCNC5_HOME_2.tar
```

And see if it gets me what I want.

---

### Post by coldcritter64 on 2014-11-06
That may very well erase the tar archive with only the md5 left. > means overwrite the whole target (your archive). >> is for appending as you are trying to do. BE CAREFUL using a single ">".

---

### Post by shahin on 2014-11-06
Thanks. I am forwarding it to a file named slightly different; I added a "_2" to it. 
N900PVPUCNC5_N900PSPTCNC5_N900PVPUCNC5_HOME_2.tar

---

### Post by coldcritter64 on 2014-11-06
I didn't note the name change. That should be ok.

---

### Post by shahin on 2014-11-06
This is where I got the command: [http://www.rwilco12.com/forum/showthread.php?tid=92]("http://www.rwilco12.com/forum/showthread.php?tid=92")

---

### Post by coldcritter64 on 2014-11-06
Usually as I've seen them used, md5s are supplied separate to but with the file on websites etc. That is you download the file, copy and paste the md5 from the same site to a text file on your machine and run a check on the downloaded file. When the md5sum command is used on the downloaded file it outputs an md5 hash. The one copied to the text file is compared to the calculated value (can be done manually by pasting the terminal output under the website one in the text file and visually compared or their are gui apps that can do the comparison a bit easier).

This is the first time I've heard of embedding the md5 in the archive. Though after some googling it seems it can be done that way as well. I'm not sure of the exact procedure though for such advanced hashing.

---

### Post by shahin on 2014-11-06
That did not work for me. I think I just got the hash of the original file in the 2nd file. I want the hash to be added to the original file.

---

### Post by coldcritter64 on 2014-11-06
Yes that sounds right now I look at the command again.

The redirect does _not_ also copy the contents of the archive if you change the name, just creates an empty archive with the hash in it. Try creating a second copy of the archive and storing it safely as a backup, in case of errors or accidents. 

Then try again without the name change and see if the md5 can be added with that command.

---

