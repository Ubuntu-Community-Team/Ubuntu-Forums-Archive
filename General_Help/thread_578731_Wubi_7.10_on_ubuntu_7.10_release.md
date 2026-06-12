---
title: "Wubi 7.10 on ubuntu 7.10 release?"
date: 2007-10-17
forum: General Help
---

### Post by xray15 on 2007-10-17
Will wubi 7.10 come out on the same day that ubuntu 7.10 comes out?
I have no more cd's to burn :(

---

### Post by ago on 2007-10-17
It will most likely be a few days later than that, and probably it will be an alpha for at least a week

---

### Post by open2linux on 2007-10-17
> **ago said:**
> It will most likely be a few days later than that, and probably it will be an alpha for at least a week

After reading the "Wubi inclusion in Gutsy" topic, I thought that Wubi would come included in the Gutsy CD, so it will be another way to install Ubuntu. From the LiveCD. Was not that the plan?. Now, what is the latest? When Wubi will merge and be part of Ubuntu? In the next Hardy Heron 8.04 ?.

I am asking because I am a big fan of Wubi. I came into Ubuntu thatnks to you people and now I have a real Ubuntu install. But I firt tried Ubuntu thanks to Wubi, Now I don miss any oportunity to talk about Wubi in any forum I participate. And in some Ubuntu sspanish forum I informed - what i thought it true- that the next version of Ubuntu will come already with Wubi.

So when the final merge with Ubuntu willl take place?

---

### Post by ago on 2007-10-17
> **open2linux said:**
> After reading the "Wubi inclusion in Gutsy" topic, I thought that Wubi would come included in the Gutsy CD, so it will be another way to install Ubuntu. From the LiveCD. Was not that the plan?. Now, what is the latest? When Wubi will merge and be part of Ubuntu? In the next Hardy Heron 8.04 ?.

Most of lupin (wubi backend) is already in Gutsy. But we have been blocked by other projects (unionfs in particular) and testing has been very difficult until few days before beta. That was too short time to solve the remaining issues and hence it was decided to only include a limited version of wubi in the LiveCD (wubi-cdboot) which will help people boot a physical CD going around bios issues. We are still in for Hardy as far as the Live CD goes. That said our main strength is the standalone installer which is not strictly linked to the release cycle of the CD. So I'll try to push Wubi as an official stand-alone installer on the main Ubuntu download page even before Hardy. We'll see what happens...

---

### Post by ilogik on 2007-10-18
Will I be able to install ubuntu 7.10 with Wubi, using the 7.10 cd image?

---

### Post by ago on 2007-10-18
> **ilogik said:**
> Will I be able to install ubuntu 7.10 with Wubi, using the 7.10 cd image?

Yes, wubi 7.10 works ONLY with the LIVE CD ISO (use the FINAL version coming out today)... The alternate ISO image is no longer used.

---

### Post by Gordonbp531 on 2007-10-18
> **ago said:**
> Yes, wubi 7.10 works ONLY with the LIVE CD ISO (use the FINAL version coming out today)... The alternate ISO image is no longer used.

I have Wubi 7.04 installed - will I be able to upgrade to 7.10, or is it a question of uninstalling 7.04 and doing a fresh install of 7.10?

---

### Post by Demz on 2007-10-18
> **gendibal said:**
> I have Wubi 7.04 installed - will I be able to upgrade to 7.10, or is it a question of uninstalling 7.04 and doing a fresh install of 7.10?
yes you should be able to to a upgrade from 7.04 to 7.10, search the forums on how to do that

---

### Post by Gordonbp531 on 2007-10-18
> **Demz said:**
> yes you should be able to to a upgrade from 7.04 to 7.10, search the forums on how to do that

I've gone here:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
and followed the instructions - Adept doesn't seem to add the Gutsy repositories.
Is this a Wubi limitation?

---

### Post by ago on 2007-10-18
> **gendibal said:**
> I have Wubi 7.04 installed - will I be able to upgrade to 7.10, or is it a question of uninstalling 7.04 and doing a fresh install of 7.10?

