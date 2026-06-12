---
title: "Grub error 17, cant get into ubuntu"
date: 2006-10-23
forum: General Help
---

### Post by M!K3_$ on 2006-10-23
i dual boot XP home and Ubuntu 6.06

the other day i reinstalled windows and then grub disapeared
so i found the instructions on how to reinstall grub from the live CD.
did it, booted up, grub was there, all was good
until...
i tryed boot ubuntu and i got a mesage saying
Error 17: cannot mount selected partition

any ideas?


edit:
srry OmahaVike, didnt see ur thread. still need help though

---

### Post by TiredBird on 2006-10-23
The message you are getting is because Grub doesn't recognize the partition type. Since it recognizes most common types it is likely that your partition table has gotten corrupted somehow, (losing that one byte that tells the type would be all that would be necessary.) 

I would suggest you look at your hard disk with a partition program that will tell you what it sees. You may need a live rescue CD. There are several good ones available which you could download and burn with your XP installation.

As an alternative, I think the Ubuntu live/install CD has some rescue functions. You might try booting from that to see what you have.

There are programs that can re-write your partition table if that is the problem. It's unlikely that your data really has disappeared, probably just the partition table at most.

If your partition table has gotten corrupted somehow, (Windows can do it), and you want to preserve the partition's contents, be careful not to do anything that would alter the data still on the disk. Recovery programs can rebuild partition tables but they can't rebuild missing data.

---

### Post by TiredBird on 2006-10-23
Looking at your message again, when you reinstalled Windows, the Windows installer overwrote the Master Boot Record. That's why Grub was gone. The MBR also contains the partition table. It appears that Windows overwrote that too. Hopefully, the reinstall didn't reformat your entire hard-drive or your Ubuntu installation may be gone. Hopefully you have backup for any important data you had on the Ubuntu partition.

---

### Post by M!K3_$ on 2006-10-23
> **TiredBird said:**
> 

There are programs that can re-write your partition table if that is the problem.

So what are examples of these progams and were can i get them
also were are the recovery programs on the live CD

thankx TiredBird

---

### Post by TiredBird on 2006-10-23
Give me a few minutes. I'm going to have to load up my Ubuntu disks and find out what they have.

As for the others, I'll put it all in the same post.

Give me a few minutes.

---

### Post by M!K3_$ on 2006-10-23
i dont know if this helps but this is what i get when i try to start the kernal



     Booting 'Ubuntu, kernel 2.6.15-27-386'
root (hd0,2)
  Filesystem type unknown, partition type 0x82
kernel /boot/vmlinuz-2.6.15-27-386  root=/dev/hdc3 ro quiet splash

Error 17: Cannot mount selected partition

Press any key to continue..._


then after i push enter. i just go back to grub
i can get into windows just not ubuntu

---

### Post by M!K3_$ on 2006-10-23
o, and i checkd the partition table and all the stuff seems to be still there because its as full as it was last time

---

### Post by Rui Pais on 2006-10-23
hi, read this:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by TiredBird on 2006-10-23
Here's a couple of things you can do immediately. 

Boot up from your Ubuntu install disk. (I assume you have one.) Execute the default first menu item, (install, or live or something like that), which will run Ubuntu from the CD. 

From the desktop, click system, (I think it is) and select the option thats about the third one, partitioning - GParted. Executing that will give you a graphical picture of your hard-disk(s) and its (their) partitions. Looking at that you should be able to see if the system is still recognizing your partitions. I'm assuming that part of it is not identifiable.

Close out of that and execute 'Applications -> Accessories -> Terminal' (I think). Anyway, get a terminal running. Then from the command line run: ```
sudo fdisk -l
``` (thats a small ell on the end, not an eye) which lists all of your drives and all of their partitions. Copy and paste the output from that to a post on the forum so I can see what you got.

In the meantime, I'll try to find some easy way for you to get a few rescue tools as its sounding more and more like that is what you are going to have to do.

Your avatar looks like the Chinese/Japanese symbol for East or am I overlooking something?

---

### Post by TiredBird on 2006-10-23
I missed your posts when I was typing mine. Looks like I was wrong. Different kind of problem.

Anyway, we still need the information.

---

### Post by TiredBird on 2006-10-23
I just looked at the reference from Rui Pais. Looks right. I think things got messed up when you reinstalled Windows. Follow the directions referred to. They should solve your problem.

