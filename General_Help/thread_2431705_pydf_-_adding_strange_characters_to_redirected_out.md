---
title: "pydf - adding strange characters to redirected output"
date: 2019-11-20
forum: General Help
---

### Post by Frank P on 2019-11-20
18.04.3 LTS
pydf output shows correctly on terminal or piped to a text file viewed via cat. Output redirected to printer or printed from text file is showing "33m" at beginning and end of title line and "0m" at beginning and end of detail lines. It's not serious, just annoying. Is there a way to clean it up
Thanks

---

### Post by spjackson on 2019-11-21
Those characters are part of escape sequences to change the colour of text in the terminal. These escape sequences are not interpreted by the printer. Use the following to disable colour switching.
```
pydf --bw
```

---

### Post by Frank P on 2019-11-21
perfect - thank you
Frank

---

