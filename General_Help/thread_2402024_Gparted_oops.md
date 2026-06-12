---
title: "Gparted oops"
date: 2018-09-25
forum: General Help
---

### Post by frank105 on 2018-09-25
[FONT=arial]I did it this time..

I have a 1 TB HD with a few partitions on it.  I had 2 partitions about 450gb each.  1  was pretty full and the second partition I didn't need anymore.  So I deleted the un needed partition and extended the full partition.

Okay - so all was going well but I didn't realize that my laptop came unplugged.  

I came back a while later and rebooted and inspected everything and the partition delete and the partition extend were complete but the new larger partition would not mount.   I  didn't record exactly the error (sorry).

But in Gparted I ran "Check" partition and it just cooked for an hour.  It seemed like it wasn't doing anything so I quit it. 

I looked and Gparted was running the command : [COLOR=#231F20]e2fsck -f -y -v -C 0 '/dev/sdb2'[/COLOR]
I ran that in the terminal and it finished in about 10 minutes.

[/FONT][COLOR=#231F20][FONT=Nylas-Pro][FONT=arial]It had like 10,000 of the following two questions:

Directories count wrong for group #3280 (1, counted=0).[/FONT]
[/FONT][/COLOR]
[COLOR=#231F20][FONT=Nylas-Pro][FONT=arial][FONT=Verdana]Fix? yes[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#231F20][FONT=Nylas-Pro][FONT=arial][FONT=Verdana]Free inodes count wrong (31724695, counted=31750379).[/FONT][/FONT]
[FONT=arial][FONT=Verdana]Fix? yes[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#231F20][FONT=Nylas-Pro][FONT=arial][FONT=Verdana]
And then it ended with:

Recreate journal? yes[/FONT][/FONT][/FONT][/COLOR]
[COLOR=#231F20][FONT=Nylas-Pro][FONT=arial][FONT=Verdana]Creating journal (262144 blocks):  Done.[/FONT][/FONT][/FONT][/COLOR]
[COLOR=#231F20][FONT=Nylas-Pro][FONT=arial][FONT=Verdana]*** journal has been regenerated ***[/FONT][/FONT][/FONT][/COLOR]
[COLOR=#231F20][FONT=Nylas-Pro][FONT=arial][FONT=Verdana]/dev/sdb2: ***** FILE SYSTEM WAS MODIFIED *****[/FONT][/FONT][/FONT][/COLOR]
[COLOR=#231F20][FONT=Nylas-Pro][FONT=arial][FONT=Verdana]        1813 inodes used (0.01%, out of 31752192)[/FONT][/FONT]
[FONT=arial][FONT=Verdana]          34 non-contiguous files (1.9%)[/FONT][/FONT]
[FONT=arial][FONT=Verdana]           2 non-contiguous directories (0.1%)[/FONT][/FONT]
[FONT=arial][FONT=Verdana]             # of inodes with ind/dind/tind blocks: 1246/1247/1248[/FONT][/FONT]
[FONT=arial][FONT=Verdana]             Extent depth histogram: 89/8[/FONT][/FONT]
[FONT=arial][FONT=Verdana]     4453136 blocks used (3.51%, out of 126978560)[/FONT][/FONT]
[FONT=arial][FONT=Verdana]           0 bad blocks[/FONT][/FONT]
[FONT=arial][FONT=Verdana]           2 large file[/FONT]s[/FONT]
[FONT=arial][FONT=Verdana]         100 regular files[/FONT][/FONT]
[FONT=arial][FONT=Verdana]           3 directories[/FONT][/FONT]
[FONT=arial][FONT=Verdana]         405 character device files[/FONT][/FONT]
[FONT=arial][FONT=Verdana]         424 block device files[/FONT][/FONT]
[FONT=arial][FONT=Verdana]         439 fifos[/FONT][/FONT]
[FONT=arial][FONT=Verdana]           0 links[/FONT][/FONT]
[FONT=arial][FONT=Verdana]           0 symbolic links (0 fast symbolic links)[/FONT][/FONT]
[FONT=arial][FONT=Verdana]         433 sockets[/FONT][/FONT]
[FONT=arial][FONT=Verdana]------------[/FONT][/FONT]
[FONT=arial][FONT=Verdana]        1804 files[/FONT][/FONT]

[/FONT][/COLOR]
[FONT=arial]

  
Looks good BUT - now the partition can mount but there is almost nothing on it.  There is a "Socket" file named pictures.  

What can I do to see if I can rescue the data?

Thanks so much in advance for any advice.

Regards,
Frank[/FONT]

---

### Post by frank105 on 2018-09-25
Forgot to mention - it is an EXT4 partition.

Thanks again

---

### Post by oldfred on 2018-09-25
Power failure of any type in the middle of a partition change often causes major issues.
If it had completed the fsck should have fixed it. 
Often you just have to restore from your backups.

       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb2 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb2
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb2

You can try testdisk and its deeper search. It may see old partition (size) and data. If it does see files immediately back then up.
there also then is photorec. It only recovers files by type or just the extension, not full file name.
      
 [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) 
           
 [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step) 
    
I had an older backup, and used photorec on a not very large drive. It took over nite to copy files to another drive. And then I had hundreds of .txt files. It also recovered the deleted files. Some even older than backup, many newer but lots of grep & comparing of files to recover them. Weeks of work. Or oldfred backs up more often.

---

### Post by frank105 on 2018-10-21
Thanks
I used TestDisk by CGSecurity.org.  Worked fine. 

It took a really long time and I ended up running out of space on my drive I was copying too. (duh)...
I then learned it is better to copy sections at a time.

One other note - I ran into (what looks like a common problem) that  after copied the file is owned by ROOT so it can't be viewed or deleted  by USER.    
(Again - simple to understand - you run Testdisk as root... so of course resulting files are owned by ROOT.... duh)

Google quickly led me to posts about changing ownership.  
Here is where I went...
[https://askubuntu.com/questions/263450/folders-showing-lock-icon](https://askubuntu.com/questions/263450/folders-showing-lock-icon)

It took a bit to run but it seemed to solve everything. 
Thanks so much!
(keys to help others searching for similar answers:  restored files  won't play.  X on files restored. can't open. don't have permission)

---

