---
title: "How do I &quot;de-Vista&quot; my MBR? (ie, restore XP bootloader)"
date: 2007-02-16
forum: General Help
---

### Post by wilberfan on 2007-02-16
Forgive me if this doesn't belong here, but these forums are a great place to get help with all KINDS of problems...

At one point, I had a tri-boot system:   XP, Ubuntu, and Vista(beta).   It became very obvious, very quickly that I had no interest in Vista....

I ended up reformatting that partition to ext3, and putting all my music files there!   

Here's my problem:  To boot into XP (which I want to hang onto for awhile), I have to select the only Windows option that appears on the GRUB menu--the same one that existed when Vista was present:   the Vista bootloader.   When I select that option, it takes me to a second screen where Vista is the default choice, and "an older Windows installation" (or something) is the other choice.

XP boots fine if I select that other option (I get an error if I let it default to Vista, obviously--since it's no longer on my system.

What I'd like is to "restore" the XP bootloader (somehow) so that my GRUB menu shows a "Windows XP" option, which if selected, will boot up XP.

Does that make sense?   Sorry if that's a little convoluted...

I've tried doing a "fixmbr" from the XP installation disk, but it changes nothing (the Vista bootloader is still there).  

Any ideas??

---

### Post by true_friend on 2007-02-16
It was somewhere in My Computer Properties but i can not remember where. u may search there i did it once. i had also same situation with windows 2000.
Regards.

---

### Post by wilberfan on 2007-02-17
> **true_friend said:**
> It was somewhere in My Computer Properties but i can not remember where. u may search there i did it once. i had also same situation with windows 2000.
Regards.

Hmmm...  There was an 'advanced' tab under My Computer/Properties, but there was only one option there (in a pull-down window).   It looks like there's an editable command, too, but I have no idea what would go in there...

Anyone else?

---

### Post by upsfeup on 2007-02-17
Is it not better to try to edit the menu from grub directly?

Trying to change the setting in Windows will probably rewrite the MBR and mess everythin up

---

### Post by mkw87 on 2007-02-17
1)  Boot into XP, right click my computer and select properties.

2)  Go to the advanced tab, and select the third settings button down for 'Startup and Recovery'.

3)  Select the edit button on the new window that popped up, this will launch notepad and allow you to edit your boot.ini file.  

4)  Before you change anything, I suggest backing it up by doing a 'File > Save As' and name it something like boot_backup.ini.

5)  Now, to edit it, simply remove the line under the [operating systems] section that pertains to vista.  Do not change anything on the one for XP.

6)  Save the file, close it, and reboot.  This should take care of it.

---

