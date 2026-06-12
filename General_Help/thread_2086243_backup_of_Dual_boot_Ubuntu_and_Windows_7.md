---
title: "backup of Dual boot Ubuntu and Windows 7"
date: 2012-11-20
forum: General Help
---

### Post by amin_pwa on 2012-11-20
Hi guys and girls,
i am having ubuntu 12.04 and windows installed (Dual boot Ubuntu and Windows 7 )
for many times i have 3 partition on my pc .
i use many apps for backup and restore of my win partition for example ghost and acronis , always i make backup and when my pc fall in problem i try restore that !
But that app delete  all my partition and i lost all my data and all my partition lost and only on partition show !
that was that restored partition ! :mad:
for know when i use ubuntu i see this is very very good and have no bug ! :guitar:
i try make backup of my partition c and d ( i have ssd 128 )
c is win 7 120gig
d is ubuntu 6 gig
i want to save them in my external hard 1T western .
my question is this :
if i make back up in ubuntu from C and D in my external driver when my win7 or ubuntu have problem , can i restore them ?
i want this app format that partition before restore and not want lost my partition or lost my dual boot Ubuntu and Windows 7 !
:confused:

---

### Post by Mark Phelps on 2012-11-20
Haven't used Ghost or Acronis in years -- so I can't advise you on those.  I use Macrium Reflect (MR) for Window backups and Clonezilla for Linux backups -- but I don't think MR handles Linux filesystems.

I have generally found that Windows utilities do a better job of backing up and restoring Windows, and Linux utilities do a better job of backing up and restoring Linux.

So, by choice, I do NOT use a single backup/restore solution for both Windows and Linux -- and in doing it this way, I have NEVER run into a situation where anything got destroyed.

---

### Post by amin_pwa on 2012-11-20
thanks for answer 
i want make back up from my to partition , in past i try make back up from 1 partition from 3 partition and always when restore that back up all partition lost and only 1 of them come back !
i think now i have ubuntu and win 7 so must make back up from both in same time !

there is 100Mb partition in my drive , what is this ?
must make back up from this ?

and this is important for me to format partition before restore files !

---

### Post by Mark Phelps on 2012-11-20
You can't backup partitions to partitions.  Acronis, Ghost, and MR all work basically the same ... they create compressed files that CONTAIN the partition image (or part of the image, if you've contrained the file sizes).  You CAN store multiple image files in the same partition (as long as the filenames are different) -- which is what I do.

As I said already, I don't use Ghost or Acronis ... so I obviously can't comment on why they do not appear to be working properly.  I use MR and have not had the problems you mention.

As I already said, in my experience, you need to use TWO different imaging programs to have good backups -- one for Windows partitions, another for Linux partitions.

You obviously can NOT run both programs at the same time, so you will have to do one backup at a time.  You can do the Windows backup from inside Windows while it is running; but you have to boot to a CD to do the Clonezilla Linux backup because it can't backup partitions that are currently in use.

---

### Post by amin_pwa on 2012-11-20
thanks ,nice answer :)

---

