---
title: "Simple scan program ruins images in 14.04"
date: 2014-06-06
forum: General Help
---

### Post by LifeEnemy on 2014-06-06
Hi all,

I have an odd problem after upgrading to 14.04. I used to use the simple scan program that came with Ubuntu without issue (it was actually quite 'simple' to use). However, after the upgrade it can't properly scan an image. Everything I try to scan comes out super-bright, washed out, and unreadable. No amount of messing with settings fixed the problem. I installed Xsane, which gets the job done, but it overly complicated and has it's own issues. It'd be much simpler to scan my notes in simple scan and save them all at once, auto-cropped and organized. How can I make simple scan work again?

I'm using an Canon Pixma MP170. It's old, but it works fine.

Thanks.

---

### Post by ajgreeny on 2014-06-06
_**HP**_ Pixma MP170 ? ?

More likely a **Canon**, surely?

Sorry, I always use xsane myself for much more control, so I can't help with the simple-scan problem

---

### Post by LifeEnemy on 2014-06-06
Yes, it's a Canon! Thanks for pointing out my mistake, I've edited the first post.

I shouldn't post so late :P

---

### Post by LifeEnemy on 2014-06-09
Bump.

Any suggestions? Xsane works, but it's FAR more than I need, and the complexity makes large scan jobs a chore.

---

### Post by LifeEnemy on 2014-06-23
bump

---

### Post by HermanAB on 2014-06-23
These three should also work: scanlite, gscan2pdf, gimp (it has a scanner plugin).

---

### Post by LifeEnemy on 2014-06-25
I used gscan to compile my scans into one pdf, didn't realize it had a scan function though (I should have). I'll try that next time. As I said, xsane works but it's far more complicated than I need.

Any idea why simple scan isn't working anymore?

---

### Post by obake2 on 2014-06-25
Try deleting any Simple Scan's configuration file.
Go to /home/_Your-Username_/.cache/ and delete the "simple-scan" directory, and re-start Simple Scan :)

I don't know if that will work, but it is wort a try.

Also try opening Simple Scan in the terminal to see if there are any "interesting" messages. To open with the termina type "simple-scan"

```
simple-scan -d
```

---

### Post by HermanAB on 2014-06-25
As for re-ordering PDFs, do yourself a favour and install pdfshuffler.

---

### Post by LifeEnemy on 2014-06-26
Well, I feel stupid. Turns out the reason the image quality was so poor was that it was set to scan "text" so my notebooks looked terrible. Setting it to scan "Photos" fixed the problem right up.

I realized this after Xsane started showing the same issue, and its preview image was B&W with horrible quality. In Xsane is was a matter of changing the scan from 'lineart' to 'gray' or 'color.'

Thanks for all the help everyone.

---

### Post by wayneoutthere on 2014-07-12
> **obake2 said:**
> Try deleting any Simple Scan's configuration file.
Go to /home/_Your-Username_/.cache/ and delete the "simple-scan" directory, and re-start Simple Scan :)

I don't know if that will work, but it is wort a try.

Also try opening Simple Scan in the terminal to see if there are any "interesting" messages. To open with the termina type "simple-scan"

```
simple-scan -d
```

Awesome dude. My old canon flatbed whatever seemed dead in the water with simple scan but after sacking the file as you said (note: You have to do control H to show hidden files first in the home folder) and restarting as you said, boom.  She's alive.

Thanks man!

---

