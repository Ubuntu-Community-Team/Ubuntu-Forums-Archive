---
title: "Windows 7 won't boot via GRUB"
date: 2014-06-18
forum: General Help
---

### Post by Matthew_Bird on 2014-06-18
Hey all!

I've come to the end of a long process of trying to fix my dual-boot setup. I've had a long hiatus while trying to complete my thesis (and not wanting to risk losing access to my (working) ubuntu install) but now I'm committed to getting this fixed.

I installed Ubuntu on a partition on my otherwise Windows 7 HDD. But I screwed up the install - I think I put GRUB on the Windows partition. The result: when I turned on my PC, GRUB booted. I could select Ubuntu and it'd boot. But if I selected Windows 7 it'd just show me the GRUB screen again.

I researched the problem and found that I'd need to repair my Windows boot loader. I used my Windows installation disk to do this. But oddly, the repair tool told me there were no problems. I did everything I could find to repair the boot loader. Still, the only effect that had was that when I turn on the computer, I'm shown nothing but a blinking cursor. 

Now I've reinstalled GRUB. I can access Ubuntu again, but selecting Windows (which is now listed in Grub as VISTA!(?)) just leads me to a blinking cursor.

Here's the mystery. I think I did manage to re-install the boot-loader. I ran boot-repair from Ubuntu. Here's the paste URL: [http://paste.ubuntu.com/7664721/](http://paste.ubuntu.com/7664721/). If you look under Windows, it does say that the Windows partition has a Windows boot file. 

I've ran out of options - I don't know what else to try. So I'm submitting myself to your expertise. I'll do absolutely everything I'm told as quickly as possible. I really want this fixed - not because I love Windows (switching to Ubuntu has been amazing), but because I can only play the video games I want to play on my Windows partition. Having just finished my thesis, and with only a few days to spare, I'm really eager to get some gaming time in!


EDIT: Just installed and ran testdisk. It says that the boot files and backup boot files for the Windows partitions are 'OK'.

---

### Post by oldfred on 2014-06-18
You never install grub to a NTFS partition's boot sector. But yours now shows as correct and grub2's os-prober finds the Windows install, so no major issues.

I would run chkdsk and repeat the automatic Windows repairs 3 times. That will reinstall a Windows boot loader into the MBR, so you can directly boot Windows. If needed use f8 then to get into Windows repair console. Trying to get f8 to work when booting from grub menu is hit or miss as it is extremely quick Some have said it works if you hit keys almost at same time.
You can use Boot-Repair to reinstall grub's boot loader after you fix Windows or manually reinstall it.

Usually better to have a separate Windows repair disk either CD or flash drive.

Grub really only boots working Windows, so you need to resolve Windows issues and that is usually best from Windows own repair console.

---

### Post by Matthew_Bird on 2014-06-18
Thanks for your reply, Oldfred!

I loaded up the Windows 7 disk and ran CHKDSK. Here's a screenshot of the result, sorry it's poor quality!: [http://i.imgur.com/M62Coz2.jpg](http://i.imgur.com/M62Coz2.jpg)

I then ran Windows automatic repair. I restarted and ran it again. I restarted and ran it again. On the third time it said there were no problems detected.

But I still get nothing but a blinking cursor when I choose Windows (which is incorrectly listed as Windows Vista) on the GRUB screen. Here's a screenshot, just in case that helps: [http://i.imgur.com/dvyAPX9.jpg](http://i.imgur.com/dvyAPX9.jpg)

Any idea what's going on? :O

Thanks again for your help!

---

### Post by oldfred on 2014-06-18
I think you are supposed to run the repair three times while in it before rebooting.
Sometimes you have to rerun chkdsk also.

I did not think there was a difference between the PBR or partition boot sector of Vista & 7. They both use bootmgr to boot. Windows XP does have a different PBR as it uses ntldr to boot and that info is in PBR.
But this says there are differences:
       [http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
    
Not even sure how grub knows the difference between Vista & 7 because it cannot parse the BCD, but that may be a clue to the issue? Are you using  a Window 7 repair disk that is same 32 or 64 bit version?
       [http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

    
Sometimes running command is better than auto fix.
 Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
chkdsk c: /r
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

And perhaps to totally new boot sector with bootsect.exe?

 How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by Matthew_Bird on 2014-06-18
Thanks again!

(You can't run the automatic boot repair three times without restarting, since after running it prompts to restart)

I've been following your instructions. When I try '[COLOR=#000000]BootRec.exe /ScanOs' it says:

[/COLOR]'Successfully scanned Windows Installations.
Total identified Windows installations: 0
The operation completed successfully.'

[S][COLOR=#000000]I guess this is causing my problem? Despite the boot files being intact, it doesn't recognise my installation anymore?[/S]

**EDIT:** I googled the above message, and came across this page. [/COLOR]http://pcsupport.about.com/od/fixtheproblem/ht/rebuild-bcd-store-windows.htm
After following the instructions there, I got it to say that there was a Windows installation present.

But the computer still just boots to that blinking cursor... UGH!

**EDIT 2: **I just ran [COLOR=#000000]bootsect.exe to install a completely new boot sector and I *still *got the flashing cursor on restarting...

I've now tried the above. I don't think this problem is caused by my boot files not working.[/COLOR]

---

### Post by Matthew_Bird on 2014-06-18
I just went here: [http://askubuntu.com/questions/144095/grub-wont-boot-windows-7-after-burg-was-tried](http://askubuntu.com/questions/144095/grub-wont-boot-windows-7-after-burg-was-tried)

I did the following, and now I can boot to Windows! **My only problem is that I have no idea how to make the changes I made permanent. Where is the file that one temporarily changes when one presses 'e' on the GRUB boot screen found, so I can edit it permanently? **

> 

[LIST=1]
[*]Boot to the GRUB menu.
[*]Select the GRUB menu entry Windows 7 (loader) (on /dev/sda1)
[*]Press e to edit the entry's GRUB commands. You should see the commands below.
insmod part_msdos  
insmod ntfs  
set root='(hd0,msdos1)'  
search --no-floppy --fs-uuid --set=root 6060682360680260  
chainloader +1
[*]Edit the commands as shown below to use GRUB's ntldr instead of the chainloader command.**Note:** Changes made to the GRUB boot menu this way are **not** persistant. They apply only to the next boot. *The grub.cfg is **not** changed.*
insmod part_msdos
insmod ntfs
insmod ntldr
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 6060682360680260
ntldr ($root)/bootmgr
Two changes were made to the commands in (3) versus (4).[INDENT]The new command insmod ntldr was added.
The command chainloader +1 was replaced with ntldr ($root)/bootmgr
[/INDENT]
[/LIST]


---

### Post by yancek on 2014-06-18
> **Where is the file that one temporarily changes when one presses 'e' on the GRUB boot scree**

In the situation you are referring to, there is no file changed.  What you want to do is put the entry in the file:  /boot/grub/grub.cfg file or if you are using Ubuntu 13.03, /boot/grub/i386-pc/grub.cfg.  You put a menuentry there.  Sample windows menuentry below.  You should use the parameters you used to boot it and will have to change the set root= line to your partition and the --set=root UUID number on the search line to your uuid for windows.  Get it with sudo blkid. 

> menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root A0A03A5CA03A395C
    chainloader +1
}

After putting your entry in grub.cfg, save the changes (need to use sudo to edit the file) and reboot.  Do not update grub.   If it boots with that entry, copy the windows menuentry entirely to the file:  /etc/default/grub.d/40_custom, save the change and then run sudo update-grub.

---

### Post by oldfred on 2014-06-18
You do not edit grub.cfg. And update or change overwrites grub.cfg. You edit /etc/default/grub or add boot entries yourself into 40_custom.

But you can add your boot stanza to 40_custom and turn off os-prober as it does not really do much if you have manually added a boot stanza. If you add a new system, you can turn it back on later.

       Copy the boot stanza from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy entire boot stanza to and edit to have only entries you want:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

    
New entry will be at bottom of menu. You can change description if you want.

This stops adding the automatic entry which is not working anyway. Once you know your custom entry works then  you can remove the default entry.
       In /etc/default/grub I added this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

---

### Post by Matthew_Bird on 2014-06-19
Thanks to both of you! I'll try this later tonight and report back.

---

### Post by Matthew_Bird on 2014-07-17
Sorry I've been so immensely slow to reply! I've been able to access my Windows partition by editing the GRUB loader for Windows every time I want to boot Windows. This is slightly annoying, but it works, so I'm *very* hesitant to change things and potentially undermine this (albeit imperfect) workaround. 

I want to follow your guide, Oldfred, but first I want to make sure I'm understanding everything correctly. Would you mind making sure I've understood? Sorry to be a pain!

> [COLOR=#000000]Copy the boot stanza from this:[/COLOR]
[COLOR=#000000]sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup[/COLOR]
[COLOR=#000000]gedit /boot/grub/grub.cfg[/COLOR]
[COLOR=#000000]Copy entire boot stanza to and edit to have only entries you want:[/COLOR]
[COLOR=#000000]gksudo gedit /etc/grub.d/40_custom[/COLOR]
[COLOR=#000000]Then do:[/COLOR]
[COLOR=#000000]sudo update-grub[/COLOR]

I enter this in my terminal:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
This will create a backup of my grub.cfg file, in case I mess up.

Then I enter this in my terminal:
gedit /boot/grub/grub.cfg
Which will open grub.cfg in gedit. 
I then copy all of the text here and close gedit.

I then run the following in my terminal:
command:gksudo gedit /etc/grub.d/40_custom
This will open a file - 40_custom - which I imagine will be blank. I paste the code I just copied from grub.cfg and make the edits to it that I normally make when editing the Windows booter in GRUB during startup. I then close gedit.

Then finally I enter the following into my terminal:
sudo update-grub

Now there'll be a new entry in the GRUB loader that I can just select to boot Windows. If I want, I can remove the old broken entry.

Is that right? Have I understood all of the steps? Thanks so much again for all your help (and everyone else who posted here!).

---

### Post by oldfred on 2014-07-17
Yes except you only copy the Windows boot stanza into your current 40_custom. Best to have both edits open at same time or one version is gedit and the other is gedit with admin rights to edit system files.
 Do not remove the couple of lines at the top of your 40_custom. And you should not have to do any edits unless it is a version that is not working. You may want to slightly change menuentry description so you know it is the one you edited as the other is still there.

Be sure to include the last } which is the end of each boot stanza as a separate line.

One script finds the other systems you have installed, but if you manually add the one you want and do not add others, you may avoid confusion by turning off os-prober. With it on you get the os-prober version and your version. If you add another Ubuntu or any other system you can just turn it on then.

 gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit which determines which scripts run.
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

---

### Post by Matthew_Bird on 2014-07-19
Thanks very much for your help and patience, Oldfred. I'm about to try it. I'll report back as soon as I can. Then hopefully we can mark this thread as solved! :-)

---

### Post by Matthew_Bird on 2014-07-19
I did the above and it works perfectly. Now there's a custom Windows 7 boot option in GRUB, and the old Windows 7 boot option no longer shows. Everything is working perfectly. 

I can't thank you enough, OldFred! And thanks to Yancek for your input too! This is a brilliant community :-)


For anyone else facing a similar problem who wants to cut to the chase without reading all of my blundering through OldFred's great advice, here's a quick summary of what I did:

1. I'd tried the usual bootrepair, etc. to no avail.
2. In Grub, I pressed 'e' on my Windows 7 loader, and made the following changes:

```
[COLOR=#000000]*insmod part_msdos*[/COLOR]
[COLOR=#000000]*insmod ntfs*[/COLOR]
[COLOR=#000000]*insmod ntldr*[/COLOR]
[COLOR=#000000]*set root='(hd0,msdos1)'*[/COLOR]
[COLOR=#000000]*search --no-floppy --fs-uuid --set=root 6060682360680260*[/COLOR]
[COLOR=#000000]*ntldr ($root)/bootmgr*[/COLOR]
```

The salient changes are adding 'insmod ntldr', removing the 'if' condition that was before 'search -- no floppy', removing the 'else' condition and the 'fi', then adding 'ntldr (%root)/bootmgr'.

3. Then I pressed F10 to load those edits. It worked. If it works for you, you can permanently edit the GRUB options by following OldFred's advice above.

---

### Post by yancek on 2014-07-19
> The salient changes are adding 'insmod ntldr', removing the 'if'  condition that was before 'search -- no floppy', removing the 'else'  condition and the 'fi', then adding 'ntldr (%root)/bootmgr'.

Interesting.  I have windows 7 on my computer and the grub.cfg file I have on Ubuntu 14.04 does NOT have 'insmod ntldr', nor does it have 'ntldr (%root)/bootmgr' and it does have the if/else and boots without problem.  Not sure what the reasons are for that.

When I install a new system to another partition, I usually boot directly from an iso file from Grub2 or an extracted file from either Grub2 or Grub Legacy so I don't have to bother with a CD/DVD or flash drive.  In that situation, where if they entry is correct, I am only going to boot it once so I can't see the point in putting an entry in a 40_custom file, running update-grub to get it in the grub.cf file to show on the menu, then booting, doing the install and going back and removing the entry from 40_custom and then re-running update-grub.   It's a lot simpler in that situation to edit grub.cfg.  I then have the entry to try multiple times if I want then when finished, just delete the entry from grub.cfg, no need for update-grub.  This is why in my earlier post, I said NOT to run update-grub if you made the change in grub.cfg manually.  The method described by OldFred is the official and correct way to put a permanent entry in the proper files.

---

### Post by Matthew_Bird on 2014-07-19
Yeah - I've no idea why mine has to be different. The version that doesn't work must be the default one (and probably the one you use). I imagine this is fixing some peculiarity of my system that's a result of my idiocy ;-p

---

### Post by DigiAngel on 2014-07-19
So hopefully i'm not hijakcing here, but I have the same-ish issue.  My 40_custom has:

menuentry "Windows 7 (bootmgr on /dev/sdb3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    insmod ntldr
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set=root 463CC2483CC2332B
    ntldr ($root)/bootmgr
}

This gives me an error "/boot/grub/x86_64-efi/ntldr.mod not found"

Sure enough, ntldr.mod isn't in /boot/grub.  What package do I need to get that to work?  Thank you.

---

### Post by oldfred on 2014-07-19
@DigiAngel
I have ntldr in both my 12.04 and 14.04.
But in 14.04 this is my path as I boot with BIOS.
       /media/trusty/boot/grub/i386-pc

You show x86_64-efi which to me would say you have an UEFI boot of Ubuntu. Did you install Windows 7 in UEFI mode or do you have the issue that UEFI and BIOS are not compatible and grub can then only boot systems installed in the same boot mode?

If still an issue may be best to start a new thread and post link to BootInfo report as it seems you have added UEFI which is a major difference.

---

### Post by DigiAngel on 2014-07-19
Thanks Oldfred...I think I'll start a new thread to hammer this out.

---

