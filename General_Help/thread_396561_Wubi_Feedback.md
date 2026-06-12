---
title: "Wubi Feedback"
date: 2007-03-29
forum: General Help
---

### Post by ago on 2007-03-29
Use this thread to tell us what you think about Wubi. Do you like it? Do you hate it? Let us know!

---

### Post by christhemonkey on 2007-03-29
I personally think wubi is an excellent idea and something that probably should have been done a long time ago!

Thankyou very much for this awesome tool.

---

### Post by ubunt00 on 2007-03-29
Do you need internet, or do you download it just from the installer and the Wubi program?

---

### Post by danbutter on 2007-03-29
I think it is really good starting with beta....I have been working on this for a few weeks now and it has come a long way in that little time.

Now that beta is out and we are past the herd my wireless works (intel 3495) my screen doesn't take five mins to scroll anymore.

All I need now is my bluetooth mouse and beryl working and I'll be happy.  Now when I try to install beryl I break the video totally.

---

### Post by Oedipe on 2007-03-30
Partitioning/Resizing  is the biggest barrier to Linux adoption for Windows users.

Wubi is a great way to _**test**_ Linux, BUT, the majority of people and novices have just one big Windows ntfs partition with both OS and Data, and they will install wubi on that one. It should be fair to tell them that they will never be able to work on their existing windows data/files with Ubuntu and that unique partition.

I point here this restriction because some novice people already asked me if they could.

Regards,

---

### Post by ago on 2007-03-30
> **Oedipe said:**
> It should be fair to tell them that they will never be able to work on their existing windows data/files with Ubuntu and that unique partition.

Yes they can: [http://www.ubuntuforums.org/showthread.php?t=396629](http://www.ubuntuforums.org/showthread.php?t=396629)

---

### Post by Mr.mouse on 2007-03-30
The Windows based installer import information from windows to ubuntu so in the first run of ubuntu the user don't have to define any thing.
The installer import from windows bookmark to firefox, internet composition, screen resolution, font size, mail define to Evolution, message (msn,icq…) to gaim…..

Windows to linux application, for example: 
If the users have in windows google earth the installer install google earth on ubuntu
Windows Skype - linux skype…

Flash java…and all files formats


All the latest updates will be downloaded

Create a small file so that when the user click on the file it will automatic download the latest version of wubi and run it

Don’t ask the user for username in wubi and in reboot, create one like my document, my home…

Give an example like, you will need this password to add/remove programs


Auto Shortcuts on the desktop to windows hard discs (read and write) by default.

Add  Wubi to Ubuntu live cd, so when the user run Ubuntu live cd on windows Wubi will popup.

---

### Post by Oedipe on 2007-03-30
> **ago said:**
> Yes they can: [http://www.ubuntuforums.org/showthread.php?t=396629](http://www.ubuntuforums.org/showthread.php?t=396629)

O.K. That's great ! :) 

I thought that Wubi-Ubuntu could only manage ntfs files on **other** ntfs partitions/disks, but not on the partition where it was installed.

Sorry to have misunderstood the matter. That's really good news :popcorn:

---

### Post by aijalu on 2007-03-31
Hi All,

 I just tried 7.04beta and I got a bad iso file - the exact steps were:
1. double click the exe, press next until it starts downloading the iso file.
2. give it lots of time
3. come back the next morning to see it aborted with a message URL PARTS ERROR
4. Try to rerun it, it completes this time because it finds the (broken) iso file.
5. reboot when it tells me to.
6. the boot loader has an added entry for ubuntu, when choosing it nothing happens (the computer stops).

So - I guess this is two bugs in one:
 1. Fails to download iso file with strange (for first time users) message.
 2. Doesn't delete iso image when it is bad (or doesn't recognize a given iso image is bad - I think there should be a, perhaps optional, md5 checksum stage before actual installation, with an option to redownload if the checksum fails)

Anyway, I think it would be a great way to gain new followers^H^H^H^H^H^H^H^HUsers once it works, so keep up the good work!

Alon
(alon is just another linux user).

---

### Post by ago on 2007-03-31
> **aijalu said:**
> Hi All,

 I just tried 7.04beta and I got a bad iso file
It's a large download (~700MB) and if there are problems with the line it will fail. But the next version will include auto-resume (thanks to Hampus). 

> 4. Try to rerun it, it completes this time because it finds the (broken) iso file.
That's strange, we already use md5, thx, we'll look into it. Are you sure you did not have other ISOs laying around?

---

### Post by joshier on 2007-03-31
> **Mr.mouse said:**
> The Windows based installer import information from windows to ubuntu so in the first run of ubuntu the user don't have to define any thing.
The installer import from windows bookmark to firefox, screen resolution, message (msn,icq…) to gaim…..

Windows Skype - linux skype…

Create a small file so that when the user click on the file it will automatic download the latest version of wubi and run it

create one like my document, my home…

Auto Shortcuts on the desktop to windows hard discs (read and write) by default.

I personally agree with these points..

It would be a "wow" factor most definitely... Users would boot into ubuntu, load firefox and Bam, all their bookmarks etc are there already.

---

### Post by ago on 2007-03-31
There is a migration assistant in Feisty but we did not have time to work on it within wubi, it will be dealt with in the near future.

---

### Post by obi.juan on 2007-03-31
Is it planned to make an installation from an Ubuntu CD? I've got a LiveCD in another computer with DSL connection because my home computer only has dial-up connection. If it's not planned, please take it into account. ;)

I've already read that Ubuntu installation is done in an unique file that works as a HD. I know that the aim of the project is to make an easier way to dualboot windows and Ubuntu without partitioning but... would it be possible that in the future the installation will be done in another already-done-partition? For better performance of windows (I give it a lot of free disk space), I would like to have separately ubuntu from windows.

Thanks in advance.

---

### Post by ago on 2007-03-31
> **obi.juan said:**
> Is it planned to make an installation from an Ubuntu CD? I've got a LiveCD in another computer with DSL connection because my home computer only has dial-up connection. If it's not planned, please take it into account. ;)
Not any time soon, but see the guide on how to use wubi on pc with no internet connection. 

> would it be possible that in the future the installation will be done in another already-done-partition?
More likely we will make a migration tool from the wubi file to a dedicated partition.

---

### Post by aijalu on 2007-03-31
I don't think it's likely that there was an iso image lying there, I'll check. Anyway, I'll wait for the version with auto-resume.

Alon

---

### Post by manino on 2007-03-31
This is amazing! I have been using ubuntu for two years now, but trying to install ubuntu in a Compaq with hidden recovery partitin was a nightmare - until now.
I simply ran the installer, and once ubuntu booted, I ran synaptic: full ubuntu server.

Bet of all, the owner of the machine is also happy :)

---

### Post by obi.juan on 2007-04-01
ago, thanx a lot for your reply.

I've just found the wubi help you've told me (definitively, I  haven't done the correct search in the wiki).



Another questions:

1st. Is the philosophy/way of Wubi the same as the one of BootCamp from Apple to install and run Windows on Macs?

2nd. Is it possible in a future to improve Wubi so it can make a "real" installation of Ubuntu in another partition instead of in a "virtual drive" file?     I.e. you could install in a secondary HD ubuntu from windows so this hard disk could be in a future a primary boot disk if there's a problem in the first one... or if you want to forget definitively Windows.


Thanks and keep on the good job  =D>

---

### Post by ago on 2007-04-01
1. I guess that this would be more like running OSX on a windows machine, but without formatting/changing partitions

2. As mentioned we will later create a tool to migrate a wubi file to a dedicated partition, so you install via wubi as usual and if you like it and have a spare partition you can move the wubi files to the partition. But no timetable for that yet.

---

### Post by w1zard on 2007-04-14
Just tried Wubi for the first time, I'm a Ubuntu virgin but the process was *very* easy to follow - great work! 

Couple of points I noticed, firstly I was told my username could not start with a capital letter. This stopped the Ubuntu auto-install process and I had to manually intervene. I can't remember whether I chose this account name myself, but I'd used 'Administrator'. Changing it to a lowercase 'administrator' fixed it - helpful if this could be checked by Wubi in the Windows-mode part, if possible?

Secondly, some kind of disk-check ran on first boot. This failed the first time (I assume while checking the virtual partition Wubi creates?), but completed the second time. I'm sure that my disk is fine and a windows chkdsk shows no errors, so am not sure why this showed? If I wasn't watching what was happening I would have ended up in XP when it rebooted on the first failure and perhaps thought it had all gone horribly wrong!

Otherwise, Wubi is extremely impressive - keep up the good work :)

---

### Post by Razzl on 2007-04-18
I installed using Wubi on an Averatec 2370 laptop with WinXp Media Center edition.  It worked perfectly, Ubuntu ran fast enough and well, and it uninstalled without problems.  The only thing I didn't understand was that its folder on my Windows Explorer showed it taking up 30gb of space on a 100gb hard drive.  I didn't know if this means that Ubuntu installs as a much bigger program when run inside Windows, or whether it had just appropriated  a percentage of the available space.

I should also point out that Wubi is not visible on the primary "3rd party project" menu because it comes last.  I spend weeks looking for something on Wubi and it seemed mysterious that it wasn't listed anywhere--you've got to get them to make it show!

---

### Post by ago on 2007-04-19
> **Razzl said:**
> I didn't know if this means that Ubuntu installs as a much bigger program when run inside Windows, or whether it had just appropriated  a percentage of the available space.
Second one, and yes you will be able to choose how much space to allocate in next version.

> I should also point out that Wubi is not visible on the primary "3rd party project" menu because it comes last.  I spend weeks looking for something on Wubi and it seemed mysterious that it wasn't listed anywhere--you've got to get them to make it show!
Well that is not up to us, the 3rd party projects are in alphabetical order, but you might give suggestions to ubuntuforums admins here [http://ubuntuforums.org/forumdisplay.php?f=48](http://ubuntuforums.org/forumdisplay.php?f=48) 

Another way to improve our visibility is to slashdot/digg us, but it's better to wait for us to push out the "final" before doing that. I use quotes since we might go gmail route as far as the beta goes...

---

### Post by johnwillyums on 2007-04-19
Hi, I've been following this project since the beginning and made several unsuccesful attempts to use the installer.
I'm waiting for an "idiot-proof" version. In the previous answer you mention the gmail root for the beta version.
Could you elaborate?
I'm amazed by how much work you guys have put into this and I just know it's going to be a success. All my (equally) non techy friends are waiting so I think it's going to be a big event for ubuntu/linux.

Thanks again, John

---

### Post by ago on 2007-04-19
> **johnwillyums said:**
> 
Could you elaborate?
I'm amazed by how much work you guys have put into this and I just know it's going to be a success. All my (equally) non techy friends are waiting so I think it's going to be a big event for ubuntu/linux.

Thanks again, John


There will be a bit of delay for our "final", but even then we might decide to keep the "beta" status in the download button for a while because:

1)  even if the "final", things might not be 100% smooth, and we do not want to overblown expectations until we are 100% sure 
2) there might be uncaught bugs that will emerge only once several people use the product (corner cases), and we might want to keep the door open to push changes in the "final". 

That said the betav3 is already fairly good and the installer should soon be far better than previous versions and hopefully easier than almost any other installer around, whatever the OS... I know it's a bold claim, but that's the aim.

---

### Post by rdelfin on 2007-04-20
Tried to install  ubuntu through Wubi, and the software kept on trying to dowoload 7.04-BETA, which is no longer available, thus making the completion of the installation impossible.

Any news regarding when the Wubi-installer will be updated to fetch the 7.04 non-beta (final) release?

(you guys are doing a great job btw).

Thanks!
R.

---

### Post by Antimethod on 2007-04-21
It's a great installer, but I think it should let you use an already existing .iso on the computer.I have downloaded  ubuntu-7.04-alternate-i386.iso and now i have to wait for WUBI to download it again.
My suggestion is to add a new option "open .iso" or something.

---

### Post by ago on 2007-04-21
> **Antimethod said:**
> It's a great installer, but I think it should let you use an already existing .iso on the computer.I have downloaded  ubuntu-7.04-alternate-i386.iso and now i have to wait for WUBI to download it again.
My suggestion is to add a new option "open .iso" or something.

If you already have an ISO, simply put it in the same folder of wubi.exe. The final ISO will not work at the moment, only the beta ISO.

---

### Post by tuxcantfly on 2007-04-22
> The final ISO will not work at the moment, only the beta ISO.

with the new wubi-7.04-v1, the final iso should now work
note that this release received rather little testing, due to the urgency of the release (beta isos are no longer available) so it might not work

---

### Post by Lightspeed on 2007-04-22
> **tuxcantfly said:**
> with the new wubi-7.04-v1, the final iso should now work

Where is it?

---

### Post by MrGreen on 2007-04-22
Just tried wubi but it cannot find iso ... the path to iso image looks wrong? I am using beta-v3 ?

---

### Post by w1zard on 2007-04-22
It's probably worth documenting in the installer that if Windows is not shut down cleanly (ie it crashes or you power it off without shutting down) then on reboot Ubuntu will not not run. Even if Ubuntu has worked in the past, if you boot back into Windows one day and don't shut it down properly, Ubuntu will not boot.

It fails at boot with a very obscure error. It's only by reading around on the forums I found a log which informed me 'the NTFS partition is dirty'. I had re-installed Wubi and Ubuntu twice by this point, when all I needed to do was boot into Windows and shut it down cleanly.

To save others the same grief it would be a great if a 'hint' of what's needed could be shown on boot failure, rather than the standard and obscure message that to a beginner looks critical.

I've got photos of what happens when a 'dirty' partition's found if anyone's unsure what the nasty message looks like.

Keep up the great work!

---

### Post by linux22 on 2007-04-25
I would like to start with telling you that you are doing a great service for the community, Wubi works well and meets its goal of making it easy to experiance linux. As an example I would like to cite my dad using it on his laptop. He had been courious for a while about linux hearing that it is quicker and better than windows. He had two major problems, lack of time to work on installation, and a lack of a CD drive for his computer. When I pointed out your installer that I came across in Yahoo, I told him about it and insisted he try it. 

Astounded at the fact that it booted QUICKER than his windows even though it had to work with the image files he immeadiatly took intrest in it. He has already figured out how to read his NTFS partition and even had begun the prosses of being active in the linux community by fileing bug reports. This may seem like little to you and other people in the linux community that make contributions on the scale of contributing to huge projects but for someone who had never experianced linux to turn around and in a month be filing bug reports and customizing his computer is spectacular. Personally I started in linux about 3 years ago and always had the obtistical of not having computers to learn on. My first attempt at a file server had a bad hard drive and set me back 2 years. I can only imagine what I would be doing now if I had this. I could have kept my computer with windows instead of finding the worst computers to experiment with to avoid corrupting my windows.

The only one thing that I think is really needed, is for this executable to be avalible on the Ubuntu CD set. It would be easy for people to experiance Ubuntu because they could either descover us, or a freind could just hand them the CD so they could run the executable. 

Thank you for our Wubi. 
--
Gotta have that fresh Ubuntu in the morning, with that fresh, robust Wubi flavor.

---

### Post by sanuward on 2007-04-25
great stuff!
but of course also some suggestions:
-choosing the offline iso, also the dvd one (I already downloaded that for another PC and wubi still downloaded the alternate iso)
-or at least: using the dvd iso if already there
-doesn't [https://wiki.ubuntu.com/WubiGuide#head-bc97a48fadb926d23e99a80a32ce6208af620e30](https://wiki.ubuntu.com/WubiGuide#head-bc97a48fadb926d23e99a80a32ce6208af620e30) the way it is also copy /home to root.img?
-are compressed ntfs-files for the image supported? could that be choosable as default for small harddisks?

---

### Post by ago on 2007-04-25
> **w1zard said:**
> To save others the same grief it would be a great if a 'hint' of what's needed could be shown on boot failure, rather than the standard and obscure message that to a beginner looks critical.
That's a good tip, only issue is to generate the unclean umounts of windows so that we can test the error

> I've got photos of what happens when a 'dirty' partition's found if anyone's unsure what the nasty message looks like.
That may help

---

### Post by ago on 2007-04-25
> **sanuward said:**
> -choosing the offline iso, also the dvd one (I already downloaded that for another PC and wubi still downloaded the alternate iso)
-or at least: using the dvd iso if already there
As mentioned in the past just put the ISO in the same folder as Wubi and it will detect it. Note that only alternate ISOs will work, and I do not think that there are alternate ISOs for the DVD version.

> -doesn't [https://wiki.ubuntu.com/WubiGuide#head-bc97a48fadb926d23e99a80a32ce6208af620e30](https://wiki.ubuntu.com/WubiGuide#head-bc97a48fadb926d23e99a80a32ce6208af620e30) the way it is also copy /home to root.img?
It shouldn't since you are using the x parameter with rsync (rsync -avx) which prevents rsync from going "outside" the current filesystem and since /home is on a different virtual drive it should not be copied over, unless I misunderstood something...

> -are compressed ntfs-files for the image supported? could that be choosable as default for small harddisks?
No. That depends on grub, which is out of our control, and grub for windows does not support compressed file systems. If anyone wanted to help patch grub to allow that, it would be much appreciated.  Detecting that might help only if there is another non-compressed partition with enough space.

---

### Post by ecology2007 on 2007-04-25
> **sanuward said:**
> great stuff!
but of course also some suggestions:
-choosing the offline iso, also the dvd one (I already downloaded that for another PC and wubi still downloaded the alternate iso)
-or at least: using the dvd iso if already there
-doesn't [https://wiki.ubuntu.com/WubiGuide#head-bc97a48fadb926d23e99a80a32ce6208af620e30](https://wiki.ubuntu.com/WubiGuide#head-bc97a48fadb926d23e99a80a32ce6208af620e30) the way it is also copy /home to root.img?
-are compressed ntfs-files for the image supported? could that be choosable as default for small harddisks?

1- We take your suggestion into account, it will be possible to use DVD isos in coming versions.
2- Yes and you have to edit fstab accordingly, and remove the line mouting home to /dev/loopX
3- No. It does not give any advantage and it is not natively supported by ntfs-3g, which is the thing we use to read and write ntfs.

> The only one thing that I think is really needed, is for this executable to be avalible on the Ubuntu CD set. It would be easy for people to experiance Ubuntu because they could either descover us, or a freind could just hand them the CD so they could run the executable.

We totally agree but it is still a young product. You can support it for the integration in feisty +1 following this post.
[http://ubuntuforums.org/showthread.php?t=415190](http://ubuntuforums.org/showthread.php?t=415190)

> It's probably worth documenting in the installer that if Windows is not shut down cleanly (ie it crashes or you power it off without shutting down) then on reboot Ubuntu will not not run.
That thing is also one of the ntfs-3g "feature" to protect your data if the NTFS partition has been compromised. It will refuse to mount such a partition. You have to reboot in windows a run a disk check.

---

### Post by sanuward on 2007-04-26
As compressed NTFS files are not yet supported, wubi should at least ensure the files it creates are not compressed - I had to manually decrompress the whole wubi folder which took about half an hour... Also menu.lst and grldr in the root directory shouldn't be compressed I guess (didn't test that, but I tested compressing ntldr once upon a time and learned from that...)

(edit)
Besides, uninstall shouldn't delete the just downloaded and nowhere else backuped iso... (reinstall wasn't available so I had uninstall first)
It would be even nicer if the home.img could be stored on a samba share and the windows pagefile.sys used as swap.img

