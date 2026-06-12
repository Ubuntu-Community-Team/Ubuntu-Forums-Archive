---
title: "I deleted the swap drive and now ubuntu won't boot"
date: 2019-03-31
forum: General Help
---

### Post by iamtheeggman2 on 2019-03-31
In a bid to rescue this is booted to the live disc, created a new swap partition, edited the fstab and then copied over the new uuid and it still didn't work. Any ideas?

I tried swap off - a command it did not complain I did anything wrong and after a reboot it still didn't work.

---

### Post by kc1di on 2019-03-31
did you try ```
sudo update-grub
``` Then reboot?

---

### Post by iamtheeggman2 on 2019-03-31
Same result I'll see if I can copy the message

OK well I can't copy it because it complains about permission issues. It's totally useless to have a live cd when it is really needed if you can't edit files or even read them. The drive is not even encrypted.

I give up. I'm going to reinstall it. Its used up hours of my time just to get rid of a swap drive and now I read ubuntu can use a swap file instead.

---

### Post by Dennis N on 2019-03-31
> I deleted the swap drive and now ubuntu won't boot 
if you have recovery mode (or emergency mode) as root:

Fix the resume file located at: **/etc/initramfs-tools/conf.d/resume** to have the new swap UUID.
Also edit the swap entry in your **/etc/fstab** file to have the new swap UUID.
and then run the command:
**update-initramfs -u**

Finally, reboot your system.

---

### Post by iamtheeggman2 on 2019-03-31
OK I'll try it tomorrow. Thanks

Hi thanks, I did the above and I was not presented with any errors however it still won't boot.

I don't suppose there is any Linux equivalent to the Windows restore program?

Found one [https://teejeetech.in/2017/10/01/timeshift-v17-10/](https://teejeetech.in/2017/10/01/timeshift-v17-10/) OK well if nobody has any ideas on the issue of no swap drive I'll have to reinstall. At least the good thing about Linux is its easy to install multiple packages of software at once where as with Windows you got to use spend time on sites like download. Com

Anyway I am going off topic now so I'll await any further responses.

---