---

### Post by M!K3_$ on 2006-10-23
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        3191    25631676    7  HPFS/NTFS
/dev/hdc2            3192        9601    51488325   83  Linux
/dev/hdc3            9602        9729     1024644+  82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
ubuntu@ubuntu:~$



thats it there

i chose my avatar because it looked cool:) , but if u know what it means then tell me (i tryed to find out but couldnt)

ill try Rui Pais's reference

---

### Post by ~LoKe on 2006-10-23
When you get the "press any key" message, press a key, then press **e** then edit your kernel line and use hdc2 instead of hdc3.  Once you're done, escape, then **b** to boot.  If that doesn't work, change it back, then screw with the hd(0,2) (make it dh(0,1), hd(1,0), hd(2,0), etc) until it boots.

---

### Post by TiredBird on 2006-10-23
I think some things are starting to make sense. I looked at what ~Loke had to say. He looked a lot closer than I had. It looks as if your partitions have been renumbered. When you set it up before you set it for (hd0,2) and hdc3, both partition 3 but your fdisk listing says the main partition is now partition two and those two items should probably be (hd0,1) and hdc2. When you reinstalled Windows the partitions got renumbered somehow.

---

### Post by M!K3_$ on 2006-10-23
ya, i tryd what ~Loke said, it started to boot the kernel,
then.
it stopped somewere (i dont know were because i had resently buggerd up my usplash screen and i cant see anything)

so i dont know what to do know, i tryd Rui Pais's reference but that didnt work

---

### Post by TiredBird on 2006-10-23
I think I've got a plan for how to get there now. I'll feed you a few instructions at a time and you confirm that everything is going okay.

(I'm sure that ~Loke knows what he's talking about but his method entails a little too much black magic for my taste. My method might be a little longer but when you're done you'll know how you did it.)

---

### Post by M!K3_$ on 2006-10-23
allright
give it too me

---

### Post by TiredBird on 2006-10-23
Boot your machine with the ubuntu live install cd (which I presume you have). When you get to the desktop invoke a terminal with ```
[COLOR="Navy"]Applications -> Accessories -> Terminal[/COLOR]
``` Then from the command line: ```
[COLOR="SeaGreen"]sudo grub[/COLOR]
``` which should give you a grub prompt '>'. At the grub prompt enter: ```
[COLOR="SeaGreen"]find /boot/grub/stage1[/COLOR]
``` which should show you in grub-speak the partitions containing Linux boot information. Hopefully, it will at least show you (hd0,1) which will be the same as 'hdc2' which according to 'fdisk -l' is where your Linux partition is. If that is not among the answers STOP! Lets find out first why its not there. But assuming you do find it there, continue on at the grub prompt with: ```
[COLOR="SeaGreen"]root (hd0,1)[/COLOR]
``` which should yield a confirmation that this is a linux partition. At the next grub prompt enter: ```
[COLOR="SeaGreen"]setup (hd0)[/COLOR]
``` which should result in confirmations by grub that it has found several key ingredients and finally with a statement that the setup was successful. At the grub prompt enter: ```
[COLOR="SeaGreen"]quit[/COLOR]
``` to get back to the command line.

What you have done so far is to install the grub boot loader in the master boot record and tell it to look on partition 2 for the rest of the stuff it needs.

Unfortunately, this is not all that has to be done. The stuff on partition 2 also needs to be corrected so it refers to stuff on partition 2, not partition 3. 

Tell me how this worked out while I finish writing up the rest.

---

### Post by ~LoKe on 2006-10-23
> **TiredBird said:**
> I think I've got a plan for how to get there now. I'll feed you a few instructions at a time and you confirm that everything is going okay.

(I'm sure that ~Loke knows what he's talking about but his method entails a little too much black magic for my taste. My method might be a little longer but when you're done you'll know how you did it.)

I was just trying to make sure he was actually able to locate his boot partition.  ;)

---

### Post by TiredBird on 2006-10-23
This set of instructions assumes that everything went okay with the previous set. If there was any problem, DO NOT CONTINUE. Stop, until we find out what is wrong.

