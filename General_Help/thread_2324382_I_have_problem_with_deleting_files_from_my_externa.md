---
title: "I have problem with deleting files from my external hard drive"
date: 2016-05-13
forum: General Help
---

### Post by v6rg2 on 2016-05-13
I have a Passport Western Digital hard (1 T) full of my files. Now I want to delet these files and I cant!
For example this is error that I found after try for delet a file:

```
Error while deleting.
There was an error getting information about the files in the folder “collection.media”.
Error  when getting information for file '/media/v6rg/My  Passport/.Trash-1000/files/Anki/User  1/collection.media/afraid_example.mp3': Input/output error
```

What should I do? I am a beginner and dont know so much about codes.

---

### Post by yancek on 2016-05-13
Posting the command you used to try to delete would be a good first step.
Partitions on external drives are generally owned by root until you change them so check the owner:group of the folder 'collection.media' as well as permissions.  The user trying to delete would need to be the owner or you would need root (sudo) privileges.
You have spaces in the command you posted which requires quotes or double quotes to succeed.

---

### Post by v6rg2 on 2016-05-13
> **yancek said:**
> Posting the command you used to try to delete would be a good first step.
Partitions on external drives are generally owned by root until you change them so check the owner:group of the folder 'collection.media' as well as permissions.  The user trying to delete would need to be the owner or you would need root (sudo) privileges.
You have spaces in the command you posted which requires quotes or double quotes to succeed.

I did not delete with command. I deleted with delete key on my keyboard.
How I could delete files in terminal and by command?

---

