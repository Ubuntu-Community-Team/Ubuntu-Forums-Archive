---
title: "OpenOffice.org strange problem"
date: 2006-10-31
forum: General Help
---

### Post by jimtb on 2006-10-31
I have a huge problem with OpenOffice. Yesterday it started to make my whole system freeze up sometimes and now this happens every time I am trying to launch it. No message appears when I run it from the terminal, but everything stops responding, the cursor, Ctrl + Alt + Backspace, Alt + Del + Ctrl, Alt + Ctrl + F1, and I can only restart the computer by pressing the reset button.

The only thing that appears in the logs is this:
```
Oct 31 19:16:00 jimakos-desktop kernel: [17179628.396000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Oct 31 19:16:00 jimakos-desktop kernel: [17179628.396000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Oct 31 19:16:00 jimakos-desktop kernel: [17179628.396000] ide: failed opcode was: unknown
```
(but not only when openoffice.org is starting)

I read somewhere that it may be an nvidia driver issue, so I thought it would be better to downgrade to the stable version(I'm using the beta drivers so I could get beryl working). However, when I removed the nvidia-glx package from Synaptic and then tried to install the official one, it said I also had to install xen-image and xen-headers. I did that, but the xserver wouldnt start with the nvidia driver, saying something about incompatible versions of X-server module and kernel nvidia module.](*,) 


I would appreciate it if you could give me any suggestions as soon as possible cause I have this huge homework saved in .odt and I have to have it finished till tomorrow. 

:-)

---