---

### Post by celsus on 2007-05-03
I have been struggling with Wubi for several hours now.  The installer does not recognize the alternate iso of the latest Xubuntu release.  I made the mistake of believing the info from the Wiki, i.e:

"How do I install on a machine with no internet connection?

Try to find a computer with internet access, and download both Wubi and the required ISO (containing the installation files):

    *

      [WWW] [http://cutlersoftware.com/ubuntusetup/latest.html](http://cutlersoftware.com/ubuntusetup/latest.html)
    *

      [WWW] [http://releases.ubuntu.com/7.04/ubuntu-7.04-beta-alternate-i386.iso](http://releases.ubuntu.com/7.04/ubuntu-7.04-beta-alternate-i386.iso)

Then copy both files within the same folder on the machine with no internet acces. Then run the Wubi executable. If you have internet access on the machine where you plan to install Ubuntu, you only need Wubi (the first link), Wubi will automatically download the other file as required.
How can I use a manually downloaded ISO?

You need to download the ALTERNATE ISO of the appropriate version. If you are using Wubi-7.04-beta-XYZ.exe, you will need Ubuntu-7.04-beta-alternate.iso. Place the ISO in the same folder where you have Wubi-7.04-XYZ.exe. Then run Wubi.
How do I install Kubuntu/Xubuntu/Fluxbuntu?

Download the alternate ISO for the desired Ubuntu flavor, make sure it is the correct version (see above). Then follow the instructions above. "

How one determines what the correct version is is murky -- there are no Ubuntu .isos named
"ubuntu-7.04-minefield2-alternate-i386.iso" (since the only Wubi installer I can find is called "wubi-7.04-minefield2.exe" -- the appellation "minefield" is an unfortunate one).  The interface is absolutely rigid.  If the installer IS capable of using an extant .iso, it gives no indication.  At the very least, provide links to the versions of the Wubi installer which WILL recognize .isos other than "ubuntu-7.04-alternate-i386.iso" (which is what the installer is now downloading on my machine; not "ubuntu-7.04-beta-alternate-i386.iso" as stated at the Wiki).  I understand that this is not a final version, and I would be glad to give feedback to help improve the program, but I'm not happy about being actively mislead.

---

### Post by celsus on 2007-05-04
I installed wubi to D: the original 20GB IDE HD that came with my eMachines T1220. D: is not part of a RAID, it is not compressed; it isn't even fragmented, but it won't boot. The loader can't find /WUBI/BOOT/MENU.LIST (I see there is a menu.lst in boot and another in its subdirectory, wingrub), but just before it terminates with error message 17 it is apparently looking on A:

Any idea how to get Ubuntu to boot?

---

### Post by celsus on 2007-05-04
Correction:  the loader can't find /WUBI/BOOT/MENU.LST

---

### Post by celsus on 2007-05-04
I see that someone else with the same problem was able to get wubi to work by putting it on C:  I don't want a 5GB folder on C:!  More to the point, I don't want to read specific instructions (at the Wiki) as to how and where to install that turn out to be completely wrong.  I'd like to be able to provide constructive feedback, but wubi needs to get its act together more before I'll spend much more time with it.  Is it really too much to ask that even the developmental versions of wubi at least permit the user to specify where to install?!?  It is a pain to have to move 5+GB folders back and forth!  I couldn't test the putative solution anyway as I'd already uninstalled.

I need some clarification as to WHAT can be installed, WHERE, and by WHICH version of wubi before I'll try again.  I also need whatever version(s) of the wubi installer I download not to be named "**minefield**" (wubi-7.04-**minefield2**.exe is all that is offered as the "latest release" and on the download page) -- what gives?  It is extremely bad form to force us to use an "experimental" version of a turn-key installer, especially when it is broken -- it is difficult to provide much feedback when you can't even boot the system!  All I can conclude from the fact that the "latest official version" is designated a "minefield" is that you don't have a stable version.  I'm interested in the project but I'm very turned off by the gap between the representations at the homepage and on the Wiki versus reality.

---

### Post by celsus on 2007-05-05
OK, I downloaded the alternate Kubuntu from the link supplied and minefield4.exe.  This time minefield asked me where to install.  I chose D: again; after making wubi contiguous and rebooting the grub loader terminates (with error 17) because it can't find menu.lst.  I uninstalled wubi and tried again.  Now, minefield did not ask where to install but started installing to the largest empty partition.  I uninstalled wubi again and restarted; now wubi ignored the .iso of kubuntu entirely and proceeded to try to download another copy.  I uninstalled wubi
again and rebooted; now minefield crashes immediately.  I have tried repeatedly to install this program after carefully reviewing all the information you have provided and nothing works!

---

### Post by LegoAddict on 2007-05-07
This is an excellent product!  I use it on my laptop, and it's saved me quite a few times.  I've suggested it to my friends (though they write it off as my complete nerdiness ;) )


My only issue is the bootscreen.  It would be nice to have a nice shiny bootscreen instead of a bunch of text. (fiesty)

---

### Post by ago on 2007-05-07
> **LegoAddict said:**
> 
My only issue is the bootscreen.  It would be nice to have a nice shiny bootscreen instead of a bunch of text. (fiesty)
Latest release (minefield0.4/test1) should provide that. 

To add it manually from Ubuntu:

sudo dpkg-reconfigure usplash

Then from windows edit C:\wubi\boot\grub\menu.lst and add "splash" as kernel parameter and in defoptions.

---

### Post by ago on 2007-05-07
> **celsus said:**
>  Now, minefield did not ask where to install but started installing to the largest empty partition.
More likely you were in reinstallation mode and wubi installed in the same partition were it was before.

> I uninstalled wubi again and restarted; now wubi ignored the .iso of kubuntu entirely and proceeded to try to download another copy.
Was the ISO in the same drive as the wubi executable? If you uninstalled it might have deleted the previous download in c:\wubi\install (one of the places searched for ISO).

> I uninstalled wubi again and rebooted; now minefield crashes immediately.
If you can find the steps to reproduce that we can test it and try to fix, uninstalling, changing drive and reinstalling seems to work for me.

---

### Post by LegoAddict on 2007-05-07
> **ago said:**
> Latest release (minefield0.4/test1) should provide that. 

To add it manually from Ubuntu:

sudo dpkg-reconfigure usplash

Then from windows edit C:\wubi\boot\grub\menu.lst and add "splash" as kernel parameter and in defoptions.

Emmmm....


Sorry, I didn't get that last part.  I'm a Linux newbie (Wubi is what gave me the courage to try it out) and I have no clue what a defoption is.  What exactly do I have to do?

---

### Post by ago on 2007-05-08
> **LegoAddict said:**
> Emmmm....


Sorry, I didn't get that last part.  I'm a Linux newbie (Wubi is what gave me the courage to try it out) and I have no clue what a defoption is.  What exactly do I have to do?

If you edit c:\wubi\boot\menu.lst from windows, you will notice that there is a line

defoptions quiet

change it to

defoptions quiet splash


then append "splash" to all the lines beginning with "kernel"

then save and reboot

---

### Post by LegoAddict on 2007-05-08
Hmmmm... I don't have that stuff.

This is my complete C:\wubi\boot\menu.lst

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        1

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

## Pretty colours
#color cyan/blue white/blue

#### KERNEL PARAMETERS ####

# the /folder/path paramater must be matched in the following 3 lines:
#
#find --set-root /folder/path/linux
#kernel /folder/path/linux find=/folder/path/linux
#initrd /folder/path/linux
#
#you must replace /folder/path with the path where the files where installed
#do not use the same folder name on different partitions

## To specify the ISO (otherwise the first one in the folder will be used)
#setup_iso=setup.iso

## To specify the root harddisk image(otherwise root.img is assumed)
#root_img=root.img

## To specify the home harddisk image (otherwise home.img is assumed)
#home_img=home.img

## To specify the swap harddisk image (otherwise swap.img is assumed)
#home_img=swap.img

## To specify extra harddisk image (otherwise extra.img is assumed)
#extra_img=extra.img

## Debug
#pause_for_debug debug

#### MENU ITEMS BELOW HERE ####

title Ubuntu
find --set-root /wubi/linux
kernel /wubi/linux find=/wubi/linux quiet ro
initrd /wubi/initrd.gz
boot
```

I used Wubi a month ago with the stable build then (Easter).


EDIT: There was another file under C:\wubi\boot\wingrub, but it said the same things, but didn't say everything this one said.

---

### Post by sanuward on 2007-05-08
just change the **bold** one...

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        1

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

## Pretty colours
#color cyan/blue white/blue

#### KERNEL PARAMETERS ####

# the /folder/path paramater must be matched in the following 3 lines:
#
#find --set-root /folder/path/linux
#kernel /folder/path/linux find=/folder/path/linux
#initrd /folder/path/linux
#
#you must replace /folder/path with the path where the files where installed
#do not use the same folder name on different partitions

## To specify the ISO (otherwise the first one in the folder will be used)
#setup_iso=setup.iso

## To specify the root harddisk image(otherwise root.img is assumed)
#root_img=root.img

## To specify the home harddisk image (otherwise home.img is assumed)
#home_img=home.img

## To specify the swap harddisk image (otherwise swap.img is assumed)
#home_img=swap.img

## To specify extra harddisk image (otherwise extra.img is assumed)
#extra_img=extra.img

## Debug
#pause_for_debug debug

#### MENU ITEMS BELOW HERE ####

title Ubuntu
find --set-root /wubi/linux
kernel /wubi/linux find=/wubi/linux quiet ro **splash**
initrd /wubi/initrd.gz
boot
```

now there is a strange thing: swap image specified by home_img=swap.img? same in my menu.lst. what is the correct version? swap_img=swap.img? I'd like to use windows' swapfile.sys in root directory, is that possible?

---

### Post by jettplane on 2007-05-08
Oedipie said: 

"It should be fair to tell them that they will never be able to work on their existing windows data/files with Ubuntu and that unique partition."


NOT TRUE.  You can access your Windows files through host, which is on the desktop.  And you can also use Windows servers with no problem.

And it works the other way around, too.  See my post labeled Accessing Wubi Disks Through Windows.

---

### Post by jettplane on 2007-05-08
Wubi is working very well for me on a Dell Inspirion 6000 laptop.  Most of the problems I've had have been with Ubuntu, not Wubi, or my own stupidity.  

A word of warning:  the uninstall wipes out EVERY virtual disk.  If you totally junk your system (as I did trying to solve a hibernation problem) an uninstall will wipe out your data  unless you make a copy of your home disk.  I do wish I knew the best way to experiment with settings...I trashed xorg.conf at one point and edited in Ubuntu, but the hibernation fixes I trashed were unrecoverable.  I guess if you have space and you are contemplating something that might trash the system, you could make a copy of the disks.

Ubuntu issues:

Mouse Alps touchpad-solved by adding two lines to xorg.conf:  "MaxTapTime" "0" and "MaxTapMove" "0".  To edit, on terminal

sudo nano /etc/X11/xorg.conf

HP LaserJet 4 driver as used in Open Office does not work with additional trays. It prints, but only on the default tray.  I think this is an Ubuntu issue.

Wine works well with Wubi so far.   Both ies4linux (Internet Explorer 6) and Visual FoxPro 6 work.

First install was minefield2, second is test1.

---

### Post by ago on 2007-05-08
> **jettplane said:**
> A word of warning:  the uninstall wipes out EVERY virtual disk.
In next version we will give the option to back up home.virtual.disk

---

### Post by LegoAddict on 2007-05-08
Got the bootscreen up.  There's a bit of text then I get it.



But it's the Kubuntu one...


I had KDE installed and I uninstalled all the KDE stuff, but I can't get rid of the screen...

---

### Post by tuxcantfly on 2007-05-08
> I had KDE installed and I uninstalled all the KDE stuff, but I can't get rid of the screen...

get rid of the package "kubuntu-artwork-usplash" and reboot

---

### Post by LegoAddict on 2007-05-08
I did.  I used the Completely Remove thing, and it's gone, but I still have the Kubuntu boot screen.  Is there some sort of cache I might need to clear?

---

### Post by ago on 2007-05-09
reinstall the ubuntu usplash and run: sudo dpkg-reconfigure usplash

---

### Post by Flying caveman on 2007-05-10
That installer worked great on my brothers HP Pavillion zv6000.  After I cleaned up his windows the best I could I installed Ubuntu.  He can access his windows files, I got his wireless working, and all the media stuff. Now when  his windows starts slowing down again he can just boot into ubuntu and everything will be just as it was.  

I think the installer needs something to tell you what its doing.  It seemed like it was taking a long time at one point, I can't remember which part of the install.  but I can just see someone thinking there computer hung and turning it off[-X [-X [-X [-X

---

### Post by ago on 2007-05-10
> **Flying caveman said:**
> I think the installer needs something to tell you what its doing.  It seemed like it was taking a long time at one point, I can't remember which part of the install.  but I can just see someone thinking there computer hung and turning it off[-X [-X [-X [-X

we are aware of that: [https://bugs.launchpad.net/lupin/+bug/113273](https://bugs.launchpad.net/lupin/+bug/113273)

---

### Post by sardaukar_siet on 2007-05-10
Well, I must say Wubi is awesome - really, really awesome. Very nice way for newbies to install Linux.

 Alas, I have 2 issues with it. First off, why only Ubuntu?

 And secondly, and most pressing in my case, I have no problem booting and all but restarting the PC is a no-show. I get logical block errors and it just stands there after the restart command (responsive, but not restarting and just complaining about IO errors on block devices). I have tested my hard-drive, it's fine. 

 All in all, works great and thanks for the effort! :D

---

### Post by ago on 2007-05-10
What version of wubi are you using? Wubi-test1 will allow you to choose other Ubuntu flavors (at the moment Xubuntu and Kubuntu, more to come soon). And the reboot issues should be fixed.

---

### Post by LegoAddict on 2007-05-10
> **ago said:**
> reinstall the ubuntu usplash and run: sudo dpkg-reconfigure usplash

That's weird.  I did that, still not working.  My computer is haunted by the Kubuntu boot screen :P

I uninstalled (complete remove) Usplash, the Ubuntu Artwork, and made sure all the KDE stuff was gone.

Then I rebooted.  no boot screen.

Then I logged in, installed Usplash and Ubuntu Artwork, and ran the Terminal line.

Then I rebooted...


Kubuntu artwork.

:(

But the wierd thing is that on shutdown, I have the Ubuntu screen, but on startup I have the Kubuntu one.


Following up on what the guy above said, it would be nice if it was possible to install other distros (specifically Open SUSE, which I'm trying to install on a VM under Ubuntu)

---

### Post by ago on 2007-05-10
sudo update-alternatives --config usplash-artwork
sudo dpkg-reconfigure usplash

---

### Post by LegoAddict on 2007-05-10
](*,) 

Still not working.  I've done everything I can think of...

---

### Post by ago on 2007-05-10
In fact that is more interesting than I thought... 

Usplash is "embedded" within the initrd, which is generated when you run sudo dpkg-reconfigure usplash, it might be that you keep booting from the old initrd and not the new one, which would explain what is happening. Make sure that the new initrd is in c:\wubi\boot under windows and that C:\wubi\boot\grub\menu.lst points to that. If you can understand why you are booting from the old initrd it would help a lot.

---

### Post by LegoAddict on 2007-05-10
Hmmmm...

How do I know where it gets generated?

---

### Post by ago on 2007-05-10
> **LegoAddict said:**
> Hmmmm...

How do I know where it gets generated?

It gets generated inside /boot. You can temporarily remove the other files except for the latest kernel and run the command, so the only initrd in there should be the new one. By the way /boot should be linked to C:\wubi\boot. If there is no link there, it is a problem: ls -l /boot

---

### Post by LegoAddict on 2007-05-10
What's the kernel?  Is that just the file named Linux under C:\wubi?


I don't have any initrds in the /boot folder.  It's in the main Wubi folder.

---

### Post by ago on 2007-05-10
it's the vmlinuz file under /boot in Ubuntu. You should have some initrd under /boot too. What version of wubi are you using?

---

### Post by LegoAddict on 2007-05-10
I don't have a number... the stable that was out between Easter and a week-week.5 after (after a few reinstalls) of this year.

---

### Post by ago on 2007-05-10
Old version were not able to update the kernel/initrd.

---

### Post by LegoAddict on 2007-05-11
So is there a way to backup everything (particularely Firefox bookmarks, Samba network settings, and Evolution email/contacts) so that I can just uninstall, get the newest build, and reinstall Wubi?  Or can I just run an updater from Windows?


How old is old?

---

### Post by southsanity on 2007-05-11
> **ago said:**
> Use this thread to tell us what you think about Wubi. Do you like it? Do you hate it? Let us know!
i think it is a great concept, theoretically, but i really wonder about the purpose of it, what i mean is that ubuntu is a distro targeted specifically at taking marketshare from windows, not co-existing with it, it seems a great way to get new users to ty ubuntu though, although, i would definately hope to see those users at sometime make a definate switch instead of sitting on the fence, hope i don't upset anyone, just my opinion, and i meant what i said, it is a great concept and an excellent piece of work, just hope it does something for our excellent distro is all
my own personal preference, i won't be needing it, i don't have windows at all, but have already let other people know wubi is out there as a great new way to try ubuntu, better than dual boot i think, way better than live cd

---

### Post by ago on 2007-05-11
Well with wubi you do get a dual boot configuration. Almost identical to what you would get by installing Ubuntu from LiveCD. The main differences are: 1) no burning of a live CD is required, 2) no partitioning, 3) you can uninstall. For the rest it's a good old dual boot setup.

---

### Post by Otkon on 2007-05-11
> **ago said:**
> Wubi-test1 will allow you to choose other Ubuntu flavors (at the moment Xubuntu and Kubuntu, more to come soon).

Will future releases install the 64-bit varieties? That would be tasty.

---

### Post by ago on 2007-05-11
> **Otkon said:**
> Will future releases install the 64-bit varieties? That would be tasty.

Almost no code change should be required* other than to add the 64 bit ISO details and recompile Wubi on a machine running the target kernel. So yes, but I have no time at the moment and no 64-bit machine. All it takes is a good soul, I'll be glad to host the build... 

See [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) under Customization, the same applies to 64 bits.


*  we do have the architecture hardocoded in a couple of places but that should be easy to replace

---

### Post by donteatthefish on 2007-05-12
in my opinion, this should now include ubuntu studio.

---

### Post by ago on 2007-05-12
> **donteatthefish said:**
> in my opinion, this should now include ubuntu studio.

It does... See wubi-7.04-test2 (main download link). The ubuntustudio servers are a bit overloaded though and download is slow atm, so could not test.

---

### Post by LegoAddict on 2007-05-13
Two other distros I would like to see:


Edubuntu and Ubuntu Christian Edition


I'm making a headway in converting a tech manager at a school district in Missouri to using Edubuntu since he needs to renew his contract with MS (and pay off the Vista laptops the Board bought so board members would have matching laptops at meetings :lol: ).  I suggested using Wubi as a way to test drive Ubuntu.  It would be great if a whole school district converted to Linux.

For the Christian Edition, our chuch computer running XP needs an exorcism... or another OS.  I thought Christian Edition would be great so that I could convince my pastor to test drive it on his laptop (which he was about to download and use Wubi on, but in the middle of downloading the Feisty ISO, his internet went down, so he gave up)

