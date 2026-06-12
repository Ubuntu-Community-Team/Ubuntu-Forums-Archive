---
title: "Ubuntu 20.04 Brother HL-L2375DW printer USB recognised now prints"
date: 2021-01-08
forum: General Help
---

### Post by Handssolow on 2021-01-08
My Brother HL-L2375DW initially printed a couple of documents then no more. GA-990FXA-UD5, AMD 8 core CPU, Ubuntu 20.04 Metacity flashback.

This laser printer was working under 16.04. In the last two weeks I'd upgraded to 18.04 and almost immediately to 20.04 To cut a long story short my printer wasn't recognized in lsusb, it wasn't a driver issue, or a usb cable issue. The log file showed errors associated with my usb ports not being recognized. At times CUPS incorrectly reported only that I had a braille printer. After Installing Brother's driver it showed in printers but with error reports that it was "waiting for the the printer to become available".

On YouTube Roel Van de Paar pointed me to **iommu**. Once this was enabled I had no USB error messages in the log and my printer was recognized in lsusb. I added the printer and chose for now the gutenprint driver. My printer works again, I may later change to using the Brother driver. 

[https://www.youtube.com/watch?v=6I3xWmSdGRM](https://www.youtube.com/watch?v=6I3xWmSdGRM)

What may have been significant was during this time I modified the bios to hopefully enable booting from NVMe memory on this GA-990FXA-UD5 mobo. I've already done this process on an Asus AMD mobo that's now booting Manjaro. Perhaps my bios configurations had been reset to disable iommu.

Having a problem with usb printer recognition? Check you have **iommu** enabled in the bios.

---

