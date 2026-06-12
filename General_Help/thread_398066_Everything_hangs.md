---
title: "Everything hangs"
date: 2007-03-31
forum: General Help
---

### Post by wonder1 on 2007-03-31
I encountered a strange problem today. When I opened my home folder everything hangs. I had to do a hard switch off as nothing was working.

Then I logged in again and the first thing I started was system monitor which was normal and everything seemed normal.

I started Rhythembox and it was playing music. Then I started Firefox that also  worked normally and I could access the net.

**The problem**
The moment I opened the Home folder innautilus everything hangs . On the system monitor I noticed cpu1 100%. A little later no button was working and I had to do a hard swith-off again.

Then I logged again second time and this time I opened one of my partitions in nautilus and it was waorking normally.

**Its only when I open my home folder that everything hangs**.

I did not install anything today but I had downloaded some files and kept them in the home folder . Could that be problem ? 

System: Ubuntu 6.10 with all updates.

---

### Post by useResa on 2007-03-31
Could you try opening your home folder by using the terminal and post the outcome.
You can do this by starting a terminal (Applications -->: Accessories --> Terminal) and issue the following command```
nautilus
```

---

### Post by wonder1 on 2007-04-01
Thanks useResa

I tried opening the home folder from the terminal as you have suggested 
The Result:    Exactly the same thing happens: cpu1 goes to 100% it alternates between cpu1 and cpu2 , with one of them at 100%. (cpu is P4 with hyperthreading) . Simultaneously,  User memory starts increasing and by the time it reaches 80% everything hangs and no button works . I have to do a hard switch - off.

I created another user (without administrative privileges) and everything  is working here including the home folder.

So the problem is limited to one user and that too only opening the home folder.
I am not able to understand what causes Nautilus to crash on opening the home folder , but the problem is more serious as after a short while nothing else works.


( I have been using Ubuntu since June last  year 2006, and this is the first time I am encountering a problem like this.)

---

### Post by useResa on 2007-04-01
> **wonder1 said:**
> I tried opening the home folder from the terminal as you have suggested Does it also give additional information when you open it using the terminal? I learned that when opening a program using the icon errors that are displayed when opening the program through the terminal are not shown.

Maybe I should have been clearer in this suggestion.
So basically my question was, could you open it using the terminal and post back what you see in the terminal or does it just give you the prompt followed by the word nautilus?

> **wonder1 said:**
>  I have been using Ubuntu since June last  year 2006
No worries, I have been using Ubuntu also only since July last year.
We all have our learning to do and we all run into problems (sometimes very unpredictable ones). But working together -- as I believe we do in this forum -- we'll get most of them sorted out. One way or the other.

EDIT: Just had a brainwave ... don't know yet if it will be helpful one though. ;)
You are aware that your CPU goes all the way to 100%. My guess would be that you determine this from the System Monitor.
If you open the System Monitor and click on the Processes tab. You can sort the processes running by decending percentage of CPU they are using by clicking on the CPU column header.
Could you do so after you have tried to open the home folder and when your system starts hanging.
Maybe we can get insight in which process is eating up your CPU and thus maybe bring us closer to the solution.

---

### Post by wonder1 on 2007-04-19
Well i could locate the problem but  still I do not understand why it happened.

I had downloaded a split file-the complete file is of   6 parts - each of 100Mb-I had downloaded 4 parts --these were rar files with password to open.These (the 4 parts) I had put in a folder in the home folder.I had not downloaded the remaining two parts.

I took these four parts of 100Mb each to a windows machine and used winrar to get the files .It gave the files but also gave a warning that some part were missing(I had not downloaded the remaining 2 parts).

I created another user and moved these files to another folder out of the user home folder and everything was back to normal . Even for the user for which system was hanging.

Then I went to this folder which i had named "test" and right clicked to see the properties .Here under contents it indicated **"some contents unreadable"** .And this folder was causing trouble when it was in the home folder of the user. But when I moved it out of the home folder of the user ,  although still within the Home folder , ie, test folder under /home  -- then everything returned to normal.

**The problem**
As I understand when i kept 4 parts of a split rar file with password to open (complete file of 6 parts of 100Mb each) then cpu1 or cpu2 goes to 100% and the user memory starts increasing and when user memory  reaches 80% the system hangs.

In my view the system tries to look what file it is and what size and due to some problem , may be encryption- rar, it is not able to do so and then it goes on trying , probably in some loop and so system hangs.

This was on ubuntu 6.10

(Extremely sorry I could not reply early)

---

