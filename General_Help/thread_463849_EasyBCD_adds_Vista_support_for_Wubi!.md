---
title: "EasyBCD adds Vista support for Wubi!"
date: 2007-06-04
forum: General Help
---

### Post by Computer Guru on 2007-06-04
**_Using Wubi with Vista via EasyBCD_**
 
**Instructions:**
[LIST=1]
[*]Download the latest version of Wubi and install.
[*]Download [EasyBCD 1.61 BETA]("http://neosmart.net/forums/showthread.php?t=642"), unzip, and install.
[*]Run EasyBCD -> Add/Remove Entries -> Linux/BSD
Select `Wubi` from the drop-down list, give it a name (or keep the default "NeoSmart Linux") and select "Add Entry"
[*]Reboot and test the entry you created.[/LIST]**NB:** It is safe to use this with Wubi already installed. It does not modify or replace any Wubi files.
 
 
---------------------------------------------------------------------------------------------------------------------------------
 
Per ecology and Ago's request, EasyBCD 1.61 will have complete Wubi support for Windows Vista.
 
I have all the infrastructure code in place, but a couple of questions left:
[LIST=1]
[*]Can I simply run a stock GRLDR against the Wubi boot menu found in `/wubi/boot/winboot/menu.lst` of a drive on that PC? Or is Wubi using something special?
[*]Will `/wubi/boot/winboot/menu.lst` always exist?[/LIST]If so, I can have EasyBCD search for `/wubi/boot/winboot/menu.lst` and add a "Wubi" entry to the Vista bootloader that will load `/wubi/boot/winboot/menu.lst` and run its contents.
 
Is this good enough to boot into Wubi? Are there any special circumstances I should be aware of?
 
Note that this bypasses Wubi's GRLDR entirely (not a problem for EasyBCD, it will still be able to parse Wubi's menu.lst - unless Wubi absoloutely needs its copy of GRLDR), does not use or rely on boot.ini and/or ntldr, and will only work on computers that have Vista installed on them (though EasyBCD can run on anything above Windows 98 without a problem, and can install Wubi to the Vista bootloader from there).
 
Any thoughts, suggestions, ideas, etc?
 
If this is all in order, I can have a beta build with Wubi support uploaded for testing even today :)

---

### Post by ago on 2007-06-04
> **Computer Guru said:**
> Per ecology and Ago's request, EasyBCD 1.61 will have complete Wubi support for Windows Vista.

Thanks a lot Computer Guru
 
> [*]Can I simply run a stock GRLDR against the Wubi boot menu found in `/wubi/boot/winboot/menu.lst` of a drive on that PC? Or is Wubi using something special?

You should point to /wubi/boot/**grub**/menu.lst. Our grldr simply embeds a psmenu.lst that calls:

find --set-root --skip-floppies \wubi\boot\grub\menu.lst
configfile \wubi\boot\**grub**\menu.lst

> [*]Will `/wubi/boot/winboot/menu.lst` always exist?[/LIST]
Nope, the menu.lst in winboot is intended to be embedded within grldr and its role is only to point to \wubi\boot\grub\menu.lst
See [https://bugs.launchpad.net/wubi/+bug/116844](https://bugs.launchpad.net/wubi/+bug/116844)

> Is this good enough to boot into Wubi? Are there any special circumstances I should be aware of?
That should be all that is needed. 
 
> Note that this bypasses Wubi's GRLDR entirely (not a problem for EasyBCD, it will still be able to parse Wubi's menu.lst - unless Wubi absoloutely needs its copy of GRLDR), does not use or rely on boot.ini and/or ntldr, and will only work on computers that have Vista installed on them (though EasyBCD can run on anything above Windows 98 without a problem, and can install Wubi to the Vista bootloader from there).
Should be fine

Thanks again

---

### Post by Computer Guru on 2007-06-04
Thanks Ago... Testing it now :)

---

### Post by ago on 2007-06-04
Of course use latest bean123 grldr ;)

---

