---
title: "Samba share"
date: 2015-06-19
forum: General Help
---

### Post by kevin.hernandez on 2015-06-19
Hello,

I have been having an issue with my samba shares being inaccessible from my 2008 R2 server. I am running samba 3.6.3 and seem to only be able to access my homedirs share by IP address. UNC by hostname brings up a windows prompt asking for credentials, which I enter, only to have it fail and bring me back to the same window. I have entered the netbios name in the smb.conf file and have verified that a correct DNS entry is located on the windows server. I can ping and nslookup both stations from each other so wondering why is I can access the share by running \\ip_address\share and not \\hostname\share. Using pbis as my authentication service. Thoughts?

---

### Post by Bucky Ball on 2015-06-19
Which release and flavour of Ubuntu are you using?

---

### Post by HermanAB on 2015-06-19
"running \\ip_address\share and not \\hostname\share"

That means your DNS isn't working.  Check it with 'dig'.

BTW, debug samba issues with 'smbclient', since it provides error messages, so then you can see what is going on.

---

### Post by kevin.hernandez on 2015-06-19
im using Ubuntu 14.04 with samba 3.6.3. Had to downgrade samba from 4 to 3 to allow functionality between samba and powerbroker.

---

### Post by kevin.hernandez on 2015-06-19
DNS seems to be working properly after issuing the dig command. Correct nameserver appears

---

