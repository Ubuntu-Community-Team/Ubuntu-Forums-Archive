---
title: "Ubuntu and Nokia 6300"
date: 2007-06-10
forum: General Help
---

### Post by PartisanEntity on 2007-06-10
I'm looking for a new phone and I could, due to my current cell phone plan, get the Nokia 6300 for free.

So the question is does anyone here have that phone and does it sync with Evolution? (my current SonyEricsson D750i does sync and I would like this functionality in the new phone as well).

Thanks.

---

### Post by Linuxcombatives on 2007-06-11
so if ubuntu can be loaded on a ericson or a nokia it could be loaded on to a samsung t619 also?

---

### Post by PartisanEntity on 2007-06-12
Just to avoid any misunderstandings, I did not load Ubuntu on to my cell phone, I merely synchronize the calendar, phone book and task list in Evolution with those on my phone :)

So, if anyone knows if the Nokia 6300 synchs with Evolution without problems please let me know, I may be getting the phone today.

---

### Post by hesee on 2007-06-12
I have just bought nokia 6300 (which is a nice phone :) ) I could try these sync things, although i haven't tried before, so i'm not sure how to do these (maybe ubuntuguide helps, i'll take a look later)

---

### Post by PartisanEntity on 2007-06-12
> **hesee said:**
> I have just bought nokia 6300 (which is a nice phone :) ) I could try these sync things, although i haven't tried before, so i'm not sure how to do these (maybe ubuntuguide helps, i'll take a look later)

Here are good instructions to Sync a phone with Evolution, I currently use it with my SonyEricsson D750i.

---

### Post by hesee on 2007-06-12
It seems so... A lot of threads, how-tos with 44 steps, etc... :( I'm a little busy right now, so i'm not sure when i have time to concetrate on this (I have a hunch that this might not be a single-click operation). 

But basically i'm interested how to do this, so i'll try when i have time.

---

### Post by PartisanEntity on 2007-06-12
> **hesee said:**
> It seems so... A lot of threads, how-tos with 44 steps, etc... :( I'm a little busy right now, so i'm not sure when i have time to concetrate on this (I have a hunch that this might not be a single-click operation). 

But basically i'm interested how to do this, so i'll try when i have time.

I forgot to post the link earlier, here it is:
[http://ubuntuforums.org/showpost.php?p=1779032&postcount=3](http://ubuntuforums.org/showpost.php?p=1779032&postcount=3)

---

### Post by UbuWu on 2007-06-12
I haven't tried synching with evolution yet, but it does work great with [Wammu]("http://wammu.eu/") phone manager.

---

### Post by PartisanEntity on 2007-06-13
So I got the Nokia 6300 yesterday and unfortunately it does not seem to be compatible with this method that I posted earlier:
[http://ubuntuforums.org/showpost.php?p=1779032&postcount=3](http://ubuntuforums.org/showpost.php?p=1779032&postcount=3)

At least it doesn't seem to support IrMC (whatever that is).

It did work with Wammu but that is useless for me since I would like to sync my phone with Evolution.

Another method I read about uses Gnokii but I don't think it syncs with Evolution.

The only work around I can think of at the moment, is to boot into Windows, first sync my old SonyEricsson with Outlook and then to sync the Nokia with Outlook.

(For me the important thing is to retain the contacts including all the data such as birthdays, emails, address, which you cannot do with SIM contacts)

---

### Post by ounn on 2007-06-16
I have just buy a nokia 6300 too. If you manage a way to sync with evolution please post here you solution. I'm trying too .....


ounn

---

### Post by PartisanEntity on 2007-06-16
I have tried various methods: Wammu, Gnokii and Multisync. Wammu and Gnokii are simple and primitive phone managers, they worked. Multisync is a proper syncing tool which worked great with my SonyEricsson D750i and tied into Evolution nicely, but it didn't work with the Nokia 6300, I think this is because the Nokia doesn't support IrMC, I am not sure what that is though.

---

### Post by ounn on 2007-06-17
Hi i managed to sync evolution contacts with my nokia 6300 :p

First pair your nokia with your pc :

 ```
 
 bluez-pin in  XX:XX:XX:XX:XX
 bluez-pin out XX:XX:XX:XX:XX

```

then with multisync gui (Use multisync-gui not multysinc)

Add a new Group call that "Nokia"

In this group create 2 members

 1. gnokii-sync
 2. evo2-sync

In gnokii xml configuration (tricky replace 6300 with 6310)


```

<config>
  <connection>bluetooth</connection>
  <port>XX:XX:XX:XX:XX:XX</port>
  <model>6310</model>
</config>

```

In evo2-sync select "Personal to every fields.


This works :)

---

### Post by PartisanEntity on 2007-06-17
> **ounn said:**
> 

then with multisync gui (Use multisync-gui not multysinc)

Add a new Group call that "Nokia"

In this group create 2 members

 1. gnokii-sync
 2. evo2-sync

I can't seem to find any 'Group' feature in multisync, which version are you using? I have 0.82

> **ounn said:**
> In gnokii xml configuration (tricky replace 6300 with 6310)


```

<config>
  <connection>bluetooth</connection>
  <port>XX:XX:XX:XX:XX:XX</port>
  <model>6310</model>
</config>

```

hmm I don't remember an xml file for gnokii is this supposed to be in /home?

Thanks for the info so far, I really hope this works out on my end too :)

---

### Post by PartisanEntity on 2007-06-17
Okay I have done some research and it seems the multisync package from the Feisty repos and multisync-gui are two different things?

This is based on the German ubuntu users wiki which offers a deb location for it:
[http://wiki.ubuntuusers.de/OpenSync](http://wiki.ubuntuusers.de/OpenSync)

---

### Post by ounn on 2007-06-17
Im using multisync-gui 0.9. It is also at fesity repo.


In the multisync-gui interface you can configure the syncronization members. The gnokki-sync conf is made by a xml. You can edit that xml within the multisync-gui.

---

### Post by PartisanEntity on 2007-06-17
> **ounn said:**
> Im using multisync-gui 0.9. It is also at fesity repo.


In the multisync-gui interface you can configure the syncronization members. The gnokki-sync conf is made by a xml. You can edit that xml within the multisync-gui.

Okay I got it to work, why do I need to choose between the evo or gnokii entries? What does it mean to me specifically?

---

### Post by ounn on 2007-06-17
In the members area you specify who are the "members" in the synchronization process. You can think in gnokii like a plugin to your nokia phone and evo a plugin to evolution. If you add the google-calendar to your members you can sync those 3 (nokia phone, evolution and google calendar). 



ounn

---

### Post by PartisanEntity on 2007-06-17
Great thanks very much.

I now managed to get about 3 copies of each entry both in Evolution as well as on my Nokia phone book, guess I am going to have to play around with it a bit more :)

---

### Post by PartisanEntity on 2007-06-17
Another question :)

Do you know if it is possible to copy all contacts from Evolution to the phone only? I do not want SIM contacts or Nokia phone book contacts copied to Evolution.

I've moved the thread to a more appropriate forum since it has become an extensive tech support thread :)

---

### Post by ounn on 2007-06-17
Yes,  i have that problem at first too. I suggest to you backup your phone and evoltuin contacts first. 

I suggest to you delete all you contacts from the phone (backup first :) ) and then add all the information you need (phone numbers) in evolution. Than synchronize both. You only have to this the first time you sync off course. Be carefuly beacause the syncronization also delete contacts ;)


