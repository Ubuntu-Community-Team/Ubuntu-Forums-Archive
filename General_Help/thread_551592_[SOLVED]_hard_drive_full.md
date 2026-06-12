---
title: "[SOLVED] hard drive full"
date: 2007-09-15
forum: General Help
---

### Post by nobloodshed on 2007-09-15
im running 7.04, ive had it on this computer for about a year now, and the other day it wouldnt login, giving me this GDM can not read the authroazation file, hard drive full.  so i took the live CD, and saved my files, and reinstalled ubuntu, completly reformating my 40 gigabyte hard drive.  
i then reinstalled ubuntu, with a 18 gig partition, and another partition for windows
that was yesterday
this morning i turned it on, went on a little installing spree, downloading approxamatly 1 gigabyte of programs and other misc. librarys and stuff.  
then i get popup that says "disk full" and i look at the home folder, and it says ive used the entire partition, which is completly and utterly impossible, because i havent downloaded anything more than that, 
so i emptied all the trashes, and stuff and couldnt find anything else to delete, so i came here.  
this is the result of me running df -h on the terminal
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G   19G     0 100% /
varrun                252M  108K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M  108K  252M   1% /proc/bus/usb
udev                  252M  108K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.20-16-generic/volatile
/dev/sda6              18G   16K   18G   1% /windows

i then looked in the forums, and started trying things, i tried to fsck, but it gave me some thing about damaging my files, so nix to that
then i tried sudo apt-get clean, and that didnt do anything at all
so please help, ive tried everything i know how to do...thank you

---

### Post by forestpixie on 2007-09-15
well it definitely says it's full - have you checked you haven't got any hidden files taking up a load of room, you say you've emptied trash - what about roots trash - do a gksudo nautilus then you can check that.

have you checked that apt-get clean actually did what it said it did?

Other than checking through nautilus to look I can't think of much else, but I'm sure there are

---

### Post by vanadium on 2007-09-15
You should start Ubuntu from the live CD and then try to free some space on the disk as suggested before. First, there are the .Trash directories. Anything in the /tmp and /var/tmp dirs should be safe to delete.  If you have user data that is already safeguarded in a backup, then you can delete that first, otherwise backup and then remove it. You might want to perform a diskcheck then, after which your system should be capable of starting up again. then it is time to reorganise your data.

---

### Post by Johnny3 on 2007-09-15
Where are the /tmp and /var/tmp Files?
Thanks Johnny3
Gainesville Fl

---

### Post by nobloodshed on 2007-09-15
i tried to delete the /var and the /tmp files (i mean the files inside them) and it said i dont have the persmissions, and it wouldnt let me delete them, cuz i wasnt root, which i am.  
i just tried that gksudo nautilus thing, and it opend the root folder, and nothing else.  any other suggestions?

---

### Post by The_PhAnT0m on 2007-09-15
Did you try to delete the files using the terminal?

---

### Post by forestpixie on 2007-09-15
> just tried that gksudo nautilus thing

I believe when you're in the live cd - if you right click the partitions you can mount them - they'll be in root/media I think - once you've got them mounted, you should be able to delete files.

---

### Post by nobloodshed on 2007-09-16
i think i solved it.  my hard drive took a dump/ died/something. so im getting a new computer.  thanks for your help, but it wasnt the linux, it was the shitbox laptop. thanks dudes

---

### Post by forestpixie on 2007-09-16
bummer when that happens - can you mark thread solved with thread tools at the top

glad I could help though - even if it didn't :)

---

### Post by nobloodshed on 2007-09-16
i think i did...

---

### Post by tvrg on 2007-09-16
> **nobloodshed said:**
> i think i solved it.  my hard drive took a dump/ died/something. so im getting a new computer.  thanks for your help, but it wasnt the linux, it was the shitbox laptop. thanks dudes

no need to get a new computer, get a new disk if that's what broke

---