Btw, I checked my installation against your instructions... mine must be ancient because everything's different.  I'm trying to back stuff up and then I'll reinstall.

---

### Post by dicerchio on 2007-05-16
Wubi is great.

For months I've been extremely interested in installing some sort of Linux, so I did some research and heard of Ubuntu so I checked it out. I read some tutorials and learned you needed to repartition your harddrive to run another operating system, or install over your current one. Now I didn't want to leave Windows forever, so I looked more into the repartitioning method. In roughly 10 minutes I decided it was way over my head so I forgot about it.

So, one day I'm browsing Digg.com and an interesting topic comes up about Wubi: The easiest way to install Linux. So I read about it, and gave it a shot. I was immediately impressed with how user-friendly it was to get Ubuntu installed. In no time, I was already booting into Ubuntu for my first time thanks to Wubi.

Now I have completely figured out Ubuntu and in a couple months, I might leave Windows forever, thanks to Wubi.

Cheers to the Wubi Development Team :popcorn:

---

### Post by hummingbird59 on 2007-05-16
Wubi is FANTASTIC!  After waiting for months (literally) trying to figure a way to try Linux without killing my getting old computer, (Compaq Presario 40G HD, P4 1.5 GHz, nVidia Vanta Graphics Win XP SP2) I finally stumbled upon wubi last week.  It works beautifully even on an elderly system like mine and for a relative novice like me.  Thankyou Thank You!  Some questions (may be dumb so prepare yourselves):
(1) If I use my wubi to boot into ubuntu and surf internet, send and receive email and so forth and I never use Windows again for those things, do I still need to worry about viruses etc... since I am still technically operating from within windows? 
(2)  I'm not sure which Wubi version I have - whatever minefield was available last week- but will it automatically update to the newest version of wubi when released or should I manually update or should I just leave it alone since everything works?  BTW, I do get software update notifications for ubuntu itself.
(3)  I love Opera but there seems to be a problem with it under ubuntu.  From searching various forums, I can't figure out whether it is an opera problem or an ubuntu problem.  Basically, it is super slow (a minute and a half to load a webpage) at times when visiting certain websites (like the ubuntu forum website). I've uninstalled, purged, reinstalled from various sources including synaptic and Opera itself(deb file).  Nothing helps.  Any ideas?
(4)  I can't switch completely because of photo printing and a brand new canon printer that apparently will work only with Windows (sorry I did not know at the time!).  Yes I 've tried Turboprint - the quality just is not there.  So can I use wubi indefintely without creating a real partition.  What are the disadvantages to doing that?

I hope these questions make some sense.  Any help/info will be very much appreciated!  Thank you so much for giving non-technies a chance to try a fantastic OS!  Keep up the great work!

---

### Post by LegoAddict on 2007-05-17
(1)  You're actually not running from within Windows! :D  Wubi is a real Ubuntu installation that just uses Windows as it's base to install.  I heard a stat that there are about 45 viri in total for all Linux distros, but some of them were created in the "lab" setting to help test Kernel security, and the others have been squashed.  You don't need to worry about a Windows virus.

(2)  I haven't been able to get a answer on Wubi installation.  I seem to have an old version with a different file framework than I should have... but I don't know if I just reinstall.  But Ubuntu's updates will come through Ubuntu itself, like normal (you should get a +300MB one at first).

(3)  I also use Opera for Windows.  I downloaded the .deb from opera.com and installed it, but I just stuck with Firefox.  I don't know, I just like Firefox in Ubuntu better /shrug

(4)  Try searching the full name of your printer with Linux right after it.  That's how I found my drivers for my printer, which didn't have official Linux drivers, but there were Open Source, HP approved drivers out there.  Easy as pie to set up.

---

### Post by hummingbird59 on 2007-05-17
Thanks for the info! I'll give the print thing another go!

---

### Post by Cloudedbrains on 2007-05-19
I had a few issues using Wubi to install but altering disk sizes on advanced options (otherwise instal hung at 33%) 
got it to install and now is running with only minor issues :)

---

### Post by djtrancient on 2007-05-20
Just wanted to thank the all those associate Wubi development.  I've been wanting to use Linux for years, but was always intimidated by the partitioning and distribution packaging.  I downloaded Wubi, no partitioning, no complication, just restarted, and I was off!!!

---

### Post by stueyboy on 2007-05-23
Just a note to say that Wubi is now responsible for sneaking Ubuntu onto my wifes laptop with success. I wouldn't say the process was easy as I had to go through a bit of a process of elimination to work out that I ought to defrag the wubi directory from XP before trying the install but I got there in the end.

Handy that you can still access the XP folders as well. I feel that it moght be a touch slower than a fresh Ubuntu install in its own partition but that may be because I am comparing this laptop with my own which is quicker and newer.

I would recommend this to anyone who wants to try Ubuntu out in a more in depth way than with the live CD version. If this install is met with approval then I will get rid of XP completely and install a fresh Ubuntu on it.

Thanks for a cool application.


Stu

---

### Post by Dizzy4U on 2007-05-28
Ok, I have one question:

I've a laptop with a broken CD-drive. That's why I'll be trying this.

The thing is that I've two partitions: C: (wich has windows and programs) and D: (Wich has all the videos, mp3s, etc).

Is it possible to install linux using just the C: partition in order to delete all windows files? I don't want to loose the info of the D: partition, but i want all the C: partition erased in order to have just linux installed and get rid of all windows stuff.

Thanks in advance.

---

### Post by aldebarn42 on 2007-05-28
the wubi project is a wonderful addition to ubuntu, excellent work guys

i used wubi to see how well ubuntu worked on my tablet pc, and of course its perfect:)

so i was wondering is there a way to expand out the original disk size chosen at installation time? or will i have to start all over again??

---

### Post by abn91c on 2007-05-28
Yopu must defrag windows Xp first before installing wubi otherwise the install will fail, also when told to reboot allow the computer to do it, **DO NOT**  use the reset button or control alt delete.

> **aijalu said:**
> Hi All,

 I just tried 7.04beta and I got a bad iso file - the exact steps were:
1. double click the exe, press next until it starts downloading the iso file.
2. give it lots of time
3. come back the next morning to see it aborted with a message URL PARTS ERROR
4. Try to rerun it, it completes this time because it finds the (broken) iso file.
5. reboot when it tells me to.
6. the boot loader has an added entry for ubuntu, when choosing it nothing happens (the computer stops).

So - I guess this is two bugs in one:
 1. Fails to download iso file with strange (for first time users) message.
 2. Doesn't delete iso image when it is bad (or doesn't recognize a given iso image is bad - I think there should be a, perhaps optional, md5 checksum stage before actual installation, with an option to redownload if the checksum fails)

Anyway, I think it would be a great way to gain new followers^H^H^H^H^H^H^H^HUsers once it works, so keep up the good work!

Alon
(alon is just another linux user).

---

### Post by Kreuger on 2007-05-31
Any chance of support for [fluxbuntu]("http://fluxbuntu.org/")?

---