### Post by opticyclic on 2007-02-17
I am in exactly the same position, wanting to get rid of the Vista/"Earlier version of Windows" choice.
However, as you can see from my boot.ini, there is no mention of Vista
```
;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTIN

```
All other information I can find seems to rely on you making the change before uninstalling Vista.
Which is already too late....
[http://apcmag.com/4054/how_to_dual_boot_xp_and_vista](http://apcmag.com/4054/how_to_dual_boot_xp_and_vista)

---

### Post by DivineOmega on 2007-02-17
One of my friends has a similar triple boot system. The page [http://www.empirechaotix.co.uk/?p=237](http://www.empirechaotix.co.uk/?p=237) relates to how he configured GRUB to recognise Vista (as it did not automatically detect it as a Longhorn boot loader).

I'll investigate this myself, but try asking your question on that page, as I've had little experience with Vista myself.

---

### Post by wilberfan on 2007-02-17
Just to clarify (perhaps I've misunderstood your post)--I want GRUB to recognize a ***NT/2000/XP bootloader*** (if it's anywhere on my system), _NOT_ the "Vista/Longhorn" bootloader...

(At least I THINK that's what I want!)

Ideally, I want something on the GRUB menu that says, "NT/2000/XP" (or the equivilent) and, if selected, boots directly into XP--bypassing having to select "Older Windows Installation" (or whatever it says)...

---

### Post by DivineOmega on 2007-02-17
> **wilberfan said:**
> Just to clarify (perhaps I've misunderstood your post)--I want GRUB to recognize a ***NT/2000/XP bootloader*** (if it's anywhere on my system), _NOT_ the "Vista/Longhorn" bootloader...

(At least I THINK that's what I want!)

Ideally, I want something on the GRUB menu that says, "NT/2000/XP" (or the equivilent) and, if selected, boots directly into XP--bypassing having to select "Older Windows Installation" (or whatever it says)...

I thought that's what you meant, I just hoped that you may be able to use that reference to your advantage.

What is your partition layout? If the XP bootloader is still intact you should be able to direct GRUB towards it by editing /boot/grub/menu.lst. The code I use to run the Windows boot-loader (granted I do not have Vista installed) is:

title		Microsoft Windows XP Professional
root		(hd0,2)
savedefault
makeactive
chainloader	+1

In theory, you should be able to direct this code towards the partition that contains Windows XP by changing (hd0,2) in the code above. 

Also, have you tried the 'fixboot' command in the Windows Recovery console as well as 'fixmbr'? That can sometimes help.

---

### Post by wilberfan on 2007-02-18
> **DivineOmega said:**
> I thought that's what you meant, I just hoped that you may be able to use that reference to your advantage.

I did go there and leave a comment; we'll see if I get any nibbles!

> What is your partition layout? If the XP bootloader is still intact you should be able to direct GRUB towards it by editing /boot/grub/menu.lst. The code I use to run the Windows boot-loader (granted I do not have Vista installed) is:

title		Microsoft Windows XP Professional
root		(hd0,2)
savedefault
makeactive
chainloader	+1

Here's my entry:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

> In theory, you should be able to direct this code towards the partition that contains Windows XP by changing (hd0,2) in the code above. 

My XP is loaded on the first partition of my first drive...and isn't that what's indicated by the "hd0,0" above?  (Forgive me, I'm pretty new at this!)

> Also, have you tried the 'fixboot' command in the Windows Recovery console as well as 'fixmbr'? That can sometimes help.

I don't believe I tried that one...  I've been playing with OpenSUSE 10.2 tonight (!), I'll have to try that next opportunity! 

Thanks for your suggestions so far!   :)

---

### Post by DivineOmega on 2007-02-18
> **wilberfan said:**
> 
Here's my entry:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```



My XP is loaded on the first partition of my first drive...and isn't that what's indicated by the "hd0,0" above?  (Forgive me, I'm pretty new at this!)


You're right, that should be correct. It seems that Vista must have overwritten your XP bootloader with its own and put the XP one to one side...

> **wilberfan said:**
> I don't believe I tried that one...  I've been playing with OpenSUSE 10.2 tonight (!), I'll have to try that next opportunity! 

Thanks for your suggestions so far!   :)

No problem.

If you work out a solution make sure to post it here so it can help other users who will no doubt be trying out Vista sometime soon, realising their mistake and wanting to return to the light.;)

---

### Post by opticyclic on 2007-02-18
I did a search of the MSDN newsgroups for the solution
[http://www.microsoft.com/communities/newsgroups/en-us/default.aspx?dg=microsoft.public.windows.vista.installation_setup](http://www.microsoft.com/communities/newsgroups/en-us/default.aspx?dg=microsoft.public.windows.vista.installation_setup)

What was suggested was VistaBootPro [http://www.vistabootpro.org/](http://www.vistabootpro.org/)
This worked perfectly for me.
It comes up with an error initially because Vista is no longer installed, but it still runs fine in XP.
It has a nice GUI and there is a section that allows you to uninstall the Vista bootloader.

A quick restart and BAM! no Vista bootloader.
I just have to change my Grub entry now back to "Windows XP Professional" instead of "Windows Vista/Longhorn (loader)"
I can also do this from XP because I have installed [http://www.fs-driver.org/](http://www.fs-driver.org/) which lets you write to Ext2 filesystems from XP!

---

