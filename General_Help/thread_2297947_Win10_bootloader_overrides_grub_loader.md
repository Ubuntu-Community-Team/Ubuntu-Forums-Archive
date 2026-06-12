---
title: "Win10 bootloader overrides grub loader"
date: 2015-10-07
forum: General Help
---

### Post by gospodorz on 2015-10-07
Hello there,

So i bought new laptop. I installed both Windows 10 and Ubuntu 14.04 LTS (Windows 1st). I also have to mention here that **I am newbie in Linux systems,** I was using only Windows before.

Short history of the problem (may be helpful in solving it):
My problem is described pretty accurately in the title. Firstly I installed Windows. Secondly I installed Ubuntu, setting partitions manually (using top rated answer to this question as guide: [http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)). Firstly I wasn't able to enter Ubuntu at all. Only Windows was aviable (grub didn't appear and couldn't enter it via BIOS boot settings). I asked my brother, who set up dual boot with same systems on his laptop some time ago, for help. And he helped. He entered Ubuntu live usb and did **'some magic'** (that means stuff that I don't fully understand, he mainly used terminal). He made it possible for me to enter Ubuntu via boot menu (when i click F12 i can choose between Windows and Ubuntu). When I won't enter F12 menu, Windows will start loading. When I enter that boot menu, and select Ubuntu, grub will appear. From here i can start ubuntu normally, passing through 2 menus is annyoing though, and here we got the problem.

_I want to get one menu, it doesn't matter if it will be grub or windows bootloader_ (as I saw smn added ubuntu to windows bootloader using this thing: [http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)).

Some info that may be useful:
- I tried to do 'some magic' by myself guided by some googled tutorials before I asked my brother for doing so, but with no effect (but I surely could break something as I didn't really know what was I doing).
- Also I tried using this 'Boot-Repair' thing, also before I passed my laptop to my brother and without effect too(I think he was using boot repair live usb too, when he was fixing it for me, here is link if anyone is wondering whats that boot repair thing: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)).
- In partitioning tutorial I mentioned above I skipped point 7 (tutorial says it's optional), there is something about /boot partition, maybe thats where I made the mistake.

So can u help me get out of this boot crazyness?

If u need some screens or pasta from terminal, just tell me what u need and how to get it. :)

Thanks for help in advance!

---

### Post by oldfred on 2015-10-07
I do not recommend separate /boot partitions for most desktop installs. Full drive LVM or full drive LVM with encryption usually have the separate /boot partition.

What brand/model computer?
Are you booting both Windows & Ubuntu in UEFI boot mode? If UEFI you should not need EasyBCD.

Post link to the summary report from Boot-Repair.

---

### Post by gospodorz on 2015-10-08
My computer brand/model: Acer Aspire V15 Nitro VN7-591G. 
Yes, I am booting both Win and Ubuntu in UEFI mode.
Here is the link to summary from Boot-Repair (I ran it on ubuntu): [http://paste.ubuntu.com/12713936/](http://paste.ubuntu.com/12713936/)
[h=1][/h]

---

### Post by oldfred on 2015-10-08
Acer requires you to create a supervisor password in UEFI and set "trust" on the efi boot files.

       Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)
Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)

---

### Post by gospodorz on 2015-10-08
Thank you very much for answers oldfred! My problem is solved. :)

If anyone in the future will find this topic, here is solution:

Basically acer computers (dunno if all) have specific securitysh things in BIOS, and there lays the problem.
I followed guide from this link: [http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
> [COLOR=#000000]not sure turn off windows fast start-up necessary[/COLOR]
[COLOR=#000000]for sure not necessary disable Secure Boot in bios in my case <a lot of advice stress the importance of this[/COLOR]

[COLOR=#000000]I try to recap my solving (for computer laptop acer E5-571-57H1)[/COLOR]
[COLOR=#000000](after installed xubuntu)[/COLOR]

[COLOR=#000000]turn on and press F2, bios come up (mine called InsydeH20 setup utility rev. 5.0)[/COLOR]
[COLOR=#000000]go to page Security[/COLOR]
[COLOR=#000000]go to "Set Supervisor Password" press ENTER (I set pass "a")[/COLOR]
[COLOR=#000000]go to "Select an UEFI file as trusted for executing:" press ENTER[/COLOR]
[COLOR=#000000]a new page appear with listed:[/COLOR]
[COLOR=#000000]HDD0[/COLOR]
[COLOR=#000000]HDD0[/COLOR]

[COLOR=#000000]press ENTER on the first HDD0 and see if a sub list with the name "<EFI>" comes up (in my case did not show <EFI> but: recycle bin and system volume info)[/COLOR]
[COLOR=#000000]press ENTER on the second HDD0 and see if a sub list with <EFI> comes up (in my case showed <EFI> and <boot-sav>)[/COLOR]
[COLOR=#000000]press ENTER on <EFI>, new list comes[/COLOR]
[COLOR=#000000]press ENTER on<ubuntu>, new list comes with:[/COLOR]
[COLOR=#000000]shimx64.efi[/COLOR]
[COLOR=#000000]grubx64.efi[/COLOR]
[COLOR=#000000]MokManager.efi[/COLOR]

[COLOR=#000000]press enter on each one and give them a for you recognizable name (I used "xubuntushimx64efi", "xubuntugrubx64efi", "xubuntuMokManagerefi")[/COLOR]
[COLOR=#000000]and press Yes[/COLOR]

[COLOR=#000000]save and exit[/COLOR]

[COLOR=#000000]go back in bios f2[/COLOR]

[COLOR=#000000]go to "Set Supervisor Password" and set pass to nill-blank (you want to eliminate a not necessary password that you could forget...)[/COLOR]

[COLOR=#000000]go to "boot page" tab[/COLOR]
[COLOR=#000000]you should find the named shimx64.efi, grubx64.efi, MokManager.efi[/COLOR]
[COLOR=#000000]bring them up in the priority boot list (above windows if you want ubuntu default system)[/COLOR]

[COLOR=#000000]go to page main - enable F12 boot menu[/COLOR]
[COLOR=#000000]save and exit[/COLOR]

Firstly grub didn't appear in 'boot page' tab in BIOS, but after restart it did. Now everything works fine.

Thanks one more time. :)

---

