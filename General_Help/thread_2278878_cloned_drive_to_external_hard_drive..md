---
title: "cloned drive to external hard drive."
date: 2015-05-19
forum: General Help
---

### Post by amr-elfiky on 2015-05-19
[COLOR=#111111][FONT=Ubuntu]i was trying to restore my formatted D partition using [/FONT][/COLOR]**testdisk**[COLOR=#111111][FONT=Ubuntu] .i was following the first answer in this question.

[/FONT][/COLOR]http://askubuntu.com/questions/296109/need-to-recover-data-from-a-data-hard-disk-that-i-used-testdisk-on-in-my-attempt

[COLOR=#111111][FONT=Ubuntu]one of the steps i was supposed to **clone** my D drive to an external hard cloned itto and external hard overnight .when it finished i noticed that the 1 TB external hard was all wiped out and replaced by my formatted D drive .[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]i tried to restore the partition of the external hard using **testdisk** ,**gparted** and **gpart** but they said they couldn't find it .[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]can anyone help me ,please ?[/FONT][/COLOR]

---

### Post by leunam12 on 2015-05-19
Didn't you get a warning telling you that you were going to lose all your data in your 1TB? What program did you use to clone? Clonezilla requires three confirmations before it starts writing to disk

---

### Post by sudodus on 2015-05-19
I'm afraid that you had tough luck. Cloning a drive means that you overwrite it (sometimes every single block, sometimes 'only' blocks that belong to files (skipping free blocks).

If the target drive is bigger than the source drive, the part of the target drive 'behind' what is overwritten might be possible to restore. So if the source drive contains 120 GB and the target drive contains 500 GB, the space 'behind' is from 120 GB to 500 GB (size 380 GB), and the file data stored there is possible to recover with for example ***PhotoRec***. If you are really lucky, there may be gaps of blocks (not overwritten), that contain valuable data also among the overwritten data.

-o-

An alternative that would keep the existing data on the external drive is to ***make a compressed image file***. That compressed image file can be expanded into another (target) drive, which will contain the directories and files of the original source drive. ***Clonezilla*** is a tool that can do that.

---

### Post by amr-elfiky on 2015-05-19
[COLOR=#DD4814][COLOR=#000000][leunam12]("http://ubuntuforums.org/member.php?u=1449887"), i didn't . i just used this command,[/COLOR][/COLOR]*sudo dd if=/dev/sdX of=/dev/sdY .*

---

### Post by amr-elfiky on 2015-05-19
[COLOR=#c61919]**sudodus,**[/COLOR] the source drive was 260 GB and the target was 1TB .i think there is still hope .i just need to get the lost partitions on the external hard back .i mean , its whole capacity now is 260 GB .there is nothing else .it's like it shrank .[COLOR=#c61919][/COLOR]

---

### Post by sudodus on 2015-05-19
dd is nick-named 'disk destroyer' :-( It does what you tell it to do without questions, and does not give you a second chance. You are neither the first nor the last victim.

-o-

But all the unallocated space behind those 260 GB is untouched by dd. It stopped writing when it had cloned the source drive, and ***PhotoRec*** can recover data without a file system (so also behind the current file system).

PhotoRec comes from [http://www.cgsecurity.org/](http://www.cgsecurity.org/) that also provides TestDisk. Please read what you can find at that web site (and maybe other helpful texts that you find via the internet), and then start using PhotoRec.

It might be a good idea to get a fresh target drive (another and empty external drive), where you can copy the files that are recovered.

---

### Post by amr-elfiky on 2015-05-19
[COLOR=#000000]disk destroyer? why do these things happen to me ?! but PhotoRec loses all the files names and restores unnecessary files .can i use other date recovery software ? even these for windows ?[/COLOR]

---

### Post by sudodus on 2015-05-19
You are right about PhotoRec. Only if the file name is stored inside the file, it can be restored by PhotoRec. But you can make separate searches for different file types and make a coarse separation that way.

I don't know any better tool. ***I hope someone will chip in and suggest some Windows tool or some other linux tool.***

You have already used TestDisk. Maybe if you do a deep search (which will take a lot of time), it might find some structure of the previous file system (NTFS?) after the overwritten part. But I don't know.

---

### Post by amr-elfiky on 2015-05-19
right now i'm "checking" the drive through gparted .the "check" option wasn't available .i guess i needed to unmount the drive .then i'll try data recovery with gparted and testdisk one more time before i lose all hope . i heard there's a great windows tool for data recovery called "Recuva ". i think it restores the files names and maybe the directory .
[https://www.piriform.com/recuva](https://www.piriform.com/recuva)

---

### Post by sudodus on 2015-05-19
Good luck :-)

And other people, who read this: ***Please chip in and suggest some Windows tool or some other linux tool.***

---

### Post by amr-elfiky on 2015-05-21
thanks a lot,[[COLOR=#C61919]sudodus[/COLOR]]("http://ubuntuforums.org/member.php?u=1499021")[COLOR=#000000]  ....should i mark this thread as solved ? i can't find an option for this here though .[/COLOR]

---

### Post by sudodus on 2015-05-21
If you feel that your problem is solved, yes, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

And I guess this is the case, so ***congratulations*** :KS

Finally, please share the solution :-)

---

### Post by amr-elfiky on 2015-05-21
[COLOR=#000000]share the solution ?[/COLOR]

---

### Post by sudodus on 2015-05-21
If your problem is ***solved***, that is, that you were able to recover important files, then ***please explain how you did it, what tool and method you used***. It might help other people in the future.

If your problem was ***not*** solved, I think you should not mark this thread as SOLVED. In that case we did our best, but failed to solve your problem. And maybe someone else will suggest another method (which would probably not happen if the thread is marked as SOLVED).

---

### Post by amr-elfiky on 2015-05-28
i just marked it unsolved as it wasn't completely solved ,for future answers . 
speaking of** data recovery software **especially for windows -sorry for that- i just used a program called **wondershare data recovery.** here is its official website .**[http://www.wondershare.com/data-recovery/](http://www.wondershare.com/data-recovery/). **it was like magic .it got me about 200GB of the original 260 GB.not bad at all . recovering the files names ,folders and directories .mostly it lost some movies other than that everything is there .

---

### Post by RobGoss on 2015-05-28
> **amr-elfiky said:**
> [COLOR=#DD4814][COLOR=#000000][leunam12]("http://ubuntuforums.org/member.php?u=1449887"), i didn't . i just used this command,[/COLOR][/COLOR]*sudo dd if=/dev/sdX of=/dev/sdY .*


If you don't mind me asking were did you get the commands you used for this process. I am very weary of the commands I find any were on the net when it comes to Linux because not knowing what they can do could be  BIG PROBLEM... It's good practice to research the commands you need for different task and the ones that you know are correct make notes for future references.

---

### Post by sudodus on 2015-05-29
> **amr-elfiky said:**
> i just marked it unsolved as it wasn't completely solved ,for future answers . 
speaking of** data recovery software **especially for windows -sorry for that- i just used a program called **wondershare data recovery.** here is its official website .**[http://www.wondershare.com/data-recovery/](http://www.wondershare.com/data-recovery/). **it was like magic .it got me about 200GB of the original 260 GB.not bad at all . recovering the files names ,folders and directories .mostly it lost some movies other than that everything is there .

Thanks for sharing your solution! It was quite good even if you did not recover everything :-)

All except some movies was not bad at all. Maybe those files were fragmented, or overwritten.

---

### Post by amr-elfiky on 2015-05-29
[[COLOR=#000000]robert159[/COLOR]]("http://ubuntuforums.org/member.php?u=1971247")[COLOR=#000000]  ....i got the command from the first answer to this question ...[/COLOR]**[http://askubuntu.com/questions/296109/need-to-recover-data-from-a-data-hard-disk-that-i-used-testdisk-on-in-my-attempt](http://askubuntu.com/questions/296109/need-to-recover-data-from-a-data-hard-disk-that-i-used-testdisk-on-in-my-attempt)**

---

### Post by RobGoss on 2015-06-01
> **amr-elfiky said:**
> [[COLOR=#000000]robert159[/COLOR]]("http://ubuntuforums.org/member.php?u=1971247")[COLOR=#000000]  ....i got the command from the first answer to this question ...[/COLOR]**[http://askubuntu.com/questions/296109/need-to-recover-data-from-a-data-hard-disk-that-i-used-testdisk-on-in-my-attempt](http://askubuntu.com/questions/296109/need-to-recover-data-from-a-data-hard-disk-that-i-used-testdisk-on-in-my-attempt)**

Thanks so much for sharing your findings ..

---

