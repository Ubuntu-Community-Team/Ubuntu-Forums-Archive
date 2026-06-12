---
title: "Unable to access external HDD"
date: 2018-08-16
forum: General Help
---

### Post by swarup on 2018-08-16
I have an older HDD which I wanted to access some files from. When I connect it to my laptop I get the message which has been attached as a screen shot. I've also placed the same message in the code window below.

```
The folder contents could not be displayed

Sorry, could not display all the contents of "67305ef4-0dfe-402e-be6d-8f3058294bff": Error when getting information for file '/media/swarup/67305ef4-0dfe-402e-be6d-8f3058294bff/Hindi Spellchecker Backup': Input/output error
```

What do I need to do to be able to access the contents of this HDD?

---

### Post by monkeybrain20122 on 2018-08-16
I think your hard drive has bad blocks/bad sectors or it might be damaged.

you can try: connect the drive, unmount it and  
```

sudo fsck /dev/sdxi
```

x is the drive identifier i is the partition number

e.g /dev/sdb1, here x == b, i == 1

you can find out with
```

sudo blkid 

```

[COLOR=#000000]
[/COLOR]

---

### Post by swarup on 2018-08-16
I hooked up the HDD intending to try what you suggested, and this time it worked fine! A bit of a mystery. 
Perhaps it is on the borderline, and would be best to remove whatever i need from it for the future.

---

