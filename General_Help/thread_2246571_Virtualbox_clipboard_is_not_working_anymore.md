---
title: "Virtualbox clipboard is not working anymore"
date: 2014-10-01
forum: General Help
---

### Post by bfuzze on 2014-10-01
My virtualbox clipboard sharing doesn't seem to be working on Ubuntu 14.04.

I installed virtualbox 4.3.10 using aptitude.
I transferred a Windows 7 vmdk from a machine running 12.04 to a 14.04, started up fine.  
I installed virtualbox-guest-additions-iso using aptitude. 
Intstalled GA from inside the Windows 7 guest, no errors, but the clipboard isn't working.

I've tried copying from:
  Firefox (host) to Chrome (guest)
  Firefox (host) to Firefox (guest)
  gedit (host) to Chrome (guest)
  gedit (host) to notepad (guest)
    
I found a post referencing parcelite on the vb forums, but I can't find anything like that. 

Not sure where to start with this.  Anyone ekse having problems?  Any sggestions?

---

### Post by bashiergui on 2014-10-05
You're halfway there with guest additions installed. You also need to enable bidirectional clipboard. Here's a guide on how to do that

[https://www.liberiangeek.net/2013/09/copy-paste-virtualbox-host-guest-machines/](https://www.liberiangeek.net/2013/09/copy-paste-virtualbox-host-guest-machines/)

---

### Post by bfuzze on 2014-10-10
This was it, thanks!  I don't remember having to do that previously... but it's been a while so it's probably just senility.  Thanks again!

---

### Post by bashiergui on 2014-10-10
Glad it worked!

---

