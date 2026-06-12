---
title: "TOTAL noob terminal stuffs"
date: 2008-02-16
forum: General Help
---

### Post by Joe of loath on 2008-02-16
well, hi all, i haven't posted here since my last antique PC gave up the ghost...

i'm making a media centre out of an old P2 machine. windows just didn't cut it (as usual) and i read up about ubuntu on t'internet... i had an old 'live' CD (6.06 LTS) from when i was experimenting a while back.

to cut to the chase, I need to know how to get my WPA wireless to work.

NOW before you move this thread to the wireless and networking forum, my problems aren't with the hardware.

I'm following the guide here:[http://ubuntuforums.org/showthread.php?t=179643](http://ubuntuforums.org/showthread.php?t=179643), and i installed 'networkmanager', but theres no icon. i'm up to stage 3, but i'm unsure what they mean by 'comment out'. i tried to edit the file, but i couldn't as i don't have root priveliges. i tried to log in as root like i used to on red hat all those yonks ago, but alas, i could not. then i tried the sudo command in terminal (i keep wanting to call it the command line. eugh), but i'm not sure what i have to do to open and 'comment out' the file.

also, i need to know how to move the 'wpasupplicant' file i created into the desired location (/etc/default) through the terminal window.

so, thanks alot for any help you may lend me, i know these are probably some quite popular questions, so i know how annoying i'm being :)

thanks,
Joe

---

### Post by Joe of loath on 2008-02-16
oh also, is it possible to access the windows NTFS partition I have with all my media on? or do i have to stick it in a windows box and convert to FAT32?

thanks again,
Joe

---

### Post by LO Matt on 2008-02-17
Try [Dapper  Wiki on NTFS]("http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only")

---

### Post by Zwack on 2008-02-17
Rather than trying to teach you to use vi I'd suggest you try sudo gedit <filename>

It's not command line but it should work...

Secondly to move files 

sudo cp <source> <destination>

That should be enough to solve your problems...

You could even try

cp <file to replace> <temporary file>
edit the temporary file
sudo cp <temporary> <final destination>

I hope that this helps,

Z.

---

### Post by Joe of loath on 2008-02-17
thanks, that looks like it should do the trick :)

---

### Post by pandayanyan on 2008-02-17
i hope this is the right place for this but it is the closest thing I could find to my problem.

ok I am having a simular problem and am way lost. 

i will start by saying that i am new to linux by a few days... so bear with me please.

I am trying to unzip a single file to a directory. I am logged in as a user  but am using su  then my password and typing sudo before all commands. (found out if i dont do that it wont do anything for me.)

so i am typing in:  

sudo unzip (myfile).zip /usr/local/yadda/yadda/ya

no matter what i try it comes back as this:

caution: filename not matched: usr/local/yadda/yadda/ya

what do i do?
I read your posts in this thread and tried the 
ls -1 thingy but that just turned the file name red in the terminal and did nothing else
how do i do this?
:confused:
please once again forgve me for my newbness.:(

---

