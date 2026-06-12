---
title: "Two Grub Boot Loaders - Choose Default"
date: 2008-01-18
forum: General Help
---

### Post by BellaBean on 2008-01-18
Here is the situation. I have an older laptop and loaded Xubuntu on it. It works great and I love it. I recently decided I wanted to also install the TinyMe PCLinuxOS distribution as it runs just a bit faster on my system and is a bit simpler for some other family members. I used gparted and resized/partitioned my HD so I had a small chunk of space to use for the TinyMe installation.

I installed TinyMe and it in turn installed the GRUB loader the same as Xubuntu did when I installed that. I ran into a problem when I realized the TinyMe GRUB loader install became the default boot loader (the Xubuntu GRUB files are still there though) and did not list Xubuntu. I found how to fix this and added Xubuntu in the TinyMe boot loader and everything is now good.

I have two questions that are related to each other and the GRUB loader situation. First, is there a way to specify which GRUB loader install is the default one to use? I have no idea how this works or how the TinyMe GRUB install became the default. I assume this happened because it was the last one I installed. 

I was also wondering what would happen if I wanted to take TinyMe off my HD and just use Xubuntu again. I don't think there is an uninstall OS button anywhere in the TinyMe installation, so I was just going to use gparted and delete/erase the partition where that OS resides. I have no idea how this will effect the laptop. I don't know if the Xubuntu GRUB loader will take over again and boot normally or if the system will become unbootable. Any ideas? Thanks.

---

### Post by danwood76 on 2008-01-18
Basically the grub boot loader is loaded into a section of the disk called the MBR (master boot record) in this section grub is installed and it links to the files stored in a specifified location to load up your boot parameters.

Obviosly you now have 2 boot partitions, if you ever wanted to remove TinyMe you can always reinstall grub with the ubuntu live cd or alternate CD so that it points to the correct place.

regards,
Danny

---

### Post by logos34 on 2008-01-18
If you decide to remove tinyme, it's easiest to overwrite the MBR first with xubuntu grub, before you delete the partition in Gparted.  Just boot into xubuntu and do

sudo grub-install /dev/sda  (or whatever the disk is).

---

### Post by BellaBean on 2008-01-18
Awesome! Thanks to the both of you. I now understand what happened and how to fix it. In the interim I was surfing around and found something called the Super Grub Disk. It looks like it could manipulate the MBR the way I wanted, but the simple command logos34 listed will do what I need and is much easier :)

---

### Post by nstamoul on 2008-04-22
Reopening this thread with a similar problem.

I have 2 disks on my pc,one for data (sda) and one with dual boot Ubuntu Hardy,Windows installed on it.To cut a long story short I somehow ended up with 3 grubs (thats  right!).Now of course I want to erase the 2 of them and keep the correct one.Here is where the boot loaders are located.

sda (data) <----------------------Needs to be erased
sdb (OS disk) <-------------------Need to keep only this one
sdb3 (root hardy partition) <-----Needs to be erased as well

Any suggestions?

---

### Post by danwood76 on 2008-04-22
do you have 3 /boot partitions?

if not then its only installed on the MBR and it doesnt matter, just set your BIOS to boot from the disk you want it to.

---

### Post by nstamoul on 2008-04-22
No I have no separate /boot partitions.

The one installed on /dev/sda3 is installed on the **root** partition.I need that removed.And of course the one on the data disk as well.

Just to make clear,my configuration is working,it just bugs me that I have the other couple of grubs installed,though not necessary.

---

### Post by danwood76 on 2008-04-22
On the other drive does it have a /boot folder (thats what I originally meant)
If not its just installed on the MBR and wont be doing anything, you cant store data on that area of the disk so just leave it.

If you didnt have grub there it would probably be another boot loader anyway so I wouldnt worry.

---

### Post by nstamoul on 2008-04-22
My problem is that i might have used sudo grub-install /dev/sdb3 which means I have installed grub on my / partition.

My assumptions are based on a script I found here on ubuntuforums which tells me that I have grub installed on the 3 partitions mentioned earlier.

I will attach the script.If you would me willing to run it and paste its output so we could compare I would be thankful.

---

### Post by danwood76 on 2008-04-22
That script wont work on my machine as im running fakeraid.
I can tell you though I have got grub installed on my main disks MBR and on my / partition boot record as I need to have it installed that way thanks to my mobo not liking dual booting much.
It doesnt make any diffrence what so ever to my disk and my system runs fine.

Even with it installed on your / partition it wont be doing anything as you never call its boot record up unless you chainload the partition.
Best thing to do is just leave it, if you have a working configuration.

---

### Post by nstamoul on 2008-04-22
Yep seems like the best option I have is to leave it as it is.

Thanks a lot for your help :)

---

### Post by AldenIsZen on 2008-05-18
I think I installed extra grubs due to not understanding what I was doing with Super Grub Disk. How do I run the script you uploaded? My Windows now boots slow.. and one I even restarted it and it restarted back to windows.. never going to grub. It's like it hangs for a minute.. literally and then boots Windows normally at the correct speed. This I would rather not just leave alone.


edit/ I figured out how to get script to run, by checking execute in properties.

 I am not a genius.. but this doens't look right to me.. 

