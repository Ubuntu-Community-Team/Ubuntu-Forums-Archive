---
title: "Need Help to Understand the following Instruction?"
date: 2008-05-24
forum: General Help
---

### Post by davidkyn on 2008-05-24
Hi,
I dont quite understand how to change the line...I follwed the part about the update and that was good,,,,,but If I can refer to to the BOLD print below:


Mute Speakers when Headphones are used

    * This has been a big deal for folks with Intel HDA type sound cards.  The fix is as follows.  Information about this fix is gotten from here.
          o Update ASLA to the latest (1.0.16 as of this writing).  I have instructions here.
          

o **In your /etc/modprobe.d/alsa-base add the following line**.
                + options snd-hda-intel probe_mask=8 model=lenovo
                + save and exit
                + reboot the machine and when you insert headphones the speakers will mute.

[SIZE="6"]???HOW DO I OPEN /ECT/MODPROBE.D/ALSA-BASE & do I simply cut and paste?????????????????[/SIZE]

---

### Post by sisco311 on 2008-05-24
To open the file as superuser:
Press Alt+F2 and type(or copy/paste):
```
gksu gedit /etc/modprobe.d/alsa-base
```Click on the *Run* button. 
Copy and paste
> options snd-hda-intel probe_mask=8 model=lenovoat the end of the file(in a new line).
Save the file and exit.(Ctrl+s,Alt+F4)

---

### Post by amn on 2008-05-24
> **davidkyn said:**
> o **In your /etc/modprobe.d/alsa-base add the following line**.
                + options snd-hda-intel probe_mask=8 model=lenovo
                + save and exit
                + reboot the machine and when you insert headphones the speakers will mute.
Do this to open the file (assuming you have gedit installed):
```
$ sudo gedit /etc/modprobe.d/alsa-base
```

Then just copy and paste the line "options snd-hda-intel probe_mask=8 model=lenovo" at the end of the file, save the file and reboot. That's my interpretation of the guide.

> **davidkyn said:**
> [SIZE="6"]???HOW DO I OPEN /ECT/MODPROBE.D/ALSA-BASE & do I simply cut and paste?????????????????[/SIZE]
No need yelling.

---

### Post by Kevbert on 2008-05-24
Please see your other post...[http://ubuntuforums.org/showthread.php?p=5031307#post5031307]("http://ubuntuforums.org/showthread.php?p=5031307#post5031307")

---

### Post by davidkyn on 2008-05-24
Thankyou very much to you all...cheers

---

### Post by hyperair on 2008-05-24
This snippet of code is a oneliner which will work in a terminal and complete all that for you.
```
echo "options snd-hda-intel probe_mask=8 model=lenovo" | sudo tee -a "/etc/modprobe.d/alsa-base"
```

Now, on a side note, your affection for large fonts has caused this to me: [img]http://i25.tinypic.com/30bgpro.gif[/img]
I hope you're happy. Please do not repeat it.

---

