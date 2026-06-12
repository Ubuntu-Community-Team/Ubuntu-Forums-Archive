---
title: "Ubuntu will not boot up, and gives this error message"
date: 2017-02-18
forum: General Help
---

### Post by elvis6 on 2017-02-18
One day, while using Ubuntu, everything on the screen froze, and I could not do anything.
My only option was to force a shut down, and re-boot.
But now, ever since then, every time I try to start up, I get the below error message, and I am clueless as to what it means.
It comes up on the black screen, even before the grub menu options appear, so there's no apparent way to go into any diagnostics ; although the "grub>" line at the end seems to indicate maybe I can type commands in there, but I know virtually nothing about Terminal language, so I wouldn't know where to start.
I'm not sure if there's specific information you need about my Ubuntu version or PC, so please let me know what else you need, in order to help. Thank you.

This is the error message that continually appears :

> GNU GRUB version 1.99-21ubuntu3.20
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions

grub>

---

### Post by speartip on 2017-02-18
What version of Ubuntu are you using?
Grub version 1.99 seems quite old to me.

---

### Post by elvis6 on 2017-02-18
> **speartip said:**
> What version of Ubuntu are you using?
Grub version 1.99 seems quite old to me.

Ubuntu 12.04 Precise version.
And I intentionally have not upgraded to a newer version, because the PC is old and with limited resources, so I didn't think it could handle the extra weight of the newer versions.

---