Upgrading wubi is not totally trivial, as mentioned elsewhere I will write a migrations script later on (unless tuxcantfly will beat me to it), but I have to release wubi first as the 7.10 patches are not finalized yet. 

My suggestion though is that you have been using 7.04 and liked it, you should seriously consider to do a proper installation to a dedicated partition using either LVPM or the live CD. You will be able to access the Wubi virtual drives from there and copy over any required file.

---

### Post by linlay on 2007-10-18
Hey guys, hope you can help.

I;m using the latest Wubi minefield, and the Ubuntu 7.10 final release. 
The wubi managed to boot the Ubuntu UI nicely, and it goes into the 'Guided Partion' step of the Ubuntu installation ...then this error pops up:
[B]The filesystem type ntfs cannot be mounted on /. 
(...)
 Please choose a different filesystem like ext2.[/B]

Then the installation will not proceed further no matter what I do ...
I thought that Wubi was supposed to deal with this Ubuntu / NTFS stuff ...

---

### Post by ago on 2007-10-18
There are a couple of things I still have to address. But to do it properly, uninstall any other wubi version, run chkdsk, download the latest build (339), install! 
(your luck may vary ;) )

---

### Post by linlay on 2007-10-18
> **ago said:**
> There are a couple of things I still have to address. But to do it properly, uninstall any other wubi version, run chkdsk, download the latest build (339), install! 
(your luck may vary ;) )

I tried again, but it still didnt work. I hope this will be fixed in the next build of Wubi! :)

---

### Post by ago on 2007-10-18
Post here /var/log/syslog + there should also be another log for partman (do not remember the name on top of my head)

---

### Post by telenut on 2007-10-18
I'm behind a firewall, is it possible that the latest build does not work behind a firewall?
I downloaded the latest RC and placed it in the same folder. (could not find a fast mirror for the final :p )

---

### Post by ago on 2007-10-18
> **telenut said:**
> I'm behind a firewall, is it possible that the latest build does not work behind a firewall?
I downloaded the latest RC and placed it in the same folder. (could not find a fast mirror for the final :p )

rev 339 requires a final. But it should work ok with an rc if you just rename the ISO file...

---

### Post by linlay on 2007-10-18
> **ago said:**
> Post here /var/log/syslog + there should also be another log for partman (do not remember the name on top of my head)


How do I get this log? I dont think i'm able to retrieve this.
Because after the error prompt, i'm not able to do anything ..except restart to Windows. Therefore this log is lost right ?

---

