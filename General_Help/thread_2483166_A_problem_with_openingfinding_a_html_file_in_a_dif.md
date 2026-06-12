---
title: "A problem with opening/finding a html file in a different partition..."
date: 2023-01-22
forum: General Help
---

### Post by kr-ubn on 2023-01-22
I have a separate partition mounted at / called /DATA. This is where my user documents are held (not in the /home/user/documents directory).
I've made a symbolic link shortcut to this partition within my /home/username directory.

I have a html file inside a subdirectory within this /DATA partition. The file contains some hyperlinks which are displayed on the browser.

I want to display this html file in the web-browser (firefox used). But when I click the html file, it says :

"
File not found
Firefox can’t find the file at /home/kaushan/DATA/kr_docs_2nd/6_Internet/0_MAIN/0_Main_index.html.
"

BUT, if I place the html file in " /home/kaushan/Documents/ " and then open with firefox, it opens just fine.

I also tried going to / and then the /DATA partition and then open file, but that also fails.

So, I'm guessing this is something to do with the separate partition that is the problem. Does someone know how to get
html files like this to open? this is somewhat inconvenient. 

thanks.

---

### Post by MAFoElffen on 2023-01-22
What happens, if in the FirFox browser address line, if you enter: (adapting to your own path, filename)
```

file:///home/kaushan/DATA/kr_docs_2nd/6_Internet/0_MAIN/0_Main_index.html

```
I do this all the time while working on webpages, refreshing the browser to update and changes.

---

### Post by ajgreeny on 2023-01-22
I assume you're using g the snap version of firefox which means that access to the filesystem other than your home and I think ***/media/user*** and maybe /***mnt*** is completely restricted so your files in /DATA my be inaccessible.

I have no snaps on my system so can't tell you much more in detail

---

### Post by Dennis N on 2023-01-22
> I have a separate partition mounted at / called /DATA. This is where my user documents are held (not in the /home/user/documents directory)

If you want to use the default Snap version of firefox and access HYML files on a separate data partition, you could change the mount point from /DATA to a subdirectory of /mnt (like /mnt/DATA) and change the owner to your user (chown -r username:username /mnt/DATA) after creating the mount point.  Then you can access and open the HTML files. This works because the snap system allows access through /mnt

---

### Post by kr-ubn on 2023-01-24
> **Dennis N said:**
> If you want to use the default Snap version of firefox and access HYML files on a separate data partition, you could change the mount point from /DATA to a subdirectory of /mnt (like /mnt/DATA) and change the owner to your user (chown -r username:username /mnt/DATA) after creating the mount point.  Then you can access and open the HTML files. This works because the snap system allows access through /mnt

This worked. I had to mount at /mnt/ and give permissions to mounted directory using chown. Then I had to make a symbolic link of that to /home/user directory. The new path opens in the browser. 
Kind of awkward about restricting partitions like this...wonder if mounting partition to /mnt/ might become a problem. hope not. 
that's what /mnt/ directory is there for, right?

---

