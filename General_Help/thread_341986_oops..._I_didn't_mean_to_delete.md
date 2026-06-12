---
title: "oops... I didn't mean to delete"
date: 2007-01-19
forum: General Help
---

### Post by OldSchool on 2007-01-19
Complete moment of madness and typed completely the wrong command. I did not notice, but sadly I wasn't quick enough and lost a chunk of media. It happens, but any quick options to getting some of it back?

x

---

### Post by taurus on 2007-01-19
Did you remove it from a terminal with the rm command or did you remove it from a file manager?

---

### Post by OldSchool on 2007-01-19
I rm'd as root

---

### Post by taurus on 2007-01-19
If it's not in /root/.Trash (or /home/**username**/.Trash), then it's probably in a black hole right now.

That's why they keep saying be real careful with root account or sudo command because with one wrong command, you will flip.

---

### Post by OldSchool on 2007-01-19
yeah, I checked already 'just incase' but alas, no. 

remember kiddies, think before you hit the big return key!

](*,)

---

### Post by Dragon45 on 2008-01-23
Similar issue: I shift - deleted from nautilus, didnt realize i had half the file in my Documents folder selected, and ended up permanently deleting a ton of stuff. Any options for me? :\

---

### Post by t20racerman on 2008-01-23
I can't offer any help here - sorry - but it is worrying how many people don't back up files regularly. This isn't meant as a lecture, but I have spent hours this week trying to repair computers where 'all the data was lost'. I managed to recover all the music and years of digital photos from one laptop that weren't backed up anywhere!

You can get small USB type external harddrives that hold 300MB plus so cheaply these days. All those who read this post - make it your new Year resolution to back things up on a separate disc somewhere!

lecture over...... :)

---

### Post by stchman on 2008-01-23
> **OldSchool said:**
> I rm'd as root

It is GONE.

---

### Post by mivo on 2008-01-23
You can *try* to recover the files, but it's not easy and there is no guarantee that it will work even partially. The more you continue to use the computer, the lower the chance of success. But anyway, start reading here: [Recovering deleted files]("http://www.samag.com/documents/s=7033/sam0204g/sam0204g.htm").

And start making backups today. External drives are cheap, and rsync is a wonderful tool to automate this (GUI in the repo: Grsync).

---

### Post by dannyboy79 on 2008-01-23
> **Dragon45 said:**
> Similar issue: I shift - deleted from nautilus, didnt realize i had half the file in my Documents folder selected, and ended up permanently deleting a ton of stuff. Any options for me? :\

if you used the delete function and not the trash function, they are gone as well. I know I had to specifically go into nautilus settings and tell it to make a "delete" button within the right click menu. Although, are you saying that you used the delete key. I am not sure what would have happened.

you can look in all the place where trash is stored by issuing this command

locate .Trash

and look in each of those folders for your files.

---

