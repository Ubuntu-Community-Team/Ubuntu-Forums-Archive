---
title: "How to extract a .cap file?"
date: 2022-05-26
forum: General Help
---

### Post by BolinMDT on 2022-05-26
Hello there

I am about to update my Ubuntu to 22.04 but want to update the BIOS first. Looks straightforward except I can't get the .zip file downloaded from ASUS' website to extract to a .cap file using the Archive Manager. I am currently running 12.04 (!!).

Any ideas on how to make this work? It acts as if it is working but doesn't produce the .cap file at the end.

Does Archive Manager not work with .cap files? So do I need to get another extraction tool that will?

Thank you for any ideas! Regards, Bolin.

---

### Post by ActionParsnip on 2022-05-26
Does the system have a make and model?

---

### Post by BolinMDT on 2022-05-26
Zoomstorm 7873-1071

Motherboard ASUS P8H61-MX R2.0

Appears to be an issue with the archive manager on Ubuntu 12.04 not extrcting the .cap file needed for the BIOS update.

---

### Post by SeijiSensei on 2022-05-26
Have you tried using unzip from the command prompt?

---

### Post by BolinMDT on 2022-06-02
SOLVED

> **SeijiSensei said:**
> Have you tried using unzip from the command prompt?

Apologies for not responding sooner! No I haven't - because I found what the issue was first.

I was extracting in a folder with a very large number of files, in reverse date order. I expected the unzipped file to appear next to the zip file, when it didn't, I thought it hadn't worked. Turns out the unzipped file uses the date of when it was created, not when it was unzipped (I didn't previously know that) so it appeared near the bottom of the very large folder (BIOS file dated from 2014). I think there were about 3 unzipped copies of it.

Made me feel really stupid and I am sorry for wasting everyone's time!

BIOS now successfully updated, new SSD installed and 22.04 loaded, with mod to get the video player working and Firefox customised, inc. with tabs below the toolbar. Very happy so far:D

---

### Post by TheFu on 2022-06-02
Please mark this thread SOLVED so people don't waste time.  "Thread Tools" button.  It helps both people seeking answers and people hoping to help.

BTW, please mark in your calendar in January 2027 that you need to upgrade to a new computer OS.  Running any OS that is 5 yrs out of support is crazy if it is connected to any network.

---