ounn

---

### Post by ounn on 2007-06-17
> **PartisanEntity said:**
> Another question :)

Do you know if it is possible to copy all contacts from Evolution to the phone only? I do not want SIM contacts or Nokia phone book contacts copied to Evolution.

I've moved the thread to a more appropriate forum since it has become an extensive tech support thread :)

I dont know how you can synchronize in just one side, at least with the multisyn-gui. You can try with the command line.


This command has the same efect of refresh botton in the gui

```

msynctool --sync nokia

```


maybe there are more option to you achieve that.

ounn

---

### Post by PartisanEntity on 2007-06-17
This is what I tried:

1. Deleted all phone book entries in Nokia
2. Started the synchronisation process

But it still copied contacts from the SIM also.

Did you also delete all SIM contacts?

And, how long does the sync process take? My bluetooth light is still blinking even though it the number of contacts synced has not changed. If I quit multisync-gui and start it at a later time it says that the previous sync process did not finish.

---

### Post by ounn on 2007-06-17
Yes it also sync the SIM contacts. Yes i have deleted all the contacts. But first i have save all the contacts in my old phone :p 

The sync process it takes 10-15 seconds.


ounn

---

### Post by PartisanEntity on 2007-06-17
There is obviously something I do not understand.

If I run the sync process a 2nd time, it multiples the entries, so I end up with 2 of each on the phone and on Evolution.

