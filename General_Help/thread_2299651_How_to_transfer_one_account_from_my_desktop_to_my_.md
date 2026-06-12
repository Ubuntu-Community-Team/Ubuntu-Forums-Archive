---
title: "How to transfer one account from my desktop to my laptop?"
date: 2015-10-20
forum: General Help
---

### Post by Ifaistos on 2015-10-20
Hello :-)

Right now I have two ubuntu installations.
[LIST]
[*]Desktop, acc01
[*]Laptop, acc02
[/LIST]
I would like to get hints, do's and dont's on how to transfer my "acc01" on my laptop.
Is there an "easy" way?

I also have a partition on my laptop (Let's call it "Data") which I want it to be accessible by both accounts.
I not only want both accounts to be able to access that partition but I also want whatever is written on the disk by acc01 to be readily accessible by acc02, and vice versa.  Is that possible?

I don't know how to do it, but I guess if I put both acc01, and acc02 into the same group, it will have that effect?

I have setup a VPN connection for acc02, which I don't want acc01 to have access to.  Is that possible?

One last thing.
How can I transfer Thunderbird with all the settings, email, filters, add-ons from the old acc01 into the new acc01?

Thank you all in advance :-)

---

### Post by slickymaster on 2015-10-20
Have a read at [How to migrate user settings and data to new machine]("http://askubuntu.com/questions/25633/how-to-migrate-user-settings-and-data-to-new-machine")

---

### Post by The Cog on 2015-10-20
Check the id of the two accounts. They are probably both 1000, in which case you can just copy the entire contents of /home/acc01 and use it to replcace the contents of /home/add02. You can do this my making a tar file on an external drive (like a zip file but also saves *nix permissions attributes). You really ought to know how to do this because it's a good way of taking and restoring a backup. 
Assuming your backup drive mounts on /media/acc01/backup, use this command to make the tar file:
```
cd /home
sudo tar cvf /media/add01/backup/myhome.tar acc01
```
and to restore - this will create /home/acc01 on the laptop. You may need to remove the old acc02 home directory and rename acc01 to acc02 afterwards:
```
cd /home
sudo tar xvf /media/add01/backup/myhome.tar
```

Alternatively, you could use **rsync** to replicate one home directory to the other over the network. 
Something like this on the main PC, to push to the laptop. The --delete says to remove files from acc02 that don't exist on the acc01 source. Correct the ip address of course:
rsync -avz -e ssh --delete /home/acc01/ 1.2.3.4:/home/acc02/

---

### Post by Ifaistos on 2015-10-20
Hello and thank you for your answer.
I read the guide.
It has many approaches of which some are obsolete as far as I can tell.

How about my other questions?

So a basic strategy would be :

1. install samba on both desktop and laptop to acquire network connectivity.
2. Share the home folder on my desktop.
3. Create a new user with the same name as the desktop on my laptop.
4. Copy all (and hidden) files from the desktop home to my home laptop.

Anyone else has something to comment?

Hello "The Cog" and thanks for your answer.

I am under the impression (and please correct me if I am wrong) that this guide is if I wanted to overwrite my acc02 (laptop) with the acc01(desktop).

However what I want to have on my laptop is two accounts.  acc01 and acc02 in parallel.
But acc01 live now on my desktop.

Hello "The Cog" and thank you for your answer!

As far as I can tell this guide (and correct me if I am wrong) is for overwritting acc02 with acc01.
What I want as an end result is having on my laptop two accounts (acc01 & acc02) in parallel.

I believe that rsync is probably the best command.
Can you please tell me again how to do this over the network?

Should I install samba on both computers?

Would the correct command be :
rsync -avz -e ssh /home/acc01/ 1.2.3.4:/home/acc01/

Please let me know... and what do I need to do in order to have both computers on the network?

I just installed Grsync on my desktop.
However I cannot find a directory outside of my desktop although my laptop is on the same network.

I guess I haven't installed network connectivity on my computers.
Do I need samba for that?

---

