---
title: "how do i play spc (snes) files in xmms?"
date: 2005-06-29
forum: General Help
---

### Post by rymdapan on 2005-06-29
Anyone know if there is a plugin for plying spc files in xmms? the nsf plugin i got (synaptic), but it  dont suport the spc files!

anny ideas?

/apan

---

### Post by SFN on 2005-06-29
You can add the Rarewares repository to your sources list.

```
sudo gedit /etc/apt/sources.list
``` 

At the end of the file, paste in the following:

## RareWares/Debian Multi-Media Repository for Unstable
deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./

And update your sources.

```
sudo apt-get update
``` 

Then you can install xmms-sexyspc

```
sudo apt-get instal xmms-sexyspc
```

After that, you should be good to go.

---

### Post by rymdapan on 2005-06-29
Worked like a charm! thank u VERY very mutch :P

---

### Post by barfos on 2005-12-22
It works for me too, but not like a charm.  My spc's all play fine in XMMS, but all the play times are wildly wrong.  Some are set to play for over 200 hours before going to the next song!

barfos

---

### Post by racarate on 2008-02-02
I am having the same problem -- the songs all display as being 100000s of hours long!  Did you ever find a solution?  


-Nick

---

### Post by peterv on 2008-03-27
Use openspc. 
```
sudo apt-get install xmms-openspc
```

Works perfectly fine for me.

---

