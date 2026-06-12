---
title: "truecrypt - mount as ext3"
date: 2007-11-25
forum: General Help
---

### Post by tbrothers on 2007-11-25
Ubuntu server 7.10 and gnome 2.2

I followed the installation instructions on the following page and it worked Great!  Thanks 
[http://www.howtogeek.com/howto/ubuntu/install-truecrypt-on-ubuntu-edgy](http://www.howtogeek.com/howto/ubuntu/install-truecrypt-on-ubuntu-edgy)

I can mount a TC volume just fine as FAT but I would like to mount as ext3.  I have created a volume using "truecrypt -c" and selected NONE as the file system type.

I can mount it as FAT just fine using ...
truecrypt -u /home/terry/truecrypt.tc /mnt/tc-mount

I would expect this to work for ext3 but it doesn't ...
truecrypt --filesystem ext3 /home/terry/truecrypt.tc /mnt/tc-mount

Any ideas?

BTW - I CAN mount as ext3 using forcefield (the truscrypt gui) but I prefer the command line.

Thanks,
Terry

---