### Post by Computer Guru on 2007-06-04
Well it worked fine with Bean's GRLDR from May 28... that's the latest, right?
 
If not... /me gets grubmenu back out ;)
 
IF it's the latest I'll upload EasyBCD 1.61 BETA with Wubi support now. If not I'll first switch to the newer grub....

---

### Post by ago on 2007-06-04
[http://ubuntuforums.org/showpost.php?p=2778441&postcount=63](http://ubuntuforums.org/showpost.php?p=2778441&postcount=63)

---

### Post by Computer Guru on 2007-06-04
OK, done :)
 
hopefully this works.
 
It's safe to install this with Wubi already installed, it will not overwrite the Wubi entry in Boot.ini or the BCD, and it won't modify/replace GRLDR or the Wubi menu.lst
 
Please let me know if it works.
 
If you spot any other bugs, post away :D
 
Thanks!

---

### Post by ago on 2007-06-04
Great work! I cannot test it myself, but for all those that have Vista, please give it a spin and provide some feedback!

---

### Post by Computer Guru on 2007-06-04
Thanks Ago,
 
Here's a screenshot:

---

### Post by ago on 2007-06-04
So the instructions are:

1. download and install Wubi
2. download and install EasyBCD
3. use EasyBCD to add Wubi as one of the boot options of Vista

---

### Post by Computer Guru on 2007-06-04
Thanks Ago. I'll update the first post.

---

### Post by Computer Guru on 2007-06-06
Has anyone had a chance to test this yet?

---

### Post by thec00lcat on 2007-06-07
I just installed The lates beta wubi . and everything went smooth !! . the only thing is that when i start up my computer . at the boot menu . there is two ubuntu entries ... 

I installed wubi on drive E . while my vista was on c ( my primary ). 

Note : the EasyBCD entry in bootmenu didn't work . there was ubuntu entry from the wubi installation itself . but the EasyBCD entry which i named something else did not work i forgot the error though sorry . and now uninstalled and everything went back to normal .. 

Now i can exlude my exuse before that linux installation is too hard !!! .

---

### Post by Computer Guru on 2007-06-07
Hi c00lcat,

Glad to hear Wubi worked for you.
Do you think you could get that error message for me?

---

### Post by ago on 2007-06-07
Please try out the latest minefield, it might even work with vista

[http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html)

Do let us know whether it works or not.

---

### Post by Mizarus on 2007-06-17
great news, wubi suport for vista!, i installed it without knowing what would happen and just managed to get back to vista (mannually unistalled wubi by deleting and editing some files) 
when i have some time il try to install using EasyBCD and post back here with some feedback.

edit: wubi install went smooth and pretty fast, the only issue i had is that on the boot menu i had 4 unbutu entry's and none for vista (2normal and 2safect) and for some reason i coudnt get blu beryl effects working but thats probly unrelated

---

### Post by Computer Guru on 2007-06-18
You can add Vista back to the boot menu with EasyBCD in the "Add/Remove Entries" section.

Glad to hear that Wubi installed OK for you though :)

---

### Post by tux_rox on 2007-06-18
Getting a new Vaio with Vista soon - excited to hear that my beloved Wubi will now work on that too.  :)  When it comes, I'll put it on the moment I turn it on.

Keep the updates coming!

---

### Post by Mizarus on 2007-06-18
> **Computer Guru said:**
> You can add Vista back to the boot menu with EasyBCD in the "Add/Remove Entries" section.

Glad to hear that Wubi installed OK for you though :)

do i need to uninstall wubi and install it again to do it? i cant run it on unbutu, ive also tryed to edit menu.lst adding a vista boot to it but when i select it all it does is run Unbutu instead

---

### Post by Computer Guru on 2007-06-19
Nope. Just stick your Vista DVD in the drive, DON'T press anything when it says "press any key to load setup" and let Vista load.

Then do the easybcd thing from within Vista and reboot.

---

