---
title: "chmod /root"
date: 2012-11-03
forum: General Help
---

### Post by Mystic Silverfox on 2012-11-03
O.K., some help would be very much appreciated. I noticed tonight that I had twice copied a directory from my OS X file system, so I started browsing to examine which directories were taking up how much space. In Nautilus I got a permission denied message when trying to access the root user's directory "/root". Did a quick search, ran "chmod -R 777 /root" from "/" in Terminal. CD'd, LS'd, and blank. Went  back to Nautilus, and had blank folder. So, should "/root" be empty on a system only ~1 week old? More importantly, how do I set the permission back to whatever it was? Thank you much.

---

### Post by rnerwein on 2012-11-03
> **Mystic Silverfox said:**
> O.K., some help would be very much appreciated. I noticed tonight that I had twice copied a directory from my OS X file system, so I started browsing to examine which directories were taking up how much space. In Nautilus I got a permission denied message when trying to access the root user's directory "/root". Did a quick search, ran "chmod -R 777 /root" from "/" in Terminal. CD'd, LS'd, and blank. Went  back to Nautilus, and had blank folder. So, should "/root" be empty on a system only ~1 week old? More importantly, how do I set the permission back to whatever it was? Thank you much.

hi
i think if you did a "chmod -R 777 /root" you have to re-install your system :(
much luck - next time

---

### Post by Mystic Silverfox on 2012-11-03
I'm guessing you're saying that because of the possibility of it being recursive? I think specifying "/root" saved me, because before I ran chmod I had also looked at "proc" and noticed some restricted directories that I did not change. At this point, they're still restricted. If it had been recursive, wouldn't that have applied to all directories in "/"?

---

### Post by mcduck on 2012-11-03
Run *chmod -R 700 /root* and you should be more or less fine. Recursive chmod doesn't apply to parent directory or it's contents, only the directory specified in the command and it's subdirectories.

As the /root is root user's home directory, and Ubuntu doesn't have an active root account by default, there shouldn't really be much anything in that directory.

Anyway, when you don't have permissions to access something, the correct way in almost every case is to *increase your user's permissions* (by using "sudo command"), not to change permissions of the system files/directories.

---

### Post by rnerwein on 2012-11-03
> **Mystic Silverfox said:**
> I'm guessing you're saying that because of the possibility of it being recursive? I think specifying "/root" saved me, because before I ran chmod I had also looked at "proc" and noticed some restricted directories that I did not change. At this point, they're still restricted. If it had been recursive, wouldn't that have applied to all directories in "/"?

/proc is a very spezial filesystem is "proc". what does --> ls -ld /etc or ls -ld /usr shows
you ( i guess the permissions are 777 - isn't it ? )
bye

---

### Post by mcduck on 2012-11-03
> **rnerwein said:**
> /proc is a very spezial filesystem is "proc". what does --> ls -ld /etc or ls -ld /usr shows
you ( i guess the permissions are 777 - isn't it ? )
bye

There is no reason why the OP's /proc would now have 777 permissions, it's not located inside /root and therefore the chmod command had no effect on it.

---

### Post by Mystic Silverfox on 2012-11-03
Much thanks to you both rnerwein and McDuck, but I think I'm going with McDuck on this. I know a fair amount about Terminal from tinkering with OS X, but Linux was suggested for my CompSci major and so I picked Ubuntu, now I'm playing around trying not to shoot my foot off.

---

