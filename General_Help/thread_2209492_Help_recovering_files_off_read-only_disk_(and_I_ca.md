---
title: "Help recovering files off read-only disk (and I can't mount anything)"
date: 2014-03-06
forum: General Help
---

### Post by gavannon on 2014-03-06
Long story short, my Ubuntu install has been botched during an upgrade attempt. (10.04, attempting to upgrade to 12.04).

I can get past my encryption password (hd is encrypted), but after that, I get the following:

```
mountall: invalid option: --tmptime=0
init: mountall main process (588) terminated with 1
fatal error mounting filesystems.
general error mourning filesystems
a maintenecne shell will now be started.
conrol-d will terminate this shell and retry
```

I can then cd to / and see all my personal folders (thankfully), but it's all read only.

If all is lost, which seems to be the case (there's no etc folder for example), I'd at least like to be able to copy my files off, and reinstall.

Is there any way I can do an emergency copy of my files to an external HD? I can plug one in, see it, but can't mount it, as everything is read-only.

---

### Post by papibe on 2014-03-06
Hi gavannon. Welcome to the forum ):P

I'd start here: [Ubuntu Wiki Data Recovery]("https://help.ubuntu.com/community/DataRecovery").

Let us know how it goes.
Regards.

---

### Post by gavannon on 2014-03-06
Thanks for the link, and the welcome! :D

I did some reading on that page, I don't think my issue is a corrupt hard disk. I think it's a corrupt Ubuntu install. The files are technically okay, and I can still see them. Unfortunately, most options suggested on that page require being able to make a directory, or install an app. As my mounted HD is read-only, those options aren't possible. :(

Any other way to copy files off a corrupt Ubuntu install?

---

### Post by papibe on 2014-03-06
Unfortunately, most of those tools require a working media where to write the recovered files.

If I were you, I'd go and buy another disk ASAP, so I can save those files to a working filesystem. At this point you have to consider the possibility that the drive is dying and it is not recoverable.

Regards.

---

### Post by varunendra on 2014-03-06
> **gavannon said:**
> Is there any way I can do an emergency copy of my files to an external HD? I can plug one in, see it, but can't mount it, as everything is read-only.

What error do you get while trying to mount it. Please show us everything that you see, and by which you think mounting (or re-mounting r/w) is a problem.

---

### Post by gavannon on 2014-03-06
On boot:

mountall: invalid option: --tmptime=0
try 'mount all --help' for more information
init: mountall main process (588) terminated with 1
general error mourning filesystems
a maintenecne shell will now be started.
conrol-d will terminate this shell and retry

I try to mount an external HD with:

mount /dev/dsa1 /mnt -t ntfs

Which returns:

the NTFS signature is missing. Failed to mount '__' invalid argument
The device ___ doesn't seem to have a valid NTFS ... etc.

The external HD is formatted in NTFS.

---

### Post by varunendra on 2014-03-06
> **gavannon said:**
> I try to mount an external HD with:

mount **/dev/[COLOR="#FF0000"]dsa1[/COLOR]** /mnt -t ntfs

Which returns:

the NTFS signature is missing. Failed to mount '__' invalid argument
The device ___ doesn't seem to have a valid NTFS ... etc.
May I assume the above highlighted part is a typo while posting here? Because there certainly can't be a device/partition named as "dsa1".

The "mountall" command depends on the /etc/fstab file, so that is irrelevant to what happens when manually mounting/re-mounting a partition. If using the command in correct form (e.g., "sudo mount -t ntfs **-o rw,nosuid,nodev** /dev/sda1 /mnt", the part in bold can usually be omitted) also returns the same error, you can use TestDisk (sudo apt-get install testdisk) in Live mode to list the partitions and their contents, and copy the files from there onto an external drive.

*[**EDIT: **Almost forgot that you have encrypted your partition. In that case, booting in Live session won't show your files. Instead, it may show one huge (probably hidden) file containing your actual files in encrypted form. I'm not familiar with how to recover that, but I know it IS possible from live mode. You'll have to read on how to recover encrypted partitions/files (you can start [here]("https://help.ubuntu.com/community/EncryptedHome"), I don't have a better link, sorry).]*

