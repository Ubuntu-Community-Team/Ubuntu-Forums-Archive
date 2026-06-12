---
title: "Truecrypt encrypted drive - mounting problems"
date: 2013-04-22
forum: General Help
---

### Post by miro8 on 2013-04-22
I noticed I have problems with mounting encrypted HDD seagate 2tb, 

Since last Wednesday, probably after ubuntu update - kernel update,

 I can't mount encrypted drive , truecrypt gives message:

```
device-mapper: resume ioctl failed: Invalid argument
Command failed
```

I read I need to rebuild truecrypt module.

Can you help me with the syntax , how can I rebuild that module?

What to type in terminal?

truecrypt version is 7.1a

---

### Post by tubbygweilo on 2013-04-22
miro8, I had this a week or so ago when attempting to access a TrueCrypt 7.1a created under Ubuntu 12.04lts from a freshly installed Ubuntu 12.10 with the LVM option + encryption. After searching about I decided that this may be down to LVM + encryption so a fresh install without LVM worked as expected.

Good luck, hope your backups are sound.

---

### Post by miro8 on 2013-04-22
thanks for the answer, you mean fresh install of partition without LVM where data is located (encrypted),  or just fresh install of operating system partition without LVM?

1st and most important step fro me now  is to copy data from encrypted partition on safe place.

---

### Post by tubbygweilo on 2013-04-22
miro8,
If you can create a backup of unencrypted data in a safe place then I would do it.
As I didn't have all that much data I need to access I used DVDs + USB memory sticks to store backups.
I then did a clean install of 12.10 with encrypted /home option, created a new set of TrueCrypt containers and filled them with the unencrypted backups.
It all worked with TrueCrypt and Ubuntu working together without problems.

You may well be able to manipulate LVM to short cut these steps but I do not have the knowledge to guide you.

You can never have too many working backups.

Hope it all goes as expected.

---

### Post by miro8 on 2013-04-23
I understand, you used truecrypt containers( encrypted files) , but in my case I encrypted whole drive.

It's too risky for me to make tests with the disk while data is stored, so first I want to make sure I can get access to files so I can backup.
But I'm not sure what kind of backup can I do , since partition  encrypted with treucrypt is hidden and ext4.

---

### Post by varunendra on 2013-04-23
@miro,
Have you tried a fresh installation of truecrypt on a live flash drive?

I find it most handy. At least it will eliminate the number of things that may go wrong (fresh, working 'live' usb + fresh TC installation).

---

### Post by miro8 on 2013-04-25
hello,

@[ ]("http://ubuntuforums.org/member.php?u=1043629")[**[COLOR=#DD4814][B]varunendra**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1043629")
 
here is the update, sorry I was busy.

I installed ubuntu live stick from installation cd (command was usb-creator-gtk) and boot from it, installed truecrypt  - the same version what I use on that disk.

What happened is that with the default truecrypt settings I got the same error as specified in the first post, so I couldn't mount it, 

then I unchecked option in truecrypt settings : settings->preferences->system integration: "DO NOT USE KERNEL CRYPTOGRAPHIC SERVICES"

and I could finally mount and see the data.

But from what I've read, without using kernel cryptographic services truecrypt performance will be very slow.

So most important is I can backup data now but what to so now?! I thought clean and new installation of ubuntu might solve the problem, knowing I need to uncheck this option probably I will need to look some alternative software.

I choosed truecrypt because it's multiplatform software.

Still need help :(

---

### Post by varunendra on 2013-04-25
As far as I know, the properties of an encrypted drive/container are independent of version of TC used to create it.

Given the descriptions so far, I doubt a broken kernel upgrade, or maybe a bug in the new kernel. If you haven't removed the older kernel after update, please try booting into the older one, and retry mounting with default options.

---

### Post by miro8 on 2013-04-26
Thanks for response, how can I actually boot with the old kernel?

BTW still I need to determine if there was kernel update in this month?

---

### Post by varunendra on 2013-04-26
You're welcome :)

To see which kernel versions are installed :
```
dpkg --get-selections | grep linux-image
```

To see current kernel in use:
```
uname -mr
```

To boot with an older kernel (if exists), choose "Older versions.." from GRUB Menu. To bring up the grub menu, press 'Shift' or 'Esc' key while the computer is booting.

---

### Post by miro8 on 2013-04-27
I put older version of kernel and still I couldn't mount it.

I plan to reinstall and disable ubuntu automatic updates.

I don't know what actually caused that problem!

---

### Post by varunendra on 2013-04-27
> **miro8 said:**
> I don't know what actually caused that problem!

Neither do I. It is beyond my understanding of TrueCrypt's working.. :(

---

### Post by miro8 on 2013-04-28
Why do you think it has to do with truecrypt?

Truecrypt is not the one who gives updates, ubuntu got updated and caused problem :)

I wont install updates anymore ,too bad I can't just downgrade.

---

### Post by varunendra on 2013-04-29
> **miro8 said:**
> Why do you think it has to do with truecrypt?

Nope, I absolutely don't think it has anything to do with TC. In fact I have been trying to point it out that its partitions/containers are independent of platform or versions, and hence the data is safe as long as the container/drive is intact.

I think I made clear that me too am doubting a broken update/upgrade on Linux part. I just don't understand how TC combines with the native OS components to mount its encrypted drives/containers.

In any case, it is a good thing that you can always use an alternate OS/version with TrueCrypt to access your encrypted data. Let's hope whatever the bug is, gets fixed soon. But if it indeed is a bug, someone like you will have to report it on launchpad first!

---

### Post by miro8 on 2013-04-29
I understand it's risky to update any system component, but I didn't expected it will be impossible to rollback the update.
I used synaptic update manager to check what's been updated, still it's not clear to me how exactly works, because I'm new to ubuntu.

WHat I could is unninstal old kernel  by unticking "X" and then repeat installation of old kernel  by putting the same "X" by the old version ,  hm...

Until this cooperation between ubuntu and TC is fixed I wont update ubuntu components I don't know what they are.

but thanks man anyway.

---

