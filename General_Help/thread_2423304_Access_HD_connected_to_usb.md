---
title: "Access HD connected to usb?"
date: 2019-07-20
forum: General Help
---

### Post by PDA1 on 2019-07-20
I'm running Ubuntu 18.04 Mate.

While running 18.04 I have plugged in a usb to sata cable and have connected the old Ubuntu 12.04 ssd to it.

The only problem is I can't access the files in the 12.04 hd home directory where all my pictures and documents reside.  I assume that's because the there's a password associated with the hd as it's a "stand alone" system.

Any idea how I can access my files in the old 12.04 while connected to the above mentioned cable when running 18.04?

Thank you,

Paul.....my name...today

---

### Post by SeijiSensei on 2019-07-20
Do you have the identical user ID and group ID on both machines? Are you getting "permission denied" messages, or can you not connect at all?  If so, you can avoid this problem by copying the files using sudo to get root privileges.  Before getting deep in the weeds, you need to tell us exactly what errors you are encountering.

---

### Post by PDA1 on 2019-07-20
The user and group ID are different.  When I click on the "home folder" there are 2 links in the folder.  One of them reads;

Access-Your-Private-Data.desktop

....the other says 

README.txt

When you click on the link- "Access-Your-Private-Data.desktop"

Here's what appears;

[ATTACH=CONFIG]283646[/ATTACH]

---

### Post by SeijiSensei on 2019-07-20
Is the data on the 12.04 drive encrypted? I don't know how to deal with that; I never use encryption.

---

### Post by TheFu on 2019-07-20
If you used LVM+LUKS on the 12.04 system, then you should be able to "activate" the LVM using **sudo vgchange -ay**, then as you double-click onto the different LVs, a prompt for the LUKS decryption key should be provided.  My 'mate' install did this through caja.

If it is HOME directory encryption, there is a how-to guide (google will find it), for gaining access to encrypted home directories in ubuntu.

If you don't know the password or key, forgetaboutit.

---

### Post by PDA1 on 2019-07-20
I don't know if it's encrypted.  How can I check?  Perhaps during initial installation of 12.04 to the hd it asked, "do you want to encrypt your home folder".  Knowing me I probably answered "yes".

---

### Post by PDA1 on 2019-07-20
Yes, happily I do know the passwords. 

Now, exactly what does **sudo vgchange -ay" **do?

It's not going to lockup or vaporize my data...will it?  I'm famous for using DD to wreck drives and using other commands late at night to wreak havoc on myself.

---

### Post by TheFu on 2019-07-20
If you want to know exactly what any command does, then reviewing the manpage is the only correct method.
**man vgchange**
I can't imagine it would do any harm.

---

### Post by PDA1 on 2019-07-20
Here's what I get;[B]

$ man vgchange
No manual entry for vgchange


[/B]

---

### Post by SeijiSensei on 2019-07-20
[https://linux.die.net/man/8/vgchange](https://linux.die.net/man/8/vgchange)

> -a, --activate [a|e|l]{y|n}
    Controls the availability of the logical volumes in the volume group for input/output. In other words, makes the logical volumes known/unknown to the kernel. If autoactivation option is used (-aay), each logical volume in the volume group is activated only if it matches an item in the activation/auto_activation_volume_list set in lvm.conf. Autoactivation is not yet supported for partial or clustered volume groups. 


However if your 18.04 machine doesn't have this man page, then it's likely the LVM utilities are not installed.  My machine doesn't have these because I didn't choose encryption during installation. You might need to install the lvm2 package.

See [http://manpages.ubuntu.com/manpages/bionic/man8/lvm.8.html](http://manpages.ubuntu.com/manpages/bionic/man8/lvm.8.html)

---

### Post by TheFu on 2019-07-20
Ok, I made a mistake. If LUKS is being used, first you'll need to open the LUKS encrypted partition using something like this:
```
sudo cryptsetup luksOpen /dev/sdX5 c720
```
You'll need to determine the specific device partition and probably need to know the correct "name" for the encrypted contents. Back in 14.04, the default name was the hostname. In the command above, c720, was the hostname.  It will prompt for the LUKS unlock key/passphrase.

I'm not convinced that LUKS is likely in your situation.  Did you have to enter a password at boot to access the machine or did it sorta "just work" when you logged in?  If the latter, that's HOME directory encryption.  If the former, that's LUKS encryption.

---

