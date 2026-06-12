---
title: "Weird Issues With File Tags"
date: 2015-12-20
forum: General Help
---

### Post by ThePowerpuffGirls on 2015-12-20
I've updated the tags for my MP3 files because some were incorrect, and it's still showing the old ones when viewed in the file properties. When I view the tags via EasyTag Editor (which is what I've used to edit the tags); they show up correctly.

Here is showing an example. You can see the file name shows the correct  name, but it shows the tags as the old name, even though I have  specifically edited both the tags and file name.

Is something cached? I noticed then when I copy the songs to another  computer, they still show up there as well. But then again, the  computers I've compied to still had had the songs with their old tags  before.

- Blossom

[IMG]http://i66.tinypic.com/2ahxoao.jpg[/IMG]

Why would it be showing the old tags or whatever it's called (song title, album artist etc)? When I had it installed in my phone, it would show up correctly.

Can anyone please help at all? I find it hard to believe no one else has this problem.

---

### Post by mcduck on 2015-12-28
First, make sure you did actually write the tags and not just the file names...

Then, it could be just a question of ID3 tag versions, some programs reading the ID3v1 tag and others using ID3v2 tags (the two aren't compatible with each other, so its possible to have both tags on a file with completely different information on them)

---

### Post by ThePowerpuffGirls on 2015-12-28
> **mcduck said:**
> First, make sure you did actually write the tags and not just the file names...

Then, it could be just a question of ID3 tag versions, some programs reading the ID3v1 tag and others using ID3v2 tags (the two aren't compatible with each other, so its possible to have both tags on a file with completely different information on them)

I only used a program called EasyTag. How would I find out which version it write and which version my songs has?

Thanks. :)

Edit:
Here is a screenshot, maybe the problem is here?
[IMG]http://i67.tinypic.com/287fy9c.jpg[/IMG]

It looks like I fixed it.

What I did was disable the write to ID3V1 tags, closed the program and reopened it, highlighted all songs and click the "Save Files" icon. They now show correctly.

---

