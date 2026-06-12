---
title: "Unable to boot after upgrading to Win10"
date: 2016-05-18
forum: General Help
---

### Post by matti123456 on 2016-05-18
At boot up i get this 'error: no such partion. entering rescue mode...'  

I found a post that explains this problem better than i could and there is a suggested solution as well. Problem is that i could not find the right partion with those suggested commands. I just want to boot Windows, download Win10 iso from Windows store and format my hard drive. Any tips?
> Let me write about some of problems to help other people who might encounter the same issues.

My computer came with Windows 8 pre-installed so I shrunk the Windows partition to make room for Ubuntu. That it how it works for the last year.

After the second reboot in Windows 10 upgrade the computer did not boot any more. The grub only displayed a grub rescue command prompt. I found out later that the problem occurred because windows somehow changed the partition scheme. The boot partition was no longer where grub expected it. I don't know how and why this happened.

First what you can do is to see the partitions in grub rescue with "ls". Mine were (hd0,gpt1), (hd0,gpt2), etc. Try to find out which partition is your boot partition. I tried the following commands until i found the right partition:
```

ls (hd0,gpt1)/

ls (hd0,gpt1)/boot

ls (hd0,gpt2)/
```

etc.

Then type 'set' in grub rescue prompt. It will display where the grub looks for its files. In my case (hd0,gpt6) has moved to (hd0,gpt7). The set command displayed:

```
prefix=(hd0,gpt6)/boot/grub

root=hd0,gpt6
```

Change the prefix and root settings to point to the right partition. In my case commands were:
```

set prefix=(hd0,gpt7)/boot/grub

set root=(hd0,gpt7)
```

Then switch from rescue to normal mode:

```
insmod normal

normal
```

You should get the normal grub menu. From now on you can boot Windows and finish your Windows upgrade. The problem is that you have to tell grub rescue about the right partitions on every reboot. That is how I did it. I left the problem of grub for later because I was not sure whether Windows will do some more changes to the partitions or boot.

When Windows finished I started to solve grub problems. Press "e" to edit boot options for Ubuntu. I changed all (hd0,gpt6) to (hd0,gpt7) and Ubuntu booted. However, I use encrypted partition and cryptswap. At the boot Ubuntu asked me for the passphrase. Fortunately I saved it at the installation of Ubuntu and entered it at the boot. Ubuntu booted without problems. I corrected the /boot/grub/grub.cfg where I replaced (hd0,gpt6) with (hd0,gpt7) and performed 'sudo grub-install'.

Now it was only the encryption. Since the root Ubuntu partition was raised for one (7 from 6), the swap partition suffered a similar change. I had to change the /etc/crypttab file to point to /dev/sda8 instead of /dev/sda7.

I am using only two partitions for Ubuntu (root and swap). If other operating systems coexisting with windows use more partitions there might be more changes required. Especially if partitions are mounted according to their numbers and not by their UUIDs. Take a look at your /etc/fstab. If the partitions are identified by UUID there should be no problems. But if there are /dev/... lines the number should be corrected if they were changed.

---

### Post by Mark Phelps on 2016-05-18
The problem with the material you posted is that it reads like the poster used GParted or the Ubuntu installer to shrink the Win8 OS partition to make room for Ubuntu, and that is known, in some cases, to corrupt the Windows filesystem -- rendering Windows unbootable.

It has nothing whatsoever to do with GRUB; instead, it is using the WRONG tool to mess with Windows filesystems.

You didn't say how far you got into the Win10 "upgrade", or what OS you are trying to boot now.  Please provide details on your situation, instead of someone else's situation.

Also, what is it you want to boot now -- Ubuntu or Win10?

We can proceed after you provide the answers.

---

### Post by matti123456 on 2016-05-18
I was not actively following the installation, last time i checked the installation process was at around 20%. I have a theory of what happened. Since I have set Ubuntu to boot as a default, it is possible that my computer restarted during the installation and thus disrupted the installation.

I am planning to format my hard drive and make clean install of Win10 and Ubuntu, but i need to download Win10 ISO first. I was under impression that Windows store was needed to download the ISO, that is why i installed Win10 just before formatting hard drive.

---

### Post by yancek on 2016-05-18
>  the installation process was at around 20%.

Installation process of what?  I'm not sure I'm reading your comment correctly, why would you install windows 10 and then format the drive (basically deleting everything)?

You don't need to be on windows to download an iso of their system.  I downloaded the windows 10 iso last week from Linux so I'm not sure what you're doing.

When do you see the error you report?  Is it on boot when selecting Ubuntu? windows? some other OS?

---

### Post by matti123456 on 2016-05-18
> **yancek said:**
> Installation process of what?  I'm not sure I'm reading your comment correctly, why would you install windows 10 and then format the drive (basically deleting everything)?

You don't need to be on windows to download an iso of their system.  I downloaded the windows 10 iso last week from Linux so I'm not sure what you're doing.

When do you see the error you report?  Is it on boot when selecting Ubuntu? windows? some other OS?

Like i said in my last post, i thought that Windows app store was needed to download it.

I decided that i am just going to format, install Win7 and upgrade to Win10.

---

