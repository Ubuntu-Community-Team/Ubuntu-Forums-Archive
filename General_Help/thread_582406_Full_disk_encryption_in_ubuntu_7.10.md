---
title: "Full disk encryption in ubuntu 7.10"
date: 2007-10-19
forum: General Help
---

### Post by kingleer on 2007-10-19
I've downloaded the ubuntu 7.10 text installer cd, and know that you can use the text installer to encrypt your ubuntu install itself. However, I have a truecrypt partition on my HDD that I want to keep. Can anyone walk me through how to manually encrypt my ubuntu install as opposed to  just using the whole disk to install an encrypted ubuntu? 

Thanks in advance.

---

### Post by mahousaru on 2007-10-22
Have you solved this yet?  If not I can post my steps.

---

### Post by kingleer on 2007-10-22
No, I have not been able to find a solution to this problem. 

Please, post your steps. :)

---

### Post by mahousaru on 2007-10-22
My set-up is a bit convoluted.  I have 5 partitions

/boot
/
/home
{extended}
swap
truecrypt

Before I start where is your TC partition?  How is your disk currently partitioned?  You will need at least 

/boot - unencrypted
/ - encrypted
swap - encrypted
tc - left well alone by the Ubuntu install process but please make sure you copy your data off first!

*EDIT*

I'm about to crash, so I thought I'd give you some things to think about

If you separate out your home, that means its a lot easier if you wish to blat your root to re-install. But this means you need to enter your encryption password in 3 times.  Once for root, then swap and then home.  I got around this by having a key saved on / and once that is decrypted they key is used to decrypt the other 2.  Problem with this is if someone steals my key they have access to my home and my swap.  

Now I can bypass using a key for the swap file by not initialising swap on boot.  But instead use a script to create the encrypted partition on startup using the random device as the key generator and then mkswap/swapon.  This means that the swap is truly random and is basically all access to its data is lost when you restart the pc.

For home, you either don't have one and home exists under root, or you manually type in your password each time for it.

So apart from listing out your current partition state, you need to decide on how you wish to create your new one.

---

### Post by mahousaru on 2007-10-22
@Mods - Sorry for the double post, but I wanted separate the guide from the blurb up the top.

@kingleer - I knocked up a quick guide based on an encrypted root and swap partition.  If you want to go for this partition set-up, but want to  change how the swap is mounted, that can be done at a later date.

Here goes!

Boot up from ALT disk
Select options until you reach Partition Disk. 
Select Manual.

Now here is where you have to be careful as you need to have at least 

/boot
/
swap
TC

Boot needs to come first but the rest can be in any order.  I believe that Ubuntu does not affect a partition unless it is told to do something to it.  But I can't stress how important it is to back up the TrueCrypt data before starting.

So either edit existing partitions, or create the following:

/boot &#8211; 200MB

For the encrypted partitions you need to in Partition Settings select  &#8220;Use as: Physical Volume for Encryption&#8221;.  Leave the rest of the settings as default.

[IMG]http://mahousaru.googlepages.com/encrypt1.png[/IMG]

/ -  Physical Volume for Encryption
swap - Physical Volume for Encryption
TrueCrypt &#8211; Make sure that the installer isn't going to mount this .

You can see in the below piccie that the TC part is not mounted and the two encrypted vols are not active.

[IMG]http://mahousaru.googlepages.com/encrypt2.png[/IMG]

Select &#8220;Configure encrypted volumes&#8221; from the top. It will give you a warning about writing to the partition table which you need to say Yes to.

It will then ask you to enter in a password for both your partitions.  You can later ditch the swap one if you wish to, but for now enter in your passwords that are strong and u can remember.

Then edit each encrypted partition by highlighting it and pressing enter.  Lets do the root first...

[IMG]http://mahousaru.googlepages.com/encrypt3.png[/IMG]

Select the mount point as /
Change the FS type if you so wish (I kept ext3 myself)
Now you must select &#8220;Erase Data&#8221;, this writes random data to the new partition. Go make a coffee as this will take a while.

Do the same for the swap partition, but with the swap you don't select a mount point.  You select Use as swap.  Again make sure you select Erase Data.

It now should look like

[IMG]http://mahousaru.googlepages.com/encrypt4.png[/IMG]

It didn't set my /boot partition as /boot, but if that happens to u, just press enter on the boot partition and edit it.

