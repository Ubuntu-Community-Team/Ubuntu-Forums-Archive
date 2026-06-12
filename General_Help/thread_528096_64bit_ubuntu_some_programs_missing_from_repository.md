---
title: "64bit ubuntu some programs missing from repository?"
date: 2007-08-17
forum: General Help
---

### Post by bone2006 on 2007-08-17
I've decided to go with the 64bit ubuntu, since I have the 64bit chip.  Well I was looking for somethings that I always had in the repository and couldn't find.  Is it because these aren't avaiable for the 64bit OS yet?

sun-java6-plugin
flashplugin-nonfree

Another question, is there a command I can type to verify if I'm running 64 or 32 to double check.  I have a lot of CDS laying around and would be nice to verify with a command,

My last question isn't related, but why isn't deluge in the repository for the 32bit nor the 64bit?

---

### Post by bone2006 on 2007-08-17
One more question LOL

I saved this as a how to enable DVD playback, will this work in the 32bit version.  Meaning will these lines that are added to the sources be 64bit compatible?  Here's the commands I used to run in the 32bit version, want to make sure I can just copy and paste in the 64bit version.

Thanks in advance

echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install libdvdread3 libxine1-ffmpeg libdvdcss2

---

