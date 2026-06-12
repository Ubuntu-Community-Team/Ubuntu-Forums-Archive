---
title: "2 large directories = 1 symlinked folder | possible?"
date: 2007-08-17
forum: General Help
---

### Post by jzlharvey on 2007-08-17
situation- I have multiple hardrives installed in my server both housing Video files.  I would like like to  be able to see them as ONE large directory.  

Example: 

/media/media1/Video/Movies1/  &  /media/media2/Video/Movies2/ = /movies/ ?

So when I browsed to /movies I would see the contents of both ..../Movies1/ and ..../Movies2/

I would like /movies to act as if it were one huge 300 gb folder.  This would be really convenient for XBMC to browse.  One universal "movie" share.  I realize this most likely don't make sense . But Im still very much a noob to the *nix world.

---

### Post by jzlharvey on 2007-08-17
I was thinking... could I not mount the directory within another directory? Somethink like

```
sudo mount /media/media1/Video/Movies1/ /media/media1/xbmc/
```

---

### Post by HermanAB on 2007-08-17
You need to define logical volumes.  This way you can make a single volume that spans multiple disks.  This is also known as RAID0 or a BOD.

'Hope that helps!

Herman

---

### Post by jzlharvey on 2007-08-17
Thanks for the reply Herman.  I'm not sure what you mean by define logical volumes but i will start researching BOD.  I dont think that raid0 is what I am looking for as I have 2 drives full of (different) media.

---

### Post by jzlharvey on 2007-08-18
could someone lead me in the right direction on "define logical volumes"?  Thanks.

---

### Post by Modernity on 2007-08-18
yes, you can mount a second HDD as a directory in your first HDD, but I don't remember how i set it up at my office. If no one replies by Monday this coming week, I will check the office server and reply back how to do it.

---

### Post by Modernity on 2007-08-18
it will look something like this
```
mount /dev/sdb /home/yourname/movies/movies2
```

mount with whatever switches if needed, probable none

/dev/sdb is the actual mounted devices like hda or sda, sdb would be your second hard drive

/home/yourname/movies/movies2 is called the mount point, just a symlink, so fill this in where you want to access your drive

---

