---
title: "How do I erase a hard drive"
date: 2008-04-02
forum: General Help
---

### Post by explorer716 on 2008-04-02
I have a computer with two hard drives that I want to donate to charity. One drive has Windows XP and the other has Linux Ubuntu.

What is the best way to erase  personal information that I  have on these two drives?

---

### Post by LaRoza on 2008-04-02
See the link in my sig. 

Get DBAN (Derik's Boot and Nuke). Boot from it and enjoy.

(Be careful, by default, it will wipe every drive, but you can chose other options)

---

### Post by indytim on 2008-04-03
Another suggestion, go to Seagate site and download their disc tools.  Do a low-level format on the selected drive.

IndyTim

---

### Post by gsmanners on 2008-04-03
I wouldn't format because that might leave data detectable on your drive. Either use DBAN or:

wipe -kq /dev/hda3

That will thoroughly erase the data on /dev/hda3.

---

### Post by stinger30au on 2008-04-03
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)
**Darik's Boot and Nuke**

   		Darik's Boot and Nuke ("DBAN") is a self-contained boot disk that securely wipes the hard disks of most computers. DBAN will automatically and completely delete the contents of any hard disk that it can detect, which makes it an appropriate utility for bulk or emergency data destruction.
  		[[IMG]http://www.dban.org/geeplogo-88x110.png[/IMG]]("http://www.geepinc.com/")  		DBAN is a means of ensuring due diligence in computer recycling, a way of preventing identity theft if you want to sell a computer, and a good way to totally clean a Microsoft Windows installation of viruses and spyware. DBAN prevents or thoroughly hinders all known techniques of hard disk

---