### Post by omgDarkWillow on 2007-05-31
It's great because I don't have to go through the pain and heartache of partitioning (which I don't know how to do, by the way).:p

---

### Post by ago on 2007-05-31
> **Kreuger said:**
> Any chance of support for [fluxbuntu]("http://fluxbuntu.org/")?

If they provide us with a metalink file targeting their alternate-iso, sure.

---

### Post by orangeLemon on 2007-06-03
> **omgDarkWillow said:**
> It's great because I don't have to go through the pain and heartache of partitioning (which I don't know how to do, by the way).:p
I know how you fill on that one. I've always wanted to put linux on my computer, but never felt like having only linux, or going through a lot of technical mess to get it on there, nor did I really fill like using a live cd all the time. Anyway haven't encountered any real problems with Wubi yet. Very neat way to dual boot for a computer newbie.

---

### Post by PPilatus on 2007-06-09
I'm a typical Windows user, but for years awaiting that moment a really safe and easy linux would appear.
Wubi/Ubuntu would be it, so I believed for an hour or so. 
Alas it became a nightmare. After running through installer, download and the rest of the proces which were very unfamiliar to the typical Win user I am, I smelt a rat when some installationprocesses gave back errors and I got stuck in the middle of installation not able to proceed or reverse. In the end I had to abort the thing and got ominous warnings that foretold ultimate doom. And so it was. After reboot.....nothing.
Couldn't do anything, there was no bootmenu. Just one sentence explaining there is no OS available. Never seen it before in my life. It was midnight by then and after a few reboots I called it quits and decided to end it drastically with my factorysealed recovery disk. Oh horror, the thing reported all kind of failures in not corresponding startsectors etc tried to repair and failed ofcourse and all came to nothing. At that point I realized I'd been duped. There is no such thing as an easy and safe foolproof linux. I called it a day, my temper was deep in the red and proceeding was dangerous in that state of mind.
Today with a fresh and calm mind I decided to investigate here hoping to find useful info. That was not really the case, but some similar cases described here gave me the idea I had to get windows going and ignore Wubi for the time being. After a lot of wrong turns, old fashioned dos is pretty useless with Win XP, I used some disktool that could at least give me a clue. It seems that during Wubi's failure to install itself properly it had deactivated the Windows partition. All to do activate C:\ and phew OS menu back, Win XP available again. Uninstalled Wubi, good riddance. Reboot, keep fingers crossed, phew it seems to work.
And then the aftermath. Wubi made two partitions of together 50 Gigs, but didn't clean them up afterward. Had to reclaim them myself with a lot of trouble because most partitionmanagers refused to do the job because of missing or incorrect partitiontables. At last Paragon Partition Manager, some freeby I once got with a harddisk, did the job. I have all space back and I hope the partitiontable is reliable now. Running some tests at the moment seems OK sofar. I call it a lucky escape. Hate to say so but Wubi is a great idea, but should not be released to us Windows suckers before tested way beyond this crappy dangerous release.

---

### Post by ecology2007 on 2007-06-10
Please edit your post and make it more readable.

---

### Post by kevinmedina on 2007-06-10
I Love Wubi!!!!

---

### Post by PPilatus on 2007-06-12
Don't know if I have to reply, but the repliant after me told somebody had to edit the post, could be me.
What is meant? I posted in readable english(I think). Do I have to write the post in commandline structure or what? I'm a Windows user so maybe I don't understand the lingo here. You are a fine bunch of people I'd love to understand and be a part of but I fear you are on another planet alltogether.

---

### Post by CrazyGuy123 on 2007-06-12
It just looks tidier if you seperate each paragraph with two enters (new lines) - keeps those people who care about how tidy things look rather than what you said happy. :)

---

### Post by welshlion on 2007-06-12
I only discovered Wubi 2 weeks ago and as someone who has been curious about Linux but not confident enough to try partitioning discs etc., I decided to give this a go and great stuff, it does exactly what it says on the tin (to borrow a phrase from a tv ad.)... still having problems learning how to make things work, but at least I got my USB Wireless adapter working.
Linux is challenge and I think the fun in using it comes from trying to find an answer to the each new issue that arises.

---

### Post by PPilatus on 2007-06-13
So no probs, it's allright to post like you are writing a book. Just the peeps that never read from oldfashioned paper have the probs. I can live with that. Don't try to mend my way of writing. It's freedom of speech and writing. Good health to all of you.

---

### Post by sanuward on 2007-06-14
Please don't post any further comments concerning writing style or whatever, I subscribed to this thread to hear more about others experience with ubuntu, and not about some trauma concerning some english teachers or whatever else does not have anything to do with wubi...

---

### Post by earther on 2007-06-18
I just heard mention of Wubi and went to the Wubi site to check it out.  Looks pretty slick to me but it doesn't look "pretty" because of the XP look.  First thing I did on XP was revert to the "Classic" theme.  The bright XP  blue and kiddie icons are about enough to keep me from using this tool.  I know why you did it but I think it is a mistake not to develop your own look.

---

### Post by Mizarus on 2007-06-19
ive always been a windows user tho i can use comand lines, format hd's and create partitions i never tryed linux out till a couple of mounths ago when i downloaded and installed Ubuntu, after a few tries fromated the hd a couple of times for messing up =p, then i finnaly managed to get it right and really liked it when i heard about Wubi i decided to install it to see how it went.
right now i have wubi and vista installed(formated again before installing wubi) and i can say that wubi is more then enough for windows users that would like to try linux out or slowly migrate to it, i love it, great job.

---

### Post by CrazyGuy123 on 2007-06-19
earther:  Do you mean the wubi website, or the wubi installer, or ubuntu?

The website is supposed to represent the transition from windows (left) to ubuntu (right).  Have you any ideas to forward to the designer on any improvements.  I like it the way it is now - enough to remind the user of windows, but different enough to show change and improvement.

If you mean the installer, it'll match your windows settings.  If you have windows classic enabled, the bubbly blue title bars and red close button will be replaced with your windows classic theme.  The screenshots are just taken with the default theme.

If you're discussing Ubuntu itself - I agree, the default theme wastes too much screen real estate (particularly spacing between icons and buttons is too big), but unfortunately, although a different theme can fix some of it, I don't think the rest can be customised easily.  Thats more of a general ubuntu interface design policy than a Wubi issue.  Windows 95 was the best OS for efficiently using screen real estate, and worked well on 640x480, but was still readable at 1280x1024 on an average monitor - no other desktop OS since has matched that.

---

### Post by Mizarus on 2007-06-19
just found a weird glitch that could be either wubi or a nvidia driver issue, i have both digital and analogic vga cables hooked to my pc, and when iam in ubuntu the digital cable wont work, when iam on vista analogic cable wont work, iam kinda new to ubuntu and linux OS so i dont know if its driver related tought i should report.

---

### Post by CrazyGuy123 on 2007-06-20
Mizarus:  I doubt it's wubi related.  It's more likley driver related.  Have you tried going through the screen settings in both windows and ubuntu?  Remember most graphics cards output different content through both of the outputs, so unless the output you're using has been selected as the primary monitor, you probably won't get anything useful out of it.  In windows, have a look at the advanced button on control panel > display > settings.  There's more driver related stuff in the tabs in there which is better than the windows one on the previous screen.

---

### Post by ljk on 2007-06-20
Wubi is absolutely great for people who don't understand and are naturally uneasy with partitioning. Like me.

There is, however, one small problem which may only occur in very special circumstances.

I live in Japan and Windows PCs come with the Japanese version of the OS installed. When Wubi is started, all the dropdown menu titles and the wubi window title bar are in Japanese characters.

We get the option to select the language used by Ubuntu but not the language displayed in the Wubi installer.

By looking at your screenshots it's easy to see what the different menus would be in English so it's not a major problem but for expatriates still working on the written language of their host country it would be even nicer to have the installer display in a language they can select.

This is the reverse of Apple's QuickTime which lets you choose the language used by the installer but only installs the "local" version of the program - your way is still a lot better than that.

Many thanks to everyone for getting Wubi this far, I am certain that lots more people will try Ubuntu just because  Wubi makes it so easy to install.

---

### Post by ago on 2007-06-21
> **ljk said:**
> We get the option to select the language used by Ubuntu but not the language displayed in the Wubi installer.
There are limitations in nsis that do not allow to change the interface at runtime, we'll se if we can do something about it.

---

### Post by earther on 2007-06-23
> **CrazyGuy123 said:**
> earther:  Do you mean the wubi website, or the wubi installer, or ubuntu?

The website is supposed to represent the transition from windows (left) to ubuntu (right).  Have you any ideas to forward to the designer on any improvements.  I like it the way it is now - enough to remind the user of windows, but different enough to show change and improvement.

If you mean the installer, it'll match your windows settings.  If you have windows classic enabled, the bubbly blue title bars and red close button will be replaced with your windows classic theme.  The screenshots are just taken with the default theme.

If you're discussing Ubuntu itself - I agree, the default theme wastes too much screen real estate (particularly spacing between icons and buttons is too big), but unfortunately, although a different theme can fix some of it, I don't think the rest can be customised easily.  Thats more of a general ubuntu interface design policy than a Wubi issue.  Windows 95 was the best OS for efficiently using screen real estate, and worked well on 640x480, but was still readable at 1280x1024 on an average monitor - no other desktop OS since has matched that.
Sorry to be slow in responding. I appreciate your thoughtful comments and questions.

My critique was based on the screenshots on the Wubi website - I really, REALLY don't like the native  XP theme and freaked out when I saw it.  I am happy to know that Wubi would match the Classic Windows theme.  I just downloaded Wubi but have not yet installed it.  I'm planning to install Ubuntu on Monday the old fashioned dual boot way. I don't know that playing with Wubi would have any benefits  as I already have Ubuntu installed on another box.  Then again, it looks like a really useful tool to introduce others to Linux.  If I'm feeling adventurous tomorrow, I might give it a spin.

I finally managed to get an Ubuntu layout pretty similar to what I have in XP using small icons etc. Took some doing though . . .  Hope I can remember how when I get the new install up and running!  Cheers!!

---

### Post by ago on 2007-06-24
> **earther said:**
> I finally managed to get an Ubuntu layout pretty similar to what I have in XP using small icons etc. Took some doing though . . .  Hope I can remember how when I get the new install up and running!  Cheers!!
That's easy, you just copy your home folder to the new installation.

---

### Post by earther on 2007-06-24
> **ago said:**
> That's easy, you just copy your home folder to the new installation.
But that would take all the fun out of it!  Besides that old box is still running Hoary or Warty (can't remember which - I don't turn it on often) and I'm sure that there are shiny new things to try.  ;)

---

### Post by fanpan on 2007-06-26
I am running a lenovo T60 with Vista business edition. It seems these two are married. 

I have tried Wubi 7.04.01, I have tried Easybcd, but whatever I do, whenever I restart the computer, it will start booting vista regardless.:(

Any ideas?

I would love to use Ubuntu, I already have it on my desktop, and really want Wubi for the laptop. Vista is an intolerable system.

---

### Post by ago on 2007-06-26
Run the bcd commands manually as indicated in [http://ubuntuforums.org/showthread.php?t=438858](http://ubuntuforums.org/showthread.php?t=438858)

You need to point the bootloader to wubildr.mbr which should have already been copied to your filesystem together with wubildr (otherwise you will find both files in c:\wubi\install\winboot).

---

### Post by Computer Guru on 2007-06-27
fanpan, in EasyBCD 1.61 BETA, when you add a Wubi entry and then reboot and select it from the list, what happens?
 
Also, check to make sure that your timeout is not set to 0 (second page in EasyBCD)

---

### Post by Krosis on 2007-07-04
I didn't use Wubi to install Ubuntu, I just checked it out.  Just wanted to post on here saying great job and it looks really nice.

---

### Post by LLauranzonIII on 2007-07-07
> **fanpan said:**
> I am running a lenovo T60 with Vista business edition. It seems these two are married. 

I have tried Wubi 7.04.01, I have tried Easybcd, but whatever I do, whenever I restart the computer, it will start booting vista regardless.:(

Any ideas?

I would love to use Ubuntu, I already have it on my desktop, and really want Wubi for the laptop. Vista is an intolerable system.

are you watching for the option to select the OS?  it'll default to windows after about 15 seconds if you don't do anything.

---

### Post by porcorosso on 2007-07-30
Wubi and Ubuntu are a very nice combination -- particularly useful to me because I wanted to stick Ubuntu onto a notebook which already runs Vista and which is used as an admin machine for a production domain. (I preferred sticking with the Windows boot loader for various reasons.)

I have run only into truly minor issues that were solved easily with a little bit of investigation. The Web-based documentation for Wubi and Ubuntu are superb in content, even if the Ubuntu docs are sometimes a wee bit rough around the edges. (The Ubuntu help files are really good.)

I do have a question, though, and I'm not sure if it's an Ubuntu question or a Wubi question. My reading in the forums here has led me to believe that invoking use of the restricted drivers for my nVidia video subsystem through the Restricted Drivers Manager in Ubuntu 7.04 should have installed the nvidia-settings application automatically.

It didn't work that way on my system. I tried issuing

```
sudo nvidia-settings
```

in a terminal and got a

```
nvidia-settings COMMAND not found
```

(May not be the exact message I saw at the CLI, but you get the idea.)

It was no biggie to install nvidia-settings. I was just curious to know if this was due to one of the changes Wubi institutes in the way the Ubuntu installation is performed.

It seems that the Wubi "version" of the Ubuntu generic installation is not exactly standard. It's obvious why some changes have been made, but it isn't obvious (at least to a beginner like me) why this change would have been made -- assuming of course that a) I'm not wrong about the default Ubuntu install behavior, and b) I'm not missing something.

Thanks again to the Wubi people for a truly fine product! I'm impressed, and I've been showing it to lots of folks.

---

### Post by talostalk on 2007-07-30
Hello all

I have a hp Pavilion zd8000 (laptop) with WinXP Media Center. A couple of days ago I installed Ubuntu through wubi. I used my download of the alternate iso and the installation was pretty fast. Wubi works as promised – Ubuntu was installed on windows partition and gives me access to my win files (docs, music etc). I still have some issues but they are Ubuntu related (i.e., still trying to disable the double tap on my synaptics, hard to install the Greek spell checker etc)...however  the wubi worked perfectly! Great work and thanks!

PS Sorry for my poor English

---

### Post by minhmeoke on 2007-08-06
> porcorosso: I do have a question, though, and I'm not sure if it's an Ubuntu question or a Wubi question. My reading in the forums here has led me to believe that invoking use of the restricted drivers for my nVidia video subsystem through the Restricted Drivers Manager in Ubuntu 7.04 should have installed the nvidia-settings application automatically.

This is a confirmed general Ubuntu (not Wubi) bug which is caused by the fact that the nvidia-settings package is obsolete, since its functionality has already been integrated into the nvidia-glx that you have installed:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/72979]("https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/72979")

What do you need the nvidia-settings package for? I encountered this issue when I was trying to integrate nvidia gpu temperature monitoring into the gnome-sensors-applet. A solution can be found at [https://bugs.launchpad.net/debian/+bug/59945]("https://bugs.launchpad.net/debian/+bug/59945"), see the post by Jason Fergus, although it may involve downgrading the nvidia drivers. Good luck.

---

### Post by porcorosso on 2007-08-07
> **minhmeoke said:**
> This is a confirmed general Ubuntu (not Wubi) bug which is caused by the fact that the nvidia-settings package is obsolete, since its functionality has already been integrated into the nvidia-glx that you have installed:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/72979]("https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/72979")

What do you need the nvidia-settings package for? I encountered this issue when I was trying to integrate nvidia gpu temperature monitoring into the gnome-sensors-applet. A solution can be found at [https://bugs.launchpad.net/debian/+bug/59945]("https://bugs.launchpad.net/debian/+bug/59945"), see the post by Jason Fergus, although it may involve downgrading the nvidia drivers. Good luck.

Thank you for this information.

I should explain that I was only trying to use nvidia-settings because I had read elsewhere here in the forums that this applet was what gives one access to the OpenGL and multiple monitor features of the hardware. (I have a Quadro GO 1400 on my notebook.)

The first time I used the RDM to install the drivers for the video subsystem I wound up being unable to find nvidia-settings. I installed nvidia-settings via the Synaptic package manager and lost Xserver after trying to use the applet to set up the system to use the notebook's built-in LCD and an external one connected through DVI from a port replicator.

I was able to resurrect the system by purging the drivers and editing the configuration, but I started over with a clean system anyway because I wanted to be sure I was starting with a clean slate. (I'm new to Linux.)

On the second installation the nvidia-settings applet appeared to have been installed automatically for me when I ran the RDM. But using the applet once again caused Xserver to fail to start. The applet appeared to be kind of buggy anyway. The driver worked flawlessly on the single built-in LCD until I attached the second monitor or until I fiddled with nvidia-settings. The VESA driver works perfectly with the monitors -- using the external monitor when the system is docked, and the internal monitor when undocked -- but it doesn't allow me to use the monitors simultaneously.

Unfortunately, the VESA driver gives me nada for OpenGL support, and I'd like to have that under Ubuntu, if possible.

I know this thread is not supposed to be a troubleshooting thread, and I'll start a thread in the appropriate section. But if anyone has a solution for getting me some OpenGL support with this system without causing Xserver to go bonkers, I'd appreciate hearing about it.

Again, many thanks for your interest.

---

### Post by pferpaddy on 2007-08-08
ok is this normal i have installed every thing and when i get to the boot screen it loads up the boot and says recovering files..ok and so on but when it gets to activating file swapover swap if dosnt move now i didn leave it for that long bbut should i?

---

### Post by ago on 2007-08-09
> **pferpaddy said:**
> ok is this normal i have installed every thing and when i get to the boot screen it loads up the boot and says recovering files..ok and so on but when it gets to activating file swapover swap if dosnt move now i didn leave it for that long bbut should i?

rename c:\wubi\disks\swap.virtual.disk to c:\wubi\disks\noswap.virtual.disk

---

### Post by Daspawnx on 2007-08-09
it's a crap .. I tryed to install it on my laptop 300 times doesn't work

---

### Post by heimo on 2007-08-09
> **Daspawnx said:**
> it's a crap .. I tryed to install it on my laptop 300 times doesn't work

Thanks for your feedback. Next time you may want to include more details, or even file a bug report if necessary. Also you could have tried to get some support from forums before banging your head against wall for 300 times and getting irritated. Your post currently doesn't contain information and it's trollish - not a good way to introduce yourself to discussion forums. Anyway, welcome and try another approach if you're searching for help, it'll be easier for everyone.

---

### Post by vexorian on 2007-08-09
> **Daspawnx said:**
> it's a crap .. I tryed to install it on my laptop 300 times doesn't work
Under that limited experience, It is possible to conclude that either your laptop is crap or wubi is crap, I guess 50%

---

### Post by Daspawnx on 2007-08-09
I think I am just dumb to be honst .. maybe you can help me perhaps .. alright .. it wants me to find /target .. I am sorry about that ..

---

### Post by MetalMusicAddict on 2007-08-10
Don't be an insulting 12 year-old. Try asking questions instead of being rude.

---

### Post by Daspawnx on 2007-08-10
lol funny  joke .. I got it working .. .really funny you should become a comdian .

---

### Post by ubromtoo on 2007-08-12
Wubi has made Windows inaccessible :confused:

    After running a dual boot Dapper/Win XP Home SP2 setup for several months, and using XP less and less often, 
I heard about Wubi and used it to very smoothly and easily install Feisty - Wubi seemed like a great idea, for about two weeks.

     
     Then I got an error message saying Feisty was running out of disc space - not true at all, but I went into XP and defragged , hoping that would take care of things.

      Right after that, while in Feisty, I clicked on the red-and-white "quit" icon, and both toolbars disappeared !  Being a computer newbie, I didn't know what else to do but hold down the power button for several seconds, to shut down the pc.

       Now, Dapper is available and works fine, but when I try to start up Windows or Feisty, the computer simply reboots. The Windows Recovery thing is available, but using that will wipe out Dapper & Windows ,and I'd have to start all over again.  The option to "press C for command line" still works - any suggestions ?


     For me , this is a fairly serious mess ](*,)[-o<           Help will be most appreciated [-o<[-o<[-o<

---

### Post by DeadSuperHero on 2007-08-13
Wubi's pretty good, but it had a number of problems on my comp.
-A number of applications could not update on the GNOME Desktop, including the hal. libc6 had dependancy errors that made it impossible to install AAC codecs. The hal somehow wasn't working correctly during a few of the installs. 
Then I tried Kubuntu, and had a lot of problems simply customizing it. Themes I installed would not work, kbfx themes didn't work, SuperKaramba crashed, I couldn't even install nvidia drivers properly through the command line.
So it has a ways to go, I think.

---

### Post by porcorosso on 2007-08-13
> **ubromtoo said:**
> Wubi has made Windows inaccessible :confused:

    After running a dual boot Dapper/Win XP Home SP2 setup for several months, and using XP less and less often, 
I heard about Wubi and used it to very smoothly and easily install Feisty - Wubi seemed like a great idea, for about two weeks.

     
     Then I got an error message saying Feisty was running out of disc space - not true at all, but I went into XP and defragged , hoping that would take care of things.

      Right after that, while in Feisty, I clicked on the red-and-white "quit" icon, and both toolbars disappeared !  Being a computer newbie, I didn't know what else to do but hold down the power button for several seconds, to shut down the pc.

       Now, Dapper is available and works fine, but when I try to start up Windows or Feisty, the computer simply reboots. The Windows Recovery thing is available, but using that will wipe out Dapper & Windows ,and I'd have to start all over again.  The option to "press C for command line" still works - any suggestions ?


     For me , this is a fairly serious mess ](*,)[-o<           Help will be most appreciated [-o<[-o<[-o<

I'm pretty new, at both Wubi and Linux, so I may not be of much help. But I think the information you've given might point at something other than Wubi (or something other than JUST Wubi) being at fault here.

Apparently after you installed Wubi on a system that was already dual booting (using GRUB as the boot loader?) the system was functioning okay -- at least in the beginning.

I find that impressive, in and of itself. Am I correct in assuming that, when you booted this dual - dual - boot system you got GRUB first, and it gave you a choice between Dapper and "Windows"? And then, if you chose Windows, you'd get the Windows boot loader which, in turn, gave you a choice between WinXP and Feisty?

It seems like it would be pretty easy to break a process like that if one wasn't pretty careful.

I'm concerned about the fact that Feisty was telling you that it was running out of disk space. You said that wasn't true. How is it that you ascertained that? As I said, I'm new to this. I find this whole loop-back file system with the virtual disks for home / swap / system to be a little confusing. How do you go about assuring yourself that you're not running out of space on any of those virtual disks?

Anyway, you got this apparently bogus message from Feisty telling you that you were short of disk space. Offhand I would think you'd have to do something about that from within Feisty, since Windows doesn't have any method I know of for getting into those files (the virtual disks) and fixing anything.

But you ran a defragmentation from within WinXP, and the system still booted up okay and let you get into Feisty, right? And it was after a hard shutdown (pushing and holding the power button) that you found yourself unable to reboot into Windows or Feisty? That, right there, seems like reason to suspect that drive corruption, perhaps of the Windows boot loader, may have happened prior to or during that hard shutdown.

That could very well implicate Wubi, if I understand how this works, because Wubi does alter the Windows boot menu -- though what it would have been doing to it while you were up and running in Feisty is beyond me.

But it could also just indicate some other problem, to my mind more likely with Feisty than with Wubi.

I wish I knew more about Wubi and Feisty. I'm just putting this message up because I'm hoping it might help you think of something you might do to restore functionality. If this is nothing more than a borked menu.lst file you may be able to fix that by accessing the Windows XP system partition from your Dapper installation, using an NTFS driver, if that's the format of that partition.

With any luck someone with some knowledge about this may be able to help you out.

Good luck!

---

### Post by porcorosso on 2007-08-13
> **Mr. Psychopath said:**
> Wubi's pretty good, but it had a number of problems on my comp.
-A number of applications could not update on the GNOME Desktop, including the hal. libc6 had dependancy errors that made it impossible to install AAC codecs. The hal somehow wasn't working correctly during a few of the installs. 
Then I tried Kubuntu, and had a lot of problems simply customizing it. Themes I installed would not work, kbfx themes didn't work, SuperKaramba crashed, I couldn't even install nvidia drivers properly through the command line.
So it has a ways to go, I think.

I'm afraid I'm beginning to sound like an apologist for Wubi. I'm not.

But there are people who have recently run into a problem with the HAL not initializing following a recent update to various HAL modules. I'm wondering if this could have anything to do with your problems?

In my case, on a notebook system, I lost my wireless connection (which had worked perfectly out-of-the-box) and the HAL stopped initializing after this recent HAL update. I was unable to fix the problem until I went intothe  Synaptics package manager and forced the earlier version of four modules and the removal of one module. Then I locked the four reverted modules to the earlier version until I hear something, one way or another.

I just thought I would mention this as another possibility, in case it could be helpful to you.

I've run into a couple of thorny problems with Feisty -- mostly having to do with trying to get the blasted binary drivers to work on my nVidia FX GO 1400 video subsystem -- but have had an excellent experience with Wubi, in and of itself.

I would think that the most likely point of failure for Wubi would be the boot loading sequence and the loop-back file system / virtual disks. I'm not sure how it could affect the HAL at all, since the only emulation is of disks, not of machines.

Obviously, being very new to this and not particularly bright in the first place, I could be wrong.

:)

---

### Post by ubromtoo on 2007-08-13
Porcorosso :

     When the system is started up, first there is a blue HP screen with three options : 
    
                       ESC = boot menu , F1 = setup (Bios,apparently)  F10 = System recovery        

If I just wait, then a second screen appears :  GNU GRUB version 0.97  which gives me choices of :

                        Ubuntu, kernel 2.6.15-28-386 (Dapper)
                        Ubuntu, kernel 2.6.15-28-386 recovery
                        Windows XP
                        Windows XP recovery

This  second screen also says press "e" to edit commands before booting, press "c" to bring up a Command-Line.

     Clicking on "Windows" causes a third  screen to show up, one which looks basically the same as the second, but offers 

choices of Windows , Windows Recovery , and Feisty .  Text at the bottom of of the screen says "For troubleshooting and 

Advanced Startup options for Windows, press F8 ".  Pressing F8 gives all these options :

                            Safe Mode
                            Safe Mode with Networking
                            Safe Mode with Command Prompt
                            Enable boot logging     
                            Enable VGA Mode
                            Last Known Good Configuration
                            Directory Services Restore Mode (Windows Domain controller only)
                            Debugging Mode
                            Disable automatic restart on system failure
                            Start Windows Normally
                            Reboot
                            Return to OS Choices Menu

        I've tried all of the above : the last two do just what they say, the rest simply return me to the third screen (i.e. 

Windows, Windows Recovery, Feisty ).


        How do I know that Feisty was not running out of disk space ?  Well , I opted to give it 15 GB during installation

with Wubi, and I just haven't used much file space , because Wubi/Feisty is a new thing for me, an experiment basically.

        Thanks for your comments and questions , Porcorosso .

	Despite this rather serious problem, let me say that Wubi is very, very interesting and promising, and that Ubuntu

is a marvelous tool for learning for an old duffer computer newbie such as myself .

	I want my Win XP back  for a few select uses, but for general usage, Ubuntu is much superior to XP.

---

### Post by porcorosso on 2007-08-13
Well, ubromtoo, I'm thinking that doesn't look very bad at all. I'll bet that one of the Wubi experts here will be able to help you troubleshoot from this point forward. To me it sounds as though all that's wrong is that the menu system for Wubi has been confused by something. I guess that it's also possible that the choices to which the menu system points -- namely Windows XP and Feisty -- have been hosed. But it seems more like this is going to be fairly easy to solve -- for someone who knows his you-know-what from his elbow. (That wouldn't be me when it comes to Wubi or Linux.)

I'm hoping one of the regulars will pop up here and give you a hand. I'd be very interested to see what's going on here.

---

### Post by redmonster13 on 2007-08-14
Wubi is a wonderful way to learn about linux. I had it installed and managed to get compiz-fusin working and learned about using linux a bit. Now somehow I have managed to kill itto the point that linux wont boot no matter what I try.

I think my completely full hard drive is at fault here, so I have ordered a new hdd and will be migrating wondows to the 300g hdd and putting a normal  ubuntu install on the 120g drive.

---

### Post by ago on 2007-08-14
> **ubromtoo said:**
> 
If I just wait, then a second screen appears :  GNU GRUB version 0.97  which gives me choices of :
That is not installed by wubi, but by the standard Ubuntu installer

>  Clicking on "Windows" causes a third  screen to show up, one which looks basically the same as the second, but offers 
This one is installed by wubi.

As mentioned elsewhere you may want to run chkdsk /f

> How do I know that Feisty was not running out of disk space ?  Well , I opted to give it 15 GB during installation
df command

---

### Post by AcworthJack on 2007-08-15
I see this thread is some what old - but I just wanted to add my 2 cents - Wubi is Great!

It is very easy to install (and reinstall) it gives great performance! Best of all, you have complete access to all of your Windows XP files right from within Ubuntu!

I did run into 1 problem with my RealTek network card and the "boot on lan" problem with Windows XP.  This turned out to be an easy fix but it took me amost a week to find the right document on the web.  :(

Overall - I am a huge fan of Wubi - especially as a "gateway drug" to full Linux.  :)

Thanks Wubi folks,
John

---

### Post by roguetrick on 2007-08-17
I tried wubi out on my mother's laptop that I'm borrowing as the dvd-rom drive is broken and I don't feel like weirding her out by repartitioning and forcing her to use GRUB.

It runs horrendously slow compared to the snappiness of XP, however this may be an Ubuntu problem and not a wubi problem(as I haven't and will not attempt to dual boot it).

When I say horrendously slow by the way, I mean firefox takes 2 minutes or so to load and the Update Manager as well as Synaptic refused to do anything but sit and load for me.

With my new computer coming tomorrow, I threw in the towel for now, but I promise to test wubi again soon.  I hope it'll be something I can help my friends install to get a taste of linux.

---

### Post by AcworthJack on 2007-08-17
> **roguetrick said:**
> I tried wubi out on my mother's laptop that I'm borrowing as the dvd-rom drive is broken and I don't feel like weirding her out by repartitioning and forcing her to use GRUB.

It runs horrendously slow compared to the snappiness of XP, however this may be an Ubuntu problem and not a wubi problem(as I haven't and will not attempt to dual boot it).

When I say horrendously slow by the way, I mean firefox takes 2 minutes or so to load and the Update Manager as well as Synaptic refused to do anything but sit and load for me.

With my new computer coming tomorrow, I threw in the towel for now, but I promise to test wubi again soon.  I hope it'll be something I can help my friends install to get a taste of linux.

Sounds like you may have hit one of the networking issues - this can manifest itself several ways including very slow web performance.  You may want to search the newbie or networking areas - or put a post there.  Be sure to include the output from ifconfig -a.  This doesn't sound like a Wubi issue to me.. good luck with the new PC.

---

### Post by porcorosso on 2007-08-19
In the continuing spirit of providing feedback on Wubi:

I learned that Wubi, apparently, interferes materially with the Linux HAL. I noticed, when I got around to looking at Power Management, that there were no sleep or hibernation options available. A quick look at the FAQ at the Wubi site confirmed that Wubi doesn't support sleep or hibernation.

That makes sense. You can get into a peck of trouble hibernating one OS on a dual boot system and then booting the other OS instead of closing the hibernated OS down properly. In Wubi's case with the loopback system and its Ubuntu "partitons" running on virtual disks which actually reside as files on an ntfs drive, it would probably be suicidal to try to suppport hibernation or sleep.

The one that got me, though, was when I enabled the backport repositories and updated the HAL. It whacked my Ubuntu's HAL (wouldn't load) and network connectivity. I was able to recover easily enough by reverting the HAL to the previous version and locking the version in Synaptic Package Manager so that I wouldn't accidentally update the HAL again.

In the end, because it was time to proceed further with Ubuntu I removed the Wubi installation and went to a standard dual boot configuration with Vista on my first drive and Feisty Fawn on the second drive. That settled the hibernation  / sleep and HAL update issues.

I'm very grateful to the Wubi folks for their software. It made it possible for me to do an initial evaluation of Ubuntu with no worries. (I was totally new to Linux, and didn't wish to replace the Windows boot loader with GRUB until I learned something about the OS.)

It's an outstanding idea, and a wonderful implementation. I do think, however, that it would be a very good idea to provide a right-up-front-in-your-eyes warning for prospective users to let them know about the HAL issues. That's especially true if Wubi is to become one of the officially supported installation methods for Ubuntu.

It's really no hardship to someone like me to not have sleep or hibernation available. But the HAL update / whacked network configuration was a bit of a wakeup.

---

### Post by Patrick793 on 2007-08-20
Okay. Here is my feedback on Wubi.

I love it. Wubi is one of the best things ever! Before I found this, I was stuck using a live CD. Reason: My sister likes windows to much, and I didn't want to mess with partions.
Wubi is awesome. I don't mind that there are no sleep or hibernate options, I don't use those anyway.
But yeah. Wubi rocks!

---

### Post by hh93 on 2007-08-22
I Love Wubi, only took me 2 days to decide to install feisty fawn to a real partition, albeit it took me twice as much time to successfully migrate it. My 2 cents below are in comparing Wubi Ubuntu to windows, i've never used any other version of linux before)

Remarkable superiority  :
- Most importantly, stability, never crashed on me, even with beryl and 3D Cube.
- Ability to extract information from windows; this assured ubuntu ability to connect to my home wireless network and wired network at work without configuring anything (love it !) 
- Speed and responsiveness : definitely faster than windows for comparable task, a lot more responsive: ubuntu installed into real partition is more superior though.
- lower user priviledge and security, this is perhaps the biggest hassle, not because of the system; due to us windows user too accustomed to being an administrator. I recalled being accustomed to  a limited priviledge user for everyday use  and an administrator account  for  software installation. The inflexibility of having to re-login for administrator account, though, for everything not working with limited user priviledge, was very discouraging: I'm not sure if MS has a workaround to this. Ubuntu however,  has a limited user privilegde as a default, but, with an ability to become administrator with the use of terminal; this make ubuntu secure and flexible at the same time. (No driveby install! yippy)
- Installation is smooth except for the limitation of space to 4 GB (for my system). Setting space beyond 4GB resulted in failure of installation; a bug that has been discussed somewhere else ([http://ubuntuforums.org/archive/index.php/t-422427.html](http://ubuntuforums.org/archive/index.php/t-422427.html))
- Productivity and entertainment software that come along with it. (love it)
- Simple update and add/remove software.
- Since i've migrated ubuntu to a real partition, i can attest that all the setting Wubi extracted from windows were transfered completely, to a more speedy and responsive system. 
- And .... it's free!
 
Needed application and support:
- Adobe Acrobate equivalent, love to be able to pdf from anywhere: no need printing (not aware if this is available yet)
- Hibernation support (definitely desireable)

Great job and two thumbs up for Ago and the Wubi team!

hh93

---

### Post by porcorosso on 2007-08-22
I'm curious. What was the file system of the Windows system onto which you tried in vain to install Wubi with a size allowance greater than 4 gigs -- ntfs or fat32?

---

### Post by hh93 on 2007-08-22
> **porcorosso said:**
> I'm curious. What was the file system of the Windows system onto which you tried in vain to install Wubi with a size allowance greater than 4 gigs -- ntfs or fat32?

Supposed the question was for me; It was XP Home with FAT 32

---

### Post by porcorosso on 2007-08-22
> **hh93 said:**
> Supposed the question was for me; It was XP Home with FAT 32

Okay, that would probably be the reason why Wubi couldn't succeed with the installation. FAT32 has pretty severe limits on the sizes of individual files. You see, Wubi has to set up its emulated partitions or disks as large files within the Windows partition. It was trying to create files that were too large for the FAT32 file system to support when its size was set larger. Once you dropped below a certain size for the Wubi installation you were golden.

It's not a bug in Wubi, it's just a characteristic of the FAT32 file system that was causing the failure. It would probably be good for the Wubi installer to give a would-be user installing to FAT32 a warning about this.

---

### Post by hh93 on 2007-08-22
off course ....

thanks porcoroso.

---

### Post by porcorosso on 2007-08-22
> **hh93 said:**
> off course ....

thanks porcoroso.

You're most welcome.

I think that *buntu is a terrific distribution for those of us who are just getting around to investigating Linux. And Wubi is a truly easy way for someone who doesn't want to have to fiddle around with a non-Windows boot loader and repartitioning to gain an introduction to *buntu.

Like you, I've gone on to a "regular" installation of Ubuntu. Now, if only I can get the nVidia drivers to work properly with my dual monitor setup on this notebook...

It's like an adventure game, I tell ya!

;)

---

### Post by ubromtoo on 2007-08-23
Went ahead and re-installed Win XP ....and immediately down-

loaded and burned a BartPE disc .

     By the way, using the recovery console (dedicated partitions , did

not have Windows XP boot discs) did not wipe out my Dapper like I

thought it would ...noobie speaking here...

     Sure wish the good folks at Wubi would have warned me about

Wubi's sensitivity to a hard powerdown.  But , I'm back in the saddle

and headed for Wubiland once more.

      Wubi is such a great idea , it's bound to help lots of folks

migrate to Ubuntu  :):):)

---

### Post by ago on 2007-08-23
> **ubromtoo said:**
> 
     Sure wish the good folks at Wubi would have warned me about

Wubi's sensitivity to a hard powerdown.  

We did...

[http://wubi-installer.org/faq.php#requirements](http://wubi-installer.org/faq.php#requirements)

> Any gotcha?
Hibernation/suspend is not supported under Wubi, _moreover Wubi filesystem is more vulnerable to hardreboots (unplugging the power) than a normal filesystem, so try to avoid unplugging the power_. These problems, however, are no longer present once the Ubuntu install created by Wubi has been transferred to a dedicated partition using LVPM.

---

### Post by ubromtoo on 2007-08-23
Ago :

   This is me,   :oops:   embarrased and apologizing.


You're quite right, you did give warning.  Please accept my apology

and my thanks for your help  and your work.

---

### Post by Schowie on 2007-08-25
Hi,
I wanted to try it - but after the installation and then starting up in Ubuntu it appeared, that it could not find my keyboard - so I was unable to type username!
I has also been a little concerned when reading about people after a "kill" of the PC being unable to boot again. But I have read somewhere, that you plan to make a USB/external HD version too, that would be very interesting?
I like Ubuntu (have it already on a separate old Laptop and it works great), but I found the idea with Wubi excellent for a dual-boot version on my desktop - so please keep on!!
:KS

---

### Post by ev5unleash1 on 2007-08-25
Yea, I got an old Laptop Hardrive and got a case for it to hook up to the computer. I wanted to install Ubuntu and I thought Wubi would be the easiest way because I've used it and others have used it many times before. But when I tried to install it externally everytime I booted I got the error message something Sdb or something about 3 times then it stopped.

---

### Post by Baneat on 2007-08-25
Doesn't work. Goes to a blank blue screen and does absolutely nothing (8+hours)

---

### Post by Baneat on 2007-08-25
You know after trying it for the 299th time you didnt ever consider trying to change something in the way you do it? it didn't work the last time, likely won't work the next:lolflag:

---

### Post by raycosm on 2007-08-25
Aww come on, it's awesome. What kind of laptop do you have?

---

### Post by por100pre1 on 2007-08-26
This thread is crap.
:lolflag:

EDIT: I posted this for a thread called "Wubi is crap". It was moved to the Wubi feedback thread. I don't have anything against the feedback thread or against Wubi!

---

### Post by Dark Star on 2007-08-26
What kinda j/k is this ? :x btw Wubi is not crap its way ou treat it.. you act silly you get pised :p I got it working in 3 of my frnds computer now even my frnds can install ubuntu via Wubi :)

---

### Post by tuxcantfly on 2007-08-26
merging thread into Wubi feedback since the poster is providing feedback rather than asking for support

---

### Post by sc0ri0n on 2007-08-28
It's been an hour and it's stuck at downloading it.I already had the 7.04.iso and I had installed Ubuntu using this iso a couple of times but it would not accept it. Looking at the documentation I realized that I need the alternate version. I looked at C:\wubi\install\ubuntu-7.04-alternate-i386.iso.metalink file to see from where I can download it and used one of the links in US. 

I downloaded that and copied it to the same folder where the executable was (a network location), then installation went thru. Unfortunately, it deleted the .iso so when I tried to run it for a different machine, it again wanted to download the .iso ...

I love the idea and hope it works well. I am still not sure why it could not find any sites to download alternate version though...

---

### Post by ago on 2007-08-28
> **sc0ri0n said:**
> I downloaded that and copied it to the same folder where the executable was (a network location), then installation went thru. Unfortunately, it deleted the .iso so when I tried to run it for a different machine, it again wanted to download the .iso ...
It's not deleted, it has been moved to c:\wubi\install
The reason why the download is sometimes slow is that the mirror at the moment is choosen at random, hence your luck may vary. We are well aware that there are better ways of choosing  a mirror and Hampus is working on a segmented downloader, but it's not ready yet.

---

### Post by sc0ri0n on 2007-08-28
You are right! I too noticed that it was moved to local drive from the network location I originally stored it. 

I am guessing that, it is moved so that when I reboot the machine, installation can access the image. It may make sense to copy it in case of a network share I guess.

Thanks for quick reply!

---

### Post by bcarteruk on 2007-08-28
Just a quick thanks - I have installed WUBI on 2 machines now - unfortunately neither succeeded 1st time - but after a bit of googling, I did eventually get both working.

WUBI was driven by the need to install Linux on my Sons laptop for his University work - I was more than a bit annoyed to find that the DELL Vostro I had bought him for Uni ships with 4 partitions already set up and in use... (Tools, Recovery, Vista, DirectMedia)... Leaving no room for a straight Ubuntu install.  

WUBI was the only solution, without blowing out the recovery or tools partition, so I tried it out on my XP desktop before risking the new laptops VISTA setup.

As for the problems...
On my desktop...
1) My own fault trying to install >4Gb on FAT (RTFM)
2) UBUNTU went black screen on 1st X load , it had set the Refresh rate to 61Hz which is not supported by my monitor, (but luckily is by my TV)  so I had to hack the X config back to vesa and 60HZ , then manually install the ATI Video drivers.  

On the Laptop 
3) WUBI hung when installing 15GB on NTFS , so I reverted to 4GB for the initial install. 
4) UBUNTU falied to start X when installing, it was trying to load an Nvidia driver that did not support the latest 8600GM video card in the Dell (hack back to vesa and then downloaded the latest beta drivers)
5) GNOME repeatedly hung when running rysnc in a terminal when I was trying to grow the system partition back to a larger file.  So eventually I made a copy of the sytem partition file and copied that one using the command prompt without gnome running.  (The following day the guide was change to point to LVPM for doing this , but I could find nothing in the LPVM docs to tell me how)

