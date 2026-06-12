---
title: "How to copy without the lock"
date: 2008-05-22
forum: General Help
---

### Post by Akeda on 2008-05-22
Hi there,

I'm sorry to ask but I'm really new to all of this. Today I installed Ubuntu. Everything is perfect and I love it. The only issue I have is the next:

Every time I copy data from a DVD (documents/folders/pictures) it appears a lock next to the folder icon and when I try to move it or delete it, I cannot do it it appears the next message [COLOR="Red"]"Unable to trash/move file: Permission denied"[/COLOR]

I know about the "sudo mv" and the "gksudo nautilus". I just want to copy my files from my dvd to the desktop without the lock and/or restriction issue. I want to move the files/folders where ever I want.

Anything that can help would be very appreciated.

Thanks.

---

### Post by niteshifter on 2008-05-22
Hi,

Let's see if it's a groups-permissions problem. Open a terminal and type this command:

cat /etc/group

and post the output here.

---

### Post by Cap'n Skyler on 2008-05-22
> **Akeda said:**
> Hi there,

I'm sorry to ask but I'm really new to all of this. Today I installed Ubuntu. Everything is perfect and I love it. The only issue I have is the next:

Every time I copy data from a DVD (documents/folders/pictures) it appears a lock next to the folder icon and when I try to move it or delete it, I cannot do it it appears the next message [COLOR="Red"]"Unable to trash/move file: Permission denied"[/COLOR]

I know about the "sudo mv" and the "gksudo nautilus". I just want to copy my files from my dvd to the desktop without the lock and/or restriction issue. I want to move the files/folders where ever I want.

Anything that can help would be very appreciated.

Thanks.

easy to fix
go to that file
highlight it(the contents)
right click and
click the permission tab
then:popcorn:
 give yourself permission to read and write for that file.
close and you are done

---

### Post by Cap'n Skyler on 2008-05-22
and BTW
some things you may want to install can give you the same issues,if it wont install,check to make sure you have read/write or execute permission

:guitar:

---

### Post by Akeda on 2008-05-22
> **Cap'n Skyler said:**
> easy to fix
go to that file
highlight it(the contents)
right click and
click the permission tab
then:popcorn:
 give yourself permission to read and write for that file.
close and you are done

Thanks a lot it worked.

I just right click on the folder,
then properties,
then permissions
and in folder access y selected "create and delete files"
and in file access "read and write".

Thanks!!!!

---

### Post by Cap'n Skyler on 2008-05-22
Woot!!:guitar:

---

