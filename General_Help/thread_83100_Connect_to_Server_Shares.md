---
title: "Connect to Server Shares"
date: 2005-10-27
forum: General Help
---

### Post by jakev383 on 2005-10-27
I went to my Places menu, and selected the Connect to Server option.  I created a sftp share to my home box, and it shows on the desktop in Gnome.  What I want to know, is how to get to this share from the command line?  I wanted to create a tar.gz file, and have it dumped directly to the sftp share drive.  Is there a sym link to this somewhere that I'm just missing, or would I have to manually add an entry to my fstab to get what I'm looking for?
Thanks in advance.

---

### Post by jakev383 on 2005-11-11
Anyone have any advice?

---

### Post by Dr. Nick on 2005-11-11
no symlink I dont think. Never done it before though but i dont see an link when using samba. You can connect to the ftp in the command line by unning "ftp" then "open IPADDY" which may or may not help. Hopefully someone has more specifics

---

### Post by jakev383 on 2005-11-11
That is a possibility. I have a server I connect to for the files I use at work. Since I use a couple different machines, I'd like to rsync the files to my mobile machines. I don't want to have to run netfs on it, since I never know what IP I may be coming from. Was hoping the 'Connect to Servers' thing made a link somewhere on the system so I could access it via CLI. I don't always need to be connected to it, but it would be nice to be able to use it from the CLI if I needed to.
Thanks, though.

---

