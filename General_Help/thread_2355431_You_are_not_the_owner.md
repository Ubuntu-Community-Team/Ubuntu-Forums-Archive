---
title: "You are not the owner"
date: 2017-03-12
forum: General Help
---

### Post by Gnusboy on 2017-03-12
Hello

I keep running into files I can't access. When I check the permissions, it states "you are not the owner so you cannot change these permissions"

Some of the files are "root" but others can be from different directories. I think that I would need to enter the original password that I set when I first installed Ubuntu 10.04.
But that password has been lost in the feeble brain of old age. I currently use Ubuntu 16.04 with several partitions - including one where I kept Ubuntu 14.04 after installing the new version.
Both partitions work and I can switch to either when I boot. I had this same access problem across the previous installs. 
I can do about 90% of the things I need every day, but it has stopped me from trying some other features.
 
I'm definitely not a Ubuntu guru, even though I've used it for several years. I should know more, but I tend to ignore stuff that I don't regularly use. 
So, if there is a fix for this problem, I'd appreciate the help.
Thanks.

---

### Post by howefield on 2017-03-12
If you give outline a specific issue where you cannot access certain files it would help you get a specific response ?

In general you need elevated privileges to access anything outside of your /home folder, you would most likely want the sudo command and your user account password to get those elevated privileges.

Do you have a current example that you are trying to complete ?

---

### Post by Gnusboy on 2017-03-12
howefield

Thanks for answering.
At the moment, I don't have any specific tasks that would require elevated privileges. 
It is just that I might want to do something, that would require the root password and I can't access it
I understand that I can use the sudo command ... and my user account password ... But the user account is the password I can't remember!
Is there "any" way to find that password? 

I also needed that password to do backups and to restore the backups. I could not get Deja Dup to work without it.

 I also had a big problem recently when I accidentally erased my entire Firefox password file.  I tried all the things I read on how to recover the file, but when I tried to open it.
it was impossible to read. It was complete gibberish and I couldn't figure out how to fix it. I know that this is a Firefox problem, not a Ubuntu problem, but I'd like to figure that out too.

---

### Post by SeijiSensei on 2017-03-12
Follow [these steps](https://wiki.ubuntu.com/RecoveryMode) to boot into Recovery Mode.  When you get a root shell, run the command:
```
passwd your_username
```
(You don't need sudo because you are the root user already in this mode.) 

The Firefox password file is encrypted so it will look like gibberish to you.  You need a copy of logins.json and key.db to repair the damage.  See [https://support.mozilla.org/t5/Install-and-Update/Profiles-Where-Firefox-stores-your-bookmarks-passwords-and-other/ta-p/4608#w_what-information-is-stored-in-my-profile](https://support.mozilla.org/t5/Install-and-Update/Profiles-Where-Firefox-stores-your-bookmarks-passwords-and-other/ta-p/4608#w_what-information-is-stored-in-my-profile)

---

### Post by mastablasta on 2017-03-13
sudo password is also needed for necessary system updates. if you are not doing them i suggest you start. alternatively you can setup unattanded updates but i woul dsuggest you do that only for security updates. tghat way system is automatically patched.

---

### Post by Gnusboy on 2017-03-31
Forgive me SeijiSensei, I got lost in my work and didn't get back until today. Thanks for your response.
Gnus

---

### Post by Gnusboy on 2017-03-31
Thanks mastablasta. I just D/L the manual. It loks like smething I can use as long as I use Ubuntu. (Which I expect to continue using until the dawn of time) Bye-bye Mr. Bill.

---

