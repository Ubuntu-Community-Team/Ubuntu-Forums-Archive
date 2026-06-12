---
title: "Firefox download PDf files instead of opening them in the windows."
date: 2016-06-18
forum: General Help
---

### Post by georgesgiralt on 2016-06-18
Hello !
The context : Ubuntu 14.04.1 with all updates installed. 
When I go to a web page with a link or icon for a PDF file, and I click on the link/icon, the files gets downloaded. I've to go to download (the bleu arrow) and open it by double click on the name. 
This behavior has changed some times ago  and was working perfectly before. 
So could you please help me finding what I broke ? And how to restore it back ? 
Many thanks in advance for your help
Edit : Thank you Howefield to pointing this huge mistake of mine !

---

### Post by howefield on 2016-06-18
I'm sure that you have a "sound" reason for using it but 10.04 is horribly end of life (on the off chance that you are unaware).

Could be an addon/extension that is blocking the built in pdf viewer ?

---

### Post by ajgreeny on 2016-06-18
@howefield:
See edit from georgesgiralt; he is using 14.04 not 10.04.

Hi georgesgiralt.
Go to the Firefox Edit menu ->Preferences->Applications tab, search for pdf and change the setting to "Preview in Firefox"

---

### Post by georgesgiralt on 2016-06-18
Thank you Ajgreeny ! It works !
But a side question : How come the appearance in the Firefox Windows is not the same as in Evince windows ? Is there a different application involved when looking at a PDf file inside Firefox and outside ?

---

### Post by ajgreeny on 2016-06-18
Different how?

---

### Post by vasa1 on 2016-06-18
> **ajgreeny said:**
> Different how?

Maybe OP's wondering about the stuff above the actual pdf contents based on "But a side question : How come the appearance in the Firefox Windows is not the same as in Evince windows ? Is there a different application involved when looking at a PDf file inside Firefox and outside ?"? 

Firefox does indeed use its own method to display pdf files. From what I remember it is largely javascript-based: [https://mozilla.github.io/pdf.js/](https://mozilla.github.io/pdf.js/)

---

### Post by ajgreeny on 2016-06-18
Great. If you are now happy, please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

### Post by coldraven on 2016-06-18
Ha Ha! I want the opposite! If the browser opens the pdf then I have to download it twice :( No problem if it is reasonably small but a pain if it is big.

---

### Post by ajgreeny on 2016-06-19
If goergesgiralt wants both options he can just set it to display in the FF preview as default, but when he needs to download the PDF for some reason simply right click on the link and use "Save link as..."

---