Back to the command line: [COLOR="SeaGreen"]```
sudo mount -t ext3 /dev/hdc2 /mnt
```[/COLOR] which mounts your ubuntu partition at /mnt. Next: ```
[COLOR="SeaGreen"]cd /mnt/boot/grub[/COLOR]
``` which puts you in the grub directory of your ubuntu partition. ```
[COLOR="SeaGreen"]cp menu.lst menu.lst.back[/COLOR]
``` which copies your boot menu to a backup file in case we need it later. ```
[COLOR="SeaGreen"]gksudo gedit menu.lst[/COLOR]
``` which should put the boot menu into an editor.

If you scroll down quite a ways you should find four blocks of entries that do not have # in front of them. Each block should begin with the word 'title'. The fourth block is for your Windows partition and shouldn't have to be changed. Its the first, second and third that are probably wrong. Each one of them probably has a line in it that says 'root (hd0,2)'. Change those to 'root (hd0,1)'. It's possible that these are already correct but I doubt it.

Then on the second or third lines of the first two blocks you'll find a reference to 'hdc3' which needs to be changed to 'hdc2'. Again these might already be correct but I doubt it.

Now if you go backward, toward the front of the file, you should find a line beginning with a # that also has an (hd0,2) in it which needs to be changed to (hd0,1). (If you didn't have to change the others you won't have to change this either.) Save the file.

Next you need to: ```
[COLOR="SeaGreen"]gksudo gedit /etc/fstab[/COLOR]
``` to edit the file system table. Again you need to look for improper references to hdc3 and change them to 'hdc2'. Again, if you didn't have to change anything in the boot file, you shouldn't have to change anything here but look carefully anyway. If you make any changes, save the file.

That's it. Exit the live CD and reboot. With a little luck everything should work. Good luck!

---

### Post by ~LoKe on 2006-10-23
Maybe I'm thinking of something else, but shouldn't you unmount the partition before rebooting?

---

### Post by TiredBird on 2006-10-23
~Loke, please forgive me. If you hadn't made the suggestions you did I probably never would have seen what was probably wrong. What you suggested would probably have worked and we may have to resort to it yet if what I'm proposing doesn't work. I was just afraid it might work and we wouldn't know why. I hope you understand. I didn't mean any offense.

---

### Post by ~LoKe on 2006-10-23
> **TiredBird said:**
> ~Loke, please forgive me. If you hadn't made the suggestions you did I probably never would have seen what was probably wrong. What you suggested would probably have worked and we may have to resort to it yet if what I'm proposing doesn't work. I was just afraid it might work and we wouldn't know why. I hope you understand. I didn't mean any offense.

Of course.  We're both just trying to help. ;)

---

### Post by TiredBird on 2006-10-23
I guess it would be better to unmount it but unless my inexperience is causing me to miss something, it shouldn't make any difference.

---

### Post by ~LoKe on 2006-10-23
> **TiredBird said:**
> I guess it would be better to unmount it but unless my inexperience is causing me to miss something, it shouldn't make any difference.

Probably wouldn't matter, but something is nagging me to mention it.

---

### Post by M!K3_$ on 2006-10-23
i have been trying to do what u said in ur first set of instructions a long time ago

that installs the grub
but then im back to square 1
so should i try the second set now
or is somthing else wrong
:S

---

### Post by TiredBird on 2006-10-23
are you getting any error messages with that?

---

### Post by M!K3_$ on 2006-10-23
nope
good to go i guess

i have to just go boot up the live CD here cus im on windows right now

---

### Post by TiredBird on 2006-10-23
what kind of response are you getting from grub when you go through that exercise?

---

### Post by TiredBird on 2006-10-23
try the next part then. see what happens.

---

### Post by M!K3_$ on 2006-10-23
ill go copy it to show u
no errors though

---

### Post by M!K3_$ on 2006-10-23
allright ill go try it

---

### Post by M!K3_$ on 2006-10-23
This is right bfor i quit


grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub>





this is right after


ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$

im going to try the 2nd step now that im on the live CD

---

### Post by TiredBird on 2006-10-23
Looking at that printout, I've got to believe we're on the right track. What do you think ~Loke? Is it going to work?

---

### Post by M!K3_$ on 2006-10-23
on your second step  im having some trouble mounting the partition

when type in the command to mount it, it just gives me all this info about the mount command

ill keep trying different things though

---

### Post by TiredBird on 2006-10-23
Actually that business about trying to guess the BIOS takes place before you see the grub prompt. It just looks like it takes place after when you execute from the command line. Don't concern yourself about it. That's normal.

