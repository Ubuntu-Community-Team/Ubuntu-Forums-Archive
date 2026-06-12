---
title: "Ubuntu 14.04: GeForce GTX 660, additional driver tool crashes"
date: 2014-04-20
forum: General Help
---

### Post by vedran-matic-82 on 2014-04-20
Hi,

I've installed Ubuntu 14.04 (64-bit) but I am unable to install propriatery nVidia driver. I try to do it in
the following way (menu options translated from Swedish):

Open System Settings -> Program and updates -> Additional drivers tab

At this point, Ubuntu starts searching for propriatery driver but eventually crashes and doesn't find any drivers.

The output of lspci | grep VGA outputs the following:

```
user@user-XPS-8500:~$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 660 OEM] (rev a1)
```

How can I install the nVidia propriatery driver?

Kind Regards.

---

### Post by gnice3d2 on 2014-04-24
1) Make sure you have no broken dps, kicking the driver install back:

sudo apt-get install -f

2) Some of the repos were late updating. Go to **Software & Updates** > **Ubuntu Software **tab and choose a local mirror from the "**Download From**" dropdown box.

3) (Optional) Should probably enable your partner repos under the **Other Software** tab while your in here.

4) Close and reload when prompted.

5) Try to install the proprietary driver again.

---