Also what does the 'Which entry do you want to use'  window mean? Which entry do I want to use from/to where?

(I have tried posting these questions to the user mailing list but my emails get bounced back even though I registered)

---

### Post by ounn on 2007-06-17
> **PartisanEntity said:**
> 
If I run the sync process a 2nd time, it multiples the entries, so I end up with 2 of each on the phone and on Evolution.


Thats strange it works for me. Every time a run the sync i get both syncs without repeated entry's.


> 
Also what does the 'Which entry do you want to use'  window mean? Which entry do I want to use from/to where?



That means that you have one contact in evolution and another in your phone with the same email or the same phone number. This is asking you wich entry do you want to save. If you choose Duplicate there you have your duplicated entrys.

---

### Post by PartisanEntity on 2007-06-18
I have been playing around with it quite a bit and I keep getting duplicates and triplicates if I run the sync process a 2nd or 3rd time. What a shame, it would be really great if it worked properly.

---

### Post by ounn on 2007-06-18
> **PartisanEntity said:**
> I have been playing around with it quite a bit and I keep getting duplicates and triplicates if I run the sync process a 2nd or 3rd time. What a shame, it would be really great if it worked properly.

Strange, to me works very good. Are you sure that you are not saying to duplicate when the application ask you what version do you want do preserve?


ounn

---

### Post by PartisanEntity on 2007-06-18
You see, the problem is I am not sure *where* the entry is that it is asking me about. It simply pops up a window with two sections and both have an 'apply' button.

---

### Post by ounn on 2007-06-18
You have two entrys write? The entry from the left is the version you have in first in you members list in multisync-gui.


Example:

If have gnokii in your members list in the first position, than the left version is from your phone and the right one from evolution. 

You have to choose the apply from the version you want to keep.

ounn

---

### Post by PartisanEntity on 2007-06-18
Thanks very much for your patience so far.

So what is this trying to tell me:

[I]p.s. in multisync-gui I have:
gnokii
evo2[/I]

---

### Post by ounn on 2007-06-18
Ok, if you press the left apply your contact in the phone will be replaced with your evoltion contact. If you press the rigth apply your evolution contact will be replaced with your phone contact.


ounn

---

### Post by PartisanEntity on 2007-06-18
But the two entries are not for the same contact, it doesn't seem to make sense?

And could you please tell me which packages you installed from the Feisty repos? I have not been able to find multisync-gui in them. Does it have a different name or have you added any 3rd party repos?

---

### Post by ounn on 2007-06-19
What multisync-gui version dou you have installed? I have 0.91
I realy dont know from what repo a install multisync-gui


But i can give you my source list.


```


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://pt.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://pt.archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://pt.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://pt.archive.ubuntu.com/ubuntu/ feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://pt.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://pt.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://pt.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://pt.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse


##Exaile
deb http://download.tuxfamily.org/syzygy42 feisty exaile

##Avant-Window-Navigator
deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe #Added by software-properties
#AUTOMATIX REPOS END
deb http://debian.o-hand.com feisty/
deb http://elisa.fluendo.com/packages feisty main
deb http://debian.cihar.com/ unstable main contrib non-free

##Bluethoot
deb http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ feisty main
deb-src http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ feisty main


```