---

### Post by TiredBird on 2006-10-23
the mount command should be: ```
[COLOR="DarkGreen"]sudo mount -t ext3 /dev/hdc2 /mnt[/COLOR]
``` It ought to work okay.

---

### Post by M!K3_$ on 2006-10-23
ok, got it that time, missed the space inbetween the hdc2 and the /mnt
:>
moving on

---

### Post by TiredBird on 2006-10-23
What's the file system type? I've been assuming it is 'ext3' is that right?

---

### Post by TiredBird on 2006-10-23
You had me worried there. I'm glad you found it.

---

### Post by M!K3_$ on 2006-10-23
i save the edited menu.lst right?

---

### Post by M!K3_$ on 2006-10-23
ahha i just realized even if this all doesnt work it will have raised my bean count 3 fold :> haha

---

### Post by TiredBird on 2006-10-23
my bean count's gone up a little too but I'm not what that means yet. Yes, you should have saved menu.lst.

---

### Post by M!K3_$ on 2006-10-23
allriht i went and saved all the gedit files
im gunna go and try it
wish me luck guys:>

---

### Post by TiredBird on 2006-10-23
There are plenty of Japanese in Vancouver if I remember correctly. Ask one of them what it means. It is very close to the kanji for East but it's not exact. Compare it to the first character in Tokyo. That stands for East. But as I recall, the cross in that is at the base of the tree, not the top of it. Also, I think it has a horizontal line through the box whereas yours has a couple of tick marks. I don't know what yours is.

---

### Post by M!K3_$ on 2006-10-23
haha
i live in kelowna, i have sum asian friends i could ask if i got really curious


umm. same problem as bfor, it starts to boot but it stalls out half way through

:S

---

### Post by TiredBird on 2006-10-23
I can't believe that didn't work.

Do another 'fdisk -l' and lets see again what you got on that hard-disk.

Also, an exact copy of the messages you get when you try to boot.

Maybe we'll see something we overlooked before.

And while you're at it, do a print-out of the menu.lst file and the fstab file. Maybe there's something there we haven't thought about.

---

### Post by M!K3_$ on 2006-10-23
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        3191    25631676    7  HPFS/NTFS
/dev/hdc2            3192        9601    51488325   83  Linux
/dev/hdc3            9602        9729     1024644+  82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
ubuntu@ubuntu:~$


thats the fdisk

---

### Post by M!K3_$ on 2006-10-23
i get no boot mesagges because a while back i accidentally deleted my usplash screen, so it boots up w/ a black screen until login.

so when it stalls out i cant read whats wrong

i check the menu.lst and fstab.file and they are both good

---

### Post by M!K3_$ on 2006-10-23
im thinkin mabye as a last resort i could make a new partition out of a piece of the hdc2 and reinstall linux on that, then i could still keep all my files in tact.

i would rather not though
but if i have to...

---

### Post by TiredBird on 2006-10-24
I've got another thought but I'm still thinking about it. 

I'm thinkings instead of cutting a little off your swap partition, (only need about 25 MB), and making a boot partition. The whole thing becomes a little easier to control then and we don't run the risk of screwing up your data.

But I'm still thinking about it.

---

### Post by M!K3_$ on 2006-10-24
allright, ive never heard of that bfor.
but im game, i have a 1Gb swap

edit: 
is it possible to take it off of hdc2 because there is like 20 Gb free on there

---

### Post by TiredBird on 2006-10-24
I've got a separate boot partition on one of my machines and it sure makes life a lot easier. It has no Linux, no other files, just a 'boot' folder which contains only a 'grub' folder which contains only the essential boot files. Simple and easy to maintain. I have it mounted on every other partition I have. On the partitions I use regularly I even have an icon on the task bar that brings up an editor on the boot menu.

---

### Post by TiredBird on 2006-10-24
I think its best to take it off your swap partition. It's unlikely that you'll ever use the whole 1GB anyway. And we can screw with that partition without putting any of your data at risk.

---

### Post by M!K3_$ on 2006-10-24
sure, explain...

---

