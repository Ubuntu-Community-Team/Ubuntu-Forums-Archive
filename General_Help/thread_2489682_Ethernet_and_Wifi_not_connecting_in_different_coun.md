---
title: "Ethernet and Wifi not connecting in different country"
date: 2023-08-07
forum: General Help
---

### Post by modena-kaamraan on 2023-08-07
Hi all, 

We set up a laptop for an international customer with 2 encrypted drives. 


[LIST=1]
[*]Windows 11 Pro
[*]Ubuntu 22.04.2 LTS
[/LIST]

We took this approach so that each drive could be fully encrypted.

This laptop was set up in South Africa with the local repositories. 
While the laptop was at our offices in South Africa, sudo apt update/upgrade etc. worked with no issues. Both wi-fi and ethernet were working perfectly.
The customer collected the laptop and took it with him to Belarus on a business trip.

In Belarus, the laptop does not show the Wifi adapter, and it also does not show the wired connection. 
As such, packages can't be installed or updated. 
We have tried to reconfigure network manager, repository settings, DNS settings, and a number of other solutions proposed on other threads, but we have had no luck in connecting to any networks or even identifying the network hardware.

Both the Wifi and Ethernet work on the Windows drive.

Does anybody know which settings may have changed and why? 
Or perhaps are there any other potential solutions?

Thanks so much, 
Kaamraan

---

### Post by modena-kaamraan on 2023-08-14
bump

---

### Post by MAFoElffen on 2023-08-14
But they need to work in Belarus, with their state owned communications monopoly "Beltelecom" and "Byfly"... [https://beltelecom.by/en/private/internet/wifi/access-methods-wifi](https://beltelecom.by/en/private/internet/wifi/access-methods-wifi)

Since it is very censored there, and everything goes through them, you have to get onto "their" network first, to get anywhere else...

At least, that is my understanding.

---

### Post by HermanAB on 2023-08-16
Well, it is no use faffing with the upper layer software if the low level devices and module’s dont work.

Sort out the HW first.

---

### Post by SeijiSensei on 2023-08-16
> **modena-kaamraan said:**
> In Belarus, the laptop does not show the Wifi adapter, and it also does not show the wired connection.
I find it unlikely that the adapter would suddenly disappear in Belarus. What do you see with lspci? Is there no longer an entry for "Network controller?"

---

