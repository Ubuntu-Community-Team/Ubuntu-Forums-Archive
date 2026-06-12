---
title: "Dual boot help needed - boot-repair didn't fix problem"
date: 2018-02-17
forum: General Help
---

### Post by expat778877 on 2018-02-17
Hi - I have 16.10 LTS and Windows 10 on my laptop, and set it up to dual boot using grub.   It worked great for over a year, until I was applying software updates in Ubuntu the other night.  It was installing a grub update, the laptop rebooted, now it boots straight to Windows.  No grub menu.   I searched the forums, downloaded boot-repair after booting a 16.10 USB.   Laptop is set to boot in legacy mode, so that's how I booted the USB.   

Boot-repair loads, gives me the message " '/boot detected, please check the options".   I take the defaults and choose 'recommended repair'.  It does its thing, creates the file and uploads to pastebin, says it repaired, but when I reboot it still boots directly to Windows 10, no grub menu.   

[http://paste.ubuntu.com/p/Ck28hK3F87/](http://paste.ubuntu.com/p/Ck28hK3F87/)

Any advice on how I can get back to dual booting using grub is appreciated!

---

### Post by oldfred on 2018-02-17
You need a current verison of Ubuntu.
 [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

>  Version     Code name             Release date     Supported until         Kernel Version     

    16.10               Yakkety Yak                        2016-10-20                   2017-07               4.8 

And it shows issues with your NTFS partitions. 
That is usually from Windows fast start up/hibernation.
And Windows turns that back on with updates, so you may have to turn it back off again.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

If you do not want to upgrade every 9 months, use the LTS version. 16.04LTS will be valid for 5 years. And 18.04 will be released in April.

---

### Post by ajgreeny on 2018-02-17
You will find it difficult to do much with version 16.10 as it is no longer supported and the repos have moved, so trying to repair will be almost pointless.

I suggest you make a backup of all your important files and then clean install either 16.04 or 17.10, both of which can be updated to 18.04 when it is released in April, or soon after.

EDIT:
Ninja'd by oldfred, who knows more aout boot-repair than I do, so follow his recommendations and yolu should be OK.

---

### Post by expat778877 on 2018-02-17
Thanks for the replies - I feel stupid - I might have 16.04 LTS on my laptop (the version that no longer loads).   I know I should know which version but I might have been wrong in my original post.  FWIW I have been applying recommended updates every week using the software update utility, if I had 16.10 would they still be available?  The ISO I am running on the USB in order to run boot-repair is 16.04.3, downloaded this week using unetbootin. 

oldfred, I turned off fast startup, restarted Windows.   No luck, restarted 16.04 from USB, ran boot-repair again and saved a new file:

[http://paste.ubuntu.com/p/7f6DzxSJnS/](http://paste.ubuntu.com/p/7f6DzxSJnS/)

Do I have any hope of fixing this other than a clean install?

Thanks

---

### Post by oldfred on 2018-02-17
I do not really know encrypted nor LVM installs.
Regular installs will show version, but your encrypted install does not.

Not sure with Boot-Repair if it always asks for you to unencrypt your LVM or / partition or not.
But it must be unencrypted for repairs to work.

One thing I see is that the grub.cfg in your ESP - efi system partition looks like it is missing a line.

 sda1/EFI/ubuntu/grub.cfg

```

search.fs_uuid af1e4d86-1f00-4aad-8a78-a043bffb6a7f root hd0,gpt6 
set prefix=($root)'/grub'

```

This is mine with the missing configfile line, which you should add to yours:
      
```
 search.fs_uuid 255a2800-b871-4fdf-a809-16987e64b8b3 root hd0,gpt6 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg 


```

Your UUID is correct for your ext4 partition, But with LVM should it be the LVM partition that is root? I do not know that.
Your Ubuntu boot entries in grub show this UUID which is not in list of UUIDs, but also the list, I believe, normally also shows the UUIDs of the LVM partitions and it does not.
 root=UUID=2b53fb3e-4483-475a-afe0-eef2f160fbdb 


   Can you unencrypt your LVM partition before running Boot-Repair?
You also still show Windows fast start up on, that must be off.
You also show UEFI Secure Boot on, try again with it off. You are showing signed entries that should work with secure boot on, but worth try with it off also.

---

### Post by expat778877 on 2018-02-19
Thanks oldfred.  I booted the recovery USB, mounted the encrypted LUKS partition, ran boot-repair, now I can see grub and and can boot into ubuntu!  Unfortunately I can't get past the prompt for the passphrase to decrypt the volume, even though I can manually mount it using that passphrase when booting from the recovery USB.  

I'll probably post a new thread about that problem.  Thanks for all your help!

---

### Post by oldfred on 2018-02-19
If you can mount it, make sure you have good backups.
With encrypted partitions having a very good backup procedure that you regularly follow is vital.

If drive or partition has issues, and you cannot mount then there is no way to recover data.
With standard partitions, there may be ways to recover partial data, but still backups are better.

---

