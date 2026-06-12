---
title: "[SOLVED] checksum generation of entire directory"
date: 2008-01-25
forum: General Help
---

### Post by flaggh on 2008-01-25
I'm trying to generate a checksum file to check the contents of an entire directory that I copied from one hard drive to another.  Is there an easy way to do this?

I found this command:
```
find /dir -type f | xargs md5sum
```
at this forum:
[http://www.linux.org.za/Lists-Archives/glug-tech-0412/msg00087.html]("http://www.linux.org.za/Lists-Archives/glug-tech-0412/msg00087.html")

but it does not appear to be able to handle directories with spaces in the names.

Is there an easy way to do this?

Thanks in advance.

---

### Post by accatagon on 2008-01-25
"tar cf - /dir  | md5sum" should work. It creates an archive of /dir using tar, which then sends the archive to standard output, which is piped to md5sum. Generally I think it's assumed you will only be md5summing archives and separate files, which is why the slightly circuitous route is necessary.

---

### Post by flaggh on 2008-01-26
Thanks for the reply.  Unfortunately that method won't work for me because the directory I copied is rather large and would require more disk space than I have to create a tar of it.  Any other ideas?

---

### Post by accatagon on 2008-01-27
Disk space shouldn't be a problem. The command "tar -cf - /dir" doesn't actually write anything to the hard disk. If you were to simply run it by itself (try it on something small), it will output the tar to standard output without writing anything to disk (though the act of printing all that output in and of itself will make your computer cry). In one of the cooler features of unix/linux, the tar program basically considers the standard output to be the same as any other file, and writes to it just like writing to "foo.tar". If this output isn't piped to anything, it shows up on your terminal. In the case of the command I sent you, it is sent to the standard input of md5sum, which then begins computing the checksum. Both processes run in parallel, with tar feeding its standard output into the standard input of md5sum. Admittedly, having to run tar in addition to md5sum might be an additional computational load that could be avoided by a more clever design, but odds are that the speed is limited by your hard disk read speed anyway, and quite frankly, it's just way easier to do it this way.

Obviously another concern is RAM usage. I didn't think it would be a problem, but just to check, I mounted my windows partition as read-only and tried running the command on the WINDOWS folder (you know, the huge one). I got no errors, indicating that it was not trying to write to the windows partition at least, and after 5-10 minutes my ram usage didn't vary by more then 10 megs.

One caveat though. I got sick of waiting for it to finish, so expect whatever you're doing to take a long time. If you don't trust your computer, change the command to "tar -cvf - /dir | md5sum" to get tar to list every file it is opening. Try it out on smaller folders if you like just to make sure that it doesn't write to disk and it does work. You can also use a live cd and make sure everything is mounted read-only.

---

### Post by 5-HT on 2008-01-27
md5deep can compute message digests recursively through a directory structure. It would generate a hash for each file though. You'll need to create an archive or image as a container if you'd only like one digest for all the contents.

cheers,

---

### Post by accatagon on 2008-01-27
He's right. My way is the easiest to get one single md5 hash, but "md5deep -r /dir" will give you a hash for each file, which is probably to your advantage. If you use "md5deep -lr /dir > file", you can save the hashes for all the files in one file (this will actually take up disk space, but only 70 bytes or so per file hashed). The "l" option only saves the relative filenames, and the "r" option specifies recursion. If you do this for both versions of the directory, then you get the HUGE advantage that if you run "diff file1 file2" for the two files generated, you know exactly which file was not copied correctly. The disadvantage to this approach is the disk usage of 70 bytes per file hashed, but unless you have a lot of really tiny files, it shouldn't be that much. One problem is you need to make sure that you run them with the same command, or else the relative filenames will be different. Good luck with whatever you do.

---

### Post by flaggh on 2008-01-28
Thanks!  md5deep was just what I was looking for.  That way I can just md5sum -c file.md5 the checksum.

---

### Post by bodhi.zazen on 2008-01-28
you can use md5sum directly.

cd into the directory ( I will use ~/bin for now)

then :

> bodhi@GutsyVZ:~/bin$ ls                                          
lsn  test  test.root

bodhi@GutsyVZ:~/bin$ md5sum * > bin.md5                            
bodhi@GutsyVZ:~/bin$ md5sum -c bin.md5                            
lsn: OK
test: OK
test.root: OK

bodhi@GutsyVZ:~/bin$ cat bin.md5                                 
0a363eb6f6b69b172b99602148849e5b  lsn
ca0321dafa2893882ba55f2548e09b25  test
d41d8cd98f00b204e9800998ecf8427e  test.root

---

### Post by flaggh on 2008-01-31
Thanks for the reply.  I realize I can generate checksums for the contents of a single directory using md5sum, however md5sum will not generate checksums for the contents of subdirectories.  I would like to be able to generate checksums for the entire directory contents, including subdirectories.  md5deep searches all subdirectories recursively and generates checksums for the entire contents of the folder.

---