### Post by TiredBird on 2006-10-24
Start by using that live CD again. Use the graphical partition editor. Delete the swap partition. (You'll have to unmount it first but the partition editor has a function for doing that.) Then create two new partitions, the swap partition at 950 MB and the balance to the boot partition. If you do it right the big swap one will end up being number 3 and the boot partition will be number 4. Four is all the primary partitions you can have so it works just fine.

---

### Post by M!K3_$ on 2006-10-24
what is the filesystem suposed to be ext3?

---

### Post by TiredBird on 2006-10-24
I'm going to keep rattling off directions. I'm not going to provide as much explanation as I did before. It seems you're pretty knowledgeable. If I don't provide enough detail on something, let me know and I'll expand.

---

### Post by TiredBird on 2006-10-24
yes, make the 50mb partition ext3.

---

### Post by M!K3_$ on 2006-10-24
ok

---

### Post by M!K3_$ on 2006-10-24
should i remount the linux swap, and how would i do that:S
if i need to

---

### Post by TiredBird on 2006-10-24
In the live cd, add two directories to the /mnt directory - 'hdc2' and 'hdc4'. You'll have to use 'sudo' to create them. Then issue the following mount commands: ```
[COLOR="DarkGreen"]sudo mount -t ext3 /dev/hdc2 /mnt/hdc2
sudo mount -t ext3 /dev/hdc4 /mnt/hdc4[/COLOR]
``` which should mount your old partition and the new boot partition. Then copy the boot stuff: ```
[COLOR="DarkGreen"]sudo cp /mnt/hdc2/boot /mnt/hdc4/[/COLOR]
``` which should duplicate the boot stuff on partition 4. Check and make sure it worked okay. Then remove everything in the /mnt/hdc4/boot folder except the 'grub' folder. Have you got this so far?

---

### Post by TiredBird on 2006-10-24
Since you're not really running linux on partition 2 there is no need to remount the swap partition. If we ever get your linux to boot it will mount the swap partition.

---

### Post by M!K3_$ on 2006-10-24
it says it doesnt exist so im gunna try to reboot 
i did partition it though

---

### Post by TiredBird on 2006-10-24
Can you operate in the live CD and still maintain contact?

---

### Post by TiredBird on 2006-10-24
If you have to run 'sudo fisk -l' from a command line to see what you have. 'mount' from the command line shows what is mounted and where.

---

### Post by TiredBird on 2006-10-24
Are you able to get the two partitions mounted?

---

### Post by M!K3_$ on 2006-10-24
ya i am in the live CD, i just had to reboot to get it to reconize the new partition i guess

---

### Post by M!K3_$ on 2006-10-24
o no, whats this now

root@ubuntu:~# mount -t ext3 /dev/hdc2 /mnt/hdc2
mount: mount point /mnt/hdc2 does not exist
root@ubuntu:~# sudo mount -t ext3 /dev/hdc2 /mnt/hdc2
mount: mount point /mnt/hdc2 does not exist
root@ubuntu:~#


wont mount

---

### Post by M!K3_$ on 2006-10-24
o wait, i know y
nvm
ill try again

---

### Post by M!K3_$ on 2006-10-24
not good.
this one i dont know how to fix

root@ubuntu:/mnt/hdc4# cp /mnt/hdc2/boot /mnt/hdc4/
cp: omitting directory `/mnt/hdc2/boot'
root@ubuntu:/mnt/hdc4# ls
lost+found
root@ubuntu:/mnt/hdc4#

thats when i try to coppy it

---

### Post by TiredBird on 2006-10-24
I'm sorry, I think I screwed that one up. I don't usually use 'cp', I usually use 'rsync' but I wasn't sure you had that one. The 'cp' command probably needed a -R as an option. If you have 'rsync' though use it. The command would be: 'sudo rsync -av /mnt/hdc2/boot /mnt/hdc4/' (I think).

---

### Post by M!K3_$ on 2006-10-24
live CD so i dont think ther is rsync 
ill try copy -R

---

### Post by M!K3_$ on 2006-10-24
worked, so now i just get rid of everything but grub right

---

### Post by TiredBird on 2006-10-24
Anyway, what you're trying to do is to get the entire contents of the 'grub' directory over to partition 4. It should be in the 'grub' folder there which should be the only thing in the 'boot' folder there which should be the only thing in that partition. Does that make sense? and can you do that? or do you need more directions?

---

### Post by M!K3_$ on 2006-10-24
root@ubuntu:/mnt/hdc4# ls
boot  lost+found
root@ubuntu:/mnt/hdc4# cd boot
root@ubuntu:/mnt/hdc4/boot# ls
System.map-2.6.15-23-386  config-2.6.15-23-386      initrd.img-2.6.15-27-386
System.map-2.6.15-26-386  config-2.6.15-26-386      memtest86+.bin
System.map-2.6.15-27-386  config-2.6.15-27-386      vmlinuz-2.6.15-23-386
abi-2.6.15-23-386         grub                      vmlinuz-2.6.15-26-386
abi-2.6.15-26-386         initrd.img-2.6.15-23-386  vmlinuz-2.6.15-27-386
abi-2.6.15-27-386         initrd.img-2.6.15-26-386
root@ubuntu:/mnt/hdc4/boot#


allrigt should i jsut keep the grub in ther then

---

### Post by TiredBird on 2006-10-24
Let me put it another way. The new partition should have only one folder in it, 'boot'. 'boot' should have nothing in it but the 'grub' folder. And the 'grub' folder should have the same stuff in it that it had on partition 2, there should be a menu.lst, stage1, stage2, several versions of stage1_5 for different types of operating systems, maybe a map file and probably not much else. Tell me is you see something that looks out of place.

---

### Post by TiredBird on 2006-10-24
Yes, all that stuff in the 'boot' folder goes except for the 'grub' folder.

---

### Post by M!K3_$ on 2006-10-24
got it
jsut workin on gettin rid of it

---

### Post by M!K3_$ on 2006-10-24
allrighty then,
now what

---

### Post by TiredBird on 2006-10-24
do that drill down again with cd ing to each successive level and let me see what you got in there.

---

### Post by M!K3_$ on 2006-10-24
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# cd /mnt/hdc4/
root@ubuntu:/mnt/hdc4# ls
boot
root@ubuntu:/mnt/hdc4# cd boot
root@ubuntu:/mnt/hdc4/boot# ls
grub
root@ubuntu:/mnt/hdc4/boot# cd grub
root@ubuntu:/mnt/hdc4/boot/grub# ls
default        fat_stage1_5  menu.lst.back   reiserfs_stage1_5  stage2
device.map     jfs_stage1_5  menu.lst~       splashimages       xfs_stage1_5
e2fs_stage1_5  menu.lst      minix_stage1_5  stage1
root@ubuntu:/mnt/hdc4/boot/grub#


thats it

---

### Post by TiredBird on 2006-10-24
Okay, sorry to ask you to do that but I still can't see why what we did before didn't work so I want to look at everything. Humor me please. Can I look at a copy of menu.lst from that partition. Bring it up in an editor because we're going to need to make some changes. Post all of it though so I can see what we need to do.

---

### Post by M!K3_$ on 2006-10-24
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hdc3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by M!K3_$ on 2006-10-24
the happy faces arnt mine the forum put them in
i think they are 8 )   without the space

