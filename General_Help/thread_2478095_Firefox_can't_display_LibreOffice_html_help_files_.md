---
title: "Firefox can't display LibreOffice html help files and more"
date: 2022-08-16
forum: General Help
---

### Post by patspiper on 2022-08-16
Hi all,

LibreOffice Calc stopped displaying help files (F1 or Help/LibreOffice Help) after I upgraded from Ubuntu 20.04 to 22.04.1.

It seems Firefox (snap) can't open and/or save files in folders outside home, such as /tmp/ or /usr/share/libreoffice/help/en-US/text/shared/ (where LibreOffice help files are). Even saving the current page (Save Page as) in /tmp/ fails.

Moreover, downloading a spreadsheet to /tmp/ and opening it from the download dropdown list lets LibreOffice show the dialogue with Open Read-Only, Notify, Open Copy, and Cancel buttons.

Are these symptoms bugs, or by design (in which case i might switch to a normal Firefox deb installation)?

---

### Post by Claus7 on 2022-08-16
Hello,

> **patspiper said:**
> Hi all,

LibreOffice Calc stopped displaying help files (F1 or Help/LibreOffice Help) after I upgraded from Ubuntu 20.04 to 22.04.1.

...

I can assure you that the moment I pressed F1, all at once the default browser opened with a new tab showing LibreOffice Help. Ubuntu 22.04.1 under flashback.

Regards!

---

### Post by patspiper on 2022-08-16
> **Claus7 said:**
> Hello,

I can assure you that the moment I pressed F1, all at once the default browser opened with a new tab showing LibreOffice Help. Ubuntu 22.04.1 under flashback.
Regards!

Is firefox (snap version) your default browser?

---

### Post by deadflowr on 2022-08-16
It's a known bug:
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1951210]("https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1951210")
Seems it regressed.

---

### Post by Claus7 on 2022-08-16
Hello,

> **patspiper said:**
> Is firefox (snap version) your default browser?
no.

Regards!

---

### Post by patspiper on 2022-08-17
> **deadflowr said:**
> It's a known bug:
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1951210](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1951210)
Seems it regressed.

Firefox snap package has been quite controversial. I hope the issues get sorted out the soonest.

---

### Post by ajgreeny on 2022-08-17
> **Claus7 said:**
> Hello,


no.

Regards!
Do you mean Firefox is not your default browser or is not the snap version?

I run Firefox from the extracted .tar.gz direct from Mozilla and on my system the LO help auto automatically opens in Firefox  whether it is my default browser or not.

---

### Post by Claus7 on 2022-08-17
Hello,

> **ajgreeny said:**
> Do you mean Firefox is not your default browser or is not the snap version?
for both questions my answer is negative: neither Firefox is my default browser nor is the snap version.

> **ajgreeny said:**
> I run Firefox from the extracted .tar.gz direct from Mozilla and on my system the LO help auto automatically opens in Firefox  whether it is my default browser or not.
my answer to this question is affirmative: it is exactly as you describe it.

Regards!

---

### Post by mIk3_08 on 2022-08-17
> **patspiper said:**
> Firefox snap package has been quite controversial. I hope the issues get sorted out the soonest.
Yes. It is. better remove the snap firefox and change it using deb package. And if you have another browser use it to save you html page. Regards and cheers.

---

