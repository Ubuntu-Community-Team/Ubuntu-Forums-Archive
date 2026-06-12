---
title: "could not delete file takesnapshot.log.bz2"
date: 2018-09-11
forum: General Help
---

### Post by monere on 2018-09-11
Hi,

I have installed Xubuntu 18.04 yesterday and at some point I have installed the "Back in Time" backup and restore software in order to... well, to create backups of my system :)

Well, I didn't like the program and I removed it, but during the time I had tested it I have also manually created a snapshot so I could test the program, and even though I have received error upon error that the snapshot can not be created I think it has actually been created because I see a file in my backups folder that shouldn't normally be there, and which I can't delete because when I click on "delete" it returns this error message: 


[I][B]could not delete file takesnapshot.log.bz2

Error removing file /home/monere/snap/backups/backintime/GA-H97M-D3H/monere/1/20180911-120001-356/takesnapshot.log.bz2: Permission denied.
Do you want to skip it?
[/B][/I]
And the only options I have are Retry / Yes to all / Yes / Cancel.... and needless to say that none of them removes the file.

I would normally not be bothered by it, but that file is 80 freaking GB large, and I have just installed this distro yesterday, so what on Earth has that software backed up worth of 80 GB on an empty OS?? I don't know... but anyway... I want to remove that file, but I don't know how because I'm not very good at Linux (I have just started using it a month ago after 30 years of using Windows)

So, does anyone know how to remove that file??

Thanks in advance!

John

---

### Post by deadflowr on 2018-09-11
Chances are it was written by root, so in those cases you need to sudo rm the file from a terminal, 
like
```
sudo rm /home/monere/snap/backups/backintime/GA-H97M-D3H/monere/1/20180911-120001-356/takesnapshot.log.bz2
```
since only root would be able to remove it.
Double check the file name before running the command.
So you don't inadvertently misspell it and remove something else.

---

### Post by monere on 2018-09-11
Hi deadflowr,

your command might have helped, but... I think I've made a mistake when I explained. Well, I definitely made a mistake, because I said I'm trying to remove a file, but in reality I was right clicking on the "backups" folder (found in /home/monere/snap), and that folder contains the entire path of folders that I've posted in my previous message, with the last folder in this tree containing a bunch of files AND another folder called "backup" which has a lock over it, but which - when accessed - shows all of the folders in my "root" partition, each of these folder also having a lock over them.

So, realistically, I would need to remove the entire "backup" folder, plus the 4 single files (config, failed, fileinfo.bz2, info)... all of these found at the end of this path: **/home/monere/snap/backups/backintime/GA-H97M-D3H/monere/1/20180911-120001-356/**

Sorry for the misleading information dude. I'm really sorry but I'm trying my best to find my way around linux, and, while it's not really difficult to understand per se, it does take some getting used to it.

Can you please tell me again what to do in this case? I have actually typed the command you have given me into the terminal, then clicked ENTER, then I was required for the password (which I typed in and clicked ENTER again), after which the terminal simply moved me to the next row, without giving me any warning / error / success message of any kind. Then I typed the command again, and it said that such file doesn't exist, which probably means that the terminal actually removed that file from the first try even if it didn't return a success message.

So anyway, what can I do in this case? Like I've said, if that file / folder was only a few MB or even 1 GB I wouldn't have minded. But 80 GB is too large of a file / folder for my 266 GB /home partition to let it go :)

Cheers!

---

### Post by QIII on 2018-09-11
Be careful about your directories.  / is the root directory ("folder" is Windows parlance) and it is critical.  There are a lot of things contained there -- like your whole machine.  You need to also understand the concepts "directory" and "file" -- and the strangeness surrounding the "everything is a file to Linux" situation.

I highly suggest that you stop mucking around for a bit.

Before you proceed, you might want to read [this]("https://www.linux.com/blog/learn/intro-to-linux/2018/4/linux-filesystem-explained").  It will probably be as clear as mud, but you can ask questions here.

---

### Post by monere on 2018-09-11
> **QIII said:**
> Be careful about your directories.  / is the root directory ("folder" is Windows parlance) and it is critical.  There are a lot of things contained there -- like your whole machine.  You need to also understand the concepts "directory" and "file" -- and the strangeness surrounding the "everything is a file to Linux" situation.

I highly suggest that you stop mucking around for a bit.

Before you proceed, you might want to read [this]("https://www.linux.com/blog/learn/intro-to-linux/2018/4/linux-filesystem-explained").  It will probably be as clear as mud, but you can ask questions here.

I know that the root partition is the most important one of a linux distro, but I'm trying to delete a backup folder, not the root partition. The fact that those folders appear in the backup is due to the fact that I've told the "Back in Time" app to screenshot the entire root partition.

Also, yeah, I will definitely have a read on that link. And in the meantime, if you know how I can remove that entire "backups" folder let me know cause it really irks me... well, the size of it anyway :)

---

### Post by QIII on 2018-09-11
Your statement > if that file / folder was only a few MB or even 1 GB leads me to believe that you do not fully understand how the Linux file system works.

Yes.  We can tell you how to delete a directory (again, "folder" is Windows parlance) and its contained directories and files, but please read the link first.  Like most Linux documentation, it is probably more likely to add to your confusion, but we are always here to answer questions.

---

### Post by monere on 2018-09-11
> **QIII said:**
> Your statement  leads me to believe that you do not fully understand how the Linux file system works.

Yes.  We can tell you how to delete a directory (again, "folder" is Windows parlance) and its contained directories and files, but please read the link first.  Like most Linux documentation, it is probably more likely to add to your confusion, but we are always here to answer questions.

Maaan! I don't know how the filesystem works indeed, I told you that I'm new to linux. But I do know that the root partition is critical, why won't you believe me? :)

---

### Post by QIII on 2018-09-11
Your notion of the expected size of /.  I typically let it have ~30GB because of the number of packages I often install.

I'm not asking you to read that just to put you off or to be elitist.  I would like to be sure that you don't over-generalize any commands using "rm" and make a huge mess later on if you attempt to do something on your own.

A little rm is a dangerous thing.  One typo or misunderstanding of the Linux file system can make rm the key to a significant emotional event.

---

### Post by monere on 2018-09-11
> **QIII said:**
> Your notion of the expected size of /.

I'm not asking you to read that just to put you off or to be elitist.  I would like to be sure that you don't over-generalize any commands using "rm" and make a huge mess later on if you attempt to do something on your own.

A little rm is a dangerous thing.  One typo or misunderstanding of the Linux file system can make rm the key to a significant emotional event.

Hehe, don't worry I'm not trying anything on my own. I'm not capable of that yet. I have only learned to use the "sudo apt install ..." command cause I've used it quite a few times in the last month (I've had Mint installed for a few weeks prior to switching to Xubuntu) and that command has somehow gotten imprinted into my brains :D

But otherwise I'm really not attempting anything on my own, don't worry! I'm waiting for your instructions like an obedient dog (no sarcasm intended) :)

Also, I'm going offline now. If you don't want to answer my question until I read that page, no problem. But it will happen tomorrow as right now it's midnight here and I'm going to get some sleep. I can barley see the keys amyway :)

Cheers!

---

