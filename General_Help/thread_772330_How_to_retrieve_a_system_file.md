---
title: "How to retrieve a system file"
date: 2008-04-28
forum: General Help
---

### Post by Ebc1de on 2008-04-28
I have seemingly introduced some errors in a couple of my /usr/include/.. files while trying some experiments, without saving a copy of the original version first :(. How can I retrieve the original files from my install CD? I have done the following steps -

sudo mkdir /mount/iso
sudo mount -t iso9660 ubuntu-7.10-desktop-i386.iso /mount/iso -o loop

I can see various files and directories in /mount/iso but they are obviously not in the std. linux tree form. How do I find the files in the image? 

The "find" command did not yield anything. If not from the iso image, can I download these files from somewhere?
Thanks.


EH

---

### Post by ryanhaigh on 2008-04-28
You could try finding what packages the files belong to and reinstalling those packages. I think apt-file might be able to tell you that information.

---

