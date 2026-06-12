---
title: "How to delete a certain filetype?"
date: 2008-04-27
forum: General Help
---

### Post by carbn1001 on 2008-04-27
Hi,

I currently keep my music in the home/****/music folder. It's arranged in subfolders according to artist/album etc. Anyway, as well as the music files, there are also a load of .m3u playlist files. Is there a terminal command I can use to exclusively delete all these .m3u files whilst leaving the actual music untouched?

Thanks

---

### Post by LaRoza on 2008-04-27
> **carbn1001 said:**
> Hi,

I currently keep my music in the home/****/music folder. It's arranged in subfolders according to artist/album etc. Anyway, as well as the music files, there are also a load of .m3u playlist files. Is there a terminal command I can use to exclusively delete all these .m3u files whilst leaving the actual music untouched?

Thanks
Assumg you want to delete all files with the file extension .m3u, this will do it:
```

rm ~/music/*.m3u

```

---

### Post by dcstar on 2008-04-27
> **carbn1001 said:**
> Hi,

I currently keep my music in the home/****/music folder. It's arranged in subfolders according to artist/album etc. Anyway, as well as the music files, there are also a load of .m3u playlist files. Is there a terminal command I can use to exclusively delete all these .m3u files whilst leaving the actual music untouched?

Thanks

```
rm *.m3u
```

---

### Post by carbn1001 on 2008-04-27
Sorry, perhaps I should have clarified. The files I wish to delete are spread throughout all the various subfolders, not just in the /music folder.

---

### Post by LaRoza on 2008-04-27
> **carbn1001 said:**
> Sorry, perhaps I should have clarified. The files I wish to delete are spread throughout all the various subfolders, not just in the /music folder.

Run the command in each folder.

---

### Post by carbn1001 on 2008-04-27
> **LaRoza said:**
> Run the command in each folder.

I had thought of this, but that pretty much amounts to around 1500 folders. I was wondering if there was a quicker way to do so.

---

### Post by ad_267 on 2008-04-27
Try this:

```
find ~/music -name *.*m3u -type f -print0 | xargs -0 /bin/rm -f
```

Edit: It would be a good idea to create a test directory with some subdirectories and test this first.

---

### Post by LaRoza on 2008-04-27
> **carbn1001 said:**
> I had thought of this, but that pretty much amounts to around 1500 folders. I was wondering if there was a quicker way to do so.
Make a file (playlistrm.sh):

```

#!/bin/bash
cd ~/music;
for i in *
do
    cd "$i";
    rm *.m3u;
    cd ..
done

```
```

chmod +x playlistrm.sh
./playlistrm.sh

```

---

### Post by jocko on 2008-04-27
> **carbn1001 said:**
> I had thought of this, but that pretty much amounts to around 1500 folders. I was wondering if there was a quicker way to do so.

You could do it like this:
```
rm ~/music/*.m3u
rm ~/music/*/*.m3u
rm ~/music/*/*/*.m3u

```...and so on. Just add one more "/*" to make it go one level deeper in the directory tree until you think you have got them all.
Then to see if you got rid of all of them, run:
```
sudo updatedb
locate .m3u
``` If you still have some, you will see where they are, if you deleted them all, you will see no output.

Or just try what dcstar suggests below:

---

### Post by dcstar on 2008-04-27
> **carbn1001 said:**
> Sorry, perhaps I should have clarified. The files I wish to delete are spread throughout all the various subfolders, not just in the /music folder.

Then just use Places-Search for the file spec and delete what it finds.

---

### Post by paintba||er on 2008-04-27
```
find ~/music -name *.m3u -exec rm {} \;
```

---

### Post by deragon on 2008-04-27
> **ad_267 said:**
> Try this:

```
find ~/music -name *.*m3u -type f -print0 | xargs -0 /bin/rm -f
```

Edit: It would be a good idea to create a test directory with some subdirectories and test this first.

Here is an improved version:

```
find ~/music -name '*.m3u' -type f -exec rm -f {} \;
```

Best regards,
Hans Deragon

---

