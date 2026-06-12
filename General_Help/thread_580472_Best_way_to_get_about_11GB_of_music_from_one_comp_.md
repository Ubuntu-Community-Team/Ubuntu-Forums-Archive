---
title: "Best way to get about 11GB of music from one comp onto another"
date: 2007-10-18
forum: General Help
---

### Post by rainwalker on 2007-10-18
I'm thinking about doing a fresh install of Gutsy (currently on Feisty) but I want to save my music. It's 10.7 gigs, so obviously it'd be a pain to import it all again. A friend of mine said I should make a torrent, but that would be stupid because I'd be the only one seeding.
We do have an external hd, but I don't know if it has enough space. Plus, it's plugged into our Windows box for backup (of course).
Are there any other efficient methods besides 
- Burning it all to CDs/DVDs
- Copying to an external hd, then importing it back
or are those the only options?

---

### Post by p_quarles on 2007-10-18
Does the Windows box have enough room to store the files temporarily? Are the two connected to each other via the LAN?

If yes to both, this should be pretty easy. 

On the Feisty box:
```
sudo apt-get install openssh-server
```
On the Windows box: download and install Filezilla. Figure out the LAN address of the Ubuntu machine, load up Filezilla on the Windows machine, select the "sftp" protocol, and login as your normal Ubuntu user. You should be able to navigate to the music directory and grab all the files onto the Windows machine. 

Once you're done with the fresh install, install openssh-server again, and then use Filezilla to upload the music files back to Ubuntu.

---

### Post by rainwalker on 2007-10-18
Hmm...alright, that sounds like something a 15-year-old could do, thanks :)

---

### Post by riggits on 2007-10-18
You could burn 3 DVDs and fit it all easily. 

Here's my solution: run Samba on your linux machine. It can access your Windows workgroup, you can browse to the Win machine and copy files or whatever you like. Just set up the share permissions (on Win machine) first.

---

### Post by Keshik on 2007-10-18
This link let me set up a shared folder between windows and ubuntu in about 10 minutes.

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

