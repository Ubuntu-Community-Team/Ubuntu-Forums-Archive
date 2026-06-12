---
title: "Permissions and stuff issues on New Kubuntu install 6.10"
date: 2006-12-13
forum: General Help
---

### Post by cosine7 on 2006-12-13
I reinstalled kubuntu 6.10 today and most things are running great, but whenever i attempt to run a bin file or anything (google earth (installer worked but not program), jUploader and flock) i get permission denied errors.....](*,) ](*,) ](*,)

often i get this

> ohiggins@ohiggins-desktop:~/google-earth$ sh googleearth-bin
googleearth-bin: 1: Syntax error: "(" unexpected


> ohiggins@ohiggins-desktop:~/Desktop$ ./PlaneShift_CBV0.3.017.bin
bash: ./PlaneShift_CBV0.3.017.bin: Permission denied


are the two errors i am getting

---

### Post by pandu.rs on 2006-12-13
In terminal type the following

chmod +x ~/google_earth/googleearth-bin

Then just double click on it.. dont use sh
Also do

chmod +x ~/Desktop/PlaneShift_CBV0.3.017.bin

Then it will work!

---

### Post by cosine7 on 2006-12-13
> **pandu.rs said:**
> In terminal type the following

chmod +x ~/google_earth/googleearth-bin

Then just double click on it.. dont use sh
Also do

chmod +x ~/Desktop/PlaneShift_CBV0.3.017.bin

Then it will work!
Thanks Pandu, but neither of those solutions worked, command line or clicking...

---

