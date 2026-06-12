---
title: "html copying"
date: 2007-01-14
forum: General Help
---

### Post by Ubuntuud on 2007-01-14
Hi,
I didn't know where to ask this, so I put it here...

I want to create a link bar that is shared with all my php pages. So let's say I have the following:
```
<span id="linkbar"><a href="page.php>Page</a></span>
```

How do I put that on 10 pages with me having to edit only 1 file to add (or remove) a link to all 10 pages?

I hope I was clear...
But do you know how to do this? Thanks in advance (and also afterwards :)).
pieter.

---

### Post by WiseElben on 2007-01-14
If I understand correctly, you can use include() to do this. On all 10 of your pages, use something like:
```
<?php include("header.php"); ?>
```

Then, inside header.php, add all the things you want. For example:
```
<span id="linkbar"><a href="page.php>Page</a></span>
```

So now when you edit header.php, every page will be changed automatically.

---

### Post by Ubuntuud on 2007-01-14
Yeah! That's it!
Thank you so much!

---