So WUBI was a must for me that really does work, Well Done !

...  But the entire experience certainly strained my brain.  The only Linux experience I have was an AIX admin course and that was 14 years ago !  I can understand real newbies getting very frustrated and giving up.

---

### Post by thebigfatgeek on 2007-08-28
> **Baneat said:**
> Doesn't work. Goes to a blank blue screen and does absolutely nothing (8+hours)

I have three PC's at home, XP Pro, XP Home, MCE 2005 with all of them running WUBI without a problem. It works great for me, and is dead easy.

---

### Post by tuxcantfly on 2007-08-28
> GNOME repeatedly hung when running rysnc in a terminal when I was trying to grow the system partition back to a larger file. So eventually I made a copy of the sytem partition file and copied that one using the command prompt without gnome running. (The following day the guide was change to point to LVPM for doing this , but I could find nothing in the LPVM docs to tell me how)

if the rsync didn't work, then LVPM won't work either (FYI to try with LVPM, you just install the package and run it, and the GUI will handle the rest (there's a resize option); shouldn't be too complex.). However, if GNOME is hanging, maybe try the old rsync instructions and before running them, just go to a terminal and kill gnome (sudo killall gdm), then see if they run properly from the terminal.

---

### Post by tuxcantfly on 2007-08-28
> 5) GNOME repeatedly hung when running rysnc in a terminal when I was trying to grow the system partition back to a larger file. So eventually I made a copy of the sytem partition file and copied that one using the command prompt without gnome running. (The following day the guide was change to point to LVPM for doing this , but I could find nothing in the LPVM docs to tell me how)

sorry, forgot to update the LVPM docs/guide with the new instructions, check there again, site is at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) (the resizing bit is towards the end)

---

### Post by Yizi on 2007-08-29
I think its a usefull software, keep up everyone! specially the maker :P

---

### Post by -SpaZ on 2007-08-29
I've messed around with it a little bit and it looks great.  I can't wait for the final release to come out.

---

### Post by bigern75 on 2007-08-30
Works great!! Keep up the good work. :guitar:

---

### Post by abhilash82 on 2007-08-31
Wubi worked great for me initially but my Ubuntu started slowing down a lot and my swap would get full most of the time. So I did a complete install on a dedicated ext3/swap partitions. I would recommend the wubi installer to have some more customizable features with respect to your disk access.

---

### Post by Dave Crowhurst on 2007-08-31
I just installed Ubuntu using Wubi. I now have a working dual boot Vista/Ubuntu system. 

Cheers :)

---

### Post by bcarteruk on 2007-08-31
> **tuxcantfly said:**
> if the rsync didn't work, then LVPM won't work either (FYI to try with LVPM, you just install the package and run it, and the GUI will handle the rest (there's a resize option); shouldn't be too complex.). However, if GNOME is hanging, maybe try the old rsync instructions and before running them, just go to a terminal and kill gnome (sudo killall gdm), then see if they run properly from the terminal.

That is basically what I did - killed gnome and then used the old rsync commands without the excludes, but I had mounted a copy of the system  rather than the working one.

Once again thanks for the great work - I would have been stuck without you !

---

### Post by vektek on 2007-09-03
good idea but doesn't work

---

### Post by ubromtoo on 2007-09-03
Vektek :

   It is a great idea which DOES work ; remember that it is still in 

Beta, and is still being worked on.  =D>

---

### Post by vektek on 2007-09-04
ok sorry.... perhaps i should have said it doesn't work for me (it almost worked) . thanks for the effort

---

### Post by AxL456 on 2007-09-12
hi..

well i'm new in this ubuntu world, the installation with wubi went just fine, the only problem y get was the keyboard config that came with the US config (i'm form venezuela)

but everything else perfect :) ..

see you later, i'll be around here reading (may not post so much, i'm not good writting in inglish) to know more about ubuntu, thank for the forum and all the information =D>:biggrin:

):P
P.D:excuse my poor inglish knowleged :lolflag:

---

### Post by TimJBart on 2007-09-12
I think the tool is a brilliant idea.  

My only complaint is that I cannot specify where to get the ubuntu alternate ISO on my hard drive, rather than downloading it again.  the download has gone very slow.

---

### Post by ago on 2007-09-12
> **TimJBart said:**
> I think the tool is a brilliant idea.  

My only complaint is that I cannot specify where to get the ubuntu alternate ISO on my hard drive, rather than downloading it again.  the download has gone very slow.

The answer is: put the iso in the same folder where you have wubi.exe

---

### Post by 3KWA on 2007-09-12
Absolutely brilliant.

For months I struggled trying to install Ubuntu on my new desktop (HP Slimline  bought January 2007) without any luck.

Wubi comes along and WHOW! at long last I don't have to use Windows XP anymore!

Keep up the good work, I believe you have a keeper ;)

Cheers,

