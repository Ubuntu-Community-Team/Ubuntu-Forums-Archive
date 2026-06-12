---
title: "Problem with file/dir rights."
date: 2007-09-30
forum: General Help
---

### Post by benchMarc on 2007-09-30
Ok, here's the thing:

I've got 2 pc's. One ubuntu and one WinXP client. On that WinXP client i shared some dirs. I mounted one dir as /mnt/share in Ubuntu via fstab: 

```
//192.168.0.50/newdownloads /mnt/share smbfs credentials=/home/marc/.smbcredentials,uid=www-data,gid=marc,dmask=777,fmask=777 0 0
```

Ok, why the www-data? I use HellaNZB on my ubuntu PC. This is a program that detects imported .nzb files and processes them (parring/extracting). I've chosen to let HellaNZB watch the /mnt/share/nzb/que dir. On my Ubuntu client i've got Apache running. I installed a webbased interface that monitors HellaNZB on it. Called Zussaweb. Via this program i can also upload .nzb files to my que dir. I found out this only works when the que dir is being owned by www-data. So that's why i mounted the shared map on my WinxP with uid=www-data. Everything goes ok. I can upload a .nzb file to the que dir. But then a problem appears. HellaNZB detects this file and begins processing, but for HellaNZB it is necessary to move the .nzb file immediately to another dir. But HellaNZB can't move this file, because HellaNZB runs under the user Marc. Even if i start it with sudo it can't move the file. I tried deleting the file in a terminal, with root and marc. And if course to no avail.

When i check the settings of the .nzb file uploaded by the Zussaweb interface it says:
Owner: www-data Access: Read and write
Group: Marc Access: Read and write
Others: Access: Read and write

So... the question is. How can i upload files to a dir with Zussaweb but giving other users the right to delete the file?

Note: I can't change the permissions of a dir i mounted. I have to specify this in the fstab file.

Hope someone can help.

---

### Post by benchMarc on 2007-09-30
I was wrong. I thought the problem was that i had not enough rights.

When i try deleting the file via the terminal it says:

rm: cannot remove 'file.nzb': Text file busy

Hmmmm...

I found this out because i uploaded another new file (which then gets in the que instead of being processed) and i was able to delete that one.

So.... i'm wondering what program uses that file. Must be something with HellaNZB

---

### Post by BUGabundo on 2007-10-02
> **benchMarc said:**
> I was wrong. I thought the problem was that i had not enough rights.

When i try deleting the file via the terminal it says:

rm: cannot remove 'file.nzb': Text file busy

Hmmmm...

I found this out because i uploaded another new file (which then gets in the que instead of being processed) and i was able to delete that one.

So.... i'm wondering what program uses that file. Must be something with HellaNZB

stupid question:
do you have permitions on the windows box to delete the files?
in which fs is it?

---

### Post by benchMarc on 2007-10-03
> **BUGabundo said:**
> stupid question:
do you have permitions on the windows box to delete the files?
in which fs is it?
Yes i have. I think the problem lies within HellaNZB itself. I use Sabnzbd now without any problems. So there was nothing wrong with the permissions. It's just that HellaNZB isn't giving the file free or something.

---

