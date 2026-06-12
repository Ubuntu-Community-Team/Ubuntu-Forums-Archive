---
title: "Extract Files from IMG file"
date: 2008-04-12
forum: General Help
---

### Post by lakshmiteam on 2008-04-12
Hi,

I am fresh to Linux flavor. I created a img file from a bootable CF card. The O/s in CF card is FreeBSD. I created IMG file of the CF card from Ubuntu using "dd" command.

Now in Ubuntu, I want to open the IMG file and see the files and directories.... How should I proceed.

The IMG file gets mounted when I issue,

mount -a -o ro,loop mycfcard.img /media/image

but when I give the following command it gives error.

# cd /media/image
# ls
ls: reading directory .:Input/Output error.

Any help please....

---

### Post by duncan.hawthorne on 2008-04-12
seems like youve done things right, looks like the image is just broken. try it with another

---