EuGeNe -- [http://www.3kwa.com](http://www.3kwa.com)

---

### Post by seiserres on 2007-09-19
Congratulations, Wubi is an excellent idea and sure a propeller for Ubuntu adoption. It works nicely on my laptop hp zd7395ea.

---

### Post by ubromtoo on 2007-09-19
Because of a past difficulty with WUBI/XP caused by a hard

powerdown, I burned a copy of BartPE , and tried to use it to 

run the following command:

     chkdsk /f

      However, the response was :

"The type of the file system is RAW.
 Cannot lock current drive.
 CHKDSK is not available for RAW drives."

    What to do ?  I was told that the problem caused by a hard

powerdown while in Wubi could be cured by the "chkdsk /f" command.

     Thanks for comments.

---

### Post by adromidon on 2007-09-20
I have a Dell 1520 and I am aware Ubuntu requires updateing and installing of nvidia drivers from a comand line at least with a normal install. However when I use Wubi it installs fine but upon loading and shortly after the normal error saying X could not start the computer says it is loading rc.local scripts and it just sits there I have left it here for over 45 minutes and still nothing the computer is not frozen however because hiting the power button intiates a graceful shutdown.

---

### Post by ZenWarrior on 2007-10-01
Pretty much a Linux noob here. However, I have installed Ubuntu before without Wubi and all went well. (Okay, so maybe I'm not your typical noob. I've been using computers continuously in some form since punch card and IBM mainframe days, starting back in 1975.)

That said, I've always said geeks just didn't understand "normal" computer users. What geeks think is easy is a mofo for regular folks. (Yea, I'm sorta a geek, but I don't forget my completely noob days as do most geeks.) 

However, this time the geeks got it 97% right with Wubi. I installed it yesterday on my tower and a laptop. Both installs went perfectly, with Ubuntu on the tower and Kubuntu on the laptop. 

Why only 97% right? The geeks forgot to hide the installation process. That will still scare away any "normal" user. They see arcane commands and immediately assume the worst. (Even Microsoft gets that one.)

Clean up what the user sees during install and boot, and I'm almost certain you'll see more adopters, or at least trials. Never forget that the end user (who isn't a geek) wants only to see pictures. Command line is like a demon from hell for those folks.

That all said, **I absolutely love Wubi**. I'll certainly be recommending it to people with older machines now running Win98 or something (yes, they still exist), but who desperately need a newer OS--but aren't willing to buy a newer computer. I've installed Ubuntu on an old Compaq desktop that runs at 500 MHz, has only a 10 GB hard drive, and you'd never ever guess the hardware under the Ubuntu OS is that dated. The sucker is actually pretty quick. (Okay, I bumped up its RAM to 768 MB. That may be helping a tad, but it's mostly Ubuntu offering the apparent high performance from such an old machine.) 

Keep up the very good work!!! You definitely have a new user here! (Take that, Microsoft!)

---

### Post by ZenWarrior on 2007-10-02
(See my entry above.)

First big problem with Wubi/Ubuntu. Tried to use Second Life after seeing an alpha Linux build there. Ran into what appears to be a known "feature" where  ATI video cards apparently aren't entirely kosher. (One gets an error message about SL not being able to open a window.)

Followed SL instructions to go to the menu/location for support of restricted drivers, saw the entry for ATI and checked to enable it. All appeared well as I was told the driver was enabled and to reboot my system. 

However, on reboot I can no longer get into Ubuntu. The Ubuntu screen with the red-orange logo/bar loads to approx. 25 percent and then everything just stops--leaving me with a blank screen with no option for any input or exit. The only way out is to hold the power button until the computer shuts down. (BTW, have tried 3 times now with the exact same outcome each time.)

And given that, I now seem to be essentially locked out of Wubi/Ubuntu by virtue of having no video. Might one of the illuminated minds here offer a remedy or some advice? Is it possible to get into Ubuntu again or must I completely uninstall? And if the latter, how is that done? From within Win XP MCE? (Sorry, can't remember that part, but will also look it up again. TIA.)

*(Seriously, I hope someone answers ASAP and with a solution. I've have just two days to persuade others with some say in the matter to make a switch to Wubi/Ubuntu for six other computers and leave Windows behind.)*

---

### Post by ZenWarrior on 2007-10-02
Help!!! BIG PROBLEM!

Trying to access my backup hard drive after installing Wubi, I was shocked (to say the least) when I was told the drive contained no data. (Note: This is while in XP.) I can neither read nor write to the drive, but can see two Wubi/Kubuntu files (wubildr and wubildr.mbr). All other folders, which just yesterday contained data, now report as empty.

I am not able to run Check Disk on the volume. It reports simply that Check Disk cannot be started. However...

...maybe there is hope (with some help here, please!). A Properties check of the drive still shows the correct allotments of used and free space. It's as if the data is there, but XP cannot see or access it.

Please, help would be grandly appreciated. I'm holding off doing anything myself (i.e., blindly) until someone here offers advice. TIA.

(Note: Unfortunately, this makes for a significant problem on each of the two computers I installed Wubi. I don't think significant issues suddenly arising around the very same time frame, and after apparently significant changes made by a common program,  is entirely coincidental--but I may be wrong.)

---

### Post by hums07 on 2007-10-06
> **ago said:**
> The answer is: put the iso in the same folder where you have wubi.exe

I tried Wubi on my laptop yesterday and It ran well. However, I had thought that the installer would have asked me where I put my iso, because I didnt find the description (or documentation) that told me that i could put the iso on the same folder. The installer downloaded a new iso while i have already had one. So I think either you should put an option there or you put a description on the Wubi website.

Overall, excellent job to you guys :KS. I write this post from Ubuntu which I installed with Wubi just yesterday.

---

### Post by libr8d on 2007-10-15
Well, hey.

Ok. Just got through a Ubuntu 7.04.04 on a win xp sp 1: Toshiba 133mhz mIII Portege 3500 with 512MB and 16mb onboard Vram.

And, well, 

First off, I've some experience over the years (since the floppy boot days) with Linux (and other *nix flavours) - Ubuntu looks close to what it promises to be....(easy for Windows users to migrate).

The Installation was as simple as I've seen Linux install. No questions.
Took me quite awhile - didn't time it - but I'd say around 1 hr including full download by the installer (at a constant rate of 308kb/s - ;) and the whole install and reboots to the desktop.

The only real hitch I wanted to share was this -

The Hd never stopped working. No matter how much rest I gave the system. The Wubi faq reads :"What is the performance?
The performance is identical to a standard installation, except for hard-disk access which is slightly slower. If your hard disk is very fragmented the performance will degenerate..."


Well the Hd was just deframented and cleaned last night.

Offhand, it wasn't even close to the win xp sp1 install I have (wintablet pc xp) - It works, slower, not as responsive and the Hd works overtime, never stopping - I wonder how long a 2-4 year old laptop can livewith that, and if it can't maybe people should know.

Though Wubi, looks great, and well, wish me luck...

time to uninstall. 

Tnx. :)

---

### Post by PGHammer on 2007-10-17
> **ZenWarrior said:**
> Pretty much a Linux noob here. However, I have installed Ubuntu before without Wubi and all went well. (Okay, so maybe I'm not your typical noob. I've been using computers continuously in some form since punch card and IBM mainframe days, starting back in 1975.)

That said, I've always said geeks just didn't understand "normal" computer users. What geeks think is easy is a mofo for regular folks. (Yea, I'm sorta a geek, but I don't forget my completely noob days as do most geeks.) 

However, this time the geeks got it 97% right with Wubi. I installed it yesterday on my tower and a laptop. Both installs went perfectly, with Ubuntu on the tower and Kubuntu on the laptop. 

Why only 97% right? The geeks forgot to hide the installation process. That will still scare away any "normal" user. They see arcane commands and immediately assume the worst. (Even Microsoft gets that one.)

Clean up what the user sees during install and boot, and I'm almost certain you'll see more adopters, or at least trials. Never forget that the end user (who isn't a geek) wants only to see pictures. Command line is like a demon from hell for those folks.

That all said, **I absolutely love Wubi**. I'll certainly be recommending it to people with older machines now running Win98 or something (yes, they still exist), but who desperately need a newer OS--but aren't willing to buy a newer computer. I've installed Ubuntu on an old Compaq desktop that runs at 500 MHz, has only a 10 GB hard drive, and you'd never ever guess the hardware under the Ubuntu OS is that dated. The sucker is actually pretty quick. (Okay, I bumped up its RAM to 768 MB. That may be helping a tad, but it's mostly Ubuntu offering the apparent high performance from such an old machine.) 

Keep up the very good work!!! You definitely have a new user here! (Take that, Microsoft!)

What absolutely tickles me about Wubi (more than the Windows-based install) is that, because I've used Feisty before (natively) on the same general hardware base, and other than the lack of partition fiddling (which you still have to deal with in terms of a native Linux install, even with Ubuntu and its relatives), there is no real change  Everything is still in the same place, and works the same way (from Update Manager to Synaptic to apt-get, and I've used all three in my Wubi-ized Feisty Fawn).

However, the bane of most newbie users (the partition resizing) is no longer a barrier, or even an issue.

Wubi is a keeper, and I highly recommend it for newbies.

---

### Post by PGHammer on 2007-10-17
> **Dizzy4U said:**
> Ok, I have one question:

I've a laptop with a broken CD-drive. That's why I'll be trying this.

The thing is that I've two partitions: C: (wich has windows and programs) and D: (Wich has all the videos, mp3s, etc).

Is it possible to install linux using just the C: partition in order to delete all windows files? I don't want to loose the info of the D: partition, but i want all the C: partition erased in order to have just linux installed and get rid of all windows stuff.

Thanks in advance.

Why would you?

That's the neat thing about Wubi; given enough free space, you need not delete *anything*.

Just do the install into whatever partition has the largest amount of free space (it need not be C:\).  How the partition is formatted doesn't matter, either (in my case, I'm using an NTFS partition).

---

### Post by PGHammer on 2007-10-18
> **omgDarkWillow said:**
> It's great because I don't have to go through the pain and heartache of partitioning (which I don't know how to do, by the way).:p

Hey; I *do* know how to do it, and I still hate it.  I love Wubi for that reason alone (NOT having to do it).

---

### Post by PGHammer on 2007-10-18
> **ago said:**
> Well with wubi you do get a dual boot configuration. Almost identical to what you would get by installing Ubuntu from LiveCD. The main differences are: 1) no burning of a live CD is required, 2) no partitioning, 3) you can uninstall. For the rest it's a good old dual boot setup.

However, let's tackle those from the top:

1.  No burning of a live CD.  (This is large strictly in terms of saving time and steps.)

2.  No partitioning.  (This is the most painful, in my humble opinion, issue in preparing to install a Linux or UNIX, as in Solaris, distribution the usual way.  With Wubi, this goes away.)

3.  The uninstall option.  Even better, you uninstall from Windows, like any Windows application.  (To be honest, the uninstall is a heck of a lot *cleaner* than that of quite a few Windows applications.)

These three reasons make the process of adding Ubuntu to your OS arsenal as easy as adding Microsoft Office (if not easier) to your Windows application arsenal.  Even better, unlike Office, Wubi-ized Ubuntu is *free*.

---

### Post by VanMuur on 2007-10-18
Hey all,

I've tried Wubi on 3 different systems, 2 Windows XP and 1 Windows Vista. The idea is absolutely incredible, and since I've been searching for a distribution that does this, I'm really happy that it exists. I've been pretty much trying every Linux distribution I can find on VMware Server and Workstation Trial, but it doesn't allow for a root system test. (I.E. a natively running Linux distribution on the system.) 

The only problem is this: My hard disk image that Wubi creates pretty much always gets corrupted. When I shut my system down, I don't have the patience to wait for XP or Vista to completely shut down. Since it always recovers properly with NTFS, I've never had a problem just hitting the power button half way, or most the way through the "Shutting down Windows..." screen. But, Wubi never survives this, so I always have to do a reinstall. 

After working on my laptop's Wubi install to get the video and wireless NIC drivers works (via ndiswrapper), I really didn't want to go through it again.

I might give the Live CD method a try, but it has no persistence, so I'm not exactly sure what to do. I'd love to have a setup that stays, with drivers, wireless, everything. (So both user and system level persistence.) I thought Wubi was the answer, but it appears not to be so.

Anyone have any ideas?

---

### Post by captevo on 2007-10-18
Please add support for SafeGuard disk encryption

---

### Post by ago on 2007-10-18
> **VanMuur said:**
> But, Wubi never survives this, so I always have to do a reinstall.
Wubi uses a nested filesystem, in a nested filesystem data loss in the host filesystem == journal loss in the guest filesystem. That happens because when Linux writes recovery data to disk, it in fact handles the data to the windows filesystem which in turn keeps it cache, so linux thinks the data for recovery is safe when it is not. That's not a wubi/linux specific issue. It applies to all nested filesystems. There is no way around that other than avoiding hard reboots. If you want to hardreboot do a normal installation to a dedicated partition, that can survive an hardreboot (not that it is recommended anyway).

---

### Post by ago on 2007-10-18
> **captevo said:**
> Please add support for SafeGuard disk encryption

Quite unlikely for the time being
Of course you can use a separate partition for Ubuntu, and Ubuntu has its own way of using encryption

---

### Post by MSchenker on 2007-10-18
I was on the fence regarding Ubuntu (Kubuntu in my case) and it was Wubi that finally pushed me to install it.  I could never quite understand how to handle the whole partition thing, so if it were not for Wubi, I would have never installed Kubuntu.

But I am now well on the way to dropping Windows completely.  After trying out Wubi, I am liking Kubuntu more and more.

Soon, I may no longer worry about the partition issue.  If I am getting rid of Windows, I'll be able to just let Kubutnu take over my hard drive.

Keep up the great work on Wubi!

Looking forward to getting Wubi on version 7.10!

---

### Post by PGHammer on 2007-10-18
> **MSchenker said:**
> I was on the fence regarding Ubuntu (Kubuntu in my case) and it was Wubi that finally pushed me to install it.  I could never quite understand how to handle the whole partition thing, so if it were not for Wubi, I would have never installed Kubuntu.

But I am now well on the way to dropping Windows completely.  After trying out Wubi, I am liking Kubuntu more and more.

Soon, I may no longer worry about the partition issue.  If I am getting rid of Windows, I'll be able to just let Kubutnu take over my hard drive.

Keep up the great work on Wubi!

Looking forward to getting Wubi on version 7.10!

I see Wubi differently.

Unlike you, I have previous experience with Linux (especially Ubuntu, specifically Feisty Fawn, which Wubi is based on).  However, while I am familiar with partitioning (and re-partitioning, in the case of a dual-boot system), I don't like doing it (the words "necessary evil" come rather painfully to mind).

Wubi puts a stake through the heart of that necessary evil, banishing it into the "things you used to have to do" category.

I installed Wubi within my production Vista Ultimate, and it runs like a charm; in fact, it runs no differently than a native Feisty Fawn would on the same hardware.  Even better, everything I'm familiar with from Feisty Fawn is present and accounted for, and works the same way.

I expect to be dual-booting Windows (either x86 or x64) and Linux for the foreseeable future, and that is *entirely* due to Wubi.  Unlike some, I don't see open-source as (at this point) a real adversary to Windows (primarily because of the typical *necessary evils* that are present in traditional Linux distributions installed traditionally).  However, given that premise, why should human beings (especially those that run Windows, which is still over seventy-five percent of the marketplace, and that figure is deliberately low) deal with avoidable evils when Wubi exists?

I'm waiting eagerly the transition of Wubi to 7.10, and it's addition to the packaged-CD/ISO distribution listing.

---

### Post by PGHammer on 2007-10-18
> **ago said:**
> Wubi uses a nested filesystem, in a nested filesystem data loss in the host filesystem == journal loss in the guest filesystem. That happens because when Linux writes recovery data to disk, it in fact handles the data to the windows filesystem which in turn keeps it cache, so linux thinks the data for recovery is safe when it is not. That's not a wubi/linux specific issue. It applies to all nested filesystems. There is no way around that other than avoiding hard reboots. If you want to hardreboot do a normal installation to a dedicated partition, that can survive an hardreboot (not that it is recommended anyway).

Even then (with ext3 or NTFS), there are issues when you have a system hang (and that's without throwing a nested filesystem, such as the one Wubi creates, into the mix).  I had exactly this issue less than an hour ago; to solve it, I let Windows (Vista Ultimate x86) boot to its login screen, then selected Restart from there.  This let NTFS (and the nested filesystem from Wubi) recover, and solved the problem.

For this reason, if you *are* going to run a product that uses a nested filesystem (such as Wubi, or even BeOS 5 Personal Edition for Windows, which also uses a nested filesystem), I recommend installing to an NTFS partition, because of how well it recovers from such issues (much better than any form of FAT) not to mention the sheer volume *size* advantages (starting with NTFS 5, which launches with Windows 2000 Professional/Server  the ceiling partition size is two terabytes [2TB}, and they *still* don't make hard disks for PCs that big!).

---

### Post by ago on 2007-10-19
> **PGHammer said:**
> Even then (with ext3 or NTFS), there are issues when you have a system hang (and that's without throwing a nested filesystem, such as the one Wubi creates, into the mix).
There is a big difference. Journaled non-nested file systems can be recovered (that's why you have a journal). Since the data loss due to hard reboots does not affect the journal. BUT data loss in a host filesystem destroys the guest filesystem journal, and recovering without a journal in place is not very fun.... That happens whatever filesystem you use. So even if you had ntfs inside ntfs, after a hard reboot, you will be able to recover the host filesystem but you risk loosing all the nested filesystem data.

As for filesystems, I'd pick ext3 over ntfs every day of the year... :P

---

### Post by PGHammer on 2007-10-19
> **ago said:**
> There is a big difference. Journaled non-nested file systems can be recovered (that's why you have a journal). Since the data loss due to hard reboots does not affect the journal. BUT data loss in a host filesystem destroys the guest filesystem journal, and recovering without a journal in place is not very fun.... That happens whatever filesystem you use. So even if you had ntfs inside ntfs, after a hard reboot, you will be able to recover the host filesystem but you risk loosing all the nested filesystem data.

As for filesystems, I'd pick ext3 over ntfs every day of the year... :P

You're also more familiar with ext3 than NTFS, correct?

Also, NTFS (especially NTFS 5 and later, which appeared first in Windows 2000) is a lot closer to ext2 than FAT32 is (what differences are there between ext3 and ext2 *other* than journaling?).


I was speaking more about the *Windows* underpinnings, as opposed to those of Linux; when I've run Linux natively, I *always* opt for ext3 whenever possible (and that goes back to my early days with RH 7.2).  If you're going to run Windows bare-metal, whenever possible, cut the FAT from your OS diet.

Yes; Linux has ext3; however, Windows can't even *read* that.

---

### Post by nicus on 2007-10-19
I just want to thank you for that great program. I wasnt sure to install ubuntu on my new thinkpad t61. i needed WinXP Pro for my school but wanted to learn some things on unix but keep the important dates on my XP.

Now i installed the Wubi Beta for Gutsy Gibbons and everything works perfect! I just had some problems with my graphics card. But with a workaround i got the nvidia drivers to work. 

To cut a long story short, i love your program! =D>
keep it up!

---

### Post by willem1933 on 2007-10-22
I have three "problems" with WUBI. 

One is the broken download I tried from Belgium, probably because of a bad connection I have (instead of the 4MB promised, only 852Kb delivered. That will then probably improve from one of the future versions afterwards.

Number two is that after I downloaded the appr. 700 MB and then trying to run it, I received the message that the file was corrupted. So it was not stopped when it went wrong. I had this problem three times, then I stopped trying.

I suppose that if my provider cannot improve his/her performance, this sort of problem will remain.

Number three is not really a problem but a suggestion. I also work in Africa, where broadband is not often available or never available. Downloading a file of appr. 700 MB is then illusionary, as the internet connection often drops out. Moreover, with a modem speed of less than 28 Kb it will cost a fortune to download, if you succeed at all. I requested and received CD-ROMs from Canonical. To make it possible for people in Africa to test and get acquainted with Linux, I would like to suggest making a wubi program that can make use of either a CD version or a downloaded version that can use the Canonical CD-Roms.

---

### Post by ago on 2007-10-22
> **willem1933 said:**
> I have three "problems" with WUBI. 

One is the broken download I tried from Belgium, probably because of a bad connection I have (instead of the 4MB promised, only 852Kb delivered. That will then probably improve from one of the future versions afterwards.

Number two is that after I downloaded the appr. 700 MB and then trying to run it, I received the message that the file was corrupted. So it was not stopped when it went wrong. I had this problem three times, then I stopped trying.

I suppose that if my provider cannot improve his/her performance, this sort of problem will remain.

Number three is not really a problem but a suggestion. I also work in Africa, where broadband is not often available or never available. Downloading a file of appr. 700 MB is then illusionary, as the internet connection often drops out. Moreover, with a modem speed of less than 28 Kb it will cost a fortune to download, if you succeed at all. I requested and received CD-ROMs from Canonical. To make it possible for people in Africa to test and get acquainted with Linux, I would like to suggest making a wubi program that can make use of either a CD version or a downloaded version that can use the Canonical CD-Roms.

Re downloads: you can use your preferred download manager to grab the ISO and simply place the ISO in the same folder where you have Wubi. Hampus Wessman is working to improve the built-in downloader, and the new one should be much faster and more robust.

Re physical CDs: they are already supported by the latest version of Wubi (7.10 rev358+). The feature has not been tested though but hopefully it should work.

---

### Post by JeTDoG on 2007-10-28
My experiences with Wubi:

Overall, a fantastic, no-risk introduction to the Ubuntu Linux OS. A few problems of note:

At some point (perhaps related to a kernel update, since that was the only substantive change I noticed over 90+ days of running Wubi), my system (a Toshiba Satellite A105-S2712 laptop with 512MB RAM, 1.73Ghz Pentium M, 60GB HD) lost the ability to "wake" from a screen-blanked state, but only after being in that state for an extended period of time, i.e., if I walked away from the system for a couple of hours, the screen saver would kick on, then the system would blank the screen after a period of time, and any mouse/keyboard activity would wake it up, but if the inactivity period were longer (say about 8 hours) any attempt to wake the system might generate a cursor arrow, but the screen would not recover, and my only choice was to restart XWindows -- the funny thing is, when I first installed Wubi, it used to work

Inability to properly shut down the system (not that I typically shut it down that often). I would get error messages (the specifics of which I don't currently recall) that seemed to relate to inability to properly dismount my NTFS partition. Only choice was to power off without completing shutdown (never a good thing in Linux).

Certain applications (such as Amarok and OpenOffice) were slow enough to be just about unusable.

All this being said, I was convinced enough by my experience to take the leap and convert my virtual partition based install to a real install via GParted and LVPM. Once I had my NTFS partition carved into a new home for Ubuntu, the conversion went flawlessly, and I haven't looked back since I did it a couple of days ago. My built-in wireless was configuration-free from the get-go (even under Wubi -- I'm currently writing this from a local coffee shop with free WiFi), built-in sound works fine (although I have an ongoing problem with Audacity being unable to play MP3's, but that's a minor issue), streaming video quality is excellent, DVDs play without issue, and the speed increase I've noticed on the real install vs. virtual is substantial. All applications are totally usable (including the aforementioned Amarok and OpenOffice).

Long story short, as far as Wubi is concerned - mission accomplished, you've got another full-time Linux convert. I'll probably blow away my NTFS partition within the next 90 days... buh-bye Mssrs. Gates & Ballmer....

---

### Post by dbclinton on 2007-11-01
I'm absolutely thrilled with this project and very grateful that you are putting this kind of time into helping us out!
Does Wubi allow me to download and install the server edition of Edubuntu (I want to convert my family's LAN to thin clients) or, if it doesn't, can I "upgrade" the desktop Edubuntu to a server after it's downloaded?
Thanks so much!

---

### Post by VanMuur on 2007-11-02
Wubi is an incredible piece of engineering. I've been following UMSDOS and looprooted installs for ages.

One of the main reason for my interest in these types of installations is that I'm usually unable to repartition my hard disk for one reason or another. Also, XP and Vista are usually very sensitive to their partitions being changed out from under them. PC-based partitioning is also very static. I've partition 10gb off for a Linux installation in the past only to find out that a) I don't use it or b) its too much/not enough space.

Wubi definitely allows me to test directly on the platform rather than some type of virtualized environment, where access to some hardware is impossible (E.G. wireless network cards, 3d graphics, etc.) Plus, of course, virtualized speeds are slower.

The only problem I have with the whole Wubi installation is the fragile nature of the disk images. Now, saying that, I've also read all the documentation regarding the nature of the disk images, and how they're susceptible to unplanned reboots (due to disk caching, sometimes not all data gets written, etc.) But, Vista being what it is, I often have to do a hard reboot to get out of a locked state. The other issue I've had is that occasionally, I've attempted to start Wubi only to find that it hangs forever and then sends me to an "initramfs" prompt. After booting it with a nosplash option, I find out its attempting to boot up on the /media/host/wubi/install/install.virtual.disk disk image, which was long since deleted after I installed it. Would there be any plausible reason why it thinks it needs to do an install boot *after* its been installed and used for quite a while? If there is some temporary file thats telling it needs to boot that way, is there any way I can remove it? After about 2-3 reboots (Both into Vista and Wubi), the issue usually clears up, and I can get back into my Wubi "partitions" again.

Lastly, speaking of "partitions" (of course, I mean virtual disk image partitions, not real ones), is there any way to be a little more granular in the "partition" setup? I know that the installer is meant to be *very* simple, but occasionally, I don't want a 500mb /home or swap partition, and just want one big huge 5gb root partition. Is this possible through some type of "advanced partition" button? 

Otherwise, I love the software, I use it constantly, keep up the good work!

Ian

---

### Post by ago on 2007-11-02
> **VanMuur said:**
> But, Vista being what it is, I often have to do a hard reboot to get out of a locked state.
If you do that it would be a good idea to run chkdsk

> The other issue I've had is that occasionally, I've attempted to start Wubi only to find that it hangs forever and then sends me to an "initramfs" prompt.
That might be due to a filesystem corruption, but the mechanism is quite different in 7.10 anyway.

> Lastly, speaking of "partitions" (of course, I mean virtual disk image partitions, not real ones), is there any way to be a little more granular in the "partition" setup? I know that the installer is meant to be *very* simple, but occasionally, I don't want a 500mb /home or swap partition, and just want one big huge 5gb root partition. Is this possible through some type of "advanced partition" button? 
It is fairly easy to do. Just replace the disk image files with a file of the appropriate size before rebooting, there are several tools for generating contiguous large files.

---

### Post by VanMuur on 2007-11-02
> **ago said:**
> It is fairly easy to do. Just replace the disk image files with a file of the appropriate size before rebooting, there are several tools for generating contiguous large files.

OK, so in otherwords, treat the disk images like the old raw QEMU disk images that were around a while ago. It makes sense to change the internal Ubuntu /etc/fstab file as well, correct?

---

### Post by Poupaa on 2007-11-09
Hello
Wubi downloaded the .iso all right and installed everything well (that's what I thought, but when I try to boot on Ubuntu, I get this screen :

  > Booting 'Ubuntu'
  (hd 0,0)
  File system is ntfs, partition type 0x7
  [Linux-bzImage, setup=0x1c00, size=0x1a82cc]
  [Linux-initrd @ 0x1885e000, 0x7918a5 bytes]
[   21.534037] .. MP-BIOS bug : 8254 timer not connected to IO-APIC
[   21.712674] Kernel panic - not syncing : IO-APIC + timer doesn't work ! Boot
with apic=debug and send report . Then try booting with the 'noapic' option
[   21.712713]
and my keyboard won't work anymore, so I have to press the reset button. Unable to understand what's going wrong, cause I'm totally new to all this.
Thank you for your help
Poupaa

---

### Post by ago on 2007-11-09
What version are you using? In 7.10 at the countdown press esc and select ACPI workarounds.

---

### Post by Poupaa on 2007-11-09
Thank you for this quick answer !
I'm using v7.04 I found on Wubi's site.
Sorry for my ignorance, but I even don't know when this countdown take place :(
btw, where can I find version 7.10 ?

---

### Post by ago on 2007-11-09
wubi-installer.org/devel/minefield

---

### Post by Poupaa on 2007-11-09
OK, this time ubuntu 7.10 is installed (I think), but by booting, it seems that the 'menu.lst' isn't found

---

### Post by Poupaa on 2007-11-10
I have no 'menu.lst' file in the 'grub' folders. In fact, I have no file at all in these folders !
What can I do ? (except re-installing, what I did 1 dozen times without success .)

---

### Post by SimonLarsen on 2007-11-13
I installed Ubuntu 7.10 through Wubi last night and everything worked perfect. 

I haven't met ONE single problem.

A great thanks to everyone involved in both Ubuntu and Wubi. :)

Though, i did try installing 7.04 with Wubi on my laptop a couple of days ago, where it froze during boot when it got to:
```
[linux-bzImage, setup=0x1c00, size=0x16c98f]
```

EDIT: Sweet! Tried 7.10 on my laptop and it worked close to perfect. 
But on startup, it shows some stuff about swapping and [ok]. cant remeber the exact thing.
it doesnt do that on my desktop computer?

---

### Post by daniel_szollosi-nagy on 2007-12-26
Wubi's virtual partition is great for people that want to dip their toes into Ubuntu, especially if they know enough about Windows to realize how wubi decreases the already low chances of things going catastrophically wrong. I installed Ubuntu the natural way on my home desktop, but did not want to fiddle with the partitioning on my work laptop.

I first installed 7.04 and was going to upgrade it to 7.10 - glad to have read about the issues this would have caused, so I took the alpha wubi installer for 7.10. A clean install of 7.10 went flawlessly, and since this one now uses the desktop ISO instead of alternate, install was fast and easy, no text mode evilness. Shame about the lousy ATI drivers, my X600 is blacklisted and can't use Compiz, but that is hardly wubi's or Ubuntu's fault - I'll have to push the company to buy Nvidia laptops in the future... 

I can also use wubi to evangelize Ubuntu to other Windows users that are afraid of partitioning. For me personally, games have been a showstopper at home, but I see no such needs on work laptop. In fact, my new year's resolution is to only use Ubuntu for work! (And of course there is always XP under virtualbox, should I run into something that I just can't get to work...)

Two thumbs up for the wubi folks!

---

### Post by rw2007 on 2007-12-26
I have a question: I tried to install Wubi on my Toshiba Satellite A55-S1063.  When I restarted my computer, it went straight to XP.  It didn't even give me a black-and-white screen to pick Ubuntu or XP.  I installed it on 8 GB.  My laptop has 256 MB RAM and 28.7 GB HDD.

---

### Post by tad1073 on 2007-12-27
The only problem with the installer is the sites used to install the .iso file. Some sites won't get above 200kbs other will start at 700kbs then drop off to nothing. I have stopped and restarted about 20 times now and am getting realy impatient. As of now I am at 470.1 mb of 696.2mb @ 225 kbs and falling and the .iso file is not being downloaded. In like a lion and out like a lamb. Hell i can't even get the .iso file from the dowmload sites that Ubuntu has listed. i am having the same problem, the download will start at a pretty goog rate then just fall off to nothing.

---

### Post by rw2007 on 2007-12-27
I got Ubuntu installed but I can't get wireless and I need WPA encryption.

---

### Post by ago on 2007-12-27
> **tad1073 said:**
> The only problem with the installer is the sites used to install the .iso file. Some sites won't get above 200kbs other will start at 700kbs then drop off to nothing. I have stopped and restarted about 20 times now and am getting realy impatient. As of now I am at 470.1 mb of 696.2mb @ 225 kbs and falling and the .iso file is not being downloaded. In like a lion and out like a lamb. Hell i can't even get the .iso file from the dowmload sites that Ubuntu has listed. i am having the same problem, the download will start at a pretty goog rate then just fall off to nothing.

You can download the iso using any download manager you want including bittorrent and place the iso into the same folder conatining wubi.exe

---

### Post by tad1073 on 2007-12-28
> **ago said:**
> You can download the iso using any download manager you want including bittorrent and place the iso into the same folder conatining wubi.exe

the problem was that the download was taking to long, then the kb/s wiould fall off to nothing the I would have to stop and restart.

---

### Post by acidburned on 2008-01-01
wubi is a great thing for new linux users.im not new,but i have wubi 7.04 installed and have no problems.please keep this project goig.

---

### Post by allforcarrie on 2008-01-03
I love it!!!! Now all i need is ot get mint running!

---

### Post by Aleph42 on 2008-01-21
Hi, cool project, keep bringing linux to the mass!

my 2 cents on the website's FAQ: change the order of the questions to have the install instructions first; 
that's what beginners will look like, the current first item of the faq is kinda obscure (I mean, what windows users knows the difference between linux and ubuntu ?).
That first item is imortant because the other pages are so simple (which is excellent!) that even beginners will read it.

All items should be reordered to be in descending interest for beginners.

---

### Post by lasbainas on 2008-01-23
I have installed Ubuntu 7.10 with Wubi. It seems to work fine, but when I try to move it to a partition with LVPM I get this message. I am new at linux, so I have no clue what it means

You are running LVPM on a host installation. You must run it on a loopmounted instal

Thanks

---

### Post by ago on 2008-01-24
> **Aleph42 said:**
> Hi, cool project, keep bringing linux to the mass!

my 2 cents on the website's FAQ: change the order of the questions to have the install instructions first; 
that's what beginners will look like, the current first item of the faq is kinda obscure (I mean, what windows users knows the difference between linux and ubuntu ?).
That first item is imortant because the other pages are so simple (which is excellent!) that even beginners will read it.

All items should be reordered to be in descending interest for beginners.

done

---

### Post by tuxcantfly on 2008-01-24
> **lasbainas said:**
> I have installed Ubuntu 7.10 with Wubi. It seems to work fine, but when I try to move it to a partition with LVPM I get this message. I am new at linux, so I have no clue what it means

You are running LVPM on a host installation. You must run it on a loopmounted instal

Thanks

You're probably running the LVPM version designed for 7.04, not 7.10. The 7.10 version is at [http://downloads.sourceforge.net/lubi/lvpm-710-ALPHA_91_all.deb](http://downloads.sourceforge.net/lubi/lvpm-710-ALPHA_91_all.deb)

If you (or anyone else) has any further questions or issues with LVPM, post them at the stickied, main LVPM thread at [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591) since I (the developer of LVPM) subscribe to that thread so I'll be notified whenever someone has an issue with it (therefore I'll be able to provide help sooner and faster). Same applies to Lubi, UNetbootin, and my other projects.

---

### Post by breaking on 2008-02-06
Thank you to the developer(s?) for all the hard work to make Wubi! My laptop doesn't seem to react well to changes to the partitions (I think it has something to do with the Dell MediaDirect partition) so Wubi was exactly what I needed to get linux running on my system. I'm hoping it becomes some kind of standard Windows-based installer for Linux distros because I would like to have Linux Mint on my laptop as well.

Keep up the good work :)

---

### Post by pcloadletter on 2008-02-19
Greetings,

I just thought I would leave some of my thoughts on my recent Wubi experience.

I am a bit of an operating system nut. I love playing with new OSes, and get this terrible urge every couple of months to try a new one.

Linux however, has been one OS that I simply never have gotten along with. It always frustrated me to install programs, the drivers were enfuriating, and the separation between KDE, gnome, enlightenment, etc. always just seemed to make things more complicated than it needed to to be. However, like I said I feel massochistic every few months, and want to try a new OS.

I always come back to Linux first, since it seems like it has the biggest open source following, and I am always hearing fellow geeks sing its praise. I give it a shot now and then, and it always seems to improve over time, but at a fairly slow pace. After I found Wubi and Hardy Heron however, things changed for the better.

First off, I LOVE the Wubi installer. Its simple, its fast, its easy, it works, and most importantly it is non destructive. 

I tried Gusty Gibbon first, but was haivng a number of frustrating driver issues that required me to manually change to the VESA driver, and then wrestle with it to output at the right resolution. Might I add that its more difficult to mess with drivers in linux than it should be?

I was frustrated, and decided to toss it, and while looking around to see if I could use Wubi to install a different version of Linux, with the hopes that my video card might work with that Distro, I found a thread where they were talking about Wubi verions that work with Hardy heron. 

I gave one of those a shot, installed it and everthing worked right away, and you know what, I actually enjoyed my Linux experience. I actually even found myself using it for the majority of the time.. weird.

I instaled the updates, used it for a few days, then some new udpates showed up today. I instaleld them too, and it nuked my install. Now it is given me some goofy command line issues, and I franky hate using the command line when I am not in a GUI, and I have everything backed up, so I figure that I will reinstall it tonight and see if it nukes itself again after some updates. 

I had issues with 3d acceleration and the proprietary drivers in with my x700 mobility and the update nuked my install... but I predict that these features will be fixed with the final release of Hardy Heron, and they are Linux issues not Wubi issues. I think we are on the brink in my opinion of Linux really becomming viable as an everyday OS for basic users like my Mother, Father, and the technophobes of the world. Wubi packaged with this, really makes it easy enough to install that those same people can isntall Ubuntu themselves as well.

I have three requests at this point.

1. One click install of programs.
2. No need to ever see a command line unless you want to.
3. Wubi to be adopted as an offical way of installing Ubuntu.

The one thing I desire to do, which I think is posible, but I have not figured it out because of the fact that Wubi is not a typical install, is to emulate my current Windows install from Ubuntu, and emulate my Ubuntu install from Windows XP. Is that possible? Thoughts?

Wubi is really a wonderful project. Thanks guys.

---

### Post by ago on 2008-02-19
> **pcloadletter said:**
> 
1. One click install of programs.
You have apt/synaptic, quite simply the best package manager in the world, bar none. 
Use Add/Remove or synaptic. That comes with the peace of mind of having all your packages signed and almost impossible to tamper with via spoofing attacks. I am not a big fan of the click-and-pray world of windows...

> **pcloadletter said:**
> 
2. No need to ever see a command line unless you want to.

That is the case these days. You will still find lots people to give you instructions that involve CLI, but that is mostly because it is FAR more conveninent to tell the user to copy/paste a line in the shell than: "Open menu X, select application Y, you should see a dialog, click on the third botton on the right, then the second tab, ...no the one below, now click properties, now, now, now..."

> **pcloadletter said:**
> 
3. Wubi to be adopted as an offical way of installing Ubuntu.

Look in the latest daily ISO ;)

> is to emulate my current Windows install from Ubuntu, and emulate my Ubuntu install from Windows XP. Is that possible? Thoughts?
Not sure what you mean.

---

### Post by w3stfa11 on 2008-02-19
Might be a stupid question, but I just want to make sure. Is it possible to use Compiz in Ubuntu when installing through Wubi?

---

### Post by ago on 2008-02-20
> **w3stfa11 said:**
> Might be a stupid question, but I just want to make sure. Is it possible to use Compiz in Ubuntu when installing through Wubi?

Yes, wubi is identical to a normal installation. Except for: 

1) no suspend/hibernation, 
2) the filesystem is less resilient to power failures, 
3) disk r/w speed is slightly reduced (not noticeable in normal circumstances)

---

### Post by Cadtech68 on 2008-02-26
All I can say is WOW!!! :), I've used the 7.04 version of Wubi for some time now but the Heron version flat out rocks.
The install was super quick and smooth.
Thanks for such an awesome program.:guitar:

---

### Post by nekra on 2008-03-03
In case an update ruins your system, boot back in the former 'kernel', search and repair
broken packages with synaptic, boot back to te latest version and if needed update again.

---

### Post by UJM on 2008-03-11
I've now  tried Wubi on 3 different installs and it's worked flawlessly on each occassion. I expected crashes when running linux from a windows folder, there were none. I also expected it to be laggy compared to a conventional install but I couldn't tell any difference. For ages I've been trying to install and run linux on a Seagate Free Agent external USB drive, and had nothing but problems. I used Wubi, (no partitioning required)  installed Ubuntu 8.04 alpha on the Seagate and it booted and ran perfectly first time around. 

 comments ... 

I use a UK keyboard, the password I entered in the Wubi installer was alpha-numeric and included the # key, this was not a good idea
 when I got to the Ubuntu login screen the password was rejected, I guess because US keyboard  layout is the default,  so I was locked
out of the desktop until I figured this out

-

---

### Post by GoogleBot on 2008-03-13
Thanks for this great program, is the very first time i can use Linux (Ubuntu) along with Windows, in a safe way, and using wireless! :)

---

### Post by FrostiEE on 2008-03-17
Just installed Kubuntu 8.04 with Wubi, it worked great! :)

