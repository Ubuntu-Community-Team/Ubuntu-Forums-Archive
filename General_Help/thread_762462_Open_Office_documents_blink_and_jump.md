---
title: "Open Office documents blink and jump"
date: 2008-04-22
forum: General Help
---

### Post by Mman_ on 2008-04-22
There's a strange problem with my OO writer that's bugged me for a couple of weeks now.

Whenever I have the OO Writer open and select File->New->Text Document, or open another document, the new document start to "blink", changing it's depth in relation to the original OO document very fast. The new document jumps to front of all other windows and  then immediately behind the original OO document. This happens like 10 times in a second.

By clicking furiously on the X icon at the upper-right corner of either window eventually helps, as the other window is either closed, or diplays the dialog asking whether to save to doc or not. This stops the blinking. Clicking cancel at the dialog keeps the both windows open and then they start behaving normally. No blinking.

Sometimes this blinking occurs with two different types of documents. Like in OO writer selecting File->New->Spreadsheet  ... blink blink blink... But most of the time it's solely between two writer documents. I haven't dared to try this with three docs :p

System: Ubuntu 7.10 OO 2.3.0

Any ideas how to fix this?

---

### Post by decoherence on 2008-07-31
Are you using special effects on the desktop a la compiz?

---

### Post by geirha on 2008-07-31
> **decoherence said:**
> Are you using special effects on the desktop a la compiz?

My first guess as well. Try opening a terminal and run ```
metacity --replace &
``` This will temporarily disable the visual effects. See if the problem with OOwriter persists. The following will turn the visual effects back on ```
compiz --replace &
```

---

