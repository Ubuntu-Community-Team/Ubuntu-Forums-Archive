---
title: "Using Tar utility to untar a continuous stream"
date: 2014-01-28
forum: General Help
---

### Post by Sajal_Malhotra on 2014-01-28
Hi,

I was just exploring an option if by using "tar -xvf -" option or any other option i could untar a live stream of input file.
Currently in my application:
- A ".tar" File is being fetched by my application from a remote server.
- now i receive this file in multiple chunks of 256 bytes each
- I assemble these chunks to form the original ".tar" file and then feed it to "tar" utility to extract its content to my local flash drive.

Is there a way that the "tar" utility provides using which i can directly feed the 256 bytes chunk into it and it starts extracting the contents.
So i dont wait for all the chunks to be received from Server and assemble them before feeding it to "tar":
So Pseudo algo that i want to achieve:
1. Get chunk of master .tar file from server
2. Feed this chunk to "tar" utility to extract the contents
3. Discard the Chunk
4. Goto Step 1 till all chunks are downloaded.

---

### Post by sudodus on 2014-01-28
Welcome to the Ubuntu Forums :-)


Well, you can use tar with pipeline, for example expanding a compressed file (for example by zcat) and piping it into tar, which in turn extracts a directory tree. So I guess it would be possible to use it with a live stream too.

Please explain with more details, what you want to do. It will make it easier to discuss the problems and possibilities.

---

### Post by Sajal_Malhotra on 2014-01-28
Hi Sudodus

Thanks a lot for a quick reply. 

Actually my problem is that the platform that i am using has a limited RAM left (8Mb Left).
And there are occassions when i get a tar file of size >8Mb from server which i then have to extract and store it in Flash.
The Remote Server sends this tar file in multiple chunks of 256 bytes each which i re-assemble into the RAM and then feed it to tar utility to extract it to the flash. 

However now since RAM i am short of RAM and file size being downloaded from server are getting bigger in size, i cannot wait for the entire tar file to be re-assembled before i extract it.
An alternate could be to store chunks in flash and once all chunks are downloaded then feed them to tar. But this will slow up the whole process.

Hence i was looking for a solution where i need not wait for entire file to re-assemble before feeding it to tar util. As soon as i receive a chunk i feed it to tar util and drop that chunk out of RAM.
I am also quite pessimistic about possibility of this but till now could not find a documented reason anywhere on internet as to why this should not be possible.

---

### Post by sudodus on 2014-01-29
I am afraid that your task is too advanced for me. I hope someone else can help.

---

