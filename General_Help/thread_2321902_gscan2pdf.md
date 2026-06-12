---
title: "gscan2pdf"
date: 2016-04-25
forum: General Help
---

### Post by peter228 on 2016-04-25
I was wondering if anyone has gscan2pdf running in 16.04?

I have installed and all that happens when I click the icon is that the program asks me to pick a crash session to restore.... so it does not actually run.

I installed from the jeffreyratcliffe ppa.

I have also uninstalled and cleaned up (autoremove) and then installed again but it is the same result.

My scanner is installed and working ... I have tested with xsane and simple scan.

---

### Post by peter228 on 2016-05-02
I got this working .... 

First remove gscan2pdf using 'Ubuntu Software'.
Then delete the dot file
Then clean with BleachBit.

Then check it was all gone using Which since the 'Ubuntu Software' had reported that it was there but could not be uninstalled.

Then reinstall.  But the 'Ubuntu Software' said it did not exist as a package so ...  use apt to update the repositories and then use apt to install.

The result was an installed package that would open.

---