Finish partitioning

It will ask to mount your TC partition, make sure you say no.  Then in the summary make sure it is going to do nothing to your TC partition.

It will ask a few more questions and should now start installing.

You now have a fully encrypted drive, but you will need to enter your passwords in twice.  Once for the root partition and once for swap.

How bleeping easy have the Ubuntu guys made it!  I'm so very impressed with 7.10 :)

---

### Post by kingleer on 2007-10-22
Thanks. Worked like a charm. That was a lot easier than I thought it would be. 

I don't know anything about linux, but I've been using Ubuntu as my main OS ever since 6.04. I'm amazed how far Ubuntu has come myself. Using it is now easier than using Windows Xp. The add/remove programs feature lets me install programs without searching the web for them. Definitely the  best idea I've seen in a long time.  

As is, Ubuntu is ready for prime time if it comes installed on a computer. 

The ubuntu team now just needs to do stuff like make setting up your wireless card easier. I know how to use ndiswrapper to set up my wireless card, but someone using Ubuntu for the first time might be intimidated by it. 

I see Ubuntu doing to windows what firefox did to internet explorer.

---

### Post by mahousaru on 2007-10-22
Yah me gob smacked myself.  I'm from a Red Hat/SuSE background and I only tried out Ubuntu 7.04 as I was going for a job in it and I loved it.  Once 7.10 came out I dropped OpenSuSE from all my personal machines and I am full Ubuntu now.  

The full disk encryption really did it for me.  I only use it on my lappy (and the eeepc when I buy one), but I just don't get why more distro's are not working on it for mobile devices.  It is such a huge issue with lost data and all.  What gets me is how people automatically think you are a criminal if you wish to encrypt.

dm-crypt and luks is great for enterprise stuff as it supports multiple passwords so there is a little bit of leeway when dealing with user forgetfulness.  BTW in case you didn't know you can do the same with TC.  You have the known to you password on it, you backup the header using the TC tools and then you get the user to set a new password.  If they forget their password, you slap on the old header!

---

### Post by High Roller on 2007-10-22
> **mahousaru said:**
> You now have a fully encrypted drive, but you will need to enter your passwords in twice.  Once for the root partition and once for swap.

You could setup LVM under the encrypted partition for both root and swap to avoid two passwords.  It also allows you to resize your partitions that are within the encrypted space later.  Here's a good How-To:  [http://www.iki.fi/kuparine/comp/ubuntu/en/cryptolvm.html](http://www.iki.fi/kuparine/comp/ubuntu/en/cryptolvm.html)

---

### Post by mahousaru on 2007-10-23
> **High Roller said:**
> You could setup LVM under the encrypted partition for both root and swap to avoid two passwords.  It also allows you to resize your partitions that are within the encrypted space later.  Here's a good How-To:  [http://www.iki.fi/kuparine/comp/ubuntu/en/cryptolvm.html](http://www.iki.fi/kuparine/comp/ubuntu/en/cryptolvm.html)

OOoo nice link, also since the set-up is manual that means the OP could have avoided messing up the TC partition.  I think I'll give LVM full disk encryption a go next :)

Thanks for the heads up

---

### Post by scotthammy on 2007-10-23
[COLOR="DarkGreen"]**Hey Everyone** - First off Really loving Gutsy 7.10 Happy I have moved from my XP system. (still have it, but will remove xp after 6 months no use)

[COLOR="DarkSlateGray"]Now Q. [/COLOR]

Laptop is a Asus A6km Built in SD slot. 
Im hoping to use this SD slot and a small 16M sd card like a master security key for full drive encryption, So if the cards pluged in, we are all go, if i leave the pc for work, I take the "key" with me.

I know if anyone got the key the drive encryption is pointless but, its better nothing, And also very kool to have a digital key for my laptop.

Hope someone can help.

Cheers
Scott, NZ.

[/COLOR]

---

### Post by High Roller on 2007-10-25
> **scotthammy said:**
> [COLOR="DarkGreen"]**Hey Everyone** - First off Really loving Gutsy 7.10 Happy I have moved from my XP system. (still have it, but will remove xp after 6 months no use)

[COLOR="DarkSlateGray"]Now Q. [/COLOR]