### Post by trevordeen on 2007-10-18
The version of Ubuntu-7.10-alpha.exe that I get from [http://wubi-installer.org/devel/minefields/](http://wubi-installer.org/devel/minefields/) claims its version to be 330, and it appears to be looking for the Gutsy RC. Is version 339 not available yet?

---

### Post by ago on 2007-10-18
Cannot check now, but it should be 339. Try to refresh the page in case you are using your cache.

---

### Post by trevordeen on 2007-10-18
I've refreshed and emptied my cache, still getting 330. I'll check back later for 339, I'm sure its a busy day.

---

### Post by ago on 2007-10-18
Yeah I'll double check later on tonight.

---

### Post by DariusJ on 2007-10-18
Sorry if is a stupid question but where I can find the 7.10 version of Wubi for download?

---

### Post by ago on 2007-10-18
[http://wubi-installer.org/devel/minefields](http://wubi-installer.org/devel/minefields)

it's still an early build though

---

### Post by DariusJ on 2007-10-18
Oh, sorry, I was distracted, until now when I saw the older message with the link.

So, I have a problem, the Wubi 7.10 isn't working with the image of Ubuntu 7.10 in the same folder. I receive an error:

[http://photo.fhost.org/uploads/4af85a705e.gif]("http://photo.fhost.org/uploads/4af85a705e.gif")

---

### Post by MSchenker on 2007-10-18
> **ago said:**
> [http://wubi-installer.org/devel/minefields](http://wubi-installer.org/devel/minefields)

it's still an early build though

Can we hear some more comments from people who have used this early build?  I am currently running Wubi 7.04, but I really like the improvements that are available in 7.10.

Is it good enough to try?

---

### Post by ago on 2007-10-18
Worse case should be that the installer itself crashes or that the installation fails, but that should have no consequence. So trying that out should be ok, since you can always uninstall.

---

### Post by MSchenker on 2007-10-18
> **ago said:**
> Worse case should be that the installer itself crashes or that the installation fails, but that should have no consequence. So trying that out should be ok, since you can always uninstall.

Thanks for the quick response!

Should I completely uninstall the Wubi 7.04 first, or should I just run the Wubi 7.10 alpha without uninstalling the old one?

---

### Post by sichbo on 2007-10-18
> **MSchenker said:**
> Can we hear some more comments from people who have used this early build?  I am currently running Wubi 7.04, but I really like the improvements that are available in 7.10.

Is it good enough to try?

Installs great for me. 

My only regret is that I didn't discover wubi four hours ago! Ever tried installing ubuntu with a dead CD ROM, no bootable USB and no floppy disks in the house? Holy liftin'. By following a guide for editing boot.ini, I had it working up until the point where my NTFS partition failed to resize despite doing chkdsk /f, multiple reboots etc. I near had the big one.

When trying wubi 7.10 alpha, I already had a copy of ubuntu-7.10-desktop-i386.iso kicking around on the network so I canceled the wubi "download" shortly after it started, deleted the incomplete ISO, x-copied the iso off the LAN, then re-run wubi alpha again. Everything worked without a hitch. 

Thanks for your efforts, wubi made my evening.

---

### Post by cnico88 on 2007-10-18
for this Wubi which iso do you need? It attempts to download the x64 verison.

---

### Post by subaqua on 2007-10-19
I tried installing Ubuntu 7.10 with Wubi 7.10.0.340. everything seemed to install ok but when i when i rebooted and i chose Ubuntu in the windows boot loader it just said 

booting Ubuntu 7.10, kernal 2.6.22-14-generic

Filesystem type is ntfs, partition type 0x7
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/hha4 loop=/ubuntu/disks/root.
disk ro quiet spalsh automatic-ubuquity locale=en_AU

Error 17: file not found

Press and key to continue...

anyone know what this might be? I used Wubi with ubuntu 7.04 and everything was fine, but 7.10 is having issues.

---

### Post by alaukik on 2007-10-19
> I tried installing Ubuntu 7.10 with Wubi 7.10.0.340


Where did you get this installer from?

---

### Post by alaukik on 2007-10-19
When i install the Wubi installer from Minefield, the installaton completes in about 10 seconds and asks me to reboot. I know that the installation wasn't done properly, but when i restart, there is some sort of terminal interface, which is obviuosly not the ubuntu gui.

Basically, the installer doesn't download or even ask me to locate the file for the Ubuntu 7.10 ISO. How do i point the alpha installer to the 7.10 ISO?

Please help, i have been trying to follow this thread but can't get anywhere b/c of this.

---

### Post by alaukik on 2007-10-19
**ago** said....

> **ago said:**
> rev 339 requires a final. But it should work ok with an rc if you just rename the ISO file...


What are we supposed to rename the ISO file to?

---

### Post by telenut on 2007-10-19
When I try to install, I notice the software tries to connect to the internet. I have no internetconnection here, so the install goes on. I don't think it will work after I reboot now :-)

---

### Post by alaukik on 2007-10-19
> **telenut said:**
> When I try to install, I notice the software tries to connect to the internet. I have no internetconnection here, so the install goes on. I don't think it will work after I reboot now :-)


I'm not an expert.
That is kinda weird because my wubi 7.10 installer doesn't try to access the internet at all.

What installer did you use? Maybe i can try that one, at least it might work on my computer.

---

### Post by ago on 2007-10-19
> **alaukik said:**
> **ago** said....
What are we supposed to rename the ISO file to?

The name must match the final ISO name...

---

### Post by ago on 2007-10-19
> **telenut said:**
> When I try to install, I notice the software tries to connect to the internet. I have no internetconnection here, so the install goes on. I don't think it will work after I reboot now :-)

Ubuntu tries to connect to the internet to look for updates. It should work nevertheless.

---

### Post by telenut on 2007-10-19
but why is the installer 10 times smaller than the previous one? :-)

---

### Post by ago on 2007-10-19
> **telenut said:**
> but why is the installer 10 times smaller than the previous one? :-)

Mostly because the previous one had our custom kernel and initrd embedded within the installer itself, this one uses the standard kernel/initrd which are extracted from the ISO/CD. On top of it there has been a bit of a cleanup.

But I like the fact that wubi is < 1MB... It takes less bandwidth to send Wubi to a friend than a single screenshot of Ubuntu...

---

### Post by alaukik on 2007-10-19
> **ago said:**
> The name must match the final ISO name...


So then, where is that ISO file supposed to be located relative to the wubi installer. Right now i have the iso "ub'untu-7.10-desktop-i386.iso" in the same folder as "Ubuntu-7.10-alpha.exe" build 340. Yet, it still does the same thing where it installs about 9mb of stuff before it finishes and ubuntu is not even loaded.

Could you please help me out with this

---

### Post by ago on 2007-10-19
Run wubi with "wubi --debug". It will tell you if the ISO is recognized or not.

---

### Post by mckernan.kevin on 2007-10-19
> **ago said:**
> Run wubi with "wubi --debug". It will tell you if the ISO is recognized or not.
I did this, put --debug after the .exe and it popped up "arch=amd64"
My OS is Windows XP Pro SP2 32-bit. I do have an Athlon 64 3400+ processor, but I want the 32 bit ubuntu.

It later said that it recognized the ISO, and that it was valid but then it said that it was the "ubuntu-7.10-desktop-i386.iso" and not "ubuntu-7.10-desktop-amd64.iso"
Then it proceeded to check every ISO that it could find on my hard drive

---

### Post by Hiroshi on 2007-10-19
Question Answered

---

### Post by Hiroshi on 2007-10-19
> **subaqua said:**
> I tried installing Ubuntu 7.10 with Wubi 7.10.0.340. everything seemed to install ok but when i when i rebooted and i chose Ubuntu in the windows boot loader it just said 

booting Ubuntu 7.10, kernal 2.6.22-14-generic

Filesystem type is ntfs, partition type 0x7
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/hha4 loop=/ubuntu/disks/root.
disk ro quiet spalsh automatic-ubuquity locale=en_AU

Error 17: file not found

Press and key to continue...

anyone know what this might be? I used Wubi with ubuntu 7.04 and everything was fine, but 7.10 is having issues.

Sorry for the double post, but I wanted to qoute this, having the same exact problem, and no, upgrading is not an option, I've spent an hour or more doing so only for the installation to get destroyed.

---

### Post by ago on 2007-10-20
> **mckernan.kevin said:**
> 
My OS is Windows XP Pro SP2 32-bit. I do have an Athlon 64 3400+ processor, but I want the 32 bit ubuntu.
If you have athlon 64 then the arch is correct. Later on, you will be able to force 32 bits installs. For now just use 64 bit one via a switch. In fact it works quite well under ubuntu...

>  later said that it recognized the ISO, and that it was valid but then it said that it was the "ubuntu-7.10-desktop-i386.iso" and not "ubuntu-7.10-desktop-amd64.iso"
Then it proceeded to check every ISO that it could find on my hard drive
Ok so the reason is that wubi tries to install the 64 bit.

---

### Post by ago on 2007-10-20
> **Hiroshi said:**
> Sorry for the double post, but I wanted to qoute this, having the same exact problem, and no, upgrading is not an option, I've spent an hour or more doing so only for the installation to get destroyed.

You probably have to edit /ubuntu/disks/boot/grub/menu.lst. Chances are that the line that begins with "root" is not correct.

---

### Post by DariusJ on 2007-10-20
> **linlay said:**
> Hey guys, hope you can help.

I;m using the latest Wubi minefield, and the Ubuntu 7.10 final release. 
The wubi managed to boot the Ubuntu UI nicely, and it goes into the 'Guided Partion' step of the Ubuntu installation ...then this error pops up:
[B]The filesystem type ntfs cannot be mounted on /. 
(...)
 Please choose a different filesystem like ext2.[/B]

Then the installation will not proceed further no matter what I do ...
I thought that Wubi was supposed to deal with this Ubuntu / NTFS stuff ...


Ok, I finally managed to force the install, everything goes well but after the installation on the first boot I receive that error, and I cannot run the installed system.

---

### Post by ago on 2007-10-20
> **DariusJ said:**
> Ok, I finally managed to force the install, everything goes well but after the installation on the first boot I receive that error, and I cannot run the installed system.

ou probably have to edit /ubuntu/disks/boot/grub/menu.lst. Chances are that the line that begins with "root" is not correct.

---

### Post by DariusJ on 2007-10-20
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda7 loop=/ubuntu/disks/root.disk ro quiet splash automatic-ubiquity locale=en_RO
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda7 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)/ubuntu/disks
kernel		/boot/memtest86+.bin

```

I think you talk about this, what I should edit?

Later Edit: I tried replacing hd0,0 with hd0,4 where 4 is the number of the partition where the 'ubuntu' folder is placed but still doesn't work.

---

### Post by ago on 2007-10-20
> **DariusJ said:**
> Later Edit: I tried replacing hd0,0 with hd0,4 where 4 is the number of the partition where the 'ubuntu' folder is placed but still doesn't work.
4th partition on 1st hd would be (hd0,3)

---

### Post by chngej1991 on 2007-10-20
i have download wubi ([http://wubi-installer.org/devel/minefields/Ubuntu-7.10-alpha.exe](http://wubi-installer.org/devel/minefields/Ubuntu-7.10-alpha.exe)) and placed it with ubuntu-7.10-alternate-i386.iso in a folder callled ubuntu. then i launch wubi and after i set the setting i install it. but it seems to download another iso(ubuntu-7.10-desktop-amd64.iso ). i'm using intel pentium D. any idea to solve the problem? Thanks a lot!!!

---

### Post by ago on 2007-10-20
Wubi 7.10 requires the DESKTOP iso not the alternate and it requries one matching your arch. So if you have a 64bit machine (intel or amd) it will use amd64. Later on you will be able to force 32 bit isos by passing: --32bit

---

### Post by DariusJ on 2007-10-20
> **ago said:**
> 4th partition on 1st hd would be (hd0,3)

Nope, it doesn't work, I receive something like that: "No such partition" .. so I suppose that isn't the correct number.

---

### Post by ago on 2007-10-20
> **DariusJ said:**
> Nope, it doesn't work, I receive something like that: "No such partition" .. so I suppose that isn't the correct number.

You can press C or E and then use TAB to show you a list of available options

Or you can try wubi rev347 ([http://wubi-installer.org/devel/minefield/](http://wubi-installer.org/devel/minefield/)) which should hopefully deal with menu.lst automatically.

---

### Post by akotan on 2007-10-20
I'll try not to look so dumb but I did this: downloaded Ubuntu and burned a CD. Can I make a iso of it and rename it as the downloaded Ubuntu? May Wubi work with this new file? Can I use the files from the CD? I have a 32bit AMD PC.

---

### Post by ago on 2007-10-20
Later wubi versions will allow you to work with physical CD, but for now you need an ISO, you can of course extract the ISO from the CD using one of the several tools available.

---

### Post by mckernan.kevin on 2007-10-21
> **ago said:**
> If you have athlon 64 then the arch is correct. Later on, you will be able to force 32 bits installs. For now just use 64 bit one via a switch. In fact it works quite well under ubuntu...


Ok so the reason is that wubi tries to install the 64 bit.
OK, so I let it go through with the 64-bit install.
I boot it up and get the "busy box" full screen terminal.
What happened?
I am going to try reinstalling

@ 11:11PM
Using a --32bit switch works in v.347, I am trying to install again now.

---

### Post by rawr2010 on 2007-10-22
When and where can i get Wubi for 7.10. I think someone said it will be setup on a real partition which I hope is true. Wubi is a great way for people to try linux with little risk or knowledge and I hope to see this project prosper. I've gotten 2 people to switch to Ubuntu in the last month using Wubi first and then using the live cd for a real install. When and where can I get Wubi for the new Gusy Gibbon release? I thought it would be available by now.

---

### Post by A3sthetix on 2007-10-22
> **rawr2010 said:**
> When and where can i get Wubi for 7.10. I think someone said it will be setup on a real partition which I hope is true. 

You should have looked a couple of posts up!
[http://wubi-installer.org/devel/minefield/](http://wubi-installer.org/devel/minefield/)

Only the alpha is available. I'm using it right now -- alpha revision 358. Let's hope Kubuntu works out for me this time! Otherwise, it's back to Ubuntu Studio for me. :popcorn:

---

### Post by ago on 2007-10-22
> **ago said:**
> Later wubi versions will allow you to work with physical CD, but for now you need an ISO, you can of course extract the ISO from the CD using one of the several tools available.
Physical CDs should now be supported

---

### Post by ineedaname on 2007-10-22
What threats do I impose upon my machine if I use the current alpha revision, instead of waiting for a more stable version?

---

### Post by ago on 2007-10-23
> **ineedaname said:**
> What threats do I impose upon my machine if I use the current alpha revision, instead of waiting for a more stable version?

Worse case should be that it does not work and you will have to uninstall (not before reporting here your issues ;) ). As usual you want to avoid hard reboots. If it hangs try: ctrl+alt+f2 (to get a terminal), the ctrl+alt+del (to reboot), then alt+sysrq+REISUB

---

### Post by ineedaname on 2007-10-23
No corruption possible of the existing windows boot loader?

---

### Post by ago on 2007-10-23
If you do not hardreboot no. And if that happens for any reason, you can run chkdsk off the windows CD.

---

### Post by ericesque on 2007-10-23
So what you're saying is we're pretty safe, but as with any partitioning software, we pose some risk of losing data.

I think I'll just back up.  Then I'm at no risk except a bit of time.  I've been waiting for Wubi to become at least beta, but I'm just chompin at the bit to have 7.10 installed.  The live cd works beautifully.

I'll report any errors or issues I encounter.

---

### Post by RandomSkratch on 2007-10-24
> **ago said:**
> ...then alt+sysrq+REISUB

What does that mean? Are those other keys?

---

### Post by ago on 2007-10-24
> **RandomSkratch said:**
> What does that mean? Are those other keys?

Keep down Alt+Sysrq then press R, E, I, S , U, B

---

### Post by Hiroshi on 2007-10-27
Ah nevermind, I see it. Well I don't have that much experience with editing the menu.lst. Especially considering I can't even boot into any GNU portion of linux and being stuck completely with Terminal. It's a safe bet that I'm pretty new with linux, otherwise I would have just installed this regularly, which to for some inexplicable reason, WONT WORK!




Alrighty, after some tweaking, I got 7.10 running nicely with full extra effects using Wubi. No problems so far.

---

### Post by anrichp on 2007-10-27
Hi everyone

I'm kinda new to ubuntu, and need some help I've got the latest version of wubi alpha rev 377 but after i install it and reboot my system , and boot up in ubuntu linux , it has the ubuntu starting screen and then goes to a black window saying something about busybox debian etc.
What do i need to do to get this working?

thnx

---

