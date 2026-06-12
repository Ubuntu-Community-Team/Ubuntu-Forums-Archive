---
title: "Unlocking Read only USB key on Ubuntu"
date: 2018-10-22
forum: General Help
---

### Post by zola2018 on 2018-10-22
Hi, I am starting with Ubuntu and I face issue due to my previous back up I did while I still was using a macbook. 

i basically back up some datas on an USB stick and I cant copy them back on my new computer. It says it is only possible to read the data but not to copy them 

Basically it seems that the USB stick has been locked during the backup 


[COLOR=#59971a]
[/COLOR]
I have checked on some forums how to unlock the read only function of an usb stick while entenring in the terminal of the computer


but the keywords i got are for windows and It seems Ubuntu keywords are slightly different. 


This is what i was planning to do: 

[COLOR=#59971a]
[/COLOR]
Diskpart 

Select volume XXX 

Attribute disk clear readonly 


[COLOR=#59971a]
[/COLOR]
with these commands it is suppose to work... 

But the first diskpart is not recognize... 

Any idea? 

Thanks

---

### Post by again? on 2018-10-22
Try mkusb.
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by mdurham on 2018-10-22
> **guber2 said:**
> Try mkusb.
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

I think the mkusb command will delete all your data, be careful.

---

### Post by oldos2er on 2018-10-22
> **guber2 said:**
> Try mkusb.
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

I believe OP needs to recover data from the USB, not format it.

---

### Post by again? on 2018-10-22
> **mdurham said:**
> I think the mkusb command will delete all your data, be careful.

Yeah, you're probably right.
I was only thinking about restoring a usb not retrieving the data.

---

