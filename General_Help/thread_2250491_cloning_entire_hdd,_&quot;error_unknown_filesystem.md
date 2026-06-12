---
title: "cloning entire hdd, &quot;error: unknown filesystem&quot;, succesful many times, 12.04"
date: 2014-10-29
forum: General Help
---

### Post by SciGuy1872 on 2014-10-29
I have used EaseUS on the Windows partition to clone the entire disk to another hdd many times, but after the Intel splash screen and when the disk tries to activate, I get the report: 

                 error: unknown filesystem
                 grub rescue>

I can browse the disk from the good one and see that the data is there and I cannot issue commands--there are just the two error lines.  I have used EaseUS Todo Backup twice (the particular program an old download with the error occuring both times) and have also tried to clone using a new release of EaseUS TB that I downloaded from the Linux partition (the other side is Windows XP, EOL).  After the program was downloaded, I moved it to the Windows partition.  
  I was wondering if someone could provide a fix?  Maybe the programs don't copy Grub for some reason (it worked 10 times, though and TB specifically states that the MBR is cloned); or maybe someone could list cloning programs for the entire disk under Ubuntu--I know that opinions are less valuable on this site than answerable questions, so maybe just list popular cloning programs that are graphical and easier to install.
  I was also wondering about the speed of the process--I have two 120GB drives and to clone, it takes 10 hours--that seems like there is a problem. 
Thanks for your time!
  Sciguy

---

### Post by sudodus on 2014-10-29
Do you want a direct clone, or do you want a compressed image?

-o-

The basic cloning tool is ***dd***, nicknamed 'disk destroyer'. It works in most cases, but it is a last resort, because it is risky. A small typing error, and you overwrite what you wanted to backup/clone/save.

***Clonezilla*** is another option. It has menus in text mode, and is much safer. It works well to clone / make image of an entire disk. I use it regularly. Download the iso file of the stable version and make a live CD/DVD/USB drive.

Clonezilla is faster than dd, because it skips free space, it only copies used blocks. The speed depends very much on the hardware, maybe 0.5 - 5 GB/minute including compression. If there are 100 GB of data, you might need 1-2 hours, but you might need 10 hours, depending on hardware.

---

### Post by slickymaster on 2014-10-29
> **sudodus said:**
> Do you want a direct clone, or do you want a compressed image?

-o-

The basic cloning tool is ***dd***, nicknamed 'disk destroyer'. I works in most cases, but it is a last resort, because it is risky. A small typing errors, and you overwrite what you wanted to backup/clone/save.

***Clonezilla*** is another option. It has menus in text mode, and is much safer. It works well to clone / make image of an entire disk. I use it regularly. Download the iso file of the stable version and make a live CD/DVD/USB drive.

+1 to Clonezilla.
Here's some useful documentation to help you get started: [Clonezilla live doc]("http://clonezilla.org/clonezilla-live-doc.php") and [Related Articles of Clonezilla]("http://clonezilla.org/related-articles/")

---

