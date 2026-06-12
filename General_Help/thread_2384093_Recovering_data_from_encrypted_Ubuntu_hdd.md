---
title: "Recovering data from encrypted Ubuntu hdd"
date: 2018-02-02
forum: General Help
---

### Post by yuriz3r0 on 2018-02-02
Hello, I have a similar issue. Someone's laptop that was running Ubuntu broke, and I put the HDD in another laptop. I am trying to recover the data from it as it is very important, but I'm unsure how I should access it.
I do not know what Ubuntu version he used. I have downloaded the latest Ubuntu version and I made a bootable USB with it. 
I have managed to see the HDD contents to some degree, I do no have access to the important files.
When I try to access the root or the /home/username files it tells me that I do not have permissions. The OS had a password for the user.
I'm still trying to figure this out, but time is pressing me so if someone could help me I'd be grateful.
Thank you in advance

[IMG]https://i62.servimg.com/u/f62/12/84/80/29/imag1411.jpg[/IMG]

---

### Post by coffeecat on 2018-02-02
Post moved to its own thread.

@yuriz3r0, welcome to the forum. Please start your own threads rather than resuscitating old, inactive ones. You are more likely to get help that way.

The screenshot shows that you are trying to access the /root folder. Don't bother. That is root's home folder. There is nothing of use there.

However, you say that you are not able to access the /home/username folder, where personal data will be held. Please detail exactly what permission error you get for that, and then someone will be able to help.

---

### Post by yuriz3r0 on 2018-02-02
Thank you for your prompt answer. The same error occurs when I try to acces that as well. Even if I do it in the terminal, I get Permission denied. [[image]("https://i62.servimg.com/u/f62/12/84/80/29/imag1412.jpg")]
I also tried to mount it using the sudo command to media, but it gives the same error. 
I managed to find some info about recovering the encryption key with "sudo ecryptfs-recover-private", but it also gives me access denied after it finds the key. [[image]("https://i62.servimg.com/u/f62/12/84/80/29/imag1413.jpg")]

UPDATE: I have managed to access the folder using the terminal with the commands [[image]("https://i62.servimg.com/u/f62/12/84/80/29/imag1414.jpg")]
sudo su
cd /media/mountedplace/home/username

But it only lists me a readme and an "acces-your-private-data.desktop". Which I managed to see in kali without having to do this, by just directly navigating in the files.

---

### Post by coffeecat on 2018-02-02
I see. The home folder is encrypted. That's a whole different ball-game. I'll amend your thread title to include that information so that those with experience of encrypted systems can help.

Question: is this a friend's laptop that you are trying to help?

---

### Post by yuriz3r0 on 2018-02-02
Yes, it's a friend that I'm trying to help. His laptop broke, but the HDD is still functional apparently. I'm trying to recover his data, but he had a password, so I believe his data is encrypted.
I took his HDD out and put it in my laptop (I can only have one HDD at a time). I made a bootable USB with Ubuntu 16.04.3 LTS version, and I'm trying to access his files to save them.
I tried booting from the HDD, but apparently there are conflicts and Ubuntu doesn't start up at all. It's stuck before showing the login screen I think... it's only text that's shown. It's a totally different laptop.
 I didn't mingle with those things in over 6 years, so consider me at beginer level.

PS: If I try to boot into the Ubuntu from his HDD it shows me this: [[image]("https://i62.servimg.com/u/f62/12/84/80/29/imag1415.jpg")]
And if I use single user it gets stuck at this: [[image]("https://i62.servimg.com/u/f62/12/84/80/29/imag1416.jpg")]

---

### Post by oldfred on 2018-02-02
Your screen shows 12.04, which is now obsolete.
You need to explain to friend that he needs to keep system updated to current versions.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

And the entire purpose of encryption is to prevent access to data. Therefore recovery is often impossible. So good backups are a requirement.
       discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery) 


I do not know encryption, but have some links that may help.
 Encrypted /home
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Mount_Passphrase](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Mount_Passphrase)

---

### Post by QIII on 2018-02-02
Closed for Staff review.

---

### Post by QIII on 2018-02-02
This thread will remain closed.

If the friend is available and has the password, the links provided by oldfred will be helpful.

Absent that, any help provided would be tantamount to providing instructions for password cracking, a subject forbidden on the Ubuntu Forums.

---