Laptop is a Asus A6km Built in SD slot. 
Im hoping to use this SD slot and a small 16M sd card like a master security key for full drive encryption, So if the cards pluged in, we are all go, if i leave the pc for work, I take the "key" with me.

I know if anyone got the key the drive encryption is pointless but, its better nothing, And also very kool to have a digital key for my laptop.

Hope someone can help.

Cheers
Scott, NZ.

[/COLOR]

When doing a manual install+partition encryption, you could "try" and put /boot onto the SD card (I don't think you could pack all that into 16mb....  try 256mb to be safe).  Also, take a look to see if your bios supports USB booting and if the SD slot falls under USB hardware.  Maybe you could move grub and everything onto the SD and have no plain text on the drive altogether (with exception to the LUKS headers).  Experimenting is fun.  There's probably other ways to manually move /boot to the SD but you'll likely leave a gap in your partitions.  This is something I've wanted to test as well but have lacked the motivation to get off my *** and buy a small USB flash drive.  :)

Can someone with a deeper knowledge of how cryptsetup works tell me if this would all be possible? I know that the key is stored within the LUKS header of the partition.  But would it not be useless without a password?

It would also seem that the strength of security would be based on the password chosen.  Meaning that since the LUKS partitions have headers they could easily be accessed and compromised to a dictionary attack.   In my mind it would seem that the password is where the strength must be maintained.  By moving your /boot and grub to an SD card you're eliminating a possible attack via keylogger in your /boot (a point of weakness) but if your password is weak then it doesn't matter anyways.  That's why I've always said a password should never be a "word".  It should be a passphrase, meaning a big long sentence with unique characters such as symbols etc.

Do you have a Windows partition you need to preserve bootable accessibility to?  (without your SD)

---

### Post by mahousaru on 2007-10-25
Hmmm well when it comes to the boot process the crypttab is used by

 sudo update-initramfs -u

to build a boot image that asks you for the password etc.  That's why if you have a separate swap that is encrypted using a password and later just set in there to decrypt using a key it will still ask you for a password.

I'll knock up a test box and see if I can get it to automatically use a key from another drive to mount the root partition.

---

### Post by High Roller on 2007-10-25
Does anyone know how to change the passphrase of an encrypted partition?  I gather this would be a command line function somehow.  I wish there was a GUI "key manager" available.  But hey, we've come a long way in just having encryption at all.

I'm taking a look at "[luks-tools]("http://www.flyn.org/projects/luks-tools/index.html")" to see if it's the answer to this.

**edit:  looks like luks-tools isn't being actively developed anymore.  booooo!  :)  <jk>

---

### Post by mahousaru on 2007-10-25
Every thing is with cryptsetup, and you can up to 5 keys (I think... might be more).  So just add another key and delete the old one.  e.g. 

```

sudo cryptsetup luksAddKey /dev/hda2

```

This will ask you for a password and add it in addtion to existing ones

do this to check what is already there

```

sudo cryptsetup -v luksDump /dev/hda2

```

Actually do this first to see what key slots are populated! And then do after you have added a key

