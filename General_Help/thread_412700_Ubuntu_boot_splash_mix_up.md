---
title: "Ubuntu boot splash mix up"
date: 2007-04-18
forum: General Help
---

### Post by Death_Sargent on 2007-04-18
I have been using Ubuntu (the gnome flavor) and desided to add kde just for a change of face.

Install went flawelesy and everything is normall still using gdm not kdm

However i no longer have the ubuntu 

Basically after installing kde instead of 

[IMG]http://shots.osdir.com/slideshows/751/2.gif[/IMG]

I get

[IMG]http://shots.osdir.com/slideshows/752/2.gif[/IMG]

---

### Post by John.Michael.Kane on 2007-04-18
Try this.
```
sudo aptitude remove kubuntu-artwork-usplash
```

Followed by.

```
sudo aptitude install usplash-theme-ubuntu
```


And reboot

---

### Post by strabes on 2007-04-18
You can also manually configure which one you want to use: [http://strabes.wordpress.com/2007/02/17/change-bootsplash-images-in-ubuntu/](http://strabes.wordpress.com/2007/02/17/change-bootsplash-images-in-ubuntu/)

---

### Post by akshaysrinivasan on 2007-04-18
So you want the old boot splash screen ?If so ,just remove the package kubuntu-artwork-usplash using synaptic ,and you should be fine.

---

### Post by MRiGnS on 2007-04-18
> **akshaysrinivasan said:**
> So you want the old boot splash screen ?If so ,just remove the package kubuntu-artwork-usplash using synaptic ,and you should be fine.

this would remove kde too

---

### Post by John.Michael.Kane on 2007-04-18
> **MRiGnS said:**
> this would remove kde too

No it would not. 

kubuntu-artwork-usplash depends on 

libc6
initramfs-tools
usplash

It also has a dependency on  kubuntu-desktop which is just a meta package, and can removed without issue

---

### Post by BeRniTo on 2007-04-18
I'm having exactly the same problem and Yes, it would remove KDE.
After marking kubuntu-artwork-usplash in Synaptic it says that kde-desktop would be removed as well.
The same happens when trying with aptitude.

So, what's the solution?

---

### Post by xopher on 2007-04-18
You should be able to use **update-alternatives** to switch between the usplashes..

```
sudo update-alternatives --config usplash-artwork.so
```

More information [here]("https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765").

---

### Post by MRiGnS on 2007-04-18
> **BeRniTo said:**
> I'm having exactly the same problem and Yes, it would remove KDE.
After marking kubuntu-artwork-usplash in Synaptic it says that kde-desktop would be removed as well.
The same happens when trying with aptitude.

So, what's the solution?


sorry i was mistaken. iw will only remove kubuntu-desktop which is a metapackage.

i apologize if i caused confusion.

---

### Post by BeRniTo on 2007-04-18
> sudo update-alternatives --config usplash-artwork.so

It worked. :)

Sorry about my previous post, I missed the line "It also has a dependency on kubuntu-desktop which is just a meta package, and can removed without issue"

Thanks. :D

---

### Post by xopher on 2007-04-18
Great to hear, mark the thread as [SOLVED], please ;)

(Press edit and you'll find a checkbox)

---

### Post by Death_Sargent on 2007-04-18
All the fixes seem to make sense only the problem is they don't work in parctice. 

none of them

---

### Post by Death_Sargent on 2007-04-19
> **strabes said:**
> You can also manually configure which one you want to use: [http://strabes.wordpress.com/2007/02/17/change-bootsplash-images-in-ubuntu/](http://strabes.wordpress.com/2007/02/17/change-bootsplash-images-in-ubuntu/)

that fix worked :)

---