---

### Post by M!K3_$ on 2006-10-24
i dont know y windows doesnt show up, but its there in grub (nvm found it)


and the first ubuntu (2.6.15-27-386) on the list is the current kernel

---

### Post by M!K3_$ on 2006-10-24
could i get rid of teh old kernals by just erasing them from ther (they dont work either)

---

### Post by TiredBird on 2006-10-24
Sorry to be taking so long. I copied the boot menu into my own editor and I'm looking at it.

---

### Post by TiredBird on 2006-10-24
We'll definitely take the unneeded kernels out of the boot menu but as to just deleting them, I don't think I would do that. Use Synaptic or something like that to delete them. I'm not sure that is necessary but it's what I do just to be on the safe side.

In any event, I wouldn't take anything out now. Wait till we get things working.

---

### Post by M!K3_$ on 2006-10-24
ok, its not like i can use synaptic right now anyway so ill take one problem at a time :) haha

---

### Post by TiredBird on 2006-10-24
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hdc2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.15-27-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hdc2 ro quiet splash
initrd /boot/initrd.img-2.6.15-27-386
savedefault
boot

title Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hdc2 ro single
initrd /boot/initrd.img-2.6.15-27-386
boot

title Ubuntu, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by TiredBird on 2006-10-24
Here's the boot menu back. I made a couple of minor changes. There were two lines in the comments beginning with #, not ##, that needed changing. They couldn't be causing this problem but they would have caused you a problem when you upgraded your kernel at some time in the future. I also took out all the references to old kernels. Your windows menu item is in there, it is the last one. It goes after the automagic stuff because it doesn't change when the kernels change. Anyway, put this back into your editor and save it as '/mnt/hdc4/boot/grub/menu.lst'. It doesn't matter that the one in partition 2 is wrong because you won't be using it anymore.

