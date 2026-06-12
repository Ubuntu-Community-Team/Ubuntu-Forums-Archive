---
title: "Transmission corrupt downloads"
date: 2013-06-02
forum: General Help
---

### Post by Windowsdefector on 2013-06-02
Hello, 

I have downloaded a file and when I right-click it and look at the properties it says that 50MB of it is corrupted. I have deleted the file and downloaded it again and some parts of it is still corrupted. I can imagine downloading this a thousand times and still get some corrupted bits as people must be seeding bad files and I can't navigate away from that. 
Is there a way to bypass this? I have tried to "very local data" and it says that no errors were found but the corrupted info remains. 
Is there a function in the program that re-downloads only the corrupted parts in hope of finding non-corrupted parts? 

I am very new to Ubuntu so bear with me.

---

### Post by 3rdalbum on 2013-06-02
Bittorrent automatically redownloads parts that are corrupt. If the download reaches 100% and starts seeding only, then it has successfully completed downloading the file. The client still tells you how much corrupt data it has downloaded, but no corrupt data ends up in the end file.

That is why Bittorrent is recommended, because it guards against file corruption.

---

### Post by Windowsdefector on 2013-06-02
Ah, ok. Good to know. I was afraid I would have to re-download the file from another source. Thank you for your response.

I am still curious to how the file was corrupted in the first place if corrupted files are "seeded out" by the program itself?

---

