---
title: "Could not Initialize HAL"
date: 2008-05-20
forum: General Help
---

### Post by globemast on 2008-05-20
Hello,

I recently upgraded from Ubuntu 7.10 to 8.04 and i get the following problem.

After login i get an error message saying: "Could not initialize HAL" with no other log information.

As a consequence, no USB drives are recognized and auto-mounted.

Has anyone else had the same problem? Any suggestions?

Thanks in advance.

---

### Post by danwood76 on 2008-05-20
Have a look through system log in the adminisration menu and see if there are any other entries related to hal.

You could also search dmesg directly from the command line/terminal with this:
```

dmesg | grep -i 'HAL'

```

---

### Post by globemast on 2008-05-20
Hi danwood76, thanks for the prompt response.


This is what i get with dmesg:

```

[   34.437048] hald[5793]: segfault at c1db186b eip 08056e76 esp bff107f0 error 5

```

Any ideas ??

---

### Post by danwood76 on 2008-05-20
There are some hal updates in the update manager if you havent updated already from the default install.

If that doesnt work you could try reinstalling HAL.
Open up synaptics and search hal, right click it and click re-install, then apply.

---

### Post by cdtech on 2008-05-20
Have you used gparted lately?

look at /usr/share/hal/fdi/policy/ for an fdi file. This could be blocking the automount.

I had this same issue, it was gparted that closed with an error and didn't delete the file gparted-disable-automount.fdi at this directory. The solution that corrected my problem was simply open gparted and close it again (with the same user that opened it before).

There were some that suggested deleting /usr/share/hal, then reinstalling hal
but deleting the hal removes some files not accossiated with hal (bad idea).

Do you get any messages with sudo /etc/init.d/hal restart?
Should get:" * Restarting Hardware abstraction layer hald"
Be sure to check your proper rc directory, just a suggestion.

Hope this helps....

---

### Post by danwood76 on 2008-05-20
Hal daemon is seg faulting, meaning its probably an install issue.
Reinstalling hal using synaptics wont remove anything silly.

---

### Post by globemast on 2008-05-20
Hi,

re-installing HAL through Synaptics solved my above problems.

Thanks to all that contributed to my question.

Best regards.

---

