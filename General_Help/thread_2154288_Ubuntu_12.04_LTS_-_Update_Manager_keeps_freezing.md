---
title: "Ubuntu 12.04 LTS - Update Manager keeps freezing"
date: 2013-06-14
forum: General Help
---

### Post by WeAreLinux on 2013-06-14
Good Morning

When using Update Manager in Ubuntu 12.04, it keeps freezing. I get the "Applying changes" screen after password auth but it just sits there @ waiting (this was for a good 5 mins today). So I cancelled, rebooted, and updated via terminal (sudo apt-get update --> sudo apt-get upgrade --> sudo apt-get dist-upgrade) which did not raise any issues (although it did not downloaded anything, just went straight to installing new packages....I'm guessing Update Manager already fetched the new packages during my issue ? :-/ ) I was able to update yesterday with UM without any problems, but that was just one minor security update (less than 1MB). Today, I had 10 updates to download (including new kernel update - linux-image-3.2.0-48-generic-pae 3.2.0-48.74) when it froze again. Suggestions?

Related questions: 

1) Since this was my first time using terminal to update, just want to confirm I used the right commands: sudo apt-get update --> sudo apt-get upgrade --> sudo apt-get dist-upgrade . This will ensure my system gets all the necessary security and recommended updates correct?

Thank You

---

### Post by mörgæs on 2013-06-14
> **WeAreLinux said:**
> 
Since this was my first time using terminal to update, just want to confirm I used the right commands: sudo apt-get update --> sudo apt-get upgrade --> sudo apt-get dist-upgrade . This will ensure my system gets all the necessary security and recommended updates correct?


Yes. After that you can finish with a ```
sudo apt-get clean
``` in order to free a little disk space.

---

### Post by fantab on 2013-06-15
> **WeAreLinux said:**
> 
1) Since this was my first time using terminal to update, just want to confirm I used the right commands: sudo apt-get update --> sudo apt-get upgrade --> sudo apt-get dist-upgrade . This will ensure my system gets all the necessary security and recommended updates correct?

The command 'sudo apt-get dist-upgrade' can remove packages and install new packages unlike 'sudo apt-get upgrade which only Upgrades your existing packages'. So carefully read the output of 'dist-upgrade' before you enter 'yes' to continue.

Generally:
```
sudo apt-get update && sudo apt-get upgrade
```

should be fine.

---

### Post by WeAreLinux on 2013-06-15
Hmm I thought you'll need to run sudo apt-get dist upgrade everytime there's a kernel update --> [http://askubuntu.com/questions/274557/update-manager-asking-me-to-update-kernel-but-apt-get-upgrade-does-not](http://askubuntu.com/questions/274557/update-manager-asking-me-to-update-kernel-but-apt-get-upgrade-does-not)

Guess I'll just continue using terminal to update my system. Trying to solve the freezing issue with UM would probably be more of a hassle. 

Thnx for the replies

---

### Post by fantab on 2013-06-16
Yes, only if you notice that the kernel is not upgraded/updated. The apt-get would tell you that.

'Synaptic Package Manager' is a great tool to have. you can install it with 'sudo apt-get install synaptic'.

---

