---
title: "qtqr will not read qr codes in 16.04.1"
date: 2016-09-08
forum: General Help
---

### Post by Nosphky on 2016-09-08
I posted a question about a week ago on launchpad/qr-tools but haven't had any reply as yet so maybe someone on the general forum here can help.

On 16.04.1 (a clean install), qtqr will generate qr codes correctly - I can read them on a smartphone.  But I cannot get qtqr to read a qr code. 

There is in the gui, an invitation to drag and drop a qr code into the gui. This does nothing at all on my system.

There is also a drop down box labelled 'decode' which has an option to 'decode from file'.  I cannot get this to do anything.

Does anyone here use qtqr and can suggest whether there is some other dependency which is not announced in Synaptic Package Manager ?
Or alternatively, suggest another software for reading qr codes ?

---

### Post by Nosphky on 2016-09-22
I tracked this down (with some suggestions from Manfred Hamp) to a recently registered bug. See following link

[https://bugs.launchpad.net/ubuntu/+source/qr-tools/+bug/1589965](https://bugs.launchpad.net/ubuntu/+source/qr-tools/+bug/1589965)

I applied the small edit suggested in comment #3 to this bug which I list below in case others here find the same problem :

"And the fix is obvious. Go to the file '/usr/lib/python2.7/dist-packages/qrtools.py', the line 181 (as root) and replace 'tostring()' with 'tobytes()' "

This fixed my problem and now qtqr decodes nicely.

---

