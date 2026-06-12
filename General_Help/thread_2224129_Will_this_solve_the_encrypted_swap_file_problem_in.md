---
title: "Will this solve the encrypted swap file problem in 14.04?"
date: 2014-05-14
forum: General Help
---

### Post by Alley_Oop on 2014-05-14
**I found this solution using Google but I am not sure if should try it. I don't want to wreck my Ubuntu install. Maybe someone can tell me if the following will really work without causing damage.**
[HR][/HR]
There is another serious bug. I'm not sure if it only exists in Kubuntu  or also in other Trusty flavours: If you encrypt your home partition  with ecryptfs, your swap partition will also be encrypted - but it will **not** be available in your system! swapon -s will report nothing.

I have the following entry in /etc/fstab:

 ```

# swap was on /dev/sda5 during installation
#UUID=1a50c1a7-cbcd-43ed-a835-8c153b253950 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0 

```

and /etc/crypttab had the follwing entry:

```

cryptswap1 UUID=1a50c1a7-cbcd-43ed-a835-8c153b253950 /dev/urandom swap,cipher=aes-cbc-essiv:sha256 

```

Although the UUID was identical, swap was not available. Another  strange thing is that sudo blkid reported a different UUID for  /dev/sda5.

In a discussion I had in another forum, a guy presented a solution that works for me:

1. Execute sudo fdisk -l and make sure that the partition shown in the  output is identical with the partition mentioned in /etc/fstab during  installation - in my case /dev/sda5.
2. Follow these steps:

```

sudo -s
umount /dev/sda5 #Replace this by the swap partition used in your system!
mkswap /dev/sda5 # Use the UUID from the output in the following line!
echo "RESUME=UUID=143c43d8-0a77-4d62-a7ae-f53a8e0229a9" > /etc/initramfs-tools/conf.d/resume
echo "cryptswap1 /dev/sda5 /dev/urandom swap,cipher=aes-cbc-essiv:sha256" > /etc/crypttab
update-initramfs -u
exit 

```

3. Reboot.
4. Swap should now be available. You can confirm this by executing swapon -s. The output should be someting like this:

```

Filename                                Type            Size    Used    Priority
/dev/mapper/cryptswap1                  partition       8787964 0       -1

```

**Original author of this solution: UNKNOWN**

---

### Post by Alley_Oop on 2014-05-18
Since I got no responses I finally decided to try this and it worked.

---

### Post by Mr.Goose on 2014-06-15
@ Alley_Opp. Your solution fixed the problem for me too, where other solutions had failed. FYI I'm running Kubuntu 14.04 AMD64, installed from pendrive onto a Crucial MX100 SSD.

My issue was that the UUID of the swap partition seems to change with every reboot. But identifying the swap from its block device name works just fine and survives a reboot. Many thanks for posting.

---

### Post by toffuuu on 2014-06-23
tried this solution and it did not work for me at all...  and Im running Xubuntu 14.04....  and swapon -s shows nothing really   just has Filename Type Size Used and Priority   but its all not there at all...
so yea  not to sure whats going on here...

---

### Post by obake2 on 2014-06-23
> **toffuuu said:**
> tried this solution and it did not work for me at all...  and Im running Xubuntu 14.04....  and swapon -s shows nothing really   just has Filename Type Size Used and Priority   but its all not there at all...
so yea  not to sure whats going on here...

 This thread is marked "solved" by OP (Original Poster), the right people who could help you might not see it since they will think that there is no longer any need to visit this thread. So I recommend you that you create a new thread.


Good luck.

---

### Post by obake2 on 2014-08-01
I want to comment that the solution provided in the 1st post has worked for me.

thank you [[COLOR=#000000]Alley_Oop[/COLOR]]("http://ubuntuforums.org/member.php?u=1923584")[COLOR=#000000] . :D

[/COLOR]
A little disappointing that they didn't fix this for the 14.04.[B]1.
[/B]
Anyways, for future readers: Yes, it works! :D
Just follow the steps carefully, read well. Don't just copy and pate.

---

### Post by felzmann on 2014-09-27
For a permanent solution, I also had to uncomment the following line in /etc/default/grub

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
GRUB_DISABLE_LINUX_UUID=true

Otherwise, the physical device names can get mixed up during boot time if a USB stick is connected for example. In my case the root device sometimes came up as sda and sometimes as sdb meaning the swap partition couldn't be found again.

---

