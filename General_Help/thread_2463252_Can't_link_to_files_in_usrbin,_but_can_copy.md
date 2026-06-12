---
title: "Can't link to files in /usr/bin, but can copy"
date: 2021-06-07
forum: General Help
---

### Post by phssthpok2 on 2021-06-07
On Ubuntu 20.04, I am trying to create hard links to some essential tools in /usr/bin for use inside a chroot jail. When I try, I get an "Operation not permitted" error. My current workaround is to copy the necessary files to my home directory, and then create links to them there whenever I construct the jail, but of course they won't get updated if the originals do.

Why is this happening, and is there any way around it?

---

### Post by mIk3_08 on 2021-06-07
Did you try to use this command;
```
sudo chmod
```
as administrative user to acquiring root permissions?
super user do is very important in Ubuntu Linux Operating System this is the administrator command and a powerful command among Ubuntu users
Now that you have the power, be sure to be safe when you issue your commands. I don't think there is a su-undo, just becareful. Good Luck.

---

### Post by scorp123 on 2021-06-07
> **mIk3_08 said:**
>  Did you try to use this command;
```
sudo chmod
```


Why that command?? He doesn't need to take ownership. Everything inside /usr/bin belongs to "root". Anything else is asking for trouble.

---

### Post by scorp123 on 2021-06-07
Hardlinks have to be on the same filesystem, because you're basically addressing the same inodes on the disk, just with 2 x (or more) different filenames at the same time. If source and target filesystems are not on the same disks then hardlinks will fail. Did you try symbolic links? Will those work for your purpose?

---

### Post by HermanAB on 2021-06-07
A hardlink is just another name for the same file.  It cannot work across different partitions/file systems. Technically, it could work on multiple disks if the disks form an array, with one file system across them all.

---

### Post by phssthpok2 on 2021-06-07
> **HermanAB said:**
> A hardlink is just another name for the same  file.  It cannot work across different partitions/file systems.
/usr/bin and the directory under /home where my sandboxes go are both within the root directory mounted on /dev/sda5 according to df.

---

### Post by phssthpok2 on 2021-06-07
> **mIk3_08 said:**
> Did you try to use this command;
```
sudo chmod
```
as administrative user to acquiring root permissions?
super user do is very important in Ubuntu Linux Operating System this is  the administrator command and a powerful command among Ubuntu users
Now that you have the power, be sure to be safe when you issue your  commands. I don't think there is a su-undo, just becareful. Good  Luck.
This doesn't help because (a) I don't want to use sudo (or setuid root!) to run the script to create my sandboxes, and (b) I have r-x access to everything in /usr/bin and write access to the directory I'm trying to create the link in, which should be enough.

---

### Post by phssthpok2 on 2021-06-07
Symbolic links won't work from inside a chroot jail.

---

### Post by SeijiSensei on 2021-06-07
I've run a few programs in chroot environments. I've always had to copy over anything I needed from /etc, /lib, etc., into the equivalent locations in the jail. No links, but actual copies of the files.

---

### Post by scorp123 on 2021-06-07
> **phssthpok2 said:**
> Symbolic links won't work from inside a chroot jail.

Riiight, I forgot about the jail part. Alternative: Docker containers maybe? I find they are easier to work with than jails anyway...

---

### Post by phssthpok2 on 2021-06-09
> **SeijiSensei said:**
> I've run a few programs in chroot environments. I've always had to copy over anything I needed from /etc, /lib, etc., into the equivalent locations in the jail. No links, but actual copies of the files.Which is very inefficient if you're setting up sandboxes dynamically, as I am. Linking is much faster and more efficient.

As I said, my workaround is to make copies of all the necessary files in a directory under /home, and then create hard links to those copies. This means I only have to copy the files once, but it means I have to re-copy them every so often if there are updates (but a cron job can check each file against the original and copy them if there are any changes).

I assume it's some sort of security policy that Ubuntu is applying -- I created a file /foo (as root) and couldn't link to that either, but when I made myself the owner instead of root, it worked. Can't find anything in the docs that explains this.

---

### Post by phssthpok2 on 2021-06-09
> **SeijiSensei said:**
> I've run a few programs in chroot environments. I've always had to copy over anything I needed from /etc, /lib, etc., into the equivalent locations in the jail. No links, but actual copies of the files.The problem that this is inefficient when you're dynamically creating sandboxes (as I am) and you have to copy the files into each one. My workaround is to copy the files I need into a directory under $HOME, and link to those, with a cron job to check each of them periodically and re-copy them if the originals have changed.

Experiments show that I can't create hard links to ANY file that I don't own -- not just files owned by root, but files owned by absolutely anyone except myself. Perhaps ln tries to create the links with the same ownership as the original file? Can't see anything in the docs about this...

---

### Post by phssthpok2 on 2021-06-09
Oops. Couldn't see reply #11 and assumed I'd forgotten to hit submit, so posted again #12. Is there a way to delete messages here?

---

### Post by phssthpok2 on 2021-06-09
> **SeijiSensei said:**
> I've run a few programs in chroot environments. I've always had to copy over anything I needed from /etc, /lib, etc., into the equivalent locations in the jail. No links, but actual copies of the files.You can also use mount -bind for /lib, /lib64, /dev and /proc.

---

### Post by phssthpok2 on 2021-06-09
> **phssthpok2 said:**
> Perhaps ln tries to create the links with the same ownership as the original file?Silly me, of course it is, since ownership & permission info is in the inode, not the directory entry...!

---

