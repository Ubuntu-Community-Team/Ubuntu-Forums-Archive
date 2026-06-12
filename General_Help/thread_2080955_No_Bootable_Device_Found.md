---
title: "No Bootable Device Found"
date: 2012-11-05
forum: General Help
---

### Post by CrusaderAD on 2012-11-05
Ok, I installed a fresh copy of Ubuntu on a Acer Aspire S7 Ultrabook and deleted everything else. The machine is using UEFI but is capable of using Legacy BIOS too. Now when I boot it says "No bootable device found". The install went fine no errors. Any ideas as to why it won't boot up?

---

### Post by ajgreeny on 2012-11-05
None at all, but it is worth clicking on the **Boot-info-script** link in my signature to use the Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Paste contents of RESULTS.txt in a New Reply, then highlight entire file and click on # in toolbar (code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ CODE] paste here [ /CODE] tags.

From V60 the script output has improved formatting and requires code tags to make it legible. New Version is a zip file that you have to extract first to get the .sh to run.

[Ubuntu Boot Repair]("http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html")  may also be helpful.

---

### Post by CrusaderAD on 2012-11-06
Solved. What I had to do what change the bios from UEIF to Legacy, restart, then run my installation of Ubuntu. Do it in this order and it'll run fine.

---

