---
title: "Is there a version of GPG included with LuBuntu 14.04? Urgently need info`"
date: 2017-04-05
forum: General Help
---

### Post by J Tinsby on 2017-04-05
My main machine with Linux Mint on it has a failed PSU as of today! I have encrypted files .gpg on that machine, I also have a thumb drive with the same files encrypted. I am using my old Dell machine with LuBuntu on it. When I put the encrypted file on the desktop and right click, I get no option to DEcrypt that file. It's very important because all my user names and P/W's are there and I need access to pay bills!!

Looking in Synaptic in LuBuntu I see there are some files that pertain to GPG that appear to be installed, but I don't see the program listed in the list of programs.

Can I only use those files from the terminal? 

Or is there something else I need to install to allow me to right click on the encrypted file and open it? I know I can do that in Mint but until now I haven't needed it on this old machine.

If I must use the terminal what is the correct syntax to use to decrypt my file?

Thank you very much, this is very important!

Regards,

J Tinsby

---

### Post by Dennis N on 2017-04-05
The package is named **gnupg** and it's installed by default on Lubuntu 14.04. But, the decrypt option is not available in the right-click menu of it's file manager (PCManFM), so you will have to formulate a terminal command to decrypt any file.

Command to decrypt file secrets.txt.gpg with decrypted result saved as secrets.txt:
**gpg -o secrets.txt -d secrets.txt.gpg**

---

### Post by J Tinsby on 2017-05-12
Thank you Dennis! Sorry for the delay in saying"thanks" thought I had done it. Cheers! J T

---

