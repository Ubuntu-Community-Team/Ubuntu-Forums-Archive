---
title: "Lenovo L14 G2 AMD wakes up from suspend with high energy consume and unresponsible"
date: 2023-07-04
forum: General Help
---

### Post by Roland_Msl on 2023-07-04
Yesterday arrived my Lenovo L14 G2 AMD. I installed Ubuntu 22.04 2 on it.
It happened 2 times, that the Lenovo waked up from suspend with high energy consume. The power button did not work, only 7 seconds press to switch off.
Energy consume normal 0.7 W in suspend, 6 W waiting for user input with screen on.
But in this case, 16 W.

---

### Post by Roland_Msl on 2023-07-05
I found in the BIOS &#8211; Config &#8211; Power &#8211; Sleep State. To choose had been &#8220;Windows 10&#8221; or &#8220;Linux&#8221;. I changed this to Linux. Now it works.
The difference is also visible on the Watt meter: 0.6 W instead of 0.7 W.

---

