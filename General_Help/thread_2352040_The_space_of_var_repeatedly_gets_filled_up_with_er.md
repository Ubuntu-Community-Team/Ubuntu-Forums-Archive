---
title: "The space of /var repeatedly gets filled up with error in log"
date: 2017-02-09
forum: General Help
---

### Post by hamcheese on 2017-02-09
The problem has happend out of a blue and had been repeated itself for 3 times in the past 2 months.
Some error message would spam the log until the space for /var has been filled up near 5GB
both kern.log and syslog would be effected with around 2GB each.

here's a sample of message from the kern.log file
Jan  2 03:32:30 hc-h kernel: [91315.252252] ieee80211 phy0: rt2800usb_tx_sta_fifo_read_completed: Warning - TX status read failed -71

does anyone know what's the cause of this problem and how do i get rid of it for good?

thank you for your time~

---

### Post by Keith_Helms on 2017-02-09
Do you have a USB wifi adapter?

---

### Post by HermanAB on 2017-02-09
Yup - that is a RALINK USB WiFi adaptor problem.  Maybe it is time to buy a new one.

---

