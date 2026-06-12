---
title: "Trouble remastering a LiveCD"
date: 2005-09-23
forum: General Help
---

### Post by MindChild on 2005-09-23
Ok, this shouldn't be rocket-science, but it apparently is. I am trying to make a LiveCD, but no matter how I go about it, I simply can't get the cd to start Ubuntu (This applies to Ubuntu AND Kubuntu 5.04 AND 5.10). The kernel boots. I get asked for my language (English), asked for my location (United States), My keyboard (American English), then it goes onto "Detecting hardware to find CD-Rom drives"... after it finishes, the screen goes red and a message is displayed:

"Non-Ubuntu CD-Rom detected. 
The CD-ROM drive contains a non-Ubuntu CD. 
Please insert the Ubuntu CD to continue with the installation"

I don't have any weird hardware... there is only one CD-Rom drive. I have tried this cd on several machines. To simplify the debugging, here is what I did to make the cd from the original image:

cd /tmp
mount -o loop -t iso9660 /tmp/ubuntu-livecd-504.iso /mnt/cdrom
mkdir ubuntu
cd ubuntu
cp -R /mnt/cdrom/* .
cd ..
mkisofs -r -J -l -V "My Ubuntu Test CD" -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o newubuntu.iso ubuntu

I then burn the ISO, and boot. Against my better judgement, I have tried several different brands of burning software with no luck. I also tried to boot the iso in VMWare with the same results, so I am pretty certain, it has to do with the CD layout, not how I am burning anything.

Any thoughts would be appreciated.

---

### Post by tomchuk on 2005-09-25
You should be using rsync or `cp -Rp` to copy the contents of the CD.

---

