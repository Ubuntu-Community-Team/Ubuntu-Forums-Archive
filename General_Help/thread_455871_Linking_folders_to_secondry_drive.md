---
title: "Linking folders to secondry drive"
date: 2007-05-27
forum: General Help
---

### Post by lukemcgregor on 2007-05-27
hey 

I have a secondry sata drive that ive mounted to /mnt/sda1 how do i create virtual links so that i make say /home/user point to a folder on the secondry drive? 

Thanks

---

### Post by mbradlcu on 2007-05-27
is this what you're looking for? on the command line and you may need to 'sudo' it:
```
ls -s /mnt/sda1 /home/users
```
you may need to change the ownership of that directory and contents. Let me know if you have any questions
thanks!

---

### Post by lukemcgregor on 2007-05-27
hey,

I tried that but it didnt work, the command seemed to execute but the link isnt going, are you sure its ls -s? man says thats to display size or something
Thanks
Luke

---

### Post by mbradlcu on 2007-05-27
crud,, yea or rather no, it's
```
ln -s /mnt/sda1 /home/users
```

---

### Post by lukemcgregor on 2007-05-27
cool thanks that works now :) does it stay there after a reboot or do i need to put it in a script somewhere?

---

### Post by mbradlcu on 2007-05-27
the link will stay, it will even stay if you have the drive not mounted, in that case it will point to /mnt/thatdrive but will be on the local filesystem.

---

### Post by lukemcgregor on 2007-05-27
awesome thanks heaps 4 ur help :)

---