ounn

---

### Post by PartisanEntity on 2007-06-19
> **ounn said:**
> 
```

##Bluethoot
deb http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ feisty main
deb-src http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ feisty main


```


Okay that is the same repo I used. It is not the **official** Ubuntu Feisty repository and that is what confused me at the beginning of this thread when I asked you if it was in the Feisty repo and you said yes :)

However for some reason which I will have to look into further at some point, I keep getting multiplications of my contacts. For the mean time I have gone back to booting into XP to sync my phone with the account I made for this sole reason in MS Outlook.

Thanks for all your help **ounn**, I appreciate it :)

---

### Post by desperado666 on 2007-06-26
Someone know how to access the Short Messages on my Nokia 6300 Phone?
Want to read and store them on my PC.

---

### Post by PartisanEntity on 2007-06-27
> **desperado666 said:**
> Someone know how to access the Short Messages on my Nokia 6300 Phone?
Want to read and store them on my PC.

Yes there are two tools you could use, one is called Wammu the other is called Gnokii, both allow you to access your phone. I would recommend Wammu, it has a more extensive user interface and allows you to do many things, such as backup all the data (phone book and messages), send sms to email etc...

---

### Post by desperado666 on 2007-06-27
ok can establish connection with my phone but i cant read the sms memory. Why?

---