---

### Post by cwskas on 2008-03-22
I installed on a WinXP without a hitch although it had to use a small (10gb) partition since the original disk is only 40gb.  Took a while, but worked without any problems.

I wish I had the option of choosing to install from a CD (I already had a copy), that would have sped the process up.

Willie

---

### Post by darco on 2008-03-22
This is my second "thanks" to the Wubi Dev (Ago et al). I just installed it on my Toshiba Satellite laptop using the 8.04 version and it of course loaded w/o any probs. WIFI works great!..My first thanks was for my Desktop (HH x64) 
Now I really think that Ubuntu is ready for the masses. Feisty had alot of issues for us noobs and I can only imagine what the next version will bring!
darco

---

### Post by PGHammer on 2008-03-23
I'd used Wubi in the 7.x days, and now tried the newer version (integrated into the 8.04 LTS beta).  Except for some issues with my X1650PRO AGP card (switching to the safe graphical install fixed those) and the fact that my X-Fi XtremeGamer is not supported (yet, but that's not am Ubuntu-specific issue, and is being worked on), it still installs smoothly (and the Update Manager is still a slick piece of work, and works even alongside other apps, such as Firefox).

Ubuntu and Wubi rocks.

---

### Post by richisan on 2008-03-27
I installed Wubi 8.04 on XP no problems. Ubuntu booted up and my Video card, network connection and sound card all worked out of the box. Installed restricted driver and Compiz-fusion to get the Cube spinning. Added a heap of new apps using the package manager and everything was great :)

