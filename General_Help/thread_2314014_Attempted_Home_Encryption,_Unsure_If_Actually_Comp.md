---
title: "Attempted Home Encryption, Unsure If Actually Completed"
date: 2016-02-17
forum: General Help
---

### Post by Alcidious on 2016-02-17
Hi all,

Been having many issues with encryption. I decided to delete all the data and partitions on my desktop PC, and switch from from Ubuntu to Kubuntu 14.04 LTS. Given my recent issues, I debated whether or not to do the LVM Encryption of the Home Folder, but eventually decided to do so. But I did not run the process until a week or so after installation. When the Update Box appeared, and hit "Record PassPhrase Now".

I used a Password Manager to come up with something good, but instead of typing it in to the terminal, I did a terminal paste. From what I can tell, the process never finished or didn't work. Here is what the screen displayed:

[ATTACH=CONFIG]267358[/ATTACH] 

In case you can't read it: 

Passphrase:
Usage:

ecryptfs-unwrap-passphrase [file]
or
printf "%s" "wrapping passphrase" | ecryptfs-unwrap-passphrase [file] -

[Enter]

After a while, I tried to exit, couldn't, and closed the terminal. When I tried to enter the strong phrase I put it, it gave me an error: "Unwrapping passphrase fialed [-5], Info: check system log for more info from libecryptfs.

However, when I input my regular Home Passphrase, it did unwrap and proved a string of characters (that I stored safely).  What the heck happened? 

Is there anyway to check if a file was created?

If I shutdown my system, will I be locked out?

Can I re-run the process to ensure it was done correctly?

Thanks!

---

### Post by sandyd on 2016-02-17
What's the output of
```

sudo ls -lA /home/*username*/
sudo ls -lA /home/.ecryptfs/*username*
mount -l

```

The /home/.ecryptfs folder stores configuration and encrypted volumes for the user, so if encryption is working, you should be able to see the mounted ecryptfs volume along with the ecryptfs config.

---