And to delete the old key (replace # with the number of the key slot)

```

sudo cryptsetup luksDelKey /dev/hda2 #

```

To be even more funky and use a key file you can do something like...

```


dd if=/dev/random of=keyfile bs=1 count=256

sudo cryptsetup luksAddKey /dev/hda2 keyfile


```

Remember all this adds additional keys, its up to u to delete the **right** one!

*EDIT*
**You should always try logging in with a new key before deleting the old one!**

---

### Post by High Roller on 2007-10-25
> **mahousaru said:**
> Every thing is with cryptsetup, and you can up to 5 keys (I think... might be more).  So just add another key and delete the old one.  e.g. 

```

sudo cryptsetup luksAddKey /dev/hda2

```

This will ask you for a password and add it in addtion to existing ones

do this to check what is already there

```

sudo cryptsetup -v luksDump /dev/hda2

```

Actually do this first to see what key slots are populated! And then do after you have added a key

And to delete the old key (replace # with the number of the key slot)

```

sudo cryptsetup luksDelKey /dev/hda2 #

```

To be even more funky and use a key file you can do something like...

```


dd if=/dev/random of=keyfile bs=1 count=256

sudo cryptsetup luksAddKey /dev/hda2 keyfile


```

Remember all this adds additional keys, its up to u to delete the **right** one!

Thanks mahousaru!

Seems to work perfectly.

---

### Post by mahousaru on 2007-10-25
> **scotthammy said:**
> [COLOR="DarkGreen"]
Laptop is a Asus A6km Built in SD slot. 
Im hoping to use this SD slot and a small 16M sd card like a master security key for full drive encryption, So if the cards pluged in, we are all go, if i leave the pc for work, I take the "key" with me.
[/COLOR]

The first thing is you can't easily edit the /etc/crypttab and tell it to use a keyfile and then rebuild a new initrd file using the built in tool update-initramfs as it will ignore any partitions that uses keys and not build them in.  

Secondly do you know if you SD slot is recognised by the kernel on boot?  For example USB hard drives were not recognised in 7.04 so a few extra steps had to be taken to get the usb modules to be loaded on boot.  The same thing would be required here, but the harder part is the modules will need to be available before the root partition has been decrypted, basically they will need to be included in the initrd drive.

Basically it looks like you will have to create your own initrd file manually.  

*scratches head* 

I haven't been there since I had to hack the zenworks boot cd to get imaging to work, my mind has blanked the whole experience as a self defence mechanism :p

---

### Post by honeydew on 2007-10-25
hey.. I am also looking for a solution along these lines.. I am using a Smart card reader in my laptop so the user still has to enter a key but with out the card the hard drive cant be booted.  I have found information on the subject here 
[http://www.saout.de/tikiwiki/tiki-index.php?page=RSAFirstSectorsMiniHOWTO](http://www.saout.de/tikiwiki/tiki-index.php?page=RSAFirstSectorsMiniHOWTO)
.. I wouldnt mind working with you on a solution.. and then we can document it for everyone else.  That howto uses the same software but dosnt really fit into the ubuntu scheme of things, I am sure we can figure something out if we get hacking.

-------------
okay umm.. I found a bit more.. but I am wondering is there a way for me to load OpenCT and OpenSC(modules or software?) during/before the root partition is loaded?  I think I have enough howtos to actually piece this together..

-------------
I am also questioning whether a SD card is 'more' secure than having the /boot partition(and key) stored on a USB drive..  With a SD card you must enter a series of numbers(no more than 8 dgits long I believe).. with a USB key you can enter a key as long as you would like..  hrmm never mind.. scratch this thought.. I have just been informed that the smartcard kills itself after 4 tries.

---

### Post by Difranco1911 on 2007-10-25
I just learned of this feature of full disk encryption...  However I can't find a download for the Text intaller version of Gutsy Gibbon... can someone point me to it?

---

### Post by honeydew on 2007-10-26
there is a radiobox under "start download"(big green arrow)  that you can check in order to get the alternative cd..

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Difranco1911 on 2007-10-26
HA HA  found it just a few minutes ago... was coming to post a "nevermind".

---

### Post by mahousaru on 2007-10-26
@honeydew - This does seem like an interesting project, but I can't really invest that much time in it for the next week or two.

If you want to potter around u can have a look at the initrd file by:

```

cd /tmp
cp /boot/initrd.img-2.6.22-14-generic initrd.gz
gunzip initrd.gz
mkdir initrd.new
cd initrd.new
cpio -i <../initrd

```

The initrd file is an archive so unable to mount it via loopback thats why the use of the cpio command.

Just in case you were wondering initrd is the initial root file structure that is mounted before the real one is.  So in the case of encryption u really need to make sure that anything you wish to access is loaded here.  The dm-crypt and luks modules are already loaded as of 7.10 *cheer*, but the problem is any other storage.  The first thing to do is to check to see what modules your external storage needs and does the default initrd load them.

I'll probably potter around with this in my spare time, but I don't have anyway to emulate a sd reader with my vmware :(

---

### Post by QCompson on 2007-10-26
I have a quick question.

I have windows installed on one drive.  I am planning on installing a fully encrypted gutsy install on a 2nd separate drive.  I have used debian's encrypted lvm installer before, so I don't anticipate any problems on that front.  

My question: Will I have any issue with the installer identifying my windows install and plopping it into grub for a dual-boot?  I assume it will be fine, but better safe than sorry!

Thanks in advance!

---

### Post by gizmobay on 2007-10-26
I installed xubuntu 7.10 with full disk encryption by using the guided method. I thought I read on another post that encryption occurs on the first boot and it takes awhile. Mine booted up normally on the first boot. When I did the install, it took awhile to format the partition about 45 minutes on a 20G hard drive. When I boot, it always asks me for a crypt password but how can I tell if the hard drive is actually encrypted?

Thanks

---

### Post by honeydew on 2007-10-26
mm.. try and mount/read it with out the key?...

---

### Post by honeydew on 2007-10-26
I am on order for a few more smart cards, till then I dont have a extra one to load keys on.  However this is one of my slated projects so hopefully Ill get it figured out in the next few weeks...

---

### Post by antiplex on 2007-10-28
> **mahousaru said:**
> ...
Now I can bypass using a key for the swap file by not initialising swap on boot.  But instead use a script to create the encrypted partition on startup using the random device as the key generator and then mkswap/swapon.  This means that the swap is truly random and is basically all access to its data is lost when you restart the pc.


dear mahousaru,

i pretty much like the idea about initialising the swap partition by script to get around typeing in the pw for it. 
can you please give some more details about how this is done?
i guess instead of creating a swap-partition during partitioning i'd have to create a filesystem-less partition in the size the randomly encrypted swap-partition will be maybe?
but where to put the script? i don't know at which stage of the booting process the system may need to have its swap partition and further i'm not a good scripter, so your help would be greatly appreciated!

regards, anti

---

### Post by mahousaru on 2007-10-28
I didn't do it this way around with my Ubuntu install as I was playing around with using keys to automate the login for my home and swap.  But with openSuSE I had in rc.local

cryptsetup -d /dev/random create swap /dev/partition
mkswap /dev/mapper/swap
swapon /dev/mapper/swap

Oh you have to make sure u rem out the swap lines in crypttab and in fstab and update the initrd file using 

```

sudo update-initramfs

```

---

### Post by nutz on 2007-11-07
This feature really should have been publicized more. I have been looking for something like this for some time now. If only I had known it was already included on the alternate CD.

Is it too late to implement this after Ubuntu is already installed? If it isn't then how difficult would it be? Is there en existing howto for gutsy?

---

### Post by kwlskwlguy on 2007-11-08
> **mahousaru said:**
> Every thing is with cryptsetup, and you can up to 5 keys (I think... might be more).  So just add another key and delete the old one.  e.g. 

```

sudo cryptsetup luksAddKey /dev/hda2

```

This will ask you for a password and add it in addtion to existing ones

do this to check what is already there

```

sudo cryptsetup -v luksDump /dev/hda2

```

Actually do this first to see what key slots are populated! And then do after you have added a key

And to delete the old key (replace # with the number of the key slot)

```

sudo cryptsetup luksDelKey /dev/hda2 #

```

To be even more funky and use a key file you can do something like...

```


dd if=/dev/random of=keyfile bs=1 count=256

sudo cryptsetup luksAddKey /dev/hda2 keyfile


```

Remember all this adds additional keys, its up to u to delete the **right** one!

The keys are successfully added/removed via this method; however, upon rebooting these new keys cannot be used to actually authenticate you for decryption.

I've used the Guided, full disk encryption using LVM, by way of the alternate install cd.
Did I miss something?  Apologies ahead of time if I did.

---

### Post by mahousaru on 2007-11-08
> **kwlskwlguy said:**
> The keys are successfully added/removed via this method; however, upon rebooting these new keys cannot be used to actually authenticate you for decryption.

I've used the Guided, full disk encryption using LVM, by way of the alternate install cd.
Did I miss something?  Apologies ahead of time if I did.

Can u login with your old key?

---

### Post by kwlskwlguy on 2007-11-08
I guess I neglected to say that this was a test environment in VMware and that I took a snapshot Just prior to making the attempt.

The original key will work but newly added ones do not.  If the orig. key is removed, access is lost entirely.  Also tried to add key 1, remove key 0, add new key 0, to see if the key slot was any factor.  It is not, I seem to remember something to the effect that, the initial key used is also used to do the encrypting, not just for access to the encrypted partition.  It would seem, at least on the surface, that this may have some credence.  I haven't read up on the documentation of the LUKS/dm-crypt/Ubuntu configuration enough to verify though.

I too am attempting to find a way to access my encrypted root partition via key stored on usb device, and will post here any pertinent info.

---

### Post by kwlskwlguy on 2007-11-12
Yeah, just verified the thing about the key being tied to the encryption of the data.


[http://www.saout.de/misc/dm-crypt/]("http://www.saout.de/misc/dm-crypt/")
> What if I want to change my passphrase?
At the moment you'll need to reencrypt your device because the passphrase is directly tied to the key. 

---

### Post by antiplex on 2007-11-20
> **mahousaru said:**
> ...  But with openSuSE I had in rc.local ...

Oh you have to make sure u rem out the swap lines in crypttab and in fstab and update the initrd file using ```
sudo update-initramfs
```

dear mahousaru,

thank you very much for your hints! i havent had time yet to try it but as i just wanted to do that now i wondered which rc.local you refer to.
there is a /etc/rc.local and /etc/init.d/rc.local ; as far as i know scripts in /etc/init.d/rc.local get executed in early userspace while /etc/rc.local is executed after the filesystems are mounted etc, right?

so we would want to create swap during the early stage of booting i guess so /etc/init.d/rc.local would be the right place i guess?

with this thought the update-initramfs command also makes sense but i'm not sure if this might be because of what i just mentioned or maybe because fstab and crypttab are also included in the initrd? :confused:

could anybody maybe please help me to better understand all this? just dont want to mess up things...

thanks!

---

### Post by mahousaru on 2007-11-21
I would very much recommend you do this on a box you don't mind trashing.  A vitural machine is ideal for doing this, and one that can snapshot (ie vmware server) is even better as it saves you waiting to re-install incase you really mess it up.

When I was using a init script to create and load my swap that was on another OS, on Ubuntu I autoloaded with a key on my root partition, but now I'm using a lvm encrypted with a single password (which was suggested earlier in the forum by someone).

*Edit* - Removed stuff you already seem to know :)

You should be able to add the script in /etc/init.d/rc.local, unless your system is really sparse on ram then it shouldn't start swapping so early, so you should be able to activate your swap late.  What is your ram?

---

### Post by antiplex on 2007-11-21
i also considered using a lvm for the same reasons (only 1 key needed) but what kept me away from doing so in the end was the fact that i could not find a safe solution on how to backup my system partition and in case something bad happens be able to easily restore everything with a lvm.
with single partitions i could at least dd the encrypted system partition (useing a livedisk e.g. clonezilla etc)... also not too convenient and efficientbut at least a way do have some sort of backup...

anyway, i somehow assumed that swap couldn't be added to a running system but i again underestimated the great flexibility of linux/debian based systems.
and you were also right that rc.local is not executed in the very early runlevel (0) as it seems but gets called later (5 for instance).
ram is not the problem on my machine, i've got 2gb installed and this is enough for most of my purposes. what i wanted to have a swap for is to at least try if it is possible to use standby/suspend-to-disk.

anybody tried that?

anyway, thanks again for your hints, mahousaru!

regards, anti

---

### Post by mahousaru on 2007-11-21
@anti - nps glad I could give some input

Backing up data is always going to be an issue with encrypted partitions.  At first I was in the same mind as you were since I was concerned about recovering data from something bad happening.  Since I always backup my laptop as soon as I get back home I realised that recovering data isn't going to be that much of an issue as I always have at least one copy of the data at home or at work.  

I tend to keep all of my sensitive data on an encrypted partition of some form, but as soon as I do I back up to another encrypted data store.  For example my home PC is a tiny Acer L310, if someone broke into my flat they could walk out with it in their bag with no problems.  So even though that box never leaves the house it still is still encrypted.  The thought of some nasty person getting their hands on my personal details like bank statements etc makes me shudder.

Of course some people would bring up the if you haven't done anything wrong then no need to hide it, but I think the above statement covers that.  Also to protect my family I tend to keep a set decryption keys off site.  That way lets say I got run over by a bus and for some reason the police raided my home.  If they demand the encryption keys for my kit, my family they won't get into any trouble.

I've got 2 gb in my desktop too and I disabled it when I was testing the speed of a swap file and I forgot to re-enable it.  I had my box on for nearly a month before I realised that it had no swap.  I do a lot of image editing with gimp and had no troubles at all :)

I'll be looking seriously at this again at the end of the month when the eeepc 8G comes out, you've guess it, I'll have ubuntu (or xubuntu) full drive encryption with TC sd card as soon as I get my paws on it :p

I did test hibernation/suspend with encrypted partitions once.  It failed miserably with the suspend to disk, but the suspend to memory worked (just my wireless card refused to wake up).  I'll test suspend/hibernation again when I get the chance.  I better get back to work now before I get my bottom smacked :p

---

### Post by antiplex on 2007-11-24
@mahousaru: i understand why/how your backup concept works and i guess in your case this is just what you may need but for me there is an additional reason: 
i depend on a certain reliability of my system and according to fitts law, a system may break down (no matter through what, malware, physical/electronical defect etc) in the very situation you need it most (like 1 day before you have to deliver some project).
so in this case i could go to the next store and get some new hardware and simply write back my backup instead of setting up my whole system from scratch (installing, configuring to my personal needs etc etc) which would take about 2 days until everything is like i had it before i guess. but well, guess everybody has its own strategy about this, _most important is that there is at least some sort of backup_.
edit: i quite like the concept of the asus eeepc and might also consider one of these as my next laptop, but i couldn'T find out for sure if it is true that the 8g-model will come with a 10" screen and what resolution it will have. i guess the 10" display would be ok for me but the 7" is definitly too small and also a bit of a waste of space i think. do you have any further infos about that? what also sounds quite interesting is the desktop version (basically the same specs, just without a display and external keyboard and equipped with the brand new intel merom cpus) asus announced. they should hit markets around spring 08 but i fear this will easily turn into summer... we'll see. 

anyways, today i successfully tried to manually setup my swap and found out the following:
[LIST][*][INDENT] if one had chosen to explicitly define no swap-partition then there is nothing to change in /etc/crypttab and /etc/fstab (but maybe still a good idea to double check!) .
in this case it is also _not_ necessary to update the initrd via 'sudo update-initramfs'.[/INDENT]
[*][INDENT] i got a little confused about runlevels and the execution of rc.local so i looked everything up: /etc/init.d/rc.local simply calls /etc/rc.local , so /etc/rc.local is where you would add the code that does whatever you want (in this case setup a swap area.
unless the system has _very little_ memory installed, it is perfectly fine to _not_ initialize the swap area at any earlier stage of booting. (as said before, rc.local gets executed at a late stage of booting at a certain runlevel (which is 2 for default desktop installations (check by typing the command 'runlevel' into a terminal.).))[/INDENT]
[*][INDENT] one should be very careful when using 'cryptsetup create <name> <device>' since in case one adds an additional harddisk to his/her system the device names could easily change and what for instance has been /dev/hd_a_2 before could now be /dev/hd_b_2 , so at /dev/hda2 could now be an unmounted partition of the disk one has just added to the system, right?
so now the script would call mkswap which actually formats the given device as a swap partition! i guess that not any data that might have been on this partition is instantly lost but for sure one would have serious trouble mounting the partition normally after that!
and at least after the swapon commaned has been executed and the system has made use of the swap area ( = written data to it ) one would seriously face a hazardous data-loss!
i'll try to figure out something that could prevent this scenario from happening; the 'isLuks' action of cryptsetup seems interesting... [/INDENT][/LIST]

---

### Post by antiplex on 2007-11-25
the more i try around with cryptsetup the more confused i get...
i found out that simply doing ```
cryptsetup -d /dev/random create my_swap1 /dev/<mydevice>
``` seems to bee enough to create volume with a random password *(passwordA)* that could be formated as swap by 'mkswap /dev/mapper/my_swap1' and then let the system use it through 'swapon /dev/mapper/my_swap1', but no matter what i do to my newly created my_swap, a check for being a luks partition through ```
cryptsetup isLuks /dev/<mydevice>
``` just fails and so do the other actions like 'luksDump', 'luksUUID' etc.

this changes as soon as i do a ```
cryptsetup -q -s 128 luksFormat /dev/sda6
``` where i also have to enter a passphrase *(passwordB)*.
after doing this all the mentioned actions work but i think i would now have to open the device through ```
cryptsetup luksOpen /dev/<mydevice> my_swap
```, right?

so now if i again call call 'cryptsetup -d /dev/random create my_swap1 /dev/<mydevice>' this also seems to succed, but still all the actions like 'isLuks', 'luksDump', 'luksUUID' etc. work fine! 
what seems weird to me is that the uuid and all other data that could be seen by luksDump is still exactly the same as before, so i wonder what 'cryptsetup [...] create [...]' exactly does, how the two passwords *(passwordA & passwordB)* relate to another and what de difference between the actions 'create' and 'luksFormat' really is?

can anybody maybe explain this to me? i looked through the manpages and searched the web but couldn't find any satisfying answer...

---

### Post by mahousaru on 2007-11-28
From what I gather there are no current plans for a 10 inch eeePC, the 8G will have its memory increased to 1GB and have 8GB ssd instead of 4GB as in the current one.

**Before anyone jumps the gun, we already know about using a single password on LVM :)**. I'm actually using it on my laptop and it is great, but there are other scenarios where the swap is residing on another disk.

You bring up a great point about using the UUID as it would be terrible to accidentally cryptsetup the wrong drive!  With a "losable" laptop that might not be such an issue as data will be backed up and even if sata, the single disk should be the first device in it (unless it has esata...), but for a device with multiple drives that could be disastrous.  Also I think it is a good idea to disable the script after a kernel update just in case.  After having a good think about it, I don't think it is such a good idea to auto generate the swap each time.  I think I'll manually type my password in or at the very least have it mount by a key on my primary encrypted partition.

The main benefit of an auto generated swap is that you don't need to type in a password and you have deniablity. You can't tell someone the key as it is auto generated each time.   
The down side is what you have already highlighted..

To get around needing a password you can have a key on the primary encrypted partition and use that to automatically mount the swap, but the problem with this is if someone compromises the file via the network, then can then use that key to unlock the swap and then try to recover your main password.  Seems like a lot of hard work and if someone is after existing files then they could just go after them instead of the key via the network.  The only benefit I can see from attacking in this way is if they want to do an analysis on the drive for deleted files.  I wonder can a partition be mounted from a key on an sd card and then the key removed?  I'll test that at a later date.

Finally I guess there is the type it in each time scenario.  This is the safest method and if you don't need to keep starting up you machine shouldn't be that much of an issue.

**Hard question about the UUID**, from what I gather it is generated when a partition is formatted and stored in the partition itself (can someone confirm this please?).  If you list yours you should see a UUID for the external partitions, so in the case of the encrypted partition maybe u are looking at the physical parition id instead of the internal encrypted partition id which is generated each time.

ls /dev/disk/by-uuid -alh

Will list all the uuids know to the system

Whilst

sudo vol_id /dev/device

will show u the info for the device itself.  if you use that to the created swap and then see if it changes or not.  

I'm just in the middle of re-installing my vmware box so I can't test it yet.  I'll try out the other things u raised about the cryptsetup command too.  Well unless someone can answer us off the bat :)

@kwlskwlguy - Thanks for the heads up.  I have never deleted the primary key and now I never will :).  I generally keep my primary as the master key that I don't use.

@everyone - Has anyone recovered from software raid 1 with a encrypted partition?  I'll test it in vmware as soon as i get a chance, but I hope if a disk fails I can just pop in another and rebuilt it....

---

### Post by mahousaru on 2007-12-06
The main issue before I start waffling is I reinstalled my laptop with a fully encrypted lvm and my eeepc in the same way.  both suspend and resume fine.  all devices recover including network and truecrypt mounted partitions.  hibernate fails for obvious reasons :p

Now onto the waffle about my new toy, I mean tool :)

I've brought a eeepc and it is amazing with Compiz on it.  But that aside, I think a major issue with it is the lack of data security.  It addresses 2 things about mobile devices very well that being lightness and cost.  I don't break my back carrying it around and if someone nicks it or it breaks I don't mind as much as loosing my lappie which costs 3 times as much.  Now even though the cost is low, I think this item is a prime candidate for encrypting and it encrypts really well.

I have one boot partition like before and the rest I have encrypted as one. I didn't leave the other special partitions as I didn't realise that they were needed for the BIOS upgrade, but I'll cross that bridge when I need to :p

I followed the instructions on the eeepc user wiki with a slight difference.  I used truecrypt to encrypt a sd card which i will use to store my data and I moved certain var directories not to tmpfs but to and encrypted usb hdd.  My reasoning is that I will only do certain maintainace tasks such as updating or adding programs at certain times.  When i do I'll plug in the hdd, it has a swap file on it so I can also plug it in if i need to load the eeepc, but that is going to be really rare.

Very happy with it and it most defiantly is worth the 185gbp I paid for it :)

---

