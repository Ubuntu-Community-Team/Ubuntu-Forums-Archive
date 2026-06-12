---
title: "Migrating mail from Thunderbird to Evolution"
date: 2006-12-05
forum: General Help
---

### Post by Master Shake on 2006-12-05
Anyone know how to migrate my emails from Thunderbird to Evolution?

---

### Post by chrisccoulson on 2006-12-05
I did this some time back, although I can't remember the exact specifics of it.

Evolution has the option of importing files. I seem to remember doing this for my Thunderbird e-mails. If you select Import from the File menu, then navigate to the files in your ~/.mozilla-thunderbird folder, you should be able to import your e-mails fairly easily.

Importing contacts is a little trickier, as Evolution won't read the format that Thunderbird uses (if my memory serves me correctly). To get my contacts in to Evolution, I had to export my contacts from Thunderbird as a tab-delimited file, and then convert the file to VCard format using a script from Sourceforge. The VCard format can then be imported in to Evolution.

The script can be found [here]("http://sourceforge.net/projects/tsv2vcf/")

---

### Post by Master Shake on 2006-12-05
Criminy.  How on earth did I miss that?
Thanks!

---

### Post by Rodneyck on 2006-12-05
> **chrisccoulson said:**
> I did this some time back, although I can't remember the exact specifics of it.

Evolution has the option of importing files. I seem to remember doing this for my Thunderbird e-mails. If you select Import from the File menu, then navigate to the files in your ~/.mozilla-thunderbird folder, you should be able to import your e-mails fairly easily.

Importing contacts is a little trickier, as Evolution won't read the format that Thunderbird uses (if my memory serves me correctly). To get my contacts in to Evolution, I had to export my contacts from Thunderbird as a tab-delimited file, and then convert the file to VCard format using a script from Sourceforge. The VCard format can then be imported in to Evolution.

The script can be found [here]("http://sourceforge.net/projects/tsv2vcf/")

Unfortunately this does not work, at least for me under Edgy. I did just make a post in the How-to section on this very topic, but unfortunately it has not been approved. Not sure how that process works.

Anyways, what you need to do is add this extension to Thunderbird which will allow you to import/export your email folders as .mbox. Evolution can then import .mbox emails into whatever folder you choose. The extension is called, "MBOXIMPORT" and can be found for download on this page;
[https://nic-nac-project.de/~kaosmos/index-en.html](https://nic-nac-project.de/~kaosmos/index-en.html)

Hope that helps..

---