```
/dev/sda	GRUB gefunden
/dev/sda1	
GRUB gefunden
/dev/sda2	
GRUB gefunden
/dev/sda3	
GRUB gefunden
/dev/sda5	
GRUB gefunden
/dev/sda6	
GRUB gefunden

/dev/sdb	GRUB gefunden
/dev/sdb1	
GRUB gefunden
/dev/sdb2	
GRUB gefunden
/dev/sdb3	
GRUB gefunden
/dev/sdb4	
GRUB gefunden
/dev/sdb5	
GRUB gefunden
/dev/sdb6	
GRUB gefunden
/dev/sdb7	
GRUB gefunden
/dev/sdb8	
GRUB gefunden

```


 Thanks,

 - Alden

---

### Post by danwood76 on 2008-05-19
It looks like its finding grub on each partition which shouldnt be right.
Especially if windows still boots, its possible that the script is getting confused somehow.

WHat do you mean by windows booting slow?
Is it that there is a delay before it starts to boot and then windows boots normally?

Do you have a graphics card with 2 video outputs? It may be for some daft reason that grub is being rendered on the second screen?

---

### Post by AldenIsZen on 2008-05-19
Yes, I think I installed grub on every partition trying to get it to work right.. and I don't know how to take it off.. 

 That is correct, there is a severe delay before Windows starts to boot (I see Windows loading splash), there is just a black screen, and then it appears to boot normally once I see the Windows loading bar and splash screen.

 I do have a video card and I have left TV out on (in windows) instead of taking it off when I don't need it, but I don't think that is it. I am pretty sure this is tied to when I tried to reinstall Grub. I have left the T.V. out on before and never had this issue.

 I also get other weird things that may be related, such as the session for Ubuntu not loading up completely, i.e. desktop icons missing. A reboot usually works, but just logging out and back in seems to always work. 

 What is REALLY bugging me is that I can't get Acronis Disk director in Windows to boot. It says something about can't see any hard drives/partitions. GParted live cd tells me that two of my partitions are corrupt and to run a disk check, and reboot twice, which I have done. I really would like to combine those partitions but I can't seem to get disk imaging software to load. I think it has to do with this!

 edit/ Oh and by the way, good morning. I just got up and checked email and it said you posted a minute before I got here!

---

### Post by danwood76 on 2008-05-19
Ctrl+r should refresh the desktop and hopefully the icons on there, try that when you next get that issue.

What are the formats of the partitions with errors?
It may be that grub is hiding some of the partitions so Acronis cant see them and its getting confused. Does acronis work with EXT3?

To fix your windows issue you might be better off re installing the windows MBR from the super grub disk and then re-installing grub from the ubuntu live CD.
The Super Grub Disk can be quite a powerful tool, but if you dont know what your doing you can royally screw things with a few of the tools in there.

---

### Post by AldenIsZen on 2008-05-19
NTFS are the two partitions that have the error in GParted. It did say there were issues with my Windows installation partition and others on the first hard drive, but it is now only the 2 on my secondary that are giving me issues. The rest of the partitions on my secondary are ext2. I don't have any ext3.

 Yes, Acronis does work with EXT3. I think it can resize, etc. I know it can see them. I would use GParted before I use Acronis though becasue it is windows based, and even though it does it on reboot and before Windows boots.

 I will try redoing the MBR with SGD and then using the live CD to fix GRUB. I am pretty sure I did the Windows MBR then did GRUB so that it would be alright if I uninstalled Ubuntu.

 get back to you in a few.. .. ..

---

### Post by danwood76 on 2008-05-20
I would run checkdisk from within windows on those two partitions.
Windows does a whole better job with NTFS than linux does (naturally).

---

### Post by agatestnalderman on 2008-06-12
ok slighhhtly different problem,

i have an acer aspire 5315 bundled with an OEM vista.  naturally, i immediately proceeded to load ubuntu 7.10, but could never get the soundcard recognized so i always had to blow through grub and boot to vista.

then i thought i would try the beta 8.04, maybe the sound card and the ALSA drivers would work on this new version but no such luck.

ok now that i saw that 8.04 was out of beta and in the LTS i got excited! i thought wow ok, now it will definitely work and i can use ubuntu again, hooray!

SO i dl in vista and burn onto DVD and to my surprise, it says it can install ubuntu 8.04 STRAIGHT THROUGH VISTA!  how cool, thinks i, so i go ahead and do this BUT now when i turn my laptop on i get grub 8.04 (the beta one) and vista as my options then when i pick vista i get the vista version of grub asking do i want to load vista or ubuntu (the stable LTS one)

My question is, how can i chuck the beta 8.04 off my MBR and delete grub altogether?? (since the stable LTS ubuntu i want to keep seems to load through the vista loader) 

I've backed everything up, i just can't figure out how to get rid of it without making problems....if i just delete the partition then im going to get grub error 22 or whatev( i've had problems with this before :p )

suggestions?

---

### Post by danwood76 on 2008-06-13
Reinstall the windows MBR, this can be done in loads of different ways, from within ubuntu, from the vista install CD.

Heres a ubuntu guide:
[http://www.arsgeek.com/?p=3340](http://www.arsgeek.com/?p=3340)

---

