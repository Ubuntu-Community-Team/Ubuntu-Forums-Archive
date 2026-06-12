---
title: "mp3, play DVDs, rip to mp3 Ubuntu"
date: 2007-03-07
forum: General Help
---

### Post by stchman on 2007-03-07
I have tested the following configuration to watch encrypted DVDs (YAY) and rip CDs to mp3s (YAY).  I have three PCs running Ubuntu 6.10 and all work with these steps.

Run the following command to get all associate codecs for ripping to mp3.
> 
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

After these packages install then you can update juicer to use lame to rip to mp3.

Watching encrypted DVDs do the following:

#Add the gpg key:
> wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

#Add the sources.list entries in a separate file, depending on your Ubuntu release:

# Ubuntu 6.06 "Dapper Drake"
# sudo wget [http://medibuntu.sos-sts.com/sources.list.d/dapper.list](http://medibuntu.sos-sts.com/sources.list.d/dapper.list) -O /etc/apt/sources.list.d/medibuntu.list

# Ubuntu 6.10 "Edgy Eft"
> sudo wget [http://medibuntu.sos-sts.com/sources.list.d/edgy.list](http://medibuntu.sos-sts.com/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/medibuntu.list

# Ubuntu 7.04 "Feisty Fawn"
#sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

# run the update
> sudo apt-get update

# install the medibuntu CSS decryptor, this will install 1.2.9-2medibuntu2 version
> sudo apt-get install libdvdcss2

The preceding is assuming you are using Edgy, use either Dapper or Feisty command line equivalents.

As I said before I can now watch encrypted DVDs (using VLC) and rip CDs to .mp3 (using Juicer).

I hope this helps.

---

### Post by etank on 2007-03-07
Nice. Looks like a good tutorial. Should be helpful in the future.

---

### Post by doncristobal on 2007-03-08
> **stchman said:**
> 
After these packages install then you can update juicer to use lame to rip to mp3.


It's not quite simple to figure out the string that you have to give juicer in order to get proper mp3. but I found a useful HowTo that explaines how it works: [http://ubuntuforums.org/showthread.php?t=295698](http://ubuntuforums.org/showthread.php?t=295698)

---

### Post by stchman on 2007-03-08
> **doncristobal said:**
> It's not quite simple to figure out the string that you have to give juicer in order to get proper mp3. but I found a useful HowTo that explaines how it works: [http://ubuntuforums.org/showthread.php?t=295698](http://ubuntuforums.org/showthread.php?t=295698)

If you go to juicers help and search for mp3 it tells you the exact string to put into it.  That is how I found it.  I just needed the proper encoder for juicer.

---

