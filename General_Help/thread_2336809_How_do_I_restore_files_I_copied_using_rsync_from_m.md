---
title: "How do I restore files I copied using rsync from my ext HDD?"
date: 2016-09-11
forum: General Help
---

### Post by nhtrader on 2016-09-11
rsync  version 3.1.0  protocol version 31
ubuntu 14.04.5 LTS (x64)
kde 4.13.3


How do I restore those files I copied using rsync from my ext HDD to their original DIR?

I have to say that using rsync to copy/backup files was easy (from /home/user to ext. HDD). 
Now all I want to do is copy/restore some of those files from the ext. HDD to the local HDD (original DIR.)
The problem stems from the fact that rsync fails when 100,000+ files are to be transferred. 
rsync produces an error: "/usr/bin/rsync: Argument list too long"


Here are the details of what I've done ....

Below are the commands I used to make copies of all of my DIRs and files (ie:/home/user/Data).

```
find /home/user/Data -type f -mtime 40 > /home/user/rsyncFileList.txt
rsync -aWvR --files-from=/home/user/rsyncFileList.txt  /  /media/user/BkUpFromextHDD/BU-user/

```
To explain, I needed the find command b/c without it rsync produced this error: "/usr/bin/rsync: Argument list too long"
The problem is that my DIR contains approx. 500,000 files. I don't know why rsync can't handle large numbers of files, but it can't.
So the commands above work around rsync's "argument list limit", and in using these 2 commands, I can copy all of my files to my ext. HDD.


Now I wish to reverse the process and restore a sub-set of my ext. HDD's copy of the files. 
I wish to copy all of the files from May 2016 from my ext. HDD, which means that any file or DIR that contains the pattern "201605" should be returned(copied back) to the local HDD.

Again, the large number of files in my DIR tree is problematic for rsync so using this simple command fails:
```
      rsync -aWvR --ignore-existing /media/user/BkUpFromextHDD/BU-user/home/user/Data/ /home/user/Data
      "/usr/bin/rsync: Argument list too long"

```
Secondly, the command above isn't exact what I want b/c I would like to copy only those DIRs and filenames containing the pattern "*201605*"


I've tried the steps below and I can't get it work.

I used these commands to create 2 files: one for all DIRs containing "201605" and another for all files containing "201605"

```
    find /media/user/BkUpFromextHDD/BU-user/home/user/Data -type f -name "*201605*" > FL4kub1FromMediaBU-201605.txt
    sort FL4kub1FromMediaBU-201605.txt > FL4kub1FromMediaBU-201605s.txt

```        (here is a sample of one line in the file = /media/user/BkUpFromextHDD/BU-user/home/user/Data/briefing-ss/20160502/FNPP-data.txt)

```
    find /media/user/BkUpFromextHDD/BU-user/home/user/Data -type d -name "*201605*" > DL4kub1FromMediaBU-201605.txt
    sort DL4kub1FromMediaBU-201605.txt > DL4kub1FromMediaBU-201605s.txt

```        (here is a sample of one line in the file = /media/user/BkUpFromextHDD/BU-user/home/user/Data/briefing-ss/20160502)

The sorted DIR listing(DL4kub1FromMediaBU-201605s.txt) contains approx. 1,000 DIRs 
and the sorted Filename listing(FL4kub1FromMediaBU-201605s.txt) contains approx 100,000 files

If I use the following command for the DIR listing, it fails:
```
    rsync -n -aWvR --include-from=DL4kub1FromMediaBU-201605s.txt /media/user/BkUpFromextHDD/BU-user/home/user/Data /home/user/Data

```
If I use the following command for the Filename listing, it fails:
```
    rsync -n -aWvR --files-from=FL4kub1FromMediaBU-201605s.txt /media/user/BkUpFromextHDD/BU-user/home/user/Data /home/user/Data

```

What is(are) the command(s) needed to restore my files from May 2016?
Why is copying these files back so much harder than backing them up?

---

### Post by papibe on 2016-09-11
Hi nhtrader.

There's a limit on how much memory the list of arguments can take. It is a limit set by the OS, and it is about 2Mb. You can change it, but I advice against it since this problem can be solved another way (read [here]("https://hugepang.wordpress.com/2011/06/08/solution-bash-usrlocalbinrsync-argument-list-too-long/") for the details).

The limit on how much size the list of arguments take, does not limit the amount of files rsync can handle. That is why when you backed up your 500,000 files you didn't have a problem. However, notice that you probably passed 2 arguments: source and destination.

Since you already have a file with the filenames you want to copy, the simplest solution would be to split that list in more manageable size:
```
split -l 5000 rsyncFileList.txt  short_
```
And then rsync for every short list:
```
for file in short_*
do
    rsync -aWvR --files-from="$file" /  /media/user/BkUpFromextHDD/BU-user/

done
```
Another alternative is divide the output of find is shorter chunks:
```
find /home/user/Data -type f -mtime 40 -print0 |  xargs -0 -n5000 rsync -aWvR --from0 --files-from=- /  /media/user/BkUpFromextHDD/BU-user/
```
Hope that helps. Let us know how it goes.
Regards.

---

