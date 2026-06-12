---
title: "Clip Board &amp; Terminal Server Client"
date: 2007-11-06
forum: General Help
---

### Post by Fidgel on 2007-11-06
I use Terminal Server Client every day.  Used it from Windoze for the last 8 to 10 years.  The only thing missing in Ubuntu's Term Server Client is clip board support.  It seems as if I cannot transfer the contents of the local clip board to the remote server and visa versa.

Am I missing a setting or something?

On another look, I don't see remote or shared printer support either.  Do I have to setup my local printers on the server manually?

Thanks
Fidgel

---

### Post by cwaldbieser on 2007-11-06
The "-r" option of rdesktop lets you share local drives and printers.
I am not sure about clipboard support.  I have problems with that in some Windows to Windows situations.  rdclip.exe just seems flaky, sometimes.

---

### Post by NoThanksM$ on 2008-03-25
The Terminal Server Client in Ubuntu should support clipboard transfer if you use the RDP v5 protocol instead of just RDP, as shown here:
[http://www.giannistsakiris.com/index.php/2007/10/04/shared-clipboard-with-terminal-server-client-on-ubuntu/](http://www.giannistsakiris.com/index.php/2007/10/04/shared-clipboard-with-terminal-server-client-on-ubuntu/)

---

### Post by Fidgel on 2008-03-25
> **NoThanksM$ said:**
> The Terminal Server Client in Ubuntu should support clipboard transfer if you use the RDP v5 protocol instead of just RDP, as shown here:
[http://www.giannistsakiris.com/index.php/2007/10/04/shared-clipboard-with-terminal-server-client-on-ubuntu/](http://www.giannistsakiris.com/index.php/2007/10/04/shared-clipboard-with-terminal-server-client-on-ubuntu/)
Coooool, Thanks I will give it a try in the morning.
 
JOhn ><>

---

### Post by smurffit on 2008-06-08
> **NoThanksM$ said:**
> if you use the RDP v5 protocol instead of just RDP

This works perfect - thank you =D>

---

