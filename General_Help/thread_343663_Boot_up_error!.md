---
title: "Boot up error??!"
date: 2007-01-21
forum: General Help
---

### Post by RaZoR-x11 on 2007-01-21
Hey there,

im getting error's on boot.

```

Trying to fix it up, but a reboot is needed
Backtrack:
Bad page statein progress 'swapper'
page:c11fbf20 flags:0x8000000 mapping:00800400 mapcount:0
```

i think it's something to do with the hard drive? there are alot off these error's and since they started i get random system crashes and reboot's and lose off data.


Meany thank's in advance.

---

### Post by jpeddicord on 2007-01-21
When you installed, did you use manual partitioning? If so, did you add a swap partition? This error looks to be as if there is no swap space, and could be why it is crashing frequently.

If you did add a swap drive manually, how big (in GB) is it? You generally should use double the size of your RAM for it. For example, I have 512 RAM, so I set up 1 GB of swap space in the installer.

If you didn't use the manual partitioning, then you shouldn't have to worry about the swap space.

Jacob

---

### Post by RaZoR-x11 on 2007-01-22
Cheer's for the reply, how do i check if i did add the swap if i remenber i made a swap 800mb as a extended partition at the end off the drive.
 
ohh and im geting IRQ error's on the recovery option is that memory related?

---