---

### Post by M!K3_$ on 2006-10-24
allrighty den.
now what
the grub thing?

---

### Post by TiredBird on 2006-10-24
The lines I changed are ones beginning '# kopt=...' and '# groot=...'. They are used as guidelines by the updater when you install a new kernel. They have to reflect the proper partitions or your bootloader will not work.

Doesn't matter much any more now because you'll never be changing a kernel on the same partition as the boot menu so there won't be any changes. I'll show you later how to keep from having to change the boot menu manually.

---

### Post by TiredBird on 2006-10-24
Okay, lets see if we can install a boot loader that works. 

Still in the live cd, command line, do a sudo grub and get it running.

Then do a 'find /boot/grub/stage1'. It should show (hd0,1) and (hd0,3), the latter being the one we just installed. If it doesn't have that one listed STOP!

Assuming it is liste, enter 'root (hd0,3)'.

Then enter: 'setup (hd0)'.

If you get all the nice messages like you got last time, that should mean that you have a bootloader in the master boot record that will boot the menu on partition 4. 

Reboot, and see if you get a menu. Move the arrow key after it comes up to keep it from going away.

Can you still communicate with me while you're doing that?

---

### Post by M!K3_$ on 2006-10-24
nope
just one puter

ill right it down if u want to tell me now

the grub setup workd

---

### Post by TiredBird on 2006-10-24
Don't need to write it down. I just hope you at least get a menu. If you do then you can continue to the Ubuntu partition to see if that works. If something doesn't work, try to get as much information as possible, then reboot with the live cd and get back to me. We'll do some other experiments to see what is causing the problem.

---

### Post by M!K3_$ on 2006-10-24
allright
hey i gtg to school tomorw and its 11;00 here so if this doesnt work i just wont log on again and mabye we can try again tomorw

if it does all be stoked and ill tell u

allright
thankx

---

### Post by M!K3_$ on 2006-10-24
nope, no go
i got the menu.
and now its a lot cleaner, on the current kernal, memtest, and XP

but still the same problem w/ stalling out.

mabye tomorw

thankx warren

---

### Post by TiredBird on 2006-10-24
you at least got to the menu and could see that we had made changes to it. It means that part of it is working. That at least tells us where to look. we'll look some more tomorrow.

---

### Post by TiredBird on 2006-10-24
Mike,

I am at a loss. Please humor me while I review a few things. 

Boot with the live cd. Mount your hdc2 partition at /mnt/hdc2: ```
[COLOR="DarkGreen"]sudo mkdir /mnt/hdc2
sudo mount -t ext3 /dev/hdc2 /mnt/hdc2[/COLOR]
``` Then bring up fstab in an editor: ```
[COLOR="DarkGreen"]gksudo gedit /mnt/hdc2/etc/fstab[/COLOR]
``` and post the entire file. I need to look at it.

NOTE: If any of my partition names and/or file names are incorrect, please tell me. If they have changed for some reason that could be part of the problem.

---

### Post by ~LoKe on 2006-10-24
In your /boot/grub/menu.lst file, remove "quiet slash" from the first kernel line and then try to boot into it.  Your splash will be gone and you'll see a lot of text.  The text should be pretty clear.

---

### Post by TiredBird on 2006-10-24
~Loke,

If you note from some of his posts, he's wiped out the splash screen. I think he has done something to 'X' and he's going to have to get help from someone else on that. I'm going to look at fstab, make sure its okay, then have have him try a single-user boot and see if he can at least get a command line prompt. Unless its in the fstab its beyond anything I can help with.

I think originally it might have been just partition numbers that had gotten changed but now I'm afraid there really is something big-time broken in his system.

---

### Post by M!K3_$ on 2006-10-24
thankx for all your guy's help but i really need to use my computer now.
so i will back up my home folder and start over again

thank you ~Loke and TiredBird

i wish you all the best of luck
and mabye u can solve my problems again somtime:-D

---

### Post by TiredBird on 2006-10-25
Sorry we didn't get the problem solved. Good Luck!

---

