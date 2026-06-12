---
title: "[SOLVED] What is what here?"
date: 2008-01-26
forum: General Help
---

### Post by Bruce M. on 2008-01-26
I am going crazy here.

I've had to reinstall, and today I'm:

bruloo@bruloo

before the install I was:

bruloo@The-Team

Name1@Name2

So what is: Name1 and Name2[Saved]       [  62%]   -rw-r--r--   bruloo     bruloo  3152    Wed Jan 23 20:20:45 2008        .conkyscripts/conky_top_left
bruloo@bruloo:~$ 

I remember during install (Alt CD) that I was asked for:

 1. Host Name
 2. Full User name
 3, Name (suggested First name here)

Where do I put what to get: bruloo@The-Team back again, and can I do it without a re-install?

Reason I ask is I'm trying to recover my /home folder with DAR and the files have Permissions for bruloo (The Team)

If I have to do another re-install (3rd one today) I want to put the right stuff in the right place.

```
# /etc/fstab: static file system information.[Saved]       [  62%]   -rw-r--r--   bruloo     bruloo  3152    Wed Jan 23 20:20:45 2008        .conkyscripts/conky_top_left
bruloo@bruloo:~$ 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=ddcf8104-10c0-4e32-afc9-e4da80b05fb6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=2b41b551-6f83-4b9f-aff3-cf1aff9e9dc7 /home           ext3    defaults        0       2
# /dev/sda1
UUID=2CE8219FE8216872 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=28677b39-1f49-4d6c-a3b9-5b4002f6f66e /media/sdb1     ext3    defaults        0       2
# /dev/sda6
UUID=6d528ba5-ca92-470e-a05e-8e2ceada79c3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

How do I extract my old /home files?
```
sudo dar -x /media/sdb1/backup/24Jan08/bruloo-master-archive -R /home -wa
```
... puts the /home folder in File System

but my /home exists here:

/dev/sda7/home

Would I need:
```
sudo dar -x /media/sdb1/backup/24Jan08/bruloo-master-archive -R /dev/sda7/home -wa -v
```

added the -v because I want to SEE what its doing this time.

Thanks
Bruce

**EDIT:** Maybe I don't need to change bruloo@bruloo

With DAR -l:
```
[Saved]       [  62%]   -rw-r--r--   bruloo     bruloo  3152    Wed Jan 23 20:20:45 2008        .conkyscripts/conky_top_left
bruloo@bruloo:~$
```
it shows bruloo  bruloo here.

---

### Post by merlinDwizzard on 2008-01-26
have you tried to navigate to the file and chmod to change permissions? look for that on the forum

---

### Post by seventhc on 2008-01-26
I thought the part after the '@' sign is the machine name. Like mine is 
j0hn@cipher:~$ 
i named my machine 'cipher' during install.
It's on the same page where you enter your name and password, it is usually already filled in so you delete what they have and enter your own.
You can still change the name though, I have to find where that is.
or am I missing something?
for host name you can go to System>administration>network look under the 'general tab'

---

### Post by Bruce M. on 2008-01-26
> **seventhc said:**
> I thought the part after the '@' sign is the machine name. Like mine is 
j0hn@cipher:~$ 
i named my machine 'cipher' during install.
It's on the same page where you enter your name and password, it is usually already filled in so you delete what they have and enter your own.
You can still change the name though, I have to find where that is.
or am I missing something?
for host name you can go to System>administration>network look under the 'general tab'

Well, that answered two things. And I can search for "Change machine name"

Now for the /home issue.  :)

Thanks j0hn@cipher seventhc
Bruce

---

### Post by Bruce M. on 2008-01-26
> **merlinDwizzard said:**
> have you tried to navigate to the file and chmod to change permissions? look for that on the forum

I can get at the file, and I think it will work just fine, if I can find out just what [path] to give to DAR to put them all in my /home folder.

However it seems no one has an answer for that so, I'm going to try that last command with the:

sda7/home ending, if that doesn't work, I'll try
sda7/home/bruloo

I'll let everyone know how things go.
Bruce

---

### Post by seventhc on 2008-01-26
The machine name can be changed where i said. :)
System>Administration>Network 
then you should be asked for your password, after that you will see 'Network Settings" click on the 'General tab' and change the 'Host name'
that will be the name that appears after the @ sign. :)
As for the home folder, I usually just paste everything into the new home, so your doing it different than me, can't offer much help there. sorry
But the name change should work. :)

---

### Post by Bruce M. on 2008-01-26
> **seventhc said:**
> The machine name can be changed where i said. :)
System>Administration>Network 
then you should be asked for your password, after that you will see 'Network Settings" click on the 'General tab' and change the 'Host name'
that will be the name that appears after the @ sign. :)
As for the home folder, I usually just paste everything into the new home, so your doing it different than me, can't offer much help there. sorry
But the name change should work. :)

Yup, it worked like a charm:

Terminal:
```
bruloo@The-Team:~$
```
> from: ID4
Hello boys!  I'm baaaaaaaaack!

Paste it!  You're kidding right?
You do **/home** backups with cut and paste?

I'm talking 63 folders (mostly hidden) and thousands of files in a compressed archive here.  :lolflag:

---

### Post by seventhc on 2008-01-26
> **Bruce M. said:**
> Yup, it worked like a charm:

Terminal:
```
bruloo@The-Team:~$
```Paste it!  You're kidding right?
You do **/home** backups with cut and paste?

I'm talking 63 folders (mostly hidden) and thousands of files in a compressed archive here.  :lolflag:

I just make an archive, burn it to dvd, but I don't think its like what you have, mostly I want configuration files, a few hiddens, music and pics. etc But I do paste the ones I want to my home :) hasn't failed me yet. :)

---

### Post by erfahren on 2008-01-26
> **seventhc said:**
> I just make an archive, burn it to dvd, but I don't think its like what you have, mostly I want configuration files, a few hiddens, music and pics. etc But I do paste the ones I want to my home :) hasn't failed me yet. :)
I do pretty much the same - when I create the backup archive I select just the hidden folders I want and copy them into a folder I name "hidden_back" and compress that with my regular directories I have in my home. (Most of the hidden directories for programs are created when the program is first launched anyway - they're not critical).

Then I just decompress the archive back into my home if needed.

this thread shows how to backup your entire filesystem into an archive: [http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

---

### Post by Bruce M. on 2008-01-27
**[CENTER]Success!  I have my old /home back[/CENTER]**

It's late, will check everything out again tomorrow, and will reply.

Thanks for the replies.
Bruce

---

### Post by seventhc on 2008-01-27
> **erfahren said:**
> I do pretty much the same - when I create the backup archive I select just the hidden folders I want and copy them into a folder I name "hidden_back" and compress that with my regular directories I have in my home. (Most of the hidden directories for programs are created when the program is first launched anyway - they're not critical).

Then I just decompress the archive back into my home if needed.

this thread shows how to backup your entire filesystem into an archive: [http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)
I actually archive my entire home(minus anything to big such as movies) but I don't really put everything back, and honestly I always want to reorginize how I have everything so I like a nice clean home from a fresh install :D) For themost part, everything I actually need fits onto my usb flash drive. I just archive the entire folder in case there is something I forgot about, but I might try it following the link in your post next time. :) Thanks for the link. :)

---

