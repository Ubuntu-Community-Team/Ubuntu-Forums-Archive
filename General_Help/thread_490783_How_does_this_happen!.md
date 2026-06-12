---
title: "How does this happen?!"
date: 2007-07-02
forum: General Help
---

### Post by Hawk__0 on 2007-07-02
Hey there guys, I was using GPROFTPD and out of nowhere, i all of a sudden could not write to the folder where the files were to be stored. i had already put files in there too.

not only that, i also could not access it unless i was root... this all came out of nowhere so i tried changing the permissions to 770 then the folder like... "broke" or something same problem, ppl couldnt access my FTP, and for some reason i cannot open my FTP server unless i sudo it in a terminal... i cant even use alt+f2 then do the same command, it wont come up.

current permissions on the folder are:
owner: root
group: root
others: none

How is it that i change the owner and group from root?
it used to be me, at least i think it did...
the only thing that works is if i chmod it to 777 :S
currently i have them at 774 but for whatever reason my computer wont realize that my mp3s are mp3s anymore (for all folders) and i can only open them if i right click, choose XMMS (even though its the default still)

---

### Post by khughitt on 2007-07-02
Heya,

chmod works for file permissions. To change the *ownership* for a file or folder try:

```
chown user:user file_or_folder_name
```

Take care!

---

### Post by Hawk__0 on 2007-07-02
thanks dude, that did the trick... but.. how does that cause this to happen?

as you can see, the default thing to do with this file is, open it with XMMS:
[IMG]http://img527.imageshack.us/img527/3096/onefq7.jpg[/IMG]

Then I open with double click, and:
[IMG]http://img412.imageshack.us/img412/7645/twohz0.jpg[/IMG]

If you're thinking something screwy with XMMS or something else, thats not the case... I can still right click, then open with -> XMMS and it works fine..

ideas?

note:
the files that have white icons change to the music note once i single click them... odd?

---

### Post by Hawk__0 on 2007-07-02
bump

---

### Post by rillip on 2007-07-03
Firstly, changes do not "come out of nowhere."  I am sure you don't understand where the changes came from, but it wasn't spontaneous.

Here's what I would do.  Check the ownership of the file.  Start going about your normal work, checking the ownership after each thing you do.  Then, when you see it change, you'll know what did it.

For example, if you typically download a song with program x, then convert it to something else with program y, listen to it with program z, then burn it with program b, I would check after x, y, z and b.  Unless you're watching when the permissions change, it's hard to tell when they changed.  I can't guess at what program you're using is changing them, but it's not spontaneous.

---

### Post by Hawk__0 on 2007-07-03
firstly, changes coming "out of nowhere" is a way of explaining that i have no idea how it happened.
you think im stupid? obviously something happened, alright?

check the ownership of every single MP3 on my NTFS AND linux volumes?
well i can tell you that they all have the same problem, and i am indeed the owner of all of them... i already checked that.

the only thing i ever did was A: install an FTP server
B: copied MP3s to it
C: I went to copy more, but could not
D:checked permissions, owner was root, so i took this guys advice and changed it back to me with chown.

and thats all.
default program is still XMMS.

from the images i posted you can see that the icon changes when i click on it, to the music note, from the file icon.  this does not make any difference when i try to open the file, it simply shows the error i posted on the screenshot.

---

### Post by Hawk__0 on 2007-07-03
bump

---

### Post by Hawk__0 on 2007-07-03
bump

---

### Post by Hawk__0 on 2007-07-03
bump :(

---

### Post by Hawk__0 on 2007-07-03
bump... so nobody here knows how this could have happened? so im screwed? linux breaks and i cant ever fix it again?

---