### Post by speartip on 2017-02-18
If you have the original CD/DVD/USB of Ubuntu 12.04 you could boot into that & re-install Grub. If Not Boot Repair Disk does an easy job of reinstalling grub.
 [https://sourceforge.net/projects/boot-repair-cd/](https://sourceforge.net/projects/boot-repair-cd/)
Of course you'll need to find another computer to download & burn the iso.

---

### Post by elvis6 on 2017-02-18
> **speartip said:**
> If you have the original CD/DVD/USB of Ubuntu 12.04 you could boot into that & re-install Grub. If Not Boot Repair Disk does an easy job of reinstalling grub.
 [https://sourceforge.net/projects/boot-repair-cd/](https://sourceforge.net/projects/boot-repair-cd/)
Of course you'll need to find another computer to download & burn the iso.

My installation method was WUBI.
I still have the WUBI exe file on that PC, stored on the "Windows side" of the dual OS.
If I click on the file, will I have an option to do what you stated above, and do so without losing any files on the Ubuntu side of the OS's ?

---

### Post by speartip on 2017-02-18
No.you didnt mention  it  was a wubi install. That makes a difference.  I've never used wubi, so I'm not sure whether windows or ubuntu control your boot. I suspect it's windows, so I'm not sure how you need to proceed.

---

### Post by oldfred on 2017-02-18
12.04 expires in April 2017.

And wubi has not really been supported since 12.04.

       Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)
[https://bugs.launchpad.net/wubi/+bug/1478239](https://bugs.launchpad.net/wubi/+bug/1478239)
But unoffical version here by hakuna_matata:
[https://github.com/hakuna-m/wubiuefi/wiki](https://github.com/hakuna-m/wubiuefi/wiki)

But my 2006 Intel Core2 Duo laptop system with 1.5GB RAM, was on 12.04. 
While I have essentially retired it for a new desktop, I just installed full Ubuntu 16.04.
Quite surprised that even Unity worked. Only a bit slow.
With 12.04 install Unity was so slow as to be unusable and I always installed fallback or gnome-panel as gui.
I have then always suggested one of the lighter weight flavors like Lubuntu, Xubuntu or Ubuntu Mate.

---

### Post by hakuna_matata on 2017-02-19
> **elvis6 said:**
> 
This is the error message that continually appears :
```
GNU GRUB version 1.99-21ubuntu3.20
Minimal BASH-like line editing is supported. For the first word, TAB  lists possible command completions. Anywhere else TAB lists possible  device or file completions

grub>                      
```

Possible reason for your grub prompt is that your root.disk is missing or the file system within root.disk is corrupted. see [http://ubuntu-with-wubi.blogspot.co.at/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.co.at/2011/08/missing-rootdisk.html)
> **elvis6 said:**
> 
although the "grub>" line at the end seems to indicate maybe I can  type commands in there, but I know virtually nothing about Terminal  language, so I wouldn't know where to start.

After checking the root.disk, you can try to boot from grub prompt with the following commands:
```

search -s -f -n /ubuntu/disks/root.disk
probe --set=diskuuid -u $root
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=UUID=$diskuuid loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot

```

---

### Post by elvis6 on 2017-02-22
> **hakuna_matata said:**
> Possible reason for your grub prompt is that your root.disk is missing or the file system within root.disk is corrupted. see [http://ubuntu-with-wubi.blogspot.co.at/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.co.at/2011/08/missing-rootdisk.html)

After checking the root.disk, you can try to boot from grub prompt with the following commands:
```

search -s -f -n /ubuntu/disks/root.disk
probe --set=diskuuid -u $root
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=UUID=$diskuuid loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot

```

Thanks for the instructions. I assume that the commands you listed are separate commands on each line ?
After the first command, I get the response "error: no such device: /ubuntu/disks/root.disk"
So, I guess this confirms the first theory, that my root disk is corrupted or missing ?

I tried your 2nd suggestion first, because it was quicker and simpler. So I assume I need to go back to the first link you provided and go through that process.

---

### Post by elvis6 on 2017-02-22
> **hakuna_matata said:**
> Possible reason for your grub prompt is that your root.disk is missing or the file system within root.disk is corrupted. see [http://ubuntu-with-wubi.blogspot.co.at/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.co.at/2011/08/missing-rootdisk.html)



So, now I have gone through a few steps on that link and I'm really stuck.
I did the chk dsk utilities to completion, and the "grub" problem still remained.
Then I moved onto the "cmd exe" steps, and got to the part where I ask it "dir /a:h"
The instructions tell me I should then locate the "found directory".
But that does not appear in the displayed list.
The list below is the response I get.
Could someone interpret this, and tell me what I need to do next ?
Does the fact that it does not show a "found directory" mean that everything is lost ?
I'm really stuck. Please help.

---

### Post by hakuna_matata on 2017-02-24
> **elvis6 said:**
> 
Then I moved onto the "cmd exe" steps, and got to the part where I ask it "dir /a:h"

Note that bcbc changed the directory with
```
cd \
```
before using the dir command. So you tried the command within the wrong directory.

> **elvis6 said:**
> 
Does the fact that it does not show a "found directory" mean that everything is lost ?

Besides my note above about the directory, it is uncommon that the root.disk is completely removed. So probably, there is a either root.disk with 0 bytes within folder /ubuntu/disks or a "found directory".

If there is a "found directory", it is the better case than a zero bytes root.disk.

In general, if your root.disk contains important data you should create backups frequently. It is really easy with copy and paste. If you have a backup, it would be also easy to restore it. But I assume, there is no backup.

---

### Post by guinea2 on 2017-02-25
Try doing this:

First type "ls" and then find the drive and partition that ubuntu is installed on

Once you found it it should be something like hdX,gptX (X meaning the number that is displayed)

Now with the drive and partition that its installed on type: "root=hdX,gptX" (X meaning the number that is shown)

Now all you have to do is type "configfile /boot/grub/grub.cfg" and it SHOULD boot up (If you put the right disk and partition numbers)

---

### Post by elvis6 on 2017-02-26
> **hakuna_matata said:**
> Note that bcbc changed the directory with
```
cd \
```
before using the dir command. So you tried the command within the wrong directory.

Besides my note above about the directory, it is uncommon that the root.disk is completely removed. So probably, there is a either root.disk with 0 bytes within folder /ubuntu/disks or a "found directory".

If there is a "found directory", it is the better case than a zero bytes root.disk.


Thank you for filling me in on the CD directory. 
So, after using that specification, the list shows hidden files including a directory of "found.000"
When I check that directory it shows "0 Files 0 Bytes".
I attached a picture with the display described above.
So, I'm a novice and a little slow on this subject, so I just want to be sure about this - does the above "0 Files 0 Bytes" response mean that the information I need is completely lost ?

> **guinea2 said:**
> Try doing this:

First type "ls" and then find the drive and partition that ubuntu is installed on


When I type "ls" (and I assume that starts with a lower case letter L), I get this response :
'ls' is not recognized as an internal or external command, operable program or batch file
Am I missing or skipping a step in this command ?

---

### Post by elvis6 on 2017-02-27
> **elvis6 said:**
> Thank you for filling me in on the CD directory. 
So, after using that specification, the list shows hidden files including a directory of "found.000"
When I check that directory it shows "0 Files 0 Bytes".
I attached a picture with the display described above.
So, I'm a novice and a little slow on this subject, so I just want to be sure about this - does the above "0 Files 0 Bytes" response mean that the information I need is completely lost ?


As an update to this, I found that it appeared there was another step I could go onto. However I am stuck again.
Based on the blog instructions saying, "Or if the whole \ubuntu\disks folder is missing:" I did the command "
C:\found.000>dir dir0000.chk 
and saw what appeared to be an 18G root.disk. So I then did the next command listed 
C:\>move dir0000.chk \ubuntu\disks
        However, instead of showing that directory moved, it stated "The system cannot find the file specified".
What does this mean ? Did I do it incorrectly ?

---

### Post by elvis6 on 2017-03-01
Hi guys. When I posted my last response, I noticed that it did not bump my thread up, (probably due to a forum message I got that the site was having issues), so as a result, my case dropped to page 4 of the forum, and I was concerned I may have been overlooked or forgotten. And my latest question seems like it would be a simple answer for the experts, so hopefully this isn't too much of a burden to re-visit this. Thanks.

---

### Post by hakuna_matata on 2017-03-03
> **elvis6 said:**
> I did the command "
C:\found.000>dir dir0000.chk 
and saw what appeared to be an 18G root.disk. So I then did the next command listed 
C:\>move dir0000.chk \ubuntu\disks

If you compare the [screenshots of bcbc]("http://ubuntu-with-wubi.blogspot.co.at/2011/08/missing-rootdisk.html") with [your screenshot]("https://ubuntuforums.org/attachment.php?attachmentid=273916&d=1488207893"). You did an additional
```
cd /
```
before the move command. So you did the command within **C:\** and bcbc did it within [B]C:\found.000

[/B]So it seems that you can recover your root.disk, if you exactly follow the advices of bcbc.

edit: After recovering your root.disk, I recommend that you create a backup of your root.disk before trying to boot into Ubuntu.

---

### Post by elvis6 on 2017-03-05
> **hakuna_matata said:**
> If you compare the [screenshots of bcbc]("http://ubuntu-with-wubi.blogspot.co.at/2011/08/missing-rootdisk.html") with [your screenshot]("https://ubuntuforums.org/attachment.php?attachmentid=273916&d=1488207893"). You did an additional
```
cd /
```
before the move command. So you did the command within **C:\** and bcbc did it within [B]C:\found.000

[/B]So it seems that you can recover your root.disk, if you exactly follow the advices of bcbc.

edit: After recovering your root.disk, I recommend that you create a backup of your root.disk before trying to boot into Ubuntu.

That worked !
Thanks you so very much for your patient assistance and all the suggestions. 
Mission accomplished.

---