### Post by lzap on 2007-07-19
[http://www.opensync.org/](http://www.opensync.org/)  -- early beta -- no packages yet (only for developers) But this project rocks!

---

### Post by diehorsti on 2007-08-03
Hi all,

I tried all what you wrote,

but I have no luck on syncing the nokia 6300 with evolution.

I used multisync and opensync 0.21 from jahn.

Used 6310 as the phone in gnokii.

Then I issue the command:
msynctool --sync nokia2 

and I get:
Synchronizing group "nokia2" The previous synchronization was unclean. Slow-syncing Member 1 of type evo2-sync just connected Member 2 of type gnokii-sync just connected All clients connected or error ... ... Received an entry pas-id-4474C21A00000010 with data of size 4 from member 1 (evo2-sync). Changetype ADDED Member 1 of type evo2-sync just sent all changes Member 2 of type gnokii-sync just sent all changes All clients sent changes or error All conflicts have been reported *** glibc detected *** /usr/lib/opensync/osplugin: double free or corruption (!prev): 0x0806de48 *** ======= Backtrace: ========= /lib/tls/i686/cmov/libc.so.6[0xb7b727cd] /lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7b75e30] /usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb7e42131] /usr/lib/opensync/plugins/gnokii_sync.so(gnokii_contact_write+0x214)[0xb7efafc4] /usr/lib/opensync/plugins/gnokii_sync.so(gnokii_contact_commit+0x185)[0xb7efb6d5] /usr/lib/libopensync.so.0(osync_member_commit_change+0x314)[0xb7c79d17] /usr/lib/opensync/osplugin(message_handler+0x5b0)[0x804abfa] /usr/lib/libopensync.so.0[0xb7c85969] /usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7e3adf2] /usr/lib/libglib-2.0.so.0[0xb7e3ddcf] /usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7e3e179] /usr/lib/opensync/osplugin(main+0x55e)[0x804a619] /lib/tls/i686/cmov/libc.so.6(libc_start_main+0xdc)[0xb7b20ebc] /usr/lib/opensync/osplugin[0x8049bb1] ======= Memory map: ======== 08048000-0804c000 r-xp 00000000 03:01 5308629 /usr/lib/opensync/osplugin 0804c000-0804d000 rw-p 00003000 03:01 5308629 /usr/lib/opensync/osplugin 0804d000-08109000 rw-p 0804d000 00:00 0 [heap] b5800000-b5821000 rw-p b5800000 00:00 0 b5821000-b5900000 ---p b5821000 00:00 0 b599c000-b59a7000 r-xp 00000000 03:01 5439552 /lib/libgcc_s.so.1 b59a7000-b59a8000 rw-p 0000a000 03:01 5439552 /lib/libgcc_s.so.1 b59b9000-b59c0000 r--s 00000000 03:01 3506411 /usr/lib/gconv/gconv-modules.cache b59c0000-b59c1000 ---p b59c0000 00:00 0 b59c1000-b61c1000 rw-p b59c1000 00:00 0 b61c1000-b61c2000 ---p b61c1000 00:00 0 b61c2000-b69c2000 rw-p b61c2000 00:00 0 b69c2000-b69c3000 ---p b69c2000 00:00 0 b69c3000-b71c3000 rw-p b69c3000 00:00 0 b71c3000-b71c4000 ---p b71c3000 00:00 0 b71c4000-b79c4000 rw-p b71c4000 00:00 0 b79c4000-b79cf000 r-xp 00000000 03:01 5308624 /usr/lib/opensync/formats/xml-kde.so b79cf000-b79d0000 rw-p 0000a000 03:01 5308624 /usr/lib/opensync/formats/xml-kde.so b79d0000-b79e5000 r-xp 00000000 03:01 5308625 /usr/lib/opensync/formats/xml-vcal.so b79e5000-b79e6000 rw-p 00015000 03:01 5308625 /usr/lib/opensync/formats/xml-vcal.so b79e6000-b79f1000 r-xp 00000000 03:01 5308623 /usr/lib/opensync/formats/xml-evolution.so b79f1000-b79f2000 rw-p 0000a000 03:01 5308623 /usr/lib/opensync/formats/xml-evolution.so b79f2000-b79fe000 r-xp 00000000 03:01 5308627 /usr/lib/opensync/formats/xml-vnote.so b79fe000-b79ff000 rw-p 0000b000 03:01 5308627 /usr/lib/opensync/formats/xml-vnote.so b79ff000-b7a0e000 r-xp 00000000 03:01 5308626 /usr/lib/opensync/formats/xml-vcard.so b7a0e000-b7a0f000 rw-p 0000e000 03:01 5308626 /usr/lib/opensync/formats/xml-vcard.so b7a0f000-b7a20000 r-xp 00000000 03:01 4474200 /usr/lib/libbluetooth.so.2.5.0 b7a20000-b7a21000 rw-p 00011000 03:01 4474200 /usr/lib/libbluetooth.so.2.5.0 b7a21000-b7a27000 r-xp 00000000 03:01 5439616 /lib/libusb-0.1.so.4.4.4 b7a27000-b7a29000 rw-p 00005000 03:01 5439616 /lib/libusb-0.1.so.4.4.4 b7a29000-b7a2b000 r-xp 00000000 03:01 5308620 /usr/lib/opensync/formats/file.so b7a2b000-b7a2c000 rw-p 00001000 03:01 5308620 /usr/lib/opensync/formats/file.so b7a2c000-b7a2d000 r-xp 00000000 03:01 5308618 /usr/lib/opensync/formats/data.so b7a2d000-b7a2e000 rw-p 00000000 03:01 5308618 /usr/lib/opensync/formats/data.so b7a2e000-b7a2f000 r-xp 00000000 03:01 5308622 /usr/lib/opensync/formats/todo.so b7a2f000-b7a30000 rw-p 00000000 03:01 5308622 /usr/lib/opensync/formats/todo.so b7a30000-b7a31000 r-xp 00000000 03:01 5308621 /usr/lib/opensync/formats/note.so b7a31000-b7a32000 rw-p 00000000 03:01 5308621 /usr/lib/opensync/formats/note.so b7a32000-b7a33000 r-xp 00000000 03:01 5308628 /usr/lib/opensync/formats/xmldoc.so b7a33000-b7a34000 rw-p 00000000 03:01 5308628 /usr/lib/opensync/formats/xmldoc.so b7a34000-b7a35000 r-xp 00000000 03:01 5308619 /usr/lib/opensync/formats/event.so b7a35000-b7a36000 rw-p 00000000 03:01 5308619 /usr/lib/opensync/formats/event.so b7a36000-b7a39000 r-xp 00000000 03:01 1572939 Member 1 of type evo2-sync committed all changes. Error writing entry pas-id-46B2FB6300000058 to member 2 (gnokii-sync): Broken Pipe Mapping Write Error: Broken Pipe ... ... Error writing entry pas-id-4474C21A00000010 to member 2 (gnokii-sync): Broken Pipe Mapping Write Error: Broken Pipe Member 2 of type gnokii-sync had an error while commiting changes: Broken Pipe All clients have written Member 2 of type gnokii-sync had an error while calling sync done: Broken Pipe Member 2 of type gnokii-sync had an error while disconnecting: Broken Pipe Member 1 of type evo2-sync just disconnected All clients have disconnected The sync failed: Unable to finish the sync for one of the members Error while synchronizing: Unable to finish the sync for one of the members

