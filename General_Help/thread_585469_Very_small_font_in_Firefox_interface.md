---
title: "Very small font in Firefox interface"
date: 2007-10-21
forum: General Help
---

### Post by vladu on 2007-10-21
Hi

I've been using Gutsy pretty long before the official launch and I've had this problem for quite some time. Unfortunately I don't know exactly when or why it appeared.

As you can see in the attached screenshot, only Firefox is affected. Increasing the font size does just that but makes all the other applications' fonts much larger.

Any ideas on how to fix this?
Thanks

---

### Post by Tyke91 on 2007-10-21
have you tried going to firefox edit>preferences and then to the content tab and increasing the font there?

[[IMG]http://img106.imageshack.us/img106/4113/screenshotqs2.th.png[/IMG]](http://img106.imageshack.us/my.php?image=screenshotqs2.png)

---

### Post by ntetreau on 2007-10-21
I've had this problem as well.  I fixed it in Firefox by going into about:config (write this in the address bar).  Then search for 
layout.css.dpi

change its value from -1 to 0.  Restart.

For more info, check [http://ubuntuforums.org/archive/index.php/t-437727.html](http://ubuntuforums.org/archive/index.php/t-437727.html)

---

### Post by ntetreau on 2007-10-21
> **Tyke91 said:**
> have you tried going to firefox edit>preferences and then to the content tab and increasing the font there?

[[IMG]http://img106.imageshack.us/img106/4113/screenshotqs2.th.png[/IMG]](http://img106.imageshack.us/my.php?image=screenshotqs2.png)

I believe he wants to change the font size for the toolbar (Fiel, Edit, etc) and not really the font size of the html content which, as you rightly pointed, could be changed through Firefox preference dialogs.

---

### Post by vladu on 2007-10-21
ntetreau, you won't believe it but I just fixed the font problem involuntarily by installing a little add-on called Fission and restarting Firefox. Disabling the add-on doesn't revert the problem so it's really strange.

layout.css.dpi was indeed -1 and I changed it to 0 but it had no effect now.

to Tyke91, ntetreau was right. It was not the size of the content that was so much of a problem but the Firefox menu and tab font size.

Thanks everybody!

---

### Post by fido on 2007-10-22
I'm having the same problem except the problem I am having is with the content. I know you can increase the size in preferences. Why is this necessary I thought web pages were supposed to decide that for themselves. When I increase the font size in preferences some pages will look good but it will screw up other pages so I don't know why that is an acceptable solution.

---

### Post by louieb on 2007-10-22
> **fido said:**
> ... problem I am having is with the content... When I increase the font size in preferences some pages will look good but it will...

Try an add on called **No Squint **My old man eyes think its great. Use Alt+(+/-) to adjust font size and Firefox remembers on a per site basis.

---