### Post by TorontoStorm on 2007-06-28
If I install Wubi and use this method of using EasyBCD to create a Wubi entry in Vista's bootloader, and something goes wrong and I cannot get into Wubi, can i just delete Wubi's virtual drive and remove the Wubi entry in Vista's bootloader to get to where I was before I installed Wubi? Also, I'm current;y using Vista's bootloader to dual-boot between Vista and XP, so can Wubi or EasyBCD screw up anything to do with XP or Vista, like not being able to load either OS?

Thanks for the help in advance

---

### Post by Computer Guru on 2007-06-29
Hi TorontoStorm,

It's perfectly safe :)

I'm not sure ATM what Wub itself does when you install it, but EasyBCD's "Add Wubi" feature is perfectly harmless and 100% reversible :)

---

### Post by ago on 2007-06-29
Yep that should be safe. Wubi does the following:

* creates a new c:\wubi folder, 
* copies 1 or 2 wubildr* files to C:\ 
* adds an entry to your bootloader
* creates a registry entry for the uninstaller

All of the above are undone by using the uninstaller. You can of course remove things manually.

---

### Post by Computer Guru on 2007-06-29
Ago, did you ever pin down the problem with people who said installing Wubi on Vista removed the Vista entry in the BCD?

---

### Post by ago on 2007-06-29
> **Computer Guru said:**
> Ago, did you ever pin down the problem with people who said installing Wubi on Vista removed the Vista entry in the BCD?

Computer Guru, as you know I have no Vista so I cannot do much debugging on that, I haven't seen any bug report from windows vista users in a while though. When did you hear about that?

---

### Post by Computer Guru on 2007-06-29
Just a 2 or 3 posts here in the Wub forums - but nothing in the past two weeks or so :)

---