TestDisk Step-by-Step : [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by gavannon on 2014-03-06
Sorry yes, it was a typo.

There is no /etc/ directory. (Yup.)

I'm trying to now recover from a new LiveCD. How can I connect to an encrypted partition from a LiveCD?

---

### Post by varunendra on 2014-03-06
> **gavannon said:**
> How can I connect to an encrypted partition from a LiveCD?

I've no idea :( Please see my edit in above post. Hope someone else having experience with encrypted filesystem may be able to offer better help on that.

---

### Post by gavannon on 2014-03-06
Okay I've solved it! To help others:

1. I gave up on trying to get back into my files. "etc" was missing... it was a mess.

2. Instead, I downloaded Ubuntu desktop, which includes the "LiveCD". Lets you run near-full working Ubuntu from the CD.

3. Once in, I was able to decrypt my partitions using trial and error of these commands:

[INDENT]```
sudo cryptsetup luksOpen /dev/sda1 encrypted_volume

```

Then I tried to mount it:

```
sudo mkdir /media/my_device
sudo mount /dev/mapper/encrypted_volume /media/my_device
```

(That didn't work. It said it was already mounted or mapped.)

So then I tired:

```
sudo udisksctl unlock -b /dev/sda1
```

This mounted my encrypted drive into /media/ubuntu/____crazylongname____

Inside that crazylongname folder was my encrypted files![/INDENT]

4. Permissions from my previous install didn't allow access to some folders. So I used:
```
sudo chmod o+rw -R foldername
```
and even
```
sudo chown root:root -R foldername
```
for each that I couldn't get into. Still no luck for either. Turns out, I had to be super user.

5. Changed to super user
```
sudo -s
```
NOW I can get into my encrypted folders, and copy them off to an external HD.

6. Launched file explorer as sudo for easy GUI copying to external HD!
```
sudo nautilus
```

7. Celebrate, do full install of latest Ubuntu.

---

### Post by varunendra on 2014-03-06
Awesome post gavannon! I'm going to bookmark it. :)

Just a few clarifications though -
> **gavannon said:**
> 
4. Permissions from my previous install didn't allow access to some folders. So I used:
```
sudo chmod o+rw -R foldername
```
and even
```
sudo chown root:root -R foldername
```
for each that I couldn't get into. Still no luck for either. Turns out, I had to be super user.

5. Changed to super user
```
sudo -s
```
NOW I can get into my encrypted folders, and copy them off to an external HD.

6. Launched file explorer as sudo for easy GUI copying to external HD!
```
sudo nautilus
```

**About point 4.**, if you are using Ubuntu in a Live session, the user is "ubuntu". As such, the following command is all you need to be able to access the files normally -
```
sudo chown -R ubuntu:ubuntu *<the target directory>*
```
where *<the target directory>* should obviously be replaced by the name of the directory (or mount-point) which you want to access normally.

If the point 4. is done as suggested above, you won't need to be root, nor would have to open the file manager (file explorer) as root.

**About point 6.**, Launching the file manager as root is potentially risky, because in that mode, all your GUI actions would be completed quietly, without any errors or warning, _[COLOR="#FF0000"]Even if it is a harmful action[/COLOR]_ like deleting/overwriting or modifying a secure and sensitive file/directory. Although I understand that didn't matter in your case, but this is something that should _always_ be made clear whenever suggesting to open a GUI program as root.

Another thing to note is that if the target directory, where you are copying the files, is located on a Linux partition or any other filesystem that supports permission bits (windows filesystems don't), the copied files would be owned by the user who has copied the files. Which means user "ubuntu" in a Live session. So when accessing those files again from an installed instance of Ubuntu, you'll need to change the ownership of the files/directories again to become their owner. Not a problem, just something one should be aware of. :)

---

