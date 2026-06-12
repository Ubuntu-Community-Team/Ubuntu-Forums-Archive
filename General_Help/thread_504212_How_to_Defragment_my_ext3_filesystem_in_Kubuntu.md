---
title: "How to Defragment my ext3 filesystem in Kubuntu?"
date: 2007-07-18
forum: General Help
---

### Post by bg1256 on 2007-07-18
I am simply curious if there is a program that will defragment my HD as in Windows.

I searched the pacakge manager, and I only found a program that will defrag an ext2 filesystem.

I hope this isn't too n00bish, but I'm hoping someone can help.  Thanks!

---

### Post by jediborger on 2007-07-18
The program defrag that you found will still work for ext3. In a nutshell ext3 is just ext2 with a journal that helps recover files in the event of a power/computer failure. So go ahead and install defrag, but you shouldn't have anywhere near the problems you had in Windows because of the way unix filesystems save files. This topic is a little lengthy and technical but here's a link if you want further reading.
[http://www.whylinuxisbetter.net/items/defragment/index.php]("http://www.whylinuxisbetter.net/items/defragment/index.php")

---

### Post by trak87 on 2007-07-18
ext2/3 is better designed than other filesystems so you don't need to defrag these partitions. It's pointless in Linux.

---

### Post by HermanAB on 2007-07-18
Here is a very efficient defrag program for Ext3:

void main()
{
  printf("Defrag start...\n");
  sleep(10);
  printf("Done!\n");
}

Cheers,

Herman.

---

### Post by trak87 on 2007-07-18
<hehe>

---

### Post by bg1256 on 2007-07-24
I do understand that Linux doesn't require defragging as Windows does; however, I was curious as to how to go about doing so should I need to. Thanks for the help.

---

### Post by kuja on 2007-07-24
To use the ext2 defrag program I think you need to first convert the ext3 partition to ext2, run the defrag, and then convert back.

---