nothing happens with the phone. No new entries. Using Obex I can send and receive files, so bluetooth is working. But no syncing.

Any ideas?

Thank you so much in advance.

Cheers.
:confused:

---

### Post by schowanni on 2007-08-04
I have the same problem

```

*** glibc detected *** /usr/lib/opensync/osplugin: double free or corruption (!prev): 0x0807c4b0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7bc77cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7bcae30]
...

```

i attached the opensync traces...

---

### Post by PartisanEntity on 2007-08-06
Unfortunately it seems that the success of syncing our phone with evolution is at the moment based on luck mainly. My syncing ends up duplicating or triplicating entries.

---

### Post by ounn on 2007-08-08
Maybe i am a lucky guy but the contacts syn works pretty fine between nokia and evolution

---

### Post by desperado666 on 2007-08-08
try to create a new one on your pc and sync it to your phone. after that try to edit this new contact and save it when you are done. For me it doesnt work.

---

### Post by CosminGC on 2007-10-01
So, how is the status now? I wanna buy a phone so I would like to know is 6300 syncing fine with evolution?

---

### Post by PartisanEntity on 2007-10-01
It works with some people and not with others, whenever I try to sync my Nokia 6300 with Evolution it ends up multiplying the entries in both. With other users it worked.

---

### Post by CosminGC on 2007-10-01
Thanks for the quick replay. Does anyone know if nokia 3110c works better? Or is there other nokia phone better with evolution?

---

### Post by nas123 on 2007-12-11
OK so I've got this far in 7.10

