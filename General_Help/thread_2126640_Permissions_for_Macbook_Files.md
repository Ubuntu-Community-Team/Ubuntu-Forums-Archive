---
title: "Permissions for Macbook Files"
date: 2013-03-17
forum: General Help
---

### Post by kwkodiak on 2013-03-17
I am using ubuntu to access files on my Macbook Pro hd in order to save some file before reformatting.   However, I get the message that I don't have permission.   Can anyone tell me how to get permission?

Thanks

---

### Post by mike555 on 2013-03-17
Sudo should do it

---

### Post by ajgreeny on 2013-03-17
You may also need the hfsplus and/or hfsutils packages to be able to mount the partition, if you don't have them already installed.

---

### Post by kwkodiak on 2013-03-18
> **ajgreeny said:**
> You may also need the hfsplus and/or hfsutils packages to be able to mount the partition, if you don't have them already installed.

I typed in   "gksudo nautilus"  and gained access; but when I attempt to copy files to my external hard drive I get a message "Error while copying "file name", There was an error copying the file into \media\ubuntu\04c0-2300.   Error opening file permission denied."


It seems all my files are read only.

Will the hfsplus and/or hfsutils packages help with this problem?  and if so where do I get them and do I jet copy them to the boot disk?

Thanks again

---

### Post by ajgreeny on 2013-03-18
You will need to install the hfs packages to your ubuntu OS, I think, if you want to do anything with the files, though you may be able to just copy them even if they are read only.  I am a bit confused as to whether or not you can even see those files using ubuntu.  Is this an installed ubuntu OS or a live OS from CD or USB?

---

### Post by kwkodiak on 2013-03-19
> **ajgreeny said:**
> You will need to install the hfs packages to your ubuntu OS, I think, if you want to do anything with the files, though you may be able to just copy them even if they are read only.  I am a bit confused as to whether or not you can even see those files using ubuntu.  Is this an installed ubuntu OS or a live OS from CD or USB?

It's a live os from a cd and while I can see the files I can't copy them.   how would I install the hfs packages to the Ubuntu os.  ( sorry if this seems to be a dumb question but I  need the step by step instructions)

thanks

---

### Post by mike555 on 2013-03-19
If your using a live CD , you will need another place to save the files to, like an external drive or thumbdrive .

---

### Post by kwkodiak on 2013-03-19
> **mike555 said:**
> If your using a live CD , you will need another place to save the files to, like an external drive or thumbdrive .

Yes. I'm using a thumbdrive

---

