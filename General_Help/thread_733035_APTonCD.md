---
title: "APTonCD"
date: 2008-03-23
forum: General Help
---

### Post by StephanG on 2008-03-23
I recently downloaded APTonCD, because I wanted to duplicate many programs in my repository onto CD, so that I would have to download it again, stuff like blender, eclipse, kdevelop, ect.  But the APTonCD package selection seems limited to only a few packages, how can I increase that to include my other programs?

Thanks for your help guys. :)

---

### Post by Oldsoldier2003 on 2008-03-24
> **StephanG said:**
> I recently downloaded APTonCD, because I wanted to duplicate many programs in my repository onto CD, so that I would have to download it again, stuff like blender, eclipse, kdevelop, ect.  But the APTonCD package selection seems limited to only a few packages, how can I increase that to include my other programs?

Thanks for your help guys. :)
> 
Add packages
    It's possible to add other deb packages inside the APTonCD media, even those that weren't installed using the apt-get tools. There are two ways to do this: you can use the Add Package... button then find and open the deb package you want to add. The other way is simply drag-and-drog the package from Nautilus to APTonCD window. Using both methods it's possible to add multiple packages at same time.

[http://aptoncd.sourceforge.net/doc-manual.html](http://aptoncd.sourceforge.net/doc-manual.html)

---

### Post by sujoy on 2008-03-24
is there any way to install packages from the aptoncd image without burning it to a disc? i did the restore from iso, but it just copies the files in cache, i cannot yet install them.
please help.

---

### Post by zvacet on 2008-03-24
In synaptic>mark all updates or 

```
cd /var/cache/apt/archives
```

after that 

```
sudo dpkg -i *deb
```

Maybe installation will stop and in that case run 

```
sudo dpkg --configure -a
```

or

```
sudo apt-get -f install
```

---

### Post by StephanG on 2008-03-28
Thanks for the help, but where can I find the .deb packages.  Does adept automatically store a copy of them somewhere or are they assimilated after the package has been installed?

---

