---
title: "Tesseract stopped working"
date: 2015-11-13
forum: General Help
---

### Post by Hamburgian on 2015-11-13
After using tesseract with gimagereader for about a year it suddenly began to behave strangely.
Around the 8th November I got very odd texts after running the OCR.
Now it has stopped launching altogether.
Wrote to Sandro Mani and sent him the generated backtrace, and he replied in the middle of the night...what a star!!!
His advice is that I've received an update for Tesseract that is causing the crash

> It looks like you got a tesseract update which enabled OpenCL support, and this is where the crash is occuring, see

#7 strlen () at ../sysdeps/x86_64/strlen.S:106

#8 0x00007fc19819c7c6 in OpenclDevice::getDeviceSelection() () from /usr/lib/x86_64-linux-gnu/libtesseract.so.3

So far I've tried removing and reinstalling tesseract, but no joy.
Can anyone tell me what tesseract updates there have been and how it might be possible to roll this back to a working application?

Ta.

---

### Post by ajgreeny on 2015-11-13
I installed tesseract on Dec 23 2014 and have had no updates since then.  Tesseract is still working great here.
> libtesseract3 (3.03.02-3)
tesseract-ocr (3.03.02-3)
tesseract-ocr-eng (3.02-2)
tesseract-ocr-equ (3.02-2)
tesseract-ocr-osd (3.02-2)
Which version do you have and which Ubuntu version are you running?

---

### Post by Hamburgian on 2015-11-13
According to synaptic I have 
tesseract-ocr (3.04.00 ppa+trusty)
libtesseract (3.04.00 ppa+trusty)
but all other packages are as yours (3.03.02-3)
Are the language files still compatible with the newer version of tesseract?
and running on Ubuntu 14.04 LTS-64bit

I've noticed that some posts on tesseract mention nvidia....why?..I have nvidia current 304.128. I also have nvidia-opencl-icd-304. Is this what is causing the problem? Will my nvidia work if I disable this package?

---

### Post by ajgreeny on 2015-11-13
It may be worth trying to disable the ppa that you use for tesseract and then uninstalling and reinstalling to get back to the same version as me, which from the standard repos.  Was the ppa at [https://launchpad.net/~rebuntu16/+ppa-packages](https://launchpad.net/~rebuntu16/+ppa-packages) ?

I used to make use of a ppa for teseract in 12.04, but found it was no longer needed in trusty, 14.04 so I removed it and I can not remember which ppa I used.

---

### Post by Hamburgian on 2015-11-13
OK...went back to synaptic, uninstalled tesseract-ocr (3.04.00 ppa+trusty) & libtesseract (3.04.00 ppa+trusty) and then force version-ed the 3.03.02-3 versions of both. Now it launches, but doesn't recognise the language files. Have reinstalled both German and English...but no joy. Will try again later

---

### Post by ajgreeny on 2015-11-13
Have you rebooted so make sure there is no residual libraries from the newer version still loaded?

---

### Post by Hamburgian on 2015-11-13
Thanx Greeny,
I didn't have any PPAs for tesseract, but after purging the lot..Gimagereader and Tesseract, then reinstalling everything for the umpteenth time..it works again. Thanks for the support

---

### Post by Hamburgian on 2015-11-13
......and just a last question.
Tesseract is working again, and properly. I was just shutting down synaptic when it told me there were pending operations. These were to update tesseract-ocr &
libtesseract to the 3.04.00 ppa+trusty versions. For now I've denied that and 'locked versions' to the 3.03.02-3 versions....should I leave it at that? I guess sometime...especially with an LTS upgrade...there will be new, improved versions about. Advise please.

---

### Post by ajgreeny on 2015-11-13
I'm afraid you either have to lock the package to a version that works in synaptic, or in /etc/apt/preferences (you may have to create this file first) and add content of 
```
Package: tesseract-ocr
Pin: 3.03.02-3
Pin-Priority: 1001
```
I have seen different Pin-Priority numbers used elsewhere and am not sure what they mean, but the 1001 did work for me in the past.

You will have to check occasionally if there is a new tesseract version that might work for you which you may have to do with dpkg, though I'm not sure how best you should do that, or if there are better ways.

[http://askubuntu.com/questions/135339/assign-highest-priority-to-my-local-repository](http://askubuntu.com/questions/135339/assign-highest-priority-to-my-local-repository) gives some info on the Pin-Priority system for us both!

---

