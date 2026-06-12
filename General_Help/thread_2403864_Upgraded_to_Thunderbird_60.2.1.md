---
title: "Upgraded to Thunderbird 60.2.1"
date: 2018-10-17
forum: General Help
---

### Post by Panawe on 2018-10-17
Have upgraded Thunderbird and now lost my calendar/diary. 

I recall this happening once before, has anyone come up with a work-around?

TIA

---

### Post by ajgreeny on 2018-10-17
Remove **lightning** the add-on which you probably got from the T'Bird add-on site and install the **xul-ext-lightning** package in the usual way for installing software.

It's the same add-on but this repository version is updated when the ubuntu repos are, and it will work with the T'Bird version you have.

---

### Post by Panawe on 2018-10-17
Installed via Synaptic Package Manager and restarted Thunderbird. Fine now.

Thanks.

---

### Post by robert48 on 2018-10-18
Brilliant! I now have my calender back in Thunderbird. I deleted the lightning add-on in Thunderbird, closed down Thunderbird and used the terminal with
```
sudo apt-get install xul-ext-lightning
```
... and all worked again when I re-opened Thunderbird.

Thank you very much!

---

### Post by med304 on 2018-11-22
Nice Solution.

---

### Post by david-paiva-fernandes on 2019-01-04
Perfect! Thank you.

---