Using Multisync from the ubuntu 7.10 repositories and 
Gnokii-sync from 
[http://opensync.gforge.punktart.de/repo/opensync-0.21/pool/main/libo/libopensync-plugin-gnokii/libopensync-plugin-gnokii_0.22-feisty2_i386.deb](http://opensync.gforge.punktart.de/repo/opensync-0.21/pool/main/libo/libopensync-plugin-gnokii/libopensync-plugin-gnokii_0.22-feisty2_i386.deb)

Gnokii connects to my phone and I've grabbed my multisync settings from there.


~$ msynctool --showgroup Nokia
Groupname: Nokia
Member 1: evo2-sync
        Configuration : <?xml version="1.0"?>
<config>
  <address_path>default</address_path>
  <calendar_path>default</calendar_path>
  <tasks_path>default</tasks_path>
</config>

Member 2: gnokii-sync
        Configuration : <config>
  <connection>Nokia</connection>
  <port>/dev/ttyACM0</port>
  <model>AT</model>
</config>


Gives me ...
~$ msynctool --sync Nokia
Synchronizing group "Nokia" 
Error while initializing syncengine: Connection type is not (correctly) set in configuration


Any clues here would be greatly appreciated,
Thanks

---

### Post by Berduchwal on 2008-01-19
I am trying to connect 6300 via usb.

Problems so far:

- do I need to pair 6300 with PC?
- in multysunc0.90 which is called multisynch-qud I can not add members to the group, when I try there is nothing I can add, list is empty.

Any clues?

- i manged to find multisync-gui but i have the same problem as described above. I can not add members of the group

---

### Post by SkeRoy on 2008-06-22
I FOUND !

Sorry, i hadn't see there were 5 pages.
So I found alone the download of opensync-plugin-gnokii on [http://packages.ubuntu.com/search?keywords=opensync-plugin-gnokii](http://packages.ubuntu.com/search?keywords=opensync-plugin-gnokii)
for intrepid but it works perfect with hardy

Thanks to [http://wiki.gnokii.org/index.php/Nokia6300Config](http://wiki.gnokii.org/index.php/Nokia6300Config)
this configuration is perfect !

<config>
  <connection>bluetooth</connection>
  <port>telephone MAC adress</port>
  <model>6510</model>
</config>

---

### Post by CosminGC on 2008-06-22
> **SkeRoy said:**
> I FOUND !

Sorry, i hadn't see there were 5 pages.
So I found alone the download of opensync-plugin-gnokii on [http://packages.ubuntu.com/search?keywords=opensync-plugin-gnokii](http://packages.ubuntu.com/search?keywords=opensync-plugin-gnokii)
for intrepid but it works perfect with hardy

Thanks to [http://wiki.gnokii.org/index.php/Nokia6300Config](http://wiki.gnokii.org/index.php/Nokia6300Config)
this configuration is perfect !

<config>
  <connection>bluetooth</connection>
  <port>telephone MAC adress</port>
  <model>6510</model>
</config>

I use:
<model>6300</model>

:D

---

### Post by [CPR]-AL.exe on 2008-07-12
How do i connect via USB?..

---

### Post by [CPR]-AL.exe on 2008-07-12
I've read through all pages, but didn't understand, how can i install gnokki and evolution plugins for multisync-gui 0.91. I've managed to find this plugins only for multisync 0.82..

---

### Post by [CPR]-AL.exe on 2008-07-13
Anyone here? :(

---

### Post by nas123 on 2008-07-13
Install   multisync-qad

lsusb will tell you what USB your device is connected to eg:

~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0421:04f9 Nokia Mobile Phones Nokia 6300 (PC-Suite mode)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Now the trick seems to be getting the device name to put in the gnokii-sync config.  I've got

<config>
  <connection>serial</connection>
  <port>/dev/ttyACM0</port>
  <speed>9600</speed>
  <model>6300</model>
</config>

But no joy yet

---

### Post by nas123 on 2008-07-13
Now trying syncml-obex-client instead of gnokii-sync as 6300 works perfectly (?)...

[http://www.opensync.org/wiki/DeviceCompatibilityList](http://www.opensync.org/wiki/DeviceCompatibilityList)

---

### Post by [CPR]-AL.exe on 2008-07-14
I've got multisync-qad and multisync-gui installed from here: [http://opensync.gforge.punktart.de/repo/opensync-0.21/pool/main/m/multisync-gui/?C=N;O=D](http://opensync.gforge.punktart.de/repo/opensync-0.21/pool/main/m/multisync-gui/?C=N;O=D)


But there are no evolution or gnokki plugin there. They come with several other plugins, but they are no use for me :(

---

### Post by nas123 on 2008-07-14
From ubuntu repos...

multisync-tools
multisync0.90
opensync-plugin-evolution
opensync-plugin-syncml

Found this - 6300 needed username/password on phone and in obex config to match
[http://libsyncml.opensync.org/ticket/123](http://libsyncml.opensync.org/ticket/123)

---

### Post by nas123 on 2008-07-14
My system is not reporting any Identifier Descriptions with

# syncml-obex-client -u
Found 3 USB OBEX interfaces
Interface 0:
	Manufacturer: Nokia
	Product: Nokia 6300
	Interface description: (null)
Interface 1:
	Manufacturer: Nokia
	Product: Nokia 6300
	Interface description: (null)
Interface 2:
	Manufacturer: Nokia
	Product: Nokia 6300
	Interface description: (null)

and it seems it should be calling them something. 

(null) should be SYNCML-SYNC

Anyone know how this occurs ?

---

