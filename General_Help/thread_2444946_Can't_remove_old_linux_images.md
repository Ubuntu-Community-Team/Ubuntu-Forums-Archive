---
title: "Can't remove old linux images"
date: 2020-06-06
forum: General Help
---

### Post by apocalypsemystic on 2020-06-06
I'm trying to free up space on my system, and it seems that I have a bunch of old linux image/modules/extras that none of the automated methods I have tried are able to remove. I haven't tried manually removing them yet because I wanted to verify that it was safe to do so.

My current image is 4.15.0-72-generic:
```
uname -r 
4.15.0-72-generic
```

I also have 4.15.0-70-generic loaded:
```

dpkg -l grep -E 'linux-image-[0-9]+'
ii  linux-image-4.15.0-70-generic
ii  linux-image-4.15.0-72-generic
...
```

And a bunch of other images listed as already removed:
```

...
rc  linux-image-3.16.0-67-generic
rc  linux-image-4.4.0-133-generic
...
```

However, dpkg still reports a number of files associated with those removed images as taking up space on my machine:
```

dpkg-query -Wf '${Installed-Size}\t${Package}\n'
...
158643    linux-image-extra-4.4.0-45-generic
152723    linux-image-extra-3.16.0-67-generic
152772    linux-image-extra-3.16.0-62-generic
66596    linux-image-4.4.0-141-generic
58329    linux-modules-4.4.0-169-generic
...
```

I have tried to remove old kernels automatically using
```
apt-get --purge autoremove
```
however, the offending images, modules, extras, etc. remain.

I have not yet tried removing them individually, such as with
```
apt purge linux-modules-4.4.0-169-generic
```
because I wanted to verify that I was correctly understanding that these are files associated with old kernel images and will not still be dependencies of my current 4.15 image. Is that correct?

It may also be worth noting that 
```
apt-mark showauto 'linux-*' 
linux-image-4.15.0-70-generic
linux-image-4.15.0-72-generic
...
``` 
displays only versions relevant to my two installed kernels and

```

apt-mark showmanual 'linux-*'
linux-generic
linux-image-generic
```
Is the complete output of showmanual.

Thanks.

---

### Post by Frogs Hair on 2020-06-06
Have you tried with the synaptic package manager ? My old kernels have been showing up as auto removable in synaptic for the last few releases.

---

### Post by apocalypsemystic on 2020-06-06
I tried synaptic and it did seem to know that they could be safely removed so I ran it and it seems clear now. Thanks.

---

