---
title: "CD  Copys Locked"
date: 2008-05-20
forum: General Help
---

### Post by rustyz on 2008-05-20
hello, i did a fresh install from the new hardy cd disk that was sent to me...

i did a "guided use entire disk" instal... like i have done with 7.6 & 7.10

before hand, i made some data files... copied my music, doccuments, and photos files on to a cd with gnomebaker...

have always done it this way... always worked great...

problem!

now, as i transfered my data files over to hardy... all these files are now "locked!"

are the user permissions for me different on this new version?

it seems to be...

if so, how may i get these files "Unlocked"

and prevent any data files transfers from being locked in the future?

thanks...

---

### Post by mc4man on 2008-05-20
they shouldn't be 'locked' to you.(owner) The lock just means you have only read access. Ck. in properties -> perrmissions if you want to change to read and write

---

### Post by rustyz on 2008-05-20
mc4> Ck. in properties -> perrmissions if you want to change to read and writeok, would you be so kind as to give me the order in witch to do this...

is it from home folder,in the file browser that pops up when the disk is inserted?

or someplace else...

one more question...

do you or anyone else know why this is different on Hardy?

thanks

---

### Post by mc4man on 2008-05-24
I usually use flash drives to transfer fies, folders, ect. but just tried from a cd and see what you mean. Hardy seems to only allow read or access permissions when copying from media that is mounted as read only (cdr's, dvdr's). That was an behavior back in dapper i believe that was changed and now has reappeared. Whether this 'behavior' is dumb or not I don't know but it's certainly annoying. What would be dumb is if there's no way to change this either at all or in a fairly obvious manner.

---

### Post by bryncoles on 2008-05-24
i get this too. is there a way to set hardy so we can transfer files from cd and not have to change permissions?

---

### Post by rustyz on 2008-05-24
mc4, yep, i've been spending alot of time on this...
have seen this issue refference on dapper also...

none the less, this has to be resolved...

i'm a loyal ubuntu fan, and would like to use the long term release...

when everybody says... "Back up your files"

i have, and would like to put them on hardy, it just wont let me...oh, unless one by one...

i have googled, searched forums, and searched for a fix...

nope...

changed my persional user name to groups, unlocked, root, samba shares, checked all boxes, create and delete files, read and write... ect...

and when i think its licked...

i shove my disk in, drag the file, and get that dopey locked icon...

i aint giving up, there has to be a simple way to do this simple task!

shame on the brainiac that thougth this one up!


will let know, if i find the simple solution...

rz

---

### Post by mc4man on 2008-05-24
Atm just run chmod u+rw -R <folder name>  to do folders and all that's in them.
If the folder has spaces in name use 'name'

---

