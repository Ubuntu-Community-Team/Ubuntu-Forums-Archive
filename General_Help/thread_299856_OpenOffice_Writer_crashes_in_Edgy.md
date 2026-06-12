---
title: "OpenOffice Writer crashes in Edgy"
date: 2006-11-14
forum: General Help
---

### Post by xdevnull on 2006-11-14
Writer has been crashing consistently for me at two points:

One is a document with .tif images.  Especially if there are a few of them, after editing text, it will crash when you click on an image.  It will also crash if after moving an image you try to click on some text.  I think it might be a memory thing, because the more images you have (say 6 vs. 1), the more often the crash.

Second is when I copy from writer and then go to paste it in Yahoo Mail (the yahoo beta mail).  OOo just crashes dead - which is really weird.  The text is still in the clipboard, though, I can select it using glipper.

It also doesn't generate a bug report like evolution does to send in - I don't now if this is because OOo doesn't ever do that, or if I don't have something installed.  This problem is annoying enough that I would install the debug packages and send in a bug report when this happens.

---

### Post by Ramaddan on 2006-11-14
Same thing happening here.

Hope someone can help us with this issue.

---

### Post by Asraniel on 2006-11-15
same here... both document that crash for me have pictures

---

### Post by d351GuJu on 2006-11-19
Same here, I inserted couple of JPEG images on OO writer and once inserted, I can't click on them, if I do so OO crashes without any errors.  I am so freaking tired of this!!!  :evil:

---

### Post by Cable on 2006-11-19
The copy/paste problem has a bug report on launchpad [here]("https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/62432"), and the image problem has a bug [here]("https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/68832").  Check those out to see if there is anything there that can help you.  I don't think the copy/paste bug is fixed yet, but the image bug *might* be.  Don't quote me on that though.

---

### Post by xdevnull on 2006-11-21
Thanks cable!  No one replied for a while so I ended up tracking down the Ubuntu bug-tracking system and filing a bug for edgy ([here]("https://launchpad.net/distros/ubuntu/+bug/72383") and [here]("https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/72384") )- or at least I think I did - not sure if maybe it was somewhere else, because I did a search for all OOo bugs and didn't find these.  At least the first one appears to be connected with a release candidate.  I got no dialogue after the crash to submit a bug - but maybe that's how OOo works in ubuntu.  I wish there was a better connect between the bug-tracking, forums, and the actual bug-tracking in the distro.  But I guess if wishes were money, we'd all be rich - or at least facing a ridiculous inflation rate.

---

### Post by rps63ifid on 2006-11-29
I too have seen the "crash on paste" bug, although OOo Writer crashes whenever I try to paste text from Writer into almost any other application (I say "almost" only because I have tried half a dozen or so and all have yeilded the same results), and it is doing it on all 4 boxes I have Edgy installed upon.

Does it behave the same way if one is using the stock OOo installation (as opposed to the installation from the Edgy repositories)?

Any word on a fix to this?

---

### Post by xdevnull on 2006-11-29
Look up at Cable's post.  There is a link to the bug report which has a link to the fix. Basically you'll need to add a repository and update several of the OOo files.  This fix worked for me.  I haven't had any problems since I applied the fix.

---

### Post by Ramaddan on 2006-12-01
> **xdevnull said:**
> Look up at Cable's post.  There is a link to the bug report which has a link to the fix. Basically you'll need to add a repository and update several of the OOo files.  This fix worked for me.  I haven't had any problems since I applied the fix.

Hi, I did what you said, and followed the instructions given in launchpad. Works great. Thanks.

---

### Post by Leonivek on 2006-12-02
I installed the version mentioned on Launchpad to fix the copy/paste bug in Writer.  

Today, though, I was in Spreadsheet and **I cannot select an entire column**.  [I]It crashes every single time. ](*,)
[/I]
To backtrace a little, I had copied and pasted a table from a Thunderbird email and pasted it in Spreadsheet.  I resized the columns and rows to fit nicely.  Then I wanted to delete 2 columns.  As soon as I selected both, it crashed.  I tried selecting just the one and it crashed, too.

Can anyone else confirm this?

Thanks!

---

### Post by xdevnull on 2006-12-03
I coulnd't reproduce this.  I entered information and no crash, then I copied a table of data off the internet and pasted it into a table.  I could select entire columns and rows without any problem.  It might be the table you are using?

---

### Post by Leonivek on 2006-12-04
No... I tried with a new blank sheet, selected two columns, and crash.  Note, again, that I am using the version of OpenOffice identified on the Launchpad bug report.  This version fixed the copy/paste crash.

---

### Post by escape on 2006-12-04
I must say the instability of openoffice in edgy is nearing unacceptable. Perhaps it has something to do with running Xgl/beryl, but one would at least expect crash recovery to actually save stuff. I can't even count how many times I've had to retype a page because openoffice writer crashed and "recovered" what I basically had the last time I saved. Just venting now, but still, it makes me want to go back to Windows...

---

### Post by Ramaddan on 2006-12-06
Can't reproduce the problem.
Why not go back to Dapper, instead of feeling the urge to go back to Windows. Dapper was a lot more stable. Well, the name of Egdy is "Edgy". ;-)

---

### Post by xdevnull on 2006-12-06
Leonivek

Have you tried uninstalling OOo completely and then reinstalling it from the new repository?  If there is a corrupt lib somewhere this *might* get rid of it.  Of course if it is some lib that doesn't get reinstalled, this won't help.  It is one more thing you could do before going to another distro version.

---

### Post by jynyl on 2006-12-09
Similar problem here, OOo crashed every time I selected text containing an image.  (System here is Kubuntu 6.10 on Intel Core2 with OOo 2.0.4 from Kubuntu repositories.)
The symptoms appear to disappear after I quit klipper.  (Which is rather inconvenient, as klipper is a great help when cutting and pasting to and from OOo.)

HTH

Peter

---

### Post by rajman on 2007-11-06
> **Ramaddan said:**
> Hi, I did what you said, and followed the instructions given in launchpad. Works great. Thanks.

I did the same, but I'm running gutsy and it hasn't worked. any clues ?

---

