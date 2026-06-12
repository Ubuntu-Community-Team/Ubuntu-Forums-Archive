---
title: "Complete n00b - Please tell me if it worth in this case"
date: 2007-01-28
forum: General Help
---

### Post by andy_blah on 2007-01-28
Hello,
I wanted to switch from Windows XP to UBUNTU. I have a harddisk splitted into 2 partitions: C:\ and D:\ . Currently Windows is on the C:\ partition and there I want to put UBUNTU after I get rid of Windows. I would like some help with what I should do and pro and cons. Also I donnot want to format D:\ because I have some important data there. If somebody could help me through MSN Messenger would be 10x better. My handle is [email]andyblah@hotmail.com[/email].

Thanks,
>-Andy-<

EDIT: Sorry I should post this into the noob part of the forum, I ask a moderator to move it, thank-you.

---

### Post by teaker1s on 2007-01-28
or use gparted live cd to resize a partition and leave free space for ubuntu
[http://www.users.bigpond.net.au/hermanzone/]("http://www.users.bigpond.net.au/hermanzone/")

---

### Post by andy_blah on 2007-01-28
Thanks for that but you didn`t quite understanded I am a _n00b_ to UBUNTU and somebody told me that this install you suggested me is even more complicated even for a user that has medium knowledge in UBUNTU. Please somebody give me a alternative or contact me on MSN Messenger instead.

Thanks,
>-Andy-<

---

### Post by teaker1s on 2007-01-28
issue is you can't install ubuntu on partition with data on it, so you either move the data or graphically resize the partition with a live boot point and click partitioner such as gparted

---

### Post by pepik on 2007-01-28
n00b to n00b advice:

1. Don't expect personal one to one help, with handholding real time walkthroughs. If you really need to chat, go to #ubuntu on IRC, you might get help there. But don't count on it.

2. Why complicate things? Back up your essential data from D: and then you can start with a clean install.

3. Don't go with just Ubuntu. It has a learning curve, and there are some things you just can't do in Linux. Your best bet is to dual boot XP and Ubuntu, have the best of both worlds. So in your case backup D:, reinstall XP, and then install Ubuntu. May take some time, but less chance of going wrong.

---

### Post by andy_blah on 2007-01-28
Thanks you both for your help, I will use the method you suggested, pepik

---

### Post by steve.horsley on 2007-01-28
If you want to blow windows away, you probably don't want D: to be a windows filesystem either.  So the best thing really is to blow away the whole disk and re-use the whole thing for Ubuntu. But that of course assumes that you can safely back up all your precious data. Actually, if the data is precious then you shoudl have  a backup anyway - I already know the grief the failure of a hard disk with no backup can cause. You should doubly have a backup if you are messing around installing a new operating system, even if you don't actually intend to wipe the whole drive.

Lecture over, I suggest you take a good backup and then blow away the whole drive.

Good luck.

---

### Post by SigmaX on 2007-01-28
I would disagree -- it shouldn't be very tough.

While going through the Ubuntu installation, just be careful to select manual partitioning.  Then you can select the first partition (That Windows called C:\), delete it, and replace it with one partition for Linux (Mounted at "/") and one for swap (Linux uses a separate partition for its paging file/virtual memory, "swap").  As long as you don't click the check-box to reformat the second partition, you should be fine (But I'd still backup just in case).

Linux can use Windows partitions, so if you don't want to, you can leave your data on D:\.

SigmaX

---

### Post by andy_blah on 2007-01-28
I wouldn`t want to get rid of windows even if it is soo crappy because I have a project in witch I must do the ports for the source code on various OSes.
Thanks for all of you for your contribution at helping me :mrgreen:

---

### Post by steve.horsley on 2007-01-28
Sorry, I got th eimpression from your first post that you wanted to get rid of Windows. If not, what do you want to do? 

Maybe there's enough space to re-size C: and put Ubuntu in the created space. I thnk the installer can do that. WHat's the question though?

---

### Post by lprofil on 2007-03-28
Hi andy,

> **andy_blah said:**
> I wouldn`t want to get rid of windows...

have you tried kvm? It works great in Feisty if you have a new processor which supports Virtualisation.

/lprofil

---

### Post by kevmartin on 2007-04-08
I wouldn't recommend anyone who is a real newbie to move completely from Windows to Ubuntu in one go.  You may get some surprises on the things you can't do in Ubuntu and regret your choice when its too late.  The exception to this would be if you are sure there is no software you run that you won't be able to find an equivalent in Ubuntu for, and you don't have any hardware that won't run under Ubuntu.  On short, research this well before ditching Windows completely.  Once you are sure you are ready - you can always ditch windows later.

Check out this thread for some others experiences on what still ties them to windows some of the time: [http://ubuntuforums.org/showthread.php?t=352271]("http://ubuntuforums.org/showthread.php?t=352271")

---