But... we've had a couple of power cuts over the last 2 days and each time after the PC has lost power, Ubuntu has refused to boot up again necessitating a complete re-install. 

Is there something I can do to make my installation survive future power cuts?

---

### Post by ago on 2008-03-27
> **richisan said:**
> 
Is there something I can do to make my installation survive future power cuts?
chkdsk /r from within windows sometimes fixes things
but if power outages are a frequent event I would suggest to do a proper installation to a dedicated partition, that is far more resilient.

---

### Post by richisan on 2008-03-28
> **ago said:**
> if power outages are a frequent event I would suggest to do a proper installation to a dedicated partition, that is far more resilient.

Thanks - I'll give it a try.

---

### Post by jimgeiser on 2008-03-30
There was a previous answer to this. If you have a bad windows (or any ) shutdown go to Windows and shut down properly. I had a similar thing happen and had to use the menu to get Ubuntu to open.

I am dong a presentation on Ubuntu for our user group and saw a remark about Wubi. I wanted to see how it worked. I tried it and was amazed that it did the installation in 45 minutes. When it finished and I executed it, it hung up on the 6 of 7 page (preferences) and I could only get by it by canceling. Everything works, but I had to manually start email.
One puzzle is that none of Open Office are working. Everything says it  is installed and ready. I even tried to do it from my Windows XP files since I used it in W XP. Any ideas?

---

### Post by ago on 2008-03-31
[https://wiki.ubuntu.com/WubiGuide#head-e4dd73d03cc565bdbdcec46e799f8f73a7b726e0](https://wiki.ubuntu.com/WubiGuide#head-e4dd73d03cc565bdbdcec46e799f8f73a7b726e0)

OO should work, if it does not use the official 8.04 Beta ISO (wubi in this stage uses daily builds).

---

### Post by bluefly on 2008-04-04
I just recently installed Wubi 7.04 (it must have been just a few days before 8.04 came out).  I have had no problems.  Everything works wonderfully.  The only reason I use Ubuntu is for ease in using sshfs to connect to my work computers (which are Mac OSX and Fedora) so that I can work from home.  I'm not doing anything heavy duty, just writing programs and then running them on my remote work computer.  I don't really need a full partition because I don't work from home that often, so this has been perfect.

---

### Post by darthlobo on 2008-05-27
I used the WUBI installer to do my first Linux/Ubuntu install on 8.04 and it will not load.  The installation goes fine, I reboot and post, I get the choice to run Ubuntu or Windows, I select Ubuntu and all I get is a screen that says "...upper memory...".  I can boot into Windows just fine, Ubuntu not so fine.

I'm still searching the forums for an answer to my problem, but so far all of the solutions I have found are not working.

---

### Post by ago on 2008-05-27
> **darthlobo said:**
> I get is a screen that says "...upper memory...".

[https://wiki.ubuntu.com/WubiGuide#head-67ff1616a5875935bb05d22e615fd9eb703d37a3](https://wiki.ubuntu.com/WubiGuide#head-67ff1616a5875935bb05d22e615fd9eb703d37a3)

---

### Post by darthlobo on 2008-05-27
> **ago said:**
> [https://wiki.ubuntu.com/WubiGuide#head-67ff1616a5875935bb05d22e615fd9eb703d37a3](https://wiki.ubuntu.com/WubiGuide#head-67ff1616a5875935bb05d22e615fd9eb703d37a3)

I have all ready tried that, and sadly it has not fixed the problem.  On another forum someone suggested I boot/install directly from the CD and try the install with what ever grub comes with v8.04 .  Does this sound correct?

---

### Post by spankinlisa on 2008-05-28
worked great on my desktop, but doesn't go into ubuntu on my laptop

---

### Post by ago on 2008-05-28
> **darthlobo said:**
> I have all ready tried that, and sadly it has not fixed the problem.  On another forum someone suggested I boot/install directly from the CD and try the install with what ever grub comes with v8.04 .  Does this sound correct?

Yes a full installation will get you a differnt version of grub which might work in your case.

---

### Post by Mander on 2008-05-30
I've been using 8.04 on an Acer Aspire 7520 laptop (1GB memory) and it seems to be fine.  Occasionally things take a long time to happen, but I think this is only when I'm running Java applications (esp. Freemind). Even with all the whizzy effects in Compiz enabled, it's still about a million times faster than Vista on the same machine, even if I turn off all the fancy effects in Windows. I haven't tried to get the wireless working, but the NVidia drivers are working just fine (installed via Envy).  

So far, I'm really happy with it.  Thanks for making it!

---

### Post by torgrot on 2008-06-17
It works well except for one nagging problem with Hardy Heron.  After doing a clean install using wubi, all was well until the first kernel update.  After that kernel update, when I need to restart the computer, it hangs after the screen with the segmented bar is all dark.  If I instead select shutdown it shutsdown.  

I am currently running  2.6.24-19 and cat /proc/cmdline shows 
root=UUID=22CC46F3CC46C0B1 loop=/ubuntu/disks/root.disk ro quiet splash

torgrot

---

### Post by ago on 2008-06-17
> **torgrot said:**
> It works well except for one nagging problem with Hardy Heron.  After doing a clean install using wubi, all was well until the first kernel update.  After that kernel update, when I need to restart the computer, it hangs after the screen with the segmented bar is all dark.  If I instead select shutdown it shutsdown.  

I am currently running  2.6.24-19 and cat /proc/cmdline shows 
root=UUID=22CC46F3CC46C0B1 loop=/ubuntu/disks/root.disk ro quiet splash

torgrot

Do you have more info on what goes wrong? If you boot in recovery mode you should have more info, even more so if you append "debug" as a kernel argument and the look into /tmp.

cat /proc/mounts
cat /proc/partitions 

would also help

---

### Post by ajwak95 on 2008-06-17
I think that this program is really a savior for the Average Joe who has been trying to install ubuntu on Vista for as long as the system has been out. The only thing that I believe to be faulty is the selection of Distro's. I actually think that you should be able to select older versions of Ubuntu like Fiesty and all of the good ones. And another hint: I think that Wubi should be able to gather all windows driver information and be able to use them in Ubuntu so that you don't need NDISwrapper.

---

### Post by binarycortex on 2008-06-17
Wubi is the best thing to happen to Windows in a long time. I used to be a "Tech Support Professional" for MS, and there is still a place in my heart for Windows, but I would rather be in Ubuntu. It has enabled me to work in linux at work on a daily basis without wiping out my laptop (and potentially losing valuable data) and provides the option of running in windows when absolutely necessary (almost never). Also now I can have the 3d desktop I have always wanted (and my coworkers are jealous too). I plan on implementing this at home as well that way my wife can still play her windows games, the best of both worlds.

Thank you Wubi.

Ian

---

### Post by torgrot on 2008-06-18
> **ago said:**
> Do you have more info on what goes wrong? If you boot in recovery mode you should have more info, even more so if you append "debug" as a kernel argument and the look into /tmp.

cat /proc/mounts
cat /proc/partitions 

would also help

This is running under the recover mode:
Here is the cat /proc/mounts 
gtgrot@gtgrot-desktop:~$ cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw,relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
/dev/sdb1 /host fuseblk rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other 0 0
/dev/loop0 / ext3 rw,relatime,errors=remount-ro,data=ordered 0 0
/dev/loop0 /dev/.static/dev ext3 rw,relatime,errors=remount-ro,data=ordered 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.24-19-generic/volatile tmpfs rw,relatime 0 0
tmpfs /dev/shm tmpfs rw,relatime 0 0
devpts /dev/pts devpts rw,relatime 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/sdb1 /boot fuseblk rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other 0 0
securityfs /sys/kernel/security securityfs rw,relatime 0 0
gvfs-fuse-daemon /home/gtgrot/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0

Here is cat /proc/partitions
gtgrot@gtgrot-desktop:~$ cat /proc/partitions
major minor  #blocks  name

   8     0   78125000 sda
   8     1   78116031 sda1
   8    16  488386584 sdb
   8    17  488384001 sdb1
   7     0   28320312 loop0

I will try restarting it now and see if it does.

Well it still hangs there is a failure message from NetworkManager: nm_dbus_signal_device_status_change failed and some other stuff then 
[ 351.503852] restarting 
and then just nothing.  I added the debug to the kernel parameters but I don't know what to look for in /tmp

torgrot

---

### Post by ago on 2008-06-18
logs look fine
in recovery mode try to run the reboot scripts manually

for x in /etc/rc6.d/K*; do
echo $x
sleep 2
[ -x $x ] && x stop
done
for x in /etc/rc6.d/S*; do
echo $x
sleep 2
[ -x $x ] && x start
done

see which one jams, the last one should be S90reboot

---

### Post by torgrot on 2008-06-18
gtgrot@gtgrot-desktop:~$ for x in /etc/rc6.d/K*; do
> echo $x
> sleep 2
> [ -x $x ] && x stop
> done
/etc/rc6.d/K01gdm
bash: x: command not found
/etc/rc6.d/K01usplash
bash: x: command not found
/etc/rc6.d/K16dhcdbd
bash: x: command not found
/etc/rc6.d/K20apport
bash: x: command not found
/etc/rc6.d/K20atieventsd
bash: x: command not found
/etc/rc6.d/K20avahi-daemon
bash: x: command not found
/etc/rc6.d/K25hwclock.sh
bash: x: command not found
/etc/rc6.d/K39ufw
bash: x: command not found
/etc/rc6.d/K50alsa-utils
bash: x: command not found
/etc/rc6.d/K59mountoverflowtmp
bash: x: command not found
/etc/rc6.d/K99laptop-mode
bash: x: command not found
gtgrot@gtgrot-desktop:~$ for x in /etc/rc6.d/S*; do
> echo $x
> sleep 2
> [ -x $x ] && x start
> done
/etc/rc6.d/S01linux-restricted-modules-common
bash: x: command not found
/etc/rc6.d/S15wpa-ifupdown
bash: x: command not found
/etc/rc6.d/S20sendsigs
bash: x: command not found
/etc/rc6.d/S30urandom
bash: x: command not found
/etc/rc6.d/S31umountnfs.sh
bash: x: command not found
/etc/rc6.d/S40umountfs
bash: x: command not found
/etc/rc6.d/S60umountroot
bash: x: command not found
/etc/rc6.d/S90reboot
bash: x: command not found

All I get is this from a terminal  

Is there something else I need to do before trying this?

torgrot

---

### Post by ago on 2008-06-18
ops...

for x in /etc/rc6.d/K*; do
echo $x
sleep 2
[ -x $x ] && [color=red]$[/color]x stop
done
for x in /etc/rc6.d/S*; do
echo $x
sleep 2
[ -x $x ] && [color=red]$[/color]x start
done

---

### Post by torgrot on 2008-06-18
```

gtgrot@gtgrot-desktop:~$ for x in /etc/rc6.d/K*; do
> echo $x
> sleep 2
> [ -x $x ] && $x stop
> done
/etc/rc6.d/K01gdm
 * Stopping GNOME Display Manager...                                     [ OK ] 
/etc/rc6.d/K01usplash
/etc/rc6.d/K16dhcdbd
 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ] 
/etc/rc6.d/K20apport
/etc/rc6.d/K20atieventsd
 * Stopping atieventsd                                                   [ OK ] 
/etc/rc6.d/K20avahi-daemon
 * Stopping Avahi mDNS/DNS-SD Daemon avahi-daemon                               Failed to open PID file: Permission denied
                                                                         [ OK ]
/etc/rc6.d/K25hwclock.sh
 * Saving the system clock
Sorry, only the superuser can change the Hardware Clock.
/etc/rc6.d/K39ufw
 * Stopping firewall: ufw...                                                    iptables v1.3.8: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
iptables v1.3.8: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
iptables v1.3.8: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
iptables v1.3.8: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
iptables v1.3.8: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
FATAL: Error inserting ip6_tables (/lib/modules/2.6.24-19-generic/kernel/net/ipv6/netfilter/ip6_tables.ko): Operation not permitted
ip6tables v1.3.8: can't initialize ip6tables table `filter': Permission denied (you must be root)
Perhaps ip6tables or your kernel needs to be upgraded.
FATAL: Error inserting ip6_tables (/lib/modules/2.6.24-19-generic/kernel/net/ipv6/netfilter/ip6_tables.ko): Operation not permitted
ip6tables v1.3.8: can't initialize ip6tables table `filter': Permission denied (you must be root)
Perhaps ip6tables or your kernel needs to be upgraded.
FATAL: Error inserting ip6_tables (/lib/modules/2.6.24-19-generic/kernel/net/ipv6/netfilter/ip6_tables.ko): Operation not permitted
ip6tables v1.3.8: can't initialize ip6tables table `filter': Permission denied (you must be root)
Perhaps ip6tables or your kernel needs to be upgraded.
FATAL: Error inserting ip6_tables (/lib/modules/2.6.24-19-generic/kernel/net/ipv6/netfilter/ip6_tables.ko): Operation not permitted
ip6tables v1.3.8: can't initialize ip6tables table `filter': Permission denied (you must be root)
Perhaps ip6tables or your kernel needs to be upgraded.
FATAL: Error inserting ip6_tables (/lib/modules/2.6.24-19-generic/kernel/net/ipv6/netfilter/ip6_tables.ko): Operation not permitted
ip6tables v1.3.8: can't initialize ip6tables table `filter': Permission denied (you must be root)
Perhaps ip6tables or your kernel needs to be upgraded.
                                                                         [fail]
/etc/rc6.d/K50alsa-utils
 * Shutting down ALSA...                                                         * warning: 'alsactl store' failed with error message 'alsactl: save_state:1278: Cannot open /var/lib/alsa/asound.state for writing: Permission denied'...                                                                               [fail] 
/etc/rc6.d/K59mountoverflowtmp
 * Unmounting any overflow tmpfs from /tmp...                            [ OK ] 
/etc/rc6.d/K99laptop-mode
gtgrot@gtgrot-desktop:~$ for x in /etc/rc6.d/S*; do
> echo $x
> sleep 2
> [ -x $x ] && $x start
> done
/etc/rc6.d/S01linux-restricted-modules-common
 * Preparing restricted drivers...                                              ld_static: cannot open output file /lib/modules/2.6.24-19-generic/volatile/ath_hal.ko: Permission denied
ld_static: cannot open output file /lib/modules/2.6.24-19-generic/volatile/fcdsl.ko: Permission denied
ld_static: cannot open output file /lib/modules/2.6.24-19-generic/volatile/fcdsl2.ko: Permission denied
ld_static: cannot open output file /lib/modules/2.6.24-19-generic/volatile/fcdslsl.ko: Permission denied
ld_static: cannot open output file /lib/modules/2.6.24-19-generic/volatile/fcdslslusb.ko: Permission denied
ld_static: cannot open output file /lib/modules/2.6.24-19-generic/volatile/fcdslusb.ko: Permission denied
ld_static: cannot open output file /lib/modules/2.6.24-19-generic/volatile/fcdslusb2.ko: Permission denied
ld_static: cannot open output file /lib/modules/2.6.24-19-generic/volatile/fcdslusba.ko: Permission denied
ld_static: cannot open output file /lib/modules/2.6.24-19-generic/volatile/fcpci.ko: Permission denied
ld_static: cannot open output file /lib/modules/2.6.24-19-generic/volatile/fcusb.ko: Permission denied
ld_static: cannot open output file /lib/modules/2.6.24-19-generic/volatile/fglrx.ko: Permission denied
ld_static: cannot open output file /lib/modules/2.6.24-19-generic/volatile/fwlanusb.ko: Permission denied
ld_static: cannot open output file /lib/modules/2.6.24-19-generic/volatile/fxusb.ko: Permission denied
ld_static: cannot open output file /lib/modules/2.6.24-19-generic/volatile/nvidia.ko: Permission denied
ld_static: cannot open output file /lib/modules/2.6.24-19-generic/volatile/nvidia_legacy.ko: Permission denied
ld_static: cannot open output file /lib/modules/2.6.24-19-generic/volatile/nvidia_new.ko: Permission denied
                                                                         [ OK ]
/etc/rc6.d/S15wpa-ifupdown
/etc/rc6.d/S20sendsigs
/etc/rc6.d/S30urandom
cat: /var/lib/urandom/random-seed: Permission denied
rm: cannot remove `/var/lib/urandom/random-seed': Permission denied
/etc/rc6.d/S31umountnfs.sh
/etc/rc6.d/S40umountfs
/etc/rc6.d/S60umountroot
/etc/rc6.d/S90reboot

```

This is the result this time.  It didn't reboot by the way.

torgrot

---

### Post by zhanglini on 2008-06-18
Another thing good about Wubi, I used to have a separate partition for Hardy, it crashed and I reinstalled ~10 times in 10 days.
After that I installed Hardy as an application, it has been running smoothly.

---

### Post by ago on 2008-06-18
that looks good, looks more like an ACPI issue then (kernel), do you boot with any acpi parameter (cat /proc/cmdline)? Can you reboot with older kernels?

---

### Post by torgrot on 2008-06-18
> **ago said:**
> that looks good, looks more like an ACPI issue then (kernel), do you boot with any acpi parameter (cat /proc/cmdline)? Can you reboot with older kernels?


cat /proc/cmdline
root=UUID=22CC46F3CC46C0B1 loop=/ubuntu/disks/root.disk ro single

So no ACPI parameters.  It is a Dell Optiplex 330,  I have had problems with my older Dells and Ubuntu and ACPI and not under WUBI on those computers.

torgrot

---

### Post by ago on 2008-06-18
what kernel version are you using now (uname -r) and can you reboot with older kernels (16)?

---

### Post by torgrot on 2008-06-19
gtgrot@gtgrot-desktop:~$ uname -r
2.6.24-19-generic

I only have 2.6.24-18 and it did it on both of them.  I try to keep the number of kernels down.

torgrot

---

### Post by Trav1s on 2008-06-22
I have used Wubi to install on four different machines without a problem.  All are running Hardy and are different ages of systems...

Toshiba Satellite 1000 (1 ghz celeron/512/20gig HD/CD Burner)
- I plan on using this machine attached to a 320 Gig HD as a file server once I move in July

Dell XPS m1330 laptop (Intel CoreDuo 1.67/2 gig of RAM/160 gig HD/DL DVD burner)
- Machine was shipped with Vista and had problems connecting to any wireless internet. I tried Ubuntu to troubleshoot and determine if it was a Hardware or Software problem

BYOB - Athlon 64 3200 (OC'd to 3450), 1 gig of DDR/Generic 256meg ATI video card, SATA drives
- this is the smoothest install and running system.  

HP Pavillion a22n - installed for friends who were about Ubuntu

---

### Post by Username000 on 2008-06-22
i tryed Wubi 8.04 didnt work good for me i try now the new relase..

---

