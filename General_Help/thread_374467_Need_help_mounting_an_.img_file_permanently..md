---
title: "Need help mounting an .img file permanently."
date: 2007-03-02
forum: General Help
---

### Post by tmoneygetpaid on 2007-03-02
ok, so I'm installing xubuntu on a friend's computer. I imaged her entire old hard drive to a single .img file, installed xubuntu, and have the img file in a directory now. I want to just mount this image permanently to her computer, maybe as a folder, so she could just browse it and pull fiiles and whatnot, and was wondering how to do this. do I mount as a loopback? and, if so, will this be permanent/ not something that I will have to redo everytime?

specific terminal commands/ walkthrough would be very much appreciated. thanks so much.

---

### Post by raevin on 2007-03-02
Some of this will help you:

[http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm](http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm)

---

### Post by GoingDown on 2007-03-02
If the image is just raw image of the hard disk partition, this should work:

mount -o loop {image name} {mount point}

You might need to specify -t {filesystem_type}.

To mount it automatically, you can add it to /etc/fstab file

---

### Post by tmoneygetpaid on 2007-03-02
Unix is amazing. That simple mount command allowed me to look at all the files, open and edit them, etc. BUT:

I added the line to fstab:

/home/theimagedir/image.img /new/directory/ ro,auto,user,loop 0 0

and running mount -a gives me;

/home/theimagedir/image.img is not a block device (maybe try '-o loop').

How do I write this option to fstab?

Thanks again.

---

### Post by DavidHuttlestonJr on 2007-03-02
I haven't used the loop option for mount, but it looks to me that you are missing a field in your fstab line.  

 <file system> <mount point>   <type>  <options>       <dump>  <pass>

You are missing the <type> field.

---

### Post by tmoneygetpaid on 2007-03-07
figured it out... had to pass vfat as the filesystem and not iso9660, even though I was mounting an iso9660 image. Yeah, I left it out in the description. shout to my uber-unix roommate.

---