### Post by tux_rox on 2007-07-02
Hold on - according to the screenshot of EasyBCD posted ([http://ubuntuforums.org/attachment.php?attachmentid=34294&d=1180957875](http://ubuntuforums.org/attachment.php?attachmentid=34294&d=1180957875)), it lists Vista, Feisty, and NeoSmart Linux.  Will all 3 come up at the boot menu?  Sorry if this is a dumb question!

P.S.  Computer Guru, congrats on all of the press recognition - I saw you in that PC World issue :popcorn:

---

### Post by Computer Guru on 2007-07-02
Hey, thanks!
 
No, that's just the list of the dual-boots **I'm** currently running on my machine...  On yours it will only show the OSes *you* add with EasyBCD :)

---

### Post by ago on 2007-07-02
I have to remember to add you to the credits section.

---

### Post by Computer Guru on 2007-07-06
Gee, thanks! :blush:

---

### Post by Jammanuser on 2008-12-10
umm...adding a Wubi entry with EasyBCD 1.7.2 didn't work for me! :( and actually, i'm depending on EasyBCD to get me through now, because when i attempted a dual boot with Windows Vista and XP (Wubi was already installed on Vista)...it seems i screwed things up with not making the partition that i wanted to install XP to active...although i **did** hide the Vista partition, before installing XP! 

to make a long story short, i installed XP on what i **thought** was the correct partition (**my** fault...i saw what XP recognized as "unpartitioned space" although it was actually a partition that i created with BootIT NG...it seems i forgot to make the partition active first, though, so when i went ahead and tried installing XP on the "unpartitioned space" **stupidly**, it installed fine-after a little tweaking and hacking to the BIOS menu-i...umm made another stupid mistake! [-( i tried making the partition that Vista was installed to active with diskpart, instead of rebooting and using BootIt NG to first **unhide** the partition! so what ended up happening after that...well it would take too long to describe it! lets get to the root of the story...), and when i got back into Vista again (after several long hours, trying to figure out the boot problem...during which i rebuilt the "bcdstore" file several times, trying to figure out what was preventing my computer from booting!:mad:), the Vista bootloader had been reinstalled, as a matter of necessity, and so naturally i lost the Wubi boot option that had been previously in my Vista bootloader!

And so my question is: why doesn't the Ubuntu entry that i created with EasyBCD allow me to boot into my Wubi install? I selected the Wubi option in the drop-down menu, btw!

Thanks in advance! :D

-jammanuser

):P

EDIT: could it be due the fact that i used a system restore on my Vista installation, so that i could back into Vista? i remember setting it back to a restore point that i believe to be the 7th of this month...it could be that's a time before i got my Wubi install to work again, after that damn crc error! :-k

EDIT #2: when i try to boot with the Ubuntu entry that i created with EasyBCD, it shows a lot of text, for a few seconds, and then it gets to a place where i can type in commands...

EDIT #3: also, after installing XP, and attempting the startup repair with Vista CD...i noticed a strange thing! it seems like the partition that i installed XP to, is now a logical drive, off of an **extended** partition...instead of the original Primary Partition that i created with BootIt NG! i assume that's probably due to the fact that i didn't have the partition that i was installing to set as "active" though...

---

### Post by Jammanuser on 2008-12-11
Bump. ^

:guitar:

---

### Post by Jammanuser on 2008-12-11
Can anyone help with my problem? ^^

Thanks in advance! :D

Jam Man

:guitar:

---

### Post by Jammanuser on 2008-12-12
Too late...:( i'm already in the process of reinstalling Wubi...again! i put all of my effort into fixing the boot problem, like last time, but it seems like when Wubi screws up (or IS screwed up by a user like me! :)) the only solution is to reinstall it...:(

oh well! at least i think i can replace the root.disk with my backed-up copy, like i did the last time, so that Wubi will be pretty much the same as it was before...files and programs intact! :popcorn:

Cheers! :)

Jamman

:guitar:

---

### Post by Jammanuser on 2008-12-15
Ok...so now trying to use EasyBCD to boot into my **migrated** Ubuntu failed! :( I finished reinstalling Wubi, and then i used LVPM to transfer my Wubi install to a dedicated partition...and since the Grub menu either got overwritten or deactivated somehow, i decided (after editing the menu.lst, thanks to azmo!):P) to try to use EasyBCD to create the needed boot entry for Ubuntu in my Windows bootloader, and hoped it would work! But **unfortunately**...it didn't! :( It seems that i need to know how to get the boot entry created by EasyBCD to point to the correct place...

Hopefully someone can help! (hint, hint) ;)

Jam Man

:guitar:

---

### Post by pawhe955 on 2009-12-17
Another (similar) question re: using EasyBCD fro Wubi:

I have a 3 partition **system** disk (XP-install-1, 'temp' data, XP-install-2) and a **separate** primary user data disk. I have installed Wubi, but with the Windows folders containing the Ubuntu virtual disks on the Data disk. The boot.ini shows a boot entry pointing to "c:\wubildr.mbr="Ubuntu", and there are two wubildr.* files in the root of C: (no wubi* folders...).

Now, I plan to (clean) install Windows7 into the first XP partition, blowing the original XP system (and it's associated system data - e.g. boot.ini, etc.) away. I'm assuming that as it's a clean install, all data will be lost, and Windows7 will not recreate the equivalent of the boot.ini Wubi entry in the new BCD. I've run up EasyBCD (latest - v1.7.2) on a test Windows7 machine, and saw that it allows you to add a Wubi entry, but this points to (a specific NeoSmart or whatever) *ldr.mbr file in a specific directory, and not the "wubildr.mbr" in the root of C:.

As my Wubi installation is in essence entirely (apart from boot pointers) on the Data Drive, it won't be affected when I blat the first partition on the system disk, and to get Wubi back, I (believe that I) just need to get the Wubi boot files in place on C:, and get a correct entry in BCD. I can copy the files back from an Acronis backup that I have (and will do another backup just before installing Win7), but I cannot see a way to manually edit the actual path and file name in the Wubi entry added to the BCD by EasyBCD - can anyone suggest how to edit BCD so I can get the entries to match what was in boot.ini, either within EasyBCD (I may have missed a "manually edit" option?), or use some other tool to edit the BCD Wubi entry, after adding the default one in EasyBCD?

Thanks,

---

