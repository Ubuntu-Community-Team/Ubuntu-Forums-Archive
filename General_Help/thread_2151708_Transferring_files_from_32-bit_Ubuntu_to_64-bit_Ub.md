---
title: "Transferring files from 32-bit Ubuntu to 64-bit Ubuntu"
date: 2013-06-05
forum: General Help
---

### Post by Chris62 on 2013-06-05
Hi,

I have just done a clean install of the 64-bit version of Ubuntu and I wondered if the files on the 32 bit version will run properly in the 64-bit version. I want to transfer all my music files and the Rhythmbox playlist to the new installation, but Rhythmbox does not appear to have an "Export" facility. Can I just copy the directory containing the files and if so how is it done, or should I copy the individual files themselves? If I copy the files themselves then presumably I will have to play them all in order to  get a new playlist??

---

### Post by sanderj on 2013-06-05
Non-executable files (like music files) can just be copied.

I'm not sure about executable files, but that should not be needed, as the new install should have the executetables you need

---

### Post by searchfgold6789 on 2013-06-05
To copy music from your old installation to your new one, all you should have to do is open up the old directory that has all your music files in it (usually /home/[username]/Music), and copy the Music folder itself straight into your home directory. (This will not work if you overwrote the system with your music on it when you reinstalled Ubuntu.) Rhythmbox should then update your files from Music - if it does not, open Rhythmbox (boy that word is hard to type) and go to Edit > Preferences. Go to the Music tab and make sure the "Watch my library for new files" box is checked.

If you use Kubuntu, I recommend using Amarok. It's a very advanced, yet easy-to-use music player that comes default in Kubuntu and interacts well with the desktop.

---

### Post by Chris62 on 2013-06-06
Thanks for your mssages sanderj and searchfgold6789. I did as you suggested, searchfgold6789, and it worked first time. With "another operating system" I would probably be tearing my hair out by now. I will give Amarok a try and see if I like it. Thanks fr the suggestion

---

