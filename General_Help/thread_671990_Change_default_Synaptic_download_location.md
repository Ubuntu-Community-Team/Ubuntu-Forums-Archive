---
title: "Change default Synaptic download location"
date: 2008-01-19
forum: General Help
---

### Post by masher_oz on 2008-01-19
Hi All

Is there a way to change the default download location for Synaptic?

My current linux parition is quite small, but I have a nice new 200Gb HDD sitting next to it. I would like to be able to download packages to the other drive (so that I don't have to delete them) but still have them play nicely with the installation process.

The main reason is that I am still playing around with different programms, and have found myself downloading the same package several times. In order to get out of blowing up my download limits, I'd like to reuse the same downloads. /var/cache/apt/archives is empty (BTW)




cheers

---

### Post by dabang on 2008-01-19
You could just mount the partition to "/var/cache/apt/archives". If you don't run "apt-get clean" the downloaded packages should stay there. I'd recommend doing a backup of the directory first, creating a new one and then mount the partition:
```
sudo mv /var/cache/apt/archives /var/cache/apt/archives_bk
sudo mkdir /var/cache/apt/archives
sudo mount /dev/sdXX /var/cache/apt/archives/
```

---

### Post by capink on 2008-01-19
Synaptic is a fontend for apt. To change the apt-get download location look [here]("http://ubuntuforums.org/showpost.php?p=3125012&postcount=3").

---

### Post by masher_oz on 2008-01-19
Cheers both for that. Guess I can called it solved now...

---

### Post by masher_oz on 2008-01-20
This is what I did:

I made the following directory structure:

```

 /media/ubuntuFiles/allPackages/archive/partial/

```

I copied the contents of /var/cache/apt/archive/partial into the equivalent directories above

then added (had to create the file too) the following to /etc/apt/apt.conf

```

Dir::Cache "media/ubuntuFiles/allPackages";
Dir::Cache::archives "archives/";

```


Works for me.

I left a readme.txt file in the /var/.. structure to remind me what I did  ;)

---

