---
title: "Help with partitioning disk"
date: 2006-11-19
forum: General Help
---

### Post by camilluk on 2006-11-19
Hello guys. I need some guidance with this. I know I'm asking a lot of questions here, but I hope one day soon I'll be able to return the favor to other newbies. I'm also planning to rollout Ubuntu to as many friends as I can, and I know I'll run into similar situations, so I want to make sure they're happily Ubunt-ed.

The scenario: I have Ubuntu Edgy Eft installed on my AMD64. The 250Gb HD is partitioned as in the attached screenshot. As you can see, three partitions are NTFS, and sda1 in particular is the primary partition, currently containing my Vista RC1 installation. The other two NTFS parts contain my data, which I already backed up on an external hard disk.

What I want to do: I want to get rid of these three NTFS partitions (and kiss Windows goodbye!), use the resulting free space to create ext3 partitions and put back my data on the new ext3 partitions.

Questions:

1.With sda1 being my primary partition (Ubuntu is on logical partition sda8, will I be able to boot after I delete sda1?

2.Can I make sda8 become my primary partition without making a complete Ubuntu reinstall (I dial-up, so I'd rather avoid having to download all apps etc.)

3.How do I rid of that little 8Mb Pri/Log partition at the bottom of the list? Something tells me it's a terribly important part of the Windows installation (perhaps the MBR?). Pls forgive my ignorance, but if it's not an important piece of disk, I'd like it to be together with the rest of the unallocated space for it to be used. I like to keep things tidy :-D

3.Can you recommend an app to actually do all this, I don't know... a gnome version of cfdisk, somethings that also gives me a visual graph of my HD.

4.When installing Ubuntu, based on something I had read, I tried to layout my ext3 partitions in a way that would make it easier to reinstall Ubuntu if I wanted to, without 
losing configurations, files and apps. The end result is what you see, which I'm pretty sure doesn't do what it was meant to. What would be the best configuration to do that?

5.If you answered to question 4, can I achieve that without reinstalling Ubuntu?

Thank you in advance! :-D
Cam

---

### Post by seshomaru samma on 2006-11-19
You can do everything with Gparted 
Its a graphical partition programme quite similar to partition magic in Windows.
```
sudo apt-get install gparted
```
you can run then with:
```
sudo gparted
```

after you install Gparted , you can post its analysis of your system which is more detailed and more help can be offered, . Basically you can use Gparted to format your NTFS partitions as ext3 and still boot from your original Ubuntu partition without reinstalling, if I understand what you posted correctly
In _my opinion_ the ideal set up for Linux is a small swap partition , a 10GB for the system and the rest for /home

---

### Post by camilluk on 2006-11-19
Thank you! I'll try that. :-)

---

