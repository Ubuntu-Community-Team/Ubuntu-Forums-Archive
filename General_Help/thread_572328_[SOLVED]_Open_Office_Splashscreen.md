---
title: "[SOLVED] Open Office Splashscreen"
date: 2007-10-10
forum: General Help
---

### Post by Haywood on 2007-10-10
OK, I did it... not that I really f'ed up my system, just the splashscreen on Open Office.  Here is what I did.

I have another copy of OpenOffice (portable) that I run from a thumb drive on Windows machines.  I noticed that it had a blue splashscreen, and did not like the default brown Ubuntu OpenOffice splashscreen. I copied the spashscreen (named intro.bmp) from the thumb drive to my Ubuntu desktop.  I then renamed it "openintro_ubuntu.bmp as this is what Open Office uses when it loads. Then ran gksudo nautilus and copied and pasted into the /usr/lib/openoffice/program folder.  Now when I run Open office instead of getting the blue splashscreen, it is now just a black box.

Any help would be appreciated. Thanks in advance... Bill

---

### Post by Lord Illidan on 2007-10-10
First try renaming it to just intro.bmp

---

### Post by Haywood on 2007-10-10
There was a file in the /usr/lib/openoffice/program folder named intro.bmp as well and I also pasted a copy of the blue intro.bmp in there as intro.bmp.  That is when I found out that OpenOffice on Ubuntu referances the openintro_ubuntu.bmp  file as the splashscreen.

---

### Post by Lord Illidan on 2007-10-10
Hmm..I see, it's been changed on Gutsy.

Can you run ls -la in the folder where there's that bmp? (post output here, of course)

Also, make sure it's the same size as the original.

---

### Post by Haywood on 2007-10-10
-rwxr--r-- 1 root root   126920 2007-01-26 13:37 intro.bmp
-rwxr--r-- 1 root root   126918 2007-10-10 11:45 openintro_ubuntu.bmp

I assume you mean the height & width size... they are both the same height & width as the other ones were.

---

### Post by Lord Illidan on 2007-10-10
Hmm, strange. When you restore the original, does it behave like that too?

---

### Post by Haywood on 2007-10-10
No it didn't, thanks.

---

### Post by Lord Illidan on 2007-10-10
Try these, and notice the specific technique noted in the page. I just tried it out on mine.

---

### Post by jpyanowski on 2007-10-10
That's a real nice looking startup Splashscreen.

---

### Post by Haywood on 2007-10-11
Thanks for all of the help.  I went to gnome-look.org and found some that appealed to me, and worked.  I really was not all that worried about it as Gusty wll be out in about a week and everything will be changed again.

R/ Bill

---

